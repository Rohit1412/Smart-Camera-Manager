# Configuration Guide

This guide explains all configuration options available in the Smart Camera Manager.

## Table of Contents
- [Camera Configuration](#camera-configuration)
- [Recording Settings](#recording-settings)
- [Performance Settings](#performance-settings)
- [Hardware Acceleration](#hardware-acceleration)
- [User Interface Settings](#user-interface-settings)
- [Advanced Configuration](#advanced-configuration)

## Camera Configuration

### Basic Camera Settings

```python
{
    "source": "rtsp://camera.local/stream",  # Camera source
    "name": "Camera 1",                      # Unique camera name
    "fps": 30,                              # Target frame rate
    "retry_interval": 5,                    # Reconnection interval
    "buffer_size": 24,                      # Frame buffer size
    "enable_detection": true                # Enable face detection
}
```

### Camera Source Types

1. **USB Cameras**
   ```python
   "source": 0  # First USB camera
   "source": 1  # Second USB camera
   ```

2. **IP Cameras**
   ```python
   "source": "rtsp://username:password@192.168.1.100:554/stream"
   "source": "http://192.168.1.100:8080/video"
   ```

3. **DroidCam**
   ```python
   "source": "http://192.168.1.100:4747/video"
   ```

### Connection Settings

```python
{
    "retry_interval": 5,      # Seconds between reconnection attempts
    "max_retries": 3,        # Maximum reconnection attempts
    "timeout": 10,           # Connection timeout in seconds
    "verify_ssl": false      # SSL verification for HTTPS streams
}
```

## Recording Settings

### Video Quality

```python
{
    "recording": {
        "resolution": {
            "width": 1920,
            "height": 1080
        },
        "fps": 30,
        "quality_crf": 23,      # Lower = better quality (18-28 recommended)
        "encoding_preset": "ultrafast"  # Options: ultrafast, superfast, veryfast, faster, fast, medium
    }
}
```

### Segmentation Settings

```python
{
    "segmentation": {
        "max_duration": 900,     # Maximum segment duration (seconds)
        "max_size": 2147483648,  # Maximum segment size (bytes, 2GB)
        "naming_pattern": "{camera_name}_{timestamp}_part{segment:03d}.mp4"
    }
}
```

### Storage Settings

```python
{
    "storage": {
        "base_path": "recordings",
        "organize_by_date": true,
        "cleanup": {
            "enabled": true,
            "max_age_days": 30,
            "min_free_space": 10737418240  # 10GB in bytes
        }
    }
}
```

## Performance Settings

### Thread Pool Configuration

```python
{
    "thread_pool": {
        "min_workers": 1,
        "max_workers": 8,
        "target_cpu_per_worker": 25,  # Target CPU% per worker
        "adjust_interval": 20         # Seconds between adjustments
    }
}
```

### Quality Profiles

```python
{
    "quality_profiles": {
        "high": {
            "preview_width": 640,
            "preview_height": 480,
            "recording_width": 1920,
            "recording_height": 1080,
            "fps": 30
        },
        "medium": {
            "preview_width": 480,
            "preview_height": 360,
            "recording_width": 1280,
            "recording_height": 720,
            "fps": 25
        },
        "low": {
            "preview_width": 320,
            "preview_height": 240,
            "recording_width": 854,
            "recording_height": 480,
            "fps": 20
        }
    }
}
```

### System Resource Limits

```python
{
    "resource_limits": {
        "max_cpu_percent": 80,
        "max_memory_percent": 80,
        "min_free_space_gb": 10,
        "max_cameras": 20
    }
}
```

## Hardware Acceleration

### CUDA Configuration

```python
{
    "gpu_acceleration": {
        "cuda": {
            "enabled": true,
            "device_id": 0,
            "memory_limit": 1024  # MB
        }
    }
}
```

### OpenCL Configuration

```python
{
    "gpu_acceleration": {
        "opencl": {
            "enabled": true,
            "platform_id": 0,
            "device_id": 0
        }
    }
}
```

### Intel MediaSDK Configuration

```python
{
    "gpu_acceleration": {
        "intel_mfx": {
            "enabled": true,
            "implementation": "hardware"  # or "software"
        }
    }
}
```

## User Interface Settings

### Window Configuration

```python
{
    "ui": {
        "window": {
            "title": "Smart Camera Manager",
            "width": 1280,
            "height": 720,
            "start_maximized": false
        },
        "theme": "default",  # or "dark"
        "camera_grid": {
            "columns": 2,
            "spacing": 5
        }
    }
}
```

### Display Settings

```python
{
    "display": {
        "show_fps": true,
        "show_detection_boxes": true,
        "show_camera_name": true,
        "show_timestamp": true,
        "overlay_opacity": 0.7
    }
}
```

## Advanced Configuration

### Logging Configuration

```python
{
    "logging": {
        "level": "INFO",
        "file": "camera_manager.log",
        "max_size": 10485760,  # 10MB
        "backup_count": 5,
        "format": "%(asctime)s - %(levelname)s - %(message)s"
    }
}
```

### Network Settings

```python
{
    "network": {
        "timeout": 10,
        "retry_interval": 5,
        "proxy": {
            "enabled": false,
            "http": "http://proxy.example.com:8080",
            "https": "https://proxy.example.com:8080"
        }
    }
}
```

### Face Detection Settings

```python
{
    "face_detection": {
        "cascade_file": "haarcascade_frontalface_default.xml",
        "scale_factor": 1.1,
        "min_neighbors": 5,
        "min_size": [30, 30],
        "flags": 0
    }
}
```

## Configuration File Locations

1. **Default Configuration**
   - Linux: `~/.config/smart-camera-manager/config.json`
   - Windows: `%APPDATA%\Smart Camera Manager\config.json`
   - macOS: `~/Library/Application Support/Smart Camera Manager/config.json`

2. **Camera Configurations**
   - Stored in `cameras.json` in the same directory

3. **User-Specific Overrides**
   - Can be specified in `user_config.json`

## Configuration Management

### Loading Configurations

```python
from smart_camera_manager import ConfigManager

# Load default configuration
config = ConfigManager.load_default()

# Load specific configuration file
config = ConfigManager.load_file("my_config.json")

# Load with overrides
config = ConfigManager.load_with_overrides("my_config.json", "overrides.json")
```

### Saving Configurations

```python
# Save current configuration
config.save("my_config.json")

# Save with pretty printing
config.save("my_config.json", pretty=True)

# Save as default
config.save_as_default()
```

### Validating Configurations

```python
# Validate configuration
is_valid, errors = config.validate()

if not is_valid:
    print("Configuration errors:", errors)
```

## Best Practices

1. **Camera Configuration**
   - Use meaningful camera names
   - Set appropriate FPS for your needs
   - Enable face detection only when needed

2. **Recording Configuration**
   - Choose quality based on storage capacity
   - Set reasonable segment sizes
   - Configure cleanup policies

3. **Performance Configuration**
   - Adjust thread pool based on CPU cores
   - Set resource limits below system maximum
   - Use hardware acceleration when available

4. **Storage Configuration**
   - Set up cleanup policies
   - Monitor free space
   - Use appropriate naming patterns

## Troubleshooting

1. **Performance Issues**
   - Reduce number of cameras
   - Lower resolution/FPS
   - Disable face detection
   - Check hardware acceleration settings

2. **Recording Issues**
   - Verify FFmpeg installation
   - Check storage permissions
   - Monitor disk space
   - Verify codec availability

3. **Camera Connection Issues**
   - Verify network connectivity
   - Check camera URLs
   - Adjust retry settings
   - Verify camera credentials 