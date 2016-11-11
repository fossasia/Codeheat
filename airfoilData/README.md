# mbdyn-airfoils
Instructions for eventual contributors

**Google code-in Warning:** this may be a challenging task! Unless you really know what you are doing, follow the instructions of the "Google code-in" section to avoid a very long task.

repository of c81 airfoil data to use with MBDyn

You can generate the data using the software of your choice (such as XFLR5 or Xfoil) or get the data from the cactus released airfoil data for NACA0015, 18, and 21 airfoils in the cactusImport subdirectory.

WARNING: you must however check the proper Mach number of these files, and it is not always available. Other data can be also gathered from the following document and converted using OCR: http://www.osti.gov/servlets/purl/6548367  Some of the data in that document is also available in numerical format inside the cactusImport directory.

Example OCR procedure: 1. if the document is in pdf extract the desired page; 2. convert it to an image with high definition: `convert -density 300 ddddd.pdf  ddd.png` 3. run ocr on it: `tesseract ./ddd.png ./d2` 4. manually check every number as some errors always occur, especially between 3 and 8 and between 5 and 6.


Most data you will be able to obtain will be for low Mach number, thus, in the event that you are not able to get airfoil data at higher Mach numbers, it is reasonable to produce a low Mach C81 file. You have two options: either use only Mach 0 column and chose a best estimate of your application's Reynolds/Mach number combination. Or better, make a series of Mach columns that are the corresponding Machs for the Reynolds numbers for which you have data available. This will allow you to perform analyses that consider the influence of the Reynolds number of the airfoil properties but ignore the compressibility effects...

Another source of drag and lift coefficient is available here: http://www.dtic.mil/dtic/tr/fulltext/u2/a420649.pdf however, no clear coefficients of moment are given. See the code in the appendices. The data comes from http://oai.dtic.mil/oai/oai?verb=getRecord&metadataPrefix=html&identifier=AD0911537 but no information on coefficient of moment was found outside the [-10°, 22°] angle of attack range.

Other airfoil data is also available in the following documents: https://ntrs.nasa.gov/search.jsp?R=19880002258 and https://ntrs.nasa.gov/search.jsp?R=19840020737 and http://www.nrel.gov/docs/legosti/old/2559.pdf

Finally, a plot digitizer tool may be useful if you are to get data points from old plots inside digitial documents: http://markummitchell.github.io/engauge-digitizer/

The following procedure is suggested for testing your newly created C81 file, but not required. You can have your own testing procedure for the newly created airfoil data file:


1. run MBDyn with the new c81 input file using the airfoil.mbd from this repository:

  `mbdyn airfoil.mbd -o DEL`
  
2. observe your resulting lift, drag, and moment coefficients when running MBDyn:

  for lift coefficient:  `cat DEL.aer |grep "       1"|awk {'print $2, $5'}|feedgnuplot --domain`
  
  for drag coefficient:  `cat DEL.aer |grep "       1"|awk {'print $2, $6'}|feedgnuplot --domain`
  
  for moment coefficient:  `cat DEL.aer |grep "       1"|awk {'print $2, $7'}|feedgnuplot --domain`


Instructions for the Google code-in
======

---

1. take one of the three airfoil properties file from the cactusImport directories

2. convert the Reynolds numbers into Mach numbers using the following rule which applies only to the cactusImport dataset: Mach = Reynolds * 2.8177e-07

3. prepare the C81 free format file, as described on p.35 of the MBDyn manual (https://www.mbdyn.org/userfiles/documents/mbdyn-input-1.7.1.pdf) and as shown in the NACA0012 example file "naca0012_free_format.c81"

4. optionnaly check that your new file gives the same results as the default naca0012 file by running the testing procedure given above

5. upload your file in the "gci_submissions" folder


---
