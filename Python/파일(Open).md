# File I/O

### File Input
Java 와 마찬가지로 파일을 다 사용하면 닫아주는 걸 잊지 말자!
```python
f = open("<파일명>","r")
contents = f.read() # 파일을 content 변수에 저장한다.
f.close()

with open("<파일명>", "r") as my_file:
    # with 구문은 close 가 없어도 with 가 끝나면 자동으로 파일이 닫힌다.
    contents_list = f.readlines() # 한 번에 list 형식으로 한 줄 씩 저장된다.
    print(contents[2])
```

### File Output
```python
f = open("<파일명.확장자>", 'w', encoding="utf8")
f.write("이것은 Python 으로 생성된 파일입니다.")
f.close()

# 기존 파일에 추가하는 방법
with open("<파일명.확장자>", 'a', encoding="utf8") as myFile:
    f.write("이것은 Python 으로 추가된 내용입니다.")
```

# os module
```python
import os

try:
    os.mkdir("py_dir")
except FileExistError:
    print("이미 존재하는 파일입니다.")

os.path.exists("py_dir") # True
os.path.isfile("py_file.txt") # False

os.path.join("desctop","filename.txt")
# desctop구분자filename 자동으로 운영체제에 맞는 구분자를 사용한다.
```

# pathlib
path 에 접근하기에 os.path 보다 더 편하다.
```python
import pathlib
cwd = pathlib.Path.cwd() # 현재 작업중인 디렉토리
```

