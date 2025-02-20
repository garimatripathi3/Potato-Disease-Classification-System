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






## 👥 Contributors

- Garima Tripathi
