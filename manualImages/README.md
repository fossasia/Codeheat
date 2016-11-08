# mbdyn-manualImages

Task description for the creation of new images for the MBDyn manual and/or website.


1. Consult the latest version of the manual, taken from the private CVS and uploaded here: input.pdf

2. find an element for which an image would be beneficial; chose a comon filename root for your new element (ie: cardano, revHinge, ...); here we'll use "yourFile"

3. starting from the revolute.blend file, of which the layers are explained in revolute.txt, create your own element image making sure you respect the description given in the manual

4. render the element in png, regenerate the color palette to use 256 colors (GIMP recommended [Menu: Image->Mode->Indexed]), trim the image to remove any white borders (GIMP recommended [Menu: Image->Autotrim])

5. convert the generated png into an eps3 file using the following command: convert yourFile.png eps3:yourFile.eps

6. submit the generated files: yourFile.blend, yourFile.png, and yourFile.eps; the eps and png should not exceed 100k each
