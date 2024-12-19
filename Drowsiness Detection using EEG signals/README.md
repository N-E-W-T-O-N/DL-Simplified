# DROWSINESS DETECTION USING DEEP LEARNING

## Goal
This project aims to implement a drowsiness detection system using deep learning techniques, comparing the performance of a convolutional neural network (CNN) with a Random Forest classifier for binary classification tasks.

## Dataset
The dataset for this project can be accessed from the following link: https://figshare.com/articles/dataset/EEG_driver_drowsiness_dataset/14273687

## Setup and Installation

1. **Python Environment**: Ensure Python 3.x is installed on your system.
2. **Libraries**: Install the necessary libraries using pip:

    ```bash
    pip install tensorflow scikit-learn matplotlib
    ```

### Libraries used
1. `Numpy`
2. `Pandas`
3. `sklearn`
4. `Keras`
5. `Tensorflow`
6. `matplotlib`

## Model Implementation

### Model - 1

**Architecture Description:**
- **Input Layer**: Receives sequences of length 12 with one feature dimension.
- **Convolutional Blocks**: Four blocks, each with two convolutional layers followed by element-wise addition (residual connection). Filters increase progressively (32, 64, 128, 256), ReLU activation.
- **Global Average Pooling Layer**: GlobalAveragePooling1D layer computes the average of each feature map across all spatial locations.
- **Dense Layers**: Four Dense layers (128, 90, 64, 32 neurons) with ReLU activation.
- **Output Layer**: Single neuron with sigmoid activation for binary classification.

**Training Description:**
- **Optimizer**: Stochastic Gradient Descent (SGD) with learning rate 0.001 and momentum 0.9.
- **Loss Function**: Binary Crossentropy.
- **Regularization**: No explicit regularization mentioned.
- **Normalization**: No explicit normalization mentioned.

<img width="551" alt="model_acc1" src="https://github.com/KamakshiOjha/DL-Simplified/assets/114620432/f0305d23-55da-4e17-bc43-7eb603c8ddea">
<img width="543" alt="model_loss1" src="https://github.com/KamakshiOjha/DL-Simplified/assets/114620432/1847bc5c-a839-478e-869b-976ba858d4fc">

### Model - 2

**Architecture Description:**
- **Input Layer**: Receives sequences of length 12.
- **Convolutional Layers**: Multiple convolutional layers with filter sizes of 32, 64, 128, and 256 respectively, each followed by Batch Normalization and ReLU activation.
- **Global Average Pooling**: Applied after the convolutional layers to reduce spatial dimensions.
- **Dense Layers**: Several Dense layers with decreasing neuron counts (128, 90, 64, 32), each followed by ReLU activation and Dropout regularization.
- **Output Layer**: Single neuron with sigmoid activation for binary classification.

**Training Description:**
- **Optimizer**: Stochastic Gradient Descent (SGD) with learning rate of 0.001 and momentum of 0.9.
- **Loss Function**: Binary Crossentropy.
- **Regularization**: Dropout regularization is used to prevent overfitting.
- **Normalization**: Batch Normalization is applied to stabilize and accelerate training.

<img width="545" alt="model_acc2" src="https://github.com/KamakshiOjha/DL-Simplified/assets/114620432/a8dcef05-042d-4156-8855-03500c83cf85">
<img width="542" alt="model_loss2" src="https://github.com/KamakshiOjha/DL-Simplified/assets/114620432/0cd8d2cf-00d8-4e0b-a9b7-cd1d53c33267">

### Model - 3

**Architecture Description:**
- **Input Layer**: Receives sequences of length 12 with one feature dimension.
- **Convolutional Blocks**: Four blocks, each with two convolutional layers followed by element-wise addition (residual connection). Filters increase progressively (32, 64, 128, 256), ReLU activation.
- **Max Pooling Layer**: After the final convolutional block, MaxPooling1D layer with pool size 2 and stride 1 reduces spatial dimensions.
- **Flatten Layer**: Reshapes output of the last convolutional layer into a 1D vector.
- **Global Average Pooling Layer**: GlobalAveragePooling1D layer computes the average of each feature map across all spatial locations.
- **Dense Layers**: Four Dense layers (128, 90, 64, 32 neurons) with ReLU activation.
- **Output Layer**: Single neuron with sigmoid activation for binary classification.

**Training Description:**
- **Optimizer**: Stochastic Gradient Descent (SGD) with learning rate 0.001 and momentum 0.9.
- **Loss Function**: Binary Crossentropy.
- **Regularization**: Dropout used to prevent overfitting.
- **Normalization**: Batch Normalization stabilizes and accelerates training.

<img width="544" alt="model_acc3" src="https://github.com/KamakshiOjha/DL-Simplified/assets/114620432/acf310f0-1c3c-4c79-9c28-496a15229f5b">
<img width="541" alt="model_loss3" src="https://github.com/KamakshiOjha/DL-Simplified/assets/114620432/b95b3d8a-4a41-44b5-989b-fc4fc8c2d876">


## Training and Evaluation
- **Data Splitting**: The dataset was split into training and testing sets using an 80:20 ratio.
- **Training**: The CNN model was trained for 150 epochs with a batch size of 4.
- **Evaluation Metrics**: Accuracy was used as the evaluation metric for both models.

## Results

To provide a conclusion based on the three models provided:

1. **Model 1**: This model consists of four convolutional blocks with residual connections, followed by global average pooling and dense layers. It employs convolutional layers to capture local patterns in the input sequences, while residual connections facilitate gradient flow and help in mitigating the vanishing gradient problem. The model architecture seems suitable for sequential data processing tasks, especially with its residual connections and global pooling layer.

2. **Model 2**: This model also utilizes convolutional layers but without residual connections. It follows a similar architecture to Model 1 but lacks the residual connections. This may result in slower convergence during training and may require more careful initialization or regularization to prevent vanishing gradients.

3. **Model 3**: Unlike the first two models, Model 3 employs a simpler architecture with convolutional layers followed by pooling and dense layers. It lacks residual connections and global pooling, which may limit its ability to capture long-range dependencies in sequential data. However, it may still perform adequately for simpler tasks or datasets with less complex patterns.

<img width="704" alt="Result" src="https://github.com/KamakshiOjha/DL-Simplified/assets/114620432/72e9bab2-ca14-4fef-a9ee-118fd6053c23">

**Conclusion**:
- Model 1 is the most comprehensive and robust among the three, due to use of residual connections and global pooling.
- Model 2 may suffer from vanishing gradients during training due to the absence of residual connections but could still perform reasonably well with proper tuning.
- Model 3, while simpler, may struggle with capturing complex patterns in sequential data compared to the other two models.

**The choice of the best model depends on factors such as the complexity of the dataset, computational resources, and the specific requirements of the task at hand.**
