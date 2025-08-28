# 🖥️ Face Recognition Attendance System (with Anti-Spoofing)

This project is a **real-time face recognition attendance system** built with Python, Firebase, and YOLO.  
It automatically detects employees, marks their attendance, and prevents spoofing attempts using phones/screens/videos.

---

## ✨ Features
- 🔍 Real-time face detection and recognition (using `face_recognition`)
- ☁️ Firebase Realtime Database + Storage integration
- ✅ Automatic attendance marking with timestamps
- 🛡️ Anti-Spoofing with YOLO (blocks screens/phones)
- 🖼️ Dynamic UI with employee details & photos
- 📊 Stores total attendance and last attendance time for each employee

---

## ⚙️ Tech Stack
- **Python** (OpenCV, NumPy, Pickle)
- **face_recognition** (dlib based embeddings)
- **Firebase** (Realtime Database + Storage)
- **YOLOv8** (Ultralytics, for spoof detection)
- **cvzone** (for UI elements)

---

## 🚀 How It Works
1. **Registration Phase**
   - Add employee images to the `images/` folder
   - Run `encodinggenerator.py` to generate encodings and upload images to Firebase Storage
   - Add employee details to Firebase using `adddatatodatabase.py`

2. **Recognition & Attendance**
   - Run `main.py`
   - System captures video from webcam
   - If a known face is detected → Attendance is marked in Firebase
   - If a **screen/phone** is detected via YOLO → Attendance is blocked

3. **UI**
   - Live feed is shown inside a custom background frame
   - Employee details and total attendance are displayed when recognized

---

## 📦 Setup Instructions

### 1. Clone the Repository
```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
