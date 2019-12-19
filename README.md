# SFND 2D Feature Tracking

<img src="images/keypoints.png" width="820" height="248" />

The idea of the camera course is to build a collision detection system - that's the overall goal for the Final Project. As a preparation for this, you will now build the feature tracking part and test various detector / descriptor combinations to see which ones perform best. This mid-term project consists of four parts:

* First, you will focus on loading images, setting up data structures and putting everything into a ring buffer to optimize memory load. 
* Then, you will integrate several keypoint detectors such as HARRIS, FAST, BRISK and SIFT and compare them with regard to number of keypoints and speed. 
* In the next part, you will then focus on descriptor extraction and matching using brute force and also the FLANN approach we discussed in the previous lesson. 
* In the last part, once the code framework is complete, you will test the various algorithms in different combinations and compare them with regard to some performance measures. 

See the classroom instruction and code comments for more details on each of these parts. Once you are finished with this project, the keypoint matching part will be set up and you can proceed to the next lesson, where the focus is on integrating Lidar points and on object detection using deep-learning. 

## Dependencies for Running Locally
* cmake >= 2.8
  * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1 (Linux, Mac), 3.81 (Windows)
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* OpenCV >= 4.1
  * This must be compiled from source using the `-D OPENCV_ENABLE_NONFREE=ON` cmake flag for testing the SIFT and SURF detectors.
  * The OpenCV 4.1.0 source code can be found [here](https://github.com/opencv/opencv/tree/4.1.0)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools](https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory in the top level directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./2D_feature_tracking`.

## Markdown
1. TASK MP.1 -> replace the following code with ring buffer of size dataBufferSize
Please refer to line 74-81 in MidTermProject_Camera_Student.cpp  
// push image into data frame buffer
        DataFrame frame;
        frame.cameraImg = imgGray;
        dataBuffer.push_back(frame);
        if (dataBuffer.size()>dataBufferSize){
            dataBuffer.erase(dataBuffer.begin());
        }
//// EOF STUDENT ASSIGNMENT
2. TASK MP.2 -> add the following keypoint detectors in file matching2D.cpp and enable string-based selection based on detectorType -> HARRIS, FAST, BRISK, ORB, AKAZE, SIFT
Please refer to line 220 - 252 in matching2D_Student.cpp

3. TASK MP.3 -> only keep keypoints on the preceding vehicle
Please refer to line 113-124 in MidTermProject_Camera_Student.cpp 

4. TASK MP.4 -> add the following descriptors in file matching2D.cpp and enable string-based selection based on descriptorType -> BRIEF, ORB, FREAK, AKAZE, SIFT
Please refer to line 63 - 103 in matching2D_Student.cpp

5. TASK MP.5 -> add FLANN matching in file matching2D.cpp
Please refer to line 195-202 in MidTermProject_Camera_Student.cpp, where provide option to select matcherType, descriptorType and selectorType.
Please refer to line 20 - 38 in matching2D_Student.cpp, where implement FLANN matching in the function of matchDescriptors.

6. TASK MP.6 -> add KNN match selection and perform descriptor distance ratio filtering with t=0.8 in file matching2D.cpp.
Please refer to line 46 - 59 in matching2D_Student.cpp, where implement KNN matching in the function of matchDescriptors.

7. Task MP.7 Counting keypoints
Please refer to line 130-151 in MidTermProject_Camera_Student.cpp.