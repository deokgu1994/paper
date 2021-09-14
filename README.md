## U-Net: Convolutional Networks for Biomedical Image Segmentation
### Paper [Link](https://arxiv.org/pdf/1505.04597.pdf)
___

## 1. Introduction
![image](https://user-images.githubusercontent.com/35412566/133273916-1613b98a-d150-491e-b722-e3a5a1ab0f06.png)
###### fig 2. Overlap-tile strategy for seamless segmentation of arbitrary large images (here segmentation of neuronal structures in EM stacks)<br><br>
This strategy allows the seamless segmentation of arbitrarily large images by an overlap-tile strategy To predict the pixels in the border region of the image, the missing context is extrapolated by mirroring the input image.  This tiling strategy is important to apply the network to large images, since otherwise the resolution would be limited by the GPU memory. [paper 3page]


## 2. Network Architecture 
![image](https://user-images.githubusercontent.com/35412566/133272129-3870a0e1-2bc7-4a5e-8d56-9bc4d70f39bb.png)
###### fig 1. U-net architecture<br><br>

It consists of a contracting path (left side) and an expansive path (right side).
<br><br>
contracting path는 It consists of the repeated application of two 3x3 convolutions (unpadded convolutions), each followed by a rectified linear unit (ReLU) and a 2x2 max pooling operation with stride 2 for downsampling. At each downsampling step we double the number of feature channels<br>
<br>
Every step in the expansive path consists of an upsampling of the feature map followed by a 2x2 convolution (“up-convolution”) that halves the number of feature channels,a concatenation with the correspondingly cropped feature map from the contracting path, and two 3x3 convolutions, each followed by a ReLU [paper 4page]
<br>

Q. 그래서 tiling은 어떻게 적용하는 걸까?

## 3. Training
To minimize the overhead and make maximum use of the GPU memory, we favor large input tiles over a large batch size and hence reduce the batch to a single image. Accordingly we use a high **momentum (0.99)** such that a large number of the previously seen training samples determine theupdate in the current optimization step
<br>

### 3.1 Data Augmentation

**We generate smooth deformations using random displacement vectors on a coarse 3 by 3 grid. The displacements are sampled from a Gaussian distribution with 10 pixels standard deviation.** Per-pixel displacements are then computed using bicubic interpolation. Drop-out layers at the end of the contracting path perform further implicit data augmentation.
<br>



