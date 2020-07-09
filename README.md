# About avsd_bgr IP

Avsd_bgr is a Bandgap Reference circuit, which is used to generate a constatnt voltage reference in analog domain which is independent of temperatarure and supply voltage variations. 
To get an basic idea about this IP, the working principle, basic implementation, applications and significance, kindly go thru [this](/Prelayout/Files/BGR.pdf)

## Symbol and Pin descriptions

<p align="center">
  <img width="800" height="500" src="Images/Circuit_and_Specs/Symbol.JPG">
</p>


## Parameters


## Typical performance characteristics

1. <p align="center">
  <img width="800" height="500" src="Images/Circuit and Specs/tv.JPG">
  </p>

2. <p align="center">
  <img width="800" height="500" src="Images/Circuit and Specs/vv.JPG">
   </p>

3. <p align="center">
  <img width="800" height="500" src="Images/Circuit and Specs/tc.JPG">
  </p>

4. <p align="center">
  <img width="800" height="500" src="Images/Circuit and Specs/vc.JPG">
  </p>

5. <p align="center">
  <img width="800" height="500" src="Images/Circuit and Specs/su.JPG">
   </p>
   
   
   
   
  
<img align="left" width="45" height="45" src=/Prelayout/Logo/logo.jpg>

## About Ngspice

