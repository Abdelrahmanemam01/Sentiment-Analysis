# BERT vs DistilBERT for Emotion Classification

This document provides a **direct comparison** between two fine-tuned models used for **emotion classification of short English texts (tweets)**:

- BERT (bert-base-uncased)
- DistilBERT (distilbert-base-uncased)

Both models were trained on the **same emotion classification task** with **six emotion classes**:
sadness, joy, love, anger, fear, surprise.

--------------------------------------------------

Models Overview

BERT Model
- Base model: bert-base-uncased
- Architecture: 12 transformer layers
- Higher capacity and representational power
- Slower inference but slightly more stable predictions

DistilBERT Model
- Base model: distilbert-base-uncased
- Architecture: 6 transformer layers (distilled from BERT)
- Smaller, faster, and more efficient
- Slightly lower confidence but much faster inference

--------------------------------------------------

Emotion Classes

Both models predict the same six emotion labels:
- sadness
- joy
- love
- anger
- fear
- surprise

--------------------------------------------------

Inference Speed Comparison (GPU, batch size = 32)

BERT:
Batch size: 32
Total batch time: 17.99 ms
Per-sample time: 0.56 ms

DistilBERT:
Batch size: 32
Total batch time: 8.53 ms
Per-sample time: 0.27 ms

Observation:
DistilBERT is approximately **2× faster** than BERT during inference while processing the same batch size.

--------------------------------------------------

Prediction Confidence Example

Input text:
"I finally finished fine-tuning my model and it works great!"

BERT Prediction Probabilities (%):
joy        99.725204
love        0.112529
sadness     0.067743
surprise    0.040485
anger       0.038323
fear        0.015717

DistilBERT Prediction Probabilities (%):
joy        97.227654
love        1.391926
sadness     0.620732
anger       0.453740
surprise    0.190397
fear        0.115555

Observation:
- Both models correctly predict **joy** as the dominant emotion
- BERT produces a more **confident and peaked probability distribution**
- DistilBERT distributes probability mass more broadly across secondary emotions

--------------------------------------------------

Performance Summary (Test Set)

BERT:
- F1 Macro: 0.8801
- Accuracy: 0.9215

DistilBERT:
- F1 Macro: 0.8902
- Accuracy: 0.9270

Observation:
Despite being smaller, DistilBERT slightly outperforms BERT on this dataset.

--------------------------------------------------

Trade-off Summary

BERT:
- Higher model capacity
- More confident predictions
- Slower inference
- Higher computational cost

DistilBERT:
- Much faster inference
- Lower memory footprint
- Comparable or better performance
- Better suited for real-time and deployment scenarios

--------------------------------------------------

Conclusion

- Use **BERT** when maximum confidence and representational capacity are required
- Use **DistilBERT** when speed, efficiency, and deployment constraints matter
- For this task, **DistilBERT offers the best trade-off** between speed and performance

--------------------------------------------------

Author

Abdelrahman Emam
Faculty of Computers and Artificial Intelligence, Helwan University

GitHub: https://github.com/Abdelrahmanemam01
Hugging Face: https://huggingface.co/abdelrahmane01
