# Defect-Detection
 
For steps to setup, read the Readme_Instruction_File.txt.

This is Deep Learning Model which I created to Check The Defects on PCB (Printed Circuit Boards). Dataset Contains Images of PCB.
I used MobileNet architecture, which was pretrained on ImageNet Dataset. I freezed some layers and trained the model on PCB dataset.
Trained the model, saved it's weight and used it deploy on Flask based web application.

sample data:-



![good (145)k](https://user-images.githubusercontent.com/47279340/125160596-7855c700-e19b-11eb-8ba3-c60ec8bb8b93.jpeg)
Good Quality PCB



![bad (25)k](https://user-images.githubusercontent.com/47279340/125160506-ea79dc00-e19a-11eb-8085-d28cae470dbe.jpeg)
Defective PCB (Notice the white and black patches in between)



So after training and running the model for set of Images:-

![download](https://user-images.githubusercontent.com/47279340/125160660-beab2600-e19b-11eb-8996-e1d69abb40bb.png)


good ().jpeg images are of good quality, and bad().jpeg are of bad quality. The (Good) and (Bad) written Inside the BRACKET is the predicted result. So, you can compare the result with the file name. That's why I used the file name in that manner.




# Flask for web application.



You have to run the flask file (app_predt_i.ipynb), upload the image, enter, and you will get the quality of the PCB.

