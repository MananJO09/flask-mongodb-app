# Flask + MongoDB on Kubernetes (Minikube)

Author: Manandeep Joshi  
Docker Hub: `mananspace/flask-mongodb-app:v1`

## 1. Overview

This project deploys a Python Flask application connected to a MongoDB database on a local Kubernetes cluster (Minikube). The app exposes:

- `/` → returns “Welcome to the Flask app! The current time is: 2025-11-28 13:12:19.190400”
- `/data`  
  - `POST` → insert JSON into MongoDB  
  - `GET` → return all documents from MongoDB

The deployment includes:

- Flask `Deployment` (2–5 replicas with HPA)
- MongoDB `StatefulSet` with authentication + persistent storage
- ClusterIP `Service` for MongoDB
- NodePort `Service` for Flask
- Resource requests & limits for both apps

---

## 2. Prerequisites

- Python 3.8+ (for local dev)
- Docker Desktop (with Kubernetes / Minikube support)
- Minikube
- kubectl
- Docker Hub account (`mananspace` used here)

---

## 3. Local Setup (Part 1 – Summary)

```bash
# 1. Create project
mkdir flask-mongodb-app
cd flask-mongodb-app

# 2. Virtual environment
python -m venv venv   # or: py -m venv venv
venv\Scripts\activate # on Windows PowerShell

# 3. Install dependencies
pip install -r requirements.txt

# 4. Run locally
python app.py
# App available at http://127.0.0.1:5000
