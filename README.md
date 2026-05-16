# 🧠 Brain Tumor Segmentation & Diagnosis System

## Sample Output
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PRIMARY DIAGNOSIS: Meningioma
GRADE: Grade II (Moderate)
CONFIDENCE: 96.1%
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
WIDTH: 40 mm | HEIGHT: 42.5 mm | AREA: 1227.5 mm²
SHAPE: Round
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TREATMENT: Surgical Resection (Moderate Urgency)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## Project Structure
Brain_Tumor_Project/
├── app.py
├── train_model_yolo.py
├── requirements.txt
├── models/
│   ├── best.pt
│   └── yolov8n-seg.pt
├── static/
│   ├── style.css
│   └── script.js
├── templates/
│   └── index.html
├── output01.JPG
├── output02.JPG
├── Project Files.JPG
└── Project Structure.JPG

## Quick Start
1. Extract Brain Tumor Project.zip
2. cd Brain_Tumor_Project
3. pip install -r requirements.txt
4. python app.py
5. Open http://127.0.0.1:5000

## Model Path in app.py
MODEL_PATH = "models/best.pt"

## Dependencies
flask==2.3.3
ultralytics==8.0.196
opencv-python==4.8.1.78
numpy==1.24.3
fpdf==1.7.2
torch==2.0.1
torchvision==0.15.2
pillow==10.0.0

## Disclaimer
This is an AI-assisted tool. Do not replace professional medical diagnosis.
