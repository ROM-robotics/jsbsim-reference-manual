---
title: Program ကို Run ခြင်း
description: JSBSim application ကို run ခြင်း။
tags:
  - quickstart
---

# Program ကို Run ခြင်း

JSBSim repository တည်ရှိသော path ကို ဤနေရာတွင် *`<JSBSim-root-dir>`* ဟု ခေါ်ပါမည်။ Source code မှ JSBSim ကို build လုပ်ထားပါက `<JSBSim-root-dir>/src/` subdirectory အောက်တွင် executable file (Linux တွင် `JSBSim` သို့မဟုတ် Windows တွင် `JSBSim.exe`) တစ်ခု ရှိပါလိမ့်မည်။ ၎င်းသည် JSBSim *standalone application* ဖြစ်ပြီး၊ root directory တွင် copy ကူးထားချင်ကောင်းချင်ပါလိမ့်မည်-

```
<JSBSim-root-dir>$ cp src/JSBSim .
```

JSBSim standalone application ကို run သည့်အခါ option များစွာကို သတ်မှတ်ပေးနိုင်ပါသည်။

```
<JSBSim-root-dir>$ JSBSim

Usage (items in brackets are optional):
  JSBSim [script name] [output directive files names] <options>
Options:
--help Returns a usage message
--version Returns the version number
--outputlogfile=<filename> Sets/replaces the name of the data log file
--logdirectivefile=<filename> Sets name of data log directives file
--root=<path> Sets the JSBSim root directory (where src/ resides)
--aircraft=<filename> Sets the name of the aircraft to be modeled
--script=<filename> Specifies a script to run
--realtime Specifies to run in actual real world time
--nice Directs JSBSim to run at low CPU usage
--suspend Specifies to suspend the simulation after initialization
--initfile=<filename> Specifies an initialization file to use
--catalog Directs JSBSim to list all properties for this model
  (--catalog can be specified on the command line along with a --aircraft option,
  or by itself, while also specifying the aircraft name, e.g. --catalog=c172)
--end-time=<time> Specifies the sim end time (e.g. time=20.5)
--property=<name=value> Sets a property to a value.
  For example: --property=simulation/integrator/rate/rotational=1

NOTE: There can be no spaces around the = sign when an option is followed by a filename
```

Script တစ်ခု၏ အမည်ကို ပေးသွင်းခြင်းဖြင့် JSBSim ကို run နိုင်ပါသည်-

```
<JSBSim-root-dir>$ JSBSim --script=scripts/c1723.xml
```

!!! note "TODO"

    စာမျက်နှာ အကြောင်းအရာများကို ပြည့်စုံစွာ ဖြည့်စွက်ရန်။

---

<figure markdown>
  ![Placeholder image](../assets/img/ac_euler_gimbal.svg){: .center width="80%" }
  <figcaption>
	ဒီတော့၊ ဒီလေယာဉ်ရဲ့ ပျံသန်းမှုကို simulate လုပ်ချင်ပါသလား။
  </figcaption>
</figure>
