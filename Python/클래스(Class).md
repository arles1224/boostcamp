# Class
Java 에서와 마찬가지로 attribute 와 method 로 구성 되어 있고, 초기화 함수가 존재한다.
```python
class MyPen(object):
    def __init__(self, color, length, cap): # 초기화 함수
        self.color = color
        self.length = length
        self.cap = cap
    
    def __str__(self):
        return f'My pen. The color is {self.color}. The length is {self.length}.'

staedtler = MyPen('black', 137, True)
```

>📌 Python 에서 \_\_는 특수한 예약 함수나 예약 변수에, 혹은 맨글링을 할 때 사용한다.

## 상속(Inheritance)
이건 Java 와 동일하다.
```python
class Staedlter(MyPen):
    def __init__(self, color, length, cap, ink_type):
        super().__init__(color, length, cap)
        self.ink_type = ink_type
    
    
    def removeCap(self):
        print('The cap is removed')
        self.cap = False
```

## 가시성(Visibility)
\_\_를 붙여 맨글링이 일어나게 하면 변수를 숨길 수 있다.
숨긴 변수를 보고 싶으면 @property 라는 decorator 를 Java 의 annotation 처럼 함수 위에 써서 선언해, 그 함수에서 숨긴 변수를 return 해주면 된다.

