
2025-12-10

Tags: [[Data Mining and Machine Learning]] [[Data]]
# Convolutional Neural Networks
CNN's are used for comparing data where each data point is a vector, the most obvious example is for learning on image data. This is a very hard problem, so part of how CNN's work is by searching for specific smaller problems such as a birds beak.

**Why CNN's:**
- Locality
	- Network should focus on local regions, without regard for the contents of the image in distant regions
	-  These local representations can be aggregated to make predictions at the whole image level
- Translation invariance
	- Network should respond similarly to the same patch, regardless of where it appears in the image
- Subsampling
	- Less parameters for the network to process the image

## Structure
---
![[Pasted image 20251210184348.png]]
#### Convolution Layer
- The convolution layer uses filters that perform convolution operations, it scans the input 𝐼 with respect to its dimensions.
- Its hyper-parameters include the filter size 𝐹 and stride 𝑆.
- The resulting output 𝑂 is called feature map or activation map.
- The idea is that each filter detects a small feature

**Padding:** add extra pixels of filler around the boundary of our input image, thus increasing the effective size of the image. This information is just nulls/0's, but it allows us to slide our "window" to include bits at the very edge of the image

**Stride:** the number of rows and columns traversed per slide as the stride. A good way to think of this is if I have a spyglass/telescope and I am spinning in a circle, stride is how many degrees I move each time after an observation.

#### Fully Connected vs Convolution
![[Pasted image 20251210185243.png]]
In a fully connected node every single node is directly connected via weights to the output, while convolution is a number of views "combined" into each other.

#### Pooling Layer
Pooling is a way of taking an input and turning it into a smaller input that can be easier / less expensive for a model to work with.

**Max Pooling:**
- For each view of the array we select the maximum value in that view to compress
- This version preserves features since we aren't altering the raw values
- Most commonly used pooling strategy

**Average Pooling:**
- Each pooling operation averages the values in the current view
- Down samples the feature map
- used in LeNet (historical)

#### Flattening
Flattening is when we take our various arrays of inputs and literally flatten them, essentially just lining them up in a row to be used as an input in a neural network. For example if we have a 2d array with a fixed size width we can represent it as a 1d array and just translate the way we access it, same exact thing.

## Building a CNN
Keep the feature space wide and shallow in the initial stages of the network, and
then make it narrower and deeper towards the end.

1. Start by using smaller filters to collect as much local information as possible.
2. Gradually increase the filter width to reduce the generated feature space width to represent more global, high-level and representative information.
3. Use `3x3`, `5x5`, and `7x7` filter sizes for the convolutional layers for a moderate or small-sized image with a stride of 2. Stride is the number of pixels shifts over the input matrix, e.g., when the stride is 1 then we move the filters 1 pixel at a time.
4. Use `2x2` or `3x3` filter sizes for Max Pooling.
5. Larger filter sizes and strides may be used to shrink a large image to a moderate size and then go further as described above.
6. Use classic networks like MobileNet, ShuffleNet, LeNet, AlexNet, VGG-16, VGG- 19 etc. as inspirations while building the architectures for your models.

[More Details](https://towardsdatascience.com/a-guide-to-an-efficient-way-to-build-neural-network-architectures-part-ii-hyper-parameter-42efca01e5d7)
[More Details](https://towardsdatascience.com/mnist-cnn-python-c61a5bce7a19)
- [Built on Keras](https://keras.io/)
# References
[[Neural Networks]]

[[Loss Functions]]