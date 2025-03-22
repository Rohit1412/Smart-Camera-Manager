# API Documentation

Detailed documentation of the Smart Camera Manager's API, including all classes, methods, and their usage.

## Table of Contents
- [Core Classes](#core-classes)
- [Utility Classes](#utility-classes)
- [GUI Components](#gui-components)
- [Hardware Acceleration](#hardware-acceleration)
- [Error Handling](#error-handling)

## Core Classes

### CameraConfig

Configuration class for camera settings.

```python
class CameraConfig:
    def __init__(self, source: Union[str, int], name: str, fps: int = 20,
                 retry_interval: int = 5, buffer_size: int = 24,
                 enable_detection: bool = True)
```

#### Parameters
- `source`: Camera source (URL or device index)
- `name`: Unique camera name
- `fps`: Target frames per second
- `retry_interval`: Seconds between connection retries
- `buffer_size`: Frame buffer size
- `enable_detection`: Enable face detection

#### Methods
- `to_dict()`: Convert config to dictionary
- `from_dict(data)`: Create config from dictionary

### CameraStream

Manages individual camera streams.

```python
class CameraStream:
    def __init__(self, config: CameraConfig)
```

#### Key Methods
- `start()`: Start camera stream
- `stop()`: Stop camera stream
- `get_frame()`: Get latest frame
- `start_recording()`: Start video recording
- `stop_recording()`: Stop video recording
- `get_status()`: Get camera status

#### Properties
- `is_connected`: Connection status
- `recording`: Recording status
- `stream_suppressed`: Stream suppression status

### CameraManager

Manages multiple camera streams.

```python
class CameraManager:
    def __init__(self)
```

#### Methods
- `add_camera(config: CameraConfig)`: Add new camera
- `remove_camera(camera_name: str)`: Remove camera
- `get_all_frames()`: Get frames from all cameras
- `get_all_statuses()`: Get all camera statuses
- `stop_all()`: Stop all cameras
- `optimize_for_camera_count()`: Optimize settings

### VideoRecorder

Handles video recording with FFmpeg.

```python
class VideoRecorder:
    def __init__(self, width: int, height: int, fps: int,
                 output_path: Path, hw_acceleration: dict = None)
```

#### Methods
- `write_frame(frame: np.ndarray)`: Write frame to video
- `start()`: Start recording
- `cleanup()`: Clean up resources

#### Configuration
- `max_segment_duration`: Maximum segment length
- `max_segment_size`: Maximum segment size
- `encoding_preset`: FFmpeg encoding preset
- `quality_crf`: Video quality setting

## Utility Classes

### FPSCounter

Calculates FPS using rolling window.

```python
class FPSCounter:
    def __init__(self, window_size=30)
```

#### Methods
- `update()`: Update frame timing
- `get_fps()`: Get current FPS

### FaceDetector

Handles face detection using Haar Cascades.

```python
class FaceDetector:
    def __init__(self)
```

#### Methods
- `detect_faces(frame: np.ndarray)`: Detect faces in frame

### SystemResourceAnalyzer

Analyzes system capabilities.

```python
class SystemResourceAnalyzer:
    def __init__(self)
```

#### Methods
- `analyze_capacity()`: Analyze system capacity
- `_generate_recommendation()`: Generate recommendations

## GUI Components

### CameraApp

Main application window.

```python
class CameraApp(tk.Tk):
    def __init__(self)
```

#### Key Methods
- `setup_ui()`: Initialize UI components
- `add_camera()`: Add camera dialog
- `remove_camera()`: Remove camera dialog
- `toggle_recording()`: Toggle recording
- `update_loop()`: Main update loop

### ResourceMonitor

Monitors system resources.

```python
class ResourceMonitor(ttk.Frame):
    def __init__(self, parent, camera_manager)
```

#### Methods
- `update_metrics()`: Update resource displays
- `setup_ui()`: Initialize monitor UI

## Hardware Acceleration

### GPUAccelerator

Manages GPU acceleration features.

```python
class GPUAccelerator:
    def __init__(self)
```

#### Methods
- `process_frame()`: Process frame using GPU
- `_cuda_process()`: CUDA processing
- `_opencl_process()`: OpenCL processing

#### Properties
- `cuda_available`: CUDA availability
- `opencl_available`: OpenCL availability

## Error Handling

### Exception Classes

```python
class CameraError(Exception):
    """Base class for camera-related errors"""
    pass

class ConnectionError(CameraError):
    """Camera connection errors"""
    pass

class RecordingError(CameraError):
    """Recording-related errors"""
    pass
```

### Error Recovery

The system implements several error recovery mechanisms:

1. **Connection Recovery**
```python
def _attempt_reconnection(self):
    """Attempt to reconnect to camera with exponential backoff"""
    pass
```

2. **Recording Recovery**
```python
def _handle_recording_error(self):
    """Handle recording errors and attempt recovery"""
    pass
```

## Usage Examples

### Basic Camera Setup
```python
from smart_camera_manager import CameraConfig, CameraManager

# Create camera configuration
config = CameraConfig(
    source="rtsp://camera.local/stream",
    name="Camera 1",
    fps=30,
    enable_detection=True
)

# Initialize manager and add camera
manager = CameraManager()
manager.add_camera(config)
```

### Recording with Hardware Acceleration
```python
from smart_camera_manager import VideoRecorder
from pathlib import Path

# Initialize recorder with NVIDIA acceleration
recorder = VideoRecorder(
    width=1920,
    height=1080,
    fps=30,
    output_path=Path("output.mp4"),
    hw_acceleration={"type": "cuda"}
)

# Start recording
recorder.start()
```

### Face Detection
```python
from smart_camera_manager import FaceDetector
import cv2

# Initialize detector
detector = FaceDetector()

# Process frame
frame = cv2.imread("image.jpg")
faces = detector.detect_faces(frame)

# Draw rectangles around faces
for (x, y, w, h) in faces:
    cv2.rectangle(frame, (x, y), (x+w, y+h), (0, 255, 0), 2)
```

## Best Practices

1. **Resource Management**
   - Always call `stop()` on cameras when done
   - Use context managers when possible
   - Clean up resources properly

2. **Error Handling**
   - Catch specific exceptions
   - Implement proper recovery mechanisms
   - Log errors appropriately

3. **Performance Optimization**
   - Use hardware acceleration when available
   - Monitor system resources
   - Adjust quality settings as needed

4. **Thread Safety**
   - Use locks when accessing shared resources
   - Implement proper synchronization
   - Avoid race conditions

## Contributing to the API

When contributing new features:

1. Follow the existing code style
2. Add proper documentation
3. Include usage examples
4. Add appropriate error handling
5. Write unit tests
6. Update this documentation 