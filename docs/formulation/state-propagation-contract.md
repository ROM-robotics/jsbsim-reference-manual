---
title: State propagation contract
description: State propagation ကို မောင်းနှင်ပေးသော JSBSim ၏ လုပ်ငန်းစဉ်။
---

# State propagation contract (State ပျံ့နှံ့မှု သဘောတူညီချက်)

## 0. အသိပေးချက်: ဤအပိုင်းသည် ဆက်လက် ဖန်တီးဆောင်ရွက်နေဆဲ ဖြစ်ပါသည်။

Vehicle ၏ state ကို အောက်ပါညီမျှခြင်းအတိုင်း ပျံ့နှံ့ (propagate) ပြုလုပ်ပါသည်-

$$
\dot{\boldsymbol{x}}(t_{k}) = \boldsymbol{f}\big( t_k, \boldsymbol{x}(t_{k}), \dot{\boldsymbol{x}}(t_{k-1}), \boldsymbol{u} \big)
$$

Simulation ကို **discrete-time integration problem** တစ်ခုအဖြစ် ဖော်ပြထားပြီး၊ ဤနေရာတွင် အချိန်ကို $t_k$ တွင် sample ယူထားပြီး $k$ သည် integer index တစ်ခု ဖြစ်ပါသည်။

## 1.1 State Vector သတ်မှတ်ချက်

Propagate ပြုလုပ်ထားသော state vector ကို အောက်ပါအတိုင်း သတ်မှတ်ထားပါသည်-

$$
\boldsymbol{x} = \big[ u, v, w,\, p, q, r,\, x_{\text{cg}}, y_{\text{cg}}, z_{\text{cg}},\, q_0, q_1, q_2, q_3,\, \text{masses},\text{inertias}\big]
$$

ဤနေရာတွင်-

- $u, v, w$: **standard body-fixed frame** ဖြင့် ဖော်ပြထားသော **ECI နှင့် ဆက်စပ်သော** CG ၏ translational velocity component များ

- $p, q, r$: **standard body-fixed frame** ဖြင့် ဖော်ပြထားသော **ECI နှင့် ဆက်စပ်သော** vehicle ၏ angular velocity component များ

- $x_{\text{cg}}, y_{\text{cg}}, z_{\text{cg}}$: **ECI frame** ဖြင့် ဖော်ပြထားသော CG ၏ position coordinate များ

- $q_0, q_1, q_2, q_3$: **ECI frame** တွင် သတ်မှတ်ထားသော vehicle ၏ attitude quaternion component များ

- $\text{masses}$: total mass၊ နှင့် vehicle ၏ sub-element များ (tank စသည်) ၏ individual mass ဖြစ်နိုင်သည်များ

- $\text{inertias}$: Body-frame ရှိ vehicle ၏ inertia matrix element ၉ ခု

## 1.2 Derivative (Dynamics) Model

Discrete time $t_k$ တစ်ခုစီတွင်၊ derivative ကို အောက်ပါအတိုင်း သတ်မှတ်ထားပါသည်-

$$
\dot{\boldsymbol{x}}(t_k) = \boldsymbol{f} \big(
   t_k, \boldsymbol{x}(t_k), \dot{\boldsymbol{x}}(t_{k-1}), \boldsymbol{u}(t_k) \big)
$$

ဤနေရာတွင်-

- $\boldsymbol{x}(t_k)$: လက်ရှိ state

- $\boldsymbol{u}(t_k)$: လက်ရှိ input များ (control, propulsion, environment စသည်)

- $\dot{\boldsymbol{x}}(t_{k-1})$: ယခင် step ၏ state derivative

- $\boldsymbol{f}(\cdot)$: EOM ၏ RHS ကို explicit form ဖြင့် ကိုယ်စားပြုသော vector-valued function။

$\dot{\boldsymbol{x}}(t_{k-1})$ ကို ထည့်သွင်းခြင်းက simulator implementation များစွာတွင် implicit ဖြစ်နေပြီးသား အရာများကို explicit ဖြစ်စေပါသည်-

- Predictor/corrector scheme များ  

- Multi-stage integrator များတွင် slope ပြန်အသုံးပြုခြင်း  

- Iterative သို့မဟုတ် stabilize ပြုလုပ်ထားသော propagation logic  

ဤ formulation က အောက်ပါတို့အကြား concept ဆိုင်ရာ edge ကို ရှင်းလင်းစေပါသည်-

- **Derivative ဖွဲ့စည်းခြင်း** ($\boldsymbol{f}$ ကို evaluate ပြုလုပ်ခြင်း)

- **Numerical integration**

## 1.3 Numerical Integration Step

State update မှာ-

$$
\boldsymbol{x}(t_{k+1}) = \boldsymbol{x}(t_k) + \int_{t_k}^{t_{k+1}} \dot{\boldsymbol{x}}(\tau)\,\mathrm{d}\tau
$$

Integral ကို `FGPropagate` အတွင်း ရွေးချယ်ထားသော integrator ကို အသုံးပြု၍ approximate ပြုလုပ်ပါသည်။
၎င်းက အောက်ပါအချက်များကို ရှင်းလင်းစွာ ဖော်ပြပါသည်-

- `FGPropagate` က numerical integration ကို လုပ်ဆောင်ပါသည်

- `FGFDMExec` က execution ordering နှင့် scheduling ကို သတ်မှတ်ပေးပါသည်

- နှစ်ခုပေါင်း၍ ODE ၏ discrete-time realization ကို implement ပြုလုပ်ပါသည်

# 2. Observation Equation (ထုတ်ဝေထားသော Output များ)

Propagation အပြင်၊ simulator သည် output များကို ထုတ်ပေးပါသည်-

$$
\boldsymbol{y}(t_k) = \boldsymbol{g}\big(
  t_k, \boldsymbol{x}(t_k), \dot{\boldsymbol{x}}(t_{k-1}), \boldsymbol{u}(t_k) \big)
$$

ဤနေရာတွင်-

- $\boldsymbol{y}(t_k)$: ထုတ်ဝေထားသော (သို့) observe လုပ်နိုင်သော output များ (aero angle, ဆင်းသက်ထားသော velocity, acceleration, navigation quantity, atmosphere value များ စသည်)

- $\boldsymbol{g}(\cdot)$: output mapping

ဤ observation equation က model execution နှင့် property publication တစ်လျှောက်လုံးတွင် ကွဲလွင့်နေသော အရာများကို formal ဖြစ်စေပါသည်။


ဖြည့်စွက်ရန် ကျန်ရှိနေသည် (TBD)
