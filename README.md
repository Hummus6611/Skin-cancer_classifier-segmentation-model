# Skin-cancer_classifier-segmentation-model
This code implements a multi-task learning approach for skin lesion analysis, combining image classification and segmentation tasks.
Here's a breakdown of the code and its architecture:

Data Loading and Preprocessing:
Loads skin lesion images, corresponding masks, and classification labels.
Normalizes pixel values to [0, 1].
Splits the data into training and validation sets.

Model Architecture:

Classification Branch:
Utilizes a CNN for image classification.
The encoder consists of a convolutional layer followed by max-pooling.
The flattened output connects to a dense layer and outputs class probabilities.

Segmentation Branch:
Employs a U-Net-like architecture for image segmentation.
The encoder mirrors the classification branch's structure.
The decoder uses up-sampling layers and a convolutional layer to produce segmentation masks.

Combination:
Both branches share initial encoder layers.
The final model has two inputs (classification and segmentation) and two outputs (classification and segmentation).
The model is compiled with appropriate loss functions and metrics for each task.

Training:
Trains the combined model using both classification and segmentation data.
Utilizes categorical cross-entropy for classification and binary cross-entropy for segmentation.
Incorporates metrics like Categorical Accuracy and Mean IoU.

Testing:
Loads skin lesion images for testing classification and segmentation separately.
Makes predictions on both tasks using the trained combined model.

Evaluation:
Evaluates the model on the validation set for both tasks.
Prints the final classification accuracy and segmentation Mean IoU.

This architecture leverages shared encoder layers for efficient feature extraction and learning multiple tasks simultaneously. The classification branch focuses on predicting skin lesion types, while the segmentation branch aims to outline lesion boundaries. The multi-task approach allows the model to learn shared representations and potentially improve overall performance.
