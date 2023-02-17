# Dataset of main bearing surface defects images 

- Being collected from front view of main bearings of a four-cylinder engine type
- Containing 500 original images of two bearing surface defects, namely scratching and pitting
- Using an 12.3MP IMX 277 Jetson Nano Camera for images capture
- Using 6mm wide lens for setting the focus
- Designing a proper lighting configuration for imaging
- Annotating the images for semantic segmentation with 
- PixelAnnotationTool_x64_v1.3.2 software
- Download [(** Data**)](https://drive.google.com/file/d/1x1fWg54HHkBc4zABBs3n2Szl6izrwr3n/view?usp=sharing)

![55](https://user-images.githubusercontent.com/85845544/219785160-e8cd9531-7489-4be4-a9f7-57b396ed61de.jpg)


# Preprocessing

-	Sobel filter

![77](https://user-images.githubusercontent.com/85845544/219801164-554c61c1-3a25-4c67-b41d-a6b850f5ba43.jpg)

**Data Augmentation (DA) technique including the following transformations:
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
-	Download Segmentation model.h5 and put it in "Checkpoints" folder [(Segmentation model)]
-	Put test image in "Segmentation Test" folder
-	Run Segmentation Test.py

![1](https://user-images.githubusercontent.com/85845544/219785782-dda85e36-68a1-4050-8089-65145ed25f28.png)![1 (1)](https://user-images.githubusercontent.com/85845544/219786401-c1855245-c89a-4e3b-8eb8-b58ab63e8dcd.png)

## Real-time industrial application of segmentation approach

-	Using NVIDIA Developer Kit Jetson Nano 4GB
-	Using 12.3MP IMX 277 Jetson Nano Camera
-	Using trained .h5 file in segmentation approach
-	Using TensorFlow 2.8.0 on NVIDIA Developer Kit Jetson Nano
-	Using Jetson Nano GPIO to show final results
