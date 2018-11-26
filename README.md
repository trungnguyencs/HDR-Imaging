## CE264HDR
An implementation of High-dynamic-range (HDR) imaging technique. First project for Fall 2018 CE264-Computer Vision at UC Santa Cruz

## Motivation
Implemented Camera Radiometric Calibration and HDR system using two composition algorithms and geneartion fine tone mapped image. Histograms are also plotted for each of the RG and B channels respectively for analysis of changes in pixel values.
 

## OS, Libraries and Language
The code can be compiled in any operating system MAC-OS, Windows. The code is written in python3 and Libraries used are:
1. Opencv
2. Numpy
3. PIL 
4. sklearn
5. Glob

## Scripts 
The project consist of three python notebooks belonging to each part of the project. The notebooks kernels can be refreshed and 
again run to verify the result of the code.
The scripts name and their functionality are decribed below :
1. RadiometryCalibration: 
* It is very likely that a camera will not produce a linear response when shooting JPEG. This means that there will be a non-linear mapping between the recorded data output brightness $B$ (the pixel values to work with) and exposute time $T$. I cannot measure $B$ directly; instead, the camera gives me a value $B'=f(B)$, where $f(B)$ is an unknown non-linear function, which changes from camera to camera

* For HDR to work well, I need to reverse-engineer the function $f$ and invert it, obtaining an approximation of the true (linear) brightness $B=f^{-1}(B')$. This is called radiometric calibration

* I will make a first order approximation that $B'=f(B)=B_1/g$ for some unknown value $g$, and find $g$ using linear regression. From there I can retrieve the brightness $B=(B')g$ which is linear with $T$

2. HDR:
   This script generates HDR using two composite merge algorithms from the three images at different exposure intensities and finally
   map it to generate fine tone-mapped image. The histograms are also plotted for the stack of three images used for HDR generation. 
   
* In this part I created a composite HDR image from your stack of three linearized images. I composed the images using two different algorithms:

* Composition Algorithm 1: For each pixel, use the pixel value of the image with largest exposure time such that the pixel is not saturated ($B' < 255$)

* Because the second and third images are over exposed, there is a set $S_1$ pixels saturated ($B' = 255$) in the second image (exposure $a_1*T$); and a set $S_2 \supset S_1$ saturated in the third image (exposure $a_2*T$) ($a_2 > a_1$)

* If the pixel belongs to $S_1$, I would use the value $B'^g(T)$ from the first image. If it belongs to $S_2$, but not to $S_1$, I would use the value $B'^g(a1*T) / a_1$ from the second image. And if it does not belong to $S_2$, I would use the value $B'^g(a_2*T) / a_2$ from the third image

### Composition Algorithm 2: For each pixel, use the average of the values in the images for which this pixel is not saturated

* E.g. if the pixel belongs to $S_2 \backslash S_1$, I would compute the average of the value $B'^g(T)$ from the first image and of the value $B'^g(a_1*T) / a_1$ from the second image

## Files 
1. CE264HDR             : parent directory
2. PictureStackedImages : Consist of three images used for generation of HDR image 
3. CalibImages          : Consist of 14 images taken at different exposure time and is used for radiometry calibration 
4. ToneMappedImages     : Final tonned mapped image are saved in this folder

Raw images:

![alt text](https://github.com/trungnguyencs/CE264HDR/blob/master/PictureStackImages/5.JPG "Title")
![alt text](https://github.com/trungnguyencs/CE264HDR/blob/master/PictureStackImages/8.JPG "Title")
![alt text](https://github.com/trungnguyencs/CE264HDR/blob/master/PictureStackImages/12.JPG "Title")

HDR Image Result:
* Method 1:
![alt text](https://github.com/trungnguyencs/CE264HDR/blob/master/ToneMappedImages/hdr1.jpg "Title")
* Method 2:
![alt text](https://github.com/trungnguyencs/CE264HDR/blob/master/ToneMappedImages/hdr2.jpg "Title")
* Method 3:
![alt text](https://github.com/trungnguyencs/CE264HDR/blob/master/ToneMappedImages/hdr_fusion_mertens.jpg "Title")
