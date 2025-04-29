# Eggs Neural Network

Neural Network trained to distinguish images and categorize them between two categories of white eggs, separated in broken and not broken eggs. 

This project uses Tensorflow to create the model and the dataset "Egg Image Dataset" uploaded in Kaggle by Abdullah Khan Kakar. (The link to the dataset in Kaggle ccan be found in the References section)

## Current State

The project has a working model with an acceptable accuracy for the final update. The data set being used is separated in train, validation and test sets. Also an image data generator was used to increase the amount of data to balance both classes. Additionally more data augmentation is used to train and test the model. In the past update in order to have relevant metrics of the model and have valuable information with which make decisions and improve the model it has been added a confusion matrix. Also the complexity of the model was slightly increased. In this final update, not only the data set was completely changed but the model had multiple alterations in order to achieve an acceptable accuracy level.

First, in the code a function was added to improve the quality of the images and make it easier for the model to find lines and shapes through an increase of light and contrast. Second, there is a new and improved model composed of 4 convolutional layers, 3 maxpooling layers, 2 dense layers and both a flatten and dropout (0.35) instances. The model uses the optimizer Adam with a learning rate of 2e-4 and the precision, recall and AUC metrics available from keras, there is also the F1 metric however this one is obtained using the available precision and recall metrics. The model also uses callbacks in order to stop the training in the best point maximizing the accuracy and minimizing the loss. Originally weights were used to balance the difference of available images for training the model, however according to Buda et al, on most cases better results are achieved when using data augmentation instead of weights to balance the categories. As a result the model shows an accuracy of aproximately 0.82. The accuracy and prediction distribution can be better appreciated in the confusion matrix and normalized confusion matrix included in the model.

## Decisions made

After the initial implementation of the model a confusion matrix was added to understand better the opportunity areas of the model and not make decision only based on the accuracy and loss of the model. Based on the information obtained from the confusion matrix it is clear that the model was in it's early stages (underfitting). To solve this it's necessary to increase the model complexity, at the time the amount of neurons in the dense layers had been increased and two additional convolutional layers and a maxpooling layers were been added. Another issue detected is that it seems the model had a lot of mistakes predicting the image category most of the time always predicting the same category. This seems to be caused by an imbalance of data. In order to solve this an investigation was be carried out which revealed that on most cases the best approach is to undo the imbalance through data augmentation. 

After that last implementation and the changes made to solve the initial problem there still seemed to be multiple issues that caused the model to still only predict the same category all the time. Unfortunatly two dataset changes were made since the selected datasets were problematic, from images with too much noice to a mighty imbalance in the data available. As such the project aim was changed from mushroom classification to egg classification. Returning to the other problems, to help solve them more metrics were added to understand better the model performance. Additionaly stronger image preprocessing was made to help the model find more easily patterns in the images, improving illumination and contrast. Also weight calculation was made since the new egg dataset also contained some data imbalance, however as mentioned before data augmentation is a better option most of the time, as such weights were discarded as data augmentation took care of the imbalance problem. 

Another problem discovered was the excesive use of maxpooling in past models which stopped the model from gaining any useful information, however with the new image preprocessing and enhancement and the new order for the model layers to extract all the relevant features, the used maxpooling layers do help the model extract multiple relevant features. Now finally to get the best possible model and stop it from overfitting callbacks and dropouts were added to the model. The callbacks would help monitor the model through training and return to the best obtained model and the dropouts would stop the model from creating an imbalance in the variables saved and forcing it to actually use them all with precision. As it can be seen from all the graphics, tables and matrices included the result is a working model with an acceptable accuracy.

## References

Buda, M., Maki, A., & Mazurowski, M. A. (2018, August 9). A systematic study of the class imbalance problem in convolutional neural networks. Neural Networks. Advance online publication. https://doi.org/10.1016/j.neunet.2018.07.011

Khan, A. (n.d.). Egg image dataset. Kaggle. Retrieved April 29, 2025, from https://www.kaggle.com/datasets/abdullahkhanuet22/eggs-images-classification-damaged-or-not

Kiss, N., & Czuni, L. (2021, September). Mushroom image classification with CNNs: A case-study of different learning strategies. 2021 12th International Symposium on Image and Signal Processing and Analysis (ISPA). https://doi.org/10.1109/ISPA52656.2021.9552053

Ringa Tech (n.d.). Redes Neuronales Convolucionales - Clasificación avanzada de imágenes con IA / ML (CNN). YouTube. Retrieved April 29, 2025, from https://www.youtube.com/watch?v=4sWhhQwHqug

TensorFlow. (n.d.). Transfer learning and fine-tuning. TensorFlow. Retrieved April 29, 2025, from https://www.tensorflow.org/tutorials/images/transfer_learning
