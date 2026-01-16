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

from flask import Flask, render_template_string
import random
import time

app = Flask(__name__)

# ---------------------------
# HTML + CSS directly in one file (using render_template_string)
# ---------------------------

html_code = """
<!DOCTYPE html>
<html lang="en">
<head> 
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Smart Health Monitoring System</title>
    <style> 
        body {
            font-family: Arial, sans-serif;
            background: #f4f6f9;
            margin: 0;
            padding: 0;
            text-align: center;
        }
        h1 {
            background: #007bff;
            color: white;
            padding: 20px;
            margin: 0;
        }
        .card {
            background: white;
            border-radius: 12px;
            padding: 20px;
            margin: 20px auto;
            width: 300px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            transition: 0.3s;
        }
        .card:hover {
            transform: scale(1.05);
        }
        .value {
            font-size: 2em;
            margin: 10px 0;
            color: #333;
        }
        .unit {
            font-size: 1.2em;
            color: #666;
        }
        .alert {
            color: red;
            font-weight: bold;
        }  
        .container {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
        }
    </style>
    <script>
        async function fetchData() {
            const response = await fetch('/data');
            const data = await response.json();
            document.getElementById('heart').innerText = data.heart_rate + " bpm";
            document.getElementById('temp').innerText = data.temperature + " °C";
            document.getElementById('spo2').innerText = data.spo2 + " %";

            // Alerts
            document.getElementById('heart_alert').innerText = 
                (data.heart_rate < 60 || data.heart_rate > 100) ? "⚠️ Abnormal Heart Rate!" : "";
            document.getElementById('temp_alert').innerText = 
                (data.temperature < 36 || data.temperature > 38) ? "⚠️ Abnormal Temperature!" : "";
            document.getElementById('spo2_alert').innerText = 
                (data.spo2 < 95) ? "⚠️ Low SpO₂ Level!" : "";
        }
        setInterval(fetchData, 2000);
        window.onload = fetchData;
    </script>
</head>
<body>
    <h1>🩺 Smart Health Monitoring Dashboard</h1>
    <div class="container">
        <div class="card">
            <h2>❤️ Heart Rate</h2>
            <div id="heart" class="value">--</div>
            <div class="unit">bpm</div>
            <div id="heart_alert" class="alert"></div>
        </div>
        <div class="card">
            <h2>🌡️ Temperature</h2>
            <div id="temp" class="value">--</div>
            <div class="unit">°C</div>
            <div id="temp_alert" class="alert"></div>
        </div>
        <div class="card">
            <h2>🌬️ SpO₂</h2>
            <div id="spo2" class="value">--</div>
            <div class="unit">%</div>
            <div id="spo2_alert" class="alert"></div>
        </div>
    </div>
</body>
</html>
"""

# ---------------------------
# Routes
# ---------------------------

@app.route('/')
def home():
    return render_template_string(html_code)

@app.route('/data')
def data():
    # Simulated sensor values (you can replace with actual IoT input later)
    heart_rate = random.randint(55, 110)
    temperature = round(random.uniform(35.5, 38.5), 1)
    spo2 = random.randint(90, 100)

    return {
        "heart_rate": heart_rate,
        "temperature": temperature,
        "spo2": spo2
    }

# ---------------------------
# Run
# ---------------------------

if __name__ == "__main__":
    app.run(debug=True)
