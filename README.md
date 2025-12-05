📸 Image Caption Generator — End-to-End ML + FastAPI + React Application

An end-to-end Image Caption Generation System built entirely from scratch without using any pretrained models.
This project combines Machine Learning, Deep Learning, FastAPI, PostgreSQL, and a modern React frontend to generate natural-language captions for images.

The primary goal of this project is to understand and design a complete ML workflow — from dataset preparation to model training to a full-stack deployment-ready system.

🚀 Tech Stack Overview
🔧 Frontend

React (Vite)

Tailwind CSS

Axios

JWT handling & protected routes

⚙️ Backend

FastAPI

PostgreSQL + SQLAlchemy ORM

JWT Authentication

Uvicorn server

Pydantic validation

🧠 Machine Learning

Custom CNN (trained from scratch)

LSTM-based caption generator

Custom tokenizer + vocabulary

Trained locally on Flickr30k dataset

📂 Project Structure
.
├── frontend/                    # React Application
├── backend/
│   ├── app/
│   │   ├── routes/
│   │   ├── database/
│   │   ├── auth/
│   │   ├── utils/
│   ├── models/                 # ML model files (ignored in Git)
│   ├── main.py
│   └── requirements.txt
├── README.md
└── .gitignore

🧠 Machine Learning Workflow

This project uses two deep learning models, trained completely from scratch:

1️⃣ Custom CNN Feature Extractor

Built and trained without pretrained weights.

Extracts visual features from images.

Generates dense feature vectors used by the caption generator.

2️⃣ LSTM Caption Generator

Trained using cleaned captions from Flickr30k.

Embedding → LSTM → Dense softmax output.

Generates captions word-by-word.

Training Pipeline Summary

Clean & normalize captions

Build vocabulary

Create token sequences

Train CNN

Train LSTM Caption model

Save:

feature_extractor.keras

model.keras

tokenizer.pkl

These files are placed in:

backend/models/


(ignored from Git)

⚙️ Backend Setup (FastAPI)
1️⃣ Install Dependencies
pip install -r backend/requirements.txt

2️⃣ Configure .env

Create backend/.env:

DATABASE_URL=postgresql://user:password@localhost:5432/caption_db
JWT_SECRET=your_secret_key

3️⃣ Add Model Files

Place the following inside backend/models/:

feature_extractor.keras

model.keras

tokenizer.pkl

4️⃣ Run the Backend
uvicorn app.main:app --reload


Backend will be available at:

http://localhost:8000

📡 API Endpoints
🔐 Authentication
Method	Endpoint	Description
POST	/auth/signup	Register a new user
POST	/auth/login	Login and receive JWT token
🖼️ Caption Generation
Method	Endpoint	Description
POST	/caption/upload	Upload an image and generate caption

Input:
multipart/form-data → image

📜 History Management
Method	Endpoint	Auth	Description
GET	/history/recent	✔	Fetch last 3 generated captions
GET	/history/all?page=1&limit=10	✔	Paginated history for the user
💻 Frontend Setup (React + Vite)
1️⃣ Install Dependencies
cd frontend
npm install

2️⃣ Run the Frontend
npm run dev


Frontend will run on:

http://localhost:5173

🌟 Features
ML

Custom CNN trained from scratch

LSTM caption generator

Vocabulary + tokenizer built manually

Backend

Secure auth using JWT

Image processing + caption inference API

User-specific caption history

Pagination supported

Frontend

Upload image → view caption instantly

Clean and responsive UI

Login/Register system

Dashboard with recent & full history