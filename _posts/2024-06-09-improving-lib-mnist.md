---
layout: post
date: 2024-06-09
title: Improving the library to classify MNIST dataset!
---

## Enhancing My Neural Network Library to Tackle the MNIST Dataset


After building a foundational neural network library from scratch, I decided to put it to the test with a classic machine learning problem: the MNIST handwritten digit classification. This challenge not only validated the robustness of my library but also pushed me to make essential enhancements. Here's a detailed account of my journey and the improvements I made to successfully classify handwritten digits.

### Setting the Stage: The MNIST Dataset
The MNIST dataset is a benchmark in the world of machine learning, consisting of 60,000 training images and 10,000 testing images of handwritten digits from 0 to 9. Each image is a 28x28 pixel grayscale image, which needs to be classified into one of the 10 digit classes.

### Initial Steps and Challenges
My initial setup included basic layers like `Linear` and `Tanh`, which were sufficient for simpler problems. However, the complexity of the MNIST dataset required more sophisticated components. Here are the key areas I focused on:

1. **Adding More Activation Functions:**
   - **ReLU (Rectified Linear Unit):** Popular for hidden layers due to its simplicity and effectiveness in mitigating the vanishing gradient problem.
   - **Softmax:** Essential for the output layer in multi-class classification tasks as it converts logits to probabilities.

1. **Improving Initialization:**
   - Improved the weight initialization to ensure faster convergence by using He initialization.

### Mathematical Explanation

#### ReLU (Rectified Linear Unit)
- **ReLU Function:**
  $$
  \text{ReLU}(x) = \max(0, x)
  $$
  This activation function sets all negative values to zero and keeps positive values unchanged. It introduces non-linearity to the network and helps in mitigating the vanishing gradient problem.

- **ReLU Derivative:**
  $$
  \text{ReLU}'(x) = \begin{cases} 
  1 & \text{if } x > 0 \\
  0 & \text{otherwise}
  \end{cases}
  $$
  This derivative is used during the backpropagation process to update the network's weights.

#### Softmax
- **Softmax Function:**
  $$
  \text{Softmax}(x_i) = \frac{\exp(x_i)}{\sum_{j} \exp(x_j)}
  $$
  This function converts logits into probabilities by exponentiating each logit and normalizing them by the sum of all exponentiated logits. This is particularly useful for multi-class classification problems.

- **Softmax Derivative:**
  $$
  \text{Softmax}'(x) = \text{Softmax}(x) \cdot (1 - \text{Softmax}(x))
  $$
  
  The derivative is used in the backpropagation step to compute the gradients for the loss function with respect to the input logits.



### Updated Layers Implementation
To incorporate these enhancements, I updated my `layers.py` file. Here’s a look at the new additions:

```


```python
def relu(x: Tensor) -> Tensor:
    return np.maximum(0, x)

def relu_prime(x: Tensor) -> Tensor:
    return (x > 0).astype(float)

class ReLU(Activation):
    def __init__(self) -> None:
        super().__init__(relu, relu_prime)

def softmax(x: Tensor) -> Tensor:
    exp_x = np.exp(x - np.max(x, axis=1, keepdims=True))
    return exp_x / np.sum(exp_x, axis=1, keepdims=True)

def softmax_prime(x: Tensor) -> Tensor:
    sm = softmax(x)
    return sm * (1 - sm)

class Softmax(Activation):
    def __init__(self) -> None:
        super().__init__(softmax, softmax_prime)

```
