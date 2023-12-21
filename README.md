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


## Example: Cr-Fe
1. cd ~/OpenCALPHAD-v6-examples
2. cd Cr-Fe
3. oc6P Cr-Fe_phase_diagram.OCM


## Example: Cr-Fe (metastable: remove SIGMA phase)
1. cd ~/OpenCALPHAD-v6-examples
2. cd Cr-Fe
3. oc6P Cr-Fe_phase_diagram-metastable.OCM
- Note: For some reason, the lines don't connect and there is a gaping hole. I have no choice but to think that this is by design. This is the same situation with Pandat.


## Example: Cr-Fe-Ni
1. cd ~/OpenCALPHAD-v6-examples
2. cd Cr-Fe-Ni
3. oc6P Cr-Fe-Ni_phase_diagram.OCM
- saf2507.TDB: Cr, Fe, Mn, Mo, N, Ni, Vacuum
- "gibbs" and "fix" are just something I tried out. I don't know if it's correct or not.


## Example: Cr-Fe-Mo
1. cd ~/OpenCALPHAD-v6-examples
2. cd Cr-Fe-Mo
3. oc6P Cr-Fe-Mo_phase_diagram.OCM
- steel1.TDB: C, Cr, Fe, Mo, Si, V, Vacuum
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
3. oc6P HSS_phase_diagram.OCM


## Example: stainless_steel_18-8 (Fe-Cr-8wt%Ni)
1. cd ~/OpenCALPHAD-v6-examples
2. cd stainless_steel_18-8
3. oc6P steel_phase_diagram.OCM


## Example: C-Cr-Fe (Fe-13%Cr-C)
1. cd ~/OpenCALPHAD-v6-examples
2. cd C-Cr-Fe
3. oc6P C-Cr-Fe_phase_diagram-fix.OCM


## Example: Al-Ni (A 4 sublattice ordering model)
1. cd ~/OpenCALPHAD-v6-examples
2. cd Al-Ni
3. oc6P Al-Ni_phase_diagram.OCM


## Example: Al-Fe (A 4 sublattice ordering model)
1. cd ~/OpenCALPHAD-v6-examples
2. cd Al-Fe
3. oc6P Al-Fe_phase_diagram.OCM


## Example: Fe-Mo (Gibbs energy curves)
1. cd ~/OpenCALPHAD-v6-examples
2. cd Fe-Mo
3. oc6P Fe-Mo_gibbs_free_energy.OCM
4. quit y
5. oo6P Fe-Mo_phase_diagram.OCM


## Example: C-Fe
1. cd ~/OpenCALPHAD-v6-examples
2. cd C-Fe
3. oc6P C-Fe_phase_diagram.OCM
4. exit y
5. oc6P C-Fe_gibbs_free_energy.OCM


## Example: HSS-melting
1. cd ~/OpenCALPHAD-v6-examples
2. cd HSS-melting
3. oc6P melting.OCM
- High-Speed Steel: Fe-C-Cr-Mo-Si-V system


## OFP-Cu (Oxygen-free phosphorus copper: Cu-H-O-P-S system)
- The copper-rich part of the Cu-H-O-S-P system at low temperatures.


## Learn more
- see "macros-OC7.pdf" and "OC6-macros.pdf" in doc
1. cd ~/opencalphad-master/examples/macros
2. ls
3. oc6P step2.OCM
4. quit y
5. oc6P map10.OCM
- Important files: step2.OCM and step6.OCM
- Important files: map10.OCM and map14.OCM
- Youtube: https://www.youtube.com/watch?v=mIRvrIzSj7I
- Youtube (GUI): https://www.youtube.com/watch?v=OsO-DiCGJ00
- Gitter: https://app.gitter.im/#/room/#opencalphad_opencalphad:gitter.im (B-Fe-Nb, etc)


## TDB files
- NIMS: CPDDB: https://cpddb.nims.go.jp/ (There are some files that cannot be read properly. It takes some time to register, but it is free to use.)
- TDBDB: https://avdwgroup.engin.brown.edu/ , https://www.sciencedirect.com/science/article/pii/S0364591618300099 (Open Access)
- MatCalc, Open free databases: https://www.matcalc-engineering.com/index.php/databases , https://doi.org/10.1016/j.calphad.2023.102531 (Open Access)
- MatCalc6: https://www.matcalc.at/index.php/databases/open-databases
- Available open databases: https://www.opencalphad.com/databases.html
-   https://github.com/pycalphad/pycalphad/tree/develop/examples
- NIST (Solder Systems): https://www.metallurgy.nist.gov/phase/solder/solder.html
-   https://www.nist.gov/mml/materials-science-and-engineering-division/thermodynamics-and-kinetics-group/published-diffusion
- JAEA: https://migrationdb.jaea.go.jp/cgi-bin/db_menu.cgi?ej=1&title=TDB
- Computational Thermodynamics, Free databases: http://www.met.kth.se/~bosse/BOOK/databases/databases.html
- nanocem CemGEMS: https://cemgems.org/cemdata/about-cemdata/
- GEMS: https://gems.web.psi.ch/TDB/?forprint
- MINES: https://geoinfo.nmt.edu/mines-tdb/
- Thermo-Chimie: https://www.thermochimie-tdb.com/
- SGTE Pure: https://www.sgte.net/en/free-pure-substance-database
- ATAT: https://www.brown.edu/Departments/Engineering/Labs/avdw/atat/
- TDB-6: https://www.oecd-nea.org/jcms/pl_22166/thermochemical-database-tdb-project


