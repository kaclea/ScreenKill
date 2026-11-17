# Coverage

**89 payloads**, parsed from **370 Power codes** across **106 brands**.


## Domestic quick set (40 codes) — `tvoff fast`

The default `tvoff` runs 89 codes. `tvoff fast` runs a leaner 40-code set tuned
for Chinese TVs:

| # | Code | Protocol | Freq | Notes |
|---|---|---|---|---|
| 1 | `CHANGHONG_TV` | NEC 0x40/0x12 | 37500Hz | **captured live, verified** |
| 2 | `AOC_TV` | NECext 0x00BD/0x01FE | 38000Hz | from probonopd/irdb |
| 3 | `KONKA_1` | raw 88v (Aiwa) | 38000Hz | **synthesized, UNTESTED** |
| 4 | `KONKA_2` | raw 88v (Aiwa) | 38000Hz | **synthesized, UNTESTED** |
| 5-26 | `NEC_xx_xx` ×22 | NEC | 37500Hz | real (addr,cmd) combos from 105 codes |
| 27-31 | `Hisense_*` ×5 | NECext / raw | 38000Hz | Flipper-IRDB |
| 32-34 | `TCL_*` ×3 | NECext / RCA | 38000/56000Hz | Flipper-IRDB |
| 35-40 | BBK, Blitzwolf, Apex, Element, Sceptre, PrismPlus | mixed | mixed | Flipper-IRDB |

**Konka warning**: those two payloads were synthesized from the Aiwa (Sanyo
LC7461) protocol spec, never verified against real hardware. If you have a
Konka TV, test `tvoff` payload 3 and 4 individually first.

## By protocol

| Protocol | Payloads | Total models |
|---|---|---|
| NEC | 22 | 100 |
| NECext | 29 | 83 |
| Samsung32 | 4 | 53 |
| RC5,RC6 | 1 | 46 |
| raw | 28 | 29 |
| SIRC | 2 | 28 |
| Kaseikyo | 1 | 19 |
| RCA | 1 | 11 |
| Pioneer | 1 | 1 |

## Multi-brand payloads (one code, many brands)

| # | Freq | Protocol | Models | Brands |
|---|---|---|---|---|
| 1 | 38000Hz | NECext | 14 | Amazon, AmazonBasics, Bolva, Dual, Element, Insignia **+3** |
| 2 | 38000Hz | NEC | 55 | GuestTek, Haier, Hisense, Hotels, LG, Sharp **+3** |
| 3 | 56000Hz | RCA | 11 | Boulanger, EssentielB, Ffalcon, RCA, TCL, Thomson |
| 4 | 38000Hz | NECext | 9 | Onn, Philips, RCA, Sanyo, TCL |
| 5 | 38000Hz | NECext | 5 | Apex, Blaupunkt, Denver, Sharp |
| 6 | 38000Hz | NECext | 8 | Dynex, Hisense, Insignia, RCA |
| 7 | 38000Hz | Samsung32 | 3 | JVC, PrismPlus, Strong |
| 9 | 38000Hz | NECext | 8 | Devant, Hisense |
| 10 | 40000Hz | SIRC | 27 | Sceptre, Sony |
| 15 | 36000Hz | RC5,RC6 | 46 | Bush, ContinentalEdison, Crown, Digihome, EdenWood, FINLUX **+15** |
| 16 | 38000Hz | NEC | 12 | Grandin, Kogan, Oky, Strong, Supra, Toshiba **+1** |
| 17 | 38000Hz | NEC | 5 | Elements, Erisson, Furrion, RCA, Sankey |
| 18 | 38000Hz | NEC | 4 | Baird, Cranker, Sweex, Westinghouse |
| 19 | 38000Hz | NECext | 4 | ContinentalEdison, Elitelux, Platinum, Telefunken |
| 20 | 38000Hz | NECext | 3 | ContinentalEdison, GVA, Viano |
| 21 | 38000Hz | NECext | 3 | Akai, Bauhn |
| 24 | 38000Hz | NECext | 3 | Emerson, Funai |
| 27 | 38000Hz | NEC | 3 | Manta, RCA |
| 28 | 38000Hz | Samsung32 | 36 | Samsung, Viore |
| 58 | 37000Hz | Kaseikyo | 19 | Panasonic |
| 64 | 38000Hz | Samsung32 | 13 | Samsung |
| 67 | 38000Hz | NEC | 3 | Sanyo |
| 76 | 38000Hz | NECext | 3 | Soniq |

