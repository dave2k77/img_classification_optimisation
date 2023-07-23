# OPTIMISATION MODELS FOR EFFICIENT AND HIGH ACCURACY IMAGE CLASSIFICATION NEURAL NETWORKS

# INTRODUCTION

In this study, we aim to explore the impact of different hyperparameter choices on the accuracy and efficiency of a convolutional neural network when classifying images from a large dataset. Our experiment will use the CIFAR-10 dataset, which consists of 60,000 colourful images, each sized at 32 x 32 pixels and with three colour channels based on the RGB colour profile. We classify each image into one of ten categories: aeroplane, automobile, bird, cat, deer, dog, frog, horse, ship, or truck. We aim to identify and select the best model design by thoroughly evaluating various hyperparameter selections for a CNN image classifier and measuring the corresponding improvements gained.

# DATA EXPLORATION AND ANALYSIS

The figure below shows a sample of the images in the CIFAR-10 dataset.

![image](https://github.com/dave2k77/img_classification_optimisation/assets/30156495/d991c436-9e8a-48ed-865f-e866f5db927b)


# NEURAL NETWORK ARCHITECTURE AND METHODOLOGY

 We used the following network architectures to conduct the experiments:

![image](https://github.com/dave2k77/img_classification_optimisation/assets/30156495/9acc41a6-1be8-4b9d-8ebc-566968a7a861)


The fine details of the architectures defined above are shown below:

**Network Structure**

|Layer  |Config. 1 | Config. 2 | Config. 3 | Config. 4 | Config. 5 | Config 6. |
|-------|:--------:|:---------:|:---------:|:---------:|:---------:|:---------:|
|CL     | 2        | 2         | 2         | 4         | 4         | 4         |
|FCL    | 1        | 1         | 1         | 3         | 4         | 3         |
|Dropout| -        | -         | 2         | 6         | 6         | 6         |
|Pooling| -        | -         | -         | Max       | Max       | Max       |
|Padding| same     | same      | same      | same      | same      | same      |

**Hyperparameters Selection: configurations 1,2 and 3**

|Hyperparameter     |Config. 1                   | Config. 2                  | Config. 3                  |
|:------------------|:---------------------------|:---------------------------|:---------------------------|
|Activation Function|ReLU and SoftMax            |ReLU and SoftMax            |ReLU and SoftMax            |
|Optimizer          |Stochastic Gradient Descent |Adam                        |Adam                        |
|Loss Function      |Categorical Cross Entropy   |Categorical Cross Entropy   |Categorical Cross Entropy   |
|Number of Batches  |32                          |32                          |32                          |
|Number of Epochs   |30                          |30                          |30                          |
|Dropout Rate       |20%                         |20%                         |20%                         |


**Hyperparameter Selections: configurations 4, 5 and 6**

|Hyperparameter     | Config. 4                  | Config. 5                  | Config. 6                  |
|:------------------|:---------------------------|:---------------------------|:---------------------------|
|Activation Function|ReLU and SoftMax            |ReLU and Sigmoid            |ReLU and tanh            |
|Optimizer          |Adam                        |Adam                        |Adam                        |
|Loss Function      |Categorical Cross Entropy   |Categorical Cross Entropy   |Categorical Cross Entropy   |
|Number of Batches  |32                          |32                          |32                          |
|Number of Epochs   |30                          |30                          |30                          |
|Dropout Rate       |20%                         |20%                         |20%                         |


# RESULTS AND FINDINGS

## Training and validation accuracy and loss for the six different network configurations

| Configuration     | Train Acc.   | Train Loss  | Val Acc  | Val Loss  |
|:------------------|:-------------|:------------|:---------|:----------|
|1                  |0.83          |0.51         |0.64      |1.2        |
|2                  |0.95          |0.12         |0.63      |2.9        |
|3                  |0.80          |0.57         |0.69      |0.97       |
|4                  |0.68          |0.89         |0.70      |0.88       |
|5                  |0.75          |0.74         |0.76      |0.70       |
|6                  |0.098         |7.3          |0.10      |8.1        |



## Training and validation errors for the six different network configurations

| Configuration     | Train MSE     | Train MAE    | Val MSE   | Val MAE    |
|:------------------|:--------------|:-------------|:----------|:-----------|
|1                  |0.025          |0.055         |0.051      |0.084       |
|2                  |0.0067         |0.013         |0.065      |0.076       |
|3                  |0.029          |0.055         |0.044      |0.074       |
|4                  |0.043          |0.084         |0.042      |0.090       |
|5                  |0.035          |0.069         |0.033      |0.067       |
|6                  |0.900          |0.880         |0.980      |0.940       |


The graphs below show that configuration 5 had the highest validation accuracy and the lowest validation loss, indicating that it is the best-performing model validation accuracy of 76%, validation MSE of 3.3%, and validation MAE of 6.7%. 

![image](https://github.com/dave2k77/img_classification_optimisation/assets/30156495/aaa3e25e-1367-478d-9fa3-359a78fa0daf)

![image](https://github.com/dave2k77/img_classification_optimisation/assets/30156495/c9ef35b4-55ce-4234-aae5-b80fb561d6bb)




A summary of its predictive performance is shown below:

|Class |Label      | % Correct |
|:-----|:----------|:----------|
|0     |Airplane   |79.70      |
|1     |Automobile |88.30      |
|2     |Bird       |60.20      |
|3     |Cat        |60.20      |
|4     |Deer       |71.00      |
|5     |Dog        |58.40      |
|6     |Frog       |87.60      |
|7     |Horse      |83.00      |
|8     |Ship       |87.10      |
|9     |Truck      |85.00      |




