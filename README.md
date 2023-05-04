# Number-Plate-Recognition-in-Armenia

This capstone project presents an Automatic Number Plate Recognition (ANPR) system designed to detect and 
recognize Armenian license plates. The system employs an object detection algorithm to detect license plates, 
applies skew and rotation adjustment to correct the orientation, and uses optical character recognition to recognize 
the characters on the plate. The project achieves a high accuracy rate of 90% on plate detection and 95% on 
character recognition on a manually collected dataset consisting of high-quality photos and videos. Overall, 
this project presents a promising solution for ANPR systems.

The full reproducible code is available in the Detection&Recognition.py file
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1vFEyAeCmFb8QFZWE57XC9f177INedpqh?usp=sharing). 

The [following link](https://drive.google.com/drive/folders/1n1fak5Y7me_ifWcE9PARYmaqWE6sw-e-?usp=share_link) provides the dataset of images and their respective label .txt files which have the bounding box coordinates of 
the license plates. The folder also includes all images used in the research paper, the weight .pt file of the object detection training,
and other materials which may be helpful to implementing a similar system. 

## Object Detection

The YOLOv7 object detection algorithm was used to detect the license plates in an image.

![Figure 1. Original Image](https://drive.google.com/uc?export=view&id=1RAIC18q_jIc5eMi63vKRrD9lEmm2lxwu)

The License plate is detected and undergoes several steps for preprocessing and rotation angle adjustment. 

The detected region is cropped to only include the license plate. 
![Figure 2. Cropped Image](https://drive.google.com/uc?export=view&id=1uGPbxJLtoBPLJQB4AVqiB9Ij9ed_kzn0)

The image is converted from RGB color to gray. 
![Figure 3. Gray Image](https://drive.google.com/uc?export=view&id=11abSPW4rsaSmKBE_LUKEual_ezVDdYzI)

The edges are detected using Canny Edge Detection

![Figure 4. Edge Detected Image](https://drive.google.com/uc?export=view&id=1gvVY0EUhtHHdbEC9SfTbbfPtVypn_BLN)

Hough transform is used to detect straight lines

![Figure 5. Hough Transdoem](https://drive.google.com/uc?export=view&id=15axv6HudhHqY91rFf-OkvAKmnrn5qvqW)

The image is rotated using Affine transformations

<div style="text-align:center"><img src="https://drive.google.com/uc?export=view&id=1h6fOZiz5maWWfiM59-RRmQnHsax8QzxL" alt="Figure 6. Rotated Image" width="50%" /></div>

The contours of the image are detected. 

<img src="https://drive.google.com/uc?export=view&id=1v333umN_MTOMKyOVLIePnPmf0-pr1wfb" alt="Figure 7. Contours Image" width="50%" />

Finally, the characters of the number plate are recognized using EasyOCR.
<img src="https://drive.google.com/uc?export=view&id=187sFFvb5QL2hvNeRjfbl583w7mhEC6Es" alt="Figure 8. Final Image" width="50%" />
