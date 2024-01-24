# PyTorch

## Introduction

PyTorch is an open source machine learning library based on the Torch library, used for applications such as computer vision and natural language processing, primarily developed by Facebook's AI Research lab (FAIR). It is free and open-source software released under the Modified BSD license. Although the Python interface is more polished and the primary focus of development, PyTorch also has a C++ interface.

## Installation

Follow the [official website](https://pytorch.org/get-started/previous-versions/).

### Method

### Tensor

A tensor is a generalization of vectors and matrices and is easily understood as a multidimensional array. The PyTorch Tensor API is nearly identical to the NumPy API. If you know how to use NumPy, you already know how to use PyTorch.

Data type | dtype | CPU tensor | GPU tensor
--- | --- | --- | ---
32-bit floating point | torch.float32 or torch.float | torch.FloatTensor | torch.cuda.FloatTensor
64-bit floating point | torch.float64 or torch.double | torch.DoubleTensor | torch.cuda.DoubleTensor
16-bit floating point | torch.float16 or torch.half | torch.HalfTensor | torch.cuda.HalfTensor
8-bit integer (unsigned) | torch.uint8 | torch.ByteTensor | torch.cuda.ByteTensor
8-bit integer (signed) | torch.int8 | torch.CharTensor | torch.cuda.CharTensor
16-bit integer (signed) | torch.int16 or torch.short | torch.ShortTensor | torch.cuda.ShortTensor
32-bit integer (signed) | torch.int32 or torch.int | torch.IntTensor | torch.cuda.IntTensor
64-bit integer (signed) | torch.int64 or torch.long | torch.LongTensor | torch.cuda.LongTensor

- multi-dimensional array
- similar to numpy
- support GPU acceleration
- default data type is float32

#### Initialization

Always copies data:

- torch.tensor()
- torch.Tensor()

Shares data with torch.Tensor():

- torch.as_tensor()
- torch.from_numpy()

```python
import torch
import numpy as np

# Construct a tensor directly from data:
x = torch.tensor([5.5, 3])

x = torch.Tensor([5.5, 3])

x = torch.as_tensor([5.5, 3])

x = torch.from_numpy(np.array([5.5, 3]))
```

#### Basic

```python
import torch

# Construct a 5x3 matrix, uninitialized:
x = torch.empty(5, 3)
print(x)

# Construct a randomly initialized matrix:
x = torch.rand(5, 3)
print(x)

# Construct a matrix filled zeros and of dtype long:
x = torch.zeros(5, 3, dtype=torch.long)
print(x)

# Construct a tensor directly from data:
x = torch.tensor([5.5, 3])
print(x)

# Get its shape:
print(x.shape, x.size())
```

### Check GPU

```python
import torch

print(torch.cuda.is_available())
```

### DataLoader

```text
__init__ : initialize the dataset

__getitem__ : get the data

__len__ : get the length of the dataset

```

```python
import torch
from torch.utils.data import Dataset, DataLoader
from torchvision import transforms

class MyDataset(Dataset):
    def __init__(self):
        # TODO
        pass

    def __getitem__(self, index):
        # TODO
        pass

    def __len__(self):
        # TODO
        pass
    
    def transform(self, image, label):
        # TODO
        pass

dataset = MyDataset()
dataloader = DataLoader(dataset, batch_size=32, shuffle=True, num_workers=4)
```

```python
# example for transform
transform = transforms.Compose([
    transforms.ToTensor(),  # convert to tensor
    transforms.Normalize((0.5,), (0.5,))  # normalize to [-1, 1] with mean 0.5 and std 0.5
])
```

```python
# example for dataloader with next()
dataset = MyDataset()
dataloader = DataLoader(dataset, batch_size=32, shuffle=True, num_workers=4)

# get the first batch
features, labels = next(iter(dataloader))
# get the second batch
features, labels = next(iter(dataloader))
```

### Model

```python
import torch
import torch.nn as nn
import torch.nn.functional as F

class Net(nn.Module):
    def __init__(self):
        super(Net, self).__init__()
        # TODO

    def forward(self, x):
        # TODO
        pass

        
net = Net()
```

#### Layers

Layers are the building blocks of deep learning models.

```python
# Convolutional layer
nn.Conv2d(in_channels, out_channels, kernel_size, stride=1, padding=0, dilation=1, groups=1, bias=True)

# Pooling layer
nn.MaxPool2d(kernel_size, stride=None, padding=0, dilation=1, return_indices=False, ceil_mode=False)

# Linear layer
nn.Linear(in_features, out_features, bias=True)

# Dropout layer
nn.Dropout(p=0.5, inplace=False)

# Batch normalization layer
nn.BatchNorm2d(num_features, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)

# Activation function
nn.ReLU(inplace=False)
nn.LeakyReLU(negative_slope=0.01, inplace=False)
nn.Sigmoid()
nn.Tanh()

# Sequential
nn.Sequential(*args)  # data flows sequentially through the layers

# Flatten
nn.Flatten()  # Reshape the tensor to (batch_size, -1)

# Softmax and Sigmoid
# Softmax is used for multi-classification
# Sigmoid is used for binary-classification
nn.Softmax(dim=None)
nn.Sigmoid() 
```

#### Loss function

Loss function is used to evaluate the performance of the model.

- CrossEntropyLoss: multi-classification
- MSELoss: regression

```python
loss = nn.CrossEntropyLoss()
loss = nn.MSELoss()
```

#### Optimizer

Optimizer is used to update the parameters of the model.

- SGD: Stochastic Gradient Descent
- Adam: Adaptive Moment Estimation

```python
import torch.optim as optim

optimizer = optim.SGD(net.parameters(), lr=0.001, momentum=0.9)
optimizer = optim.Adam(net.parameters(), lr=0.001)
```

#### Gradient

Torch autograd package provides automatic differentiation for all operations on Tensors.

```python
import torch

x = torch.ones(5)  # input tensor
y = torch.zeros(3)  # expected output
w = torch.randn(5, 3, requires_grad=True)
b = torch.randn(3, requires_grad=True)
z = torch.matmul(x, w)+b
loss = torch.nn.functional.binary_cross_entropy_with_logits(z, y)

# compute the gradient
loss.backward()
print(w.grad)
print(b.grad)
```

Stop recording the history on Tensors:

```python
# Using torch.no_grad()
with torch.no_grad():
    pass

# Using detach()
z = torch.matmul(x, w)+b
z_det = z.detach()
```

Reset the gradient if use backward() multiple times:

```python
# Using zero_grad()
# before the backward pass
optimizer.zero_grad()
```

#### Save and load model

```python
# Save
PATH = './Mynet.pth'
torch.save(net.state_dict(), PATH)

# Load
net = Net()
net.load_state_dict(torch.load(PATH))
```

### Training

```python
# example for training
import torch
import torch.nn as nn
import torch.optim as optim
from torch.utils.data import Dataset, DataLoader
from torchvision import transforms

class MyDataset(Dataset):
    def __init__(self):
        # TODO
        pass

    def __getitem__(self, index):
        # TODO
        pass

    def __len__(self):
        # TODO
        pass
    
    def transform(self, image, label):
        # TODO
        pass

class Net(nn.Module):
    def __init__(self):
        super(Net, self).__init__()
        # TODO

    def forward(self, x):
        # TODO
        pass


dataset = MyDataset()
dataloader = DataLoader(dataset, batch_size=32, shuffle=True, num_workers=4)

net = Net()
criterion = nn.CrossEntropyLoss()
optimizer = optim.SGD(net.parameters(), lr=0.001, momentum=0.9)

for epoch in range(2):
    running_loss = 0.0
    for i, data in enumerate(dataloader, 0):
        # get the inputs; data is a list of [inputs, labels]
        inputs, labels = data

        # zero the parameter gradients
        optimizer.zero_grad()

        # forward + backward + optimize
        outputs = net(inputs)
        loss = criterion(outputs, labels)
        loss.backward()
        optimizer.step()

        # print statistics
        running_loss += loss.item()
        if i % 2000 == 1999:    # print every 2000 mini-batches
            print('[%d, %5d] loss: %.3f' %
                  (epoch + 1, i + 1, running_loss / 2000))
            running_loss = 0.0
    
    # save the best model
    if  running_loss < best_loss:
        best_loss = running_loss
        PATH = './Mynet.pth'
        torch.save(net.state_dict(), PATH)

print('Finished Training')
```

## References

[PyTorch筆記](https://hackmd.io/@Kuo-Li-Chen/SJSdUwv65)

[PyTorch org](https://pytorch.org/)

[PyTorch docs](https://pytorch.org/docs/stable/index.html)
