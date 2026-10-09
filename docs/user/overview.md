---
title: Overview
description: JSBSim User Manual overview.
---

# Overview

## JSBSim ဆိုတာ တကယ်တော့ ဘာလဲ?

Application programming ရှုထောင့်မှ ကြည့်ပါက၊ JSBSim သည် အများစုအားဖြင့် C++ programming language ဖြင့် ရေးသားထားသော program code အစုအဝေးတစ်ခု ဖြစ်ပါသည် (သို့သော် C language routine အချို့ကိုလည်း ထည့်သွင်းထားပါသည်)။ JSBSim ကို ဖွဲ့စည်းသော C++ class အချို့သည် atmosphere, flight control system, သို့မဟုတ် engine ကဲ့သို့ ရုပ်ပိုင်းဆိုင်ရာ entity များကို model ပြုလုပ်ပါသည်။ Class အချို့သည် equations of motion, matrix, quaternion, သို့မဟုတ် vector ကဲ့သို့သော concept များ သို့မဟုတ် mathematical construct များကို encapsulate လုပ်ပါသည်။ Class အချို့ကလည်း object အခြားများ၏ collection များကို management လုပ်ပါသည်။ အားလုံးစုစည်းကြည့်ပါက၊ JSBSim application သည် control input များကို ယူပြီး၊ ထို control input များနှင့် environment မှ ထွက်ပေါ်လာသော force နှင့် moment များကို တွက်ချက်ပေါင်းစည်းကာ၊ vehicle ၏ state (velocity, orientation, position စသည်) ကို discrete time step များဖြင့် ရှေ့ဆက်တိုးစေပါသည်။

JSBSim ကို Windows သို့မဟုတ် Linux run သော PC၊ Apple Macintosh၊ နှင့် Silicon Graphics ၏ IRIX operating system ကဲ့သို့ platform အမျိုးမျိုးပေါ်တွင် build လုပ်ပြီး run ထားပါသည်။ အခမဲ့ GNU g++ compiler က JSBSim ကို လွယ်ကူစွာ compile လုပ်ပေးပြီး၊ Borland နှင့် Microsoft ကဲ့သို့ compiler အခြားများကလည်း ကောင်းမွန်စွာ အလုပ်လုပ်ပါသည်။ ပိုမို အချက်အလက်များအတွက် Programmers Guide ကို ကြည့်ပါ။

End-user (သုတေသန ပြုလုပ်နေသော ကျောင်းသားတစ်ဦး ဖြစ်နိုင်သည်) ရှုထောင့်မှ ကြည့်ပါက၊ JSBSim ကို XML format ဖြင့် input file များ ပေးထားသော တစ်မျိုးအားဖြင့် “black box” တစ်ခုအဖြစ် ရှုမြင်နိုင်ပါသည်။ ဤ XML file များတွင် aerospace vehicle, engine, script စသည်တို့၏ ဖော်ပြချက်များ ပါဝင်ပါသည်။ ဤ file များကို JSBSim ထဲသို့ load လုပ်သည့်အခါ၊ ၎င်းတို့က JSBSim ကို ထို vehicle ၏ flight ကို (FlightGear သို့မဟုတ် OpenEaagles ကဲ့သို့) ပိုကြီးသော simulation framework တစ်ခု၏ တစ်စိတ်တစ်ပိုင်းအဖြစ် real-time တွင် model လုပ်ရန် သို့မဟုတ် batch mode တစ်ခုတွင် real-time ထက် ပိုမြန်စွာ model လုပ်ရန် ညွှန်ကြားပါသည်။ JSBSim ၏ run တစ်ခုချင်းစီသည် simulate ပြုလုပ်ပြီး လေ့လာနေသော vehicle ၏ performance နှင့် dynamics ကို ပြသသော data file များ ထွက်ပေါ်လာစေပါမည်။

Software integrator (ဥပမာ JSBSim ကို ပိုကြီးသော simulation framework တစ်ခုထဲသို့ ပေါင်းစပ်နေသူတစ်ဦး) ရှုထောင့်မှ ကြည့်ပါက၊ JSBSim သည် call လုပ်နိုင်သော library တစ်ခု ဖြစ်ပြီး၊ (pilot မှ control input များကဲ့သို့) input များ ပေးထားကာ၊ (vehicle သည် အချိန်မည်သည့်အချိန်တွင်မဆို မည်သည့်နေရာတွင် ရှိသည်ကို ဖော်ပြသော) output များ ပြန်လည် ထုတ်ပေးပါသည်။

