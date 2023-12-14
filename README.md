# OpenCALPHAD-v6-examples
- Note 1: The "map" can not be created well in many systems. I tried various TDBs of "CPDDB", but OpenCALPHAD should be considered to be of limited use. 
- Note 2: If you want to draw trigonometric phase diagrams, pycalphad is recommended. Examples files are also available here (https://github.com/by-student-2017/pycalphad-v.0.10.3-examples.git).


## Installation (OpenCALPHAD)
1. sudo apt update
2. sudo apt -y install gfortran liblapack-dev
3. sudo apt -y install gnuplot
4. wget http://www.opencalphad.com/downloads/oc6-stable.zip
5. unzip oc6-stable.zip
6. cd opencalphad-master
7. gedit Makefile
```
-----(before) (Line 90 and 140)
        # Linux >>
        #$(C) -c $(FCOPT) -DLinux src/utilities/GETKEY/getkey.c

        $(FC) -c $(FCOPT) -Dqtplt -Dlixhlp src/userif/pmon6.F90
-----
-----(after)
        # Linux >>
        $(C) -c $(FCOPT) -DLinux src/utilities/GETKEY/getkey.c

        $(FC) -c $(FCOPT) -Dqtplt -Dlixhlp -Dx11 src/userif/pmon6.F90
-----
```
8. make all
9. echo 'export PATH=$PATH:$HOME/opencalphad-master' >> ~/.bashrc
10. bash


## Help
1. oc6P
2. ?
3. map?


## Installation (this examples)
1. cd ~
2. git clone https://github.com/by-student-2017/OpenCALPHAD-v6-examples.git


## Example: Ag-Cu
1. cd ~/OpenCALPHAD-v6-examples
2. cd Ag-Cu
3. oc6P Ag-Cu_phase_diagram.OCM
4. quit y
5. oc6P Ag-Cu_gibbs_free_energy.OCM


## Example: C-Fe
1. cd ~/OpenCALPHAD-v6-examples
2. cd C-Fe
3. oc6P C-Fe_phase_diagram.OCM
4. exit y
5. oc6P C-Fe_gibbs_free_energy.OCM


## Example: Cr-Fe
1. cd ~/OpenCALPHAD-v6-examples
2. cd Cr-Fe
3. oc6P Cr-Fe_phase_diagram.OCM


## Example: Cr-Fe (metastable: remove SIGMA phase)
1. cd ~/OpenCALPHAD-v6-examples
2. cd Cr-Fe
3. oc6P Cr-Fe_phase_diagram-metastable.OCM
- Note: For some reason, the lines don't connect and there is a gaping hole. I have no choice but to think that this is by design. This is the same situation with Pandat.


## Example: Cr-Fe-Mo
1. cd ~/OpenCALPHAD-v6-examples
2. cd Cr-Fe-Mo
3. oc6P Cr-Fe-Mo_phase_diagram.OCM
- steel1.TDB: C, Cr, Fe, Mo, Si, V, Vacuum
- "gibbs" and "fix" are just something I tried out. I don't know if it's correct or not.


## Example: Cr-Fe-Ni
1. cd ~/OpenCALPHAD-v6-examples
2. cd Cr-Fe-Ni
3. oc6P Cr-Fe-Ni_phase_diagram.OCM
- saf2507.TDB: Cr, Fe, Mn, Mo, N, Ni, Vacuum
- "gibbs" and "fix" are just something I tried out. I don't know if it's correct or not.


## Example: Mo-Ni-Re
1. cd ~/OpenCALPHAD-v6-examples
2. cd Mo-Ni-Re
3. oc6P Mo-Ni-Re_phase_diagram-1500K.OCM
- BEF.TDB: Mo, Ni, Re, Vacuum
- "gibbs" and "fix" are just something I tried out. I don't know if it's correct or not.


## Example: Al-Mg-Zn
1. cd ~/OpenCALPHAD-v6-examples
2. cd Al-Mg-Zn
3. (mmc1.TDB (Qiu et al. (2015)) from TDBDB (https://avdwgroup.engin.brown.edu/))
4. mv mmc1.TDB Qiu_2015.TDB
5. sudo apt -y install nkf
6. nkf -w Qiu_2015.TDB > Qiu_2015_en.TDB
7. oc6P Al-Mg-Zn_phase_diagram.OCM
- need "nkf" for "UnicodeDecodeError: 'utf-8' codec can't decode byte 0xfc in position 193546: invalid start byte"
- cost507R.TDB: Al, B, C, Ce, Cr, Cu, Fe, Li, Mg, Mn, N, Nd, Ni, Si, Sn, Ti, V, Y, Zn, Zr, Vacuum
- "modified_almgzn_hay_oc6.tdb" from CPDDB
- With my technical ability, I could not completely reproduce the ternary phase diagram of Al-Mg-Zn.


## Example: HSS (High-Speed Steel)
1. cd ~/OpenCALPHAD-v6-examples
2. cd HSS
3. oc6P map7.OCM


## Example: HSS-melting
1. cd ~/OpenCALPHAD-v6-examples
2. cd HSS-melting
3. oc6P melting.OCM
- High-Speed Steel: Fe-C-Cr-Mo-Si-V system


## Example: 18-8_stainless_steel
1. cd ~/OpenCALPHAD-v6-examples
2. cd 18-8_stainless_steel
3. oc6P map6.OCM
- 18-8 stainless steel: Fe-Cr-8wt%Ni


## Example: Fe-Mo (Gibbs energy curves)
1. cd ~/OpenCALPHAD-v6-examples
2. cd Fe-Mo
3. oc6P Fe-Mo_gibbs_free_energy.OCM
4. quit y
5. oo6P Fe-Mo_phase_diagram.OCM


## Learn more
- see "macros-OC7.pdf" and "OC6-macros.pdf" in doc
1. cd ~/opencalphad-master/examples/macros
2. ls
3. oc6P step2.OCM
4. quit y
5. oc6P map10.OCM
- Important files: step2.OCM and step6.OCM
- Important files: map10.OCM and map14.OCM


## TDB files
- NIMS: CPDDB: https://cpddb.nims.go.jp/ (There are some files that cannot be read properly. It takes some time to register, but it is free to use.)
-   OpenCALPHAD Japanese manual: https://cpddb.nims.go.jp/cpddb/OpenCalphad/opencalphad.htm
- TDBDB: https://avdwgroup.engin.brown.edu/ , https://www.sciencedirect.com/science/article/pii/S0364591618300099 (Open Access)
- MatCalc, Open free databases: https://www.matcalc-engineering.com/index.php/databases , https://doi.org/10.1016/j.calphad.2023.102531 (Open Access)
- Available open databases: https://www.opencalphad.com/databases.html
-   https://github.com/pycalphad/pycalphad/tree/develop/examples


Acknowledgment
=======
- This project (modified version) is/was partially supported by the following :
- meguREnergy Co., Ltd.
- ATSUMITEC Co., Ltd.
- RIKEN
- Without the support of "meguREnergy Co., Ltd." and "ATSUMITEC Co., Ltd.", I would not have been able to develop the examples to the level shown on this github. I would like to express my sincere gratitude. 
- I received permission from Dr. Abe of NIMS to post the revised version of TDB (11/Dec/2023 12:04). I would like to express my gratitude to you.
- It's working fine with PyCALPHAD, but due to my (By STUDENT) lack of skill, some parts are incorrectly drawn with OpenCALPHAD.


PC specs used for test
=======
+ OS: Microsoft Windows 11 Home 64 bit
+ BIOS: 1.14.0
+ CPU： 12th Gen Intel(R) Core(TM) i7-12700
+ Base Board：0R6PCT (A01)
+ Memory：32 GB
+ GPU: NVIDIA GeForce RTX3070
+ WSL2: VERSION="22.04.1 LTS (Jammy Jellyfish)"
+ Python 3.10.12
