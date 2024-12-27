# Fine Tuning with PyTorch

## Introduction to Fine Tuning

**Fine tuning** in machine learning is the process of adapting a **pre-trained model** for specific tasks or use cases. It has become a fundamental technique, especially in the training of foundation models used for generative AI.

## Objectives

After this lesson, you will be able to:
- Prepare the dataset for loading and model definition.
- Fine-tune the complete model and its final layer.

## Datasets

1. **IMDB Dataset**
   - Contains 50,000 samples of movie reviews.
   - It is a binary classification dataset with two classes: **positive** and **negative**.

2. **AG News Dataset**
   - Contains 120,000 training samples and 7,600 test samples.
   - It is a multi-class classification dataset with four classes: **world sports**, **business**, and **science and technology**.

## Fine Tuning Process

### Pre-training and Fine-tuning Approach

- **Pre-train** the model on the AG News dataset to build a robust understanding of language in context from diverse topics.
- **Fine-tune** the IMDB dataset to specialize the model for sentiment analysis of movie reviews.

### Preparing the Data

1. **Loading the IMDB Dataset**
   - Define a class to load the IMDB dataset.
   - Load the dataset into test and train iterators.

2. **Tokenizer and Embeddings**
   - Define a tokenizer and load GloVe embeddings.
   - Build a vocabulary object from the pre-trained GloVe word embedding model, assigning index values and setting the default index to the token.

3. **Data Transformation**
   - Convert the dataset into map-style datasets and perform a random split to create separate training and validation datasets.
   - Create a collate function that:
     - Tokenizes the dataset.
     - Converts tokens to sequences of token indices.
     - Transforms sequences and class labels into tensors.

### Model Definition

- Define the **transformer-based model class** for classification using PyTorch.
- The constructor initializes the text classifier with configurations such as the number of classes, vocabulary size, and transformer settings (number of heads and layers).
- The **forward method** applies embeddings, adds positional encoding, passes data through the transformer encoder, averages the data, and finally classifies it using a linear classifier.

### Training and Evaluation

1. **Training the Model**
   - Use the provided optimizer and loss criteria.
   - Iterate through the specified number of epochs.
   - Evaluate model performance on a validation dataset, print the loss per epoch, and optionally save the model and performance metrics if the validation accuracy improves.

2. **Prediction**
   - The predict function processes text for machine learning and uses a pre-trained model to predict text labels for classification.

3. **Fine-tuning the Model**
   - Create a model object with PyTorch, using four neurons in the output layer.
   - Load parameters from a pre-trained model on the AG News dataset.
   - Adjust the number of neurons in the final layer from four to two to match the IMDB dataset's categories.
   - Define loss function, optimizers, and scheduler for fine-tuning with the IMDB dataset.

### Results and Trade-offs

- **Complete Model Fine-tuning**: Achieves approximately 90% accuracy on validation data.
- **Final Layer Fine-tuning**: While training is faster, performance is significantly worse. This necessitates a trade-off between fine-tuning the entire model and certain key parameters.

## Conclusion

In this lesson, you learned that fine-tuning involves adapting a pre-trained model for specific tasks. The process includes data preparation, model definition, training, and evaluation. Fine-tuning the entire model yields better performance than only tuning the final layer, but it requires balancing speed and accuracy.