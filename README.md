# Tomato Leaf Disease Classification

This project focuses on developing a lightweight and accurate model for identifying tomato leaf diseases from images. Early disease detection is crucial for effective crop management and minimizing yield losses.

* **Lightweight Model:** The model is designed to be efficient and deployable across various platforms, including servers, web browsers, and edge devices.
* **High Accuracy:** Leverages transfer learning with EfficientNetB0 and data augmentation to achieve robust performance. The model exhibits robust performance, with a validation accuracy of 97.91% and a test accuracy of 97.43%, demonstrating effective generalization to unseen data.
* **Diverse Dataset:** Trained on a dataset containing over 10,000 images, covering 10 disease classes and healthy leaves.
* **Docker Deployment:** Provides a streamlined way to deploy the SavedModel using TensorFlow Serving within a Docker container for real-time predictions.

## Technical Requirements

* TensorFlow Serving 2.8.0
* Docker Desktop 4.34.2

## Deployment with Docker

1. **Export the Trained Model:** Ensure you have your trained Keras model saved in the SavedModel format (as done in the notebook).

2. **Run the Docker Container:**

   ```bash
   docker run -it -v tomato-leaf-disease-classification\models:/models -p 8501:8501 --entrypoint /bin/bash tensorflow/serving
   ```

3. **Start Model Inside the Container, s:**

   ```bash
   tensorflow_model_server --rest_api_port=8501 --model_name=saved_model --model_base_path=/models/saved_model/
   ```
   
## Usage

This project provides a deployed model for tomato leaf disease classification. You can use it to:

1. **Classify a single image:** Preprocess your image and send it to the TensorFlow Serving endpoint for prediction.
2. **Classify multiple images in a batch:** Preprocess your images and send them together to the endpoint for batch prediction.

For detailed code examples and explanations, please refer to the `deployement_testing.ipynb` notebook. 

## Project Structure

* `images/`: Contains the testing images.
* `models/`: Stores the trained models in various formats (Keras, TensorFlow.js, TensorFlow Lite, SavedModel).
* `requirements.txt`: Lists the project dependencies.
* `tomato_leaf_disease_classification.ipynb`: Jupyter Notebook with the model training and evaluation code.
* `deployement_testing.ipynb`: Jupyter Notebook with the model deployment code testing.

## Acknowledgments

* The dataset used in this project is sourced from [Kaggle](https://www.kaggle.com/datasets/ashishmotwani/tomato).
