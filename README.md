# HackAura-AI-SafetyObjectsDetection

## 🚀 Project Overview
This project demonstrates a robust, real-time vision system for detecting essential safety equipment in industrial environments. We leverage synthetic data created with the Falcon digital twin simulator, train a YOLOv8 model, and deploy the solution through an interactive Streamlit web app for instant detection via webcam.

## ❗ Problem Statement
Many industrial and hazardous work environments lack standardized and affordable systems for monitoring the presence and accessibility of critical safety equipment. Our project addresses this gap by providing an automated, flexible, and scalable detection tool that leverages synthetic data and modern deep learning.  
(See attached `HackAura-Hackathon-Documentation-1.pdf` for full details.)


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
- Other dependencies listed in `requirements.txt`

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
    git clone https://github.com/<yourteam>/<reponame>.git
    cd <reponame>
    ```

2. **Install Dependencies**
    ```
    pip install -r requirements.txt
    pip install streamlit ultralytics
    ```

3. **Download Model Weights**
   - Place the trained `best.pt` file in the project directory or follow instructions in the README on how to acquire it.

4. **Run the Streamlit Webcam App**
    ```
    streamlit run webcam_app.py
    ```
    The application will open in your browser. Click “Start Webcam” to see real-time detection with bounding boxes and confidence scores.

5. **Training the Model (Optional)**
   - For retraining, update `yolo_params.yaml` with your dataset paths.
   - Run:
    ```
    python train.py
    ```

---

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

_For complete methodology, dataset details, mAP scores, and further results, refer to the attached `HackAura-Hackathon-Documentation-1.pdf`._


## 🖼️ Results
| Object           | mAP@0.5 | Precision | Recall |
|------------------|--------:|----------:|-------:|
| OxygenTank       |   0.81  |    0.94   |  0.92  |
| NitrogenTank     |   0.82  |    0.95   |  0.93  |
| ...              |   ...   |    ...    |  ...   |
See `/results/` for all class metrics and annotated images.
