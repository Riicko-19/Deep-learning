# Deep-learning
#  Indian Sign Language Gesture Recognition  
### Using EfficientNet-B0 + Transformer + CBAM

A deep learning model designed to recognize **static Indian Sign Language (ISL) gestures** using a hybrid architecture that combines:

- EfficientNet-B0 → base CNN feature extractor  
- CBAM (Convolutional Block Attention Module) → local + spatial attention  
- Transformer Layer → global context modeling

This project aims to improve accessibility for the hearing-impaired community by enabling automated ISL interpretation.

---

##  Key Features
- Classifies alphabets (A–Z) and numerals (0–9)
- Built on 100k+ image dataset (Mendeley ISL dataset)
- Robust to variations in:
  - background
  - lighting
  - clothing
  - hand orientation
- Lightweight architecture suitable for real-time execution

---

##  Dataset
We use the publicly available:

> Mendeley Indian Sign Language Dataset (Static Gestures)  

Contains:
- ~102,470 images
- Multiple age groups (Kids, Teens, Adults)
- Sleeve variations (Full/Half)
- Different illumination conditions

> 🔗 Add dataset link here:  
`[Dataset Link]`

### Preprocessing
- Images resized → `128×128` (EfficientNet-B0)
- Augmentations: flips, rotation, brightness, contrast, random crop, Gaussian noise
- Train/Val/Test split → `80/10/10`

---

## Architecture Overview

```text
Input Image
     ↓
EfficientNet-B0 (Feature Extractor)
     ↓
CBAM (Channel + Spatial Attention)
     ↓
Transformer Layer (Global Dependency Modeling)
     ↓
Dense Classifier
     ↓
Gesture Label
Why EfficientNet-B0?
Balanced accuracy vs computation

Ideal for real-time applications

But CNNs mostly learn local patterns → struggle with global structure

Why Transformers?
Model long-range relationships across image

Important for finger positioning and holistic gesture interpretation

Why CBAM?
Focuses on important features and important regions

Removes background noise and irrelevant features

Combined Effect
Component	Benefit
CBAM	Local attention, highlights hand region
Transformer	Global relationship understanding
Together	More robust + context-aware classification

 Installation & Setup
Clone Repository
bash
Copy code
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
Install Dependencies
bash
Copy code
pip install -r requirements.txt
Run Training
bash
Copy code
python train.py
Run Inference
bash
Copy code
python predict.py --image path/to/image.jpg
 Results (Sample Placeholders)
Model Variant	Accuracy	Parameters	Notes
EfficientNet-B0 only	90%	~5M	Baseline CNN
+ CBAM	93%	+ small overhead	Better spatial focus
+ CBAM + Transformer	95–97%	+ moderate overhead	Best performance

Replace with actual results once training is completed

 Future Work
Extend to dynamic gestures (video-based)

Deploy to edge devices (Jetson Nano / Mobile)

Real-time sign-to-speech system

 Team Members
Rhivu Dutta (20231CAI0012)

Praneetha Devarakonda (20231CAI0010)

G Abijith (20231CAI0040)

Guided By: Prof. Selvaraj Poornima
