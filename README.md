# A glance at avsdbgp_3v3 IP

**avsdbgp_3v3** is a Bandgap Reference circuit, which is used to generate a constant voltage reference in analog domain which is independent of temperatarure and supply voltage variations.

The objective was to achieve some specifications using only **open-source tools** with the Flow/FreePDKs provided by **VLSI Computer Architecture Research Group** [(**VLSIARCH**)](https://vlsiarch.ecen.okstate.edu/) at **Oklahoma State University** [(**OSU**)](https://go.okstate.edu/).  

To get an basic idea about this **IP**, the working principle, basic implementation, applications and significance, kindly go thru [**this**](/Prelayout/Files/BGR.pdf)

## Symbol and Pin descriptions

<p align="center">
  <img width="700" height="500" src="/Images/Circuit_and_Specs/symbol.jpg">
</p>


## Parameters

To view the specifications, go through [this](https://github.com/ankursah5/avsdbgp_3v3/blob/master/Prelayout/Files/specs.md)

**Below is the compiled list of parameters according to specifications**

| Parameter| Description| Min | Type | Max | Unit | Condition |
| :---:  | :-: | :-: | :-: | :---:  | :-: | :-: |
|RL|Load resistance| 100|||Mohm|T=-40 to 125C|
|CL|Load capacitance|||1|pF|T=40 to 85C|
|Vbgp|Output Reference voltage|1.28464 |1.28|1.28627|V|T=-40 to 140C|
|TC_Vbgp|Temperature Coefficient of Vbgp|-25|5|2|ppm/C|T=-40 to 125C|
|VC_Vbgp|Voltage Coefficient of Vbgp|0.065|0.07|0.08|V|V=2.1 to 6.6, T=-40 to 125C |
|V_Noise|Noise at Vbgp Terminal||||uV rms|Vdd= 3.3V T=27C, f=0.1 to 10Khz|
|T_start|Start up time| |||uS|Vdd=27c, T=27C, Cl=50pF|
|VDD|Supply Voltage|2.1|3.3|3.6|V|T=-40C to 125C|


   
 ##  Future work and limitations
 
 - The reference voltage needs to needs to more accurate with specifications. 
 - The post layout spice file has parasitic BJTs. Their origin shall be studied and tried to get rid off. 
 - The Bipolar models are imported from LTspice.
 - The futurework involves working/obtaining on a compatible **Bipolar** model with osu180nm tech, Which is not included in OSU libraries. 
 
 # IP usage
 
 ## Tools needed to view and simulate this IP
 
  <img align="left" width="45" height="45" src=/Prelayout/Logo/logo.jpg>

### 1. Ngspice

[Ngspice](http://ngspice.sourceforge.net/devel.html) is the open source spice simulator for electric and electronic circuits. Ngspice is an open project, there is no closed group of developers.

#### Installing Ngspice in Ubuntu 20.04

 Open the terminal and type the following to install Ngspice
```
$  sudo apt-get install ngspice
```

<img align="left" width="45" height="45" src=/Postlayout/Logo/logo.JPG>

 ### 2. Magic
 
 [Magic](http://opencircuitdesign.com/magic/) is a VLSI layout tool.
 
#### Installing Magic in Ubuntu 20.04

Open the terminal and type the following to install Magic
```
$  wget http://opencircuitdesign.com/magic/archive/magic-8.3.32.tgz
$  tar xvfz magic-8.3.32.tgz
$  cd magic-8.3.28
$  ./configure
$  sudo make
$  sudo make install
```
### Steps to clone this git repository in Unix based systems for simulating waveforms.

Open the terminal and type the following

```
$  sudo apt install -y git
$  git clone https://github.com/ankursah5/avsdbgp_3v3

```
##  Pre-Layout simulations

- To run and view the waveforms, type the following commands after cloning in above step.

 ```
$  cd avsdbgp_3v3/Prelayout/Cir/
$  ngspice
```
- This opens ngspice shell.
- **To plot Vref vs Temperature (-40 to 140C) at Rload = 100Mohms**, Type the following in Ngspice shell and press enter.

```
ngspice 1 -> source 1bgr_tv.cir
```

 <p align="center">
  <img width="800" height="500" src="/Images/Pre_layout/tv.jpg">
</p>

- **To Plot Vref vs Vdd (2V to 4V) at Rload=100Mohms**, Type the following in Ngspice shell and press enter.

```
ngspice 1 -> source 2bgr_vv.cir
```

<p align="center">
  <img width="800" height="500" src="/Images/Pre_layout/vv.jpg">
</p>

- **To plot Temperature Co-efficient of Vref vs Temperature (-40 to 125C) at Rload=100Mohms**,  Type the following in Ngspice shell and press enter.

```
ngspice 1 -> source 3bgr_tc.cir
```

<p align="center">
  <img width="800" height="500" src="/Images/Pre_layout/tc.jpg">
</p>


- **To plot Voltage Co-efficient of Vref vs VDD(2.1V to 3.6V) at Rload=100Mohms**, Type the following in Ngspice shell and press enter.

```
ngspice 1 -> source 4bgr_vc.cir
```

<p align="center">
  <img width="800" height="500" src="/Images/Pre_layout/vc.jpg">
</p>

- **To plot Start-up Votage variation with time using ramp signal**, Type the following in Ngspice shell and press enter.

```
ngspice 1 -> source 5bgr_su.cir
```

<p align="center">
  <img width="800" height="500" src="/Images/Pre_layout/su.jpg">
</p>


##  Post-Layout simulations

- To view the **layout**, type the following comand in continuation with pre-layout simulations,

```
ngspice 1 -> exit
```

- This exits the ngspice shell. 
- In the terminal, type the following commands.

```
$  cd ..
$  cd ..
$  cd Postlayout2/Mags
$  magic -T osu018.tech bgr1.mag
```

<p align="center">
  <img width="1000" height="500" src="/Postlayout2/Images/layout.JPG">
</p>

 - **To run and view the post- layout waveforms**, type the following commands after above steps in terminal.

 ```
$  cd ..
$  cd spice \files/
$  ngspice
```
- This opens ngspice shell.
- **To plot Vref vs Temperature (-40 to 140C) at Rload = 100Mohms**, Type the following in Ngspice shell and press enter.

```
ngspice 1 -> source 1pl_tv.spice
```

 <p align="center">
  <img width="800" height="500" src="/Postlayout2/Images/1tv.JPG">
</p>

- **To Plot Vref vs Vdd (2V to 4V) at Rload=100Mohms**, Type the following in Ngspice shell and press enter.

```
ngspice 1 -> source 2pl_vv.spice
```

<p align="center">
  <img width="800" height="500" src="/Postlayout2/Images/2vv.JPG"">
</p>

- **To plot Temperature Co-efficient of Vref vs Temperature (-40 to 125C) at Rload=100Mohms**,  Type the following in Ngspice shell and press enter.

```
ngspice 1 -> source 3pl_tc.spice
```

<p align="center">
  <img width="800" height="500" src="/Postlayout2/Images/3tc.JPG"">
</p>


- **To plot Voltage Co-efficient of Vref vs VDD(2.1V to 3.6V) at Rload=100Mohms**, Type the following in Ngspice shell and press enter.

```
ngspice 1 -> source 4pl_vc.spice
```

<p align="center">
  <img width="800" height="500" src="/Postlayout2/Images/4vc.JPG"">
</p>

- **To plot Start-up Votage variation with time using ramp signal**, Type the following in Ngspice shell and press enter.

```
ngspice 1 -> source 5pl_su.spice
```

<p align="center">
  <img width="800" height="500" src="/Postlayout2/Images/5su.JPG"">
</p>
 
## Author

**Ankur Sah**

Contact Information
===================================
- ANKUR SAH, 
 M.tech Embedded Systems, NIT Jamshedpur
  ankursah5@gmail.com
- KUNAL GHOSH, 
 Director, VSD Corp. Pvt. Ltd. 
  kunalpghosh@gmail.com
- PHILIPP GÜHRING, 
Software Architect at LibreSilicon Association
  pg@futureware.at
 - Dr. GAURAV TRIVEDI, 
 Co-Principal Investigator, EICT Academy, IIT Guwahati
 trivedi@iitg.ac.in
