# TASK 2 --> Lung Tidal Volume Estimation

## Dataset Acquisition and Evaluation


To build the model, I acquired a dataset from kaggle.

## Approach to find dataset
- First I did a simple google search to find a potential model,I got a link of a few medical websites that gave what tidal volume is how it is calculated , but non contained any dataset.
- When looking through kaggle, by searching for keyword ,'lung capacity' , I found a dataset (The lungcapacity.csv) which contained 750 entries.
- I cleaned the data , removed the outliyer and NA vales (The entire process is described in the Jupyter file.).
- Taking this cleaned data, I normalized it, and used it for my model. 

### Approach to the Problem
- I used a simple tensorflow model containing 3 layers.I also used activation function ReLU in case there is any non-linearity in the relation between lung capacity and other features.
- I used mse as my loss,since it will tell me the distance between the predicted value and the actual value.
- I introduced early stopping , and set it monitor val_loss and to restore the best weights. This prevented my model from over-fitting, and the requirement of monitoring the model for several epochs as it automatically stops at the best weights.
- Using a custom deep neural network, also prevented the need of feature engineering as this task is automatically handled by the neurons(In each neuron all the neurons from the previous layer combine with different weights thus handling the job of feature engineering.)

### Roadblocks and Measures to Increase Accuracy

During the task, I encountered several challenges:

-  **Data preprocessing**:
    1. This involved removing the NA values from the dataset. I made a function named RemoveNA which removes NA from the dataset  
    `(NOTE: All the data in the column must be numeric for this function to properly work.)`
    2. Converting the Columns like Gender, Smoker to numerical values so that the values can be interpreted by the model.
    3. Removing outliers from the dataset, for this I used the describe function of pandas.
- **Model selection**: 
    1. Experimenting with different sized models for the task having a small model was not able to capture the details and having a more complex model would cause overfitting and took longer time to train.
- **Overfitting**: Implementing early stopping to mitigate overfitting.

To increase accuracy, I:

- Fine-tuned model hyperparameters such as Number of epochs ,number of layers,etc.
- Introduced early stopping to stop when minimum val loss is achieved.

## Instructions to Run the Code
Use these Saved weights --> `Task_2_weights.h5`
To run the code:

1. Clone this repository to your local machine.
2. Upload the file `Task_2-->Aarush_singh_kushwaha.ipynb` in colab and read the comments as a guide to run the notebook.
3. Upload the `lungcapacity.csv` dataset to colab or directly use `Cleaned Lung Capacity.csv` to avoid data preprocessing step.  <br>
OR  

Directly run in colab though this [Notebook link](https://colab.research.google.com/drive/11O9-D08ry2M5Zk4UUcO4axn1OtBhIgk_?usp=sharing)


## Screenshots
Loss and Accuracy of the model over several epochs<br>
<img src="Screenshots/Screenshot from 2024-05-23 21-59-32.png" alt="Alt Text"  height="400">
<img src="Screenshots/Screenshot from 2024-05-23 21-59-23.png" alt="Alt Text" height="400">

Predicted values vs Actual values of the test set<br>
<img src="Screenshots/Screenshot from 2024-05-23 21-59-47.png" alt="Alt Text"  height="400">

