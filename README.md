# 🧠 NeuroScan Pro — Brain Tumor Segmentation & Diagnosis System

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![Flask](https://img.shields.io/badge/Flask-2.3.3-green.svg)](https://flask.palletsprojects.com/)
[![YOLOv8](https://img.shields.io/badge/YOLOv8-Segmentation-red.svg)](https://github.com/ultralytics/ultralytics)
[![License](https://img.shields.io/badge/License-Research%20Only-yellow.svg)]()
[![Status](https://img.shields.io/badge/Status-Active-brightgreen.svg)]()

> An AI-powered web application for brain tumor detection, segmentation, and clinical diagnosis using YOLOv8 segmentation models trained on MRI scan data.

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Key Features](#-key-features)
- [Demo & Output](#-demo--output)
- [Project Structure](#-project-structure)
- [Quick Start](#-quick-start)
- [Installation](#-installation)
- [Model Setup](#-model-setup)
- [Running the App](#-running-the-app)
- [API Endpoints](#-api-endpoints)
- [Clinical Grading System](#-clinical-grading-system)
- [Treatment Protocols](#-treatment-protocols)
- [Troubleshooting](#-troubleshooting)
- [Technical Details](#-technical-details)
- [Disclaimer](#%EF%B8%8F-disclaimer)

---

## 📋 Overview

**NeuroScan Pro** is a comprehensive web-based system that leverages state-of-the-art YOLOv8 segmentation to detect and analyze brain tumors from MRI scans. The system provides radiologist-grade analysis including tumor localization, morphological measurements, clinical grading, and downloadable PDF reports.

### Why This Project?

Brain tumor diagnosis requires precise segmentation and measurement. Traditional methods are time-consuming and subjective. This system provides:

- **Automated segmentation** with pixel-accurate tumor boundary detection
- **Quantitative measurements** (area, dimensions, shape analysis)
- **Clinical grading** based on standardized WHO criteria
- **Actionable treatment recommendations** tailored by tumor class and grade
- **Downloadable PDF reports** suitable for clinical review

---

## 🎯 Key Features

| Feature | Description |
|---|---|
| 🎯 **Multi-Class Detection** | Glioma, Meningioma, Pituitary tumor, or No Tumor |
| 🔬 **Pixel-Perfect Segmentation** | Accurate tumor boundary detection using YOLOv8-seg |
| 📊 **4-Panel Visualization** | Original MRI · Heatmap · Bounding Box · Macro Zoom |
| 📐 **Morphological Metrics** | Width, Height, Area, Circularity, Aspect Ratio |
| 🏥 **Clinical Grading** | Automated WHO Grade I–III classification |
| 💊 **Treatment Recommendations** | Drug regimen & urgency assessment per tumor type |
| 📄 **PDF Report Generation** | Comprehensive downloadable radiology reports |
| 🎨 **Modern Web UI** | Responsive Flask dashboard with real-time analysis |

---

## 📸 Demo & Output

### Project Files & Directory
![Project Files](docs/images/Project%20Files.JPG)

### Project Structure Overview
![Project Structure](docs/images/Project%20Structure.JPG)

### Output Sample — Segmentation & Heatmap
![Output 01](docs/images/output01.JPG)

### Output Sample — Clinical Report
![Output 02](docs/images/output02.JPG)

> **Note:** Place all screenshot images inside the `docs/images/` folder. If you keep them in the root directory, update the paths above to `![Project Files](Project%20Files.JPG)` (with `%20` for spaces, or rename files to remove spaces).

---

## 📁 Project Structure

```
Brain-Tumor-Project/
│
├── app.py                      # Main Flask application entry point
├── requirements.txt            # Python dependencies
├── README.md                   # Project documentation
│
├── models/                     # YOLOv8 model weights (stored outside zip)
│   ├── best.pt                 # Custom-trained brain tumor segmentation model
│   └── yolov8n-seg.pt          # YOLOv8 nano segmentation base model
│
├── static/
│   ├── css/
│   │   └── style.css           # Dashboard stylesheet
│   ├── js/
│   │   └── main.js             # Frontend interaction logic
│   └── uploads/                # Temporary uploaded MRI images
│
├── templates/
│   └── index.html              # Main web UI template
│
├── utils/
│   ├── inference.py            # YOLOv8 inference & segmentation logic
│   ├── visualization.py        # 4-panel image generation
│   ├── grading.py              # Clinical grade & treatment logic
│   └── report.py               # PDF report generator
│
└── docs/
    └── images/                 # Screenshots for README
        ├── Project Files.JPG
        ├── Project Structure.JPG
        ├── output01.JPG
        └── output02.JPG
```

---

## ⚡ Quick Start

```bash
# 1. Clone the repository
git clone https://github.com/your-username/brain-tumor-project.git
cd brain-tumor-project

# 2. Create and activate a virtual environment
python -m venv venv
# Windows:
venv\Scripts\activate
# macOS / Linux:
source venv/bin/activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Place model files
mkdir -p models
# Copy best.pt and yolov8n-seg.pt into the models/ folder

# 5. Run the application
python app.py
```

Then open your browser at **http://127.0.0.1:5000**

---

## 🔧 Installation

### Prerequisites

| Requirement | Version |
|---|---|
| Python | 3.8 or higher |
| pip | Latest |
| Git | Any recent version |
| CUDA (optional) | 11.8+ for GPU acceleration |

### Step-by-Step

**1. Clone the repository**
```bash
git clone https://github.com/your-username/brain-tumor-project.git
cd brain-tumor-project
```

**2. Create a virtual environment** *(strongly recommended)*
```bash
python -m venv venv
```

Activate it:
- **Windows:** `venv\Scripts\activate`
- **macOS/Linux:** `source venv/bin/activate`

**3. Install Python dependencies**
```bash
pip install -r requirements.txt
```

`requirements.txt` should include:
```
flask==2.3.3
ultralytics>=8.0.0
opencv-python>=4.7.0
numpy>=1.24.0
Pillow>=9.5.0
reportlab>=4.0.0
torch>=2.0.0
torchvision>=0.15.0
```

---

## 🤖 Model Setup

The model weights are **not included** in the ZIP archive. Place them manually:

```
brain-tumor-project/
└── models/
    ├── best.pt           ← Your custom-trained model
    └── yolov8n-seg.pt    ← YOLOv8 nano segmentation base model
```

### Downloading the Base Model

```bash
# Automatically downloads on first run, or manually:
from ultralytics import YOLO
model = YOLO("yolov8n-seg.pt")  # downloads from Ultralytics if not found
```

### Model Path Configuration

In `app.py` or `utils/inference.py`, ensure the model path is set correctly:

```python
import os

BASE_DIR = os.path.dirname(os.path.abspath(__file__))
MODEL_PATH = os.path.join(BASE_DIR, "models", "best.pt")

model = YOLO(MODEL_PATH)
```

> ⚠️ **Common Issue:** Using relative paths like `"best.pt"` or `"../best.pt"` will cause `FileNotFoundError` if the script is run from a different directory. Always use `os.path.join` with `os.path.abspath(__file__)` as shown above.

---

## 🚀 Running the App

```bash
# Development server (default: http://127.0.0.1:5000)
python app.py

# With debug mode enabled
FLASK_DEBUG=1 python app.py

# On a specific host/port
python app.py --host 0.0.0.0 --port 8080
```

### Upload & Analyze

1. Open `http://127.0.0.1:5000` in your browser
2. Click **Upload MRI Scan** and select a `.jpg` / `.png` image
3. Click **Analyze**
4. View the 4-panel result and clinical report
5. Download the PDF report

---

## 🌐 API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/` | Main web dashboard |
| `POST` | `/predict` | Upload MRI and run inference |
| `GET` | `/report/<filename>` | Download PDF report |
| `GET` | `/result/<filename>` | View saved result image |
| `GET` | `/health` | API health check |

### Example — `/predict` Request

```bash
curl -X POST http://127.0.0.1:5000/predict \
  -F "file=@/path/to/mri_scan.jpg"
```

### Example — `/predict` Response

```json
{
  "status": "success",
  "tumor_class": "Glioma",
  "confidence": 0.94,
  "grade": "Grade II",
  "area_cm2": 12.4,
  "width_mm": 38.2,
  "height_mm": 41.7,
  "urgency": "High",
  "result_image": "/result/output_mri_scan.jpg",
  "report_pdf": "/report/report_mri_scan.pdf"
}
```

---

## 🏥 Clinical Grading System

The system follows a simplified WHO grading framework:

| Grade | Criteria | Urgency |
|---|---|---|
| **Grade I** | Small area (< 5 cm²), high circularity, low aspect ratio | Moderate |
| **Grade II** | Medium area (5–15 cm²), moderate shape irregularity | High |
| **Grade III** | Large area (> 15 cm²) or highly irregular morphology | Critical |

### Tumor Classes

| Class | Description |
|---|---|
| `Glioma` | Most common malignant brain tumor; arises from glial cells |
| `Meningioma` | Usually benign; arises from meninges (brain lining) |
| `Pituitary` | Tumor of the pituitary gland; often benign but hormonally active |
| `No Tumor` | No detectable tumor in the MRI scan |

---

## 💊 Treatment Protocols

Treatment recommendations are generated automatically based on tumor class and grade:

### Glioma
- **Grade I:** Surgical resection + observation
- **Grade II:** Temozolomide (TMZ) chemotherapy + radiation
- **Grade III:** Aggressive TMZ + bevacizumab + radiation

### Meningioma
- **Grade I:** Surgical resection; gamma knife radiosurgery if inoperable
- **Grade II:** Resection + fractionated radiotherapy
- **Grade III:** Gross total resection + adjuvant radiation

### Pituitary Tumor
- Dopamine agonists (bromocriptine / cabergoline) for prolactinomas
- Transsphenoidal surgery for non-functioning adenomas
- Radiation for residual/recurrent disease

> ⚠️ These protocols are for **educational/research purposes only**. All clinical decisions must be made by qualified medical professionals.

---

## 🔍 Troubleshooting

### `FileNotFoundError: best.pt not found`
- Ensure `best.pt` is placed inside the `models/` folder
- Use absolute paths in your code (see [Model Setup](#-model-setup))

### `ModuleNotFoundError: No module named 'ultralytics'`
```bash
pip install ultralytics
```

### `OSError: [Errno 98] Address already in use`
```bash
# Kill the process using port 5000
# Linux/macOS:
lsof -ti:5000 | xargs kill -9
# Windows:
netstat -ano | findstr :5000
taskkill /PID <PID> /F
```

### Images not displaying in README
- Rename image files to remove spaces (e.g., `Project_Files.JPG`) **or** use `%20` encoding in paths
- Place images inside `docs/images/` and update paths accordingly
- On GitHub, paths are **case-sensitive** — match the filename exactly

### CUDA / GPU not detected
```bash
python -c "import torch; print(torch.cuda.is_available())"
# If False, install the CUDA version of PyTorch:
pip install torch torchvision --index-url https://download.pytorch.org/whl/cu118
```

### Low confidence or wrong predictions
- Ensure input MRI images are axial-view, grayscale or RGB
- Recommended input resolution: **224×224** or **640×640**
- Use `best.pt` (custom-trained), not `yolov8n-seg.pt` (base model)

---

## 🛠 Technical Details

### Model Architecture

| Component | Detail |
|---|---|
| Base Model | YOLOv8n-seg (nano segmentation) |
| Custom Model | `best.pt` — fine-tuned on brain MRI dataset |
| Input Size | 640 × 640 pixels |
| Output | Bounding boxes + polygon segmentation masks |
| Framework | Ultralytics YOLOv8 |

### Visualization Pipeline

1. **Original MRI** — raw input scan
2. **Heatmap** — confidence-weighted activation overlay (Jet colormap)
3. **Bounding Box** — detected tumor region with class label and confidence
4. **Macro Zoom** — cropped and enlarged tumor region for detail

### PDF Report Contents

- Patient scan metadata (filename, timestamp)
- Tumor class & confidence score
- Morphological measurements (area, width, height, circularity)
- Clinical grade assessment
- Recommended treatment protocol
- Annotated result image (embedded)

---

## 📦 Model Training (Optional)

If you wish to retrain the segmentation model on your own dataset:

```bash
from ultralytics import YOLO

model = YOLO("yolov8n-seg.pt")  # Load base model

model.train(
    data="brain_tumor.yaml",   # Dataset config file
    epochs=100,
    imgsz=640,
    batch=16,
    name="brain_tumor_seg",
    device=0                   # GPU index (use "cpu" for CPU training)
)
```

Dataset YAML format (`brain_tumor.yaml`):
```yaml
path: ./datasets/brain_tumor
train: images/train
val: images/val
test: images/test

nc: 4
names: ["glioma", "meningioma", "pituitary", "notumor"]
```

---

## ⚠️ Disclaimer

> **This system is intended for research and educational purposes only.**
>
> - It is **not** a certified medical device and must **not** be used for clinical diagnosis.
> - All outputs should be reviewed and validated by qualified radiologists and oncologists.
> - The authors accept no liability for any clinical decisions made based on this tool.
> - Always follow your institution's clinical protocols and ethical guidelines.

---

## 👨‍💻 Author

Engr. Muhammad Yasin Khan


---

## 📄 License

This project is licensed for **research use only**. Commercial use is not permitted without explicit written consent.
