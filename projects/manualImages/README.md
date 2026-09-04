# mbdyn-manualImages

Task description for the creation of new images for the MBDyn manual and/or website.


1. Consult the latest version of the manual, taken from the private CVS and uploaded here: input.pdf, to see how cardano.256.png, inline.256.png, revHinge.256.png, and spherHinge.256.png were included in the manual (p.225, 240, 248, and 255)

2. find an element for which an image would be beneficial; chose a common filename root for your new element (ie: cardano, revHinge, ...); for the instructions here we'll use "yourFile"

3. starting from the revolute.blend Blender file, of which the layers are explained in revolute.txt, create your own element image making sure you respect the element description given in the manual; save the modified Blender file with a new name (yourFile.blend)

4. render the element in png, regenerate the color palette to use 256 colors (GIMP recommended [Menu: Image->Mode->Indexed]), trim the image to remove any white borders (GIMP recommended [Menu: Image->Autotrim])

5. convert the modified generated png into an eps3 file using the following command: `convert yourFile.png eps3:yourFile.eps`

6. submit the generated files: yourFile.blend, yourFile.png, and yourFile.eps; the eps and png files should not exceed 100k each
