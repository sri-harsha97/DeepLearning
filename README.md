<h1>Identify different types of cell nuclei in a colon cancer sample </h1>


Overall Goal

Colon cancer is the 3rd most common cancer in the world.

The normal colon has projections known as villi which absorb food and appear as circles of cells on a microscope image of the tissue (since the villi are cut through):
Histopathology image of early colon cancer.

The cell nuclei of these images can be segmented and coloured according to the different cell types:
Image segmented according to cell type.
(Orange cells are normal, red cells are cancer, green cells are immune cells invading to help, and blue cells are connective tissue.)

The following image shows a worse grade of colon cancer where you can see that the circles of normal cells have disintegrated and the nuclei have become larger and less well formed (due to DNA damage):
More advanced colon cancer with cell types indicated.

Digital pathology aims to apply machine learning to digital pathology images like these to determine if the tissue is normal or cancerous. One approach is to segment out the nuclei of cells from these images and classify them into different cell types including malignant cell nuclei (i.e. cancerous cells).

Your overall goal for this data science task is to train a deep neural network which can take a 32x32 image with a cell nuclei and classify it into one of the following types which are shown in the figures above:

Normal epithelial cells (shown orange).
Cancer epithelial cells (shown in red).
Immune leukocyte cells (shown in green).
Connective fibroblast cells (shown in blue).
The “Deep Learning for MSc Coursework 2022” Kaggle site has a training set of nuclei images (train.zip) with images given in suitable subdirectories with the label names. It also contains test archive (test.zip) which has similar 32x32 images of unlabelled cell nuclei. (Note that the identity of each image is given by its number 'N.png'. This then corresponds to its identity in the submitted csv files.)

You may notice that the classes in the training file are unbalanced with 'Normal' cells being in the minority. However, the testing file is balanced with roughly equal numbers of each cell type. So accuracy is an appropriate metric and this will be used. But you will have to think about how you handle the unbalanced training set.

The goal of this coursework is to develop a ConvNet that can predict the cell type of the images in the test.zip file. However, you must also attempt to do unsupervised pre-training by training an autoencoder on the unlabelled test image data and then use the 'encoder' section (with trained weights) as a feature extractor for the first part of your ConvNet.

You must also have a maximum of only 8 layers in your final ConvNet design - with layers defined as either (CNN + activation), (pooling) or (fully connected + activation).

You may wish to approach this challenge with the following steps (note the lecture on recommendations to producing a deep learning system):

Create a simple ConvNet trained on the labelled data and see if you can get better than random accuracy.
See if you can turn this simple ConvNet into an autoencoder and train it using the unlabelled test image data.
Use the encoder part of the autoencoder to recreate your ConvNet and train it using the smaller quantity of labelled data and see if you can beat the accuracy of your initial ConvNet.
Note that you may also want to use a validation dataset and plot out loss / accuracy curves to ensure you are not overfitting the training data set.

So you need to submit a 'test.csv' file where the first column is the identifier of the test image and the second column is your predicted cell type given as bold above.
