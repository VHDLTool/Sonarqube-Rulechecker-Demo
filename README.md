# Source description
This repository holds a working example for several repositories hosted by VHDLTool.
It use features from:
* [VHDL_handbook_CNE](https://github.com/VHDLTool/VHDL_Handbook_CNE). This repository gathers a collections of VHDL rules formatted has a XML file plus VHDL examples. The CNES handbook is a derivate of [VHDL_handbook_STD](https://github.com/VHDLTool/VHDL_Handbook_STD) including more formatting rules. These handbooks can be freely edited and converted to PDF through the [dedicated toolchain](https://github.com/VHDLTool/VHDL_Handbook_Toolchain).   
For additionnal information see the associted [wiki for the toolchain](https://github.com/VHDLTool/VHDL_Handbook_Toolchain/wiki)
* [Zamiacad-Rulechecker](https://github.com/VHDLTool/Zamiacad-Rulechecker). This project add linting capabilities to (Zamiacad)[http://zamiacad.sourceforge.net/web/] eclipse plugin. This is the core engine responsible to analyse the VHDL design with regard to the rules defined in the handbook. This linter project can be used by its own though eclipse and is described inside its [Wiki](https://github.com/VHDLTool/Zamiacad-Rulechecker/wiki). Nevertheless, outputs of the linter are in XML file and are not very friendly to analyse.
* [sonar-VHDLRC](https://github.com/VHDLTool/sonar-VHDLRC). This project aims to hide Zamiacad-Rulechecker complexity and improves user experience with Sonarqube. The Eclipse-Zamiacad-RC is hided inside sonarqube scanner. The [associated wiki](https://github.com/VHDLTool/sonar-VHDLRC/wiki) explain how to compile and install this plugin inside Sonarqube.
* [sonar-coverage-ghdl](https://github.com/VHDLTool/sonar-coverage-ghdl) and [sonar-coverage-modelsim](https://github.com/VHDLTool/sonar-coverage-modelsim) are additionnal sonarqube plugin included in the demo. They can import GHDL-GCC coverage and modelsim coverage reports inside Sonarqube. 
* [Plasma](https://opencores.org/projects/plasma)VHDL example design. Plasma was the test project for Zamiacad.It is included as example for this demo.

The demo might not be up to date with regard to the origianl repositories. Please consult the dedicated release page in Github for the latest version.

# Demo description
The demo includes every projects already configured and ready to work.
## Utilization
1. download the demo Zip in [the release page](https://github.com/VHDLTool/Sonarqube-Rulechecker-Demo/releases) and unzip it.
2. You can execute the script in order (1 to 5) on windows and (a to e) on linux:
   1. Launch sonarqube web server. The sonarqube included in the demo is the  orginal Sonarqube with additionnal features:
      * Add sonar-VHDLRC,sonar-coverage-ghdl and sonar-coverage-modelsim inside the <extensions\plugins\> folder
      * Add sonar-fpga_metrics plugin inside the <extensions\plugins\> folder
      * Configure in sonarqube with a quality gate example
      * Add a java folder with inlcude openjdk 12 (this avoid JRE version problems for the demo)
      * Configure Sonarqube to use embedded Openjdk (this is done by editing <\sonarqube-7.9.1\conf\wrapper.conf> file)
      The server can be launch manually by selecting the right executable in <\sonarqube-7.9.1\bin> folder
   2. Open Sonarqube. The web server can be accessed from any internet browser at the address *http://127.0.0.1:9000*. 
   3. The login and password are *admin/admin*.
   4. Do importation of 2 example projects.
      1. Import plasma example Version 1.   
      This step moves the terminal to the plasma folder and calls the sonnarqube-RC-scanner.   
      This scanner is a modified version of Sonarqube scanner made to include Zamiacad inside a portable eclipse.    
      The scan launch Zamiacad-RC in the portable Eclipse and upload everything inside sonarqube server.   
      You can then go to sonarqube webpage to see the importation of the design
      2. Import plasma example Version 2.   
      This is an updated version of the project to display evolution in Sonarqube.
   5. The importation can now be seen inside Sonarqube webpage.
## Test with a custom project
Do try an analysis with a custom project do as following:
* Create a new directory on you computer
* Put your VHDL files inside this folder
* create a file called *sonar-project.properties*. You can use plasma sonar-project.properties file as example.  
  You  have to change at least *sonar.projectKey* to be unique inside sonarqube and *sonar.sources* to include the relative path to your VHDL files.
* launch, from the location of your *sonar-project.properties* file (which if the root of your project) the rc-scanner located in *rc-scanner-4.0-3-windows\bin\rc-scanner.bat* (or *rc-scanner-4.0.0.1744-1-linux\bin\rc-scanner*)
* project should now be visible inside sonarqube    

You can add scm.git or scm.svm plugins inside sonarqube to get benefit or the automatic version management inside Sonarqube. With this feature each time you commit new code and scan it , you will see the delta evolution of your project. (This could be done manually by changing *sonar.projectVersion* property in *sonar-project.properties* file).   

If you want to include Modelsim code coverage you can include a file called *report.txt.xml* from Modelsim *Tools->Coverage Report->Text "XML format"*. This can be changed in Sonarqube Code Coverage configuration.
