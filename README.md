## MedMambaSE

MedMambaSE is an advanced deep learning model specifically designed for analyzing medical ultrasound images. It builds upon the MedMamba architecture by incorporating Squeeze-and-Excitation (SE) blocks, which enhance the model's ability to recalibrate features dynamically. This addition allows MedMambaSE to emphasize important features while suppressing less useful ones, leading to improved performance in detecting abnormalities.

### Architecture

The architecture of MedMambaSE includes:

- **Patch Embedding:** Converts input images into patch tokens.
- **SS-Conv-SSM Blocks:** Integrates convolutional operations with Selective Scan mechanisms to capture both local and global context.
- **SE Blocks:** Dynamically adjust feature importance to improve sensitivity and specificity.
- **Path Merging:** Gradually reduces spatial dimensions while increasing feature channels, enabling efficient feature extraction.
- **Classifier:** Final layer that outputs class predictions based on processed features.

MedMambaSE is optimized for medical image classification tasks, offering enhanced accuracy and robustness, making it a reliable tool for clinical applications.
