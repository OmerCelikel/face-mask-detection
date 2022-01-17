# face-mask-detection
With that project it is possible to determine whether to wear a mask or not, for different people and camera angles.

	
# Face Mask Detection

## Introduction
Coronavirus, which emerged in August 2019, is a dangerous global disease. The World Health Organization (WHO) has confirmed that this disease is transmitted by droplets or through the air. There are ways we can prevent airborne transmission. One of them is to wear a mask. It is a greater risk not to wear a mask, especially in built-up areas. Despite the warnings, there are those who do not wear masks. Therefore, it is important to develop face mask detection. In this article, it is aimed to develop face mask detection with artificial intelligence. When the experimental results were made, it is possible to determine whether to wear a mask or not, for different people and camera angles.
Machine Learning
Machine learning is basically divided into these two groups. Supervised and Unsupervised learning
1. Supervised Learning
Machine learning trained in this way is called Supervised Learning if the data at hand has marked which input value will give which output.
For example, if you want to design a system that decides whether the pictures you give are human faces or not, if you first give different human faces and mark them as faces, if you mark the pictures without faces in the opposite direction, this is Supervised Learning.

## 2. Unsupervised Learning
It is a learning method that creates certain groups with the Clustering method according to the characteristics of the data at hand. In this learning style, it is not known whether this grouping is a face or not, but when you give a sample image, it can find out which bunch it is in and bring similar ones. This type of machine learning is also called Unsupervised Learning.
The machine learning that will be used in this article is Supervised Learning. Because masked and unmasked photographs were computerized. It was determined that they were masked or unmasked.
Implementation

First you need to run the aProcet.ipynb file. When this file runs, the camera will open and recognize your face 200 times. When you do this with a mask, it will be saved in the without_mask.npy file. Run this file again, put on a mask and save it to the with_mask.npy file.


Figure 1. It takes all the images one by one and saves them as npy.

Then the saved npy files are retrieved by loading. Reshape is done to convert the received files into 2 dimensions. In this process, the first dimension is the number of images, and the second dimension is size*size*rgb. Reshaped arrays are concatenated with the help of np.r_. After the concatenate, an np.zeros array of all images is created for you to label each image. The first 200 of this array is changed to 1. If the label of the image is 1, it means “ NO MASK ”, and 0 means “ MASK ”.



Figure 2. Npy file is loaded. Reshape , concatenate process has been done. All images are labeled.

The main purpose when setting up the machine learning algorithm is to predict the target variable as accurately as possible. Therefore, in order to test how accurate the forecast data are and to better optimize the model, we need to split the data set horizontally. Before modeling on the observation values, it has to be divided into 3 separate parts horizontally so that the model can be studied on one part (train), the model can be improved on the other part (validation) and tested in another part.

Figure 3. Train, test, split
PCA is a useful statistical technique used in recognition, classification, and image compression. It is a technique whose main purpose is to keep the data set with the highest variance in high-dimensional data, but to provide dimension reduction while doing this. By finding the general features in the over-dimensional data, it reduces the number of dimensions and compresses the data.


Figure 4. PCA

We can call SVM a discriminant classifier. SVM applies the data points in a split operation with a hyperplane with the largest amount of margin. SVM is required to classify new data points.

Figure 4. SVM

Accuracy Score




Result Code





Figure 5. Opens a new window and show result

haarcascade_frontalface it just shows the face area.  cv2.VideoCapture(0) is for my main computer camera. If “No Mask” in your face rectangle will be red, otherwise it will be green and It says “Mask”. We can say that there is no mask or mask, because according to our previous data, masked ones are assigned 0 and unmasked ones are assigned 1. The program can be terminated by pressing ESC.






Outputs


Outputs




Conclusion
It may be important to develop this algorithm on days when wearing a mask is very important. When the examples used for the algorithm used in the project were increased, it was seen that the result was better. Tested on a computer camera. This project can be developed and used especially in the control of closed areas.

References
https://colab.research.google.com/github/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/Index.ipynb