## ဘယ်သူတွေအတွက် ဖြစ်ပြီး ဘယ်လို အသုံးပြုနိုင်သလဲ?

JSBSim flight dynamics model (FDM) software library သည် သင့်တင့်လျောက်ပတ်စွာ နားလည်လွယ်အောင် ရည်ရွယ်ထားပြီး၊ အဆင့်မြင့် aerospace engineering ကျောင်းသားများအတွက် အသုံးဝင်အောင် design လုပ်ထားပါသည်။ Configure လုပ်ရန် လွယ်ကူသောကြောင့်၊ industry professional များအတွက်လည်း နည်းလမ်းများစွာဖြင့် အသုံးဝင်ကြောင်း သက်သေပြခဲ့ပါသည်။ ၎င်းကို (FlightGear, Outerra, နှင့် OpenEaagles ကဲ့သို့) ပိုကြီးသော၊ full-featured ဖြစ်သော flight simulation application နှင့် architecture များထဲသို့ ပေါင်းစပ်ထည့်သွင်းခဲ့ပြီး၊ industry နှင့် academia တွင် batch simulation tool တစ်ခုအဖြစ်လည်း အသုံးပြုခဲ့ကြပါသည်။

## အသုံးပြုမှု ဥပမာများ

### Aerocross Echo Hawk

Aerocross Echo Hawk UAV ၏ Hardware-in-the-Loop (HITL) testing အတွက် JSBSim ကို အသုံးပြုခဲ့ပါသည်။ RS-232/422/485, proportional analog I/O, discrete I/O, နှင့် socket များမှတစ်ဆင့် flight hardware (PC/104-based system) နှင့် interface လုပ်ရန် custom code ကို ရေးသားခဲ့သော်လည်း core simulation code မှာ မပြောင်းလဲသေးသော JSBSim code ဖြစ်ပါသည်။ Pilot/operator training သည်လည်း 6-DoF code အဖြစ် JSBSim ကို အားကိုးပါသည်။

### DuPont Aerospace Company

DuPont Aerospace Company တွင် real-time HITL simulation နှင့် pilot/operator training အတွက် Matlab နှင့်အတူ JSBSim ကို အသုံးပြုခဲ့ပါသည်။ DuPont Aerospace Company ၏ Rex duPont က project ကို ရှင်းပြခဲ့ပါသည်-

> ၁၉၉၀ ခုနှစ်များတွင် duPont Aerospace Company သည် vertical takeoff fan jet transport plane တစ်စီးအတွက် ၎င်း၏ concept ကို စမ်းသပ်ရန် လေယာဉ်တစ်စီး တည်ဆောက်နေခဲ့ပါသည်။ ကျွန်ုပ်တို့သည် Microsoft Windows-based flight simulator တစ်ခုကို ဖန်တီးထားပြီး၊ အဆိုပြု လေယာဉ်၏ flying quality များကို စမ်းသပ်ရန် ၎င်းကို အသုံးပြုခဲ့ပါသည်။ သို့သော်လည်း full-sized mockup တစ်ခုပေါ်တွင် flight actuator များကို loop ထဲတွင် run ထားကာ flight characteristic များကို real time တွင် စမ်းသပ်နိုင်ရန် simulation တစ်ခု လိုအပ်ခဲ့ပါသည်။ ကျွန်ုပ်တို့သည် JSBSim flight dynamics model ကို အသုံးပြုသည့် FlightGear simulator ကို ရွေးချယ်ခဲ့ပါသည်၊ အကြောင်းမှာ code အပြည့်အစုံ ရယူနိုင်ခြင်း၊ ကျွန်ုပ်တို့၏ လေယာဉ်နှင့် ကိုက်ညီအောင် subprogram အသစ်များ ဖန်တီးနိုင်ရန် သေသေချာချာ စီစဉ်ထားခြင်း၊ နှင့် support ကို လွယ်ကူစွာ ရရှိနိုင်ခြင်း တို့ ဖြစ်ပါသည်။

