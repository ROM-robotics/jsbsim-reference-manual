---
title: Properties
description: JSBSim's property manager system.
---

# Properties

Simulation program များသည် state information အများအပြား ကို management လုပ်ရန် လိုအပ်ပါသည်။ အထူးသဖြင့် program ကြီးများတွင်၊ data management task သည် ပြဿနာများ ဖြစ်စေနိုင်ပါသည်-

- Contributor များသည် program ထဲသို့ အသုံးဝင်သော ထပ်ဖြည့်မှုများ ပြုလုပ်ရန်အတွက် လိုအပ်သော interface အရေအတွက်ကို ကျွမ်းကျင်ပိုင်နိုင်ရန် ပိုမိုခက်ခဲလာပြီး၊ ထို့ကြောင့် contribution များ နှေးကွေးသွားပါသည်။
- Runtime configurability သည် module အမျိုးမျိုးက mechanism မတူညီသည်များ (environment variable, custom specification file, command-line option စသည်) ကို အသုံးပြုသောကြောင့် ပိုမိုခက်ခဲလာပါသည်။
- Module တစ်ခု၏ initialization routine များသည် initialize မပြုလုပ်ရသေးသော module တစ်ခုမှ state information ကို သတ်မှတ်ရန် သို့မဟုတ် ရယူရန် လိုအပ်နိုင်သောကြောင့်၊ module များ၏ initialization order သည် ရှုပ်ထွေးပြီး ကြွပ်ဆတ် (brittle) ဖြစ်ပါသည်။
- Add-on script, specification file စသည်တို့မှတစ်ဆင့် ချဲ့ထွင်နိုင်မှု (extensibility) သည် program က ပေးအပ်ထားသော state information ပမာဏအတိုင်းသာ ကန့်သတ်ထားပြီး၊ code မရေးတတ်သော developer များသည် developer များက variable အသစ်တစ်ခု ထည့်ပေးသည်အထိ ကြာရှည်စွာ စောင့်ဆိုင်းရလေ့ရှိပါသည်။

Property Manager system သည် ရွေးချယ်ထားသော program state information အားလုံးအတွက် interface တစ်ခုတည်းကို ပေးအပ်ပြီး၊ run-time တွင် user-specified variable အသစ်များကို dynamic ဖန်တီးခွင့် ပေးပါသည်။ နောက်ဆုံးဖော်ပြထားသော စွမ်းရည်သည် JSBSim ၏ control system model အတွက် အထူးအရေးကြီးပါသည်၊ အကြောင်းမှာ လေယာဉ်တစ်စင်း၏ control law definition ကို ဖွဲ့စည်းသော control system component အမျိုးမျိုး (PID controller, switch, summer, gain စသည်) သည် configuration file တစ်ခုထဲတွင်သာ တည်ရှိသောကြောင့် ဖြစ်ပါသည်။ Run-time တွင် — component definition များကို parse လုပ်ပြီးနောက် — component များကို instantiate လုပ်ပြီး property manager သည် component တစ်ခုစီ၏ output value ကို သိမ်းဆည်းရန် property တစ်ခု ဖန်တီးပေးပါသည်။

Property များကိုယ်တိုင်သည် Unix file system ၏ ဖွဲ့စည်းပုံနှင့် ဆင်တူသော hierarchical, tree-like structure ထဲသို့ အုပ်စုဖွဲ့ထားသော၊ ရွေးချယ်ပိုင်ခွင့် ကန့်သတ်ထားသော visibility (read သို့မဟုတ် read/write) ရှိသည့် global variable များနှင့် တူပါသည်။ Property tree ၏ structure တွင် root node၊ sub node (subdirectory များကဲ့သို့)၊ နှင့် end-node (property) များ ပါဝင်ပါသည်။ Unix file system နှင့် ဆင်တူစွာပင်၊ property များကို current node နှင့် သက်ဆိုင်သော (relative) အနေအထားဖြင့် သို့မဟုတ် root node ကို အခြေခံ၍ ရည်ညွှန်းနိုင်ပါသည်။ Node များကို file သို့မဟုတ် directory များကို symbolic link ချိတ်ဆက်သကဲ့သို့ပင် node တစ်ခုအပေါ် node တစ်ခု graft (ဆက်စပ်ထည့်သွင်း) နိုင်ပါသည်။ Property များကို JSBSim နှင့် FlightGear တစ်လျှောက်လုံးတွင် program code ၏ parameter အသီးသီးကို ရည်ညွှန်းရန် အသုံးပြုပါသည်။ Property များကို command line မှ၊ specification file နှင့် script များမှ၊ ထို့အပြင် socket interface မှတစ်ဆင့်ပင် သတ်မှတ်နိုင်ပါသည်။ Property name များသည် ဤကဲ့သို့ ဖြစ်ပါသည်- `position/h-sl-ft`, နှင့် `aero/qbar-psf`။

