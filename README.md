## Capstone 3:Predicting Pneumonia in X-ray images

![X-ray_AI](https://github.com/user-attachments/assets/e19e1532-a61f-4b41-9dbe-ff9d7b13760c)




Introduction

A person dies of pneumonia every 13 seconds. As of 2016, pneumonia is the fourth leading cause of death worldwide, heavily impacting children under 5 and adults over 70. Early detection of pneumonia is critical in avoiding severe complications or death.

Background

One of the primary methods for detecting pneumonia is through the use of X-ray images. Chest X-rays are one of the most common diagnostic tools, as they can reveal the location and extent of inflammation in the lungs. However, interpreting chest X-rays can be time-consuming for radiologists, especially given the global shortage of trained medical professionals in underdeveloped regions. For example, Liberia, with a population of 3.5 million, has fewer than 10 radiologists.

Project Goals

This project aims to develop a tool for prescreening X-ray images to assist radiologists in diagnosing pneumonia efficiently and accurately. By leveraging deep learning models, this tool can:

- Help reduce the diagnostic workload for radiologists.

- Provide faster and more accurate predictions.

- Serve as a critical resource in underdeveloped and rural areas where radiologists are scarce.

Impact

- Accurate and early detection of pneumonia can save lives by:

- Speeding up the diagnostic process for patients.

- Allowing for timely medical intervention, which can be the difference between life and death, especially for young children and older adults.

- Supporting healthcare systems in resource-constrained regions, improving global health outcomes.

This project demonstrates the potential of artificial intelligence to assist in medical diagnostics, addressing a pressing global health issue effectively.



## The data was obtained from [kaggle.com](https://www.kaggle.com/datasets/alifrahman/chestxraydataset/data) this data set contains over 5000 x-ray images of the lungs of healthy patients and patients with Pneumonia classified either as bacterial infection or viral.

# 1. Load data and install necessary libraries:
In this part of the project the data is loaded using a function get_training_data. Before this project I had never worked with a data set that was in image form. This function gets the images from my directory and places them in an empty arrary data. The fucntion then reads the images in grayscale mdoe, resizes to ensure uniform dimension for training. The resize image is then appended and its numerica label to the data array.
This part of the project was time consuming and I had to look at online resources to help write this function. 
# 2. EDA:
In this step of the project I examine the qualites of my data such as number of training images, number of testing and validation images. Furthermore I get to visualize the distribution of my training and testing data which helps me determine appropriate course of action to handle imbalanced data set. I also discover an important feature, pixel intensity between lung images with Pneumonia vs. Normal lung images.


![image](https://github.com/user-attachments/assets/814f2100-c08b-4b1e-a5fb-c06a7579251d)



![image](https://github.com/user-attachments/assets/cc19771a-1d6c-484f-a06c-e801667e1393)



# 3. Preprocessing: 
In preprocessing I load ImageDataGenerator which helps with data augmentation on images. This part of the project involves rescaling images, randomly adding image rotation and shifts to improve roboutness of the model.

# 4. Modeling: 
In this part of the project I decide to choose to build two Convolutional Neural Network models. The first model is set as sequential which means that data flows linearly from one layer to the next. The first convolutional layer applies a filter and a ReLU is applied to replace negative values with 0. The model transforms image data into abstract features and then uses those featurs to make a binary classification predicting Pneumonia or Normal.
In the second model_2 I include BatchNormalization, Dropout and L2 regularization to improve generalization and reduce overfitting, this however leads to increased time needed to train the model.  


# 5. Model evaluation and Metrics: In this part of the process I use a classification report, confusion matrix and test accuracy to compare how both models perform.
- Model 1 classification report and accuracy: The metric that I decided to focus on is Recall or True Postitive Rate as this metric is vital in correctly evaluating if my model does what its suppose to which is to identify X-ray images of patients with Pneumonia.
While this models test accuracy is 77% its Recall score for classifying patients with Pneumonia is 87%.


<img width="416" alt="image" src="https://github.com/user-attachments/assets/c47f2c29-f010-4c77-b9b4-0d9781af6acb" />




- Model_2 classification report and accuracy: The metric that I decided to focus on for model_2 was Recall. This models recall score was lower at 83% and its accuracy was also lower at 72%. This reduction in performace leads me to believe that my first model might be slighly overfitting as model_2 has functions to help reduce overfitting.


<img width="414" alt="image" src="https://github.com/user-attachments/assets/15afc1a4-6ea8-4421-be33-7eabffea0291" />




# 6. Conclusion:

Given that my stated goal was to develop a model that was effective at identifying X-ray images of patients with Pneumonia my first model achieved a Recall socre of 87%. While this leaves room for improvement considering that not identifying a patient with Pneumonia can have catostrophic consequences, this is a great first step and can be used as a prescreening tool in medical diagnosis.

# 7. Next steps:
- 1. Retrain model on at least 50 epochs as this is the suggested number for medical imaging.

- 2. Use oversampling techniques on Pneumonia images to increase recall score of this class. 

- 3. Add additional convolutional layers to increase complexity.

- 4. Use transfer learning with pre-trained models.

- 5. Adjust Thresholds.
 
       




