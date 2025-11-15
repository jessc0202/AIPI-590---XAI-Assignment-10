# Mechanistic Interpretability Starter Notebook: AIPI-590 XAI Assignment 10

## Overview

This repository contains the starter code and analysis for **Assignment 10** of the **AIPI-590: Explainable AI (XAI)** course. The assignment focuses on **Mechanistic Interpretability (Mech Interp)**, which is the study of reverse-engineering the algorithms and circuits implemented within large language models (LLMs) to understand *how* they work, rather than just *what* they predict.

The notebook, `mechanistic_interp_starter.ipynb`, guides the user through the process of setting up the environment, loading a small Transformer model, and performing fundamental circuit analysis techniques.

---

## Setup and Prerequisites

To run this notebook locally or on Google Colab, you need the following dependencies.

### 1. Environment Setup

The primary tool used for mechanistic interpretability on Transformer models is the **TransformerLens** library.

**Installation (in the notebook):**

```python
# Install TransformerLens and other necessary libraries
! pip install transformer_lens
# also need to install PyTorch, circuitsvis, etc., depending on the environment
```
### 2. Required Libraries
transformer_lens: A specialized library for easy and robust experimentation with Transformer model internals.
torch: PyTorch for efficient tensor manipulation and model handling.
numpy: For standard numerical operations.
circuitsvis (Optional): Often used for visualizing attention patterns and internal model circuits.

## Notebook Contents and Analysis Steps
The mechanistic_interp_starter.ipynb notebook outlines a typical Mech Interp project workflow:

### 1. Model Initialization
Loading: Load a small, pre-trained Transformer model (e.g., GPT-2 Small) using HookedTransformer.from_pretrained().

Architecture Review: Examine the model configuration (layers, attention heads, residual stream dimension).

### 2. Defining the Task/Behavior
Prompt Design: Select a specific linguistic behavior (e.g., name repetition, induction) and design clean and corrupted prompts to test the behavior.

Baseline Metric: Establish a quantifiable metric, typically the logit difference, to measure the model's performance on the task.

### 3. Core Mechanistic Analysis
The notebook focuses on essential interpretability techniques:

Activation Caching: Execute the model while storing all intermediate activations (weights, residual stream values) at every layer.

Direct Logit Attribution (DLA): Calculate the contribution of specific components (attention heads, MLP neurons) to the final logit prediction.

Activation Patching / Causal Tracing: Systematically swap activations from a corrupted run into a clean run to precisely identify the minimal circuit required for correct behavior.

Attention Visualization: Plotting attention patterns to visually identify key heads responsible for carrying information across the sequence.

### 4. Conclusion and Discussion
The final section involves synthesizing the patching and attribution results to identify the complete mechanistic circuit for the chosen task and answering the assignment's interpretive questions.

I use Gemini 2.5 flash at 2025/11/12 8:09 pm to help with formatting and some part of the readme writing.
here is the link:https://gemini.google.com/app/fe8aaf50f3e43322?is_sa=1&is_sa=1&android-min-version=301356232&ios-min-version=322.0&campaign_id=bkws&utm_source=sem&utm_source=google&utm_medium=paid-media&utm_medium=cpc&utm_campaign=bkws&utm_campaign=2024enUS_gemfeb&pt=9008&mt=8&ct=p-growth-sem-bkws&gclsrc=aw.ds&gad_source=1&gad_campaignid=21015480439&gbraid=0AAAAApk5BhkV_lmXpTyRp8afYonolzG9I&gclid=CjwKCAiAoNbIBhB5EiwAZFbYGGTdte1Lf8XZdshhwwlvh6OSpm4qQG-vRciyuqDzeJC_9GPd3liFyRoCLOkQAvD_BwE
