# Smart Camera Manager

A powerful, feature-rich camera management system built with Python. Manage multiple camera feeds, record videos with intelligent segmenting, detect faces, and optimize performance automatically based on your system resources.

## 📚 Documentation Structure

Our documentation is organized into several sections for easy navigation:

### 📖 Core Documentation
- [Installation Guide](docs/installation/README.md) - Get up and running quickly
- [Configuration Guide](docs/configuration/README.md) - Configure the system to your needs
- [User Guide](docs/guides/user_guide.md) - Learn how to use the system
- [API Documentation](docs/api/README.md) - Detailed API reference
- [Architecture Overview](docs/architecture/README.md) - System design and components

### 🚀 Quick Start
```bash
# Clone the repository
git clone https://github.com/yourusername/smart-camera-manager.git

# Install dependencies
pip install -r requirements.txt

# Run the application
python smart_camera_manager.py
```

### ✨ Key Features

#### Camera Management
- Multi-camera support (USB, IP cameras, RTSP streams)
- Dynamic stream handling
- Automatic performance optimization

#### Video Processing
- Real-time face detection
- Hardware acceleration support (CUDA, OpenCL)
- Dynamic quality adjustment

#### Recording
- Intelligent video segmentation
- Multiple codec support
- Automatic quality optimization

#### User Interface
- Live preview of all cameras
- Performance monitoring
- Easy configuration management

### 🛠 System Requirements

- Python 3.7+
- OpenCV
- FFmpeg
- CUDA/OpenCL (optional, for hardware acceleration)
- 4GB RAM minimum (8GB+ recommended)
- Modern CPU with multiple cores

### 📈 Performance

The system automatically adjusts to your hardware capabilities:
- Supports 1-20+ cameras (depending on hardware)
- Automatic thread pool management
- Dynamic quality adjustment
- Hardware acceleration when available

### 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

### 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

### 🙏 Acknowledgments

- OpenCV team
- FFmpeg project
- All contributors

### 📞 Support

- [Issue Tracker](https://github.com/yourusername/smart-camera-manager/issues)
- [Documentation](docs/)

![Smart Camera Manager Screenshot][placeholder_for_screenshot]

## Features

### Camera Management
- **Multi-Camera Support**: Connect to USB webcams, IP cameras (RTSP, HTTP), and more
- **Dynamic Stream Handling**: Automatically adjust thread allocation based on system load
- **Camera Status Monitoring**: Track FPS, connection status, and stream health

### Video Processing
- **Face Detection**: Real-time face detection using Haar cascades
- **Hardware Acceleration**: Utilize CUDA, OpenCL, or Intel MediaSDK when available
- **Performance Optimization**: Dynamically adjust processing based on system resources

### Recording
- **Intelligent Segmenting**: Automatically create new video segments by time or size
- **Dynamic Quality Adjustment**: Optimize CRF (Constant Rate Factor) based on recording conditions
- **Flexible Output Options**: Configure resolution, framerate, and encoding speed

### User Interface
- **Live Preview**: View all camera streams simultaneously
- **Performance Metrics**: Monitor CPU, memory, and processing performance in real-time
- **Configuration Management**: Save and load camera configurations
- **Recording Controls**: Start/stop recording for individual cameras

### System Integration
- **Resource Monitoring**: Analyze system capacity for optimal camera count
- **Error Handling**: Robust error recovery for camera disconnections
- **Graceful Shutdown**: Properly close resources when exiting

## Requirements

- Python 3.7+
- OpenCV (cv2)
- NumPy
- Tkinter (usually comes with Python)
- psutil
- FFmpeg (must be installed separately)

## Installation

1. Clone this repository:
   ```
   git clone https://github.com/yourusername/smart-camera-manager.git
   cd smart-camera-manager
   ```

2. Install Python dependencies:
   ```
   pip install -r requirements.txt
   ```

3. Install FFmpeg:
   - **Windows**: Download from [ffmpeg.org](https://ffmpeg.org/download.html) and add to PATH
   - **macOS**: Use Homebrew: `brew install ffmpeg`
   - **Linux**: Use your package manager: `sudo apt install ffmpeg` (Debian/Ubuntu)

## Usage

1. Launch the application:
   ```
   python smart_camera_manager.py
   ```

2. Add a camera:
   - Click "Add Camera"
   - Enter a name for the camera
   - Specify the source:
     - For USB cameras: Enter the device index (usually 0, 1, 2...)
     - For IP cameras: Enter the full URL (e.g., rtsp://admin:password@192.168.1.100:554/stream)

3. Control cameras:
   - Start/stop recording for selected camera
   - Suppress/unsuppress the stream (to save CPU while still recording)
   - Remove camera when no longer needed

4. Adjust settings:
   - Click "Recording Settings" to configure video quality, segment size, etc.
   - The system will also automatically adjust settings based on your hardware

5. Save your configuration:
   - Click "Save Config" to save your camera setup for next time
   - Use "Load Config" to restore a previously saved configuration

## Key Shortcuts

- **Ctrl+A**: Add a new camera
- **Ctrl+R**: Remove selected camera
- **Ctrl+S**: Start/stop recording for selected camera
- **Ctrl+T**: Suppress/unsuppress selected camera stream
- **Ctrl+Q**: Quit the application

## Optimizing Performance

- If you experience performance issues:
  - Reduce the number of active cameras
  - Lower the resolution or framerate in Recording Settings
  - Disable face detection for cameras where it's not needed
  - Ensure hardware acceleration is available and enabled

## Troubleshooting

### Common Issues

1. **"Failed to open camera"**:
   - For USB cameras: Ensure the device index is correct and the camera is not in use by another application
   - For IP cameras: Verify the URL, username, and password are correct, and that the camera is accessible from your network

2. **"FFmpeg not found"**:
   - Ensure FFmpeg is installed and added to your system PATH
   - Restart the application after installing FFmpeg

3. **High CPU usage**:
   - Reduce the number of active cameras
   - Disable face detection
   - Lower the resolution in Recording Settings
   - Suppress streams that don't need to be monitored in real-time

### Getting Help

If you encounter issues not covered here, please [open an issue](https://github.com/yourusername/smart-camera-manager/issues) with details about your problem, including:
- Your operating system
- Python version
- Error messages
- Steps to reproduce the issue

## Future Enhancements

- Motion detection
- Object recognition
- Cloud storage integration
- Mobile app for remote viewing
- Email/SMS notifications

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- OpenCV team for the excellent computer vision library
- FFmpeg project for video encoding capabilities
- All contributors and testers

---

[placeholder_for_screenshot]: screenshot.png "Smart Camera Manager Screenshot"