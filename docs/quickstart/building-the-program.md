---
title: Program ကို Build လုပ်ခြင်း
description: JSBSim ကို build လုပ်နည်း။
tag:
  - quickstart
  - building
---

# Program နှင့် Library ကို Build လုပ်ခြင်း

JSBSim ကို [CMake](https://cmake.org/) သို့မဟုတ် [Microsoft Visual Studio](https://www.visualstudio.com/free-developer-offers/) ဖြင့် build လုပ်နိုင်ပါသည်။ Mac OSX သို့မဟုတ် Linux platform သုံးနေပါက CMake ကို အသုံးပြုရမည် ဖြစ်ပါသည်။ Windows user တစ်ဦးဖြစ်ပါက နှစ်မျိုးစလုံးကို အသုံးပြုနိုင်ပါသည်။

JSBSim ကို standard C++98/C99 ဖြင့် ရေးသားထားပြီး dependency မရှိသောကြောင့်၊ သင့် platform တွင် C/C++ compiler တစ်ခု install လုပ်ထားရုံသာ လိုအပ်ပါသည်။

## CMake ဖြင့် Build လုပ်ခြင်း

CMake သည် software များကို build လုပ်ရန်နှင့် test လုပ်ရန်အတွက် multiplatform tool တစ်ခု ဖြစ်ပါသည်။ ၎င်းသည် JSBSim ကို GNU make သို့မဟုတ် Microsoft Visual Studio ဖြင့် build လုပ်ရန်အတွက် file များကို ထုတ်ပေးနိုင်ပါသည်။ Build file များကို source code နှင့် သီးခြားထားရန်အတွက်၊ JSBSim ကို သီးခြား directory တစ်ခုတွင် build လုပ်ခြင်းက ပိုကောင်းပါသည်။
```bash
> cd jsbsim-code
> mkdir build
> cd build
```
CMake သည် software ကို *build မလုပ်ပါ*၊ ၎င်းသည် build tool အမျိုးမျိုးအတွက် file များကို ထုတ်ပေးခြင်းသာ ဖြစ်ပါသည်။ အောက်ပါ command များသည် JSBSim ကို build လုပ်ရန် GNU make ကို အသုံးပြုနေသည်ဟု ယူဆထားပါသည်။

ဦးစွာ CMake ကို run ပြီးနောက် make ကို run ပါ
```bash
> cmake ..
> make
```

ဤသည်က class အမျိုးမျိုးကို compile လုပ်ပေးပြီး၊ `build/src` တွင် တည်ရှိမည့် JSBSim application ကို build လုပ်ပေးပါမည်။

### CMake သို့ ပေးပို့သော Option များ

CMake သည် JSBSim ၏ build ကို ညှိနိုင်းရန်အတွက် parameter အမျိုးမျိုးကို အသုံးပြုနိုင်ပါသည်။ မတူညီသော option များကို အောက်တွင် ဖော်ပြထားပါသည်။ သင့်လိုအပ်ချက်အလိုက် ၎င်းတို့ကို သီးသန့် (သို့) ပေါင်းစပ် အသုံးပြုနိုင်ပါသည်။

#### Compiler သို့ Parameter များ ပေးပို့ခြင်း

Compiler option များ သတ်မှတ်လိုပါက JSBSim ၏ `Debug` version ကို build လုပ်ရန် CMake သို့ flag များ ပေးပို့နိုင်ပါသည်။ JSBSim သည် code အချို့အတွက် C ကိုလည်း အသုံးပြုထားသောကြောင့်၊ C++ နှင့် C compiler နှစ်ခုစလုံးအတွက် option များ သတ်မှတ်နိုင်ပါသည်။
```bash
> cmake -DCMAKE_CXX_FLAGS_DEBUG="-g -Wall" -DCMAKE_C_FLAGS_DEBUG="-g -Wall" -DCMAKE_BUILD_TYPE=Debug ..
> make
```
သို့မဟုတ် အခြားနည်းလမ်းတစ်ခုအနေဖြင့် JSBSim ၏ release version ကို build လုပ်ပြီး GNU Make ကို core 4 ခုအသုံးပြု၍ executable ကို ပိုမြန်စွာ build လုပ်ရန် တောင်းဆိုနိုင်ပါသည်။
```bash
> cmake -DCMAKE_CXX_FLAGS_RELEASE="-O3 -march=native -mtune=native" -DCMAKE_C_FLAGS_RELEASE="-O3 -march=native -mtune=native" -DCMAKE_BUILD_TYPE=Release ..
> make -j4
```

#### Expat ကို Build လုပ်ခြင်း သို့မဟုတ် System Library ကို အသုံးပြုခြင်း

JSBSim သည် XML file များဖတ်ရန်အတွက် [Expat library](https://libexpat.github.io/) ကို အသုံးပြုပါသည်။ Expat ၏ source code ကို JSBSim source code နှင့်အတူ ပေးထားပြီး JSBSim build လုပ်စဉ်တွင် အတူတကွ compile လုပ်ပါသည်။ သို့သော်၊ Expat ကို သင့် platform တွင် install လုပ်ထားပြီးသားဖြစ်ပါက၊ ထပ်နေခြင်းကို ရှောင်ရှားရန်အတွက် သင့် system ၏ Expat library ကို အသုံးပြုလိုနိုင်ပါသည်။ ထိုသို့သော အခြေအနေတွင်၊ `SYSTEM_EXPAT` flag ကို CMake သို့ ပေးပို့ရပါမည်-
```bash
> cmake -DSYSTEM_EXPAT=ON ..
> make
```

### JSBSim ၏ [Python](https://www.python.org/) Module ကို Build လုပ်ခြင်း

JSBSim ၏ Python module ကိုလည်း CMake ဖြင့် build လုပ်နိုင်ပါသည်။ ထိုအတွက် သင့် platform တွင် [Cython](http://cython.org/) install လုပ်ထားရန် လိုအပ်ပါသည်။ CMake သည် Cython ကို အလိုအလျောက် detect လုပ်ပြီး Python module ကို build လုပ်ပေးပါလိမ့်မည်။

## Microsoft Visual Studio ဖြင့် Build လုပ်ခြင်း

Visual Studio မှ `JSBSim.vcxproj` project file ကို ဖွင့်၍ JSBSim အတွက် project တစ်ခု ဖွင့်နိုင်ပါသည်။ Project file သည် JSBSim executable ကို build လုပ်ရန် Visual Studio ကို setup ပေးပါလိမ့်မည်။

**မှတ်ချက် ၁-** JSBSim ၏ တရားဝင် build tool မှာ CMake ဖြစ်ပါသည်။ Visual Studio project file များကို အဆင်ပြေစေရန်အတွက် ပေးထားခြင်းဖြစ်ပြီး code နှင့် up to date ဖြစ်မည်ဟု အာမခံချက် မရှိပါ။

**မှတ်ချက် ၂-** Visual Studio 2017 မှစ၍ Microsoft သည် CMake ကို ထည့်သွင်းပေးထားသောကြောင့်၊ VS2017 ပေါ်တွင် CMake file မှတစ်ဆင့် JSBSim ကို တိုက်ရိုက် build လုပ်နိုင်သင့်ပါသည်။

## JSBSim ကို Test လုပ်ခြင်း

JSBSim တွင် build မှန်ကန်မှုကို အလိုအလျောက် စစ်ဆေးပေးသည့် test suite တစ်ခု ပါဝင်ပါသည်။ ဤ test suite သည် `tests` directory တွင် တည်ရှိပြီး Python ဖြင့် ရေးသားထားသောကြောင့်၊ [JSBSim ၏ Python module ကို build လုပ်ထားရန်](Building the Python module of JSBSim) လိုအပ်ပါသည်။

Test suite ကို `build` directory တွင် `ctest` ကို အသုံးပြု၍ run နိုင်ပါသည်။ Test များကို `-j` option ဖြင့် core များစွာ (အောက်ပါ ဥပမာတွင် ၄ ခု) ပေါ်တွင် တစ်ပြိုင်နက် run နိုင်ပါသည်
```bash
> ctest -j4
```

## JSBSim ကို Install လုပ်ခြင်း

JSBSim ကို build လုပ်ပြီး test ပြီးသည်နှင့်၊ C++ header နှင့် library ကို platform တစ်ခုလုံးအတွက် install လုပ်နိုင်ပါသည်။ ထိုအတွက် `build` directory မှ GNU make ကို run နိုင်ပါသည်
```bash
> make install
```

## Python Module ကို Install လုပ်ခြင်း

C++ header နှင့် library များအပြင် JSBSim ၏ Python module ကိုပါ install လုပ်မည်ဆိုပါက၊ `INSTALL_PYTHON_MODULE` flag ကို CMake သို့ ပေးပို့ရပါမည်
```bash
> cmake -DINSTALL_PYTHON_MODULE=ON ..
> make
> make install
```

အခြားနည်းလမ်းတစ်ခုအနေဖြင့်၊ Python module ကို `build` directory မှ အောက်ပါ command များကို run ခြင်းဖြင့် manual အနေဖြင့် install လုပ်နိုင်ပါသည်
```bash
> cd tests
> python setup.py install
```
---

<figure markdown>
  ![Placeholder image](../assets/img/ac_airspeeds_recap.svg){: .center width="80%" }
  <figcaption>
	ဒီတော့၊ ဒီလေယာဉ်ရဲ့ ပျံသန်းမှုကို simulate လုပ်ချင်ပါသလား။
  </figcaption>
</figure>
