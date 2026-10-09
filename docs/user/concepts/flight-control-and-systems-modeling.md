---
title: Flight Control and System Modelling
description: Modeling flight controls and systems with JSBSim.
---

# Flight Control and System Modelling (ထိန်းချုပ်မှုစနစ်နှင့် System Model ပြုလုပ်ခြင်း)

လေယာဉ်တစ်စင်းကို ယေဘုယျ dynamical system တစ်ခုအဖြစ် ယူဆပါက၊ ၎င်းသည် control input vector $\boldsymbol{u}$ တစ်ခု၏ သက်ရောက်မှုကို ခံစားရပါသည်။ Input အရေအတွက်နှင့် အမျိုးအစားများသည် သုံးသပ်နေသည့် လေယာဉ်အမျိုးအစားပေါ် မူတည်နိုင်ပါသည်။ ပုံမှန် configuration ရှိသော လေယာဉ်တစ်စင်းအတွက်၊ input အနည်းဆုံး အစီအစဉ်ကို ပုံမှန်အားဖြင့် ဤကဲ့သို့ ပေးလေ့ရှိပါသည်-

\begin{equation}
\boldsymbol{u} = \big[ \,
\delta_\mathrm{T}, \, \delta_\mathrm{a}, \, \delta_\mathrm{e}, \, \delta_\mathrm{r}
\,\big]
\label{eq:Control:Inputs}
\end{equation}

ဤနေရာတွင် $\delta_\mathrm{T}$ သည် throttle setting ဖြစ်ပြီး $\delta_\mathrm{a}$, $\delta_\mathrm{e}$, နှင့် $\delta_\mathrm{r}$ တို့မှာ အသီးသီး right aileron, elevator, နှင့် rudder တို့၏ angular deflection များ ဖြစ်ပါသည်။ ဤ quantity များသည် standard sign ရှိကြပြီး၊ ၎င်းတို့၏ range သည် သီးခြား လေယာဉ် design အလိုက် ကွဲပြားနိုင်ပါသည်။ Flight simulation practice တွင်၊ ၎င်းတို့၏ ပြောင်းလဲမှုသည် cockpit ရှိ သက်ဆိုင်ရာ control တစ်ခု၏ normalized setting နှင့် ဆက်စပ်ပါသည်။

ပုံမှန်အားဖြင့် throttle setting ၏ range သည် 0 (idle) မှ $+1$ (maximum power) အထိ ရှိပါသည်။ Concept အရ $\delta_\mathrm{T}$ ကို လက်ရှိ flight speed နှင့် altitude တွင် ရရှိနိုင်သော maximum thrust output ၏ လက်ရှိ fraction ဟု ယူဆနိုင်ပါသည်။

Stick excursion များအားလုံးကို $−1$ မှ $+1$ အထိ range တစ်ခုသို့ map လုပ်ထားပါသည်။

ဤ mapping များသည် pilot action ၏ နောက်ဆုံး effect ကို actual effector deflection နှင့် thrust output အပေါ် ပြောင်းလဲနိုင်သော control law ရှိမရှိပေါ် မကြာခဏ မူတည်ပါသည်။

သင်္ချာအရ ပြောရလျှင်၊ actual aerosurface deflection နှင့် thrust output ကို ယူဆသည်ဖြစ်စေ၊ normalized command range ကို ယူဆသည်ဖြစ်စေ၊ ၎င်းတို့ကို control variable vector $\boldsymbol{u}$ အတွက် bound အစုတစ်ခုအဖြစ် ရှုမြင်ပါသည်။

