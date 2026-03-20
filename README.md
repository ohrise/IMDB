# 🎬 IMDB Sentiment Classification

IMDB 영화 리뷰 데이터셋을 활용하여,  
**Colab 무료 GPU 환경(제한된 메모리)**에서 최대 성능을 내는 모델을 구축하는 프로젝트입니다.

> baseline 대비 성능 개선을 목표로 다양한 학습 기법을 적용했습니다.

---

## 📊 Dataset

- [IMDB Dataset (Hugging Face)](https://huggingface.co/datasets/stanfordnlp/imdb)

---

## 🧠 Baseline

- 참고 모델: [bert-imdb](https://huggingface.co/lvwerra/bert-imdb)
- Accuracy: **94%**

---

## 🚀 Model

- Backbone: [bert-large-cased](https://huggingface.co/google-bert/bert-large-cased)

### 🔧 Applied Techniques

- FGM (Fast Gradient Method, Adversarial Training)
- Label Smoothing
- AdamW Optimizer + Weight Decay
- Gradient Clipping (max norm = 1.0)
- Dropout (0.3)
- AMP (Mixed Precision Training)

---

## 🏋️ Training Strategy

### Stage 1

- Train: 30%
- Validation: 20%

| Epoch | Loss Total | Val Accuracy |
|------|------|-------------|
| 1 | 816.90 | 0.90 |
| 2 | 554.49 | 0.92 |

→ Best model saved

---

### Stage 2

- Train: 50%
- Initialize from Stage 1 best model

| Epoch | Loss Total | Val Accuracy |
|------|------|-------------|
| 1 | 1948.03 | 0.93 |
| 2 | 554.49 | 0.92 |

→ Final model selected

---

## 📈 Result

- **Final Accuracy: 93%**

---

## 💡 Key Insight

- 제한된 GPU 환경에서도  
  **Adversarial Training + Mixed Precision** 조합이 성능 향상에 효과적
- staged training 전략이 안정적인 수렴에 기여

---

## 🛠 Tech Stack

- Python
- PyTorch
- Hugging Face Transformers
- Google Colab
