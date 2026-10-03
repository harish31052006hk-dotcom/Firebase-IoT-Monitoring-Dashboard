# Firebase IoT Monitoring Dashboard

### Task 4 — Firebase Realtime Web Dashboard

> A full-stack, secure cloud dashboard built with Firebase Authentication, Realtime Database, and Hosting to monitor and control an IoT environment system.

---

## 📌 Overview
This task shifts focus to the cloud layer, developing a secure web application to interface with IoT hardware. It replaces the third-party Adafruit IO dashboard with a fully customized, login-protected Firebase web application that displays real-time telemetry, historical logs, and provides manual/auto control toggles.

## 🎯 Objectives
- Create a Firebase cloud project and configure Authentication.
- Design a JSON-tree structure for a Realtime Database.
- Develop a frontend HTML/CSS/JS dashboard.
- Implement real-time listeners for telemetry (Temperature, Humidity, LDR).
- Secure the database using Firebase Rules.
- Deploy the web application via Firebase Hosting.

## 🧠 Concepts Covered
- Backend-as-a-Service (BaaS)
- NoSQL Realtime Databases
- User Authentication & Security Rules
- WebSockets and Real-time Data Binding
- Static Web Hosting

## 🏗️ System Architecture
1. **Frontend**: HTML/CSS/JS dashboard hosted on Firebase Hosting.
2. **Authentication**: Firebase Auth ensures only registered users can view or modify data.
3. **Database**: Firebase Realtime Database synchronizes `sensors/`, `control/`, and `status/` nodes across all connected clients.
4. *(Hardware integration is covered in Task 5)*.

## 🔧 Hardware
- This task focuses purely on the cloud architecture and frontend dashboard development.

## 💻 Software
- HTML, CSS, JavaScript (Vanilla)
- Firebase Web SDK (v9 Modular)
- Node.js & Firebase CLI (for deployment)

## ⚙️ Implementation
- **Database Structure**: Divided into `sensors` (live telemetry), `control` (actuator states and auto/manual modes), `logs` (historical array), and `status` (device connectivity).
- **Dashboard**: Features dynamic DOM updates. When Firebase pushes new data, event listeners immediately update the UI cards.
- **Controls**: Buttons push JSON updates to the `control` node (e.g., `mode: "AUTO"`, `bulb: "ON"`).
- **Security**: Applied `.read` and `.write` rules restricted to `auth != null`.

## 🧪 Testing
- Verified user login and rejection of invalid credentials.
- Simulated hardware by manually editing the Firebase console and watching the web dashboard update instantly.
- Verified that clicking "Turn Bulb ON" on the dashboard updated the database in real-time.
- Successfully downloaded historical logs via the CSV export button.

## 🛠️ Challenges & Fixes
- **Async Data Loading**: The dashboard occasionally rendered before Firebase data arrived. Added loading spinners and placeholder text (`--`) until the initial data snapshot was received.
- **Firebase V9 Syntax**: Transitioning to the modular SDK required adjusting imports (e.g., `onValue`, `ref`) compared to older Firebase documentation.

## 📚 Learning Outcomes
- Mastered the integration of Firebase services into a custom frontend.
- Understood NoSQL data structuring for IoT applications.
- Learned how to secure cloud databases against unauthorized access.

## 💭 Reflection
Building a custom dashboard from scratch provides far more flexibility and professional polish than using constrained third-party dashboards. It provides a highly scalable foundation for enterprise IoT applications.

## 🔗 Project Information
- **Live Login**: [https://env-monitor-845af.web.app/index.html](https://env-monitor-845af.web.app/index.html)
- **Live Dashboard**: [https://env-monitor-845af.web.app/dashboard.html](https://env-monitor-845af.web.app/dashboard.html)
- **Developer**: Harish Kumaran
- **Course**: ProtoSem

## 🏁 Conclusion
The Firebase dashboard was successfully developed, secured, and deployed. It is now ready to receive live telemetry from the physical ESP32 sensor node deployed in Task 5.
