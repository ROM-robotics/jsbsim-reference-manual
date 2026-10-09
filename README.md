# JSBSim ရည်ညွှန်းလက်စွဲ (JSBSim Reference Manual)

ဤဆိုက်သည် GitHub Pages မှ hosting လုပ်ပေးထားသော၊ [MkDocs](https://www.mkdocs.org/) ကို အခြေခံ၍ [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) theme ဖြင့် ဖန်တီးထားသော [JSBSim Reference Manual](https://jsbsim-team.github.io/jsbsim-reference-manual) ၏ မူလဆိုက်ဖြစ်ပါသည်။

<p align="center">
<img width="250" heigth="250" src="https://github.com/JSBSim-Team/jsbsim-logo/blob/master/logo_JSBSIM_globe.png">
</p>

[JSBSim](https://github.com/JSBSim-Team/jsbsim) သည် C++ ဖြင့်ရေးသားထားသော၊ platform အမျိုးမျိုးတွင် အသုံးပြုနိုင်သည့် ယေဘုယျရည်ရွယ်ချက်အတွက် object-oriented Flight Dynamics Model (FDM) တစ်ခု ဖြစ်ပါသည်။ FDM ဆိုသည်မှာ လေယာဉ်၊ ဒုံးကျည် စသည်တို့အပေါ် ထိန်းချုပ်မှုယန္တရားအမျိုးမျိုးနှင့် သဘာဝ တွန်းအားများကို အသုံးပြု၍ သက်ရောက်စေသည့် အင်အားနှင့် moment များအောက်တွင် ၎င်းတို့၏ လှုပ်ရှားမှုကို သတ်မှတ်ပေးသည့် physics & math model ပင် ဖြစ်ပါသည်။ JSBSim ကို graphical display မပါသော standalone batch mode flight simulator အဖြစ် စမ်းသပ်မှုနှင့် လေ့လာမှုအတွက် run နိုင်သကဲ့သို့၊ [FlightGear](https://www.flightgear.org/) သို့မဟုတ် အခြား flight simulator များနှင့် ပေါင်းစပ်၍လည်း အသုံးပြုနိုင်ပါသည်။
 
## ပါဝင်ကူညီရန် (Contribute)

### Bug များ သတင်းပို့ရန် သို့မဟုတ် feature များ တောင်းဆိုရန်

Bug များ သတင်းပို့လိုပါက သို့မဟုတ် feature/အသစ်ထည့်သွင်းမှုများ တောင်းဆိုလိုပါက [issue အသစ်တစ်ခု ဖွင့်ပါ](https://github.com/JSBSim-Team/jsbsim-reference-manual/issues)။

### စာရွက်စာတမ်း (documentation) ကို ပါဝင်ကူညီရန်

Documentation တွင် ပါဝင်ကူညီလိုပါက [pull request တစ်ခု တင်သွင်းပါ](https://github.com/JSBSim-Team/jsbsim-reference-manual/pulls)

ထိုသို့ ပြုလုပ်ရန်အတွက် သင်သည် ဤ repository ကို fork လုပ်ပြီး သင့်ကွန်ပျူတာတွင် [Python3](https://www.python.org/) နှင့် [pip](https://pip.pypa.io/en/stable/installation/) ကို install လုပ်ရန် လိုအပ်ပါမည်။

1. အထက်တွင် ဖော်ပြထားသော prerequisite များကို install လုပ်ပါ။

2. Repository ကို clone လုပ်ပါ။
```bash
git clone https://github.com/JSBSim-Team/jsbsim-reference-manual.git
```

3. သီးသန့် virtual environment တစ်ခု ဖန်တီးပါ။
```bash
cd jsbsim-reference-manual
python3 -m venv env # OR < py -m venv env > on Windows
```

4. Virtual environment ကို activate လုပ်ပြီး လိုအပ်သော PyPi package များကို install လုပ်ပါ။
```bash
source env/bin/activate # OR < .\env\Scripts\activate > on Windows
python3 -m pip install -r requirements.txt # OR < py -m pip install -r requirements.txt > on Windows
```

5. ဆိုက်ကို build လုပ်ပြီး local server တစ်ခုတွင် ရရှိနိုင်အောင် ပြုလုပ်ပါ။
```bash
mkdocs serve
```

6. http://localhost:8000 ကို ဖွင့်ကြည့်ပါ။

ထို့နောက် MkDocs သည် http://localhost:8000 တွင် local web server တစ်ခုကို run ပေးမည်ဖြစ်ပြီး၊ သင်ပြောင်းလဲမှု ပြုလုပ်တိုင်း ဆိုက်ကို ပြန်လည် build ပေးပါလိမ့်မည်။ (`CTRL`+`C`) ကို နှိပ်ခြင်းဖြင့် အချိန်မရွေး ထွက်နိုင်ပါသည်။

အောက်ပါ command များကို အသုံးပြု၍ manual ကို offline အသုံးပြုရန် static site အဖြစ်လည်း build လုပ်နိုင်ပါသည်-
```bash
export OFFLINE=true # OR < set OFFLINE=true > on Windows
export CI=false
mkdocs build
```
Build လုပ်ပြီးသော manual သည် *site/* directory တွင် ရှိပါမည်။ ယခုအခါ သင်သည် search feature ကို offline တွင် အသုံးပြုနိုင်ပါပြီ။

ပြီးဆုံးပါက၊ အောက်ပါ command ဖြင့် သင့် virtual environment မှ ထွက်နိုင်ပါသည်-
```bash
deactivate
```
