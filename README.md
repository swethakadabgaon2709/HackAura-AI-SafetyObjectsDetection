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

## 🧩 Model & Dataset  
- **Model:** YOLOv8 (small/medium versions)  
- **Dataset:** Synthetic images and YOLO annotations from Falcon Editor, covering these safety equipment classes:  
  - OxygenTank, NitrogenTank, FirstAidBox, FireAlarm, SafetySwitchPanel, EmergencyPhone, FireExtinguisher

## 🛠️ How to Run on Google Colab

1. **Dataset Setup**  
   - Download the synthetic dataset as a ZIP file from Falcon's secure link.  
   - Upload the ZIP and related files manually to your Google Drive.  
   - Mount Google Drive within your Colab notebook to access the data seamlessly.

2. **Run Training Notebook**  
   - Open the provided `.ipynb` notebook in Colab.  
   - Paste and execute the cells in sequence.  
   - After uploading and mounting the dataset, **update file paths** inside the notebook as needed.

3. **Update `yolo-params.yaml`**  
   - Modify the dataset path entries in `yolo-params.yaml` within Colab to reflect the mounted Drive paths where the dataset resides.  
   - This step is crucial to ensure YOLOv8 training references the correct dataset location.

4. **Training and Evaluation**  
   - Run the training with YOLOv8 parameter settings from `yolo-params.yaml`.  
   - Evaluation metrics such as mAP, precision, and recall will be generated automatically.

---

## 🔍 Interpreting Inference Graphs

- Training logs and graphs display key model performance indicators over epochs, including loss curves and precision-recall metrics.  
- A decreasing training and validation loss curve indicates the model is learning effectively.  
- The mAP@0.5 metric shows detection accuracy per class; higher values (close to 1.0) reflect better performance.  
- Precision and recall graphs show the model's balance between correctly finding objects and avoiding false detections.  
- These graphs support validation of the model’s robustness and readiness for deployment.

---


## 🏁 Quickstart with Streamlit App (USE CASE)

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

---


<img width="2400" height="1200" alt="results" src="https://github.com/user-attachments/assets/789234b7-010a-437a-82d1-0ae095f95c45" />

![val_batch2_pred](https://github.com/user-attachments/assets/8edf1dcf-2252-49ce-a1a9-5d4713b4804c)
![val_batch1_labels](https://github.com/user-attachments/assets/0ef3f9bb-d30b-487a-9b2a-b1d0f802813b)

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


## 🖼️ Results
| Object           | mAP@0.5 | Precision | Recall |
|------------------|--------:|----------:|-------:|
| OxygenTank       |   0.81  |    0.94   |  0.92  |
| NitrogenTank     |   0.82  |    0.95   |  0.93  |
| ...              |   ...   |    ...    |  ...   |
See `/results/` for all class metrics and annotated images.
