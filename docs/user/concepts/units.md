---
title: Units
description: JSBSim's supported units of measurement.
---

# Units (တိုင်းတာမှု ယူနစ်များ)

JSBSim သည် internal calculation များအတွက် English unit ကိုသာ အဓိကအားဖြင့် အသုံးပြုပါသည်။ သို့သော်၊ configuration file တွင် parameter အချို့ကို မတူညီသော unit များဖြင့် input ထည့်နိုင်ပါသည်။ စင်စစ်အားဖြင့် ရှုပ်ထွေးမှုကို ရှောင်ရှားရန်၊ unit ကို အမြဲတမ်း သတ်မှတ်ရန် အကြံပြုပါသည်။ Unit များကို `unit` attribute ကို အသုံးပြု၍ သတ်မှတ်ပါသည်။ ဥပမာအားဖြင့်၊ wingspan (အတောင်ပံအကျယ်) အတွက် specification သည် ဤကဲ့သို့ ဖြစ်ပါသည်-

```xml
<wingspan unit="FT"> 35.8 </wingspan>
```

အထက်ပါ statement က wingspan ကို ပေ ၃၅.၈ ပေ (35.8 feet) ဟု သတ်မှတ်ပါသည်။ Wingspan ကို မီတာဖြင့် သတ်မှတ်သော အောက်ပါ statement သည် ဖတ်ရှုစဉ်တွင် ပေ ၃၅.၈ ပေသို့ ပြောင်းလဲသွားမည် ဖြစ်ပါသည်-

```xml
<wingspan unit="M"> 10.91 </wingspan>
```

Wingspan အတွက် statement နှစ်ခုစလုံးသည် အကျိုးသက်ရောက်မှုအားဖြင့် တူညီကြပါသည်။

လက်ရှိ JSBSim တွင် support လုပ်ထားသော unit များမှာ အောက်ပါအတိုင်း ဖြစ်ပါသည်-

**အရှည် (Length)**

| `unit=`  | unit   |
| ---:     | :---   |
| `FT`     | ft     |
| `IN`     | in     |
| `M`      | m      |
| `KM`     | km     |

**ဧရိယာ (Area)**

| `unit=`  | unit   |
| ---:     | :---   |
| `M2`     | m²     |
| `FT2`    | ft²    |

**ပမာဏ (Volume)**

| `unit=`  | unit   |
| ---:     | :---   |
| `FT3`    | ft³    |
| `CC`     | cm³    |
| `M3`     | m³     |
| `LTR`    | l      |

**အလေးချိန်နှင့် ဝန် (Mass and Weight)**

| `unit=`  | unit   |
| ---:     | :---   |
| `LBS`    | lbm    |
| `KG`     | kg     |

**လှည့်တုံ့ဆွဲမှု (Moments of Inertia)**

| `unit=`    | unit   |
| ---:       | :---   |
| `SLUG*FT2` | slug ft² |
| `KG*M2`    | kg m²  |

**ထောင့် (Angles)**

| `unit=`    | unit   |
| ---:       | :---   |
| `RAD`      | rad    |
| `DEG`      | deg    |

**စပရင်အားအင် (Spring Force)**

| `unit=`    | unit   |
| ---:       | :---   |
| `N/M`      | N/m    |
| `LBS/FT`   | lb/ft  |

**တုန်ခါမှု ထိန်းချုပ်အားအင် (Damping Force)**

| `unit=`    | unit   |
| ---:       | :---   |
| `N/M/SEC`  | N/(m s) |
| `LBS/FT/SEC` | lb/(ft s) |

**စွမ်းအား (Power)**

| `unit=`    | unit   |
| ---:       | :---   |
| `WATTS`    | W      |
| `HP`       | Hp     |

**အားအင် (Force)**

| `unit=`    | unit   |
| ---:       | :---   |
| `LBS`      | lb     |
| `N `       | N      |

**အလျင် (Velocity)**

| `unit=`    | unit   |
| ---:       | :---   |
| `KTS`      | kts    |
| `FT/SEC`   | ft/s   |
| `M/S`      | m/s    |

**လှည့်အားအင် (Torque)**

| `unit=`    | unit   |
| ---:       | :---   |
| `N*M`      | N m    |
| `FT*LBS`   | lb ft  |

**ဖိအား (Pressure)**

| `unit=`    | unit   |
| ---:       | :---   |
| `PSF`      | lb/ft² |
| `PSI`      | lb/in² |
| `ATM`      | atm    |
| `PA`       | N/m²   |
| `INHG`     | in HG  |
