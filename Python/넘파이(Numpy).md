# Numpy
**Python 의 고성능 과학 계산용 패키지로 Array 연산의 표준이다**. 따라서 매우매우 중요하다.

## ndarray
numpy 를 이용해 생성하는 array 로 Java 와 마찬가지로 하나의 자료형만 사용할 수 있다. 자료형은 배열을 생성할 때 지정한다.
```python
import numpy as np
ndarray = np.array(['A', 'B', 'C', 7], np.str)

print(ndarray)
# ['A', 'B', 'C', '7']
type(ndarray)
# <class 'numpy.ndarray'>
```

### ndarray 의 속성들
```python
ndarray = np.array([[1, 2],[2, 3],[3, 4],[4, 5],[5, 6]], float)

print(ndarray)
# [1. 2. 3. 4. 5.]

ndarray.dtype # 데이터 타입
# dtype('float64')

ndarray.shape # 배열의 형태
# (5, 2)

ndarray.ndim # 배열의 차원(rank)
# 2

ndarray.size # 원소의 개수
# 10

ndarray[np.newaxis] # ndarray 에 새로운 축 추가
# array([[[1., 2.], [2., 3.], [3., 4.], [4., 5.], [5., 6.]]])

ndarray[np.newaxis].shape
# (1, 5, 2) aixs=2 가 추가된 것을 볼 수 있다.
```

### ndarray 의 메소드
#### reshape
array 의 형태를 바꿔주는 메소드인데, element 의 개수는 유지되므로 reshape를 사용할 때는 size 에 유의하는 게 좋을 것 같다.
원소 순서대로 reshape 가 되는데 axis=0 이나 aixs=1 기준으로 reshape 를 할 수는 없는지 궁금해 찾아보니 정수 외의 다른 attribute 를 받는 경우는 없었다.
```python
ndarray = np.array([[1, 2],[2, 3],[3, 4],[4, 5],[5, 6]], float)

ndarray.size # 10

reshape_array = ndarray.reshape(2,5)
# [[1, 2, 2, 3, 3], [4, 4, 5, 5, 6]]

# size 를 계산하기 어렵거나 귀찮을 경우
ndarray.reshape(-1, 5) # -1 을 사용하면 size 에 맞게 숫자를 조정해준다.
```

#### flatten
말 그대로 평평하게 즉, 1차원 array 로 shape 를 바꿔주는 메소드.
```python
my_array = np.array([[[1,2],[3,4]],[[5,6],[7,8]],[[9,10],[11,12]]], dtype=np.int8)

my_array.shape
(3,2,2)

my_array.flatten()
# array([ 1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12], dtype=int8)

my_array.flatten().shape
# (12,)
```

#### vstack, hstack, concatenate
vertical stack, horizontal stack 는 각각 세로 방향, 가로 방향으로 행렬을 붙여준다. concatenate 는 axis attribute 를 사용해 붙이는 방향을 정할 수 있다.

### ndarray 의 Indexing
ndarray 는 \[0]\[0] 표기법 외에도 \[0,0] 표기법도 지원한다.
#### boolean index
```python
my_array = np.array([[[1,2],[3,4]],[[5,6],[7,8]],[[9,10],[11,12]]], dtype=np.int8)

my_array > 8
#array([[[False, False], [False, False]], [[False, False], [False, False]], ​[[ True,  True], [ True,  True]]])

my_array[my_array < 6]
# array([1, 2, 3, 4, 5], dtype=int8)
```

### ndarray 의 slicing
```python
my_array = np.array([[[1,2],[3,4]],[[5,6],[7,8]],[[9,10],[11,12]]], dtype=np.int8)

my_array[:2,:,:]
# 3차원의 1번 index, 2차원의 전체, 1차원의 전체
# array([[[1, 2], [3, 4]],[[5, 6], [7, 8]]])

my_array[:,::2]
# array[[[1, 2], [5, 6], [9, 10]]]
```

### ndarray 생성 메소드
#### arange
```python
np.arange(10)
# array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])

np.arange(4, 0.5)
# array([0, 0.5, 1, 1.5, 2, 2.5, 3, 3.5])

np.arange(12).reshape(2,3,2)
# array([[[0, 1],[2, 3],[4, 5]],[[6, 7],[8, 9],[10, 11]]])
```

#### zeros, ones, empty & ~\_like
```python
np.zeros(shape=(2,3), dtype=np.int8)
# array([[0, 0, 0],[0, 0, 0]])

np.ones(3,2)
# array([[1., 1.],[1., 1.],[1., 1.]])

np.empty(shape=(4, 5), dtype=np.float64) # 빈 공간으로 만들어준다

np.ones_like(np.zeros(shape=(2,3), dtype=np.int8))
# array([[1, 1, 1],[1, 1, 1]])
```

#### identity & eye
```python
# identity: 단위 행렬 생성
np.identity(n=2, dtype=np.int8)
# array([[1, 0], [0, 1]], dtype=int8)

# eye: 대각선으로 1인 행렬
np.eye(2,4,k=1)
# array([[0., 1., 0., 0.],[0., 0., 1., 0.]])

np.diag(np.eye(2,4,k=1), k=1)
# array([1., 1.])
```

#### random
```python
np.random.uniform(0, 1, 10)
# 0부터 1까지 size 가 10인 균등분포 1차 행렬

np.random.normal(0, 1, 8).reshape(2,-1)
# 0부터 1까지 size 가 8인 정규분포 matrix
```

## 연산 메소드
#### dot
행렬의 곱연산
```python
array_1 = np.arange(1,9).reshape(4,2)
array_2 = np.arange(3,11).reshape(2,4)

array_1.dot(array_2)
array_1 @ array_2 # 연산자로 표현
```

transpose
$A^T$로 표시하는 그것을 해주는 메소드.
```python
array_1 = np.arange(1,9).reshape(4,2)
# array([[1, 2],[3, 4],[5, 6],[7, 8]])

array_1.transpose()
# array([[1, 3, 5, 7][2, 4, 6, 8]])
array_1.T
```

### 검색 메소드
#### where
#### isnan(행렬)
#### isinf(행렬)

#### argmax, argmin
최대값 혹은 최솟값의 index 를 return 한다.
```python
array_1 = np.arange(1,9).reshape(4,2)

np.argmax(array_1,axis=1)
# array([1, 1, 1 ,1])
np.argmax(array_1, axis=0)
# array([3, 3])
```

## data I/O
### loadtxt, savetxt
```python
data_array = np.loadtxt("<파일명>", delimeter="<구분자>")
np.savetxt("<파일명>", <대상>, fmt="<포멧>", delimeter="<구분자>")
```