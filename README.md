# Face Recognition Attendance System with Anti-Spoofing

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python)
![OpenCV](https://img.shields.io/badge/OpenCV-4.x-blue?logo=opencv)
![YOLOv8](https://img.shields.io/badge/YOLOv8-ultralytics-orange)
![cvzone](https://img.shields.io/badge/cvzone-1.5%2B-brightgreen)

An advanced, real-time attendance system that leverages facial recognition for automated check-ins. This project's key feature is a robust **YOLOv8-powered anti-spoofing mechanism** that prevents proxy attendance by detecting phones, screens, or printed images, ensuring reliable identity verification.

## 📸 Demo

*(**Important:** You should record a GIF of your project in action and add it here. Show a successful check-in and a failed spoof attempt. You can use a tool like [ScreenToGif](https://www.screentogif.com/) or [Kap](https://getkap.co/).)*

![Project Demo GIF](https://your-link-to-demo.gif)

## ✨ Key Features

* **AI-Powered Attendance:** Automates the attendance process using real-time facial recognition from a webcam feed.
* **Advanced Anti-Spoofing:** Integrated with **YOLOv8** to detect spoofing attempts. The system can identify if a person is trying to use a photo, video, or a screen to fool the camera, making the attendance system secure.
* **Dynamic UI Display:** Uses `cvzone` to create a clean and informative overlay on the video feed. This UI displays:
    * Employee/Student Profile (Name, ID, etc.)
    * Total Attendance Count
    * Time of Last Successful Attendance
* **Efficient Monitoring:** The clear UI and reliable verification provide a massive improvement in monitoring and logging efficiency.
* **Real-time Database Integration:** (Assuming this) Automatically logs verified attendance into a CSV file or database with timestamps.

## 🛠️ Technology Stack

* **Python:** The core programming language.
* **OpenCV:** For capturing the webcam feed and performing all core computer vision processing.
* **YOLOv8 (Ultralytics):** For state-of-the-art, real-time object detection (used for anti-spoofing).
* **cvzone:** A helpful library built on top of OpenCV to simplify drawing UI elements, bounding boxes, and text.
* **face_recognition:** (Or your specific library) For encoding known faces and matching them against new ones.
* **NumPy:** For high-performance numerical operations on image data.

## ⚙️ How It Works

The system follows a multi-stage pipeline in real-time:

1.  **Capture Frame:** The system captures a frame from the webcam.
2.  **Anti-Spoofing:** The frame is passed through the **YOLOv8 model** trained to detect objects like 'phone' or 'screen'. If a spoofing object is detected with high confidence, the recognition process is halted for that frame.
3.  **Face Detection:** If no spoofing is detected, the system locates all faces in the frame.
4.  **Face Recognition:** For each face, it computes the facial embeddings and compares them against a pre-computed database of known individuals.
5.  **Mark Attendance:** If a match is found:
    * The system checks if the person has already been marked present recently.
    * If not, it logs the attendance (e.g., in a `attendance.csv` file) with the person's name and a timestamp.
6.  **Update UI:** The `cvzone` interface is updated to display the person's profile information and their attendance status.

## 🚀 Getting Started

### Prerequisites

* Python 3.8+
* A webcam
* Pre-trained YOLOv8 model weights for anti-spoofing (e.g., `your_model.pt`)

### Installation

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/vedantnarang/face-recognition-attendance-with-spoof-detection.git](https://github.com/vedantnarang/face-recognition-attendance-with-spoof-detection.git)
    cd face-recognition-attendance-with-spoof-detection
    ```

2.  **Create and activate a virtual environment:**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    ```

3.  **Install the required packages:**
    *(It's best if you create a `requirements.txt` file in your repo)*
    ```bash
    pip install -r requirements.txt
    ```
    *(If you don't have one, list the main packages)*
    ```bash
    pip install opencv-python ultralytics cvzone face-recognition numpy
    ```

4.  **Prepare Face Data:**
    * Add images of known individuals to the `(your-images-folder)` directory.
    * Run the encoding script to generate the face encodings file:
        ```bash
        python your_encoding_script.py
        ```

## ▶️ How to Run

Once the setup is complete, run the main application script:

```bash
python main.py  # Or whatever your main script is named