Property များနှင့် configuration file များ အသုံးပြုခြင်း၏ စွမ်းအားကို သရုပ်ပြရန်၊ စွမ်းအားမြင့် jet လေယာဉ်မော်ဒယ်တစ်ခု၏ ဥပမာကို သုံးသပ်ကြည့်ပါ။ ဥပမာလေယာဉ်၏ control panel တွင် FCS ၌ pitch limit ကို override လုပ်ရန် pilot ကို ခွင့်ပြုသော switch အသစ်တစ်ခု ထပ်ဖြည့်ထားသည်ဟု ယူဆပါ။ FlightGear အတွက်၊ instrument panel ကို configuration file တွင် သတ်မှတ်ထားပြီး၊ visual display အတွက် switch ကိုလည်း ထိုနေရာတွင် သတ်မှတ်ထားပါသည်။ Property name တစ်ခုကိုလည်း switch definition သို့ သတ်မှတ်ပေးထားပါသည်။ JSBSim aircraft specification file ၏ flight control အပိုင်းအတွင်း၊ instrument panel definition file ရှိ pitch override switch သို့ သတ်မှတ်ထားသည့် property name အတူတူကိုပင် အသုံးပြု၍ switch ၏ position အလိုက် control law များကို လိုချင်သော path ဖြင့် ပို့ပေးနိုင်ပါသည်။ Code ကို ထိခိုက်ရန် မလိုအပ်ပါ။

Specific simulation parameter များသည် JSBSim အတွင်းမှရော configuration file specification များတွင် properties မှတစ်ဆင့်ပါရော ရရှိနိုင်ပါသည်။ ယခင်က ဖော်ပြခဲ့သည့်အတိုင်း၊ “properties” ဆိုသည်မှာ configuration file တစ်ခုအတွင်းမှ သို့မဟုတ် command line ပေါ်မှ ကျွန်ုပ်တို့ access လုပ်နိုင် (သို့) သတ်မှတ်နိုင်သော parameter များကို ဖော်ပြရန် သုံးသော term ဖြစ်ပါသည်။

Property အများစုသည် standard property များ — ဆိုလိုသည်မှာ vehicle အားလုံးအတွက် အမြဲတမ်း ရှိနေသော property များ — ဖြစ်ပါသည်။ Aerodynamic coefficient များ၊ engine များ၊ thruster များနှင့် flight control/autopilot model များတွင်လည်း dynamic သတ်မှတ်ထားသော property များ ရှိပါလိမ့်မည်။ ၎င်းမှာ aerodynamic coefficient၊ engine စသည်တို့၏ အစုလိုက်ကို လေယာဉ်တစ်စင်းအတွက် သက်ဆိုင်ရာ configuration file ကို ဖတ်ပြီးမှသာ သိရှိနိုင်သောကြောင့် ဖြစ်ပါသည်။ ဤ parameter များအတွက် property name ပေးသော convention ကို သိထားမှသာ ၎င်းတို့ကို access လုပ်နိုင်ပါသည်။ ဥပမာအနေဖြင့်၊ X-15 model ၏ flight control system တွင် အောက်ပါ component များ (အခြားများနှင့်အတူ) ပါဝင်ပါသည်-

```xml
<flight_control name="X-15">
   <channel name="Pitch">
      <summer name="fcs/pitch-trim-sum">
         <input> fcs/elevator-cmd-norm </input>
         <input> fcs/pitch-trim-cmd-norm </input>
         <clipto>
            <min> -1 </min>
            <max>  1 </max>
         </clipto>
      </summer>
      <aerosurface_scale name="fcs/pitch-command-scale">
         <input> fcs/pitch-trim-sum </input>
         <range>
            <min> -50 </min>
            <max>  50 </max>
         </range>
      </aerosurface_scale>
      <pure_gain name="fcs/pitch-gain-1">
         <input> fcs/pitch-command-scale </input>
         <gain> -0.36 </gain>
      </pure_gain>
   </channel>
</flight_control>
```

အထက်ပါ component ပထမဆုံးတစ်ခု (`fcs/pitch-trim-sum`) သည် နေရာနှစ်ခုမှ input ကို ယူသည်၊ ၎င်းမှာ သိရှိပြီးသား static property များဖြစ်သော `fcs/elevator-cmd-norm` နှင့် `fcs/pitch-trim-cmd-norm` တို့ ဖြစ်ပါသည်။ နောက်တစ်ခု component သည် ပထမ component ၏ output ကို input အဖြစ် ယူပါသည်။ ဒုတိယ component အတွက် ဖော်ပြထားသော input property မှာ `fcs/pitch-trim-sum` ဖြစ်ပါသည်။ အထက်ပါအတိုင်း ဆက်လက်သုံးသပ်ရန်၊ နောက်ဆုံး component ဖြစ်သော `fcs/pitch-gain-1` သည် ရှေ့ component ဖြစ်သော `fcs/pitch-command-scale` ၏ output ကို input အဖြစ် ယူပြီး၊ ၎င်းသည် `fcs/pitch-command-scale` ဟု property name ပေးထားပါသည်။

ထို့ကြောင့် ယခုအခါ JSBSim အတွင်းရှိ parameter များစွာကို access လုပ်ရန် နည်းလမ်းတစ်ခု ရရှိပါပြီ။ FCS ကို JSBSim တွင် မည်သို့ တွဲဆောက်ထားသည်ကို ကျွန်ုပ်တို့ သိရှိပြီးဖြစ်ပါသည်။ FCS တွင် အသုံးပြုထားသော component အတူတူများကို autopilot သို့မဟုတ် အခြား system တစ်ခု တည်ဆောက်ရန်လည်း အသုံးပြုနိုင်ပါသည်။

