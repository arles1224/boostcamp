# Numpy
**Python 의 고성능 과학 계산용 패키지로 Array 연산의 표준이다**. 따라서 매우매우 중요하다.

## ndarray
numpy 를 이용해 생성하는 array 로 Java 와 마찬가지로 하나의 자료형만 사용할 수 있다. 자료형은 배열을 생성할 때 지정한다.
```python
import numpy as np
ndarray = np.array(['A', 'B', 'C', 7], str)

print(ndarray)
# ['A', 'B', 'C', '7']
type(ndarray)
# <class 'numpy.ndarray'>
```