Control input အရေအတွက်နှင့် အမျိုးအစားများသည် ယူဆထားသော လေယာဉ်တစ်စင်း၏ feature တစ်ခု ဖြစ်ကြောင်း ထပ်ခါထပ်ခါ မီးမောင်းထိုးပြရန် လိုအပ်ပါသည်။ Category ကျယ်ကျယ်ပြန့်ပြန့် တူညီသော်လည်း၊ လေယာဉ် design နှစ်ခုသည် control အစီအစဉ်နှင့် အရေအတွက် သိသိသာသာ ကွဲပြားနိုင်ပါသည်။ သို့သော်လည်း ယေဘုယျအားဖြင့်၊ အနည်းဆုံး ၎င်းတို့၏ 'main' control များမှာ concept အရ တူညီကြပါသည်- Aileron တစ်စုံ၊ main longitudinal control တစ်ခု၊ ဆိုလိုသည်မှာ symmetrical အနေအထားဖြင့် ရွေ့လျားသော elevator တစ်စုံ၊ နှင့် rudder တစ်ခု တို့ ဖြစ်ပါသည်။ Case များစွာတွင် horizontal empennage များသည် fuselage reference line နှင့် ဆက်စပ်သော variable rigging angle တစ်ခု ရှိကြပြီး၊ flight mechanics စာအုပ်အများစုတွင် $i_\mathrm{H}$ ထောင့် ဟု သိကြပါသည်။

## Conventions (ဓလေ့ထုံးတမ်းများ)

<figure markdown>
  ![Aerosurface deflections](../../assets/img/ac_aerosurface_deflections.svg){: .center width="80%" }
  <figcaption>
    Standard လေယာဉ် aerodynamic control surface များ။
  </figcaption>
</figure>

## Aerodynamic Modelling အကြောင်း ခြုံငုံသုံးသပ်ချက်

Linearized pitch coefficient-

\begin{equation}
C_m = C_{m0} + C_{m\alpha} \, \alpha_\mathrm{B} + C_{m\delta_\mathrm{e}} \delta_\mathrm{e} + C_{m i_\mathrm{H}} \, i_\mathrm{H} + \left( C_{mq} \, q + C_{m\dot{\alpha}} \, \dot{\alpha}_\mathrm{B}\right) \frac{\bar{c}}{2V}
\label{eq:Cm}
\end{equation}

<figure markdown>
  ![Alpha and beta](../../assets/img/c172_fcs.svg){: .center width="100%" }
  <p markdown="span">
	c172p model တွင် elevator channel ၏ command-to-deflection logic။ Yoke movement နှင့် pitch trim lever regulation ၏ ပေါင်းစပ်မှုကို normalize လုပ်ပြီး interval $[−1, 1]$ သို့ map လုပ်ထားပါသည်။ Channel ၏ output သည် real variable fcs/elevator-pos-rad ဖြစ်ပြီး equivalent elevator deflection $\delta_\mathrm{e}^\star = \delta_\mathrm{e} + \delta_\mathrm{e,tab}^\star$ ကို ကိုယ်စားပြုပါသည်။ ထောင့် $\delta_\mathrm{e,tab}^\star$ သည် actual tab angle $\delta_\mathrm{e,tab}$ နှင့် equivalent ဖြစ်သော elevator deflection တစ်ခု ဖြစ်ပါသည်။ $\delta_\mathrm{e}$ သည် $[\delta_\mathrm{e,min}, \delta_\mathrm{e,max}]$ range အတွင်း ပြောင်းလဲပါသည်။ Tail ကို equivalent condition (အပေါ်ဘက်) နှင့် actual condition (အောက်ဘက်) နှစ်မျိုးစလုံးတွင် ရွေ့လျားနေသော surface များ deflect ဖြစ်နေသည့်အတိုင်း ကိုယ်စားပြုထားပါသည်။
  </p>
</figure>

## Propulsion Modelling အကြောင်း ခြုံငုံသုံးသပ်ချက်

<figure markdown>
  ![Thrust thruster](../../assets/img/ac_thrust_definitions.svg){: .center width="80%" }
  <figcaption>
	Engine နှစ်လုံးပါ propeller လေယာဉ်တစ်စင်း။ Body frame တွင် engine thruster ၏ တည်နေရာ၊ thrust application point၊ နှင့် thrust vector orientation။
  </figcaption>
</figure>

<figure markdown>
  ![Thruster locations](../../assets/img/c172_thruster.svg){: .center width="80%" }
  <figcaption>
	c172p ၏ FDM တွင် 'thruster' နှင့် 'tank' entity များနှင့် သက်ဆိုင်သော တည်နေရာများ။
  </figcaption>
</figure>

