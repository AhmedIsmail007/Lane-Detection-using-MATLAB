# Lane-Detection-using-MATLAB


## Overview
This Matlab project is designed to detect and draw lane lines in a video using computer vision techniques. The code reads a video file containing footage of a car driving on a road, processes each frame to identify lane markings, and then outputs a video with the detected lane lines.

## Initialization
The code initializes by clearing the command window, closing all figures, and clearing all variables from the workspace. It then imports the video file using VideoReader() with the file name specified as input_video.mp4.

Next, the code loads region of interest (ROI) variables from a previously saved .mat file named 'roi_variables'. The variables r and c are loaded from this file, defining the vertices of a polygonal region of interest used to extract the portion of the image containing the road and lane markings.

## Processing Loop
The main processing loop reads each frame from the video file using hasFrame() and readFrame() functions. Inside the loop, the following steps are performed for each frame:

1. Color Thresholding: The frame is converted from RGB to grayscale, and masks are created to identify white and yellow regions based on predefined threshold values for hue, saturation, and value channels.

2. Edge Detection: Canny edge detection algorithm is applied to the masks to obtain binary images containing only the edges of white and yellow regions.

3. Noise Removal: Small edges are eliminated using bwareaopen() function with a threshold of 15 to reduce noise in the edge maps.

4. Region of Interest (ROI): The polygonal ROI is applied to isolate the relevant portion of the image containing road and lane markings.

5. Hough Transform: Hough transform is used to detect straight lines representing lane markings within the ROI.

6. Lane Detection and Drawing: Detected lane lines are plotted on the original frame using Hough lines and written to the output video using writeVideo() function.
   
## Processing Loop
![output_snapshot](https://github.com/AhmedIsmail007/Lane-Detection-using-MATLAB/assets/108105551/caba50ee-9474-4166-aed7-8c777e394e2c)


## Usage
To use this code, follow these steps:

1. Place your input video file (e.g., input_video.mp4) in the same directory as the Matlab script.
2. Ensure that the ROI variables are saved in a .mat file named 'roi_variables' in the same directory.
3. Run the Matlab script to process the video and generate the output video with detected lane lines.

   
## Dependencies
This project relies on the following Matlab functions:

* VideoReader(): To read the input video file.
* VideoWriter(): To create the output video file with detected lane lines.
* roipoly(): To select the region of interest (ROI) from the image.
* edge(), bwareaopen(): For edge detection and noise removal.
* hough(), houghpeaks(), houghlines(): For Hough transform and lane line detection.
Make sure these functions are available in your Matlab environment.

## Notes
* Adjust the threshold values and ROI coordinates as needed for optimal lane detection based on your video footage.
* Visualizations using imshow() function are commented out but can be uncommented for debugging or visualization purposes.
