# Object Detection with Raspberry Pi Using CircuitDigest Cloud

This project demonstrates how to perform real-time object detection using a Raspberry Pi, a USB Camera, and the CircuitDigest Cloud API. This solution eliminates the need for manual dataset collection, data labeling, or local model training. By leveraging the CircuitDigest Cloud API, the Raspberry Pi can act as a plug-and-play object detection system capable of identifying over 75+ object classes.

## Features
- **Real-Time Detection:** Uses cloud-based AI to quickly identify objects in the frame.
- **Multiple Operating Modes:**
  - **Keyboard Mode:** Capture images manually by pressing the `SPACE` key (ideal for desktop/VNC use).
  - **Auto Mode:** Automatically captures images at a fixed time interval (e.g., every 5 seconds) for continuous monitoring.
  - **SSH Mode:** Runs in the terminal without needing an OpenCV display window.
- **Adjustable Parameters:** Easily customize confidence thresholds and filter specific object classes.
- **Low Hardware Requirements:** No heavy local processing is needed; inference is done on the cloud.

## Hardware Requirements
- **Raspberry Pi** (Any model like Pi 3 or Pi 4, connected to external power)
- **USB Web Camera** (Connected to any USB port on the Pi)
- MicroSD Card (with Raspberry Pi OS installed)

## Hardware Setup
1. Connect the USB Camera to one of the USB ports on the Raspberry Pi.
2. Ensure the Raspberry Pi is powered by a sufficient external power supply.
3. Access the Raspberry Pi either via:
   - **Direct Connection:** Monitor, Keyboard, and Mouse.
   - **SSH:** Headless terminal access.
   - **VNC Viewer:** Remote desktop access.

## Software Setup
1. Setup your Raspberry Pi using the **Raspberry Pi Imager** with a standard OS installation.
2. Create an account on the [CircuitDigest Cloud](https://www.circuitdigest.cloud/).
3. Navigate to the **Object Detection** feature and obtain your **API Key**.
4. Open **Thonny IDE** (or your preferred Python editor) on your Raspberry Pi.
5. Install the necessary Python packages if they aren't already installed:
   ```bash
   pip install opencv-python requests
   ```

## Installation & Usage
1. Clone this repository or copy the Python script to your Raspberry Pi.
2. Edit the script to include your API key and configure parameters:
   ```python
   SERVER_URL = "https://www.circuitdigest.cloud/api/v1/object-detection/detect"
   API_KEY    = "YourApikey"  # <-- Paste your CircuitDigest API Key here
   CLASSES    = "[]"          # <-- Define specific classes or leave empty for all
   CONFIDENCE = "0.2"         # <-- Adjust confidence threshold (e.g., 0.2 for 20%)
   MODE = "auto"              # <-- Set to "keyboard", "auto", or "ssh"
   AUTO_INTERVAL = 5          # <-- Interval in seconds for auto mode
   ```
3. Run the script:
   ```bash
   python object_detection.py
   ```
4. Depending on the mode you selected, the system will start capturing images, sending them securely to the CircuitDigest Cloud, and printing the detected objects along with their confidence scores to the terminal.

## Troubleshooting
- **Camera not found! Check USB camera connection:** 
  Check the physical connection. You may need to change the camera index in the code from `cv2.VideoCapture(0)` to `cv2.VideoCapture(1)`.
- **API request failure or timeout error:** 
  Verify your Wi-Fi connection and ensure your API key is correct. You can also try increasing the timeout value in the request.
- **Low detection accuracy:** 
  Ensure good lighting and that the object is clearly visible. Increase the `CONFIDENCE` threshold to reduce false positives.
- **Slow response from the system:** 
  Try reducing the camera resolution in OpenCV, or increase the `AUTO_INTERVAL` time. A stable internet connection is required for faster API responses.

## Advantages & Limitations
| Advantages | Limitations |
| :--- | :--- |
| Real-time object detection using cloud AI | Depends entirely on an active internet connection |
| Low-cost system using a Raspberry Pi | Slight delay due to API processing time |
| Easy to implement without heavy local processing | Limited API usage (scans per day/month depending on your plan) |
| Supports 75+ predefined object classes | Accuracy can drop in low-light conditions |

## Link for the Full Guide

https://circuitdigest.com/microcontroller-projects/raspberry-pi-object-detection-using-circuitdigest-cloud

---


## Relevant Links
- [CircuitDigest Cloud Platform](https://www.circuitdigest.cloud/)
- [Raspberry Pi based Object Detection GitHub Repo](https://github.com/Circuit-Digest/Raspberry-Pi-based-Object-Detection)
