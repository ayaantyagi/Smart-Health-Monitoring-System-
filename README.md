# 🩺 Smart Health Monitoring System  

## 📌 Overview  
The **Smart Health Monitoring System** is an IoT-based application that continuously monitors vital health parameters such as **heart rate, body temperature, and oxygen levels (SpO2)**. The system uses sensors to collect data and displays it in a **real-time web dashboard** for patients and doctors to track.  

---

## 🎯 Features  
- ❤️ Real-time Heart Rate Monitoring  
- 🌡️ Body Temperature Tracking  
- 🌬️ SpO2 (Oxygen Level) Measurement  
- 📊 Live Dashboard with Graphs & Charts  
- 🔔 Alerts for Abnormal Readings  
- ☁️ Data Storage for Historical Analysis  

---

## 🛠️ Tech Stack  
- **Hardware:** Arduino / Raspberry Pi, Sensors (Pulse, Temperature, SpO2)  
- **Backend:** Python (Flask/Django)  
- **Frontend:** HTML, CSS, JavaScript, Bootstrap  
- **Database:** Firebase / MySQL  
- **APIs/Tools:** Chart.js, OpenCV (if face detection used)  
- **Version Control:** Git, GitHub  

---

## 📂 Folder Structure  
```bash
Smart-Health-Monitoring/
│── static/              # CSS, JS, Images
│── templates/           # HTML Templates
│── sensors/             # Sensor Data Scripts
│── app.py               # Main Backend (Flask/Django)
│── requirements.txt     # Dependencies
│── README.md            # Project Documentation
Smart-Health-Monitoring-System/
│── app.py
│── requirements.txt
│── .gitignore
│── LICENSE
│── README.md
│── static/
│   └── style.css
│── templates/
│   └── index.html
│── docs/
│   ├── dashboard.png
│   └── live-monitor.png
from flask import Flask, render_template
import random

app = Flask(__name__)

@app.route("/")
def home():
    health_data = {
        "heart_rate": random.randint(60, 100),
        "temperature": round(random.uniform(36.5, 37.5), 1),
        "spo2": random.randint(92, 100)
    }
    return render_template("index.html", data=health_data)

if __name__ == "__main__":
    app.run(debug=True)
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Smart Health Monitoring</title>
    <link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
</head>
<body>
    <div class="container">
        <h1>🩺 Smart Health Monitoring Dashboard</h1>
        <div class="card">
            <p>❤️ Heart Rate: <strong>{{ data.heart_rate }} bpm</strong></p>
            <p>🌡️ Temperature: <strong>{{ data.temperature }} °C</strong></p>
            <p>🌬️ SpO2: <strong>{{ data.spo2 }} %</strong></p>
        </div>
    </div>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    background: #f5f7fa;
    margin: 0;
    padding: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}

.container {
    text-align: center;
}

h1 {
    color: #2c3e50;
    margin-bottom: 20px;
}

.card {
    background: white;
    padding: 20px;
    border-radius: 12px;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    display: inline-block;
}
flask
venv/
__pycache__/
*.pyc
*.pyo
*.pyd
*.db
*.sqlite3
.env
.DS_Store
MIT License

Copyright (c) 2025 Ayan Tyagi

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND.
python -m venv venv
source venv/bin/activate    # Mac/Linux
venv\Scripts\activate       # Windows
pip install -r requirements.txt
python app.py

