# Flask Hello World Application

This project demonstrates a simple Flask application deployed using Gunicorn.

---

## Project Structure
project/
│── app.py
│── requirements.txt

----

## Prerequisites
- Python 3.8+
- pip

---

## Step 1: Create Virtual Environment
python3 -m venv venv  
source venv/bin/activate

---

## Step 2: Install Dependencies
pip install -r requirements.txt

---

## Step 3: Run Application (Development)
python app.py

Access in browser:  
http://<server-ip>:5000

---

## Step 4: Run Application with Gunicorn (Production)
gunicorn app:app --bind 0.0.0.0:5000

Explanation:  
- app:app → app.py file and Flask app object  
- 0.0.0.0 → allows external access  
- 5000 → application port  

---

## Step 5: Run Gunicorn in Background
nohup gunicorn app:app --bind 0.0.0.0:5000 &

Check process:  
ps -ef | grep gunicorn

---

## Step 6: Open Port (AWS EC2)
Security Group → Inbound Rules  
Custom TCP → Port 5000  
Source → 0.0.0.0/0

---

## Step 7: Test Application
curl http://localhost:5000

Expected Output:  
Hello, World!

---

## Step 8: Stop Application
pkill gunicorn

---

## Notes
- Flask built-in server is for development only  
- Gunicorn is a production WSGI server  
- Nginx can be added as a reverse proxy
