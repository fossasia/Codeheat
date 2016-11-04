# mbdyn-airfoils
repository of c81 airfoil data to use with MBDyn or similar software

The following procedure is suggested for simplicity but by no means required; you can have your own testing procedure for the newly c reated airfoil data file.

So, testing the newly created file:

1. run MBDyn with the new c81 input file

mbdyn airfoil.mbd -o DEL

cat DEL.jnt |grep "       1"|awk {'print $16, $3'}|feedgnuplot --domain

2.