## Widom Alloy Database
- https://alloy.phys.cmu.edu/


## CAMP databases (CAMP Homepage)
- https://databases.fysik.dtu.dk/


## 2NN MEAM Interatomc Potential
- https://cmse.postech.ac.kr/home_2nnmeam


## MatCalc Open Databases
- Al-base
```
awk 'NR>=6751 {$0="$ "$0}1' mc_al_v2.035.tdb > new_mc_al_v2.035.tdb
```
- Steel database
```
awk 'NR>=11625 {$0="$ "$0}1' mc_fe_v2.060.tdb > new_mc_fe_v2.060.tdb
```
- Bainite database1
```
awk 'NR>=11677 {$0="$ "$0}1' mc_fe_bainite.tdb > new_mc_fe_bainite.tdb
```
- Ni-base
```
awk 'NR>=9635 {$0="$ "$0}1' mc_ni_v2.034.tdb > new_mc_ni_v2.034.tdb
```


## UTF-8
1. sudo apt -y install nkf
2. nkf -w bfend_hal.tdb > bfend_hal_en.tdb


## B-Fe-Nd
- Development of a prototype thermodynamic database for Nd-Fe-B permanent magnets. T.Abe, et al., STAM, 22, (2021), 557-570. doi.org/10.1080/14686996.2021.1936627
- It is sufficient to create an input file that shows results consistent with the above paper. With my ability, it is difficult to show results beyond what is shown in the test folder. hope readers will consider this.
- I am preparing this as a test. I think it's worth using demo versions of Pandat and other commercial software if they match up roughly.
- If the crystal structure is clear from the above calculation, use Akai-KKR to perform element substitution and calculate the formation energy. The formation energy obtained with Akai-KKR should be used as a reference only, as the structure may be retained even if it is somewhat energetically disadvantageous due to effects such as entropy.
- VASP (QE, OpenMX, Siesta or ...) etc. can take into account the displacement of atomic positions, but because the calculation cost is high, this is done after checking the element substitution situation with Akai-KKR. If you can create an appropriate potential for molecular dynamics, it is best to use it to optimize the structure and finally confirm it using VASP (QE, OpenMX, Siesta or ...), etc.
- e.g., (B, Al, Ga)-(Fe, Co, Cu)-(Nd, Dy) system
- It is good to remember that machine learning potentials other than graph neural networks become unstable in systems with four or more elements. Graph neural networks are not easily available, so I don't know how reliable they are.
- If you only need ternary phase diagrams, pycalphad is recommended. It is very unfortunate that in the current state of development, it is not possible to draw a ternary system phase diagram by fixing other elements such as a quaternary system.
- I'm not particularly confident about "heat capacity". Just tried it.
- As written in the "Note" section below, discussing Coercivity is impossible unless the organization is also considered. The phase field method is used to understand the relationship between tissue and magnetism.
- Note 1: Since most of the region inside the magnet is the T1 phase, the alloy composition is located near the stoichiometric composition of the T1 phase within the (T1+L) region.
- Note 2: The end of the tie line on the liquid phase side varies greatly depending on the local average composition of Nd around the grain boundary position. This is the reason why the experimental data changed.
- Note 3: In a metastable phase diagram (for example, at 873 K), only two phases, the T1 phase and the liquid phase, are considered.
- Note 4: Coercivity cannot be obtained unless Nd is precipitated at a reasonably high concentration at the grain boundaries (2-3 nm width).
- Note 5: If there is less Nd in the grain boundaries, Fe will mainly exist and will not act as a barrier to domain wall movement, resulting in a decrease in coercive force. 
- Note 6: steady state：Fe-5at%B-15at%Nd


Acknowledgment
=======
- This project (modified version) is/was partially supported by the following :
- meguREnergy Co., Ltd.
- ATSUMITEC Co., Ltd.
- RIKEN
- Without the support of "meguREnergy Co., Ltd." and "ATSUMITEC Co., Ltd.", I would not have been able to develop the examples to the level shown on this github. I would like to express my sincere gratitude. 
- Al-Mg-Zn: I received permission from Dr. Abe of NIMS to post the revised version of TDB (11/Dec/2023 12:04). I would like to express my gratitude to you.
- Al-Mg-Zn: It's working fine with PyCALPHAD, but due to my (By STUDENT) lack of skill, some parts are incorrectly drawn with OpenCALPHAD.


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
