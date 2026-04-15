# ⚙️ Setup & Installation

**Prerequisites**

- Python 3.10+
- Google Colab account (recommended for GPU acceleration)
- Kaggle or local maize dataset organised into binary classes:

```txt

dataset/
├── train/
│   ├── good/
│   └── bad/ 

```

**Local Environment (Optional)**

If running locally on Linux:

```bash
# Install dependencies

pip install tensorflow tensorflowjs scikit-learn matplotlib
```

# 📈 Training Workflow

1. **Data Loading**: Uses `ImageDataGenerator` with a 20% validation split. Images are rescaled and resized to `128x128`.
2. **Model Architecture**:
    - Base: MobileNetV2 (weights: ImageNet, include_top: False)
    - Head: GlobalAveragePooling2D -> Dense (128, ReLU) -> Dense (1, Sigmoid)
3. **Compilation**:
    - Optimizer: Adam
    - Loss: Binary Crossentropy
    - Metrics: Accuracy, Precision, Recall
4. **Monitoring**: Launch TensorBoard to watch the training progress:

```py
%load_ext tensorboard
%tensorboard --log_dir logs
```