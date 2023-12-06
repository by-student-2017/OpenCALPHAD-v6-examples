# OpenCALPHAD-v6-examples


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
4. exit
5. y
6. oc6P Ag-Cu_gibbs_free_energy.OCM


## Example: C-Fe
1. cd ~/OpenCALPHAD-v6-examples
2. cd C-Fe
3. oc6P C-Fe_phase_diagram.OCM
4. exit
5. y
6. oc6P C-Fe_gibbs_free_energy.OCM


## Example: Cr-Fe
1. cd ~/OpenCALPHAD-v6-examples
2. cd Cr-Fe
3. oc6P Cr-Fe_phase_diagram.OCM


## Example: Cr-Fe-Mo
1. cd ~/OpenCALPHAD-v6-examples
2. cd Cr-Fe-Mo
3. oc6P Cr-Fe-Mo_phase_diagram.OCM


## Example: Cr-Fe-Ni
1. cd ~/OpenCALPHAD-v6-examples
2. cd Cr-Fe-Mo
3. oc6P Cr-Fe-Mo_phase_diagram.OCM


## Learn more
- see OC6-macros.pdf in doc
1. cd ~/opencalphad-master/examples/macros
2. ls


Acknowledgment
=======
- This project (modified version) is/was partially supported by the following :
- meguREnergy Co., Ltd.
- ATSUMITEC Co., Ltd.
- RIKEN
- Without the support of "meguREnergy Co., Ltd." and "ATSUMITEC Co., Ltd.", I would not have been able to develop the examples to the level shown on this github. I would like to express my sincere gratitude. 
