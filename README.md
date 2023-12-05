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

## Help
1. cd ~/opencalphad-master
2. ./oc6P
3. ?

## Fe-C
1. cd ~/opencalphad-master
2. mkdir work
3. cd work
4. cp ./../examples/macros/steel1.TDB ./
5. vim Fe-C_map.OCM
6. ./../oc6P Fe-C_map.OCM

## Ag-Cu
1. cd ~/opencalphad-master
2. mkdir work
3. cd work
4. cp ./../examples/macros/agcu.TDB ./
5. vim Ag-Cu_map.OCM
6. ./../oc6P Fe-C_map.OCM