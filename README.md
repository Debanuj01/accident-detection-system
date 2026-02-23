# 🚗 YOLOv8 Vehicle Crash Detection System

<div align="center">

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![YOLOv8](https://img.shields.io/badge/YOLOv8-Latest-green)
![License](https://img.shields.io/badge/License-MIT-yellow)
![Status](https://img.shields.io/badge/Status-Active-success)

*An intelligent real-time vehicle accident detection system powered by YOLOv8 deep learning model with instant WhatsApp notifications.*

[Features](#-features) • [Installation](#-installation) • [Usage](#-usage) • [Configuration](#%EF%B8%8F-configuration) • [Screenshots](#-screenshots)

</div>

---

## 📋 Overview

This advanced Computer Vision system leverages YOLOv8 object detection to monitor live camera feeds and automatically detect vehicle accidents in real-time. Upon detection, it immediately sends WhatsApp alerts via Twilio, saves evidence images, and maintains a comprehensive detection log.

### 🎯 Key Highlights

- **Real-time Detection**: Processes live video feeds with high accuracy
- **Dual Interface**: Desktop GUI (CustomTkinter) and Web App (Streamlit)
- **Instant Alerts**: WhatsApp notifications via Twilio integration
- **Evidence Management**: Automatic saving of accident frames with timestamps
- **Multi-Camera Support**: Monitor multiple camera sources simultaneously
- **Detection History**: Complete log of all detected incidents with location tracking
- **Configurable Confidence Threshold**: Adjust detection sensitivity

---

## ✨ Features

### 🖥️ Desktop Application (main.py)

- **Modern Dark-themed GUI** built with CustomTkinter
- **Real-time video processing** with live feed display
- **Configurable detection settings**:
  - Adjustable confidence threshold (0-100%)
  - Camera source selection (Webcam/External)
  - Accident frame confirmation threshold
- **WhatsApp Notifications**:
  - Automatic alerts with location and timestamp
  - Test notification feature
  - Configurable cooldown period
- **Camera Location Management**: Assign names to different camera feeds
- **Evidence Storage**: Automatically saves accident frames with metadata
- **Detection History Viewer**: Browse all detected incidents with images
- **Export Logs**: Export detection data to CSV format

### 🌐 Web Application (app.py)

- **Streamlit-based interface** for browser access
- **Video/Image Upload**: Analyze pre-recorded footage
- **Live Webcam Detection**: Real-time processing through browser
- **Interactive Dashboard**: Visual statistics and detection metrics
- **Downloadable Evidence**: Save detected accident frames

### 🧠 AI Model

- **YOLOv8 Architecture**: State-of-the-art object detection
- **Custom Trained Model**: Specialized for accident detection
- **High Accuracy**: Optimized for various accident scenarios
- **Fast Inference**: Real-time processing capabilities

---

## 🛠️ Installation

### Prerequisites

- Python 3.8 or higher
- Webcam or IP camera
- Twilio account (for WhatsApp notifications)

### Step 1: Clone the Repository

```bash
git clone https://github.com/Debanuj01/accident-detection-system.git
cd accident-detection-system
```

### Step 2: Create Virtual Environment

```bash
# Windows
python -m venv venv
venv\Scripts\activate

# Linux/Mac
python3 -m venv venv
source venv/bin/activate
```

### Step 3: Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 4: Download Model

**Important**: The model file is not included in the repository due to its size.

See [MODEL_DOWNLOAD.md](MODEL_DOWNLOAD.md) for instructions on:
- Training your own model
- Using pre-trained YOLOv8 models
- Model placement

The `best.pt` file must be in the root directory before running the application.

---

## 🚀 Usage

### Desktop Application

Run the main application:

```bash
python main.py
```

**Getting Started:**

1. **Configure Detection Settings**:
   - Navigate to "Detection Settings" tab
   - Adjust confidence threshold (default: 0.5)
   - Select camera source (Webcam/External)
   - Enable/disable evidence saving

2. **Setup WhatsApp Notifications** (Optional):
   - Go to "Notification Settings" tab
   - Enable WhatsApp notifications
   - Enter your Twilio credentials:
     - Account SID
     - Auth Token
     - Twilio phone number
     - Recipient phone number
   - Click "Save Notification Settings"
   - Test with "Test WhatsApp Notification" button

3. **Configure Camera Locations**:
   - Go to "Camera Locations" tab
   - Assign names to your camera feeds
   - Click "Save Location Settings"

4. **Start Detection**:
   - Click "▶️ Start Detection"
   - Monitor the live feed
   - Accidents will be automatically detected and logged

5. **View Detection History**:
   - Click "View Detection History"
   - Browse all detected incidents
   - View evidence images

### Web Application

Launch the Streamlit app:

```bash
streamlit run app.py
```

Access the web interface at `http://localhost:8501`

**Features:**
- Upload video files for analysis
- Use webcam for live detection
- View detection statistics
- Download evidence images

---

## ⚙️ Configuration

### Twilio WhatsApp Setup

1. **Create Twilio Account**:
   - Visit [Twilio](https://www.twilio.com/)
   - Sign up for a free account

2. **Enable WhatsApp Sandbox**:
   - Go to Twilio Console → Messaging → Try it out → Send a WhatsApp message
   - Follow instructions to connect your WhatsApp

3. **Get Credentials**:
   - Account SID: Found in Twilio Console Dashboard
   - Auth Token: Found in Twilio Console Dashboard
   - Twilio Number: Your Twilio WhatsApp-enabled number

4. **Configure in Application**:
   - Open the app
   - Navigate to "Notification Settings"
   - Enter your credentials
   - Save and test

### Detection Parameters

Edit these variables in `main.py` for customization:

```python
confidence_threshold = 0.5          # Detection confidence (0-1)
notification_cooldown = 10          # Seconds between notifications
accident_frames_threshold = 5       # Frames to confirm accident
```

### Camera Configuration

- **Webcam**: Set to `0` (default)
- **External Camera**: Set to `1` or camera URL
- **IP Camera**: Use RTSP URL format

---

## 📁 Project Structure

```
accident-detection-system/
│
├── main.py                  # Desktop application (CustomTkinter)
├── app.py                   # Web application (Streamlit)
├── best.pt                  # YOLOv8 trained model
├── coco1.txt               # Class labels
├── requirements.txt        # Python dependencies
├── .gitignore              # Git ignore file
│
├── accident_evidence/      # Saved accident frames
├── freedomtech/           # Training dataset
│   ├── images/
│   └── labels/
│
└── yolov8_object_detection_on_custom_dataset.ipynb  # Model training notebook
```

---

## 📦 Dependencies

### Core Libraries

- **ultralytics** - YOLOv8 implementation
- **opencv-python** - Computer vision operations
- **customtkinter** - Modern GUI framework
- **streamlit** - Web application framework
- **pandas** - Data manipulation
- **Pillow** - Image processing
- **twilio** - WhatsApp messaging
- **cvzone** - Computer vision utilities

See `requirements.txt` for complete list.

---

## 🔒 Security & Privacy

- **Credentials**: Never commit sensitive data (Twilio credentials)
- **Evidence Storage**: Accident images saved locally only
- **Network Security**: Use HTTPS for IP camera streams
- **Data Privacy**: No data transmitted except WhatsApp alerts

---

## 🎨 Screenshots

### Desktop Application

- Modern dark-themed interface
- Real-time video feed with bounding boxes
- Live detection status
- Configurable settings tabs

### Web Application

- Clean Streamlit interface
- Upload and analyze videos
- Interactive detection dashboard
- Downloadable results

---

## 🚦 How It Works

1. **Video Capture**: System captures frames from camera/video source
2. **Preprocessing**: Frames resized and prepared for model input
3. **Detection**: YOLOv8 model analyzes each frame for accidents
4. **Confirmation**: Multiple consecutive detections required to confirm
5. **Alert**: WhatsApp notification sent with location and timestamp
6. **Evidence**: Frame saved with metadata to accident_evidence folder
7. **Logging**: Incident recorded in detection history

---

## 🔧 Troubleshooting

### Common Issues

**Camera Not Opening:**
- Ensure camera is connected and not in use by another application
- Try different camera IDs (0, 1, 2)
- Check camera permissions

**WhatsApp Notifications Not Working:**
- Verify Twilio credentials are correct
- Ensure WhatsApp sandbox is activated
- Check phone number format (+country code)
- Verify internet connection

**Low Detection Accuracy:**
- Adjust confidence threshold
- Ensure good lighting conditions
- Check camera angle and position
- Verify model file (best.pt) is present

**Performance Issues:**
- Reduce frame processing rate
- Lower camera resolution
- Close unnecessary applications
- Ensure sufficient RAM available

---

## 📈 Future Enhancements

- [ ] Multi-threaded camera processing
- [ ] Cloud storage integration for evidence
- [ ] SMS alert option
- [ ] Email notifications
- [ ] Mobile app version
- [ ] Advanced analytics dashboard
- [ ] Integration with traffic management systems
- [ ] Vehicle license plate recognition
- [ ] Severity classification

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## 👥 Authors

- **Debanuj** - [GitHub](https://github.com/Debanuj01)

---

## 🙏 Acknowledgments

- **Ultralytics** for YOLOv8 framework
- **Twilio** for messaging API
- **OpenCV** community
- All contributors and testers

---

## 📞 Support

For issues, questions, or suggestions:

- Open an issue on GitHub
- Contact: [GitHub Profile](https://github.com/Debanuj01)

---

## ⭐ Star History

If you find this project useful, please consider giving it a star! ⭐

---

<div align="center">

**Made with ❤️ using Python and YOLOv8**

[Back to Top](#-yolov8-vehicle-crash-detection-system)

</div>
