# Emotion Classification with DistilBERT

This repository contains the **training, evaluation, and inference pipeline** for an **emotion classification task** using a **fine-tuned DistilBERT model**.
The model classifies short English texts (such as tweets) into **six emotion categories**.

🔗 **Hugging Face Model**
https://huggingface.co/abdelrahmane01/SentimentAnalysis-distilbert-base-uncased-finetuned-emotion

---

## 📌 Task Overview

**Task:** Multi-class text classification (Emotion Classification)  
**Input:** Short English text (tweets)  
**Output:** One of six emotion labels:

- sadness  
- joy  
- love  
- anger  
- fear  
- surprise  

The model was trained using the 🤗 **Transformers Trainer API** with a **class-weighted loss function** to address dataset imbalance.

---

## 🚀 Model Details

- **Base model:** distilbert-base-uncased  
- **Framework:** PyTorch + Hugging Face Transformers  
- **Loss function:** Cross-Entropy with class weights  
- **Primary metric:** Macro F1 Score  

---

## 📊 Model Performance (Test Set)

| Metric | Value |
|------|------|
| Loss | 0.2094 |
| F1 Macro | 0.8902 |
| Accuracy | 0.927 |

> Macro F1 is emphasized because the dataset is imbalanced.

Detailed **classification reports** and **confusion matrices** for both validation and test sets are included in this repository.

---

## 🧪 Training Summary

### Hyperparameters

- Learning rate: 2e-5  
- Train batch size: 32  
- Eval batch size: 32  
- Epochs: 10  
- Optimizer: AdamW  
- Scheduler: Linear  
- Seed: 42  

### Best Model Selection

The best checkpoint was selected based on **validation Macro F1 score**.

---

## 🧠 Dataset & Preprocessing

- Emotion-labeled tweet dataset (6 classes)
- Data split: Train / Validation / Test
- Tokenization using DistilBERT tokenizer
- Padding and truncation to a fixed maximum length
- Label encoding via Hugging Face `ClassLabel`

---

## ▶️ Inference Example

```python
from transformers import pipeline

classifier = pipeline(
    "text-classification",
    model="abdelrahmane01/SentimentAnalysis-distilbert-base-uncased-finetuned-emotion"
)

classifier("I finally finished fine-tuning my model and it works great!")
```

---

## ⚠️ Limitations

- Optimized for short texts
- English-only
- Not suitable for high-stakes decision-making
- May reflect dataset bias

---

## 🛠 Framework Versions

- Transformers: 4.44.2  
- PyTorch: 2.6.0  
- Datasets: 4.4.1  
- Tokenizers: 0.19.1  

---

## 📄 License

This project is licensed under the **Apache 2.0 License**.

---

## 👤 Author

**Abdelrahman Emam**  
Faculty of Computers and Artificial Intelligence, Helwan University

GitHub: https://github.com/Abdelrahmanemam01  
Hugging Face: https://huggingface.co/abdelrahmane01
