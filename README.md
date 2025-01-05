# MRI-Based Classification of Alzheimer's Disease Stages Using 3D, 2D, and Transfer Learning Convolution Neural Networks Models
This project aims to classify Alzheimer's disease stages (Cognitively Normal, Mild Cognitive Impairment, and Alzheimer's Disease) using advanced CNN architectures. Utilizing the ADNI dataset with 32,559 MRI scans, we implement workflows for data preprocessing, model training, and evaluation based on accuracy, AUC, and confusion matrices.
# Pipeline description
![image](https://github.com/user-attachments/assets/254a634f-3775-465a-804b-db319017e08a)
# Installation
git clone https://github.com/Toqa277/MRI-Alzheimers-CNN.git
cd MRI-Alzheimers-CNN
# Primary Scripts
## 1. Data Preprocessing 
it involved multiple essential steps to prepare MRI images for analysis, utilizing the dicom2nifti and antspyx packages. The process included converting DICOM files to NIfTI for a standardized format, applying bias field correction to enhance image quality, and registering images using the MNI152 template for alignment. Skull stripping isolated the brain region, while normalization ensured consistent intensity values. For 2D models, slice extraction converted 3D volumes into 2D slices, and resizing standardized image dimensions for compatibility with CNNs. Finally, min-max normalization scaled pixel values to 0–1, improving model performance.
## 2. 2D Proposed Model
* Two separate CNN models, CNN1 and CNN2, are constructed with unique configurations:
CNN1 focuses on extracting fine-grained local features using smaller kernels and regularized convolutional layers.
CNN2 uses larger kernels to capture broader, high-level patterns.
* Feature Fusion via Combined Model:
Outputs from CNN1 and CNN2 are concatenated into a combined model, where a dense layer processes the fused features.
The combined architecture facilitates the integration of complementary features captured by both CNNs, enhancing classification accuracy.
## 3. 3D ResNet-18
* Utilizes a residual learning framework with 3D convolutional layers and shortcut connections to effectively handle volumetric MRI data.
* Trains the network using cross-entropy loss and the Adam optimizer, incorporating dropout layers to reduce overfitting while tracking metrics like accuracy and loss.
* Adjusts weights iteratively through backpropagation
## 4. Transfer Learning 
* Using Pre-trained VGG16 Model: A pre-trained VGG16 model is utilized with weights from ImageNet. The input images, initially grayscale, are expanded to RGB by concatenating the grayscale channel. The VGG16 model's layers are frozen to use transfer learning for feature extraction.
* Custom Classification Layers: The extracted features are passed through custom dense layers with L2 regularization, batch normalization, and dropout layers. The final output layer uses a softmax activation to classify images into three categories.
# Primary Data Structures
The ADNI1 is a public-private collaboration supported by organizations such as the National Institute on Aging, the Foundation for the National Institutes of Health, the
 Alzheimer's Association, and several companies. This dataset includes advanced imaging techniques such as MRI. With 5,409 participants at various cognitive stages,
 it is one of the largest datasets available for Alzheimer's research. It includes 32,559 original MRI scans that areclassed as follows: 6,584 photos from AD patients,
 20,025 photos from MCI subjects, and 11,046 photos from CN participants
 # Results Summary:
3D ResNet-18: AUC = 0.92 (MCI), 0.73 (AD), 0.85 (CN), Validation Accuracy = 70%.
Dual 2D-CNNs: AUC = 0.96–0.98 across classes, Validation Accuracy = 85–90%.
VGG-16 Transfer Learning: Validation Accuracy = 90%.
# External Packages of Note
1. [ANTsPy](https://antspyx.readthedocs.io/en/latest/ants.html)
   A Python library for advanced image processing and registration, designed specifically for medical imaging applications.
2. [dicom2nifti](https://dicom2nifti.readthedocs.io/en/latest/)
   A tool for converting DICOM medical imaging files into the NIfTI format
3. [PyTorch](https://pytorch.org/docs/stable/index.html)
   A deep learning framework that enables flexible model building with dynamic computation graphs and accelerates training using GPU support.
4. [Keras](https://keras.io/)
   A user-friendly, high-level API for building and training neural networks
5. [Tensorflow](https://www.tensorflow.org/api_docs)
   An open-source machine learning library for numerical computation and building scalable machine learning models.
# Contributers
* Abdelrahman Fouad : Transfer Learning Implementation 
* Suhaila Samir : Proposed 2D Architure Implemntation 
* Toqa Khaled : 3D ResNet-18 Implemntation 
