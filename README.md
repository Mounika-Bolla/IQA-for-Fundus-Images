# IQA-for-Fundus-Images
# Abstract: 
### 
The accuracy of diagnosing and monitoring eye diseases using the fundus imaging is
strongly dependent on the quality of the images. Poor image quality can result in delays or inaccuracies in diagnosis, thus risking patient health. Image quality assessment
(IQA) is crucial for regulating retinal imaging quality and assisting in successful diagnoses. In this paper, a learning-based model for evaluating the quality of fundus
images is proposed. The EyeQ dataset is selected due to its ease of availability and
large collection of images. The images in the dataset are classified into three labels
based on their perceptual quality. Label 0 denotes good, 1 denotes fair and 2 denotes
poor quality. The ResNet50 and EfficicentNetB0 deep learning models are fine-tuned
with different hyperparameters to develop models, which are labelled as network-1 and
network-2, network-3 and network-4. Network-1,3 uses the Stochastic Gradient Descent (SGD) optimizer, Categorical Cross Entropy (CCE) loss function and is trained for
40 epochs. Network-2,4 utilizes an Adam optimizer, CCE loss function and is trained
for 40 epochs. The learning rate for both networks is kept the same. The performance
of the trained models is compared using the accuracy validation curve and the loss validation curve. Network-1 demonstrates an accuracy value of 85.8% with a loss of 0.37
and network-2 achieves an accuracy of 86.2% with a loss of 0.34.Similarly, Network-3
demonstrates an accuracy value of 81.4% with a loss of 0.45 and network-4 achieves
an accuracy of 84.72% with a loss of 0.38. The results indicate that network-2 and 4
slightly outperforms the performance of the other in terms of accuracy, and should be
preferred. Moreover, it is evident that the ResNet50 model is highly adept in appropriate
feature extraction and quality evaluation of retinal fundus imaging.
