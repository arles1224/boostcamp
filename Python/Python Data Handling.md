# CSV(Comma-Separated Values)

>💡CSV 파일의 구조는 각 열(column)마다 헤더(표의 열 제목)와 실제 값으로 이루어진 행(row)으로 구성됩니다. 각 행은 줄바꿈 문자로 구분되며, 각 열 값은 쉼표(,)로 구분됩니다. 하지만 때때로 쉼표 대신 탭(tab) 또는 세미콜론(;)과 같은 다른 구분자도 사용될 수 있습니다.
>
>출처: ChatGPT

엑셀 파일을 손쉽게 열기 위해 사용하는 형식이라고 한다. 웹개발 배울 때 MySQL 에 데이터 미러링하는 게 힘들었는데 이걸 알았으면 훨씬 편했을 것이다. 역시 아는 만큼 보이는 법이다.

다만 그때도 ','로 고생했듯이 데이터 자체에 ','가 포함되어 있으면 그때부터 고생이다. 전처리 해서 미리 제거해줘야 한다.

## CSV 객체
Python 에서는 CSV 파일을 쉽게 다룰 수 있는 CSV 객체를 제공하고 있다.
```python
import csv

f = file.open("<파일 경로>",r)
reader = csv.reader(f, delimiter=',', quotechar='"', quoting=csv.QUOTE_ALL)
```


