# 리스트

## 리스트에 대하여
파이썬 리스트 특징 중에 제일 늦게 익혀진 것이 unpacking 이다.
```python
my_list = ['apple', 'banana', 'lemon']

fruit1, fruit2, fruit3 = my_list
```
이렇게 코드를 작성하면 `my_list` 안의 값들이 각각의 변수들에 할당되는데, 이것을 unpacking 이라고 부른다.

그리고 리스트를 복제할 때 메모리 주소에 대해 주의해야 할 것이 있다.
```python
a = [1, 2, 3, 4, 5]

b = a # a 와 b 의 메모리 주소가 동일하다
b = a[:] # a 와 b 의 메모리 주소가 다르다.
```
`b` 를 `a` 를 복사했지만 별개로 수정되게 하고 싶으면 `[:]`를 사용해 복사하면 된다.
단, 이 경우는 1차원 배열에서만 해당된다. 2차원에서는 `copy` 라는 모듈을 사용한다.
```python
import copy
numbers = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

numbers_copy = copy.deepcopy(numbers)
```

## 리스트 메소드

```python
my_list = [1, 2, ,3, 4, 5]

my_list.append(6) # list object 맨 뒤에 6이 추가된다.
my_list.pop() # 맨 뒤 원소를 return 함과 동시에 my_list의 맨 뒤 원소가 삭제된다.
my_list.pop(3) # 3번 index 원소에 pop 이 작동한다.
```

## List Comprehension
파이썬은 리스트를 한 줄로 바로 생성할 수 있다. Java 나 JavaScript 랑은 확실히 구분되는 Python 만의 특징이다.
```python
list_1 = ["가", "나", "다"]
list_2 = ["마", "바", "사"]

[i + j for i in list_1 for j in list_2]
# ["가마", "가바", "가사", "나마", "나바", "나사"]

[[i + j for i in list_1] for j in list_2]
# [["가마", "나마", "다마"], ["가바", "나바", "다바"], ["가사", "나사", "다사"]]
```
첫 번째의 경우는 `list_1` 의 for loop 가 먼저 돌아가고, 두 번째의 경우는 `list_2` 의 for loop 가 먼저 돌아가서 출력 결과가 다르게 나온다.
이렇게 한 줄로 간단하게 2차원 리스트를 만들 수 있어서 편리하다. 이런 편리함이 Python 이 갖는 강점인가보다.

## Enumerate
list 의 element 와 index 번호를 편리하게 추출할 수 있다. String 에도 동일하게 사용할 수 있다.
```python
my_list = ["A", "B", "C"]
for i, v in enumerate(my_list):
    print(i, v)
# 0, A
# 1, B
# 2, C
```

## Zip
여러 개의 list의 값을 같은 인덱스끼리 tuple 로 묶어 준다. Python 은 enumerate 와 zip 같은 편리한 메소드? 가 기본으로 내장되어 있는 것이 마음에 든다. 수학 관련 작업을 할 때 편할 것 같다.
```python
list_1 = [10, 20, 30]
list_2 = [100, 200, 300]
list_3 = [1000, 2000, 3000]

one, two, three = zip(list_1, list_2, list_3)
# 위 라인에서는 zip 과 unpacking 이 동시에 일어나고 있다! 이게 바로 pythonic code 인가
# (10, 100, 1000), (20, 200, 2000), (30, 300, 3000)

[sum(decimal) for decimal in zip(list_1, list_2, list_3)]
# list comprehension 과 zip. 이게 Python 의 힘이구나
# [1110, 2220, 3330]
```

---
## 튜플(tuple)
상수 리스트. 값을 바꿀 없다. 나머지는 리스트와 동일하다.
```python
my_tuple = (1, 2, 3, 4, 5)
t = (1) # Integer 로 인식
t = (1,) # tuple 로 인식
```

