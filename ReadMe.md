# WaterBnB – IoT Pool Rental System

## 📘 Overview
WaterBnB is a cloud-based IoT swimming pool rental system inspired by property-sharing platforms. Users can view, select, and request access to nearby swimming pools monitored by ESP32 devices.  

The system integrates:  
- **ESP32 microcontrollers** for real-time pool monitoring  
- **Node-RED** for flow-based logic and dashboards  
- **Flask (Python)** backend hosted on Render/Railway  
- **MongoDB Atlas** for data persistence  
- **MQTT** for real-time messaging  
- **MongoDB Charts** for analytics and insights  

## ✨ Features
- Real-time pool status monitoring (temperature, availability)  
- Interactive map dashboard built with Node-RED  
- User authentication and pool rental request flow  
- MQTT-based communication between ESP32 devices and cloud  
- Cloud-hosted Flask server for access control and business logic  
- MongoDB for storing user and pool data  
- Analytics dashboard for visualizing pool demand and usage  
- LED strip feedback on ESP32 indicating pool availability (Green/Yellow/Red)  

## 🏗️ System Architecture
**ESP32 Devices:** Publish pool data (temperature, location, status) to MQTT topics and control RGB LED for status.  
**Node-RED Dashboard:** Displays pool locations, handles login, rental requests, and communicates with Flask server.  
**Flask Server (Cloud):** Validates users/pools, sends MQTT commands, and logs transactions to MongoDB.  
**MongoDB Atlas:** Stores user credentials, pool states, rental logs, and powers analytics dashboards.  
**MQTT Broker:** Enables real-time messaging between devices and cloud.  

## 🚀 Setup & Installation
1. **Clone the Repository**  
```bash
git clone https://github.com/DheerajParkash/WaterBnB-IoT-Pool-Rental.git
cd WaterBnB-IoT-Pool-Rental
```

2. **ESP32 Setup**  
- Upload ESP32 code from `/esp/`  
- Configure Wi-Fi and MQTT broker details  
- Connect and test LED strip  

3. **Node-RED Setup**  
- Import `node-red-flow.json`  
- Install required nodes: `node-red-dashboard`, `node-red-contrib-web-worldmap`, `node-red-node-ui-table`  
- Set up MQTT broker connection  

4. **Flask Server Setup**  
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```  
- Set environment variables for MongoDB and MQTT  
- Deploy to Render/Railway  

5. **MongoDB Atlas**  
- Create free cluster and WaterBnB database  
- Add `users` and `logs` collections  
- Whitelist your server IP  

## 📡 Usage
**User Login:** Access Node-RED dashboard with student/client ID.  
**Browse Pools:** View available pools on map and see details.  
**Request Access:** Send access requests via dashboard, Flask validates, ESP32 LED shows status:  
- Green: Available  
- Yellow: Occupied  
- Red: Denied  

**Analytics Dashboard:** MongoDB Charts shows most requested pools, rental frequency, and user activity.  
- [MongoDB Dashboard](https://charts.mongodb.com/charts-project-0-gpmtr/public/dashboards/300b3150-ec7d-4fd4-8528-1c7f95721541)  

## 🔗 Live Links
- GitHub: [WaterBnB Repository](https://github.com/DheerajParkash/WaterBnB-IoT-Pool-Rental)  
- Flask Server (Railway): [WaterBnB Live](https://waterbnbf-master-production.up.railway.app/)  
- Analytics Dashboard: [MongoDB Charts]  (https://charts.mongodb.com/charts-project-0-gpmtr/public/dashboards/300b3150-ec7d-4fd4-8528-1c7f95721541)

## 👥 Contributors
- Dheeraj Parkash  
- Benna  
- Supervised by Gilles Menez – University Nice Côte d’Azur  

## 📌 Notes
- ESP32 subscribes to two MQTT topics: `uca/iot/piscine` (pool data) and a grant topic for access messages.  
- LED feedback may have slight delays due to MQTT messaging.  
- Designed as a learning exercise in IoT, cloud deployment, and full-stack integration.  

## 📄 License
Educational use only – University Nice Côte d’Azur IoT Course Project
