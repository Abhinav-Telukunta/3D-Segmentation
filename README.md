# Aorta Segmentation Using Deep Learning

## Project Overview
Aorta segmentation is a vital task in medical imaging, enabling precise analysis of the aorta's structure and potential pathologies. This project leverages state-of-the-art deep learning architectures to automate the segmentation process, addressing challenges like time-consuming manual annotation, inter-observer variability, and scalability for large datasets. The outcomes of this work have significant implications for improving diagnostic accuracy, surgical planning, and longitudinal studies in cardiovascular diseases.

## Purpose
The primary goal of this project is to evaluate deep learning models for automated multi-class segmentation of the aorta in 3D medical images. Accurate segmentation is essential for assessing conditions such as aneurysms, dissections, and other vascular diseases, ultimately aiding in clinical decision-making and enhancing patient outcomes.

## Dataset
For this project:
- **Data Format**: 50 3D aorta volumes in MHA format.
- **Preprocessing Steps**:
  - Intensity normalization and orientation alignment.
  - Resampling to uniform voxel spacing of (2, 2, 2) mm³.
  - Augmentation (random flipping, rotations) for improved robustness.
- **Training/Validation Split**: 40 volumes for training and 10 volumes for validation.

## Networks Used
The following deep learning architectures were used for aorta segmentation:
1. **U-Net**: A classic encoder-decoder network with skip connections, widely used for precise localization in medical imaging.
2. **V-Net**: An extension of U-Net for volumetric data, employing 3D convolutions for detailed segmentation.
3. **Swin UNETR**: Combines a Swin Transformer encoder with a U-Net decoder for global self-attention and multi-scale feature representation.
4. **CIS U-Net**: Introduces a Context-aware Shifted Window Self-Attention (CSW-SA) mechanism for improved multi-class segmentation.

All models were implemented using the **MONAI** library, except CIS U-Net, which was sourced from its GitHub repository. Training was conducted using the **NVIDIA A100 GPU**, ensuring efficient handling of computationally intensive tasks.

## Metrics
The segmentation performance was evaluated using both qualitative and quantitative metrics:
- **Quantitative Metrics**:
  - **Dice Similarity Coefficient (DSC)**: Measures the overlap between predicted and ground truth segmentations.
  - **Mean Hausdorff Distance (MHD)**: Captures the greatest deviation between segmented boundaries.
  - **Mean Surface Distance (MSD)**: Assesses geometric differences between segmentation surfaces.
- **Qualitative Metrics**: Visual comparisons between predicted and ground truth segmentations to evaluate anatomical accuracy.

### Performance Summary
| Model       | Mean Dice Coefficient (MDC) | Mean Surface Distance (MSD) | Mean Hausdorff Distance (MHD) |
|-------------|-----------------------------|-----------------------------|-------------------------------|
| U-Net       | 0.644                       | 4.333                       | 17.256                        |
| V-Net       | 0.674                       | 3.983                       | 18.931                        |
| Swin UNETR  | 0.659                       | 7.832                       | 35.449                        |
| CIS U-Net   | **0.695**                   | 4.508                       | 23.286                        |

CIS U-Net demonstrated the highest overall performance in terms of the Dice coefficient, achieving accurate segmentation of complex aortic structures. However, V-Net exhibited a better balance of surface and Hausdorff distances.

## Conclusion
This project highlights the potential of deep learning-based segmentation models in automating medical image analysis. CIS U-Net emerged as the most effective model, showcasing its capability to capture intricate details of the aorta and its branches. The results emphasize the importance of leveraging advanced architectures to address clinical challenges.

