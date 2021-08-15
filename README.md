# Export paths:

```bash
export WEIGHTS="/mnt/2B59B0F32ED5FBD7/Projects/KIKAI/model-zoo/nobi_model_v2/scaled_nobi_pose_v2.weights"
export NAMES="/mnt/2B59B0F32ED5FBD7/Projects/KIKAI/model-zoo/nobi_model_v2/scaled_nobi_pose_v2.names"
export CFG="/mnt/2B59B0F32ED5FBD7/Projects/KIKAI/model-zoo/nobi_model_v2/scaled_nobi_pose_v2.cfg"
export SAVE_DIR="/mnt/2B59B0F32ED5FBD7/Projects/KIKAI/AlphaPose/nobi-hw-videocapture/EMoi///"
export ENGINE="/mnt/2B59B0F32ED5FBD7/Projects/KIKAI/model-zoo/nobi_model_v2/scaled_nobi_pose_v2.engine"
export ALPHAPOSE_MODEL="/mnt/2B59B0F32ED5FBD7/Projects/KIKAI/AlphaPose/AlphaPose_TorchScript/model-zoo/fast_pose_res50/fast_res50_256x192.jit"
```

# Streamming

## Build Streamming 4 Camera Test

```bash
rm -rf .cmake/ *
cmake -DFOUR_CAMS=ON -DCAM_ID_EXAMPLES=ON ..
cmake --build . --config Release
./Nobi_App
```

## Build Streamming 4 Video Source Test

```bash
rm -rf .cmake/ *
cmake -DFOUR_CAMS=ON -DVIDEO_EXAMPLES=ON ..
cmake --build . --config Release
./Nobi_App
```

## Build Streaming From Camera Test

```bash
rm -rf .cmake/ *
cmake -DSINGLE_CAM=ON -DCAM_ID_EXAMPLES=ON ..
cmake --build . --config Release
./Nobi_App
```

## Build Streaming From Video Soure Test

```bash
rm -rf .cmake/ *
cmake -DSINGLE_CAM=ON -DVIDEO_EXAMPLES=ON ..
cmake --build . --config Release
./Nobi_App
```

# Video Inference

## Build test object detection by TensorRT model on a sample video path like darknet


```bash
rm -rf .cmake/ *
cmake -DINFERENCE_VIDEO=ON ..
cmake --build . --config Release
./Nobi_App
```

## Build test object detection by darknet C++ model on a sample video path like darknet

```bash
rm -rf .cmake/ *
cmake -DINFERENCE_VIDEO=ON -DINFERENCE_DARKNET=ON -DVIDEO_EXAMPLES=ON ..
cmake --build . --config Release
./Nobi_App
```

## Build test object detection by TensorRT model on a sample video path like darknet, and support pose estimation

```bash
rm -rf .cmake/ *
cmake -DINFERENCE_VIDEO=ON -DVIDEO_EXAMPLES=ON -DINFERENCE_ALPHAPOSE_TORCH=ON ..
cmake --build . --config Release
./Nobi_App
```

## Build test object detection by darknet C++ model on a sample video path like darknet, and support pose estimation

```bash
rm -rf .cmake/ *
cmake -DINFERENCE_VIDEO=ON -DINFERENCE_DARKNET=ON -DVIDEO_EXAMPLES=ON -DINFERENCE_ALPHAPOSE_TORCH=ON ..
cmake --build . --config Release
./Nobi_App
```

# API like darknet

## Build test object detection by TensorRT model on a sample video path like darknet

```bash
rm -rf .cmake/ *
cmake -DTENSORRT_API=ON ..
cmake --build . --config Release
./Nobi_App --engine-file ${ENGINE} --label-file ${NAMES} --dims 512 512 --obj-thres 0.7 --nms-thres 0.7 --type-yolo csp --dont-show
```

## Build test object detection by darknet C++ model on a sample video path like darknet

```bash
rm -rf .cmake/ *
cmake -DTENSORRT_API=ON -DINFERENCE_DARKNET=ON ..
cmake --build . --config Release
./Nobi_App --weights-file ${WEIGHTS} --cfg-file ${CFG} --names-file ${NAMES} --thresh 0.7 --dont-show
```

## Build test object detection by TensorRT model on a sample video path like darknet, and support pose estimation

```bash
rm -rf .cmake/ *
cmake -DTENSORRT_API=ON -DINFERENCE_ALPHAPOSE_TORCH=ON ..
cmake --build . --config Release
./Nobi_App --engine-file ${ENGINE} --label-file ${NAMES} --alphapose-jit ${ALPHAPOSE_MODEL} --dims 512 512 --obj-thres 0.7 --nms-thres 0.7 --type-yolo csp --dont-show
```

## Build test object detection by darknet C++ model on a sample video path like darknet, and support pose estimation

```bash
rm -rf .cmake/ *
cmake -DTENSORRT_API=ON -DINFERENCE_DARKNET=ON -DINFERENCE_ALPHAPOSE_TORCH=ON ..
cmake --build . --config Release
./Nobi_App --weights-file ${WEIGHTS} --cfg-file ${CFG} --names-file ${NAMES} --alphapose-jit ${ALPHAPOSE_MODEL} --thresh 0.7 --dont-show
```

# Nobi API

## Build Nobi API support object detection TensorRT

```bash
rm -rf .cmake/ *
cmake -DNOBI_CAMERA_AI_API=ON -DVIDEO_EXAMPLES=ON ..
cmake --build . --config Release
./Nobi_App --engine-file ${ENGINE} --label-file ${NAMES} --save-dir ${SAVE_DIR} --dims 512 512 --obj-thres 0.7 --nms-thres 0.7 --type-yolo csp --dont-show
```

## Build Nobi API support object detection darknet C++

```bash
rm -rf .cmake/ *
cmake -DNOBI_CAMERA_AI_API=ON -DINFERENCE_DARKNET=ON -DVIDEO_EXAMPLES=ON ..
cmake --build . --config Release
./Nobi_App --weights-file ${WEIGHTS} --cfg-file ${CFG} --names-file ${NAMES} --save-dir ${SAVE_DIR} --thresh 0.7 --dont-show
```

## Build Nobi API support object detection TensorRT and pose estimation

```bash
rm -rf .cmake/ *
cmake -DNOBI_CAMERA_AI_API=ON -DVIDEO_EXAMPLES=ON -DINFERENCE_ALPHAPOSE_TORCH=ON ..
cmake --build . --config Release
./Nobi_App --engine-file ${ENGINE} --label-file ${NAMES} --alphapose-jit ${ALPHAPOSE_MODEL} --save-dir ${SAVE_DIR} --dims 512 512 --obj-thres 0.7 --nms-thres 0.7 --type-yolo csp --dont-show
```

## Build Nobi API support object detection darknet C++ and pose estimation

```bash
rm -rf .cmake/ *
cmake -DNOBI_CAMERA_AI_API=ON -DINFERENCE_DARKNET=ON -DVIDEO_EXAMPLES=ON -DINFERENCE_ALPHAPOSE_TORCH=ON ..
cmake --build . --config Release
./Nobi_App --weights-file ${WEIGHTS} --cfg-file ${CFG} --names-file ${NAMES} --alphapose-jit ${ALPHAPOSE_MODEL} --save-dir ${SAVE_DIR} --thresh 0.7 --dont-show
```

