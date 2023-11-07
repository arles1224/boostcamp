# set
set 은 중복을 허락하지 않는다. 말 그대로 집합!
```python
my_set = set([1, 1, 2, 2, 3, 3, 4, 4, 5, 5])
my_set # {1, 2, 3, 4, 5}

my_set = {2, 3}
type(my_set) # set
```

## set 원소 관련 메소드
```python
my_set = {1, 2, 3}
my_set.add(4) # 원소 4 추가
my_set.remove(1) # 원소 1 삭제
my_set.discard(3) # 원소 3 삭제
my_set.update([1, 4, 5, 6]) # 1, 4, 5, 6 추가
my_set.clear() # 모든 원소 삭제
```

## set 수학 관련 메소드
```python
s1 = {1, 2, 3, 4, 5}
s2 = {3, 4, 5, 6, 7}

# 합집합
s1.union(s2)
s1 | s2

# 교집합
s1.intersection(s2)
s1 & s2

# 차집합
s1.difference(s2)
s1 - s2
```