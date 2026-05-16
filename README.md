# 🧠 Brain Tumor Segmentation & Diagnosis System

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![Flask](https://img.shields.io/badge/Flask-2.3.3-green.svg)](https://flask.palletsprojects.com/)
[![YOLOv8](https://img.shields.io/badge/YOLOv8-Segmentation-red.svg)](https://github.com/ultralytics/ultralytics)
[![License](https://img.shields.io/badge/License-Research%20Only-yellow.svg)]()

> An AI-powered web application for brain tumor detection, segmentation, and clinical diagnosis using YOLOv8 segmentation models.

---

## 📌 Table of Contents
- [Overview](#-overview)
- [Key Features](#-key-features)
- [Demo & Output](#-demo--output)
- [Project Structure](#-project-structure)
- [Quick Start](#-quick-start)
- [Model Training](#-model-training)
- [API Endpoints](#-api-endpoints)
- [Clinical Grading System](#-clinical-grading-system)
- [Treatment Protocols](#-treatment-protocols)
- [Troubleshooting](#-troubleshooting)
- [Technical Details](#-technical-details)
- [Disclaimer](#-disclaimer)

---

## 📌 Overview

**NeuroScan Pro** is a comprehensive web-based system that leverages state-of-the-art YOLOv8 segmentation to detect and analyze brain tumors from MRI scans. The system provides radiologist-grade analysis including tumor localization, morphological measurements, clinical grading, and downloadable PDF reports.

### Why This Project?

Brain tumor diagnosis requires precise segmentation and measurement. Traditional methods are time-consuming and subjective. This system provides:
- **Automated segmentation** with pixel-perfect accuracy
- **Quantitative measurements** (area, dimensions, shape analysis)
- **Clinical grading** based on standardized criteria
- **Actionable treatment recommendations**

---

## 🎯 Key Features

| Feature | Description |
|---------|-------------|
| 🎯 **Multi-Class Detection** | Glioma, Meningioma, Pituitary tumor, or No Tumor |
| 🔬 **Pixel-Perfect Segmentation** | Accurate tumor boundary detection using YOLOv8 |
| 📊 **4-Panel Visualization** | Original MRI, Heatmap, Bounding Box, Macro Zoom |
| 📐 **Morphological Metrics** | Width, Height, Area, Shape analysis |
| 🏥 **Clinical Grading** | Automated Grade I-III classification |
| 💊 **Treatment Recommendations** | Drug regimen & urgency assessment |
| 📄 **PDF Report Generation** | Comprehensive radiology reports |
| 🎨 **Modern UI** | Responsive dashboard with real-time analysis |

---

## 📸 Demo & Output

### Diagnostic Dashboard
![Diagnostic Data](WhatsApp%20Image%202026-05-11%20at%205.21.33%20AM.jpeg)

### Clinical Analysis Report
![Clinical Report](WhatsApp%20Image%202026-05-11%20at%205.21.33%20AM%20(1).jpeg)

### Sample Output
# PRIMARY DIAGNOSIS: Meningioma
# GRADE: Grade II (Moderate)
# CONFIDENCE: 96.1%
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
# WIDTH: 40 mm | HEIGHT: 42.5 mm | AREA: 1227.5 mm²
# SHAPE: Round
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
# TREATMENT: Surgical Resection (Moderate Urgency)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## text

---

## 📁 Project Structure
Brain_Tumor_Project/
│
├── app.py # Main Flask application
├── train_model_yolo.py # YOLO training script
├── best.pt # Trained model weights
├── scan_history.json # Scan records
├── requirements.txt # Dependencies
│
├── brain_tumor_seg/ # Training output
│ └── yolov8_cpu/
│ └── weights/
│ └── best.pt
│
├── static/ # Static assets
│ ├── style.css
│ └── script.js
│
├── templates/ # HTML templates
│ └── index.html
│
└── temp_*.jpg # Temporary visualizations

## text

---

## 🚀 Quick Start

### Prerequisites
- Python 3.8 or higher
- pip package manager
- 4GB+ RAM (8GB recommended)

### Installation

**1. Clone the repository**
```bash
git clone https://github.com/yourusername/brain-tumor-segmentation.git
cd brain-tumor-segmentation
