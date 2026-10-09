---
title: Overview
description: JSBSim ၏ formulation process ခြုံငုံသုံးသပ်ချက်။
---

# Overview

ပျံသန်းနေသော vehicle တစ်ခု၏ equations of motion ကို derivative များအတွက် ရှင်းလင်းစွာ ဖြေရှင်းထားသော simultaneous first-order differential equation အစုတစ်ခုအဖြစ် စီစဉ်နိုင်ပါသည်။ (position, velocity စသည်၏ component များကဲ့သို့) independent variable $n$ ခု ဖြစ်သော $x_i$ နှင့် (throttle, control surface deflection စသည်ကဲ့သို့) control input $m$ ခု ဖြစ်သော $u_i$ တို့အတွက်၊ ယေဘုယျ form မှာ အောက်ပါအတိုင်း ဖြစ်ပါလိမ့်မည်-

$$
\left\{
  \begin{array}{rl}
    \dot{x}_1 & {}= f_1\big( x_1\,,\, x_2\,,\, \ldots \,,\,x_n\,,\,u_1\,,\, u_2\,,\, \ldots \,,\,u_m \big) \\
    \dot{x}_2 & {}= f_2\big( x_1\,,\, x_2\,,\, \ldots \,,\,x_n\,,\,u_1\,,\, u_2\,,\, \ldots \,,\,u_m \big) \\
      \cdots  & \quad \cdots \\
    \dot{x}_n & {}= f_n\big( x_1\,,\, x_2\,,\, \ldots \,,\,x_n\,,\,u_1\,,\, u_2\,,\, \ldots \,,\,u_m \big)
  \end{array}
\right.
\label{eq:EoM:ODE}
$$

ဤနေရာတွင် function $f_i$ များသည် vehicle ၏ actual subsystem များကို model ပြုလုပ်ရာမှ ထွက်ပေါ်လာသော nonlinear function များ ဖြစ်ပါသည်။ Variable $x_i$ များသည် ပေးထားသော input $u_i$ များနှင့်အတူ system ၏ အမူအကျင့်ကို အပြည့်အစုံ ဖော်ပြနိုင်သော (ဆိုလိုသည်မှာ အချိန်နှင့်အမျှ ၎င်း၏ evolution ကို deterministic အနေဖြင့် တွက်ချက်နိုင်သော) variable အစုအနိမ့်ဆုံးကို ဖွဲ့စည်းပြီး system အတွက် *state variable အစု* ဟု ခေါ်ပါသည်၊ ထို့ပြင် Equation ($\ref{eq:EoM:ODE}$) သည် system ၏ *state-space* ဖော်ပြချက်တစ်ခု ဖြစ်ပါသည်။ Function $f_i$ များသည် single-valued continuous function များ ဖြစ်ပါသည်။ Equation ($\ref{eq:EoM:ODE}$) ကို မကြာခဏ symbol ဖြင့် အောက်ပါအတိုင်း ရေးလေ့ရှိပါသည်-

$$
\dot{\boldsymbol{x}} = \boldsymbol{f}\big( \boldsymbol{x}\,,\,\boldsymbol{u} \big)
\label{eq:EoM:ODE:Compact}
$$

ဤနေရာတွင် state vector $\boldsymbol{x}$ သည် state variable $n$ ခု၏ $n \times 1$ column array ဖြစ်ပြီး၊ control vector $\boldsymbol{u}$ သည် control variable များ၏ $m \times 1$ column array ဖြစ်ကာ၊ $\boldsymbol{f}$ သည် nonlinear function array တစ်ခု ဖြစ်ပါသည်။

$\boldsymbol{u}$ ကို ပုံသေ ထားသည့်အခါ၊ nonlinear state equation ($\ref{eq:EoM:ODE}$) များ (သို့မဟုတ် ၎င်း၏ subset တစ်ခု) သည် ပုံမှန်အားဖြင့် multidimensional state နှင့် control space ထဲတွင် ပေးထားသော state variable derivative အစုတစ်ခု သုညဖြစ်သွားသော (ပုံမှန်အားဖြင့် translational သို့မဟုတ် angular acceleration ဟု အဓိပ္ပာယ်ရှိသော derivative များ) *equilibrium point* တစ်ခု သို့မဟုတ် တစ်ခုထက်ပို ရှိလေ့ရှိပါသည်။

State-space formulation ၏ အဓိက အားသာချက်တစ်ခုမှာ nonlinear state equation များကို numerically ဖြေရှင်းနိုင်ခြင်း ဖြစ်ပါသည်။ အရိုးရှင်းဆုံး numerical solution method မှာ Euler integration ဖြစ်ပြီး အောက်ပါအတိုင်း ဖော်ပြထားပါသည်-

$$
\boldsymbol{x}(t_{k+1}) = \boldsymbol{x}(t_k) + \boldsymbol{f}\big( \boldsymbol{x}_k\,,\,\boldsymbol{u}_k \big) \, \Delta t
\label{eq:EoM:ODE:Euler:Integration}
$$

ဤနေရာတွင် $\boldsymbol{x}(t_k)$ သည် သတ်မှတ်ထားသော initial condition $\boldsymbol{x}(t_0) = \boldsymbol{x}_0$ မှ စတင်ကာ $k = 0,1,2, \ldots$ ဖြင့် discrete time $t_k = k \Delta t$ တွင် တွက်ချက်ထားသော state vector ၏ value ဖြစ်ပါသည်။ Integration time step $\Delta t$ ကို $\Delta t$ interval တစ်ခုစီအတွက် $\boldsymbol{u}$ ကို ပုံသေ value $\boldsymbol{u}(t_k)$ ဖြင့် approximate ပြုလုပ်နိုင်ပြီး $\dot{\boldsymbol{x}} \Delta t$ သည် state vector ၏ increment ကို ကောင်းမွန်စွာ approximate ပြုလုပ်ပေးနိုင်လောက်အောင် သေးငယ်အောင် ပြုလုပ်ရပါမည်။ ဤ numerical integration က state vector ကို $\Delta t$ time increment များဖြင့် ရှေ့ဆက်တိုးစေကာ *time-history simulation* တစ်ခု ရရှိစေပါသည်။

---

ဖြည့်စွက်ရန် ကျန်ရှိနေသည် (TBD)
