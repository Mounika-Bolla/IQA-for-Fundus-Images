# IQA-for-Fundus-Images

Overview
- Image quality assessment (IQA) for fundus images using ResNet50 and EfficientNet variants.
- Notebooks:
  - [RESNET50.ipynb](IQA-for-Fundus-Images/RESNET50.ipynb) — training/evaluation with ResNet50, prediction helper [`predict_`](IQA-for-Fundus-Images/RESNET50.ipynb).
  - [EfficientNet.ipynb](IQA-for-Fundus-Images/EfficientNet.ipynb) — EfficientNet baseline.
  - [EfficientNet_Adam.ipynb](IQA-for-Fundus-Images/EfficientNet_Adam.ipynb) — EfficientNet trained with Adam.
  - [Adam_RESNET50.ipynb](IQA-for-Fundus-Images/Adam_RESNET50.ipynb) — ResNet50 trained with Adam.

Dataset
- Local structure:
  - [DataSet/](IQA-for-Fundus-Images/DataSet/)
    - TRAIN/
      - Train_img_0/, Train_img_1/, Train_img_2/
    - TEST/
      - Test_img_0/, Test_img_1/, Test_img_2/
- In notebooks the mount path variables used: `train_path="/content/gdrive/MyDrive/TRAIN_UP"` and `test_path="/content/gdrive/MyDrive/TEST_UP"` (`RESNET50.ipynb`).

Quick setup (Colab)
1. Mount Drive: drive.mount('/content/gdrive') (see each notebook header).
2. Ensure dataset is copied to your Drive under the TRAIN_UP / TEST_UP folders.

Training & artifacts
- Models are saved as JSON + weights:
  - model JSON: `/content/gdrive/My Drive/model.json` (`model.to_json()` in [RESNET50.ipynb](IQA-for-Fundus-Images/RESNET50.ipynb))
  - weights: `/content/gdrive/My Drive/best_model.h5` (loaded in prediction flow)
- History is saved from `H.history` to `history.json` (see [RESNET50.ipynb](IQA-for-Fundus-Images/RESNET50.ipynb)).
- Typical evaluation call used: `model.evaluate_generator(...)` (see [RESNET50.ipynb](IQA-for-Fundus-Images/RESNET50.ipynb)).

Prediction
- Use the notebook helper function [`predict_`](IQA-for-Fundus-Images/RESNET50.ipynb) to:
  - load model JSON and weights,
  - compile model (SGD lr=1e-4, momentum=0.9 in current code),
  - preprocess with OpenCV, resize to (224,224),
  - call model.predict and map to labels.
- Example call inside notebook: `predict_("path/to/image.jpeg")`.

How to reproduce
1. Open the relevant notebook link above.
2. Confirm dataset paths and Drive mount.
3. Run training cells; save artifacts to Drive.
4. Use the saved model and [`predict_`](IQA-for-Fundus-Images/RESNET50.ipynb) for batch predictions (notebook shows iteration over `/content/gdrive/MyDrive/TEST_UP/Test_img_*` folders).

References (workspace)
- Files:
  - [IQA-for-Fundus-Images/RESNET50.ipynb](IQA-for-Fundus-Images/RESNET50.ipynb)
  - [IQA-for-Fundus-Images/EfficientNet.ipynb](IQA-for-Fundus-Images/EfficientNet.ipynb)
  - [IQA-for-Fundus-Images/EfficientNet_Adam.ipynb](IQA-for-Fundus-Images/EfficientNet_Adam.ipynb)
  - [IQA-for-Fundus-Images/Adam_RESNET50.ipynb](IQA-for-Fundus-Images/Adam_RESNET50.ipynb)
  - [IQA-for-Fundus-Images/README.md](IQA-for-Fundus-Images/README.md)
  - [IQA-for-Fundus-Images/DataSet/](IQA-for-Fundus-Images/DataSet/)
- Symbols in code:
  - [`predict_`](IQA-for-Fundus-Images/RESNET50.ipynb)
  - [`H.history`](IQA-for-Fundus-Images/RESNET50.ipynb)
  - [`model.evaluate_generator`](IQA-for-Fundus-Images/RESNET50.ipynb)
  - [`model.to_json`](IQA-for-Fundus-Images/RESNET50.ipynb)

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
