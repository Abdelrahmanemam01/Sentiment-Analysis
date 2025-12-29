# Emotion Classification with BERT

This repository contains the training, evaluation, and inference pipeline for an emotion classification task using a fine-tuned BERT model.
The model classifies short English texts (such as tweets) into six emotion categories.

Hugging Face Model:
https://huggingface.co/abdelrahmane01/SentimentAnalysis-bert-base-uncased-finetuned-emotion

--------------------------------------------------

Task Overview

Task: Multi-class text classification (Emotion Classification)
Input: Short English text (tweets)
Output: One of six emotion labels:

- sadness
- joy
- love
- anger
- fear
- surprise

The model was trained using the Hugging Face Transformers Trainer API.

--------------------------------------------------

Model Details

Base model: bert-base-uncased
Framework: PyTorch + Hugging Face Transformers
Loss function: Cross-Entropy Loss
Primary metric: Macro F1 Score

--------------------------------------------------

Model Performance (Test Set)

Loss: 0.2913
F1 Macro: 0.8801
Accuracy: 0.9215

Macro F1 is emphasized because the dataset is imbalanced and provides a more reliable measure of performance across all emotion classes.

--------------------------------------------------

Training Summary

Hyperparameters:
Learning rate: 1e-5
Train batch size: 16
Eval batch size: 16
Epochs: 6
Optimizer: AdamW (Torch fused)
Scheduler: Linear
Seed: 42

Best Model Selection:
The best checkpoint was selected based on validation Macro F1 score.

--------------------------------------------------

Dataset and Preprocessing

- Emotion-labeled dataset of short English texts (6 classes)
- Train / Validation / Test split
- Tokenization using BERT tokenizer
- Padding and truncation to a fixed maximum length
- Label encoding via Hugging Face ClassLabel

--------------------------------------------------

Inference Example

from transformers import pipeline

classifier = pipeline(
    "text-classification",
    model="abdelrahmane01/SentimentAnalysis-bert-base-uncased-finetuned-emotion"
)

classifier("I finally finished fine-tuning my model and it works great!")

--------------------------------------------------

Limitations

- Optimized for short texts
- English-only
- Not suitable for high-stakes decision-making
- May reflect dataset bias

--------------------------------------------------

Framework Versions

Transformers: 4.57.1
PyTorch: 2.8.0
Datasets: 4.4.1
Tokenizers: 0.22.1

--------------------------------------------------

License

Apache 2.0 License

--------------------------------------------------

Author

Abdelrahman Emam
Faculty of Computers and Artificial Intelligence, Helwan University

GitHub: https://github.com/Abdelrahmanemam01
Hugging Face: https://huggingface.co/abdelrahmane01
