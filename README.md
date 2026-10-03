# Firebase IoT Monitoring Dashboard

### Task 4 — Firebase Realtime Web Dashboard

---

## Task Overview
This task shifts focus to the cloud layer, developing a secure web application to interface with IoT hardware. It replaces constrained third-party dashboards with a fully customized, login-protected Firebase web application that displays real-time telemetry, historical logs, and provides manual/auto control toggles.

## Problem / Purpose
To provide a highly scalable, fully customizable, and secure frontend interface for monitoring and controlling IoT devices, leveraging modern backend-as-a-service technologies.

## Objectives
- Create a Firebase cloud project and configure Authentication.
- Design a JSON-tree structure for a Realtime Database.
- Develop a frontend HTML/CSS/JS dashboard.
- Implement real-time listeners for telemetry (Temp, Hum, LDR).
- Secure the database using Firebase Rules.
- Deploy the web application via Firebase Hosting.

## Concepts Covered
- Backend-as-a-Service (BaaS)
- NoSQL Realtime Databases
- User Authentication & Security Rules
- WebSockets and Real-time Data Binding
- Static Web Hosting

## System Architecture

```text
[ Web Browser ] <---(HTTPS)---> [ Firebase Hosting ]
      |
(Auth & Realtime Sync)
      |
      v
[ Firebase Auth & Realtime Database ]
```

## Data Flow
1. User logs in via Firebase Authentication.
2. Dashboard establishes WebSocket connection to Realtime Database.
3. Live data from `/sensors` updates DOM elements instantly.
4. User clicks a control button, sending JSON payload to `/control`.

## Hardware
- This task focuses purely on the cloud architecture and frontend dashboard development. *(Hardware integration occurs in Task 5)*.

## Software & Technologies
| Technology | Role |
|------------|------|
| HTML/CSS/JS | Frontend UI development |
| Firebase Web SDK v9 | Modular client-side Firebase library |
| Firebase RTDB | NoSQL JSON database |
| Firebase Hosting | Global CDN deployment |

## Configuration & Setup
The project uses placeholder Firebase configuration variables to protect secrets:
```javascript
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  databaseURL: "https://YOUR_PROJECT.firebaseio.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT.appspot.com",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};
```

## Implementation Workflow
- **Database Structure**: Divided into `sensors` (live telemetry), `control` (actuator states), `logs` (historical array), and `status` (device connectivity).
- **Dashboard**: Features dynamic DOM updates. When Firebase pushes new data, event listeners immediately update the UI cards.
- **Controls**: Buttons push JSON updates to the `control` node (e.g., `mode: "AUTO"`, `bulb: "ON"`).

## Source Code Explanation
- `index.html`: Handles Firebase Auth email/password login.
- `dashboard.html`: The main authenticated view. Uses `onValue()` listeners from the Firebase v9 modular SDK to subscribe to database changes. Contains logic to download historical arrays as CSV.

## Testing
- Verified user login and rejection of invalid credentials.
- Simulated hardware by manually editing the Firebase console and watching the web dashboard update instantly.
- Successfully downloaded historical logs via the CSV export button.

## Evidence
- *Note: Dashboard screenshots and structure are fully documented in the ProtoSem weekly report.*

## Challenges & Fixes
- **Async Data Loading**: The dashboard occasionally rendered before Firebase data arrived. Added placeholder text (`--`) until the initial data snapshot was received.
- **Firebase V9 Syntax**: Transitioning to the modular SDK required adjusting imports compared to older Firebase documentation.

## Key Learnings
- Mastered the integration of Firebase services into a custom frontend.
- Understood NoSQL data structuring for IoT applications.
- Learned how to secure cloud databases using robust `.read` and `.write` rules.

## Future Improvements
- Add graphical charts (e.g., Chart.js) to visualize historical data directly in the browser instead of exporting to CSV.

## Reflection
Building a custom dashboard from scratch provides far more flexibility and professional polish than using constrained third-party dashboards. It provides a scalable foundation for enterprise applications.

## Project Links
- [Live Login Page](https://env-monitor-845af.web.app/index.html)
- [Live Dashboard](https://env-monitor-845af.web.app/dashboard.html)
- Developer: Harish Kumaran (ProtoSem Week 7)

## Conclusion
The Firebase dashboard was successfully developed, secured, and deployed. It is now ready to receive live telemetry from the physical ESP32 sensor node deployed in Task 5.
