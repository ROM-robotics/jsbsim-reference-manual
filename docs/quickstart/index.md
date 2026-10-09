---
title: အမြန်စတင်ရန်
description: JSBSim ကို အသုံးပြုစတင်ရန်။
tags:
  - quickstart
---

# အမြန်စတင်ရန်

JSBSim ကို အကျိုးရှိစွာ အသုံးပြုရန်အတွက် *programmer တစ်ဦး၏ သဘောထား* ကို ယူဆထားသင့်ပါသည်။ ဆိုလိုသည်မှာ သင်ကိုယ်တိုင် source code များကို download လုပ်ပြီး သင့် platform ပေါ်တွင် compile လုပ်ရမည် ဖြစ်ပါသည်။ သင့်ကွန်ပျူတာတွင် သင့်လျော်သော tool များ install လုပ်ထားလျှင် ၎င်းသည် မလွယ်ကူသော လုပ်ငန်းစဉ်တစ်ခု မဟုတ်ပါ။

စိတ်မရှည်သူများအတွက်၊ library ၏ နောက်ဆုံးထွက် binary များကို ပေးပို့သည့် အလိုအလျောက် remote build procedure များ ရှိပါသည်။ ၎င်းတို့ကို အောက်ပါ လင့်များတွင် ရှာတွေ့နိုင်ပါသည်-

## FlightGear project developer များမှ ပံ့ပိုးထားသော build များ ([Jenkins server](https://jenkins.io/))

- [Linux အတွက် JSBSim build (Linux CentOS 7 VM)](http://build.flightgear.org:8080/job/JSBsim)

  Workspace area [build.flightgear.org:8080/job/JSBSim/ws](http://build.flightgear.org:8080/job/JSBSim/ws/) သို့ သွားပြီး ဖိုင်အားလုံးကို [Zip archive](http://build.flightgear.org:8080/job/JSBSim/ws/*zip*/JSBsim.zip) အဖြစ် download လုပ်ပါ။ Archive ကို ဖွင့်ကြည့်ပြီး `/JSBSim/build/src/` folder သို့ သွားပါ။ ထို့နောက် executable file `JSBSim` နှင့် static library file `libJSBSim.a` ကို ရှာပါ။

- [Windows အတွက် JSBSim build](http://build.flightgear.org:8080/job/JSBsim-win)

Workspace area [build.flightgear.org:8080/job/JSBSim-win/ws](http://build.flightgear.org:8080/job/JSBSim-win/ws/) သို့ သွားပြီး ဖိုင်အားလုံးကို [Zip archive](http://build.flightgear.org:8080/job/JSBSim-win/ws/*zip*/JSBSim-win.zip) အဖြစ် download လုပ်ပါ။ Archive ကို ဖွင့်ကြည့်ပြီး `/JSBSim-win/build/src/Debug/` folder သို့ သွားပါ။ ထို့နောက် executable file `JSBSim.exe` နှင့် static library file `JSBSim.lib` ကို ရှာပါ။

JSBSim ၏ pre-compiled binary များကို ပေးအပ်ရန် ဤကြိုးပမ်းမှုသည် [FlightGear](https://www.flightgear.org/) project အတွက် [continuous integration and delivery service](http://build.flightgear.org:8080/) ၏ တစ်စိတ်တစ်ပိုင်း ဖြစ်ပါသည်။ Jenkins ဖြင့် continuous integration အကြောင်း ပိုမိုလေ့လာလိုပါက [ဤလင့်ကို ကြည့်ပါ](https://wiki.jenkins.io/display/JENKINS/Meet+Jenkins)။

## JSBSim-Team မှ ပံ့ပိုးထားသော build များ ([Travis server](https://travis-ci.org/) နှင့် [AppVeyor server](https://www.appveyor.com/))

JSBSim-Team သည် Ubuntu 14.04.5 LTS (Trusty Tahr) နှင့် MS Windows နှစ်ခုစလုံးအတွက် x64 binary များကို ပေးအပ်သော ၎င်း၏ကိုယ်ပိုင် Continuous Integration service ကို ပံ့ပိုးပေးပါသည်။ ထွက်ရှိမှုများကို `v2018a` (သို့မဟုတ် ပိုနောက်ပိုင်း) ဟု tag တပ်ထားပြီး [GitHub repository ၏ Releases section မှ](https://github.com/JSBSim-Team/jsbsim/releases) download လုပ်နိုင်ပါသည်။

နောက်ဆုံးထွက် build များ၏ လက်ရှိအခြေအနေကို စစ်ဆေးလိုပါက အောက်ပါ လင့်များသို့ သွားနိုင်ပါသည်-

- [Ubuntu အတွက် Travis build](https://travis-ci.org/JSBSim-Team/jsbsim) (Python 2.7 နှင့် 3.6 နှစ်မျိုးစလုံးဖြင့် test များ ပါဝင်သည်) [![Travis CI](https://travis-ci.org/JSBSim-Team/jsbsim.svg?branch=master)](https://travis-ci.org/JSBSim-Team/jsbsim)

- [Windows အတွက် AppVeyor build](https://ci.appveyor.com/project/agodemar/jsbsim/branch/master) (test မပါ) [![Build status](https://ci.appveyor.com/api/projects/status/89wkiqja63kc6h2v/branch/master?svg=true)](https://ci.appveyor.com/project/agodemar/jsbsim/branch/master)

<figure markdown>
  ![Placeholder image](../assets/img/ac_sideview_climb_simplified.svg){: .center width="80%" }
  <figcaption>
	ဒီတော့၊ ဒီလေယာဉ်ရဲ့ ပျံသန်းမှုကို simulate လုပ်ချင်ပါသလား။
  </figcaption>
</figure>
