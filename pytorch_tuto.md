* Fonction ending with _ like add_ modify inplace a tensor. For example add is different from add_.

* you can switch with numpy with : 

  ```python
  a = torch.ones(5)
  b = a.numpy()
  print(b)
  a.add_(1)
  print(a)
  print(b) 	# see how the numpy array changed in value

  import numpy as np
  a = np.ones(5)
  b = torch.from_numpy(a)
  np.add(a, 1, out=a)

  ```

  # CudaTensor

* ```python
  # let us run this cell only if CUDA is available
  if torch.cuda.is_available():
      # creates a LongTensor and transfers it
      # to GPU as torch.cuda.LongTensor
      a = torch.LongTensor(10).fill_(3).cuda()
      print(type(a))
      b = a.cpu()
      # transfers it to CPU, back to
      # being a torch.LongTensor
  ```

  # Autograd

```python
import torch
from torch.autograd import Variable

x = torch.randn(3)
x = Variable(x, requires_grad=True)

y = x * 2
while y.data.norm() < 1000:
    y = y * 2

print(y)
print(y.creator)

gradients = torch.FloatTensor([0.1, 1.0, 0.0001])
y.backward(gradients)

print(x.grad)
```



# NN

Define a class that inherit(nn.Module). _ini should extend nn.Module _init by calling super(MNISTConvNet self).init()

It also has to define a forward function.



```python
import torch
from torch.autograd import Variable
import torch.nn as nn
import torch.nn.functional as F


class MNISTConvNet(nn.Module):

    def __init__(self):
        # this is the place where you instantiate all your modules
        # you can later access them using the same names you've given them in
        # here
        super(MNISTConvNet, self).__init__()
        self.conv1 = nn.Conv2d(1, 10, 5)
        self.pool1 = nn.MaxPool2d(2, 2)
        self.conv2 = nn.Conv2d(10, 20, 5)
        self.pool2 = nn.MaxPool2d(2, 2)
        self.fc1 = nn.Linear(320, 50)
        self.fc2 = nn.Linear(50, 10)

    # it's the forward function that defines the network structure
    # we're accepting only a single input in here, but if you want,
    # feel free to use more
    def forward(self, input):
        x = self.pool1(F.relu(self.conv1(input)))
        x = self.pool2(F.relu(self.conv2(x)))

        # in your model definition you can go full crazy and use arbitrary
        # python code to define your model structure
        # all these are perfectly legal, and will be handled correctly
        # by autograd:
        # if x.gt(0) > x.numel() / 2:
        #      ...
        #
        # you can even do a loop and reuse the same module inside it
        # modules no longer hold ephemeral state, so you can use them
        # multiple times during your forward pass
        # while x.norm(2) < 10:
        #    x = self.conv1(x)

        x = x.view(x.size(0), -1)
        x = F.relu(self.fc1(x))
        x = F.relu(self.fc2(x))
        return x
```

# Optim

```python
import torch.optim as optim

# create your optimizer
optimizer = optim.SGD(net.parameters(), lr=0.01)

# in your training loop:
optimizer.zero_grad()   # zero the gradient buffers
output = net(input)
loss = criterion(output, target)
loss.backward()
optimizer.step()    # Does the update
```



# torchVision

# Visdom

```shell
 python -m visdom.server
```

```python
import visdom
vis = visdom.Visdom()
vis.image(tensor.numpy())
```