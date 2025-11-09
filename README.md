# 🧠 Temporal Learning Without Backpropagation

This project investigates an alternative training method to backpropagation for **time-series forecasting** tasks — inspired by the concept of **Forward-Forward Learning**.  
The model predicts **stock prices** using locally updated layers, providing evidence that forward-only optimization can achieve competitive or superior accuracy on temporal data.

---

## 🔍 Motivation

Conventional neural networks depend on backpropagation — a process that is computationally heavy, memory-intensive, and biologically implausible.  
This project demonstrates how **local layer updates** through dual forward passes can achieve effective learning **without global error propagation**.

---

## 🧩 Highlights

- 🚫 **No Backpropagation Required** — All learning occurs through **layer-local forward updates**.  
- ⚖️ **Positive–Negative Sample Learning** — The model learns to differentiate between correct and perturbed input sequences.  
- 📉 **Improved RMSE** — Achieved **2.60** test RMSE, outperforming LSTM (**3.62**) and Transformer (**9.53**) models.  
- 🧬 **Better Generalization** — Exhibited a **28% improvement** in unseen data prediction.  
- 🔁 **Focused on Temporal Sequences** — Applied to stock data for practical time-series forecasting.

---

## ⚙️ Core Methodology

1. **Dual Forward Pass**
   - The model runs twice per batch — once with **true samples** and once with **synthetic negatives**.  
2. **Local Weight Updates**
   - Each layer adjusts weights based on activation differences, removing the dependency on backward gradients.  
3. **Energy-Based Objective**
   - Encourages high activations for positive inputs and low activations for negatives.  
4. **Temporal Sequence Modeling**
   - Stock price history is segmented into overlapping time windows for supervised sequence prediction.

---

```bash
git clone https://github.com/<your-username>/temporal-forward-learning.git
cd temporal-forward-learning
pip install -r requirements.txt
python main.py
