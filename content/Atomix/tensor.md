# Tensor

A tensor is just a multi-dimensional array of numbers.

- **scalar** = single number
- **vector** = 1D array
- **matrix** = 2D array
- **tensor** = 3D or higher-dimensional array, or more generally multi-dimensional data

So tensor operations are computations done on such arrays, for example:
- tensor addition
- tensor multiplication
- matrix multiply
- convolution-like multiply-accumulate work
- reshaping / transpose / reduction

In AI, tensors are used because data like images, feature maps, weights, activations, and batches of inputs are naturally stored as multi-dimensional arrays.

## Why tensor operations matter here

AI workloads spend a lot of time doing repeated math like:
- multiply many numbers
- add partial sums
- move lots of structured data through memory
