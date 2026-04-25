# HNG Stage 2 DevOps Task

## 📌 Overview
This project is a simple job processing system built with:
- FastAPI (API service)
- Redis (queue)
- Python worker (background processing)

It allows users to submit jobs and processes them asynchronously.

---

## ⚙️ Prerequisites

Make sure you have the following installed:

- Ubuntu / WSL
- Python 3.12+
- pip
- Redis

Install Redis:
sudo apt update
sudo apt install redis-server -y

Start Redis:
sudo service redis-server start

---

## 🚀 Setup Instructions

### 1. Clone the repository
git clone https://github.com/varlov/hng14-stage2-devops.git
cd hng14-stage2-devops

---

### 2. Setup API

cd api
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

Run API:
uvicorn main:app --reload

---

### 3. Setup Worker

Open a new terminal:

cd ~/hng14-stage2-devops/worker
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

Run worker:
python worker.py

---

## 🧪 Testing the system

Open another terminal and run:

curl -X POST http://localhost:8000/jobs

---

## ✅ Expected Output

You should receive a response like:

{"job_id": "some-uuid"}

In the worker terminal, you should see:

Processing job <job_id>
Done: <job_id>

---

## 📂 Environment Variables

See `.env.example` for required environment variables.

---

## 🛠️ Notes

- Redis runs on localhost:6379
- Jobs are stored in Redis queue
- Worker processes jobs asynchronously

---

## 📄 Submission

GitHub Repo:
https://github.com/varlov/hng14-stage2-devops
