# mbdyn-airfoils
repository of c81 airfoil data to use with MBDyn or similar software

The following procedure is suggested for simplicity but by no means required; you can have your own testing procedure for the newly created airfoil data file.

You can generate the data using the software of your choice or, for simplicity, get the data from the cactus released airfoil data for NACA0015, 18, and 21 airfoils in the cactusImport subdirectory. WARNING: must however check the proper Mach number of these files (are they constant at different Machs?). Other data can be also gathered from the following document and converted using OCR: http://www.osti.gov/servlets/purl/6548367

To test your newly created file you can perform the following actions:

1. run MBDyn with the new c81 input file

  `mbdyn airfoil.mbd -o DEL`
  
  for lift coefficient:  `cat DEL.aer |grep "       1"|awk {'print $2, $5'}|feedgnuplot --domain`
  
  for drag coefficient:  `cat DEL.aer |grep "       1"|awk {'print $2, $6'}|feedgnuplot --domain`
  
  for moment coefficient:  `cat DEL.aer |grep "       1"|awk {'print $2, $7'}|feedgnuplot --domain`

2.
