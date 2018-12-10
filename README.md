## HDR Imaging
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
   Plot the histogram of each R,G & B channels respectively  and regress the function to calculate g values.
2. HDR:
   This script generates HDR using two composite merge algorithms from the three images at different exposure intensities and finally
   map it to generate fine tone-mapped image. The histograms are also plotted for the stack of three images used for HDR generation. 

## Files 
1. CE264HDR             : parent directory
2. PictureStackedImages : Consist of three images used for generation of HDR image 
3. CalibImages          : Consist of 14 images taken at different exposure time and is used for radiometry calibration 
4. ToneMappedImages     : Final tonned mapped image are saved in this folder

## Results 

Raw images:

![alt-text-1](https://github.com/trungnguyencs/CE264MultiViewStereo/blob/master/StereoImages/01.jpeg "left image") ![alt-text-2](https://github.com/trungnguyencs/CE264MultiViewStereo/blob/master/StereoImages/01.jpeg "right image")

<img src="https://github.com/trungnguyencs/CE264MultiViewStereo/blob/master/StereoImages/01.jpeg" width="425"/> <img src="https://github.com/trungnguyencs/CE264MultiViewStereo/blob/master/StereoImages/01.jpeg" width="425"/> 



![alt text](https://github.com/trungnguyencs/CE264MultiViewStereo/blob/master/StereoImages/01.jpeg "Title")
Right image:
![alt text](https://github.com/trungnguyencs/CE264MultiViewStereo/blob/master/StereoImages/02.jpeg "Title")

HDR Image Result:
* Method 1:
![alt text](https://github.com/trungnguyencs/CE264HDR/blob/master/ToneMappedImages/hdr1.jpg "Title")
* Method 2:
![alt text](https://github.com/trungnguyencs/CE264HDR/blob/master/ToneMappedImages/hdr2.jpg "Title")
* Method 3:
![alt text](https://github.com/trungnguyencs/CE264HDR/blob/master/ToneMappedImages/hdr_fusion_mertens.jpg "Title")
