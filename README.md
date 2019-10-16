This repository holds a working example for several repositories hosted by VHDLTool.
It use features from:
* [VHDL_handbook_CNE](https://github.com/VHDLTool/VHDL_Handbook_CNE). This repository gathers a collections of VHDL rules formatted has a XML file plus VHDL examples. The CNES handbook is a derivate of [VHDL_handbook_STD](https://github.com/VHDLTool/VHDL_Handbook_STD) including more formatting rules. These handbooks can be freely edited and converted to PDF through the [dedicated toolchain](https://github.com/VHDLTool/VHDL_Handbook_Toolchain).   
For additionnal information see the associted [wiki for the toolchain](https://github.com/VHDLTool/VHDL_Handbook_Toolchain/wiki)
* [Zamiacad-Rulechecker](https://github.com/VHDLTool/Zamiacad-Rulechecker). This project add linting capabilities to (Zamiacad)[http://zamiacad.sourceforge.net/web/] eclipse plugin. This is the core engine responsible to analyse the VHDL design with regard to the rules defined in the handbook. This linter project can be used by its own though eclipse and is described inside its [Wiki](https://github.com/VHDLTool/Zamiacad-Rulechecker/wiki). Nevertheless, outputs of the linter are in XML file and are not very friendly to analyse.
* [sonar-VHDLRC](https://github.com/VHDLTool/sonar-VHDLRC). This project aims to hide Zamiacad-Rulechecker complexity and improves user experience with Sonarqube. The Eclipse-Zamiacad-RC is hided inside sonarqube scanner. The [associated wiki](https://github.com/VHDLTool/sonar-VHDLRC/wiki) explain how to compile and install this plugin inside Sonarqube.
* [sonar-coverage-ghdl](https://github.com/VHDLTool/sonar-coverage-ghdl) and [sonar-coverage-modelsim](https://github.com/VHDLTool/sonar-coverage-modelsim) are additionnal sonarqube plugin included in the demo. They can import GHDL-GCC coverage and modelsim coverage reports inside Sonarqube. 
* [Plasma](https://opencores.org/projects/plasma)VHDL example design. Plasma was the test project for Zamiacad.It is included as example for this demo.

This repository holds example design for:
* Zamiacad Rulechecker included inside a portable eclipse
* RC scanner which import VHDL project into Sonarqube
* Sonarqube for managing issues logged by Zamiacad rulechecker
* VHDL design example Plasma

Please refers to :
* https://github.com/VHDLTool/VHDL-RC : for latest RC-scanner
* https://www.sonarqube.org/downloads/ : for the latest LTS sonarqube version
* https://github.com/VHDLTool/Zamiacad-Rulechecker : for the latest Zamiacad-Rulechecker plugin
* https://github.com/VHDLTool/VHDL-RC/wiki/How-rc-scanner-is-built#2-assemble-a-portable-eclipse : for how to create a portable eclipse for windows
* https://github.com/VHDLTool/VHDL-RC/wiki/How-rc-scanner-is-built#2-assemble-eclipse : for how to create a portable eclipse for linux
