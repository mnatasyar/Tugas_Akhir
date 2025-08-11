# Face Detection And Expression Recognition Of Elementary School Students Using Yolov8 And Resnet50 Models To Measure Interest In Subjects

**Bahasa:** [🇮🇩 Bahasa Indonesia](README.md) | [🇺🇸 English](README_en.md)

<p align="center">
  <img src="https://raw.githubusercontent.com/mnatasyar/mnatasyar/main/DemoAplikasi.gif" alt="Demo" width="700"/>
</p>

This project aims to develop an AI-based system capable of detecting faces and recognizing emotional expressions of elementary school students using **YOLOv8** for face detection and **ResNet50** for expression recognition from uploaded images or videos. The system is designed to assist teachers in evaluating students’ level of interest in the subject being taught.

---

## Table of Contents

- [Main Features](#main-features)
- [Project Structure](#project-structure)
- [Technologies Used](#technologies-used)
- [System Workflow](#system-workflow)
- [Running the Project Locally](#running-the-project-locally)
  - [1. Frontend](#1-frontend)
  - [2. Backend](#2-backend)
- [Final Project Outcome](#final-project-outcome)

---

## Main Features

This system consists of a **frontend** (user interface) and a **backend** (data processing & deep learning models) that are integrated to detect faces and recognize students' expressions.

Key features include:

- **Face Detection:** Utilizes a custom-trained YOLOv8 model optimized for detecting elementary school students' faces.
- **Expression Recognition:** Uses a fine-tuned ResNet50 model to classify expressions into three interest levels: Interested, Neutral, and Not Interested.
- **Input Flexibility:** Accepts both image and video uploads within the same form for detection.
- **API Integration:** Provides FastAPI endpoints to receive frames, process face detection & interest recognition, and send results back to the frontend.
- **Detailed Analysis:** Displays comprehensive results from the analyzed media.
- **Performance Optimization:** Designed with two models to deliver optimal performance on both CPU and GPU.

---

## Project Structure

```
Tugas_Akhir/
├── frontend/
│ ├── public/
│ ├── src/
│ └── ...
├── backend/
│ ├── app/
│ ├── model/
│ ├── output-video/
│ ├── tmp/
│ └── requirements.txt
├── README.md
└── README_en.md
```

## Technologies Used

### Frontend

The frontend is built using **React** with **TailwindCSS** for responsive styling and **Axios** for API communication with the backend.  
It is designed to be simple, intuitive, and accessible to non-technical users, especially teachers.

### Backend

The backend is built with **Python** using **FastAPI** as the main framework and **OpenCV** for image/video processing.  
It receives frames from the frontend, runs **YOLOv8** for face detection and **ResNet50** for expression recognition, and returns detection results to the frontend.

---

## System Workflow

1. User uploads an image or video via the web interface.
2. Frontend sends the file to the backend via API.
3. Backend processes the file:
   - Detects faces using YOLOv8
   - Recognizes expressions using ResNet50
4. Results are sent back to the frontend:
   - Annotated image/video with bounding boxes & labels
   - Interest level statistics

---

## Running the Project Locally

Follow these steps in order to set up and run the project locally from scratch.

### Prerequisites

- Node.js (for frontend via Vite)
- Python 3.10+
- Git

---

### Clone Repository

Run the following command to clone this repository to your local machine:

```
git clone https://github.com/mnatasyar/Tugas_Akhir.git
cd Tugas_Akhir
```

### 1. Frontend

> [!TIP]
> 💡 Want to try it without local installation?
> Use the online version here: [ai.mnatasyar.com](https://ai.mnatasyar.com) > _Note:_ Only the frontend is available online; backend must be run locally.

```
# 1. Navigate to the frontend development directory
cd frontend

# 2. Install all required dependencies
npm install

# 3. Run the frontend server locally
npm run dev
```

The application will be available at:

```
http://localhost:5173
```

### 2. Backend

**Langkah 1: Environment Setup**

Open a new terminal tab in the **Tugas_Akhir** root directory (not inside the frontend folder).

```
# 1. Navigate to the backend directory
cd backend

# [Optional] 2. Create a virtual environment (venv or conda)
# Example with venv
python -m venv venv
venv\Scripts\activate

# 3. Install backend dependencies
pip install -r requirements.txt
```

**Langkah 2: Download Models**

The YOLOv8 and ResNet50 models are **not** included in this repository due to GitHub’s large file restrictions.  
Please download them manually via the links below.

#### 1. **Create the model folder** if it doesn’t exist:

- `backend/model/`

#### 2. **Download files** and place them in the folder:

- **File:** `best.pt`

  - **Download Link:** https://drive.google.com/file/d/1GDi7h0_C4_BqWuBh4gWlS30CahQ7EsZH/view?usp=sharing
  - **Path:** `backend/models/best.pt`

- **File:** `resnet50v2_finetuned_tingkat_ketertarikan.h5`
  - **Download Link:** https://drive.google.com/file/d/1hxz-XOdy39ZvUj33uDoQ5ezn5ruTk_Ca/view?usp=sharing
  - **Path:** `backend/models/resnet50v2_finetuned_tingkat_ketertarikan.h5`

Final structure after placing models:

```
Tugas_Akhir/
└── backend/
    └── model/
        ├── best.pt
        └── resnet50v2_finetuned_tingkat_ketertarikan.h5
```

**Langkah 3: Run Backend Server**

Run the backend server using the command below::

```
# If running from backend folder
uvicorn app.main:app --reload --host 0.0.0.0 --port=8000

# If running from project root folder
uvicorn backend.app.main:app --reload --host 0.0.0.0 --port 8000
```

The backend will be available at:

```
http://localhost:8000
```

> [!NOTE]
> Make sure to adjust the API URL in `frontend/src/lib/constants.js` to match your backend server address.

## Final Project Outcome

This project produces a facial detection and expression recognition system for elementary school students capable of analyzing their level of interest in a subject based on image or video input.

Overall, the system can:

1. Detect student faces from uploaded media using the YOLOv8 model.
2. Classify facial expressions into three interest categories (Interested, Neutral, and Not Interested) using a fine-tuned ResNet50 model.
3. Present the analysis results in the form of visualizations and descriptive information through a simple, intuitive, and user-friendly web interface for non-technical users such as teachers or educational staff.
4. Process input offline/locally for the backend, with a frontend that can be accessed online or locally.