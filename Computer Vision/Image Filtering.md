Image Filtering is a process used to modify or improve digital images

It adjusts digital images by applying mathematical operations to each pixel allowing for effects such as smoothing, sharpening or edge detection.

# Some Filteration used by OpenCV

# 1. Identity Kernel

- Simplest and basic kernel operation.
- The output image is exactly as the input.
- Changes the input image
- Its a square matrix with the center element equal to 1. Other elements of the matrix are 0.


```python
img = cv2.imread('input_image.png)
identity_kernel = np.array([
	[0,0,0],
	[0,1,0],
	[0,0,0]
])

identity_img = cv2.filter2D(src=img, depth=-1,kernel=identity_kernel)
show_img('Identity Filter', identity_img)
```

