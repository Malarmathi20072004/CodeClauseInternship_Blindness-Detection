# CodeClauseInternship_Blindness-Detection

This code is a deep learning model for the task of blindness detection, specifically for the APTOS 2019 Blindness Detection competition on Kaggle. The goal of the competition is to classify fundus images of the eye into five severity levels of diabetic retinopathy.

Data Preprocessing:

The Kaggle API is used to download the dataset for the competition.
The training data (train.csv) is loaded, and the distribution of classes is visualized.
Images are preprocessed using functions like preprocess_image and crop_image_from_gray.

Image Augmentation:

The ImageDataGenerator class from Keras is used to perform data augmentation on the training images. This includes horizontal and vertical flips, random rotations, and zooming.

Data Splitting:

The training data is split into training and validation sets using train_test_split.

Model Architecture:

The model uses the DenseNet121 architecture pretrained on ImageNet as a feature extractor.
The architecture includes global average pooling, dropout, and dense layers.
The model is compiled with the binary cross-entropy loss, Adam optimizer, and custom evaluation metric (F1 score).

Training:

The model is trained using the training data and augmented images.
A custom callback (KappaMetrics) is used to track the quadratic weighted Cohen's kappa score on the validation set during training.
The model weights are saved when the validation kappa score improves.

Kappa Score Evaluation:

The quadratic weighted Cohen's kappa score is used as the evaluation metric for the competition. It assesses the agreement between predicted and true labels, accounting for the fact that the classes have ordinal relationships.

Saving the Model:

The model architecture is saved in JSON format, and the weights are saved in HDF5 format whenever the validation kappa score improves.

The code demonstrates the process of loading and preprocessing data, building a deep learning model for image classification, performing data augmentation, and tracking the performance using a relevant evaluation metric for the competition. The focus is on detecting different severity levels of diabetic retinopathy.
