This project implements a Pruning Agent using Reinforcement Learning (RL) to optimize the number of filters in a neural network. The agent systematically reduces the number of filters in each convolutional layer by deciding which ones to prune, balancing model accuracy and computational efficiency.

# Introduction
In many deep learning tasks, computational efficiency is as important as achieving high accuracy. This project uses a reinforcement learning-based approach to prune convolutional filters in neural networks. The pruning agent learns to minimize the number of filters while maintaining acceptable performance, improving both accuracy and efficiency.

# Features
Policy Network: A neural network that decides which filters to prune.
Reward Calculation: The agent calculates a reward based on both accuracy drop and efficiency gain after pruning.
Pruning Layer-by-Layer: The model iteratively prunes filters from each convolutional layer and fine-tunes after pruning.
Efficient Training: Reinforcement learning is employed to train the pruning agent

### 1. Define the Policy Network: 
The PolicyNetwork is a simple feedforward network that outputs filter retention probabilities.

### 2. Pruning the Layers: 
The core pruning process happens layer-by-layer with the help of RL. The agent gets the actions (0 for prune, 1 for keep) and then applies these binary actions to prune filters in the current layer.

# How It Works?

### Policy Network
The PolicyNetwork outputs probabilities for each filter, indicating whether it should be kept or pruned. The pruning decision is made by sampling binary actions (0 or 1) based on these probabilities.

### Pruning Process
The agent decides which filters to prune based on the policy network's output.
Pruning is performed layer-by-layer using the prune_layer function.
After each pruning step, the model is fine-tuned to regain accuracy.

### Reward Calculation
The reward is based on two factors:

Accuracy drop: Calculated from the difference between the baseline accuracy and the accuracy after pruning.
Efficiency: Reward increases as fewer filters are kept.

### Training
Training the pruning agent involves iterating through each layer of the model, pruning filters, fine-tuning the model, and updating the policy network based on rewards.
