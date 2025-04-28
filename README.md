# GeoViT: A Convolutional-Transformer Model for Geolocation Prediction

## 🧠 Model Summary
**GeoViT** is a hybrid convolutional-transformer neural network developed to predict geographic locations from Google Street View images. Inspired by the game *Geoguessr*, the model learns visual geographical cues such as architecture, road signs, vegetation, and terrain using the [OpenStreetView-5M](https://huggingface.co/datasets/osv5m/osv5m) dataset.

The architecture combines a convolutional frontend for local feature extraction with a Vision Transformer (ViT) backbone for global context learning.

---

## 🔍 Intended Use

### Primary Purpose
- Predict geolocation grid cell (based off Google S2 Geometry) from Google Street View images.

### Research Applications
- Visual geolocation
- Vision transformer ablation studies
- Robustness and generalization testing
- Multimodal geospatial learning

### Not Intended For
- Real-time navigation or emergency response
- Surveillance or any privacy-invasive applications

---

## 🏗️ Model Architecture

- **Input**: RGB image (3:2 aspect ratio converted to 224x224)
- **Backbone**:
  - Convolutional layers (ResNet50)
  - Vision Transformer (ViT) encoder (vit_small_patch16_224)
- **Output**:
  - Grid cell classification: Google's S2 Geometry Grid Cell

---

## 📦 Datasets

### 🗺️ Training Dataset
**[OpenStreetView-5M Subset](https://www.kaggle.com/datasets/josht000/osv-mini-129k)**  
- ~129k images from Google Street View for 10 US states
- Global GPS coordinate annotations  
- High variety in terrain and cultural environments

**Preprocessing Includes**:
- Resizing, normalization
- Mapping coordinates to S2 geometry grid system

---

## 📊 Evaluation Metrics

- **Top-1, Top-3, Top-5 prediction accuracy** 
- **Occlusion Sensitivity Analysis** for interpretability

---

## 🧪 Experiments

### ✅ Experiment 1: Vision Transformer Ablation

**Goal**: To understand what parts of an image the CNN-ViT hybrid model relies on to predict geolocation

- Slide a 32x32 pixel occlusion with stride 8
- Calculate drop in the model's confidence when sliding occlusion
---

### ✅ Experiment 2: Probability Distribution Visualized on a Map

**Goal**: Determine if the model clusters its predictions around the correct class or if the probability distribution is spread out

- Visualize the S2 Geometry grid system on US map with state lines
- Color model predictions to visually identify clusters

---

## ⚠️ Limitations

- Biased toward densely sampled or urban regions
- Decreased performance in homogenous areas (e.g., deserts, forests)
- No built-in uncertainty estimation (yet)
- Street View-based models can reflect socio-economic or regional biases

---

## 🧭 Ethical Considerations

- Model is trained on publicly available imagery
- Use responsibly and in compliance with privacy and geospatial laws
- Avoid applications that could infringe on personal or regional privacy

---

## 👨‍💻 Authors & Acknowledgments

- Developed by **Alan Tran and Caleb Wolf**
- Datasets:
  - OpenStreetView-5M (Hugging Face)
  - @article{osv5m,
    title = {{OpenStreetView-5M}: {T}he Many Roads to Global Visual Geolocation},
    author = {Astruc, Guillaume and Dufour, Nicolas and Siglidis, Ioannis
      and Aronssohn, Constantin and Bouia, Nacim and Fu, Stephanie and Loiseau, Romain
      and Nguyen, Van Nguyen and Raude, Charles and Vincent, Elliot and Xu, Lintao
      and Zhou, Hongyu and Landrieu, Loic},
    journal = {CVPR},
    year = {2024},
    }
  - StreetView Image Dataset (Kaggle)
- Inspired by research in Vision Transformers, CNN-ViT hybrids, and geolocation AI



---

## 📎 Related Links

- [OpenStreetView-5M Dataset](https://huggingface.co/datasets/osv5m/osv5m)
- [StreetView Image Dataset (Kaggle)](https://www.kaggle.com/datasets/ayuseless/streetview-image-dataset/data)
- [PlaNet - Photo Geolocation with Convolutional Neural Network](https://arxiv.org/abs/1602.05314)
