## MedMambaSE

MedMambaSE is an advanced deep learning model specifically designed for analyzing medical ultrasound images. It builds upon the MedMamba architecture by incorporating Squeeze-and-Excitation (SE) blocks, which enhance the model's ability to recalibrate features dynamically. This addition allows MedMambaSE to emphasize important features while suppressing less useful ones, leading to improved performance in detecting abnormalities.

### Architecture

The architecture of MedMambaSE includes:

- **Patch Embedding:** Converts input images into patch tokens.
- **SS-Conv-SSM Blocks:** Integrates convolutional operations with Selective Scan mechanisms to capture both local and global context.
- **SE Blocks:** Dynamically adjust feature importance to improve sensitivity and specificity.
- **Path Merging:** Gradually reduces spatial dimensions while increasing feature channels, enabling efficient feature extraction.
- **Classifier:** Final layer that outputs class predictions based on processed features.

![MedMambaSE Architecture](https://github.com/Tanjim-Islam/MedMambaSE/blob/7b450c975e07a454322167b9d3cdc93e77609980/images/architecture.png)


MedMambaSE is optimized for medical image classification tasks, offering enhanced accuracy and robustness, making it a reliable tool for clinical applications.

## How to use

Make a folder named "data" then make 3 different folders "train", "val", "test" in it. Then keep your image files there.

### Installation

```
pip install -r requirements.txt
```

### Requirements

- Python == 3.10
- Windows
- Pytorch == 2.1.0
- einops==0.7.0
- hydra-core==1.3.2
- numpy==1.26.4
- omegaconf==2.3.0
- timm==0.9.16
- tqdm==4.65.0
- CUDA == 11.2 (For Windows specifically)
