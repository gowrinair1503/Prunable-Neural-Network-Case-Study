# Prunable Neural Network (Self-Pruning Model)

## Overview
This project implements a self-pruning neural network where the model learns to remove unnecessary weights during training using learnable gates.

The goal is to reduce model complexity while maintaining performance.

## Key Idea
Each weight has a learnable gate:
- Gate ∈ (0,1) using sigmoid
- Final weight = weight × gate
- Gate ≈ 0 → weight is pruned

## Model Architecture
- Fully Connected Neural Network
- Custom `PrunableLinear` layers
- Trained on CIFAR-10 dataset

## Loss Function
Total Loss = CrossEntropy + λ × Sparsity Loss

- Sparsity Loss = average of gate values
- Encourages gates → 0 (pruning)

## Results

| Lambda | Accuracy (%) | Sparsity (%) |
|--------|--------------|--------------|
| 0.1    | 54.64        | 22.33        |
| 0.5    | 55.26        | 48.34        |
| 1.0    | 55.35        | 63.28        |

## Insights
- Increasing λ increases sparsity
- Accuracy remains stable despite pruning
- Shows many weights are redundant

## Project Structure
