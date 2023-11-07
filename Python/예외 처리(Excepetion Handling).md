# 예외 처리
Java 의 try-catch 문과 같다.
```python
try:
    # 예외 발생 가능 코드
except <Exception Type> as alias:
    # 예외 발생 시 대응 코드
except <Exception Type>:
    # 예외 발생 시 대응 코드
else:
    # 예외가 발생하지 않을 때 작동할 코드
finally:
    # 예외 발생 여부와 상관 없이 작동하는 코드
```
try -> except/else -> finally 순으로 작동한다.

## raise
원하는 상황에 Exception 을 발생시킬 수 있다.
```python
def check_positive_number(digit):
    try:
        if digit < 0:
            raise ValueError('음수는 허용되지 않습니다.')
        else:
            print('양수입니다.')
    except TypeError as ve:
        print('숫자만 입력해주세요.')
```

## assert
특정 조건을 만족하지 않을 경우 예외를 발생시킬 수 있다.
```python
def divide(number1, number2):
    assert number2 != 0, '두 번째 인자는 0이 될 수 없습니다.'
    return number1 / number2
```