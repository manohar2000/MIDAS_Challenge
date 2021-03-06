# MIDAS_Challenge

## Problem Statement
Task 2: 
* Part 1: Use this dataset (https://www.dropbox.com/s/pan6mutc5xj5kj0/trainPart1.zip) to train a CNN. Use no other data source or pre-trained networks, and explain your design choices during preprocessing, model building and training. Also, cite the sources you used to borrow techniques. A test set will be provided later to judge the performance of your classifier. Please save your model checkpoints.
* Part 2: Next, select only 0-9 training images from the above dataset, and use the pre-trained network to train on the MNIST dataset. Use the standard MNIST train and test splits (http://yann.lecun.com/exdb/mnist/). How does this pre-trained network perform in comparison to a randomly initialized network in terms of convergence time, final accuracy and other possible training quality metrics? Do a thorough analysis. Please save your model checkpoints.
* Part 3: Finally, take the following dataset (https://www.dropbox.com/s/otc12z2w7f7xm8z/mnistTask3.zip), train on this dataset and provide test accuracy on the MNIST test set, using the same test split from part 2. Train using scratch random initialization and using the pre-trained network part 1. Do the same analysis as 2 and report what happens this time. Try and do a qualitative analysis of what's different in this dataset. Please save your model checkpoints.


## Requirements :
open terminal and type 
`pip install -r requirements.txt`

## Analysis

This challenge mainly focuses on the analysis of a convolution neural network's performance on different variations of the [NIST dataset](https://www.nist.gov/srd/nist-special-database-19). The NIST dataset is a special variation of the MNIST database which includes small letters and capital letters as well. Thus making the total number of classes to be classified from 10 to 62 (10 digits + 26 small letters + 26 capital letters).
* In the [first part](part-1.ipynb), we are asked to build a CNN model on a limited number of images from the NIST dataset. This part is challenging as we are only given 40 images for each of 62 categories. This small dataset of 2480 images is insufficient as it might lead to overfitting. Additionally, we also have an implied constraint on the number of layers as this CNN has to be retrained on the 28x28 images in part 2 and part 3. To tackle these problems I have used various techniques like data augmentation, bigger kernel size, dropout layers and dynamic learning rate(to prevent local minima). These techniques help in preventing the model from overfitting and underfitting. 
* In the [second part](part-2.ipynb), we have to use the pre-trained model and re-train it on the MNIST digits dataset. On comparing the pre-trained model with a randomly initialised model, I concluded that that the pre-trained model has a faster convergence speed and can generalise slightly better. This is because the pre-trained model already has some initial knowledge and has to tweak its parameters to classify a subset of the previous classes whereas the randomly initialised model has to set its parameters from scratch. Since the dataset is large enough, the accuracy and loss of both the models are almost similar in the end and the major difference is between the learning curve.
* Finally, in the [third part](part-3.ipynb), we have to retrain our model on MNIST dataset digits which have been organised in the wrong folders(eg. folder0 contains images of all the digits except 0). Since there is no correct label for the model to train on, the model's performances degrade quickly. The pre-trained model, which has been extensively trained on the correct dataset, performs better than the randomly initialised model due to the pre-existing parameters and converges slowly. The pre-trained model gives higher accuracy and lower loss than the randomly initialised model.


To observe metrics like overfitting, convergence speed, stagnation at local minima and saturation of accuracy/loss we need to train the models for longer epochs. Therefore, all the models have been trained for 100 epochs. A thorough analysis has been provided in the respective notebooks. Please check!! :) 

## Results

I have used categorical cross entropy loss.
### Part 1 (Initial Model)
Set | Accuracy | Loss |
-----| --------| -----------
Training | 77.379% | 0.70 |
Testing |  69.89% | 1.244 |

### Part 2 (Comparision of pre-trained and randomly initialised model on MNIST dataset)
Training metrics:
Model | Accuracy | Loss |
-------| --------| ---------
Pre-trained model | 99.83% | 0.0048 |
Randomly initialised model | 99.86% | 0.0056 |

Testing metrics:
Model | Accuracy | Loss |
-------------| --------- | ----------- |
Pre-trained model | 99.4% | 0.041  |
Randomly initialised model | 99.35% | 0.041 |

### Part 3 (Comparision of pre-trained and randomly initialised model on wrongly tagged digits training dataset)
Training metrics :
Model | Accuracy | Loss |
-------------| --------- | ----------- |
Pre-trained model | 12.88%  | 2.19 |
Randomly initialised model | 10.40% | 2.30 |

Testing metrics
Model | Accuracy | Loss |
-------------| --------- | ----------- |
Pre-trained model | 11.21% | 2.21 |
Randomly initialised model | 10.40% | 2.30 |



P.S: Result - Didn't get selected(Though I don't understand why)
