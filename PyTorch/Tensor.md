# Tensor
numpy - ndarray $\approx$ PyTorch - Tensor
## Tensor 생성
### list 나 ndarray 통해서; tensot(), ~Tensor(), from_numpy(), as_tensor()
```python
import numpy as np
import torch

ndarray = np.arange(12).reshape(3,4)


tensor = torch.FloatTensor(ndarray)

tensor
# tensor([[0., 1., 2., 3.], [4., 5., 6., 7.], [8., 9., 10., 11,]])
tensor.ndim
# 2
tensor.shape
# (3, 4)

tensor2 = torch.from_numpy(ndarray)
# tensor([[ 0,  1,  2,  3],[ 4,  5,  6,  7], [ 8,  9, 10, 11]])

data = [[0, 1], [2, 3]]

tensor3 = torch.tensor(data)
```
`tensor()` 는 data 를 copy 하므로 numpy array 를 copy 하고 싶지 않다면 `torch.from_numpy()`나 `torch.as_tensor()` 를 사용한다.

```python
my_array = np.zeros(shape=(3,3), dtype=float)
my_tensor = torch.as_tensor(my_array)

my_tensor
"""
tensor([[0., 0., 0.],
        [0., 0., 0.],
        [0., 0., 0.]], dtype=torch.float64)
"""

my_array[0][0] = 1

my_tensor
"""
tensor([[1., 0., 0.],
        [0., 0., 0.],
        [0., 0., 0.]], dtype=torch.float64)
"""
```
### rand 를 통해서 생성
```python
tensor4 = torch.rand(size=(3,3))
tensor4
# tensor([[0.3881, 0.6196, 0.8375], [0.8043, 0.6016, 0.2739], [0.2926, 0.9907, 0.2605]])
```
## Tensor 수정하기

### view, reshape
```python
tensor.shape
# (3, 4)
tensor.view([-1, 2])
"""
tensor([[ 0,  1],
        [ 2,  3],
        [ 4,  5],
        [ 6,  7],
        [ 8,  9],
        [10, 11]], dtype=torch.int32)
"""

tensor.reshape([4, 3])
"""
tensor([[ 0,  1,  2],
        [ 3,  4,  5],
        [ 6,  7,  8],
        [ 9, 10, 11]], dtype=torch.int32)
"""
```
`view()` 는 copy 를 한 것이 아니라 메모리 주소를 그대로 가져와서 형태만 바꿔준다. 그래서 원본 tensor 를 수정하면 `view()` 로 형태를 바꾼 tensor 의 data 도 바뀐다.
`reshape()` 는 copy 를 한다.
## Tensor 연산
### 행렬곱; mm(matmul)
pytorch 에서 `dot()` 은 벡터의 내적만, `mm()` 은 행렬곱만 지원한다.
```python
tensor4.shape
# (3, 3)
tensor.shape
# (3, 4)

tensor4.dot(tensor)
# RuntimeError: 1D tensors expected, but got 2D and 2D tensors

tensor4.mm(tensor)
"""
tensor([[ 9.1786, 11.0239, 12.8691, 14.7144],
        [ 4.5974,  6.2771,  7.9569,  9.6367],
        [ 6.0466,  7.5904,  9.1342, 10.6780]])
"""
```
`mm()` 은 broadcasting 을 지원하지 않고, `matmul()` 은 broadcasting 을 지원한다.

## nn.functional 모듈
```python
import torch.nn.functional as F

x = torch.FloatTensor([[0.6, 0.72, 0.8], [0.3, 0.5, 0.6]])
h_tensor = F.softmax(x, dim = 0)
"""
tensor([[0.5744, 0.5548, 0.5498],
        [0.4256, 0.4452, 0.4502]])
"""
```

## 그 외 속성과 메소드
numpy 의 것과 비슷하게 사용할 수 있다.
1. 인덱싱
2. flatten(), size(), ~\_like()
3. shape, dtype
등등

