---
title: Frames of reference
description: Frames of reference in JSBSim.
---

# Frames of Reference (ရည်ညွှန်းဘောင်များ)

Configuration file syntax ၏ ဖော်ပြချက်ထဲသို့ မဝင်ရောက်မီ၊ (*i*) လေယာဉ်ပေါ်ရှိ ပစ္စည်းများ၏ တည်နေရာကို ဖော်ပြရာတွင်၊ (*ii*) space ထဲရှိ လေယာဉ်၏ position နှင့် orientation နှင့် သက်ဆိုင်သော condition များကို သတ်မှတ်ရာတွင်၊ သို့မဟုတ် (*iii*) flight condition တစ်ခုအတွက် input များ သတ်မှတ်ရာတွင် အသုံးပြုသော frame of reference (ရည်ညွှန်းဘောင်) အချို့၏ အခြေခံအချက်အလက်ကို ကျွန်ုပ်တို့ နားလည်ထားရန် လိုအပ်ပါသည်။

[Wikipedia ၏ axes convention အကြောင်း](https://en.wikipedia.org/wiki/Axes_conventions) တွင် ပိုမိုလေ့လာနိုင်ပါသည်။

## Structural Frame သို့မဟုတ် "Construction" Frame

ဤ frame သည် manufacturer တစ်ခု၏ ဘုံ reference frame ဖြစ်ပြီး၊ center of gravity, wheel အားလုံး၏ တည်နေရာ, pilot eye-point, point mass, thruster စသည်တို့ကဲ့သို့ လေယာဉ်ပေါ်ရှိ point များကို သတ်မှတ်ရန် အသုံးပြုပါသည်။ JSBSim aircraft configuration file ထဲရှိ item များကို ဤ frame ကို အသုံးပြု၍ တည်နေရာ သတ်မှတ်ထားပါသည်။

Structural frame တွင်၊ X-axis သည် fuselage length တစ်လျှောက် run သွားပြီး tail ဆီသို့ ညွှန်ပါသည်၊ Y-axis သည် fuselage မှ right wing ဆီသို့ ညွှန်ပါသည်၊ ထို့ပြင် Z-axis သည် upward direction အတွက် positive ဖြစ်ပါသည်။ ပုံမှန်အားဖြင့်၊ ဤ frame အတွက် origin $O_\mathrm{C}$ သည် လေယာဉ်ရှေ့ဘက် (nose ၏ အစွန်းတွင်၊ single engine လေယာဉ်တစ်စင်းအတွက် firewall တွင်၊ သို့မဟုတ် nose ရှေ့တွင် ခပ်ဝေးဝေး) တွင် တည်ရှိပါသည်။ ဤ frame ကို $\mathcal{F}_\mathrm{C} = \{O_\mathrm{C}, x_\mathrm{C}, y_\mathrm{C}, z_\mathrm{C}\}$ ဟု မကြာခဏ အမည်ပေးလေ့ရှိပါသည်။

<figure markdown>
  ![Construction axes](../../assets/img/ac_construction_axes.svg){: .center width="90%" }
  <p markdown="span">
    Origin $O_\mathrm{C}$ ပါသော လေယာဉ် structural (သို့မဟုတ် construction) ရည်ညွှန်းဘောင်။ Structural frame axis များဖြစ်သော $x_\mathrm{C}$, $y_\mathrm{C}$, နှင့် $z_\mathrm{C}$ အပြင်၊ standard body frame axis များဖြစ်သော $x_\mathrm{B}$, $y_\mathrm{B}$, နှင့် $z_\mathrm{B}$ ကိုလည်း center of mass $G$ တွင် origin ရှိအောင် ပြသထားပါသည်။ Pilot ၏ eye-point ကို $P_\mathrm{EP}$ တွင် ထားရှိပါသည်။
  </p>
</figure>

X-axis သည် ပုံမှန်အားဖြင့် fuselage centerline နှင့် ဖြစ်တည်ပြီး thrust axis နှင့်လည်း မကြာခဏ ဖြစ်တည်ပါသည် (ဥပမာအားဖြင့်၊ single engine propeller လေယာဉ်တွင် propeller hub ကို ဖြတ်သန်းပါသည်)။ $x_\mathrm{C}$ axis တစ်လျှောက်ရှိ position များကို stations ဟု ခေါ်ပါသည်။ $z_\mathrm{C}$ axis တစ်လျှောက်ရှိ position များကို waterline positions ဟု ခေါ်ပါသည်။ $y_\mathrm{C}$ axis တစ်လျှောက်ရှိ position များကို buttline positions ဟု ခေါ်ပါသည်။

<figure markdown>
  ![Construction axes](../../assets/img/c172x_blender.png){: .center width="70%" }
  <p markdown="span">
    3D modeling software Blender မှ ရိုက်ထားသော screenshot တစ်ပုံ။ Scene တွင် ၎င်း၏ structural frame $\mathcal{F}_\mathrm{C} = \{O_\mathrm{C}, x_\mathrm{C}, y_\mathrm{C}, z_\mathrm{C}\}$ ပါသော Cessna 172 model တစ်ခု ပြသထားပါသည်။ ဤကိစ္စတွင် origin $O_\mathrm{C}$ သည် dashboard အနီး cockpit အတွင်းတွင် တည်ရှိပါသည်။
  </p>
</figure>

JSBSim-modeled လေယာဉ်တစ်စင်းအတွက် origin ကို မည်သည့်နေရာတွင်မဆို ထားနိုင်ကြောင်း သတိပြုပါ၊ အကြောင်းမှာ JSBSim သည် internally CG နှင့် object အမျိုးမျိုးအကြား *relative distance* ကိုသာ အသုံးပြုပြီး — absolute location များကို အသုံးမပြုသောကြောင့် ဖြစ်ပါသည်။

<figure markdown>
  ![Center of gravity](../../assets/img/ac_center_of_gravity.svg){: .center width="90%" }
  <p markdown="span">
    Construction frame တစ်ခုတွင် ဆုံးဖြတ်ထားသော center of gravity (CG) position, point $G$။
  </p>
</figure>

<figure markdown>
  ![Ground reaction](../../assets/img/c172_ground_reaction.svg){: .center width="90%" }
  <p markdown="span">
    Construction frame တည်နေရာများ၏ အနေအထားဖြင့် ground contact point များ၏ သတ်မှတ်ချက်။
  </p>
</figure>

<figure markdown>
  ![Key locations](../../assets/img/c172_sideview.svg){: .center width="70%" }
  <p markdown="span">
    Structural frame ရှိ key point location နှစ်ခု $P_\mathrm{ARP}$ နှင့် $P_\mathrm{CG,EW}$၊ အသီးသီး aerodynamic moment များ၏ pole နှင့် airframe ၏ Empty Weight CG တို့ ဖြစ်ပါသည်။ Wing root profile ၏ ပုံသဏ္ဍာန်နှင့် ၎င်း၏ chord ကိုလည်း ပုံဖော်ပြထားပါသည်။
  </p>
</figure>

<figure markdown>
  ![Key locations](../../assets/img/c172_perspective_view_left.svg){: .center width="70%" }
  <p markdown="span">
    Point $P_\mathrm{CG,EW}$ အပြင်၊ အရေးကြီးသော တည်နေရာနှစ်ခုဖြစ်သည့် $P_\mathrm{Pilot}$ နှင့် $P_\mathrm{Right\,Pass}$ ကို ပြသထားပြီး၊ ဤနေရာများတွင် pilot နှင့် right passenger ၏ mass ထပ်ဆောင်းနှစ်ခု စုစည်းထားပါသည်။
  </p>
</figure>

## Body Frame

JSBSim တွင်၊ body frame သည် structural frame နှင့် ဆင်တူသော်လည်း $y_\mathrm{C}$ ပတ်လည် 180 degree rotate လုပ်ထားပြီး origin ကို CG နှင့် ဖြစ်တည်စေထားပါသည်။ ပုံမှန်အားဖြင့်၊ body frame ကို လေယာဉ်၏ center of mass $G$ ၏ position နှင့် longitudinal construction axis $x_\mathrm{C}$ ၏ direction ကို သိရှိခြင်းဖြင့် သတ်မှတ်ပါသည်။ Axis $x_\mathrm{B}$ ကို $G$ မှ စတင်ပြီး $x_\mathrm{C}$ နှင့် parallel ဖြစ်ကာ $G$ မှ fuselage nose ဆီသို့ positive verse ရှိအောင် ရွေးချယ်ရပါမည်။

Body axis frame ကို $\mathcal{F}_\mathrm{B} = \{G, x_\mathrm{B}, y_\mathrm{B}, z_\mathrm{B}\}$ ဟု မကြာခဏ ခေါ်ပါသည်။ $x_\mathrm{B}$ axis ကို *roll axis* ဟု ခေါ်ပြီး ရှေ့ဆီသို့ ညွှန်ပါသည်၊ $y_\mathrm{B}$ axis ကို *pitch axis* ဟု ခေါ်ပြီး right wing ဆီသို့ ညွှန်ပါသည်၊ $z_\mathrm{B}$ axis ကို *yaw axis* ဟု ခေါ်ပြီး fuselage ၏ ဗိုက်ဘက် (belly) ဆီသို့ ညွှန်ပါသည်။

<figure markdown>
  ![Body axes](../../assets/img/ac_body_axes.svg){: .center width="90%" }
  <p markdown="span">
    Center of gravity $G$ တွင် origin ရှိသော standard လေယာဉ် body axis frame။
  </p>
</figure>

Body frame တွင် လေယာဉ်၏ force များနှင့် moment များကို ပေါင်းစည်းပြီး ထွက်ပေါ်လာသော acceleration များကို integrate လုပ်ကာ velocity များ ရရှိစေပါသည်။

## Stability Frame သို့မဟုတ် "Aerodynamic" Frame

ဤ frame ကို airframe နှင့် ဆက်စပ်သော relative wind vector ၏ instantaneous orientation ကို အခြေခံ၍ သတ်မှတ်ပါသည်။ ရိုးရှင်းစေရန် Earth နှင့် ဆက်စပ်၍ လေ ငြိမ်နေသည် (no wind) ဟု ယူဆပါက၊ $\boldsymbol{V}$ သည် Earth-fixed observer တစ်ဦးနှင့် ဆက်စပ်သော လေယာဉ် center-of-mass velocity vector ဖြစ်ပြီး (relative motion ကို မီးမောင်းထိုးပြရန် $\boldsymbol{V}_\mathrm{CM/E}$ ဟုလည်း ခေါ်ပါသည်)၊ ထို့နောက် $-\boldsymbol{V}$ သည် relative wind velocity ဖြစ်ပြီး $V = \|\boldsymbol{V}\|$ သည် airspeed ဖြစ်ပါသည်။

$\mathcal{F}_\mathrm{A} = \{ G, x_\mathrm{A}, y_\mathrm{A}, z_\mathrm{A} \}$ ဟု အမည်ပေးထားသော frame တွင်၊ axis $x_\mathrm{A}$ သည် လေယာဉ် symmetry plane $x_\mathrm{B} z_\mathrm{B}$ ပေါ်သို့ project လုပ်ထားသော relative wind vector ဆီသို့ ညွှန်ပါသည်။ Axis $y_\mathrm{A}$ သည် right wing ဆီသို့ ဆက်လက် ညွှန်နေပြီး body axis $y_\mathrm{B}$ နှင့် ဖြစ်တည်ပါသည်၊ axis $z_\mathrm{A}$ ကလည်း right-hand system ကို ပြီးမြောက်စေပါသည်။

<figure markdown>
  ![Alpha and beta](../../assets/img/ac_aero_axes.svg){: .center width="90%" }
  <p markdown="span">
    Aerodynamic angle $\alpha_\mathrm{B}$ နှင့် $\beta$ ကို သတ်မှတ်ပေးသော Aerodynamic frame။
  </p>
</figure>

Axis နှစ်ခုဖြစ်သော $x_\mathrm{A}$ နှင့် $z_\mathrm{A}$ တို့သည် definition အားဖြင့် လေယာဉ် symmetry plane ထဲတွင် ပါဝင်ကြသော်လည်း၊ relative wind velocity vector $\boldsymbol{V}$ ၏ orientation သည် vehicle နှင့် ဆက်စပ်၍ ပြောင်းလဲနိုင်သောကြောင့် *ပျံသန်းမှုအတွင်း ၎င်းတို့ rotate ဖြစ်နိုင်ပါသည်*။ အထက်ပါပုံသည် aerodynamic frame ကို မည်သို့ တည်ဆောက်ထားသည်ကို ပြသထားပါသည်။ Axis နှစ်ခုဖြစ်သော $x_\mathrm{A}$ နှင့် $x_\mathrm{B}$ အကြား ထောင့်သည် လေယာဉ် angle of attack $\alpha_\mathrm{B}$ ဖြစ်ပါသည်။ $\boldsymbol{V}$ ၏ instantaneous direction နှင့် $x_\mathrm{B} z_\mathrm{B}$ plane ပေါ်သို့ ၎င်း၏ projection တို့ ဖွဲ့စည်းသော ထောင့်သည် sideslip angle $\beta$ ဖြစ်ပါသည်။

ဤ frame ကို manual အချို့တွင် stability frame ဟု ခေါ်ကြသော်လည်း၊ instantaneous aerodynamic resultant force $\mathcal{F}_\mathrm{A}$ ၏ axis $z_\mathrm{A}$ ပေါ်သို့ projection $Z_\mathrm{A}$ သည် aerodynamic lift ကို သတ်မှတ်ပေးသောကြောင့် ဤနေရာတွင် 'aerodynamic frame' ဟုလည်း ခေါ်ထားပါသည်။ အထူးသဖြင့်၊ lift $L$ သည် $\mathcal{F}_\mathrm{A}$ ၏ $z_\mathrm{A}$ တစ်လျှောက်ရှိ component ဖြစ်သော $-L$ ဖြစ်ကြောင်း၊ ဆိုလိုသည်မှာ $Z_\mathrm{A}=-L$ ဖြစ်ပါသည်။

အထက်ပါ observation ကို visualize ပြုလုပ်ရန်၊ flight mechanics တွင် လေ့လာလေ့ရှိသော maneuver တစ်ခုကို သုံးသပ်ကြည့်ပါ- zero-sideslip (သို့မဟုတ် 'coordinated') ဖြစ်ပြီး altitude ပုံသေ၊ airspeed တည်ငြိမ်သော turn (turn) တစ်ခု ဖြစ်ပါသည်။ ဤအခြေအနေတွင် wing များသည် bank လုပ်ထားပြီး lift ကလည်း banked ဖြစ်နေပါသည်။ ထို turn တွင် $\mathcal{F}_\mathrm{A}$ သည် banked ဖြစ်ပြီး $x_\mathrm{A}$ ကို horizontal အနေအထားတွင် ထားရှိပါသည်။ ယေဘုယျအားဖြင့်၊ lift ကို vector တစ်ခုအနေဖြင့် ရှုမြင်ပါက လေယာဉ် symmetry plane ထဲတွင် အမြဲတမ်း သတ်မှတ်ထားပါသည်။

<figure markdown>
  ![Level turns](../../assets/img/three_d_forces_level_turn.svg){: .center width="90%" }
  <p markdown="span">
	Altitude ပုံသေတွင် steady coordinated turn တစ်ခုတွင် banked ဖြစ်နေသော lift။ Bank angle $\phi_\mathrm{W}$ သည် relative wind velocity vector ပတ်လည် rotation တစ်ခု ဖြစ်ပါသည်။ Velocity vector သည် North နှင့် ညီထွေဖြစ်နေချိန်တွင် motion ကို freeze (အေးခဲ) ထားပါသည်။ Coordinated turn ဆိုသည်မှာ $\beta=0$ ဖြစ်ခြင်းကို ဆိုလိုပြီး constant altitude ဆိုသည်မှာ $x_\mathrm{A}$ ကို horizontal အနေအထားတွင် ထားရှိခြင်းကို ဆိုလိုပါသည်။
  </p>
</figure>

*မှတ်ချက်* --- Dynamic stability study များတွင် 'stability frame' ဟု ရည်ညွှန်းသောအရာသည် အထက်တွင် ဖော်ပြခဲ့သော aerodynamic frame နှင့် အနည်းငယ် ကွာခြားပါသည်- Aircraft flight dynamics နှင့် stability convention များတွင် stability frame သည် initial symmetrical, steady, wings-level, constant altitude flight condition တစ်ခုနှင့် သက်ဆိုင်၍ သတ်မှတ်ထားသော body-fixed frame အမျိုးအစားတစ်ခုမျှသာ ဖြစ်ပါသည်။ ဤ condition က $x_\mathrm{S}$ ၏ direction ကို ပေးပါသည် (ထို particular flight attitude တွင် $x_\mathrm{A}$ နှင့် ဖြစ်တည်ပါသည်)။ ထို့ကြောင့်၊ dynamic stability study များတွင် stability frame သည် aerodynamic frame နှင့် မတူဘဲ vehicle နှင့် ချိတ်ဆက်ထား (fixed) ပါသည်။

JSBSim တွင် stability frame $\mathcal{F}_\mathrm{S} = \{ G, x_\mathrm{S}, y_\mathrm{S}, z_\mathrm{S} \}$ ဆိုသော concept ကို aerodynamic frame ကို ဆိုလိုရန် အသုံးပြုပါသည်။

## Earth-Centered Inertial Frame (ECI) နှင့် Earth-Centered Earth-Fixed Frame (ECEF)

Earth-Centered Inertial frame (သို့မဟုတ် ရိုးရှင်းစွာ 'inertial frame') $\mathcal{F}_\mathrm{ECI} = \{ O_\mathrm{ECI}, x_\mathrm{ECI}, y_\mathrm{ECI}, z_\mathrm{ECI} \}$ ၏ origin ကို Earth ၏ center တွင် fixed ထားပါသည်။ ၎င်း၏ cartesian axis များသည် star များနှင့် ဆက်စပ်၍ fixed ဖြစ်နေပြီး၊ လေယာဉ် (သို့မဟုတ် spacecraft) ၏ equations of motion ကို အရိုးရှင်းဆုံး ဖော်ပြနိုင်သော reference frame တစ်ခု ပေးပါသည်။ Positive $z_\mathrm{ECI}$ axis သည် Earth ၏ geographic North Pole ကို ဖြတ်သန်းပါသည်။ $x_\mathrm{ECI}$ နှင့် $y_\mathrm{ECI}$ axis များသည် equatorial plane ထဲတွင် တည်ရှိပါသည်။ Axis $x_\mathrm{ECI}$ သည် vernal equinox တွင် Sun ၏ center of mass မှ Earth ၏ orbit position ဆီသို့ မျဉ်းတစ်ကြောင်းနှင့် parallel အမြဲတမ်း ဖြစ်ပါသည်။ ECI system ကို နောက်ပုံတွင် ပြသထားပါသည်။

<figure markdown>
  ![Inertial frame](../../assets/img/inertial_frame.svg){: .center width="60%" }
  <p markdown="span">
	Earth-Centered Inertial (ECI) frame နှင့် Earth-Centered Earth-Fixed (ECEF) frame။
  </p>
</figure>

$x_\mathrm{ECEF}$, $y_\mathrm{ECEF}$, နှင့် $z_\mathrm{ECEF}$ ဟု label တပ်ထားသော Earth-Centered, Earth-Fixed (ECEF) ရည်ညွှန်းဘောင်၏ axis များကိုလည်း အထက်ပါပုံတွင် ဖော်ပြထားပါသည်။ ECEF coordinate axis များသည် Earth နှင့် ဆက်စပ်၍ fixed ဖြစ်နေပါသည်။ ဤ cartesian system ၏ origin $O_\mathrm{ECEF}$ သည် inertial frame ကဲ့သို့ပင် earth ၏ mass center တွင် တည်ရှိပါသည်။ $z_\mathrm{ECEF}$ axis သည် Earth ၏ spin axis တစ်လျှောက်တွင်လည်း တည်ရှိပြီး $z_\mathrm{ECI}$ နှင့် ဖြစ်တည်ပါသည်။ $x_\mathrm{ECEF}$ နှင့် $y_\mathrm{ECEF}$ axis နှစ်ခုစလုံးသည် equatorial plane ထဲတွင် တည်ရှိပြီး၊ positive $x_\mathrm{ECEF}$ axis သည် prime meridian (Greenwich Meridian) ကို ဖြတ်သန်းပါသည်။ ECEF frame သည် angular velocity $\omega_\mathrm{E}$ ဖြင့် Inertial frame ၏ $z_\mathrm{ECI}$ axis ပတ်လည် counter-clockwise rotate ပြုလုပ်ပါသည်။ Earth angular rate $\omega_\mathrm{E}$ သည် ခန့်မှန်းခြေအားဖြင့် $2\pi/24$ radians/hour ညီမျှပါသည်။

## North-Oriented Tangent Frames

Earth ၏ surface ကို mathematical representation (*spheroid* သို့မဟုတ် approximate လုပ်ထားသော sphere) တစ်ခုအနေဖြင့် ယူဆသည့်အခါ *tangent-plane* coordinate system တစ်ခုကို သတ်မှတ်နိုင်ပါသည်။ Surface $O_\mathrm{E}$ ပေါ်ရှိ interest point တစ်ခုနှင့် tangent ဖြစ်သော plane တစ်ခုကို reference အဖြစ် ယူပါသည်။ *North-Oriented Tangent Frame* ဟု ခေါ်သော geographic system $\mathcal{F}_\mathrm{E} = \{ O_\mathrm{E}, x_\mathrm{E}, y_\mathrm{E}, z_\mathrm{E}\}$ ၏ origin ကို interest point $O_\mathrm{E}$ တွင် fixed ထားပြီး ၎င်း၏ plane $x_\mathrm{E} y_\mathrm{E}$ ကို tangent plane နှင့် ဖြစ်တည်စေထားပါသည်။ Axis $x_\mathrm{E}$ သည် geographic North ဆီသို့ ညွှန်ပြီး၊ axis $y_\mathrm{E}$ သည် East ဆီသို့ ညွှန်ပါသည်။ နောက်ဆုံးအနေဖြင့်၊ axis $z_\mathrm{E}$ သည် spheroid normal နှင့် parallel ဖြစ်ကာ အောက်ဘက် (downward) ဆီသို့ ညွှန်ပါသည် (Spheroid အစား approximate လုပ်ထားသော sphere ကို အသုံးပြုပါက Earth ၏ center ဆီသို့ ညွှန်ပါသည်)။ ဤအကြောင်းကြောင့် frame $\mathcal{F}_\mathrm{E}$ ကို *tangent NED* frame (North-East-Down) ဟုလည်း ခေါ်ပါသည်။

<figure markdown>
  ![ECI and ECEF frames](../../assets/img/earth_frames.svg){: .center width="60%" }
  <p markdown="span">
	Earth-Centered Earth-Fixed (ECEF) frame, geographic coordinate များ, Tangent (T) frame, နှင့် local Vertical (V) frame။
  </p>
</figure>

## Local-Vertical Local-Level Frame သို့မဟုတ် Local NED Frame

Local vertical frame $\mathcal{F}_\mathrm{V} = \{ G, x_\mathrm{V}, y_\mathrm{V}, z_\mathrm{V}\}$ သည် space ထဲရှိ လေယာဉ်၏ orientation နှင့် မသက်ဆိုင်ဘဲ၊ Earth-fixed observer တစ်ဦးနှင့် ဆက်စပ်သော ၎င်း၏ CG position ဖြင့်သာ သတ်မှတ်ထားပါသည်။ $G_\mathrm{GT}$ ကို ground ပေါ်သို့ project လုပ်ထားသော CG ('ground tracked') ဟု ယူဆပါက၊ coordinate plane $x_\mathrm{V} y_\mathrm{V}$ သည် $G_\mathrm{GT}$ တွင် Earth ၏ surface ကို local tangent ဖြစ်သော plane တစ်ခုနှင့် parallel ဖြစ်ပါသည် --- ဆိုလိုသည်မှာ $O_\mathrm{E} \equiv G_\mathrm{GT}$ ဖြစ်သော plane $x_\mathrm{E} y_\mathrm{E}$ ဖြစ်ပါသည်။ ထို့နောက်၊ axis $x_\mathrm{V}$ သည် geographic North ဆီသို့ ညွှန်ပြီး၊ axis $y_\mathrm{V}$ သည် East ဆီသို့ ညွှန်ပါသည်။ နောက်ဆုံးအနေဖြင့်၊ axis $z_\mathrm{V}$ သည် Earth ၏ center ဆီသို့ အောက်ဘက်ဆီသို့ ညွှန်ပါသည်။ ဤအကြောင်းကြောင့် frame $\mathcal{F}_\mathrm{V}$ ကို *local NED* (vehicle-carried) frame ဟုလည်း ခေါ်ပါသည်။

<figure markdown>
  ![Local vertical axes](../../assets/img/ac_local_vertical_axes.svg){: .center width="90%" }
  <p markdown="span">
	လေယာဉ် body frame နှင့် local vertical frame (NED frame)။ လေယာဉ် Euler angle များကိုလည်း ပြသထားပါသည်- heading angle $\psi$ (ပုံတွင် negative ဖြစ်နေသည်)၊ elevation angle $\theta$၊ နှင့် roll angle $\phi$။
  </p>
</figure>

NED convention က လေယာဉ်၏ weight သည် frame $\mathcal{F}_\mathrm{V}$ တွင် $(0,0,mg)$ component ရှိသော force တစ်ခု ဖြစ်ကြောင်း သေချာစေပါသည်၊ ဤနေရာတွင် $m$ သည် လေယာဉ်၏ mass ဖြစ်ပြီး $g$ သည် gravitational acceleration ဖြစ်ပါသည်။

အထက်ပါပုံတွင် frame နှစ်ခု $\mathcal{F}_\mathrm{V}$ နှင့် $\mathcal{F}_\mathrm{B}$ ပါသော လေယာဉ်တစ်စင်းကို ပြသထားပါသည်။ Local NED frame နှင့် ဆက်စပ်၍ body frame ၏ orientation ကို သတ်မှတ်ပေးသော Euler angle များကို *လေယာဉ် Euler angle* ဟု ခေါ်ပါသည်။ Atmospheric flight vehicle များအတွက် Euler angle များကို သတ်မှတ်ရန် အသုံးပြုသော rotation sequence မှာ '3-2-1' ဖြစ်ပါသည်။ ဤသည်က Earth နှင့် ဆက်စပ်သော observer တစ်ဦးနှင့် ဆက်နွယ်၍ *heading* angle $\psi$, *elevation* angle $\theta$, နှင့် *roll* angle $\phi$ တို့ကို သတ်မှတ်ပေးပါသည်။

<figure markdown>
  ![Euler gimbal](../../assets/img/ac_euler_gimbal.svg){: .center width="60%" }
  <p markdown="span">
	လေယာဉ်တစ်စင်းအတွက် Euler angle sequence။ Frame $\mathcal{F}_\mathrm{E} = \{ O_\mathrm{E}, x_\mathrm{E}, y_\mathrm{E}, z_\mathrm{E}\}$ သည် Earth-fixed NED coordinate system တစ်ခု ဖြစ်ပြီး၊ origin $O_\mathrm{E}$ ကို ground ပေါ်တွင် (သို့မဟုတ် sea level တွင်) တစ်နေရာရာတွင် ထားရှိကာ plane $x_\mathrm{E} y_\mathrm{E}$ ကို Earth surface နှင့် tangent ဖြစ်စေထားပါသည်။ Ground track point $G_\mathrm{GT}$ သည် $O_\mathrm{E}$ နှင့် သိပ်မဝေးလှပါက၊ Earth frame $\mathcal{F}_\mathrm{E}$ axis များသည် local NED frame $\mathcal{F}_\mathrm{V} = \{ G, x_\mathrm{V}, y_\mathrm{V}, z_\mathrm{V}\}$ ၏ axis များနှင့် parallel ဖြစ်ပါသည်။
  </p>
</figure>

## Wind Frame

Lift အပြင်၊ instantaneous aerodynamic resultant force vector $\mathcal{F}_\mathrm{A}$ တွင် $z_\mathrm{A}$ သည် တတိယ axis ဖြစ်သော ရည်ညွှန်းဘောင်တစ်ခုတွင် component နှစ်ခု ထပ်မံပါရှိပါသည်။ ဤ frame ကို *wind frame* $\mathcal{F}_\mathrm{W} = \{ G, x_\mathrm{W}, y_\mathrm{W}, z_\mathrm{W}\}$ ဟု ခေါ်ပါသည်။

Wind frame ကို $x_\mathrm{W}$ axis ကို relative wind တစ်လျှောက် motion direction ဖြင့် positive verse ရှိအောင် ယူ၍ သတ်မှတ်ပါသည်။ ဆိုလိုသည်မှာ $x_\mathrm{W}$ သည် vector $\boldsymbol{V}$ နှင့် superimpose ဖြစ်ပါသည်။ $\mathcal{F}_\mathrm{W}$ ၏ တတိယ axis ကို lift line of action တစ်လျှောက်ယူပါသည်၊ ဆိုလိုသည်မှာ $z_\mathrm{W} \equiv z_\mathrm{A}$ ဖြစ်ပါသည်။ နောက်ဆုံးအနေဖြင့်၊ ဒုတိယ axis $y_\mathrm{W}$ ကို right-handed triad ပြီးမြောက်စေရန် ရွေးချယ်ပါသည်။ Wind frame ၏ တတိယ axis သည် airframe symmetry plane ('reference plane' ဟုလည်း ခေါ်) ထဲတွင် အမြဲတမ်း ရှိနေပါသည်။ Wind axis သုံးခုလုံးသည် relative wind $-\boldsymbol{V}$ နှင့် ဆက်စပ်၍ လေယာဉ်၏ attitude ပြောင်းလဲနေမှုကြောင့် body axis များနှင့် ဆက်စပ်၍ rotate ဖြစ်ပါသည်။

$\boldsymbol{V}$ direction တစ်လျှောက် force vector $\mathcal{F}_\mathrm{A}$ ၏ component $X_\mathrm{W}$ သည် aerodynamic drag ကို သတ်မှတ်ပေးပါသည်- Drag $D$ သည် $X_\mathrm{W}=-D$ ဖြစ်ပါသည်။ Sideslip angle $\beta$ သုညမဟုတ်သည့်အခါ၊ lateral axis $y_\mathrm{W}$ တစ်လျှောက် $\mathcal{F}_\mathrm{A}$ ၏ တတိယ component သုညမဟုတ်သည့်အရာ ဖြစ်ပေါ်လာပါသည်၊ ဆိုလိုသည်မှာ side force component $Y_\mathrm{W}$ ဖြစ်ပါသည်။

Sideslip angle $\beta$ သုညဖြစ်သည့်အခါ၊ wind frame နှင့် aerodynamic frame တို့ ဖြစ်တည်ပါသည်။ ဤအခြေအနေတွင်သာ $y_\mathrm{W}$ သည် $y_\mathrm{A}$ နှင့် $y_\mathrm{B}$ နှင့် ဖြစ်တည်နေသောကြောင့် reference plane $x_\mathrm{B} z_\mathrm{B}$ နှင့် normal ဖြစ်ပါသည်။

အောက်ပါပုံသည် calm air တွင် climbing flight ပြုနေသော လေယာဉ်တစ်စင်းအတွက် standard ရည်ညွှန်းဘောင်များကို ပြသထားပါသည်။ Wind frame $\mathcal{F}_\mathrm{W}$ ကို ထောင့် $-\beta$ ဖြင့် $z_\mathrm{W}$ ပတ်လည် rotate လုပ်သည့်အခါ aerodynamic frame $\mathcal{F}_\mathrm{A}$ နှင့် superimpose ဖြစ်စေနိုင်ပါသည်။

<figure markdown>
  ![3D defs](../../assets/img/three_d_definitions.svg){: .center width="90%" }
  <p markdown="span">
	Calm air တွင် climbing flight ပြုနေသော လေယာဉ်တစ်စင်း၏ standard ရည်ညွှန်းဘောင်များ။ CG velocity vector $\boldsymbol{V}$ သည် horizontal plane နှင့် flight path angle $\gamma$ ကို ဖွဲ့စည်းပါသည်။ Standard aerodynamic resultant force component သုံးခုဖြစ်သော $D$, $L$ နှင့် $Y_\mathrm{A}$ ကိုလည်း ပြသထားပါသည်။
  </p>
</figure>

ဆက်လက်၍၊ wind frame $\mathcal{F}_\mathrm{W}$ ကို ဦးစွာ ထောင့် $-\beta$ ဖြင့် $z_\mathrm{W}$ ပတ်လည် rotate လုပ်ပြီး ထို့နောက် ထောင့် $\alpha_\mathrm{B}$ ဖြင့် axis $y_\mathrm{A}$ ပတ်လည် rotate လုပ်သည့်အခါ body frame $\mathcal{F}_\mathrm{B}$ နှင့် superimpose ဖြစ်စေနိုင်ပါသည်-

$$
\mathcal{F}_\mathrm{W} \stackrel{-\beta \, \curvearrowright \, z_\mathrm{W}}{ \longrightarrow } \mathcal{F}_\mathrm{A} \stackrel{\alpha_\mathrm{B} \, \curvearrowright \, y_\mathrm{A}}{ \longrightarrow } \mathcal{F}_\mathrm{B}
\label{eq:FW:To:FB}
$$

Body axis များတွင် aerodynamic resultant force ၏ component များကို ထို့နောက် အောက်ပါအတိုင်း ဖော်ပြနိုင်ပါသည်-

$$
\left\{\begin{matrix}
  X_\mathrm{B} \\ Y_\mathrm{B} \\ Z_\mathrm{B}
\end{matrix}\right\} =
\left[\begin{matrix}
  \cos\alpha_\mathrm{B} & 0 & -\sin\alpha_\mathrm{B} \\
  0 & 1 & 0 \\
  \sin\alpha_\mathrm{B} & 0 & \cos\alpha_\mathrm{B}
\end{matrix}\right]
  \left[\begin{matrix}
    \cos\beta & \sin(-\beta) & 0 \\
    -\sin(-\beta) & \cos\beta & 0 \\
    0 & 0 & 1
  \end{matrix}\right]
  \left\{\begin{matrix}
    -D \\ Y_\mathrm{W} \\ -L
  \end{matrix}\right\}
\label{eq:DYL:To:XYZB}  
$$

Drag, side force နှင့် lift တို့ဖြင့် ဖော်ပြထားပါသည်။

