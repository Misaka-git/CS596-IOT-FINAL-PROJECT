Luming Qi CS596 IOT

Youtube website
https://www.youtube.com/watch?v=rOfBI49xPAM
# 🧪 Air Quality Monitoring Dashboard

A real-time environmental monitoring system using an ESP32, sensors (DHT22, SDS011, SGP30), a Flask server, and a web dashboard. This project collects and visualizes temperature, humidity, CO₂, TVOC, PM2.5, and PM10 data. It also sends email alerts when pollutant levels are too high.

---

## 🌐 Features

- 📡 ESP32 sends environmental data to Flask server via HTTP POST  
- 📈 Real-time web dashboard at `/` with an exponential-scaled chart  
- 🔔 Automatic **email alerts** (via Gmail) for high sensor readings  
- 🕒 `/latest` endpoint returns most recent data in JSON  
- 📊 Data chart uses Chart.js with log scale for sensor values  

---

## 🔧 Hardware Setup

- **ESP32 board** (e.g., LilyGO T-Display S3)  
- **Sensors:**  
  - DHT22 for temperature/humidity  
  - SGP30 for eCO₂ and TVOC  
  - SDS011 for PM2.5 and PM10  
  SGP30 :
  SCL--GPIO-43
  SDA--GPIO-44

  DHT22 :
  OUT--GPIO-1

  LED :
  GPIO-21

---

## 🛠️ Installation

### 1. Clone the repo
```bash
git clone https://github.com/yourusername/air-quality-dashboard.git
cd air-quality-dashboard
```

### 2. Create a virtual environment
```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install dependencies
```bash
pip install flask
```

---

## 📁 Project Structure

```
.
├── server.py          # Flask server
├── templates/
│   └── index.html     # Web dashboard
└── static/
    └── chart.js       # Charting library (optional if CDN used)
```

---

## ✉️ Email Alert Configuration

1. Use a Gmail account.  
2. Enable [App Passwords](https://myaccount.google.com/apppasswords) and generate a 16-character password.  
3. In `server.py`, replace:

```python
EMAIL_ADDRESS = 'your_email@gmail.com'
EMAIL_PASSWORD = 'your_app_password'
TO_EMAIL = 'recipient_email@gmail.com'
```

**Note:** Do **not** use your main Gmail password. Use the App Password feature.

---

## 🚀 Running the Flask Server

```bash
python server.py
```

- Open browser at: `http://<your-ip>:5000/`  
- Post data to: `http://<your-ip>:5000/data`  
- View latest value at: `http://<your-ip>:5000/latest`  

---

## 🧪 Sample JSON Payload

```json
{
  "temp": 26.5,
  "humidity": 44.0,
  "pm25": 12,
  "pm10": 15,
  "eco2": 450,
  "tvoc": 25
}
```

---

## ⚠️ Alert Thresholds

Alerts are triggered if:

- PM2.5 > 100 µg/m³  
- eCO₂ > 1000 ppm  
- TVOC > 200 ppb  

---

## 🖥️ Dashboard Preview

_Include a screenshot here if needed._

---

## ✅ To Do

- Store historical data to a database  
- Add login & authentication  
- Deploy with gunicorn + nginx for production  

---

## 📄 License

MIT License
