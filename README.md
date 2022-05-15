# Change Background: Greenscreen matting without the green screen

# INTRODUCTION

Human matting is an extremely interesting task where the goal is to find any human in a picture and remove the background from it. It is really hard to achieve due to the complexity of the task, having to find the person or people with the perfect contour. In this post, I review the best techniques used over the years and a novel approach published on November 29th, 2020. Many techniques are using basic computer vision algorithms to achieve this task, such as the GrabCut algorithm, which is extremely fast, but not very precise. 

# Start of the algorithm of the background removal algorithm 

I am going to turning on the webcam and taking one  snapshot of that an then i close my snapshot by using <webcam> and The <snapshot> function opens a camera preview on the device and returns the current frame in MATLAB® as an RGB image. The resolution of the image is specified by the Resolution property of the camera object cam.
  
```matlab
  clc
  clear
  close all 
  warning off 
  ca= webcam; 
  e=ca.snapshot;
  imshow(e);
  ```
  
  # Background Matting 
  I am reading an image that we are going to use to replace our background and that I am also showing.
  
  ```matlab
gk=imread('Nature.JPG'); 
figure; 
imshow(gk); 
   ```
  
  # create mask
   we gonna use imresize that  returns image gm that has the number of rows and columns specified by the two-element vector [r c] , createMask that returns a binary mask image with pixels inside the ‘e’ set to true and pixels outside the ‘e’ set to false and mkdir  folderName creates the folder folderName. If folderName exists, MATLAB® issues a warning. If the operation is not successful, mkdir throws an error to the Command Window.
 
   ```matlab
 [r, c , b]=size(e);
gm=imresize(gk,[r c]);
mkdir=createMask(e);
figure;
imshow(mkdir);
   ```
  
  # changing the background
  
  
  
  
  
  ```matlab
  gs=gm.*uint8(~mkdir);
figure;
imshow(gs);
subplot(1,2,1);
imshow(e);
subplot(1,2,2);
imshow(gs+e.*uint8(mkdir));
gm=gk;
   ```

  
 
  
  


