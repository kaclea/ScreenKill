# ScreenKill

Infrared kill switch for Android. One tap, target goes dark.

```
● STANDBY

ScreenKill
SIGNAL  TERMINATOR

┌────────────────────────────┐
│       [  F I R E  ]        │
└────────────────────────────┘

──────────────────────────────

> awaiting input
> target: unknown
> ready
```

## What it does

Emits a sweep of TV power codes over the phone's IR LED. Covers 37 domestic
(Chinese) payloads plus 89 global ones, extracted from Flipper-IRDB and two
captured live signatures.

| Command | Payloads | Time |
|---|---|---|
| `tvoff` | 37 domestic | ~8s |
| `tvoff quick` | 1 (Changhong true code) | 0.3s |
| `tvoff full` | 89 global | ~18s |
| `tvoff scan` | 256-address NEC sweep | ~20s |
| `tvoff quiet N` | payload #N only | 0.1s |

Sample output:

```
=== FIRING - domestic set ===
aim at target, within 3m

  [ 1/37] CHANGHONG_TV     37500Hz  68v  108ms
  [ 2/37] NEC_04_08        37500Hz  67v   70ms
  [ 3/37] NEC_40_12        37500Hz  67v   70ms
  ...

DONE: 37 ok / 0 fail / 37 total in 8.3s
```

## Requirements

- Root (Magisk). Temporary root works.
- `/system/bin/app_process` (stock Android).
- SELinux permissive recommended — the IR HAL gets blocked under enforcing.

## Install

```bash
# push payloads + emitter
adb push payloads/* /data/local/tmp/irtool/
adb push apk/irblast.dex /data/local/tmp/
adb push scripts/tvoff /data/local/tmp/irtool/tvoff

adb shell 'su -c "
  chmod 755 /data/local/tmp/irtool/tvoff
  chmod 644 /data/local/tmp/irtool/*.txt
  chmod 777 /data/local/tmp/irtool/tmp
  chcon -R u:object_r:shell_data_file:s0 /data/local/tmp/irtool
  chmod 644 /data/local/tmp/irblast.dex
"'

# optional GUI
adb install apk/ScreenKill.apk
```

## Why not just use an app

Standard IR apps use `ConsumerIrManager`. This goes one level down — it talks
to `IConsumerIrService` over binder via `app_process`, which is roughly 5x
faster per frame (11ms short-frame floor vs ~200ms with `service call`).

That speed matters when you're sweeping 37 codes in the time a normal app
sends 5.

## How the codes were obtained

1. **Flipper-IRDB** — 370 power codes parsed, 8 protocols reimplemented
   (NEC, NECext, Samsung32, SIRC, RCA, RC5/RC6, Kaseikyo, Pioneer). 89 unique
   after dedup.
2. **Live capture** — hooked `ConsumerIrManager.transmit` in a third-party
   remote app with frida, pressed the power button, recorded the exact
   timing array. Done for a Changhong TV and a Hisense AC.

Captured signatures (verified, reproduced byte-for-byte):

```
CHANGHONG_TV   NEC  0x40/0x12  37500Hz  68 values
HISENSE_AC     Kaseikyo         38000Hz  269 values
```

## Timing parameters

Standard NEC is `9000/4500, 560/560, 560/1690`. Real devices drift:

```
Changhong measured:  9029/4544, 578/591, 578/1743
```

Payloads here use the measured values where available.

## Known limits

| Limit | Why |
|---|---|
| ~3m range | Phone IR LED power |
| Bluetooth remotes | No IR receiver at all |
| Some brands uncovered | Skyworth, Konva, Huawei — no true codes yet |

## Files

```
scripts/tvoff          emitter script (POSIX sh)
payloads/cn_final.txt  37 domestic codes
payloads/changhong.txt Changhong true signature
payloads/flipper_full.txt  global set
payloads/cn_pwr.txt    256-address sweep
payloads/ac_captured.txt  Hisense AC signature
apk/ScreenKill.apk        GUI
apk/irblast.dex        binder emitter (11ms/frame)
```

## License

MIT
