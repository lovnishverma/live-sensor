
# 🌡️ Live DHT11 Sensor Data Dashboard

This project demonstrates how to read temperature and humidity from a **DHT11 sensor** using an **ESP8266** microcontroller, upload the data to **Firebase Realtime Database**, and display it in real-time on a web interface hosted via **GitHub Pages**.

---

## 📌 Features

- 🚀 ESP8266 reads live temperature & humidity data
- ☁️ Sends sensor readings to Firebase over HTTPS
- 🌐 GitHub Pages displays data live using JavaScript
- 🔄 Auto-updating interface every 5 seconds
- 🧑‍🔧 Lightweight and beginner-friendly IoT stack

---

## 🛠️ Components Used

| Component         | Description                        |
|------------------|------------------------------------|
| ESP8266           | NodeMCU / Wemos D1 mini, etc.      |
| DHT11 Sensor      | Temp + Humidity sensor (3 or 4 pin)|
| Firebase          | Realtime Database (cloud backend)  |
| GitHub Pages      | Hosting frontend (HTML/JS)         |

---

## 🔌 Circuit Diagram

| DHT11 Pin | ESP8266 NodeMCU Pin |
|-----------|---------------------|
| VCC       | 3.3V                |
| DATA      | D4 (GPIO2)          |
| GND       | G                   |

> For raw DHT11 modules: Add a 10KΩ pull-up resistor between `VCC` and `DATA`.

---

## 🔧 Firebase Setup

1. Go to [https://console.firebase.google.com](https://console.firebase.google.com)
2. Click **"Add project"** → Give it a name (e.g., `live-sensor`)
3. Go to **Build → Realtime Database → Create Database**
4. Start in **Test Mode** ✅
5. Note your database URL (e.g., `https://your-project-id.firebaseio.com/`)
6. Go to **Rules** and replace with:

```json
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
````

---

## 📟 ESP8266 Arduino Code

Install libraries:

* `ESP8266WiFi`
* `ESP8266HTTPClient`
* `WiFiClientSecure`
* `DHT sensor library`

Use this structure:

```cpp
const char* ssid = "your_wifi_name";
const char* password = "your_wifi_password";
const char* firebaseHost = "https://your-project-id.firebaseio.com/sensordata.json";
```

> For full code, see [`esp8266_dht11_firebase.ino`](esp8266_dht11_firebase.ino)

---

## 🌐 GitHub Pages Frontend

HTML page fetches sensor data from Firebase and displays it live.

📁 `index.html` key features:

* Auto-updates every 5 seconds
* Fetches JSON from Firebase
* Displays sensor ID, sample name, temperature, and humidity

Host this HTML on any static web server or [GitHub Pages](https://pages.github.com/).

---

## 🔄 Live Update Logic

Uses JavaScript `fetch()` to retrieve Firebase JSON:

```js
const url = "https://your-project-id.firebaseio.com/sensordata.json";

async function updateData() {
  const res = await fetch(url);
  const data = await res.json();
  // update DOM
}
setInterval(updateData, 5000);
```

---

## 📦 Folder Structure

```
live-sensor-project/
├── index.html                # GitHub Pages frontend
├── esp8266_dht11_firebase.ino # ESP8266 Arduino sketch
└── README.md                 # You're here!
```

---

## 🚧 Limitations

* Firebase Realtime DB in test mode is insecure (use rules in production)
* DHT11 is low-precision (consider DHT22 or BME280)
* Page refresh not required, JavaScript auto-updates via fetch()

---

## ✅ Future Improvements

* Store historical data and chart using Chart.js
* Add timestamps to logs
* Secure Firebase access with authentication
* Push alerts for abnormal sensor readings

---

## 📸 Demo Preview

![Live Sensor Dashboard](https://user-images.githubusercontent.com/demo/dashboard-preview.gif)

---

## 💬 Contributing

Pull requests welcome! Feel free to fork and improve the dashboard or ESP code.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

## 🙌 Acknowledgments

* [Firebase Realtime Database](https://firebase.google.com/)
* [ESP8266 Arduino Core](https://github.com/esp8266/Arduino)
* [DHT Sensor Library](https://github.com/adafruit/DHT-sensor-library)

```

---

## 📝 To Use:

- Save this content as `README.md`
- Put it in the root of your GitHub repository
- Push the file to GitHub to show the README on your project page


