## MedMambaSE

MedMambaSE is an advanced deep learning model specifically designed for analyzing medical ultrasound images. It builds upon the MedMamba architecture by incorporating Squeeze-and-Excitation (SE) blocks, which enhance the model's ability to recalibrate features dynamically. This addition allows MedMambaSE to emphasize important features while suppressing less useful ones, leading to improved performance in detecting abnormalities.

### Architecture

The architecture of MedMambaSE includes:

- **Patch Embedding:** Converts input images into patch tokens.
- **SS-Conv-SSM Blocks:** Integrates convolutional operations with Selective Scan mechanisms to capture both local and global context.
- **SE Blocks:** Dynamically adjust feature importance to improve sensitivity and specificity.
- **Path Merging:** Gradually reduces spatial dimensions while increasing feature channels, enabling efficient feature extraction.
- **Classifier:** Final layer that outputs class predictions based on processed features.

![MedMambaSE Architecture](https://github.com/Tanjim-Islam/MedMambaSE/blob/master/images/architecture.png)


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

### Feature Recalibration with SE Blocks

One of the standout features of MedMambaSE is its use of Squeeze-and-Excitation (SE) blocks to achieve feature recalibration. This process involves dynamically adjusting the importance of different feature maps, enabling the model to focus on the most relevant aspects of the input data. 

#### How SE Blocks Work

1. **Squeeze:** The spatial dimensions of the input feature maps are reduced using global average pooling, resulting in a vector of size equal to the number of channels.
2. **Excitation:** This vector is passed through two fully connected (FC) layers with a ReLU activation and a sigmoid activation, producing a set of channel-wise weights.
3. **Recalibration:** These weights are then used to scale the original feature maps, emphasizing important features and suppressing less useful ones.

By integrating SE blocks, MedMambaSE can effectively recalibrate its features, enhancing its ability to detect abnormalities in medical ultrasound images. This feature recalibration improves the sensitivity and specificity of the model, leading to better performance in medical image classification tasks.

The image below illustrates the effect of SE blocks on the feature maps:

![Feature Recalibration](https://github.com/Tanjim-Islam/MedMambaSE/blob/master/images/recalibration.png)

On the left, we see the feature maps before applying the SE block, and on the right, the feature maps after applying the SE block. Notice how the SE block enhances important features, making the model more effective in its analysis.

### Training and Evaluation

For our proposed model (MedMambaSE), we have employed the Adam optimizer with a learning rate of 0.001, weight decay of 1e-4, $\beta_1 = 0.9$, and $\beta_2 = 0.999$. We used Cross Entropy Loss to optimize the model parameters and trained the dataset for 20 epochs with a batch size of 16. Due to resource limitations, we did not use data augmentation techniques or pre-trained weights to assess the model's original performance. The training was conducted on a system with Windows 11 and an NVIDIA GeForce RTX 4090 GPU.

### Summary of Experimental Setup for MedMambaSE

| **Experimental Setup**     | **Details**                                   |
| -------------------------- | --------------------------------------------- |
| Operating System            | Windows 11                                    |
| GPU Accelerators            | NVIDIA GeForce RTX 4090                       |
| CPU                         | 13th Gen Intel(R) Core(TM) i9-13900K          |
| DL Framework                | PyTorch                                       |
| Optimizer                   | Adam (learning rate = 0.001, weight decay = 1e-4, $\beta_1 = 0.9$, $\beta_2 = 0.999$) |
| Loss Function               | Cross Entropy Loss                            |
| Epochs                      | 20                                            |
| Batch Size                  | 16                                            |
| Image Size                  | 128                                           |
| Additional Techniques       | No data augmentation                          |
|                             | No pre-trained weights used                   |

### Model Performance

MedMambaSE was trained for 20 epochs with early stopping. Initially, the training accuracy was 55.39% and validation accuracy was 51.37%. By the final epoch, training accuracy improved to 90.6% and validation accuracy reached 87.21%. Training loss decreased consistently, indicating effective optimization, but performance remained below 90%, likely due to the limited number of epochs.

![MedMambaSE Performance](https://github.com/Tanjim-Islam/MedMambaSE/blob/master/images/medSE.png)

### Accuracy Comparison

We compared MedMambaSE's performance with other models, as shown in the table below:

| **Model**        | **Training Accuracy (%)** | **Test Accuracy (%)** | **Validation Accuracy (%)** |
| ---------------- | ------------------------- | ---------------------- | --------------------------- |
| Swin Transformer | 88.61                      | 73.95                  | 75.5                         |
| MedMamba         | 87.56                      | 81.2                   | 83.49                        |
| **MedMambaSE**   | **90.6**                   | **84.23**              | **87.21**                    |
