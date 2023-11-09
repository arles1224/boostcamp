그 판다가 아니라니.
# Pandas
## CSV 파일을 불러오는 경우
```python
import pandas as pd

data = pd.read_csv('data.csv',encoding='EUC-KR')

data.values
# 값들을 출력

data.colums
"""
Index(['측정날짜(MSRDATE)', '측정소_행정동코드(MSRADMCODE)', '대기환경등급(GRADE)', '통합대기환경지수(MAXINDEX)', '지수결정물질(POLLUTANT)', '이산화질소_농도(NITROGEN)', '이산화실소_지수(NITROGENINDEX)', '오존_농도(OZONE)', '오존_지수(OZONEINDEX)', '일산화탄소_농도(CARBON)', '일산화탄소_지수(CARBONINDEX)', '아황산가스_농도(SULFUROUS)', '아황산가스_지수(SULFUROUSINDEX)', '미세먼지_농도(PM10)', '미세먼지_지수(PM10INDEX)', '미세먼지(24시)농도(PM24)', '미세먼지(24시)지수결정물질(PM24INDEX)', '권역코드(MSRRGNCODE)', '권역명(MSRRGNNAME)', '측정소명(MSRSTENAME)'], dtype='object')
"""

data['측정날짜(MSRDATE)']
# 해당 데이터 출력

data[['권역명(MSRRGNNAME)','미세먼지_지수(PM10INDEX)']][3:6]
# column 2개 3, 4, 5 index 출력
```

## Series
```python
from pandas import Series, DataFrame

my_list = [['20231106','Python 기초', '완료'],['20231107','선형대수 기초', '진행중'], ['20231108', '확률론 기초', '완료']]

my_index = ['a', 'b', 'c']

s_list = Series(data = my_list, index = my_index)
s_list['a']
# ['20231106','Python 기초', '완료']
```
### Series 에 map 사용하기
```python
series = Series(np.arange(8))
datas = {3: 'apple', 4: 'orange', 7: 'peach'}

series.map(datas) # dict 의 key 에 맞는 index 자리에 값을 넣어준다.
"""
0       NaN
1       NaN
2       NaN
3     apple
4    orange
5       NaN
6       NaN
7     peach
"""
```

### Series 내장 메소드
#### value_counts
```python
my_list = [['20231106','Python 기초', '완료'],['20231107','선형대수 기초', '진행중'], ['20231108', '확률론 기초', '완료']]

df =DataFrame(my_list, columns=['날짜', '과목', '상태'])

df['과목'].value_counts(normalize=True)
"""
과목
Python 기초    0.666667
선형대수 기초      0.166667
확률론 기초       0.166667
"""
```
## DataFrame

### DataFrame Indexing
```python
from pandas import Series, DataFrame

my_list = [['20231106','Python 기초', '완료'],['20231107','선형대수 기초', '진행중'], ['20231108', '확률론 기초', '완료']]

df =DataFrame(my_list, columns=['날짜', '과목', '상태'])
# DataFrame 객체 생성

df['날짜'].iloc[2]
# '20231108'

df[['날짜', '상태']]
"""
         날짜   상태
0  20231106   완료
1  20231107  진행중
2  20231108   완료
"""

df['상태'] = df['상태'].replace({'완료': True, '진행중': False})
```

>💡깨알 팁
>import dateutil
>df['날짜'] = df['날짜'].apply(dateutil.parser.parse, dayfirst=False)
>위의 코드를 작성해주면 날짜가 2023-11-06 형태로 바뀐다.

### DataFrame column 추가 방법 with Series
```python
values = Series(data = ['mac', 'mac'], index=[0, 2])
df['플랫폼'] = values
df
"""
         날짜         과목   상태  플랫폼
0  20231106  Python 기초   완료  mac
1  20231107    선형대수 기초  진행중  NaN
2  20231108     확률론 기초   완료  mac
"""
```

