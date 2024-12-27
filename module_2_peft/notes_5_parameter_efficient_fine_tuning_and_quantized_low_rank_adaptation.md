# Parameter-Efficient Fine-Tuning and Quantized Low-Rank Adaptation

## Overview

Congratulations on completing this lesson! You are now familiar with key concepts and techniques related to **Parameter-Efficient Fine-Tuning (PEFT)** and **Quantized Low-Rank Adaptation (QLoRA)**. This lesson covered various methods to efficiently fine-tune models while minimizing the number of trainable parameters and optimizing performance.

## Parameter-Efficient Fine-Tuning (PEFT)

PEFT methods are designed to reduce the number of trainable parameters in a model. Key methods include:

- **Selective Fine-Tuning:** Adjusts only specific parts of a model.
- **Additive Fine-Tuning:** Adds new parameters to the model while keeping existing ones fixed.
- **Reparameterization Fine-Tuning:** Modifies the parameterization of the model to make it more efficient.

### Low-Rank Adaptation (LoRA)

- LoRA aims to reduce trainable parameters by leveraging pre-trained models with high-dimensional matrices.
- The original weight matrix is kept frozen during fine-tuning.
- The **LinearWithLoRA** class copies the original linear model to create a **LoRALayer** object.
- **LoRA with PyTorch**: Uses the Internet Movie Database (IMDB) dataset to implement movie reviews, employing two low-rank matrices in the LoRALayer class.
- **LoRA with HuggingFace**: Facilitates easy model training using a tokenizer to create input IDs and loads BERT-like models from the HuggingFace transformer library.

## Quantized Low-Rank Adaptation (QLoRA)

QLoRA is a fine-tuning technique aimed at optimizing the performance and efficiency of large language models (LLMs) by reducing memory usage and enhancing computation efficiency.

### Key Concepts in QLoRA

- **Quantization**: Reduces numerical precision to a finite set of discrete levels, enabling efficient computation on hardware with limited precision.
  - The quantization range is between -1 to 1.
  - Methods used include 4-bit NormaFloat (NF4) and double quantization.
- Reduces memory footprints by utilizing model parameters, gradients, two-state optimizers, and activations.
- Model quantization reduces the model size and improves inference speed without compromising accuracy.

### Model Quantization Techniques

- **Uniform Quantization**: Maps values to a uniformly spaced set.
- **Non-uniform Quantization**: Uses a non-linear mapping for quantization.
- **Weight Clustering**: Groups similar weights to reduce model complexity.
- **Pruning and Quantization**: Combines weight pruning with quantization for model optimization.

### Tools for Model Quantization

- **TensorFlow Lite**: A framework for deploying TensorFlow models on mobile and embedded devices.
- **PyTorch**: Provides tools for model quantization to reduce model size and improve performance.

By understanding these methods, you can effectively fine-tune models with reduced computational resources while maintaining or enhancing performance.