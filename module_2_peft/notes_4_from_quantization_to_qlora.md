# From Quantization to QLoRA

## Introduction

Welcome to "From Quantization to QLoRA." After watching this video, you will be able to define **quantization** and **QLoRA**, explain the importance of QLoRA, and understand how it optimizes performance and efficiency in machine learning.

## Understanding QLoRA

- **QLoRA** stands for **Quantized Low-Rank Adaptation**.
- It is a **fine-tuning technique in machine learning** designed to optimize the performance and efficiency of Large Language Models (LLMs).
- QLoRA achieves this by combining **quantization** with **LoRA** (Low-Rank Adaptation), allowing efficient use of computational resources without significantly sacrificing the model's accuracy.

## What is Quantization?

- **Quantization** reduces the precision of numerical values to a finite set of discrete levels.
- This process decreases memory usage and enables efficient computation on hardware with limited precision.
- Example: To convert an image's color to 256 shades of gray, quantization reduces the number of gray levels from 256 to fewer levels like 16, 8, 4, and 2. This results in less vibrant images but reduces memory requirements.

## Quantization in QLoRA

- **Quantization Range and Levels**:
  - In QLoRA, the quantization range lies between **-1 and 1**.
  - The number of bits used to represent values determines the quantization levels.
  - Example: 3-bit quantization represents eight discrete levels such as -1, -0.75, -0.5, -0.25, 0.25, 0.5, 0.75, and 1.

- **Unique Quantization Methods**:
  - QLoRA uses **4-bit normal float (NF4)** and **double quantization**.
  - Employs **paged optimizers**, a memory management trick, not a quantization technique, allowing large models to fit into limited memory by dynamically loading and unloading model parameters.

## Memory Footprint Reduction

### Analysis of a 7 Billion Parameter Model

1. **Model Parameters**:
   - Uses **FP16** (16 bits per parameter) resulting in a memory footprint of **14 gigabytes**.

2. **Gradients**:
   - Uses **FP16 gradients** resulting in a memory footprint of **14 gigabytes**.

3. **Optimizer States**:
   - Uses **FP32** (32 bits per optimizer state) resulting in a memory footprint of **56 gigabytes**.

4. **Activations**:
   - Assume FP16 activations are the same size as model parameters, resulting in a memory footprint of **14 gigabytes**.

- Total memory footprint for FP16: **98 gigabytes**.

### Contrast with 4-bit Model Quantization

- **4-bit Quantization**:
  - Uses 4 bits to represent each parameter, leading to a memory footprint of **3.5 gigabytes** for both parameters and gradients.
  - 8-bit quantized optimizer states result in **14 gigabytes**.
  - 4-bit quantized activations result in **3.5 gigabytes**.

- Total memory footprint for 4-bit quantization: **24.5 gigabytes**.

- **Reduction**: Memory footprint reduces from 98 gigabytes (FP16) to 24.5 gigabytes (4-bit quantization), a reduction of around **75%**.

## Importance of Quantization and QLoRA

- **Quantization** reduces the precision of numerical values to a finite set of discrete levels by defining the quantization range and levels.
- Understanding quantization and QLoRA techniques is crucial for developing efficient and scalable machine learning models.
- **QLoRA** reduces memory footprints by up to 75%, enabling models to run on less powerful hardware.