CNN is an advanced version of ANN primarily designed to extract features from grid-like matrix datasets.
Widely used in Computer Vision.

## Stride 
The number of pixels a filter (or kernel) moves across the input image (or feature map) at each step during the convolution operation, controlling how much the filter scans the image.

A stride of 1 means the filter moves one pixel at a time, while a larger stride (like 2 or 3) makes the filter jump, reducing the output spatial dimensions and lowering computational cost but potentially losing fine details

#### Key Aspects of Stride
- Movement: It dictates the step size horizontally and vertically determining the overlap between consecutive filter application.
- **Downsampling:** A stride > 1 effectively downsamples the input, creating a smaller output feature map, which is useful for reducing model size and complexity.
- Default
- Hyperarameter

## Layers

- Input Layer
- Convolution Layer 
- Max Pooling Layer
- Dense Layer
- Output Layer
