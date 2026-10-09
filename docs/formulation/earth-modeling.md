---
title: Earth modeling
description: JSBSim က ကမ္ဘာဂြိုဟ်ကို မည်သို့ model ပြုလုပ်သည်။
---

# Earth Modelling (ကမ္ဘာ့ပြင် Model ပြုလုပ်ခြင်း)

ဖြည့်စွက်ရန် ကျန်ရှိနေသည် (TBD)

## Longitude သတ်မှတ်ချက်များ

ဖြည့်စွက်ရန် ကျန်ရှိနေသည် (TBD)

## Point တစ်ခု၏ Geocentric Coordinate များ

ဖြည့်စွက်ရန် ကျန်ရှိနေသည် (TBD)

## Point တစ်ခု၏ Geodetic Coordinate များ

ဖြည့်စွက်ရန် ကျန်ရှိနေသည် (TBD)

## Curvature Radius များ

ဖြည့်စွက်ရန် ကျန်ရှိနေသည် (TBD)

## Spheroid အတွက် Trigonometric ဆက်စပ်မှုများ

ဖြည့်စွက်ရန် ကျန်ရှိနေသည် (TBD)

## Cartesian/Polar Coordinate ပြောင်းလဲမှုများ

ဖြည့်စွက်ရန် ကျန်ရှိနေသည် (TBD)

## Earth နှင့်ဆိုင်သော Coordinate ပြောင်းလဲမှုများ

ဖြည့်စွက်ရန် ကျန်ရှိနေသည် (TBD)


---

Dry air adiabatic lapse rate (DALR) သည် 1000&nbsp;ft (304.8&nbsp;m) လျှင် 3&nbsp;°C ဖြစ်ပြီး၊
100&nbsp;m လျှင် 1&nbsp;°C ဖြစ်ပါသည်။
Saturated-air adiabatic lapse rate (SALR) သည် 1000&nbsp;ft လျှင် 1.5&nbsp;°C သို့မဟုတ် 100&nbsp;m
လျှင် 0.5&nbsp;°C ဖြစ်ပါသည်။ ထို့ကြောင့်၊
$\lambda_\mathrm{SALR} = \frac{1}{2} \lambda_\mathrm{DALR}$ ဖြစ်ပါသည်။

နေရာတစ်ခုနှင့် အချိန်တစ်ခုတွင် atmospheric layer များထဲရှိ height $h$ နှင့်အတူ temperature
ပြောင်းလဲမှု နှုန်းကို ၎င်း၏ *temperature lapse rate* သို့မဟုတ် ရိုးရှင်းစွာ *lapse rate* ဟု ခေါ်ပြီး
$\lambda$ ဖြင့် ဖော်ပြပါသည်။ Height တိုးလာသည်နှင့်အမျှ temperature လျော့ကျပါက lapse rate ကို
positive ဟု ယူဆပြီး၊ ဆန့်ကျင်ဘက်လည်း ထို့အတူပင် ဖြစ်ပါသည်။

$$
\begin{equation}
\lambda = - \frac{\mathrm{d}T}{\mathrm{d}h} \label{eq:Lapse:Rate}
\end{equation}
$$
