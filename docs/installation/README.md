# Installation Guide

This guide will help you install and set up the Smart Camera Manager on your system.

## Table of Contents
- [Prerequisites](#prerequisites)
- [System Requirements](#system-requirements)
- [Installation Steps](#installation-steps)
- [Platform-Specific Instructions](#platform-specific-instructions)
- [Troubleshooting](#troubleshooting)
- [Next Steps](#next-steps)

## Prerequisites

### Required Software
- Python 3.7 or higher
- pip (Python package manager)
- git (for cloning the repository)
- FFmpeg
- OpenCV dependencies

### Optional Software
- CUDA Toolkit (for NVIDIA GPU acceleration)
- OpenCL runtime (for GPU acceleration on other devices)

## System Requirements

### Minimum Requirements
- CPU: Dual-core processor, 2.0 GHz
- RAM: 4 GB
- Storage: 1 GB free space
- OS: Windows 10, Ubuntu 18.04+, or macOS 10.14+

### Recommended Requirements
- CPU: Quad-core processor, 3.0 GHz or better
- RAM: 8 GB or more
- Storage: 5 GB free space
- GPU: NVIDIA GPU with CUDA support
- OS: Windows 10/11, Ubuntu 20.04+, or macOS 11+

## Installation Steps

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/smart-camera-manager.git
cd smart-camera-manager
```

### 2. Create a Virtual Environment (Recommended)
```bash
# On Windows
python -m venv venv
.\venv\Scripts\activate

# On Linux/macOS
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Python Dependencies
```bash
pip install -r requirements.txt
```

### 4. Install FFmpeg

#### Windows
1. Download FFmpeg from [ffmpeg.org](https://ffmpeg.org/download.html)
2. Extract the archive
3. Add the bin folder to your system PATH
4. Verify installation: `ffmpeg -version`

#### Ubuntu/Debian
```bash
sudo apt update
sudo apt install ffmpeg
sudo apt install ubuntu-restricted-extras
```

#### macOS
```bash
brew install ffmpeg
```

### 5. Install Hardware Acceleration (Optional)

#### NVIDIA CUDA
1. Download CUDA Toolkit from [NVIDIA website](https://developer.nvidia.com/cuda-downloads)
2. Follow NVIDIA's installation guide
3. Verify installation: `nvcc --version`

#### OpenCL
- Usually comes with GPU drivers
- Install GPU vendor's development kit if needed

## Platform-Specific Instructions

### Windows

1. Install Visual C++ Redistributable
```bash
# Download from Microsoft's website
# https://aka.ms/vs/16/release/vc_redist.x64.exe
```

2. Install K-Lite Codec Pack
- Download from [codecguide.com](https://www.codecguide.com/download_kl.htm)
- Install using default settings

### Linux (Ubuntu/Debian)

1. Install additional dependencies
```bash
sudo apt install python3-dev
sudo apt install libopencv-dev
sudo apt install v4l-utils
```

2. Set up camera permissions
```bash
sudo usermod -a -G video $USER
```

### macOS

1. Install Xcode Command Line Tools
```bash
xcode-select --install
```

2. Install Homebrew (if not already installed)
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## Troubleshooting

### Common Issues

1. **"FFmpeg not found" error**
   - Ensure FFmpeg is in your system PATH
   - Try running `ffmpeg -version` in terminal
   - Reinstall FFmpeg if needed

2. **"ImportError: No module named cv2"**
   - Reinstall OpenCV: `pip install opencv-python`
   - Install OpenCV dependencies: `pip install opencv-contrib-python`

3. **Camera access issues**
   - Check camera permissions
   - Ensure camera is not in use by other applications
   - Try different camera index or URL

4. **Hardware acceleration not working**
   - Update GPU drivers
   - Check CUDA/OpenCL installation
   - Verify GPU compatibility

### Getting Help

If you encounter issues not covered here:
1. Check the [Issue Tracker](https://github.com/yourusername/smart-camera-manager/issues)
2. Search existing issues for similar problems
3. Create a new issue with:
   - Detailed description of the problem
   - Steps to reproduce
   - System information
   - Error messages
   - Log files

## Next Steps

After installation:
1. Read the [Configuration Guide](../configuration/README.md)
2. Follow the [User Guide](../guides/user_guide.md)
3. Check [Examples](../examples/README.md) for common use cases 