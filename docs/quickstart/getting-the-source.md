---
title: Source Code ရယူခြင်း
description: JSBSim ၏ source code ကို ရယူခြင်း။
tags:
  - quickstart
  - building
---

# Source Code ရယူခြင်း

JSBSim ၏ GitHub repository ကို ဤလင့်တွင် ဝင်ရောက်ကြည့်ရှုနိုင်ပါသည်- [github.com/JSBSim-Team/jsbsim](https://github.com/JSBSim-Team/jsbsim)။ ဤ repository သည် SourceForge ပေါ်ရှိ မူရင်း repository ကို mirror လုပ်ထားခြင်း ဖြစ်ပါသည်- [sourceforge.net/projects/jsbsim](https://sourceforge.net/projects/jsbsim)။

## Source ကို download လုပ်ရန် လိုအပ်သည့်အရာများ

[Git software](https://git-scm.com/) ကို install လုပ်ထားရန် လိုအပ်ပါသည်။ Git သည် *version control software* တစ်ခုဖြစ်ပြီး၊ ဖိုင်တစ်ခု သို့မဟုတ် ဖိုင်အစုအဝေးတစ်ခု၏ ပြောင်းလဲမှုများကို အချိန်နှင့်အမျှ မှတ်တမ်းတင်ပေးသည့် စနစ်တစ်ခု ဖြစ်ပါသည်။ ထို့ကြောင့် နောက်ပိုင်းတွင် သီးခြား version များကို သင် ပြန်လည်ခေါ်ယူနိုင်ပါသည်။ JSBSim software ၏ source code file များကို Git ဖြင့် version control လုပ်ထားပါသည်။

Git ကို install လုပ်ရန် [ဤ download site သို့ သွားပါ](https://git-scm.com/downloads) ပြီး သင့် platform အတွက် version ကို ရယူပါ။ Git ကို သင့်ကွန်ပျူတာတွင် နည်းလမ်းနှစ်မျိုးဖြင့် local အနေဖြင့် အသုံးပြုနိုင်ပါသည်- [GUI client](https://git-scm.com/downloads/guis) တစ်ခုခုမှတစ်ဆင့် သို့မဟုတ် command shell (ဥပမာ Linux သို့မဟုတ် Windows ပေါ်ရှိ *Bash shell*) မှတစ်ဆင့် ဖြစ်ပါသည်။

Git ကို install လုပ်ပြီးပါက၊ command shell မှတစ်ဆင့် Git ကို အသုံးပြုမည်ဟု ယူဆပါက၊ JSBSim source code public repository ကို အောက်ပါနေရာနှစ်ခုအနက် တစ်ခုခုမှ *clone* လုပ်နိုင်ပါသည်။

## [SourceForge](https://sourceforge.net/p/jsbsim/code/ci/master/tree/) မှ Download လုပ်ခြင်း

ဤကိစ္စတွင် repo ကို clone လုပ်ရန် Git command မှာ (HTTPS mode)

```bash
> git clone https://git.code.sf.net/p/jsbsim/code jsbsim-code
```  

သို့မဟုတ် (SSH mode)

```bash
> git clone git://git.code.sf.net/p/jsbsim/code jsbsim-code
```  

## [GitHub](https://github.com/JSBSim-Team/jsbsim) မှ Download လုပ်ခြင်း

ဤကိစ္စတွင် repo ကို clone လုပ်ရန် Git command မှာ (HTTPS mode)

```bash
> git clone https://github.com/JSBSim-Team/jsbsim.git jsbsim-code
```  

သို့မဟုတ် (SSH mode)

```bash
> git clone git@github.com:JSBSim-Team/jsbsim.git jsbsim-code
```  

---

<figure markdown>
  ![Placeholder image](../assets/img/ac_airspeeds_recap.svg){: .center width="80%" }
  <figcaption>
	ဒီတော့၊ ဒီလေယာဉ်ရဲ့ ပျံသန်းမှုကို simulate လုပ်ချင်ပါသလား။
  </figcaption>
</figure>
