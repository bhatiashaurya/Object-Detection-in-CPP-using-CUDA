# YOLOv8 Object Detection with OpenCV + ONNX + CUDA (Windows)

This project demonstrates real-time object detection using the YOLOv8 ONNX model with OpenCV's DNN module accelerated by CUDA.

## 🚀 Features

- 🧠 YOLOv8 (nano) ONNX model  
- 🖥️ Real-time webcam input  
- ⚡ CUDA-accelerated inference (OpenCV DNN + CUDA)  
- 🛠️ C++ implementation with OpenCV 4.11  
- 🧱 Built using CMake and Visual Studio on Windows  

## 🧾 Project Structure

```
/self
├── main.cpp                # Core object detection code
├── yolov8n.onnx            # YOLOv8 ONNX model file
├── coco.names              # COCO dataset class names
├── CMakeLists.txt          # Build configuration
└── README.md               # This file
```

## 🛠️ Requirements

- CUDA Toolkit 12.8  
- cuDNN for CUDA 12.8  
- Visual Studio 2019 or later  
- CMake 3.10+  
- OpenCV 4.11 (built from source with CUDA and DNN support)  

## 🧰 Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/object-detection-onnx-cuda.git
cd object-detection-onnx-cuda
```

### 2. Download YOLOv8n ONNX Model

```bash
wget https://github.com/ultralytics/assets/releases/download/v0.0.0/yolov8n.onnx
```

Or download it manually from https://github.com/ultralytics/ultralytics

### 3. Add Class Names

Create a file called coco.names with the 80 class names from the COCO dataset or download from:  
https://github.com/pjreddie/darknet/blob/master/data/coco.names

### 4. Build OpenCV with CUDA (if not already)

Clone OpenCV and OpenCV_contrib and configure with CMake:

```bash
cmake -D WITH_CUDA=ON ^
      -D WITH_CUDNN=ON ^
      -D OPENCV_DNN_CUDA=ON ^
      -D BUILD_opencv_world=ON ^
      -D CUDA_ARCH_BIN=8.6 ^
      -D CMAKE_BUILD_TYPE=Release ^
      -D CMAKE_INSTALL_PREFIX=C:/opencv/opencv/build/install ..
```

Build with:

```bash
cmake --build . --config Release --target INSTALL
```

## 🧪 Build This Project

### 1. Make Sure Paths Are Set in CMakeLists.txt

- OpenCV_DIR = "C:/opencv/opencv/build/x64/vc16/lib"
- ONNXRUNTIME_DIR = "D:/onnxruntime-windows-x64-gpu-1.17.0"
- CUDA Toolkit = "C:/Program Files/NVIDIA GPU Computing Toolkit/CUDA/v12.8"

### 2. Build with CMake

```bash
mkdir build
cd build
cmake ..
cmake --build . --config Release
```

## ▶️ Run the Program

```bash
./object_detection.exe
```

It will launch your default webcam and run detection in real-time using CUDA.

## ⚠️ Troubleshooting

- Make sure cuDNN and CUDA versions match (both should be 12.8)  
- Rebuild OpenCV with CUDA support if DNN_BACKEND_CUDA errors occur  
- Ensure all DLLs (onnxruntime + OpenCV + CUDA) are discoverable in PATH  

## 📄 Model Info

| Model     | Format | Size | Speed (CUDA) |
|-----------|--------|------|--------------|
| YOLOv8n   | ONNX   | ~6MB | ~30 FPS      |

## 📸 Example Output

You can include a sample screenshot here to show live detection:

```
docs/sample_output.png
```

## 📜 License

This project is licensed under the MIT License.

## 🙋‍♂️ Credits

- [Ultralytics](https://github.com/ultralytics) for YOLOv8  
- OpenCV contributors  
- Microsoft ONNX Runtime

## 📬 Contact

Feel free to open an issue or discussion if you run into problems or want to suggest improvements.
