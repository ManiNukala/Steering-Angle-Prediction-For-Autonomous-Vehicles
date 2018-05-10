# Steering-Angle-Prediction-For-Autonomous-Vehicles
In this project we will be teaching a car how to steer using deep learning. The dataset was open sourced by
Udacity for the Self Driving Car Challenge 2. The data consists of images from left, right and center camera at varying lighting, lane and
traffic conditions along with recorded driving data such as speed, throttle and steering angle.

## Image Processing
Initial images were sized 640 x 480 x3. Because the input to the deep learning network in the next stage requires, resized our images to height of 224 pixels, width of 224 pixel and 3 channels. The images were one a 256-color scale were normalized, and results were converted into a numpy arrays which will be the input to the next step. 
## Feature Extraction
VGG 16 was used for feature extraction purposes. The model was frozen from training and only the feed forward functionality was used till the last fully connected layer for feature extraction purposes. The final dense layer which performs classification has been removed and the output of the feedforward, which is a (4096,1) numpy array of all the images have been stored in an array, to be fed as input to the next step. 
## Training an LSTM
The Sequence of the features of the images created in the previous step were fed as the inputs to the LSTM. The label for each sequence is the steering angle of the first image in the sequence. The LSTM was a 4 layered network and batch normalization was used after the input layer to normalize existing variations in the input which existed due to variance in driving conditions found in the video frames. The LSTM network was trained in 40 epochs using Adam Optimizer. 
## Results
We achieve an mse of  0.00123 on our training data and 0.029 radians on the testing data. On visualizing our results we see that our model predicts exceptionally well.
