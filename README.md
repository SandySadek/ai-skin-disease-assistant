# 🩺 AI Skin Disease Assistant

> A multimodal AI system that detects and classifies skin diseases using both **image analysis** and **natural language symptom descriptions** — combining Vision Transformers, BERT, LSTM, and Fusion models.

---

## 🎯 Project Overview

This project builds and compares **5 deep learning models** for skin disease classification across **8 dermatological conditions**, evaluating each model's strengths based on accuracy, F1-score, and real-world reliability.

### 🦠 Diseases Covered
| Disease | Difficulty | Notes |
|---|---|---|
| Acne | 🟢 Easy | Distinct appearance, recognizable keywords |
| Impetigo | 🟢 Easy | Characteristic sores and visual patterns |
| Skin Cancer | 🟢 Easy | Irregular borders are visually distinctive |
| Warts | 🟡 Medium | Recognizable shape, may resemble Psoriasis |
| Vitiligo | 🟡 Medium | White patches visible, some overlap |
| Eczema | 🔴 Hard | Strong similarity to Contact Dermatitis |
| Psoriasis | 🔴 Hard | Overlaps visually with Eczema |
| Contact Dermatitis | 🔴 Hard | Highly similar to Eczema |

---

## 🤖 Models Built & Compared

| # | Model | Type | Best Val Acc | Test Acc |
|---|---|---|---|---|
| 1 | **LSTM** | Recurrent NN | 100% | 100%* |
| 2 | **BERT** | NLP Transformer | 87.5% | 68.75% |
| 3 | **ViT** | Vision Transformer | 66.7% | 66.7% |
| 4 | **Fusion (BLIP)** | Multimodal | 56.25% | 50% |
| 5 | **EfficientNet B3** | Image CNN | 40% | 37.5% |

> *LSTM's 100% likely reflects overfitting on the small dataset. **BERT is the most practically reliable model.**

---

## 🏗️ Architecture

```
Patient Input
    ├── 📷 Image → EfficientNet B3 / ViT (Vision Transformer)
    ├── 📝 Text Description → BERT / LSTM
    └── 🔀 Both → Fusion Model (BLIP + EfficientNet + BERT)
                        ↓
              Skin Disease Classification
         (8 classes: Acne, Eczema, Psoriasis...)
```

---

## 📊 Key Results

- **Best NLP Model:** BERT — 87.5% validation accuracy, reliable medical context understanding
- **Best Image Model:** ViT — 66.7% consistent val/test accuracy, captures skin texture patterns via patch attention
- **Best Overall (practical):** BERT for text-based diagnosis
- **Future Potential:** Fusion model expected to outperform all others with a larger dataset

### 🔬 Per-Disease Insights
- **Easiest to classify:** Acne, Impetigo, Skin Cancer — each has unique visual/textual features
- **Hardest to classify:** Contact Dermatitis, Psoriasis, Eczema — these conditions visually overlap significantly

---

## 🛠️ Tech Stack

| Category | Tools |
|---|---|
| Deep Learning | PyTorch, HuggingFace Transformers |
| Image Models | EfficientNet B3, Vision Transformer (ViT) |
| NLP Models | BERT, LSTM |
| Multimodal | BLIP (Bootstrapped Language-Image Pretraining) |
| Data & Analysis | NumPy, Pandas, Scikit-learn |
| Visualization | Matplotlib, Seaborn |

---

## 📁 Project Structure

```
ai-skin-disease-assistant/
├── models/
│   ├── efficientnet_b3/       # EfficientNet training & inference
│   ├── vit/                   # Vision Transformer
│   ├── bert/                  # BERT text classifier
│   ├── lstm/                  # LSTM text classifier
│   └── fusion/                # Multimodal BLIP fusion
├── data/                      # Dataset & preprocessing scripts
├── notebooks/
│   └── skin_models_analysis.ipynb   # Comprehensive model analysis
├── requirements.txt
└── README.md
```

> ⚠️ **Note:** Model weights (`.pth`, `.safetensors`) are not included in this repo due to file size limits. Download links below.

---

## 🚀 Getting Started

### 1. Clone the repo
```bash
git clone https://github.com/SandySadek/ai-skin-disease-assistant.git
cd ai-skin-disease-assistant
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Download model weights
> *(Add your Hugging Face / Google Drive links here)*

### 4. Run inference
```bash
python predict.py --image path/to/skin_image.jpg --text "itchy red patches on arms"
```

---

## 📈 Analysis Notebook

The notebook [`skin_models_analysis.ipynb`](notebooks/skin_models_analysis.ipynb) includes:
- 📊 Val Accuracy vs Test Accuracy comparison charts
- 🌡️ F1 / Precision / Recall heatmaps per disease per model
- 🏆 Per-disease winner analysis
- 🔍 Disease difficulty classification
- 💡 Explanations for why each model performs the way it does

---

## 🔮 Future Work

- [ ] Expand dataset (DermNet, ISIC Archive)
- [ ] Improve Fusion model with larger multimodal training data
- [ ] Deploy as a web app (FastAPI + React)
- [ ] Add explainability (Grad-CAM for image models)
- [ ] Clinical validation with dermatologists

---

## 👩‍💻 Author

**Sandy Sadek**  
[![GitHub](https://img.shields.io/badge/GitHub-SandySadek-181717?logo=github)](https://github.com/SandySadek)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?logo=linkedin)](https://linkedin.com/in/YOUR_LINKEDIN_HERE)

---

## 📄 License

This project is for educational and research purposes.
