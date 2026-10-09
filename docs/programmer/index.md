---
title: Programmer Manual
description: JSBSim Programmer Manual home page.
---

# Programmer manual (Programmer လမ်းညွှန်)

JSBSim ၏ design ၏ သီးခြား ရည်ရွယ်ချက်တစ်ခုမှာ small သို့မဟုတ် large simulation program တစ်ခုထဲသို့ ပေါင်းစပ်ထည့်သွင်းရန် အတော်လေး လွယ်ကူစေရန် ဖြစ်ပါသည်။ Simulation program များ (နှင့် software application များ ယေဘုယျအားဖြင့်) တွင် မကြာခဏ ဖြစ်တတ်သကဲ့သို့၊ "feature creep" စတင်ဝင်ရောက်ကာ program code သည် ရည်ရွယ်ထားသည်ထက် ကြီးမားသော product တစ်ခုအဖြစ် ဖွံ့ဖြိုးလာတတ်ပါသည်။ JSBSim ၏ကိစ္စတွင်၊ code base ကို တတ်နိုင်သမျှ သေးငယ်အောင် ထိန်းသိမ်းထားရန် ကြိုးစားခဲ့သော်လည်း၊ ပထမဆုံး ကြည့်ချိန်တွင် ၎င်းသည် ဒုနှင့်ဒေးရှုပ်ထွေးစေနိုင်ပါသေးသည်။

Simulator application အချို့နှင့် မတူဘဲ၊ JSBSim (ဤစာကို ရေးသားနေချိန်တွင်) သည် external dependency မရှိပါ။ ဆိုလိုသည်မှာ JSBSim ကို build လုပ်ရန် လိုအပ်သော code *အားလုံး*ကို ၎င်းနှင့်အတူ package လုပ်ပေးထားပါသည်။ ၎င်းက JSBSim executable ကို build လုပ်ခြင်းကို သိသိသာသာ ရိုးရှင်းစေပါသည်။ JSBSim ထဲတွင် automatically generate လုပ်ထားသော code လည်း မရှိပါ။ Code အားလုံးသည် standard C++ ဖြစ်ပါသည် (ပါဝင်ထားသော eXpat XML parsing code မှ C code အချို့ ပါဝင်ပါသည်)။

!!! info ""

	JSBSim distribution တွင် ပိုင်ဆိုင်မှုအထူးအခွင့်ရှိသော (proprietary) program code မပါဝင်ပါ။ JSBSim နှင့်အတူ ပါဝင်လာသော code အားလုံးကို ပညာရေးရည်ရွယ်ချက်ဖြင့် အများပြည်သူ ရရှိနိုင်သော သတင်းအချက်အလက်များကို အသုံးပြု၍ စေတနာ့ဝန်ထမ်းအနေဖြင့် developer များက ဖွံ့ဖြိုးတိုးတက်စေခဲ့ပြီး၊ မကြာခဏ သီးခြား စာအုပ်တစ်အုပ်ကို တိုက်ရိုက် ရည်ညွှန်းထားပါသည်။ Case အချို့တွင်၊ generic သဘောသဘာဝရှိသော code များကို project ထံသို့ ပြန်လည် လှူဒါန်းခဲ့ကြပါသည်။

