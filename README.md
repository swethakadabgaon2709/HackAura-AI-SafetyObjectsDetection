# HackAura-AI-SafetyObjectsDetection

## 🚀 Project Overview
This project demonstrates a robust, real-time vision system for detecting essential safety equipment in industrial environments. We leverage synthetic data created with the Falcon digital twin simulator, train a YOLOv8 model, and deploy the solution through an interactive Streamlit web app for instant detection via webcam.

## ❗ Problem Statement
Many industrial and hazardous work environments lack standardized and affordable systems for monitoring the presence and accessibility of critical safety equipment. Our project addresses this gap by providing an automated, flexible, and scalable detection tool that leverages synthetic data and modern deep learning.  

## 📦 Key Features
- Robust object detection model trained on YOLOv8
- Real-time safety equipment detection using user’s webcam
- Interactive Streamlit web application for easy deployment and live monitoring
- Easily extensible for additional safety objects or environments

## ⚙️ Requirements
- Python 3.8+
- Streamlit
- Ultralytics (YOLOv8)
- OpenCV
- Other dependencies listed in [requirements.txt](./requirements.txt)


## 🧩 Model Architecture & Dataset
- **Model:** YOLOv8 (small/medium)
- **Dataset:** Synthetic images & YOLO-format annotations created in Falcon Editor, featuring seven safety objects:
  - OxygenTank
  - NitrogenTank
  - FirstAidBox
  - FireAlarm
  - SafetySwitchPanel
  - EmergencyPhone
  - FireExtinguisher

**Download the synthetic dataset directly from Falcon:**  
[https://falcon.duality.ai/secure/documentation/7-class-hackathon&utm_source=hackathon&utm_medium=instructions&utm_campaign=hackaura](https://falcon.duality.ai/secure/documentation/7-class-hackathon&utm_source=hackathon&utm_medium=instructions&utm_campaign=hackaura)


---


## 🛠️ Step-by-Step Instructions to Run and Test the Model

### 🏁 Quickstart

1. **Clone the Repository**
    ```
    git clone https://github.com/nidhi-ii24/hackaura-yolo-app.git
    cd hackaura-yolo-app
    ```

2. **Install Dependencies**
    ```
    pip install -r requirements.txt
    pip install streamlit ultralytics
    ```

3. **Download Model Weights**
   - Place your trained `final.pt` (or `best.pt`) into the project root (same folder as `streamlit_app.py`).

4. **Run the Streamlit Webcam App**
    ```
    streamlit run streamlit_local.py
    ```
    - The app will open in your browser.  
    - Click "Start Webcam" to see live detection (bounding boxes & confidence scores).

5. **Training the Model (Optional)**
   - To retrain, update your dataset paths/config in `yolo_params.yaml`.
   - Run:
    ```
    python train.py
    ```
---


<img width="2400" height="1200" alt="results" src="https://github.com/user-attachments/assets/789234b7-010a-437a-82d1-0ae095f95c45" />
![train_batch2](https://github.com/user-attachments/assets/74457ff5-7422-4781-bd05-54eab250f79c)
![train_batch555](https://github.com/user-attachments/assets/49d8ff57-b421-45a0-9e6f-cf22014c8a4c)
![train_batch556](https://github.com/user-attachments/assets/87a7c5f6-2bc5-42c2-85e0-0e9ff6ad3fba)
![val_batch2_pred](https://github.com/user-attachments/assets/0dad5ac4-7504-411e-95e7-1832cf8d05a9)
![val_batch1_pred](https://github.com/user-attachments/assets/3b27f257-1a60-4a99-85b3-666fd041f947)






## 🖼️ Notes on Expected Outputs & Their Interpretation

- **Interface:** Webcam video stream overlays colored boxes and class labels (with confidence scores) for each safety object detected.
- **Classes:** OxygenTank, NitrogenTank, FirstAidBox, FireAlarm, SafetySwitchPanel, EmergencyPhone, FireExtinguisher.
- **High-confidence detections:** Only objects passing confidence threshold (default 0.5) are shown for robust safety monitoring.
- **Sample Image:** See results folder for annotated examples and accuracy screens.
- **Output Meaning:** Bounding boxes correspond to real-world object locations. Confidence score indicates prediction certainty. Consistent results across lighting, occlusions, and backgrounds demonstrate project robustness.

---

## ❓ Troubleshooting

- **No webcam detected?** Restart app, ensure permissions, disconnect from other software (e.g., Zoom).
- **Streamlit error?** Upgrade/reinstall with `pip install --upgrade streamlit`.
- **Model not loading?** Check `best.pt` path and dependency versions. Verify torch installation for GPU support.

---

## 🔄 Reproducing Final Results

- Download or generate the synthetic dataset using Falcon, as described in `data/README.md`.
- Use `train.py` with `yolo_params.yaml` to retrain or fine-tune the YOLOv8 model.
- Place `best.pt` in the project directory.

---


## 🖼️ Results
| Object           | mAP@0.5 | Precision | Recall |
|------------------|--------:|----------:|-------:|
| OxygenTank       |   0.81  |    0.94   |  0.92  |
| NitrogenTank     |   0.82  |    0.95   |  0.93  |
| ...              |   ...   |    ...    |  ...   |
See `/results/` for all class metrics and annotated images.
