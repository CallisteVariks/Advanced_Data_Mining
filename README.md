# Advanced_Data_Mining


## Human gesture analysis
In this project's purpose is to train various classifiers (k-NN, Random Forest, MLP, SVM, etc.), evaluate their performance on the test set and compare their results. 
The dataset used in this task consists of samples of dynamic sign language gestures. The gestures were recorded using Microsoft Kinect. Microsoft Kinectproduces the 3D skeleton of the body with 20 joints as shown in the picture below.

<img align="middl" width=50% alt="Coding" src="https://github.com/CallisteVariks/Advanced_Data_Mining/blob/main/visuals/skeleton.png">

Thus, the data costs 60 (=20x3) dimensions. Each sign gesture is an ordered sequence of 20 joints representing their movement. The example below shows the 3 frames (60 dimensions each) of a sign gesture.

-0.37722 0.676463 2.477132 -0.36725 0.493018 2.566909 -0.52942 0.35584 2.57627 -0.1943 0.431102 2.561145 -0.56758 0.087563 2.615399 -0.03334 0.579121 2.433389 -0.58943 -0.12229 2.591342 -0.11276 0.775669 2.344967 -0.57233 -0.21128 2.548121 -0.17889 0.813138 2.315454 -0.34965 0.147281 2.577553 -0.34631 0.078289 2.574845 -0.41984 -0.00526 2.57652 -0.26435 0.007698 2.571115 -0.45848 -0.46034 2.673417 -0.23598 -0.47961 2.666875 -0.46103 -0.84788 2.715237 -0.22958 -0.86515 2.683695 -0.46605 -0.89852 2.631478 -0.20799 -0.93692 2.647322 

-0.37696 0.676517 2.47677 -0.36693 0.492976 2.56663 -0.52912 0.355951 2.576212 -0.19417 0.431174 2.561022 -0.56739 0.087649 2.61518 -0.03471 0.580535 2.43321 -0.58941 -0.12126 2.590974 -0.08724 0.764255 2.342603 -0.57263 -0.21045 2.548043 -0.14457 0.812098 2.321061 -0.34946 0.147283 2.57727 -0.34615 0.078288 2.574732 -0.41969 -0.00526 2.576389 -0.26428 0.007711 2.57107 -0.45848 -0.46306 2.674643 -0.23591 -0.48003 2.666955 -0.46135 -0.84594 2.716278 -0.22912 -0.866 2.683765 -0.48433 -0.92402 2.698534 -0.20776 -0.9373 2.633385

-0.37708 0.676532 2.476376 -0.36615 0.492745 2.566584 -0.52869 0.355584 2.575751 -0.1941 0.431192 2.560928 -0.5673 0.087411 2.61505 -0.03648 0.580642 2.432762 -0.5879 -0.11961 2.588753 -0.08555 0.764783 2.340891 -0.5722 -0.20986 2.547663 -0.11184 0.807713 2.319608 -0.34904 0.147191 2.577028 -0.34581 0.078215 2.574604 -0.41941 -0.00538 2.57626 -0.26406 0.007717 2.570943 -0.45842 -0.46289 2.674515 -0.23591 -0.48006

2.666903 -0.46149 -0.84789 2.716548 -0.22904 -0.86625 2.684294 -0.48464 - 0.92603 2.699292 -0.20736 -0.93739 2.639276


### Features Extracted
The cosine angles for each joint have been extracted costing another 60 dimensions. So, each gesture now is a sequence of positions and cosine angles of all joints.
< positions(20 * 3 = 60); cosine angles (20 * 3 = 60) > - >< 120 features per frame >
i.e. each gesture is a sequence of 120 features.

Classifiers like k-NN, SVM and Random Forest require the data to be position vectors in any dimensions. They cannot handle sequential data. Therefore, we have represented the data by their MEAN (mean) and STANDARD DEVIATION (std).
i.e. Each gesture is: <mean (positions), std (positions), mean (angles), std (angles)>
i.e. < 60; 60; 60; 60 >= 240dimensions.
Now, each gesture is 1x240 dimensional position vector. 


### Dataset CSV Files
To implement the task you are given a training and a test set to train and test your algorithms in csv file forms:
***
* train-final.csv: contains gestures for training 
* test-final.csv: contains gestures for testing.

Each row in any CSV file contains:
* a set of 240 features representing a sign gesture
* gesture name (string)
* gesture ID (numeric)
* the candidate who performed the sign gesture (string)


Some of these gestures are performed by single hand only and other gestures require both hands.
The task here would be to:

Task 1
* Handle missing values.
* Pre-process the attribute values, so that they are in the appropriate form to be given as an input for an algorithm.
* Visualize the data with different techniques.
  
Task 2
* Train several classifiers (Decision Tree, Random Forest, the training set.
* Evaluate their performance on the test set.
  
Task 3
* For the two best classifiers, reduce the dimensions • using PCA and evaluate their performance on the test set again.
* Reduce again to 50% (from 120 to 60) and evaluate.
