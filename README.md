# Dataset of main bearing surface defects images 

- Being collected from front view of main bearings of a four-cylinder engine type
- Containing 500 original images of two bearing surface defects, namely scratching and pitting
- Using an 12.3MP IMX 277 Jetson Nano Camera for images capture
- Using 6mm wide lens for setting the focus
- Designing a proper lighting configuration for imaging
- Annotating the images for semantic segmentation with 
- PixelAnnotationTool_x64_v1.3.2 software
- Download [(** Data**)](https://drive.google.com/file/d/1x1fWg54HHkBc4zABBs3n2Szl6izrwr3n/view?usp=sharing)

![Capture](https://user-images.githubusercontent.com/85845544/197382474-270632ca-1a53-483b-abfa-61344cb1d571.JPG)

# Preprocessing

-	Sobel filter
** 	Data Augmentation (DA) technique including the following transformations:
- Horizantalflip
-	GaussianNoise
-	IAAPerspective
-	Gamma
-	Sharpen
-	Contrast
-	HueSaturationValue
-	Lamda

![666](https://user-images.githubusercontent.com/85845544/219784654-376ca2c5-cc4f-4ef6-bb85-1fcfbd9cf1f3.jpg)

# Approach

-	Enlarging training dataset by combination of Sobel filter and 8 transformations
-	Using Unet with MobileNet architecture as backbone
-	Using transfer learning with the pre-trained ImageNet weights
-	Annotation of images


![Capture1](https://user-images.githubusercontent.com/85845544/197391026-5b557bc0-319d-435d-b1e0-bedb894362fd.PNG)

# Setup
```
Data
 |-- checkpoints
 |-- Segmentation Data
 |  |-- segmentation Train
 |  |  |-- Images
 |  |  |-- Images Masks
 |  |-- segmentation Validation
 |  |  |-- Images
 |  |  |-- Images Masks
 |  |-- segmentation Test
 |  |  |-- test image
 |  |  |-- test image mask
 ...
```
## Usage



**Segmentation**

-	If wish to self-train CNN, please follow steps 1 to 4. Otherwise, please download Segmentation model.h5 from step 5.
-	Put dataset in the folders previously mentioned
-	Install Tensorflow 2.8.0, Keras 2.8.0, opencv_python-4.5.5.64, albumentations-1.1.0, segmentation_models-1.0.1
-	Run segmentation train.py and create Segmentation model.h5
-	Download Segmentation model.h5 and put it in "Checkpoints" folder (Segmentation model)
-	Put test image in "Segmentation Test" folder
-	Run Segmentation Test.py




![predictions ](https://user-images.githubusercontent.com/85845544/197379493-e1580868-cd68-471b-ba76-e1334bfe0647.jpg)

## Real-time industrial application of segmentation approach

-	Using NVIDIA Developer Kit Jetson Nano 4GB
-	Using 12.3MP IMX 277 Jetson Nano Camera
-	Using trained .h5 file in segmentation approach
-	Using TensorFlow 2.8.0 on NVIDIA Developer Kit Jetson Nano
-	Using Jetson Nano GPIO to show final results


![20220813_130507](https://user-images.githubusercontent.com/85845544/197379046-95c4e241-56b0-4b53-8c7b-b8fd0365ac75.jpg)
