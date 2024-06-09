---
layout: post
title: "Cracking the XOR: Testing My Neural Network Library"
date: 2024-06-09
---
One of the fundamental tests for any neural network implementation is the XOR problem. The XOR function is a classic example that demonstrates the limitations of simple linear models, as it cannot be learned with a single linear layer. By solving the XOR problem, I can validate the effectiveness of my neural network library and ensure that it can handle non-linear decision boundaries.

### The XOR Problem

The XOR function takes two binary inputs and outputs a binary value according to the following truth table:

```
Input   | Output
--------|--------
0   0   |  1   0
1   0   |  0   1
0   1   |  0   1
1   1   |  1   0
```

This non-linear function cannot be solved by a single linear model, making it a perfect candidate to test the capabilities of a neural network.

### Setting Up the Experiment

To solve the XOR problem, I set up a neural network with the following architecture:
- **Input Layer:** 2 neurons (corresponding to the two inputs)
- **Hidden Layer:** 2 neurons with Tanh activation
- **Output Layer:** 2 neurons (corresponding to the two outputs)

### Code Implementation

Here's the code I used to train the neural network on the XOR problem:

```python
import numpy as np
from nnet.train import train
from nnet.nn import NeuralNet
from nnet.layers import Linear, Tanh

# Define the inputs and corresponding targets
inputs = np.array([
    [0, 0],
    [1, 0],
    [0, 1],
    [1, 1]
])

targets = np.array([
    [1, 0],
    [0, 1],
    [0, 1],
    [1, 0]
])

# Initialize the neural network with a hidden layer and output layer
net = NeuralNet([
    Linear(input_size=2, output_size=2),
    Tanh(),
    Linear(input_size=2, output_size=2)
])

# Train the neural network on the XOR data
train(net, inputs, targets)

# Test the trained network and print the results
for x, y in zip(inputs, targets):
    predicted = net.forward(x)
    print(x, predicted, y)
```

### Results

After training the neural network, I obtained the following output:

```
[0 0] [ 9.99999996e-01 -4.23385083e-09] [1 0]
[1 0] [3.72591513e-09 1.00000000e+00] [0 1]
[0 1] [6.66842143e-09 1.00000001e+00] [0 1]
[1 1] [ 9.99999996e-01 -4.29201630e-09] [1 0]
```

### Interpreting the Results

The predicted outputs are close to the expected targets:

- For input `[0, 0]`, the predicted output is close to `[1, 0]`.
- For input `[1, 0]`, the predicted output is close to `[0, 1]`.
- For input `[0, 1]`, the predicted output is close to `[0, 1]`.
- For input `[1, 1]`, the predicted output is close to `[1, 0]`.

Although the predictions are not exact (due to the small discrepancies from numerical precision), they are sufficiently close to demonstrate that the neural network has successfully learned the XOR function. The near-zero values indicate high confidence in the predictions.

### Thoughts

Solving the XOR problem with my neural network library was a critical step in validating its functionality. The successful learning of the XOR function, a classic non-linear problem, indicates that this library can handle more complex tasks! This experiment solidified my understanding of neural networks and reinforced the robustness of my implementation.

Next steps include further testing with more complex datasets and exploring additional features to enhance the library's capabilities. Maybe MNNIST? Stay tuned for more updates as I continue to expand and refine my neural network library!