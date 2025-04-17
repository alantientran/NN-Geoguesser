# GeoViT: A Convolutional-Transformer Model for Geolocation Estimation

## 🧠 Model Summary
**GeoViT** is a hybrid convolutional-transformer neural network developed to predict geographic locations from Google Street View images. Inspired by the game *Geoguessr*, the model learns visual geographical cues such as architecture, road signs, vegetation, and terrain using the [OpenStreetView-5M](https://huggingface.co/datasets/osv5m/osv5m) dataset.

The architecture combines a convolutional frontend for local feature extraction with a Vision Transformer (ViT) backbone for global context learning.

---

## 🔍 Intended Use

### Primary Purpose
- Predict (latitude, longitude) coordinates from Street View images.

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

- **Input**: RGB image (3:2 aspect ratio, optionally square for robustness testing)
- **Backbone**:
  - Convolutional layers (e.g., ResNet34, ConvNeXt)
  - Vision Transformer (ViT) encoder
- **Output**:
  - Coordinate regression: (Latitude, Longitude)
  - Optional: country classification or region cluster prediction

---

## 📦 Datasets

### 🗺️ Training Dataset
**[OpenStreetView-5M](https://huggingface.co/datasets/osv5m/osv5m)**  
- ~5 million images from Google Street View  
- Global GPS coordinate annotations  
- High variety in terrain and cultural environments

**Preprocessing Includes**:
- Resizing, normalization, color jitter
- Coordinate normalization (e.g., spherical projection)
- Optional tiling/cropping for ablation and robustness studies

---

## 📊 Evaluation Metrics

- **Mean Geodesic Distance (MGD)**  
- **Median Distance Error**  
- **Hit Rate** within threshold distances (e.g., 10km, 100km, 500km)  
- **Visual Attention Maps** for interpretability

---

## 🧪 Experiments

### ✅ Experiment 1: Vision Transformer Ablation

**Goal**: Measure the transformer's contribution to geolocation accuracy.

- Vary the number of transformer layers (e.g., 12 → 6 → 3)
- Vary attention heads (e.g., 12 → 6 → 3)
- Compare geolocation performance and attention visualizations

---

### ✅ Experiment 2: Robustness to Context & Aspect Ratio

**Goal**: Test the model’s ability to generalize under limited field-of-view.

- Evaluate on square-cropped test set from OSV5M
- Evaluate on **[StreetView Image Dataset](https://www.kaggle.com/datasets/ayuseless/streetview-image-dataset/data)** (square images)
- Compare against original 3:2 test set

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
