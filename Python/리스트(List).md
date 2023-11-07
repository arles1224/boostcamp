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

---
## 리스트 메소드

```python
my_list = [1, 2, ,3, 4, 5]

my_list.append(6) # list object 맨 뒤에 6이 추가된다.
my_list.pop() # 맨 뒤 원소를 return 함과 동시에 my_list의 맨 뒤 원소가 삭제된다.
my_list.pop(3) # 3번 index 원소에 pop 이 작동한다.
```

---

- 오늘 새로 배운 내용 : 2차원 이상의 배열은 모듈을 이용해야지만 메모리 주소가 다른 리스트로 복제된다.
- 고민한 내용과 결과 : 
- 도움이 될 만한 내용이나 자료 : 
- 회고 : 