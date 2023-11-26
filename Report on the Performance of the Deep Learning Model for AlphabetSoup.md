Report on the Performance of the Deep Learning Model for Alphabet Soup


Overview of the Analysis:

The purpose of this analysis is to develop a deep learning model using TensorFlow and Keras to predict the success of funding applications for Alphabet Soup, a nonprofit organization. The dataset used for this analysis is from charity_data.csv, and the target variable is "IS_SUCCESSFUL," indicating whether the funding application was successful.

Results:

Data Preprocessing:

Target and Features:

* Target Variable(s): IS_SUCCESSFUL  
* Feature Variable(s): All columns except IS_SUCCESSFUL and STATUS
* Variables Removed: EIN and NAME (non-beneficial ID columns)  

Binning:

* APPLICATION_TYPE: Binning was performed to group types with counts less than 500 into an 'Other' category.
* CLASSIFICATION: Classifications with less than 1000 occurrences were grouped into the "Other" category.

Encoding:

* Categorical data was converted to numeric using one-hot encoding..


Compiling, Training, and Evaluating the Model:

Initial Model (pre-feature importance evaluation):

* Neural Network Structure:

    * Input Layer: Number of features
    * Hidden Layer 1: 80 neurons, ReLU activation, with a dropout of 25%
    * Hidden Layer 2: 40 neurons, ReLU activation
    * Hidden Layer 3: 10 neurons, ReLU activation
    * Output Layer: Sigmoid activation
* Model Compilation: 

    * Loss: Binary Crossentropy
    * Optimizer: Adam
* Model Training:

    * Epochs: 30
* Model Evaluation:

    * Accuracy: 73.05%

Post-Feature Selection Model:

* Feature Selection:

    * Features with importance above the 50th percentile were selected.
* Neural Network Structure:

    * Input Layer: Number of selected features
    * Hidden Layer 1: 110 neurons, ReLU activation, with a dropout of 25%
    * Hidden Layer 2: 80 neurons, ReLU activation, with a dropout of 50%
    * Hidden Layer 3: 10 neurons, ReLU activation, with a dropout of 25%
    * Output Layer: Sigmoid activation
* Model Compilation:

    * Loss: Binary Crossentropy
    * Optimizer: Adam
* Model Training:

    * Epochs: 30
* Model Evaluation:

    * Accuracy: 72.82%

Version III (Hyperparameter Tuning):

* Hyperparameter Tuning:

    * Used Keras Tuner to search for the best hyperparameters.
* Best Hyperparameters:

    * Activation: ReLU
    * First Layer Neurons: 66
    * Number of Hidden Layers: 2
    * Neurons in Hidden Layers: 26, 1, 31, 1, 11
* Best Model Evaluation:

    * Accuracy: 73.20%

Keeping "NAME" Column:

* Data Adjustment:

    * "NAME" column was added back to features.
* Neural Network Architecture:

    * Input Layer: 80 neurons, ReLU activation, with a dropout of 25%
    * Hidden Layer 2: 40 neurons, ReLU activation
    * Hidden Layer 3: 10 neurons, ReLU activation
    * Output Layer: 1 neuron, Sigmoid activation

* Model Compilation:

    * Loss: Binary Crossentropy
    * Optimizer: Adam
* Model Training:

    * Epochs: 30
* Model Evaluation:

    * Accuracy: 76.85%

# Summary:

* The initial model achieved an accuracy of 73.05%, but further optimization was attempted.
* Feature selection in Version II did not significantly improve performance, with an accuracy of 72.82%.
* Hyperparameter tuning in Version III resulted in a slightly improved accuracy of 73.20%.
* Reintroducing the "NAME" column in the final model increased accuracy to 76.85%. 

# Recommendation:

Considering the improved performance after reintroducing the "NAME" column, it is recommended to keep this feature in the model. Further exploration and feature engineering may still be beneficial to enhance the model's predictive capabilities. Additionally, alternative models, such as ensemble methods or gradient boosting, could be explored for comparison and potentially better performance in solving this classification problem.