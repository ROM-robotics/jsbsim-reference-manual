---
title: Equations of motion
description: JSBSim က equations of motion ကို မည်သို့ ဖော်ပြသည်။
---

# Equations of motion (ရွေ့လျားမှု ညီမျှခြင်းများ)

Flight dynamics model တစ်ခု၏ core ရည်ရွယ်ချက်မှာ vehicle အပေါ် သက်ရောက်နေသော force နှင့် moment များကို ပေးထားသောအခါ၊ ကမ္ဘာ (သို့မဟုတ် ဂြိုဟ်တစ်ခုခု) ၏ surface ပေါ်မှ ပျံသန်းနေသော craft တစ်ခု၏ path ကို propagate ပြုလုပ်ပြီး track လိုက်ရန် ဖြစ်ပါသည်။ ကျွန်ုပ်တို့သည် လေယာဉ်၏ characteristic များကို သိရှိထားပြီး၊ ဂြိုဟ် (gravity, rotation rate စသည်) ၏ characteristic များကိုလည်း သိရှိထားပါသည်။ Reader သည် moving reference frame များ ပါဝင်သော rigid body dynamics ကို ကျွမ်းကျင်ထားပြီးသားဟု မျှော်လင့်ထားပါသည်။ သို့သော်လည်း၊ ဤအချက်အလက်အားလုံးကို flight simulator တစ်ခုထဲတွင် စုစည်းတည်ဆောက်ခြင်းသည် ဒုနှင့်ဒေးဖြစ်ပြီး ပင်ပန်းစေနိုင်ပါသည်။

ဤအပိုင်းတွင် JSBSim က ပေးအပ်ထားသော quaternion, matrix, vector, နှင့် location math class များကို အသုံးပြု၍ `JSBSim::FGPropagate` တွင် implement ပြုလုပ်ထားသည့်အတိုင်း aerospace vehicle equations of motion ကို ဆွေးနွေးထားပါသည်။ Rigid body equations of motion နှင့် ဆက်စပ်သော အောက်ပါအပိုင်းများတွင် ဖော်ပြထားသော equation အများစုကို JSBSim software ၏ အဓိက formulation reference ဟု ယူဆထားသော **(Stevens:Lewis:Johnson:2015)** စာအုပ်မှ ကိုးကားထားပါသည်။

ဤ reference manual တွင် အသုံးပြုထားသော notation သည် Stevens နှင့် Lewis အသုံးပြုသည့်အတိုင်း ဖြစ်ပါသည်-

- Lower right subscript၊ ဥပမာအားဖြင့် $\boldsymbol{v}_\mathrm{CM/e}$ သည် parameter ၏ object သို့မဟုတ် frame ဆက်နွယ်မှုကို ဖော်ပြပါသည်။
  ပေးထားသော ဥပမာတွင်၊ $\boldsymbol{v}_\mathrm{CM/e}$ သည် ECEF frame နှင့် ဆက်စပ်သော CM (center of mass) ၏ velocity ကို ရည်ညွှန်းပါသည်။

- Upper right superscript၊ ဥပမာအားဖြင့် $\boldsymbol{v}^\mathrm{b}$ သည် coordinate system တစ်ခုကို ရည်ညွှန်းပါသည်။
  ဆိုလိုသည်မှာ motion ကို မည်သည့် coordinate system တွင် ဖော်ပြထားသည်ကို ဖော်ပြပါသည်။

- Left superscript သည် derivative တစ်ခု ယူထားသော frame ကို သတ်မှတ်ပေးပါသည်။

**ဆက်လက် ဖြည့်စွက်ရန်**

<figure markdown>
  ![Inertial frame](../assets/img/inertial_frame.png){: .center width="60%" }
  <figcaption>
    Earth-Centered Inertial (ECI) frame နှင့် Earth-Centered Earth-Fixed (ECEF) frame။
  </figcaption>
</figure>

<figure markdown>
  ![Earth frames](../assets/img/earth_frames.png){: .center width="60%" }
  <figcaption>
    Earth-Centered Earth-Fixed (ECEF) frame, geographic coordinate များ, Tangent (T) frame, နှင့် local Vertical (V) frame။
  </figcaption>
</figure>

<figure markdown>
  ![Angular velocity vector](../assets/img/ac_pqr_omega.svg){: .center width="90%" }
  <p markdown="span">
    လေယာဉ် angular velocity vector $\boldsymbol{\Omega}$ နှင့် body axis $(p,q,r)$ ရှိ angular speed component များ။
  </p>
</figure>

<figure markdown>
  ![Ground reaction model](../assets/img/c172_ground_reaction_model.svg){: .center width="90%" }
  <p markdown="span">
    Ground reaction model။ Main gear ၏ right wheel အတွက် $\mathrm{WOW} = 1$ နှင့် nose wheel အတွက် $\mathrm{WOW} = 0$ ဖြစ်နေသော ground contact အခြေအနေတစ်ခု။
  </p>
</figure>