### DataFrame 행/열 삭제 방법
```python
df.drop('플랫폼', axis=1)
"""
         날짜         과목   상태

0  20231106  Python 기초   완료
1  20231107    선형대수 기초  진행중
2  20231108     확률론 기초   완료
"""
df.drop(1)
"""
         날짜         과목  상태  플랫폼

0  20231106  Python 기초  완료  mac
2  20231108     확률론 기초  완료  mac
"""
```
### DataFrame 연산
```python
from pandas import DataFrame
import numpy as np

df1 = DataFrame(np.arange(6).reshape(2,3), columns=list('abc'))
df2 = DataFrame(np.arange(9).reshape(3,3), columns=list('def'))

df1 + df2
"""
    a   b   c   d   e   f

0 NaN NaN NaN NaN NaN NaN
1 NaN NaN NaN NaN NaN NaN
2 NaN NaN NaN NaN NaN NaN
"""

df1.add(df2,fill_value=0)
"""
     a    b    c    d    e    f

0  0.0  1.0  2.0  0.0  1.0  2.0
1  3.0  4.0  5.0  3.0  4.0  5.0
2  NaN  NaN  NaN  6.0  7.0  8.0
"""
```

## Groupby
SQL 의 그 group by 가 맞다. 이걸 Python 에서 사용할 수 있다는 게 신기하다.
```python
import pandas as pd
from pandas import DataFrame

my_list = [['20231106','Python 기초', 3, '완료'],['20231106','Python 기초', 4, '완료'],['20231107','선형대수 기초', 2, '진행중'], ['20231107','Python 기초', 2, '완료'], ['20231108', '확률론 기초', 2, '완료'], ['20231108','Python 기초', 2, '완료']]

df = DataFrame(my_list, columns=['날짜', '과목', '시간', '상태'])

# df.groupby("<기준 컬럼>")["<적용 컬럼>"].연산()
times = df.groupby(["과목","날짜"])["시간"].sum()
type(times)
# <class 'pandas.core.series.Series'>
# groupby 결과는 Series 데이터이다.
times
"""
과목         날짜      
Python 기초  20231106    7
           20231107    2
           20231108    2
선형대수 기초    20231107    2
확률론 기초     20231108    2
Name: 시간, dtype: int64
"""

times.index
times.unstack() # 행렬화
times.reset_index()
"""
          과목        날짜  시간
0  Python 기초  20231106   7
1  Python 기초  20231107   2
2  Python 기초  20231108   2
3    선형대수 기초  20231107   2
4     확률론 기초  20231108   2
"""
```

### groupby unpacking
```python
import pandas as pd
from pandas import DataFrame

my_list = [['20231106','Python 기초', 3, '완료'],['20231106','Python 기초', 4, '완료'],['20231107','선형대수 기초', 2, '진행중'], ['20231107','Python 기초', 2, '완료'], ['20231108', '확률론 기초', 2, '완료'], ['20231108','Python 기초', 2, '완료']]

df = DataFrame(my_list, columns=['날짜', '과목', '시간', '상태'])

grouped = df.groupby("과목")["날짜"]

for key, value in grouped:
    print(key)
    print(value)
"""
Python 기초
0    20231106
1    20231106
3    20231107
5    20231108
Name: 날짜, dtype: object

선형대수 기초
2    20231107
Name: 날짜, dtype: object

확률론 기초
4    20231108
Name: 날짜, dtype: object
"""
```

### groupby 데이터 다루기
#### agg
```python
import numpy as np

grouped.agg(sum)
grouped.agg([max, min])
grouped.agg([np.mean, np.sum, np.std])

df.groupby(['날짜','상태']).agg({'과목': 'count', '시간': sum})
"""
                과목  시간
날짜         상태
2023-11-06 완료    2   7
2023-11-07 완료    1   2
           진행중   1   2
2023-11-08 완료    2   4
"""
```
agg 는 꼭 SQL 쓰는 것 같아서 재밌다.
#### transform
이걸 왜 쓰는 거지?

## Categorical
```python
subject_categories = pd.Categorical(df['과목'])
subject_categories.categories
# Index(['Python 기초', '선형대수 기초', '확률론 기초'], dtype='object')
```