# iter
반복가능한 객체의element에 index 순서대로 하나씩 접근할 수 있게 해준다.
```python
lan = ['Python', 'Java', 'C']
iter_lan = iter(lan)

next(iter_lan)
# 'Python'
next(iter_lan)
# 'Java'
next(iter_lan)
# 'C'
```

# generator
이해가 안 돼서 ChatGPT 한테 물어봤다.

>💡파이썬에서 제너레이터(generator)는 시퀀스를 생성하는 함수입니다. 일반적으로 모든 값을 메모리에 저장하지 않고 필요한 시점에 값을 반환하는 방식으로 동작합니다. 이는 대량의 데이터나 무한한 시퀀스를 처리할 때 유용합니다.
>
>제너레이터는 일반 함수와 다르게, yield 문을 사용하여 값을 생성하고 반환합니다. 함수가 호출될 때마다 상태를 유지하고 마지막으로 호출된 위치에서 계속 실행됩니다.
>
>제너레이터는 필요한 순간에 값을 생성하며, 모든 값을 한 번에 메모리에 저장하지 않고도 효율적으로 대규모 데이터나 무한한 시퀀스를 다룰 수 있습니다. `next()` 함수로 값을 가져오는 동안에 상태를 유지하므로 매 호출 시 새로운 값을 반환합니다.
>
>출처: ChatGPT

```python
def my_generator():
    yield 1
    yield 2
    yield 3

gen = my_generator()
print(next(gen))
# 1
print(next(gen))
# 2
print(next(gen))
# 3
```
generator 를 사용하면 메모리 용량을 아낄 수 있으니 대용량 자료를 다루는 일이 많은 작업에서는 generator 를 쓰는 게 더 효율적이겠구나. 속도도 더 빠르겠다.

### generator comprehension
list comprehension 과 표현법은 동일하지만, \[] 대신 ()를 사용한다.
```python
gen = (x ** 2 for x in range(10))

type(gen)
# <class 'generator'>
```