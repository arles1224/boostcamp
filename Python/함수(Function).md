# 함수(Function)
함수는 다음과 같을 때 선언하면 좋다
- 공통으로 여러번 사용하는 코드가 있을 때
- 수식이 복잡할 때
- 조건이 복잡할 때
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

## 재귀함수(Recursive Function)
```python
# n^x 를 구하는 재귀함수
def power(x, n):
    if n == 0:
        return 1
    return x * power(x, n-1)
```

## Arguments 를 넘기는 방법
### Keyword arguments
함수 parameter 의 변수명을 사용해서 순서와 상관 없이 arguments 를 넘길 수 있는 방법이다.
```python
def my_function(param1, param2):
    print(f'{param2}과 {param1}')


my_function(param2='성실', param1='노력')
```

### Default arguments
말 그대로 arguments 에 기본값을 정해서 사용하는 것이다.
```python
def my_function(param1, param2='성실'):
    print(f'{param2}과 {param1}')

my_function('노력')
```

### Variable-length arguments
개수가 정해지지 않은 변수를 함수의 parameter 로 사용할 때 \*로 표시한다. 가변인자는 가장 마지막 parameter 로 딱 한 개만 사용할 수 있다.
```python
def calculate_mean(*args):
    sum = 0
    for i in args:
        sum += i
    
    return sum / len(args)


calculate_mean(5,6,7,8,9,10)
# 7.5
```

### Keyword variable-length arguments
parameter 의 이름을 따로 지정하지 않고 arguments 를 함수로 보내는 방법이다. 이때 argument 는 dict 형태로 전송된다.
```python
def my_function(**kwargs):
    for k, v in kwargs.items():
        print(f'Key: {k}, Value: {v}')


my_function(date='2023.11.07', time='13:54', weather='sunny')
# Key: date, Value: 2023.11.07
# Key: time, Value: 13:54
# Key: weather, Value: sunny
```