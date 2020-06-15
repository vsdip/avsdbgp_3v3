# Bandgap Reference
The project is about simulating Bandgap Reference circuit (BRG) and obtain its characteristics. 

*This project is now in its starting phase which involves working in Windows using Multisim* 

<img align="left" width="45" height="45" src=/Images/logo.png>

## About Multisim

Multisim™ software integrates industry-standard SPICE simulation with an interactive schematic environment to instantly visualize and analyze electronic circuit behavior developed by National Instruments.


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
`
$  sudo apt-get install wine
$  cd /tmp/
$  wget http://download.ni.com/support/softlib/Core/Circuit_Design_Suite/14.1/14.1/NI_Circuit_Design_Suite_14_1_Education.zip
$  unzip NI_Circuit_Design_Suite_14_1_Education.zip
$  wine setup.exe
$  rm Multisim.exe
`



Steps for viewing circuit and simulation using above files
===================================

1. Open NI Multisim 14.1 from start menu.
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
