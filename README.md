# Temporal Learning with No Backpropogation : Forward Forward Algorithm for Time Series Forecasting

## Overview
This repository contains an implementation of the Forward Forward Algorithm for stock price prediction and forecasting. Unlike conventional deep learning approaches that rely on backpropagation, this project implements an innovative training methodology inspired by Geoffrey Hinton's work on neural networks that learn through local updates only.

## Key Features
- **No Backpropagation**: Implementation of the Forward Forward Algorithm (FFA) that trains neural networks without using backpropagation
- **Contrastive Learning**: Utilizes positive and negative sample pairs to train the network through local weight updates
- **Performance**: Achieves superior results (test RMSE: 2.60) compared to traditional LSTM (3.62) and Transformer (9.53) architectures
- **Time Series Analysis**: Specialized for stock price forecasting using temporal sequential data

## Technical Implementation
The core innovation of this project is the Forward Forward Algorithm which:
1. Replaces the traditional forward-backward pass with two forward passes (positive and negative examples)
2. Updates weights locally based on the difference between positive and negative activations
3. Eliminates the need for error backpropagation through the network

### Model Architecture
The model consists of three feedforward layers:
- Input layer → 128 hidden units
- 128 hidden units → 64 hidden units
- 64 hidden units → 32 hidden units

Each layer updates its weights locally without gradient propagation from subsequent layers.

### Training Process
Rather than optimizing a global loss function, each layer:
1. Processes "positive" examples (correct input-output pairings)
2. Processes "negative" examples (incorrect pairings)
3. Updates weights to maximize the difference between positive and negative activations
4. Uses ReLU activation for non-linearity

### Data Preparation
- Historical AAPL stock data from 2018-2023
- Standardization of price data
- Creation of sequence-based training examples with 10-day lookback windows

## Results
The Forward Forward Algorithm demonstrates remarkable performance:
- **Forward Forward Algorithm**: Train RMSE: 2.31, Test RMSE: 2.60
- **LSTM**: Train RMSE: 3.74, Test RMSE: 3.62
- **Transformer**: Train RMSE: 6.91, Test RMSE: 9.53

This represents a 28% improvement in prediction accuracy compared to LSTM models.

## Advantages
- **Biological Plausibility**: More aligned with how biological neurons learn
- **Local Learning**: Each layer updates weights based only on its own inputs and outputs
- **Memory Efficiency**: Doesn't require storing activations for a backward pass
- **Potential Parallelism**: Each layer could potentially learn independently

## Future Work
- Implementing hybrid approaches that combine Forward Forward with traditional methods
- Exploring different network topologies for improved performance
- Testing on diverse market conditions and additional stock tickers
- Investigating potential for real-time prediction applications