> ကျွန်ုပ်တို့သည် ပိုမိုထိရောက်သော autopilot guidance system များ ဖွံ့ဖြိုးတိုးတက်စေရန် တစ်ပြိုင်နက် Matlab simulator တစ်ခုကိုလည်း ဖွံ့ဖြိုးတိုးတက်စေခဲ့ပါသည်၊ အကြောင်းမှာ ကျွန်ုပ်တို့၏ အဓိက task သည် autopilot တစ်ခုတည်းကို အသုံးပြု၍ လေယာဉ်ကို takeoff ပြုလုပ်ပြီး ၃၀ စက္ကန့်ကြာ hover ပြုလုပ်ရန် ဖြစ်လာခဲ့သောကြောင့် ဖြစ်ပါသည်။ ၎င်းက control system သည် လုံလောက်စွာ ကြံ့ခိုင်ကြောင်းကို သေချာစွာ ပြသပါလိမ့်မည်။ ထို့ကြောင့် ကျွန်ုပ်တို့သည် Matlab simulator နှင့် JSBSim derivative simulator ၏ သက်ဆိုင်ရာ module တစ်ခုစီထဲသို့ system နှစ်ခု sync ဖြစ်နေကြောင်း cross verify လုပ်နိုင်သော input sequence တစ်ခုကို model တစ်ခုစီသို့ ပေးအပ်သော unit test series တစ်ခုကို တည်ဆောက်ခဲ့ပါသည်။

> Matlab model ဖြင့် လွယ်ကူစွာ test မလုပ်နိုင်သော dynamic issue အမျိုးမျိုးကို စမ်းသပ်ရန် JSBSim system ကို အသုံးပြုခဲ့ပါသည်၊ အထူးသဖြင့် pilot feel နှင့် hover သို့ ဝင်ထွက်ကူးပြောင်းစဉ် controllability ပါဝင်သော issue များ ဖြစ်ပါသည်။ Transition ဖြစ်နေစဉ် underlying force structure သည် aerodynamic force များ ပိုမိုအရေးကြီးလာပြီး pure thrust control force များ လျော့နည်းလာသောကြောင့်၊ ဤ issue များကို Matlab ၏ pure control-system ကမ္ဘာထဲတွင် အကဲဖြတ်ရန် ခက်ခဲပါသည်။

> ကျွန်ုပ်တို့သည် estimation အတွက် ဖြစ်နိုင်သော error များနှင့် ပတ်သက်၍ aerodynamic simulation ရှိ key parameter များ၏ sensitivity ကဲ့သို့သော issue များကိုလည်း parametric study ပြုလုပ်ခဲ့ပါသည်။ ၎င်းတို့ကို pilot တစ်ဦးအား parameter တစ်ခု သို့မဟုတ် တစ်ခုထက်ပိုသော parameter များကို (parameter မည်သည့်ခု ပြောင်းလဲသည်ကို pilot မသိစေဘဲ) ၅၀% အထိ degrade လုပ်ထားသည့်အခါ လေယာဉ်၏ response ကို စမ်းသပ်ရန် ဒီဇိုင်းရေးဆွဲထားသော standard maneuver series တစ်ခုကို ပျံသန်းစေခြင်းဖြင့် ပြုလုပ်ခဲ့ပါသည်။

> ကျွန်ုပ်တို့သည် servo bandwidth အမျိုးမျိုးကိုလည်း simulate ပြုလုပ်ခဲ့ပြီး၊ flying characteristic များ မည်သည့်အချက်တွင် လက်မခံနိုင်လောက်အောင် ဖြစ်လာသည်ကို စမ်းသပ်ခဲ့ပါသည်။ ၎င်းက လိုအပ်သော characteristic များကို သတ်မှတ်ရန် အထောက်အကူ ဖြစ်ခဲ့ပါသည်။ Control system များထံမှ pilot များ လိုချင်သည့်အရာသည် optimal theoretical parameter များနှင့် အမြဲတမ်းနီးပါးပင် ကွဲပြားလေ့ ရှိပါသည်။

