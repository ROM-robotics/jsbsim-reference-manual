---
title: Class hierarchy
description: JSBSim's API class hierarchy.
---

# Class Hierarchy (Class ဖွဲ့စည်းပုံ အစီအစဉ်)

!!! note "TODO"

    စာမျက်နှာ အကြောင်းအရာများကို ပြည့်စုံစွာ ဖြည့်စွက်ရန်။


```cpp
fdmex = new FGFDMExec( /* ... */ ); // (1) Instantiation
result = fdmex->LoadModel( /* ... */ ); // (2) Model loading
```
<figure markdown>
  ![FGJSBBase Diagram](../assets/img/Class_Diagram_FGJSBBase.png){: .center width="95%" }
  <figcaption>
    FGJSBBase class ၏ class diagram။
  </figcaption>
</figure>

<figure markdown>
  ![FGJSBBase Diagram](../assets/img/Call_Diagram_FGFDMExec_Initialize.png){: .center width="95%" }
  <figcaption>
    FGFDMExec::Initialize function ၏ call graph။
  </figcaption>
</figure>