## Brands with the most payloads

| Brand | Payloads |
|---|---|
| Sharp | 9 |
| RCA | 7 |
| Grundig | 6 |
| Hisense | 5 |
| Strong | 4 |
| ContinentalEdison | 4 |
| Samsung | 4 |
| Telefunken | 3 |
| Toshiba | 3 |
| LG | 3 |
| Vizio | 3 |
| TCL | 3 |
| Philips | 3 |
| JVC | 3 |
| Hitachi | 3 |
| Magnavox | 3 |
| Insignia | 2 |
| Westinghouse | 2 |
| Hotels | 2 |
| Sanyo | 2 |
| Sony | 2 |
| Bush | 2 |
| Medion | 2 |
| Grandin | 2 |
| Emerson | 2 |

## Full inventory

```
ScreenKill inventory: 89 unique payloads from 370 Power codes
==========================================================================================

[ 1] 38000Hz  67v  NECext      14 models  brands: Amazon, AmazonBasics, Bolva, Dual, Element, Insignia, Telefunken, Toshiba, Westinghouse
[ 2] 38000Hz  67v  NEC         55 models  brands: GuestTek, Haier, Hisense, Hotels, LG, Sharp, SkyVue, Sunbrite, Vizio
[ 3] 56000Hz  35v  RCA         11 models  brands: Boulanger, EssentielB, Ffalcon, RCA, TCL, Thomson
[ 4] 38000Hz  67v  NECext       9 models  brands: Onn, Philips, RCA, Sanyo, TCL
[ 5] 38000Hz  67v  NECext       5 models  brands: Apex, Blaupunkt, Denver, Sharp
[ 6] 38000Hz  67v  NECext       8 models  brands: Dynex, Hisense, Insignia, RCA
[ 7] 38000Hz  67v  Samsung32    3 models  brands: JVC, PrismPlus, Strong
[ 8] 38000Hz  67v  NECext       2 models  brands: AWA, BBK
[ 9] 38000Hz  67v  NECext       8 models  brands: Devant, Hisense
[10] 40000Hz  27v  SIRC        27 models  brands: Sceptre, Sony
[11] 38000Hz  67v  NECext       1 models  brands: Blitzwolf
[12] 38000Hz 107v  raw          1 models  brands: Hisense
[13] 38000Hz  71v  raw          1 models  brands: Hisense
[14] 38000Hz  67v  NECext       1 models  brands: TCL
[15] 36000Hz  29v  RC5,RC6     46 models  brands: Bush, ContinentalEdison, Crown, Digihome, EdenWood, FINLUX, Gogen, Grundig, Hitachi, JVC, Kendo, Magnavox, Medion, PDi, Philips, Technika, Telefunken, Toshiba, ViewSonic, Waltham, Watson
[16] 38000Hz  67v  NEC         12 models  brands: Grandin, Kogan, Oky, Strong, Supra, Toshiba, United
[17] 38000Hz  67v  NEC          5 models  brands: Elements, Erisson, Furrion, RCA, Sankey
[18] 38000Hz  67v  NEC          4 models  brands: Baird, Cranker, Sweex, Westinghouse
[19] 38000Hz  67v  NECext       4 models  brands: ContinentalEdison, Elitelux, Platinum, Telefunken
[20] 38000Hz  67v  NECext       3 models  brands: ContinentalEdison, GVA, Viano
[21] 38000Hz  67v  NECext       3 models  brands: Akai, Bauhn
[22] 38000Hz  67v  NEC          2 models  brands: ContinentalEdison, Sencor
[23] 38000Hz  67v  NECext       2 models  brands: DYON, Wbox
[24] 38000Hz  67v  NECext       3 models  brands: Emerson, Funai
[25] 38000Hz  67v  NECext       2 models  brands: Emerson, Magnavox
[26] 38000Hz  67v  NECext       2 models  brands: Hotels, LG
[27] 38000Hz  67v  NEC          3 models  brands: Manta, RCA
[28] 38000Hz  67v  Samsung32   36 models  brands: Samsung, Viore
[29] 38000Hz  67v  NEC          1 models  brands: Android
[30] 38000Hz  67v  NECext       1 models  brands: BGH
[31] 38000Hz  75v  raw          1 models  brands: Brandt
[32] 38000Hz  67v  raw          1 models  brands: Brandt
[33] 38000Hz  67v  NEC          1 models  brands: Bush
[34] 38000Hz  67v  NEC          1 models  brands: CCE
[35] 38000Hz  67v  NEC          1 models  brands: Daewoo
[36] 38000Hz  67v  NEC          2 models  brands: Enseo
[37] 38000Hz  67v  NECext       1 models  brands: Fetch
[38] 38000Hz 255v  raw          1 models  brands: GPX
[39] 38000Hz  67v  NEC          1 models  brands: Gigabyte
[40] 38000Hz  67v  NEC          1 models  brands: Grandin
[41] 38000Hz  71v  raw          1 models  brands: Grundig
[42] 38000Hz 167v  raw          1 models  brands: Grundig
[43] 38000Hz  47v  raw          1 models  brands: Grundig
[44] 38000Hz  83v  raw          1 models  brands: Grundig
[45] 38000Hz  63v  raw          1 models  brands: Grundig
[46] 38000Hz  67v  NEC          1 models  brands: Hitachi
[47] 38000Hz  67v  NEC          1 models  brands: Hitachi
[48] 38000Hz  69v  raw          1 models  brands: JVC
[49] 38000Hz  67v  NECext       1 models  brands: Kraft
[50] 38000Hz  67v  NECext       1 models  brands: LG
[51] 38000Hz  67v  NECext       1 models  brands: LodgeNet
[52] 38000Hz  67v  NECext       1 models  brands: Magnavox
[53] 38000Hz  67v  NECext       1 models  brands: Manta
[54] 38000Hz  67v  NEC          1 models  brands: Medion
[55] 38000Hz  67v  NECext       1 models  brands: Mivar
[56] 38000Hz 189v  raw          1 models  brands: NEC
[57] 38000Hz  67v  NEC          1 models  brands: NEC
[58] 37000Hz  99v  Kaseikyo    19 models  brands: Panasonic
[59] 38000Hz  67v  Samsung32    1 models  brands: Panasonic
[60] 38000Hz  67v  NECext       1 models  brands: Philips
[61] 40000Hz  67v  Pioneer      1 models  brands: Pioneer
[62] 38000Hz 155v  raw          1 models  brands: RCA
[63] 38000Hz 135v  raw          1 models  brands: RCA
[64] 38000Hz  67v  Samsung32   13 models  brands: Samsung
[65] 38000Hz 303v  raw          1 models  brands: Samsung
[66] 38000Hz 129v  raw          1 models  brands: Samsung
[67] 38000Hz  67v  NEC          3 models  brands: Sanyo
[68] 38000Hz  64v  raw          1 models  brands: Sharp
[69] 38000Hz  99v  raw          1 models  brands: Sharp
[70] 38000Hz  95v  raw          1 models  brands: Sharp
[71] 38000Hz 127v  raw          1 models  brands: Sharp
[72] 38000Hz 159v  raw          1 models  brands: Sharp
[73] 38000Hz  67v  NEC          1 models  brands: Sharp
[74] 38000Hz 223v  raw          1 models  brands: Sharp
[75] 38000Hz  67v  NECext       1 models  brands: Silver
[76] 38000Hz  67v  NECext       3 models  brands: Soniq
[77] 38000Hz  67v  NECext       1 models  brands: Soniq
[78] 40000Hz  27v  SIRC         1 models  brands: Sony
[79] 38000Hz  67v  NEC          1 models  brands: Strong
[80] 38000Hz  67v  NEC          1 models  brands: Strong
[81] 36700Hz  52v  raw          1 models  brands: Symphonic
[82] 38000Hz  67v  NECext       1 models  brands: Syntax-Brillian
[83] 38000Hz  25v  raw          1 models  brands: Telekom
[84] 38000Hz  67v  NEC          1 models  brands: Tevion
[85] 38000Hz  67v  NECext       1 models  brands: Vitec
[86] 38000Hz  71v  raw          2 models  brands: Vizio
[87] 38000Hz  79v  raw          1 models  brands: Vizio
[88] 38000Hz  33v  raw          1 models  brands: Zenith
[89] 38000Hz  33v  raw          1 models  brands: Zenith

```