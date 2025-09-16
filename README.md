# Real-Time Facial Recognition Entry System  


This project was originally crafted by my friend.  
I just ran it on my laptop, dropped a few *"hey, maybe do this"* suggestions,  
and pretended to understand everything (don’t worry, I eventually did 👀).  
So here’s the *officially unofficial* README.

---

## 📌 Project Overview  
This project implements a real-time facial recognition-based entry system designed to automate employee check-ins with high accuracy and low latency. The system captures real-time face images via a web frontend, processes and enhances the images, extracts facial embeddings using advanced deep learning models, and matches them against stored employee data for instant authentication and attendance logging.  

---

## ✨ Key Features  

- **Real-Time Face Capture** – Employees use a browser-based camera interface to capture their face images on the spot.  
- **Image Quality Enhancement** – Utilizes **GFPGAN** to improve low-quality or low-light face images, increasing recognition accuracy.  
- **Robust Face Recognition** – Combines **ArcFace (InsightFace)** and **Vision Transformer (ViT)** models for highly accurate facial embedding extraction.  
- **Multi-Modal Embeddings** – Uses both ArcFace and ViT embeddings to improve match robustness under varying lighting, angles, and facial accessories (spectacles, masks, etc.).  
- **Automatic Face Registration** – Streamlines onboarding by allowing employees to register their faces directly through live capture.  
- **Efficient Database Storage** – Stores facial embeddings and employee info securely in **PostgreSQL** for quick retrieval.  
- **API-Driven Backend** – **FastAPI** powers backend endpoints for check-in, face registration, and embedding retrieval.  
- **Frontend Integration** – **Next.js** frontend offers a seamless user experience with real-time camera capture, check-in initiation, and success/failure alerts.  
- **Face Detection** – **MediaPipe** enhances face detection robustness before recognition.  
- **Error Handling** – Handles scenarios like face capture failure, embedding generation errors, and unauthorized check-ins gracefully with informative responses.  

---

## 🛠️ Technologies Used  

| Layer/Component     | Technology/Library          | Purpose |
|---------------------|-----------------------------|---------|
| **Frontend**        | Next.js                     | Camera UI, user interaction, API calls |
| **Backend**         | FastAPI                     | REST API endpoints, business logic |
| **Face Detection**  | MediaPipe                   | Real-time face detection |
| **Face Enhancement**| GFPGAN                      | Face image super-resolution and restoration |
| **Face Recognition**| InsightFace (ArcFace)       | Extract facial embeddings |
|                     | Vision Transformer (ViT)    | Alternate embeddings |
| **Database**        | PostgreSQL                  | Store employee data and facial embeddings |
| **Image Processing**| OpenCV                      | Real-time video frame capture and processing |
| **Machine Learning**| PyTorch, TensorFlow         | Model inference and embedding extraction |

---

## 🔄 System Architecture & Flow  

1. Employee opens the frontend (Next.js) and clicks the **Start Check-in** button.  
2. Browser accesses the camera and captures a real-time image of the employee's face.  
3. Captured image is sent to the **FastAPI backend** via a POST request.  
4. Backend uses **MediaPipe** to detect the face in the image.  
5. If the image quality is low or face features are blurred, the image is enhanced using **GFPGAN**.  
6. The system extracts two sets of facial embeddings:  
   - ArcFace embedding via **InsightFace**  
   - Vision Transformer (ViT) embedding  
7. The embeddings are compared with stored embeddings in **PostgreSQL** to find a matching employee.  
8. On successful match, a check-in record is created in the database with a timestamp.  
9. The backend returns a success message with the employee’s name and check-in time.  
10. The frontend displays an alert confirming the successful check-in.  
11. If no match or errors occur, appropriate error messages are returned and displayed.  

---

