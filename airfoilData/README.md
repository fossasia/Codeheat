# mbdyn-airfoils
Warning: this is a challenging task!

repository of c81 airfoil data to use with MBDyn or similar software

The following procedure is suggested for simplicity but by no means required; you can have your own testing procedure for the newly created airfoil data file.

You can generate the data using the software of your choice or, for simplicity, get the data from the cactus released airfoil data for NACA0015, 18, and 21 airfoils in the cactusImport subdirectory. WARNING: must however check the proper Mach number of these files (are they constant at different Machs?). Other data can be also gathered from the following document and converted using OCR: http://www.osti.gov/servlets/purl/6548367

Most data you will be able to obtain will be for low Mach number, thus, in the event that you are not able to get airfoil data at higher Mach numbers, it is reasonable to produce C81 files with only Mach 0 and Mach 0.2 number columns, making them equal, and making different C81 files based on the variation of the Reynolds number (go for more or less 5 Reynolds number).

Another source of drag and lift coefficient is available here: http://www.dtic.mil/dtic/tr/fulltext/u2/a420649.pdf however, no clear coefficients of moment are given. See the code in the appendices. The data comes from http://oai.dtic.mil/oai/oai?verb=getRecord&metadataPrefix=html&identifier=AD0911537 but no information on coefficient of moment was found outside the [-10°, 22°] angle of attack range.

Finally, a plot digitizer tool may be useful if you are to get data points from old plots inside digitial documents: http://markummitchell.github.io/engauge-digitizer/

To test your newly created file you can perform the following actions:

1. run MBDyn with the new c81 input file:

  `mbdyn airfoil.mbd -o DEL`
  
2. observe your resulting lift, drag, and moment coefficients when running MBDyn:

  for lift coefficient:  `cat DEL.aer |grep "       1"|awk {'print $2, $5'}|feedgnuplot --domain`
  
  for drag coefficient:  `cat DEL.aer |grep "       1"|awk {'print $2, $6'}|feedgnuplot --domain`
  
  for moment coefficient:  `cat DEL.aer |grep "       1"|awk {'print $2, $7'}|feedgnuplot --domain`
