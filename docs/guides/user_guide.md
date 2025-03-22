# User Guide

A comprehensive guide to using the Smart Camera Manager.

## Table of Contents
- [Getting Started](#getting-started)
- [Basic Operations](#basic-operations)
- [Advanced Features](#advanced-features)
- [Tips and Tricks](#tips-and-tricks)
- [Troubleshooting](#troubleshooting)

## Getting Started

### First Launch

1. **Launch the Application**
   ```bash
   python smart_camera_manager.py
   ```

2. **Initial Setup**
   - The application will create necessary directories
   - Default configuration will be loaded
   - System capabilities will be analyzed

3. **Main Window Overview**
   ![Main Window](../images/main_window.png)
   - Left panel: Camera controls and settings
   - Center area: Camera views
   - Right panel: System monitoring

### Adding Your First Camera

1. **Click "Add Camera" or press Ctrl+A**
2. **Enter Camera Details:**
   - Name: Give your camera a unique name
   - Source: 
     - For USB cameras: Enter 0, 1, 2, etc.
     - For IP cameras: Enter the URL (e.g., rtsp://192.168.1.100:554/stream)
   - FPS: Choose desired frame rate (default: 30)
   - Enable Detection: Toggle face detection

3. **Click "Add" to connect**
   - The system will test the connection
   - Camera view will appear if successful
   - Status will be shown in the camera list

## Basic Operations

### Camera Management

#### Adding Cameras
1. Click "Add Camera"
2. Enter camera details
3. Click "Add"

#### Removing Cameras
1. Select camera from list
2. Click "Remove Camera"
3. Confirm removal

#### Camera Settings
1. Right-click camera in list
2. Select "Settings"
3. Adjust as needed:
   - Resolution
   - Frame rate
   - Detection settings

### Recording

#### Start Recording
1. Select camera
2. Click "Start Recording" or press Ctrl+R
3. Recording status will be indicated

#### Stop Recording
1. Select recording camera
2. Click "Stop Recording" or press Ctrl+R again

#### Recording Settings
1. Click "Recording Settings"
2. Configure:
   - Quality (CRF value)
   - Segment duration
   - Storage location

### Live View

#### View Modes
- Single camera: Double-click camera
- Grid view: Click "Grid View"
- Custom layout: Drag and drop cameras

#### Stream Controls
- Pause: Click pause button
- Resume: Click play button
- Suppress: Click "Suppress Stream"

## Advanced Features

### Face Detection

1. **Enable Detection**
   - Select camera
   - Click "Enable Detection"
   - Adjust detection settings if needed

2. **Detection Settings**
   - Scale factor: Affects detection accuracy
   - Minimum neighbors: Reduces false positives
   - Minimum size: Smallest face to detect

### Hardware Acceleration

1. **Enable CUDA**
   - Requires NVIDIA GPU
   - Set in configuration
   - Verify in system monitor

2. **Enable OpenCL**
   - Available on most GPUs
   - Configure in settings
   - Monitor performance

### Performance Optimization

1. **Thread Pool**
   - System automatically adjusts
   - Monitor in resource panel
   - Manual adjustment possible

2. **Quality Profiles**
   - High: Full resolution
   - Medium: Balanced
   - Low: Performance focused

## Tips and Tricks

### Performance

1. **Optimize CPU Usage**
   - Reduce camera resolution
   - Lower frame rate
   - Disable unused features

2. **Reduce Memory Usage**
   - Smaller frame buffers
   - Fewer active cameras
   - Regular cleanup

3. **Storage Management**
   - Enable automatic cleanup
   - Set reasonable segment sizes
   - Monitor free space

### Camera Setup

1. **IP Cameras**
   - Use direct RTSP when possible
   - Set appropriate timeout
   - Configure reconnection

2. **USB Cameras**
   - Check device permissions
   - Use appropriate resolution
   - Monitor USB bandwidth

3. **Multiple Cameras**
   - Balance system resources
   - Use grid layout
   - Consider network impact

### Recording

1. **Quality vs Size**
   - CRF 18-23: High quality
   - CRF 23-28: Balanced
   - CRF 28-32: Storage efficient

2. **Segmentation**
   - Use reasonable durations
   - Monitor segment sizes
   - Set up auto-cleanup

3. **Storage Planning**
   - Calculate needed space
   - Set up rotation
   - Monitor usage

## Troubleshooting

### Common Issues

1. **Camera Won't Connect**
   - Check network/USB connection
   - Verify camera URL/index
   - Check permissions
   - Review logs

2. **Poor Performance**
   ```
   Symptoms:
   - High CPU usage
   - Dropped frames
   - Slow response
   
   Solutions:
   - Reduce camera count
   - Lower resolution
   - Enable hardware acceleration
   - Check system resources
   ```

3. **Recording Issues**
   ```
   Symptoms:
   - Failed recordings
   - Missing segments
   - Poor quality
   
   Solutions:
   - Check storage space
   - Verify FFmpeg
   - Adjust CRF
   - Check codec support
   ```

### Error Messages

1. **"Failed to open camera"**
   - Check camera connection
   - Verify URL/index
   - Check permissions
   - Try different port

2. **"Hardware acceleration failed"**
   - Update GPU drivers
   - Check GPU support
   - Verify CUDA/OpenCL
   - Fall back to CPU

3. **"Recording error"**
   - Check disk space
   - Verify write permissions
   - Check FFmpeg status
   - Review codec support

### Getting Help

1. **Log Files**
   - Location: `~/.local/share/smart-camera-manager/logs/`
   - Check recent errors
   - Include in bug reports

2. **System Information**
   - Click "About"
   - Copy system info
   - Include in reports

3. **Support Channels**
   - GitHub Issues
   - Documentation
   - Community forums

## Keyboard Shortcuts

| Action | Shortcut |
|--------|----------|
| Add Camera | Ctrl+A |
| Remove Camera | Ctrl+R |
| Start/Stop Recording | Ctrl+S |
| Suppress Stream | Ctrl+T |
| Full Screen | F11 |
| Settings | Ctrl+, |
| Help | F1 |
| Quit | Ctrl+Q |

## Best Practices

1. **Regular Maintenance**
   - Check logs weekly
   - Clean old recordings
   - Update configuration
   - Monitor performance

2. **Backup Configuration**
   - Save settings regularly
   - Document changes
   - Keep backup copy

3. **Resource Management**
   - Monitor CPU/RAM usage
   - Check storage space
   - Review camera settings
   - Optimize as needed

4. **Security**
   - Use secure passwords
   - Update regularly
   - Check permissions
   - Monitor access

## Additional Resources

1. **Documentation**
   - [Installation Guide](../installation/README.md)
   - [Configuration Guide](../configuration/README.md)
   - [API Documentation](../api/README.md)

2. **Examples**
   - [Example Scripts](../examples/README.md)
   - [Configuration Examples](../examples/configs/)
   - [Use Cases](../examples/use_cases/) 