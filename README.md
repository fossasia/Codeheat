# mbdyn-airfoils
repository of c81 airfoil data to use with MBDyn or similar software

The following procedure is suggested for simplicity but by no means required; you can have your own testing procedure for the newly c reated airfoil data file.

So, testing the newly created file:

1. run MBDyn with the new c81 input file

  mbdyn airfoil.mbd -o DEL
  
  for lift coefficient:  cat DEL.aer |grep "       1"|awk {'print $2, $5'}|feedgnuplot --domain
  
  for drag coefficient:  cat DEL.aer |grep "       1"|awk {'print $2, $6'}|feedgnuplot --domain
  
  for moment coefficient:  cat DEL.aer |grep "       1"|awk {'print $2, $7'}|feedgnuplot --domain

2.
