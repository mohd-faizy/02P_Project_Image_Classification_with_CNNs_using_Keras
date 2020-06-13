<center><img src= 'https://miro.medium.com/max/3840/1*oB3S5yHHhvougJkPXuc8og.gif' <center></center>

# 2_Project_Image_Classification_with_CNNs_using_Keras
Training  a CNN in Keras with a TensorFlow backend to solve Image Classification problems


## __Project Overview__
Image Classification with CNNs using Keras

## __Objectives__
The Project Focus on two learning objectives:

1. Understand how to create convolutional neural networks in Keras.
2. Be able to train convolutional neural networks to solve image classification problems.

## __CIFAR-10 DATASET__

> The __CIFAR-10__ dataset (__Canadian Institute For Advanced Research__) is a collection of images that are commonly used to train __machine learning__ and __computer vision algorithms__. It is one of the most widely used datasets for machine learning research.The __CIFAR-10__ dataset contains __60,000 32x32 color images__ in __10 different classes__. The 10 different classes represent __airplanes, cars, birds, cats, deer, dogs, frogs, horses, ships,__ and __trucks__. There are __6,000 images__ of each class.

> Computer algorithms for recognizing objects in photos often learn by example. CIFAR-10 is a set of images that can be used to teach a computer how to recognize objects. Since the images in CIFAR-10 are __low-resolution (32x32)__, this dataset can allow researchers to quickly try different algorithms to see what works. Various kinds of convolutional neural networks tend to be the best at recognizing the images in __CIFAR-10__.

> CIFAR-10 is a labeled subset of the 80 million tiny images dataset. When the dataset was created, students were paid to label all of the images.
<center><img src='https://blog.kickview.com/content/images/size/w2000/2016/12/cfar-1.jpg'></center>

## __Project Structure__
The hands on project on Image Classification with CNNs using Keras is divided into following tasks:

### __Task 1: Introduction__
- Introduction to the problem.
- Introduction to the Rhyme interface.
- Importing the required libraries and helper functions.

### __Task 2: Pre-process Data__
- Importing the CIFAR-10 dataset.
- Creating a subset of the dataset which has just 3 classes instead of 10. This is done for both the training and test set.
- Randomly shuffling the newly created subset.

### __Task 3: Visualize Examples__
- Plotting randomly selected examples of a given set.
- We look at some examples from training and test set along with their labels.

### __Task 4: Create Model__
- Creating a Keras Sequential model.
- Creating a function to add a convolutional block to the model.
- A look at the model summary.

### __Task 5: Train the Model__
- Fit the model on the subset.
- Setting the EarlyStopping callback.
- Setting the ModelCheckpoint callback.

### __Task 6: Final Predictions__
- Plotting the training and validation accuracy from the training.
- Loading the best model.
- Getting predictions on the test set and displaying the results.
