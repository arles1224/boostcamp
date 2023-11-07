# 내장 메소드
## lambda
이름 없이 사용할 수 있는 익명 함수로, 간단한 함수를 간략하게 표현할 수 있다는 점이 매력적이다.
return 을 사용하지 않아도 : 뒤에 적은 값이 return 된다.
lambda 함수를 변수에 초기화 시키지 않고도 바로 사용할 수 있다.
```python
my_lambda = lambda param1, param2, param3: param1 + param2 + param3

print(my_lambda("lambda 로 ", "concat 한 ", "문장입니다."))
# lambd 로 concat 한 문장입니다.

# 변수에 초기화 시키지 않고 lambda 함수 사용하는 법
(lambda a, b: a % b)(192, 33)
# 27

# lambda 연습
upper_lower = lambda up, low: up.upper() + low.lower()
print(upper_lower('p','H.D'))
```
근데 PEP8 부터는 lambda 를 권장하지 않는다고 한다. 함수 테스트랑 해석이 어려워서 그렇다고 하는데 그래도 편한걸... 그런데 다른 사람이 쓴 lambda 함수는 읽기 불편할 것 같긴 하다.

## map
map 은 함께 사용할 함수와 parameter 로 넣어줄 시퀀스형 자료가 필요하다. 이것도 lambda 와 마찬가지로 읽기 어렵다는 이유로 권장하지 않는다고 한다. 나도 가능하면 이것 대신 list comprehension 같은 것을 사용하는 것이 더 이해하기 쉬워 보인다. 
```python
decimal_list = ["1", "2", "3", "4", "5"]

list(map(int, decimal_list))
# [1, 2, 3, 4, 5]

my_lambda = lambda x, y: x + y
list(map(my_lambda, decimal_list, decimal_list))
# ['11', '22', '33', '44', '55']
```
