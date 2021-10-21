***

# Designing of PCB Defect Detection Model and it's Web Application TEST0

***

**Note**:- For setup related instruction, kindly open and follow "[Setup_Instruction_File.txt](Setup_Instruction_File.txt)".
- Main File:- "[defect_pred_i.ipynb](defect_pred_i.ipynb)"
- Prediction File:- "[prediction_model_i.ipynb](prediction_model_i.ipynb)"
- Web Application File:- "[app_predt_i.ipynb](app_predt_i.ipynb)"
- Trained Weight File:- "[model.h5](model.h5)"
- [dataset](dataset) folder contains image sets used for training and testing purposes.
- [static](static) folder contains test images (used by Flask).
- [templates](templates) folder contains HTML files (used by Flask).

***
## Defect-Detection of PCB using Deep Learning

### Abstract
This is a PCB(Printed Circuit Board) Defect Detection Model. The images of PCB are in Binary Format i.e. Black and White, where the black part denotes the circuit's
component. There are different kinds of defects found in the circuits, which is usually denoted by a small white or black patch in the image.

***
### Dataset

DeepPCB dataset used here and can be accessed from [here](https://github.com/tangsanli5201/DeepPCB). The Image is of JPEG format and with dimensions of 640x640. I reduced the size of images to 224x224 using the Anti-Aliasing technique, which reduces the size without major loss in the quality of the image.

<div align=center><img src="https://user-images.githubusercontent.com/47279340/125171710-2761c500-e1d3-11eb-93e1-c444fd3c78bf.jpeg" width="300" style="margin:20">
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<img src="https://user-images.githubusercontent.com/47279340/125171653-f2557280-e1d2-11eb-8f15-ad7fddef7f09.jpeg" width="300" style="margin:20"> 
 </div>
<div align=center>
 PCB without Defect 
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
 PCB with Defect (Notice the Patches)
 </div>

***

### Model

MobileNets, a lightweight deep convolution neural network architecture is used. Here, I used the model which is pre-trained on the ImageNet dataset (Transfer Learning). By setting the first 20 layers of this model to be non-trainable, and training only the last few dense layers leads to fast training and higher accuracy. Callbacks are also used to check the learning rate and stop training when optimal results are already there.

<div align=center><img src="https://user-images.githubusercontent.com/47279340/125174833-a06a1800-e1e5-11eb-8567-d585102cf0eb.png" width="750" style="margin:20">
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
 </div>
 
Pandas is used to split the dataset and putting them in respective dataframe. And with the help of the Matplotlib library, multiple graphs are used to denote the segregation of data according to their labels. Using Image data generator tools, Data Augumentaion is also applied to make the dataset more diverse, leading to a robust model.

After training, which almost took an hour in Google Colab, the model's weight is saved as "model.h5" file. Which is used further for the web application creation process.

#### Here are some graphs to visualise training

<div align=center><img src="https://user-images.githubusercontent.com/47279340/125171519-4c096d00-e1d2-11eb-820e-4da9a63aaee6.png" width="550" style="margin:20">
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
 </div>
</div>
 <div align=center>
  Graph of "Loss vs Epochs" and "Accuracy vs Epochs" respectively.
 </div>

***

### Results

The file named as "good ().jpeg" and bad().jpeg are of good and bad quality PCB images respectively. **The Result (Good) and (Bad) written on the right side of the file name inside the BRACKET is the predicted result. So, you can compare the result with the file name. That's why I used the file name in that manner.**

<div align=center><img src="https://user-images.githubusercontent.com/47279340/125174250-9c3bfb80-e1e1-11eb-8c8a-b8ec1b718708.png" width="750" style="margin:20">
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
 </div>
 
***

## Flask for the web application

After saving the model in .h5 format, I wrote some functions which change the test image's format into an array, which then passed into the prediction model one-by-one. Then I created two HTML files and designed them in a way and on the first page, it will ask to select an image by browsing the file system. It uploads the image and then after uploading, it will direct into the next HTML page, which shows the image with the predicted result i.e. quality is good or bad.

All the function call is done after setting up Flask's function respectively. On the second HTML page, the uploaded image is passed in the model and then it displays the image along with the result.

The HTML file is designed by using Bootstrap.

### This is how it looks

<div align=center><kbd><img src="https://user-images.githubusercontent.com/47279340/125175412-8cc0b080-e1e9-11eb-87be-bb04da89742d.png" width="750" style="margin:20"></kbd>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
 </div>
 <div align=center>
 First Page, ask to select and upload the image file 
 </div>
<br/>

<br/>
<div align=center><kbd><img src="https://user-images.githubusercontent.com/47279340/125176421-d5c83300-e1f0-11eb-9ea6-2428b48cfcaf.png" width="750" style="margin:20"></kbd>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
 </div>
 <div align=center>
 Second Page, shows image with predicted result. 
 </div>

***

## Conclusion
The Architecture and parameters used in this network are capable of producing accuracy of 95.71% on Validation Data which is good. I think the model can be improved more by manipulating networks. Flask based web application can be improved and decorated as per requirement by using Bootstrap's CSS and JS-based design templates.

***

