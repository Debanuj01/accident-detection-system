# Model File Required

## Download the YOLOv8 Model

The trained YOLOv8 model file (`best.pt`) is not included in this repository due to its large size (21+ MB).

### How to Get the Model

**Option 1: Train Your Own**
- Use the provided Jupyter notebook: `yolov8_object_detection_on_custom_dataset.ipynb`
- Follow the training instructions
- The trained model will be saved as `best.pt`

**Option 2: Use Pre-trained YOLOv8**
- Download from [Ultralytics YOLOv8](https://github.com/ultralytics/ultralytics)
- Use a pre-trained model for initial testing
- Fine-tune on your accident detection dataset

### Model Placement

Place the `best.pt` file in the root directory of this project:
```
accident-detection-system/
├── best.pt          ← Place model file here
├── main.py
├── app.py
└── ...
```

### Model Requirements

- **Format**: PyTorch (.pt)
- **Framework**: YOLOv8 (Ultralytics)
- **Classes**: Trained on accident detection dataset
- **Size**: ~21 MB

The application will look for `best.pt` in the root directory when it starts.
