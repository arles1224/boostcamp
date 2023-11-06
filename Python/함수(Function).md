# 함수(Function)
---
## 함수 선언
파이썬의 함수는 재미있게 생겼다.
```python
def function_name(param1, param2):
    # code


def function_name2():
    # code
```
Java 나 JavaScript 는 {}를 사용해서 code block 을 구분하는데 Python 은 indentation 으로 구분하는 게 재미있다. 그리고 함수와 함수 사이엔 2칸을 띄우는 것도 특이하다. 개인적으로는 빠르게 작성할 수 있어서 마음에 든다.

## 💡Call by Object Reference
이것도 재미있는 특징이다.
파이썬은 객체의 주소가 함수로 전달되기 때문에, 전달된 객체를 참조해서 변경하면 기존 객체가 수정된다. 그러나 새로운 객체를 만들면 기존 객체와 별개가 된다.
```python
def my_function(number_list):
    number_list.append(3)
    number_list = [i for i in range(10)] # 새로운 number_list 객체 생성
    print(number_list)

number_list = [0, 1, 2]
my_function(number_list)
# [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
print(number_list)
# [0, 1, 2, 3]
```