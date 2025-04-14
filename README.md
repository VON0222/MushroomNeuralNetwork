# Mushroom Neural Network

Neural Network trained to distinguish images and categorize them between four categories of mushrooms, separated in edible and poisonous and each divided in sporocap and mushroom sporocap. 

This project uses Tensorflow to create the model and the dataset "edible and poisonous fungi" uploaded in Kaggle by Marcos Volpato.

## Current State

Right now the project has a working model (Although it's not yet as accurate as the project aims to achieve), the data set being used separated in the train and test sets, an image data generator to increase the amout of data used to train the model and of course the preprocessed data that is used to train and test the model. In the latest update in order to have relevant metrics of the model and have valuable informamation with which make decisions and improve the model it has been added a confusion matrix (There are two implementations, a manual one and an automatic one made with a library). Also the complexity of the model has been slightly increased. This section will be updated as the project progresses.

## Decisions made

After the initial implementation of the model a confusion matrix was added to understand better the opportunity areas of the model and not make decision only based on the accuracy and loss of the model. Based on the information obtained from the confusion matrix it is clear that the model is still in it's early stages (currently underfitting). To solve this it's necessary to increase the model complexity, up till now the amount of neurons in the dense layers has been increased and two additional convolutional layers and a max pooling layers have been added. This is still too simple, so more developing in the complexity is necessary, however before doing that an investigation will be done to find out the proper way to increase the complexity in order to solve underfitting. Another issue detected is that it seems the model has a lot of mistakes predicting the image to be posionous sporocap most of the time. This seems to be caused by an imbalance of train data, as this type of image has almost three times more examples used to train the model than the edible sporocap. In order to solve this an investigation will be carried out to find out how to balance the data. 

After a small investigation two papers (referenced below) have been used to find a solution to the current problems of the model. While the implementation has yet to be carried out, it has been found out that in order to solve the data imbalance it is necesarry to do oversampling of the image categories which have less data available. This seems to be the best alternative from all the other methods explained in the paper because of the amount of classes and the imbalance ratio present in the model. The second paper proposed the use of a mask to force the model to learn more parameters from the images, and while this is still not surely to be implemented it is a valuable consideration to have in mind to improve the model.

## References used

Ghazal, M., Al-Khatib, W., & Al-Ayyoub, M. (2019). Convolutional neural networks for text classification: A comprehensive review. Neural Networks, 111, 25–45. https://doi.org/10.1016/j.neunet.2018.12.002

DeVries, T., & Taylor, G. W. (2017). Improved Regularization of Convolutional Neural Networks with Cutout. arXiv preprint arXiv:1708.04552. https://arxiv.org/abs/1708.04552