> ထို့အပြင်၊ ground speed ကို အလွန်တိကျစွာ ထိန်းချုပ်ရန် လိုအပ်သော hover လုပ်ငန်းစဉ်တွင် အထောက်အကူပြုမည့် HUD display system အများအပြားကို ကျွန်ုပ်တို့ ဖွံ့ဖြိုးတိုးတက်စေခဲ့ပါသည်။ နောက်ဆုံးတွင် pilot license ပင် မရှိသေးသော young engineer တစ်ဦးအား takeoff ပြုလုပ်ကာ altitude ပုံသေတစ်ခုတွင် ၃၀ စက္ကန့်ကျော် ပေတစ်ပေအတွင်း hover ထိန်းထားနိုင်စေသော system တစ်ခု ကျွန်ုပ်တို့ ရရှိခဲ့ပါသည်။

> ကျွန်ုပ်တို့သည် ၂၀၀၇ ခုနှစ် စက်တင်ဘာလ ၃၀ ရက်နေ့တွင် ခန့်မှန်းခြေ ၄၅ စက္ကန့်ကြာမြင့်သော ပျံသန်းမှု နှစ်ကြိမ်တွင် autopilot ထိန်းချုပ်သော takeoff နှင့် hover ဆိုသော ရည်မှန်းချက်ကို နောက်ဆုံးတွင် ပြီးမြောက်အောင် ဆောင်ရွက်နိုင်ခဲ့ပါသည်။ Control ပြဿနာကြောင့် မဟုတ်ဘဲ engine တစ်လုံးက fuel ကုန်သွားသောကြောင့် ပျံသန်းမှု နှစ်ကြိမ်စလုံး ရပ်တန့်သွားခဲ့ပါသည်။

### MITRE Air Traffic Studies

CDA (Continuous Descent Arrival) နှင့် OPD (Optimized Profile Descent) များဖြစ်နေစဉ် FMS (Flight Management System) ၏ အမူအကျင့်ကို 6-DoF simulation တစ်ခု ဖွံ့ဖြိုးတိုးတက်စေရန် MITRE တွင် JSBSim ကို အသုံးပြုနေပါသည်။ JSBSim ၏ standalone version (batch run များအတွက်) နှင့် FlightGear နှင့် ပေါင်းစပ်ထားသော version နှစ်ခုစလုံးကို အသုံးပြုခဲ့ပါသည်။ သီးခြား lateral နှင့် vertical navigation study များကို ပံ့ပိုးရန် control system component ထပ်ဆောင်းများကိုလည်း ဖန်တီးခဲ့ပါသည်။

MITRE တွင် အသုံးပြုနေသော application တစ်ခုထံသို့ socket တစ်ခုမှတစ်ဆင့် message များ output ပြုလုပ်ရန် JSBSim ကိုလည်း extend လုပ်ခဲ့ပြီး၊ ၎င်းက Air Traffic Control operator တစ်ဦး မြင်ရမည့်အတိုင်း ဆင်တူသော view တစ်ခု ပေးပါသည်။

### U.S. Department of Transportation

U.S. D.O.T. နှင့်အတူ ပြုလုပ်ခဲ့သော လုပ်ငန်းတွင်၊ human pilot math model တစ်ခုကို 6-DoF (six degree-of-freedom) simulation core အဖြစ် JSBSim ကို အသုံးပြု၍ ဖွံ့ဖြိုးတိုးတက်စေခဲ့ပါသည်။

### The University of Naples, Italy, Federico II

University of Naples တွင် FlightGear နှင့် JSBSim က drive လုပ်ပေးသော motion base flying/driving simulator တစ်ခု ရှိပါသည်။ Simulator တွင် screen သုံးခုပါသော visual presentation ရှိပြီး 190 degree field-of-view ပေးစွမ်းနိုင်ပါသည်။ Force feedback စွမ်းရည် ပေးနိုင်ရန် JSBSim source code ကို ပြင်ဆင်ခဲ့ပါသည်။

