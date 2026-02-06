# IoT Sensor Data System

## 🛠 Tech Stack

![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=node.js&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-005C84?style=for-the-badge&logo=mysql&logoColor=white)
![MQTT](https://img.shields.io/badge/MQTT-660066?style=for-the-badge&logo=eclipse-mosquitto&logoColor=white)
![JavaFX](https://img.shields.io/badge/JavaFX-000000?style=for-the-badge&logo=java&logoColor=white)

## 📌 Introduction
This project is an **IoT system** used to collect, process, store, and visualize sensor data.  
The system integrates **sensors, an MQTT broker, a backend server, a database, and a JavaFX frontend** to enable real-time monitoring and interaction.

---

## 🏗 System Architecture
The system consists of the following main components:

1. **Sensors (Node.js client / hardware devices)**  
   - Collect raw data (e.g., temperature, humidity, motion).  
   - Send data in **JSON** format via the **MQTT protocol** to the broker.

2. **MQTT Broker**  
   - Acts as a message intermediary between sensors and the backend server.  
   - Ensures reliable data transmission using MQTT’s publish/subscribe model.

3. **Backend Server (Spring Boot / Node.js Express)**  
   - Subscribes to data from the MQTT broker.  
   - Processes JSON packets from sensors.  
   - Stores data in the **MySQL database**.  
   - Provides **HTTP REST APIs** for data querying and updates.  
   - Handles user interaction logic.

4. **MySQL Database**  
   - Stores sensor data and related information.  
   - Supports historical and real-time data queries.  

5. **JavaFX Frontend**  
   - Desktop application for users.  
   - Communicates with the backend via **HTTP API**.  
   - Provides a visual interface, dashboard, and real-time interaction features.  

---

## 🔄 Data Flow
1. **Sensor → MQTT Broker**  
   - Sensor publishes JSON data via MQTT.  

2. **MQTT Broker → Backend Server**  
   - Backend subscribes to MQTT topics.  
   - Extracts and processes sensor data.  

3. **Backend Server → MySQL Database**  
   - Stores processed JSON data into MySQL.  

4. **Backend Server ↔ JavaFX Frontend**  
   - Uses **HTTP requests** for user interaction and updates.  
   - JavaFX fetches data and displays it to the user.  

---

## ⚙️ Technologies Used
- **IoT & Messaging**: MQTT, Node.js (sensor simulation)  
- **Backend**: Spring Boot (Java) 
- **Database**: MySQL  
- **Frontend**: JavaFX (desktop app)  
- **Communication**:  
  - MQTT (sensor → broker → backend)  
  - HTTP REST API (backend ↔ frontend, backend ↔ database)

---

## 🚀 Getting Started

### Prerequisites
- Java 17+ (for Spring Boot & JavaFX)  
- Node.js (for sensor simulation / Express backend option)  
- MySQL 8.0+  
- MQTT Broker (e.g., Mosquitto)  

### Installation
1. **Start MQTT Broker**  
   ```bash
   mosquitto -v
   ```

2. **Run MySQL Database**  
   ```bash
   mysql -u root -p
   CREATE DATABASE sensor_data;
   ```

3. **Start Backend Server**  
   - **Spring Boot**:  
     ```bash
     ./mvnw spring-boot:run
     ```
   - **Node.js Express**:  
     ```bash
     npm install
     node server.js
     ```

4. **Run Sensor Simulation**  
   ```bash
   node sensor.js
   ```

5. **Run JavaFX Frontend**  
   - Open in IDE (IntelliJ/Eclipse/NetBeans)  
   - Run `Main.java`  

---

## 📊 Example MQTT JSON Message
```json
{
  "deviceId": "DV-101A-01",
  "classroomId": 1
}
```

---

## 📡 Example REST API (Backend → Frontend)

- **Get all sensor data**
  ```http
  GET /api/devices
  ```

- **Get sensor data by deviceId**
  ```http
  GET /api/devices/{Id}
  ```

- **Fix devices by deviceCode**
  ```http
  PUT /api/devices/{deivceCode}
  ```

---

## 🔒 Security & Authentication
- JWT-based authentication (optional).  
- Role-based access for **Admin / User**.  
