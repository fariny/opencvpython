# opencvpython
## openCV library for Python from freecodecamp

!git clone https://github.com/misbah4064/opencvTutorial.git
%cd opencvTutorial/
from IPython.display import clear_output
clear_output()


### 1. Read and display an image

import cv2
from google.colab.patches import cv2_imshow
import numpy as np
image = cv2.imread("images/color.jpg")
print("color.jpg dimension is :" , image.shape)
cv2_imshow(image)


### 2. Changing color profile : grayscale

gray = cv2.cvtColor(image,cv2.COLOR_BGR2GRAY)
print(gray.shape)
cv2_imshow(gray)


### 3. Changing color profile : HSV

hsv = cv2.cvtColor(image, cv2.COLOR_BGR2HSV)
print(hsv.shape)
cv2_imshow(hsv)



### 4. Edge detection

gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
cannyImage = cv2.Canny(gray,150,200)
cv2_imshow(cannyImage)


### 5. Erosion

kernel = np.ones((2,2), np.uint8)
erodeImage = cv2.erode(cannyImage,kernel,iterations=1)
cv2_imshow(erodeImage)


### 6. Dilation

kernel = np.ones((3,3), np.uint8)
dilateImage = cv2.dilate(cannyImage, kernel, iterations=1)
cv2_imshow(dilateImage)


### 7. Dilation + erosion

erodeImage1 = cv2.erode(dilateImage, kernel, iterations=1)
cv2_imshow(erodeImage1)


### 8. Placing images side by side (horizontally)

display = np.hstack((cannyImage, dilateImage, erodeImage, erodeImage1))
cv2_imshow(display)


### 9. Drawing shapes and writing text on an image

import cv2
from google.colab.patches import cv_imshow

import numpy as np

### creating a blank "canvas" for drawing

canvas = np.zeros((512,512,3), np.uint8)


### DRAWING A CIRCLE

cv2.circle(canvas,(100,100),50,(0,0,255),-1)
#cv2.circle(tmpt nak lukis, coordinate(radius), saiz, warna, thickness)
#-1 thickeness utk fill shape, >=1 utk stroke


### DRAWING A RECTANGLE

cv2.rectangle(canvas,(160,160),(250,250),(0,255,0),-1)
#cv2.rectangle(tmpt nak lukis,(pt1:),(pt2:x,y),warna,thickness)

cv2_imshow(canvas)

