**Face Detection with dlib**
**_1) HOG and Linear SVM of dlib_**

Pros:
   
>* More accurate than Haar cascades
>* More stable detection than Haar cascades (i.e., fewer parameters to tune)
>* Expertly implemented by dlib creator and maintainer, Davis King
>* Extremely well documented, both in terms of the dlib implementation and the HOG + Linear SVM framework in the computer vision literature

Cons:

>* Only works on frontal views of the face — profile faces will not be detected as the HOG descriptor does not tolerate changes in rotation or viewing angle well.
Requires an additional library (dlib) be installed — not necessarily a problem per se, but if you’re using just OpenCV, then you may find adding another library into the mix cumbersome.
Not as accurate as deep learning-based face detectors.
For the accuracy, it’s actually quite computationally expensive due to image pyramid construction, sliding windows, and computing HOG features at every stop of the window.
Upscaling needs to done for detection of smaller faces.

**_2) dlib CNN face detector_**

Davis King, the creator of dlib, trained a CNN face detector based on his work on max-margin object detection. The method is highly accurate, thanks to the design of the algorithm itself, along with the care Davis took in curating the training set and training the model.

Pros:

Incredibly accurate face detector
Small model size (under 1MB)
Expertly implemented and documented

Cons:

Requires an additional library (dlib) be installed
Code is more verbose — end-user must take care to convert and trim bounding box coordinates if using OpenCV
Cannot run in real-time without GPU acceleration
Not out-of-the-box compatible for acceleration via OpenVINO, Movidius NCS, NVIDIA Jetson Nano, or Google Cora
without GPU acceleration, this model cannot realistically run in real-time.
