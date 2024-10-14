# Maixduino Facial Recognition Project
# 🚀 Project Overview
This repository contains a cutting-edge project developed on the Maixduino Sipeed Board using facial recognition. The system captures real-time images via the GC0328 camera and leverages a model trained on the Maixhub platform to perform facial recognition. The objective is to implement an efficient, embedded AI system that can recognize and track faces in real time using minimal resources.  

# 🧠 Key Features
*Board:* Maixduino Sipeed K210 RISC-V AI+IoT board  
*Camera:* GC0328 camera for image capturing and dataset creation  
*Training Platform:* Model trained using Maixhub  
*Technology:* Facial recognition using embedded machine learning  
*Real-time Processing:* Fast, low-latency face detection and recognition  
*SD Card Storage:* Option to store datasets or captured images  
# 📸 Components Used
*Maixduino Sipeed Board* - RISC-V dual-core processor with AI capabilities.  
*GC0328 Camera* - Captures real-time images to feed into the recognition system.  
*MicroSD Card* - Optional, for storing datasets and captured images.  
*Maixhub* - Used for training and deploying the facial recognition model.  
# 🛠️ Setup Instructions
# Prerequisites:
Maixduino Sipeed Board with K210 chip.  
GC0328 Camera Module.  
MicroSD Card for optional image storage.  
MaixPy IDE for writing and uploading code.  
Maixhub Account to upload and train your model.  
Step-by-Step Guide:  
# Hardware Setup:

Connect the GC0328 camera to the Maixduino board.  
Ensure the camera is properly attached and facing the desired direction for facial data capture.  
# Dataset Collection:

Capture facial images using the board’s camera.  
Use MaixPy to control the camera and collect your dataset.  
# Training with Maixhub:

Upload your dataset to Maixhub.  
Train your facial recognition model.  
Download the trained model (.kmodel) once completed.  
# Model Deployment:

Upload the trained model to your Maixduino board.  
Ensure the model is stored in the right directory for inference.  
# Facial Recognition:

Run the provided script to start the recognition process.
The system will capture live frames from the camera and process them using the trained model.
Code Snippet (Main Script)
python
Copy code
import sensor, image, lcd, time
from Maix import KPU

lcd.init()
sensor.reset()
sensor.set_pixformat(sensor.RGB565)
sensor.set_framesize(sensor.QVGA)
sensor.run(1)

# Load your trained model
task = KPU.load("/sd/facial_rec.kmodel")

while True:
    img = sensor.snapshot()
    lcd.display(img)
    # Perform facial recognition inference
    faces = KPU.forward(task, img)
    if faces:
        for face in faces:
            img.draw_rectangle(face)
    lcd.display(img)
# Deployment:
Copy the trained model and the script to the Maixduino board’s SD card.
Execute the script using MaixPy.  
# 🔧 Troubleshooting
*No Camera Detected:* Ensure the GC0328 camera is properly connected to the board.     
*Low Accuracy:* Ensure you have collected a diverse dataset for training. Try retraining with more samples on Maixhub.    
*Model Loading Error:* Verify that the trained model is saved with the correct path (/sd/facial_rec.kmodel).    
# 🏗️ Future Enhancements
Integrating voice feedback to notify the user when a face is recognized.      
Extending the system to recognize multiple faces in crowded environments.    
Adding cloud support to log recognized faces for remote monitoring.    
# 📄 License
This project is open-sourced under the MIT License. Feel free to fork and improve it!  
# Happy Making! 😎