[Ngspice](http://ngspice.sourceforge.net/devel.html) is the open source spice simulator for electric and electronic circuits. Ngspice is an open project, there is no closed group of developers.

#### Installing Ngspice in Ubuntu 20.04
 - Open terminal.
 - Type `sudo apt-get install ngspice` and press enter.
 
#### Viewing simulation output in ngspice
 - Download the `cir` files from this repository.
 - Go to the downloaded folder.
 - Right click and open terminal.
 - Type `ngspice <filename>.cir` and press enter
 
 # Pre-Layout simulations
 
 ## Output Plots and Values obtained in Ngspice simulations
  To run the `cir` files, migrate to the folder Cir containing `cir` files and write following command in terminal and press enter.
  ```
  ngspice filename.cir
  ```
 ### Plotting Vref vs Temperature (-40 to 140C) at Rload = 100Mohms
 
 <img align ="right" src= "/Ngspice/Specifications from VSD/Temperature variation.JPG" width=" 200">
 
  - replace `filename.cir` with `1bgr_tv.cir`
  
   <p align="center">
  <img width="800" height="500" src="/Ngspice/Outputs/1bgr_tv.JPG">
</p>

  - At temperature -40<sup>o</sup>C, Vref = 1.2835 V
  - At temperature 27<sup>o</sup>C, Vref = 1.2841 V
  - At temperature 140<sup>o</sup>C, Vref = 1.2816 V
  
 ### Vref vs Vdd (2V to 4V) at Rload=100Mohms
 
 <img align ="right" src= "/Ngspice/Specifications from VSD/Voltage variation.JPG" width=" 200">
 
  - replace `filename.cir` with `2bgr_vv.cir`
  
  <p align="center">
  <img width="800" height="500" src="/Ngspice/Outputs/2bgr_vv.JPG">
</p>

 - Vref at 2V Vdd= 1.1916V
 - Vref at 4V Vdd= 1.3335V

### Temperature Co-efficient of Vref vs Temperature (-40 to 140C) at Rload=100Mohms

 <img align ="right" src= "/Ngspice/Specifications from VSD/Temperature coefficient.JPG" width=" 200">

 - replace `filename.cir` with `3bgr_tc.cir`
 
 <p align="center">
  <img width="800" height="500" src="/Ngspice/Outputs/3bgr_tc.JPG">
</p>

 - Range of Temperature co-efficient (approx)-> ( 34 to -108) uV/<sup>o</sup>C
  
### Voltage Co-efficient of Vref vs VDD(2V to 4V) at Rload=100Mohms 

<img align ="right" src= "/Ngspice/Specifications from VSD/Voltage coefficient.JPG" width=" 200">

 - replace `filename.cir` with `4bgr_vc.cir`
 
 <p align="center">
  <img width="800" height="500" src="/Ngspice/Outputs/4bgr_vc.JPG">
</p>

 - Voltage co-efficient of Vref at three different temperatures -40<sup>o</sup>C, 30<sup>o</sup>C and 100<sup>o</sup>C.
 - Range of Voltage Co-efficient-> (0.06 to 0.08)

### Noise level at Vref terminal (expected 25uV rms)
 - replace `filename.cir` with `5bgr_noise.cir`
 
 <p align="center">
  <img width="800" height="500" src="/Ngspice/Outputs/5bgr_noise.JPG">
</p>
 
  - onoise_total = 1.461129e-05 (Output noise voltage over the specified frequency range)


### Start-up Votage variation with time using ramp signal.
 
 - replace `filename.cir` with `6bgr_startuptime1.cir`
 
<img align ="right" src= "/Ngspice/Specifications from VSD/Startup Time Specifications.JPG" width=" 200">

<p align="center">
  <img width="800" height="500" src="/Ngspice/Outputs/6bgr_startuptime1.JPG">
</p>

## Layouts and Spice

### BGR without Bipolar

<p align="center">
  <img width="800" height="500" src="/Layout_week2/Images/layout.JPG">
</p>

### Circuit

<p align="center">
  <img width="800" height="500" src="/Layout_week2/Images/ckt.JPG">
</p>




## About Multisim

Multisim™ software integrates industry-standard SPICE simulation with an interactive schematic environment to instantly visualize and analyze electronic circuit behavior developed by National Instruments.

<img align="left" width="45" height="45" src=/Images/logo.png>

### Installing NI Multisim in Windows (Student Edition)

<img align ="right" src= "https://user-images.githubusercontent.com/66694233/84514942-70ea9280-ace9-11ea-8ffb-e7fc96b8942b.JPG" width=" 200">

-Go to [National Instruments](https://www.ni.com/en-in/shop/electronic-test-instrumentation/application-software-for-electronic-test-and-instrumentation-category/what-is-multisim.html) and click on STUDENT DOWNLOAD to download the student edition. 

 
 - Unzip NI_Circuit_Design_Suite_14_1_Education.zip
 - Click on setup.exe to install. 

### Installing NI Multisim in Linux

There is no Linux version available yet. To use Multisim in Linux, one can install Windows OS in virtual box or it can run using WINE in Ubuntu.

<img align="left" width="45" height="45" src=/Images/wine.png>

#### Wine

[Wine](https://www.winehq.org/) (originally an acronym for "Wine Is Not an Emulator") is a compatibility layer capable of running Windows applications on several POSIX-compliant operating systems, such as Linux, macOS, & BSD.

#### Installation in Ubuntu 20.04
 - Open Terminal and type below commands. 
If your system is 64 bit, enable 32 bit architecture (if you haven't already): 
```
$ sudo dpkg --add-architecture i386 
```
 - Download and add the repository key:
```
$ wget -O - https://dl.winehq.org/wine-builds/winehq.key | sudo apt-key add -
```
 - Add the repository for Ubuntu 20.04:
```
$ sudo add-apt-repository 'deb https://dl.winehq.org/wine-builds/ubuntu/ focal main'
```
 - Update packages for stable version:
```
$ sudo apt install --install-recommends winehq-stable
```
### Multisim installation using WINE in Ubuntu 20.04

-Go to [National Instruments](https://www.ni.com/en-in/shop/electronic-test-instrumentation/application-software-for-electronic-test-and-instrumentation-category/what-is-multisim.html) and click on STUDENT DOWNLOAD to download the student edition. 

 - Unzip NI_Circuit_Design_Suite_14_1_Education.zip
 
 - Right click on `setup.exe` and click on `Open with other application`.
 - In the `Select Application` window, click on `Wine windows program loader` and click on `select`.
 - Install the required files asked by wine and continue Multisim installation. 
 - To install required windows dependencies for Multisim (time approx 90 minutes), open terminal and type
   ` $ winetricks mdac28 jet40 dotnet46 `


## Steps for viewing circuit and simulation using above files

1. Open NI Multisim 14.1 from start menu. (For ubuntu, find it under applications.)
   - Schematics are saved in .ms14 format.
     
2. Download the BGR.ms14 file from this repository.
3. To open this file go to
   `File -> Open -> choose schematic file BGR.ms14`
   The circuit will show up in the editor. 
 
   
4. To change simulation parameters go to ` Simulate -> Analyses and simulation` and set parameters. 

    <img align ="center"  src= "https://user-images.githubusercontent.com/66694233/84515901-b52a6280-acea-11ea-8c85-644a9c61ede5.jpg" width=" 200">
    
5. To directly run and see simulation results go to `Simulate -> Run `
   Outputs will be shown on simulation window.
6. To extract spice netlist
   `Transfer -> Export SPICE Netlist -> Save` (save in .cir extension)
   
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
