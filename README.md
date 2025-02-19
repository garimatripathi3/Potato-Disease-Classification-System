# 🥔 Potato Disease Classification

An end-to-end deep learning solution that automatically identifies diseases in potato plants through image analysis, helping farmers detect problems early and take preventive measures.

![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![GCP](https://img.shields.io/badge/Google_Cloud-4285F4?style=for-the-badge&logo=google-cloud&logoColor=white)

## 📋 Project Overview

This project delivers a complete workflow for potato disease classification:

- **AI Model**: TensorFlow-based CNN trained on potato leaf images
- **Backend API**: FastAPI service exposing model predictions
- **Web Interface**: ReactJS application for desktop/laptop use
- **Mobile App**: React Native implementation for field diagnostics
- **DevOps**: Docker-based CI/CD pipeline for seamless deployment

The system accurately classifies potato plant images into three categories:
- Healthy plants
- Plants with Early Blight disease
- Plants with Late Blight disease

With 99%+ confidence in predictions, the system provides reliable results for farmers to take timely action.

## 🏗️ System Architecture

```
                                 ┌─────────────────┐
                                 │   Image Input   │
                                 └────────┬────────┘
                                          │
                 ┌──────────────────────┬─┴──┬──────────────────────┐
                 │                      │    │                      │
        ┌────────▼─────────┐  ┌─────────▼────▼──────────┐  ┌───────▼────────┐
        │   Web Frontend   │  │      API Backend        │  │   Mobile App   │
        │     (ReactJS)    │  │       (FastAPI)         │  │  (React Native)│
        └────────┬─────────┘  └─────────┬───────────────┘  └───────┬────────┘
                 │                      │                          │
                 │             ┌────────▼───────────┐              │
                 └─────────────►  TensorFlow Model  ◄──────────────┘
                               └────────┬───────────┘
                                        │
                               ┌────────▼───────────┐
                               │    Prediction      │
                               │   with 99%+ acc    │
                               └────────────────────┘
```

## 🧠 Machine Learning Model

- **Framework**: TensorFlow / Keras
- **Architecture**: Convolutional Neural Network (CNN)
- **Training Dataset**: Kaggle potato disease image collection
- **Optimization**: Transfer learning with fine-tuning
- **Performance**: 99%+ accuracy on validation data
- **Model Size**: Optimized for edge deployment (~15MB TF Lite)

## 🚀 Implementation Details

### Backend (FastAPI)

```python
from fastapi import FastAPI, File, UploadFile
import tensorflow as tf
import numpy as np

app = FastAPI()
model = tf.keras.models.load_model("models/potato_disease_model.h5")
CLASS_NAMES = ["Early Blight", "Late Blight", "Healthy"]

@app.post("/predict")
async def predict(file: UploadFile = File(...)):
    image = read_file_as_image(await file.read())
    image_batch = np.expand_dims(image, 0)
    predictions = model.predict(image_batch)
    predicted_class = CLASS_NAMES[np.argmax(predictions[0])]
    confidence = np.max(predictions[0])
    return {
        "class": predicted_class,
        "confidence": float(confidence)
    }
```

### Frontend (ReactJS)

- **Component Structure**: Modular design with reusable components
- **State Management**: React Context API for application state
- **UI Framework**: Material-UI for responsive design
- **Image Handling**: Client-side image preprocessing

### Mobile App (React Native)

- **TensorFlow Lite Integration**: On-device inference
- **Camera Access**: Native camera integration
- **Offline Capability**: Functional without internet connection
- **Cross-Platform**: Works on both iOS and Android

## 🔧 Deployment

### Cloud Deployment (GCP)
- **Container Registry**: Docker images stored in GCR
- **Cloud Run**: Serverless deployment of FastAPI backend
- **Storage Buckets**: Static asset hosting
- **CI/CD Pipeline**: Automated testing and deployment

### Docker Configuration

```dockerfile
# Backend Dockerfile
FROM python:3.9-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY ./app ./app
COPY ./models ./models

CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8080"]
```

## 📊 Performance Metrics

| Metric | Value |
|--------|-------|
| Model Accuracy | 99.2% |
| Inference Time (API) | ~200ms |
| Inference Time (Mobile) | ~350ms |
| API Response Time | <500ms |
| Mobile App Size | 25MB |

## 🛠️ Getting Started

### Prerequisites
- Python 3.8+
- Node.js 14+
- Docker

### Setup Instructions

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/potato-disease-classification.git
   cd potato-disease-classification
   ```

2. **Backend Setup**
   ```bash
   cd backend
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   pip install -r requirements.txt
   uvicorn main:app --reload
   ```

3. **Frontend Setup**
   ```bash
   cd frontend
   npm install
   npm start
   ```

4. **Mobile App Setup**
   ```bash
   cd mobile-app
   npm install
   npx react-native run-android  # or run-ios
   ```

5. **Docker Deployment**
   ```bash
   docker-compose up -d
   ```

## 🔮 Future Enhancements

- [ ] Add support for additional crop diseases
- [ ] Implement progressive learning for model improvement
- [ ] Enhance mobile app with augmented reality visualization
- [ ] Add multi-language support for global use
- [ ] Integrate with weather APIs for contextual predictions

## 👥 Contributors

- Garima Tripathi