University of Naples တွင် near-ground flight operation များ၏ risk level evaluation ကို ပံ့ပိုးသော tool တစ်ခုအဖြစ် JSBSim ကို အသုံးပြုခဲ့ပါသည်။ ထို collision risk study များတွင် သုံးသပ်ထားသော လက်တွေ့ပြဿနာတစ်ခုမှာ obstacle အသစ်တစ်ခု (ဥပမာ အဆောက်အအုံ သို့မဟုတ် radar tower) ကို airport area ထဲတွင် တည်ထားသည့်အခါ flight operation များအပေါ် ဖြစ်ပေါ်လာနိုင်သော ခြိမ်းခြောက်မှုကို အကဲဖြတ်ခြင်း ဖြစ်ပါသည်။ Risk evaluation ကို obstacle ၏ geometry နှင့် location ကို ပြောင်းလဲခြင်းဖြင့် ပြုလုပ်ခဲ့ပါသည်။ Risk assessment procedure သည် “ပုံမှန်” flight path မှ aircraft trajectory များ၏ statistical deviation ကို analysis ပြုလုပ်ခြင်းကို အခြေခံထားပြီး၊ generic trajectory တစ်ခုသည် potential obstacle ကို ဝန်းရံထားသော “protection” area ပေးထားတစ်ခုကို ဖြတ်သန်းနိုင်ခြေ (probability) ကို အကဲဖြတ်ပါသည်။ ဤ framework အတွင်း၊ operational scenario ကို formal အနေဖြင့် ဖော်ပြပြီး computer simulation များစွာကို run ရန် implement ပြုလုပ်ခဲ့ပါသည်။

### Fraunhofer Institute for Wind Energy Systems

Italy ၏ University of Naples Federico II နှင့် ပူးတွဲသုတေသနတစ်ခုတွင်၊ Fraunhofer Institute for Wind Energy Systems (IWES) ၏ သုတေသနသူများသည် light airplane များ wind turbine wake များကို ဖြတ်သန်းပျံသန်းသောအခါ ဖြစ်ပေါ်လာသော wake encounter ပြဿနာကို လေ့လာခဲ့ကြပါသည်။

ဤသုတေသနအတွက်၊ သတ်မှတ်ထားသော လေနှင့် turbulence field များ ရှိနေစဉ် flight simulation scenario အုပ်စုတစ်ခုကို generate လုပ်ပြီး ထိန်းချုပ်ရန် software application framework တစ်ခုကို ဖွံ့ဖြိုးတိုးတက်စေခဲ့ပါသည်။ JSBSim ကို framework အတွင်း flight dynamics model အဖြစ် အသုံးပြုခဲ့ပြီး၊ ၎င်း၏ autopilot system များကို navigation လုပ်နေစဉ် လက်တွေ့ကျသော pilot အမူအကျင့်ကို simulate ပြုလုပ်ရန် ချိန်ညှိထားပါသည်။
Turbine wake များတွင် လေဖြန့်ဝေမှုကို OpenFOAM ဖြင့် တွက်ချက်ပြီး dynamic model အတွက် input အဖြစ် ပေးအပ်ခဲ့ပါသည်။

### TFASA - Test Flying Academy of South Africa

Test Flying Academy of South Africa သည် test pilot training အတွက် ground based Variable Stability System (VSS) simulator တစ်ခု၏ အခြေခံအဖြစ် JSBSim ကို အသုံးပြုခဲ့ပါသည်။ Base aircraft model တစ်ခု၏ aerodynamic stability နှင့် control coefficient များကို flying task များအပေါ် ၎င်းတို့၏ သက်ရောက်မှုကို ပြသရန် ပြုပြင်ထားပါသည်။ Lag, delay နှင့် rate limit ပမာဏ မတူညီမှုများကြောင့် PIO အပေါ် ၎င်းတို့၏ ဖြစ်နိုင်ချေရှိသော သက်ရောက်မှုကို ပြသရန် Actuator များကိုလည်း model လုပ်ထားပါသည်။

Flight Control Mechanical Characteristics (FCMC) ၏ သက်ရောက်မှုများကိုပါ ပြသရန်အတွက် fixed wing aircraft နှင့် rotary aircraft နှစ်မျိုးစလုံးကို programmable force-feedback inceptor များဖြင့် simulate ပြုလုပ်ထားပါသည်။

JSBSim ကို Prepar3D နှင့် ပေါင်းစပ်ထားပြီး Prepar3D ၏ outside visual များကို အသုံးချထားပါသည်၊ ၎င်းတို့ကို large LCD သုံးခု သို့မဟုတ် triple projector setup တစ်ခုတွင် 180 degree view ဖြင့် render ပြုလုပ်ပါသည်။

---

!!! note "TODO"

    အသုံးပြုမှု ဥပမာများ (2014+) ကို update လုပ်ပြီး ထပ်ဖြည့်ရန်။

