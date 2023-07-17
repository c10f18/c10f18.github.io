---
title: "Python 파일 I/O"

categories:
  - Python
tags:
  - [python]

date: 2023-07-10 15:00:00 +0900
last_modified_at: 2023-07-10 15:00:00 +0900
published: true
---
# 파일 생성 및 쓰기
* `open` 메소드는 파일 경로와 파일 열기 모드를 인자로 받음 (root 경로는 파이썬 설치 경로)
  * `r` : 파일 읽기
  * `w` : 파일 쓰기
  * `a` : 파일 마지막 라인에 새로운 내용 추가
* 파일 쓰기 작업이 완료되면 `close`를 호출하여 파일쓰기를 종료해야함
* `with` 문을 통해 자동으로 파일의 파일쓰기 종료를 수행할 수 있음

## 파일 쓰기 방법 1
```
with open('{파일경로}', 'a') as f:
  f.write('\nwith 문을 사용하면 리스스 해제가 가동으로 된다')
  f.write('\nwith 문 블럭 내에서는 연속적인 쓰기가 가능함')
```

## 파일 쓰기 방법 2
```
f = open('{파일경로}', 'a')
f.write('\n파일 쓰기가 종료되면 파일쓰기를 반드시 종료해야함')
f.close()
```

# 파일 읽기
## 파일 읽는 방법 1
```
f = open('{파일경로}', 'r')
while True:
  tmp = f.readline()
  if not tmp:
    break
f.close()
```

## 파일 읽는 방법 2
```
f = open('{파일경로}', 'r')
tmp = f.readlines()
for lineResult in tmp:
  fileResult += lineResult
f.close()
```

## 파일 읽는 방법 3
```
f = open('{파일경로}', 'r')
tmp_list = list(enumerate(f))
for i in range(len(tmp_list)):
  fileResult += tmp_list[i]
f.close()
```

## 읽은 파일에서 전체 라인 수 구하기
```
# readLines 이용
f = open('{파일경로}', 'r', encoding='UTF8' )
print("파일 길이 : %d" % len(f.readlines()))

# enumerate 이용
f = open('{파일경로}', 'r', encoding='UTF8' )
print("파일 길이 : %d" % (len(list(enumerate(f)))))
```

# 경로 존재 여부 확인 후 파일인지 폴더인지 판단 및 생성, 파일 쓰기
```
import os

filepath = "/test/A/B.txt"
# 파일 존재 유무 확인
if not os.path.exists(filepath):
  #디렉토리 존재 확인
  if not os.path.exists(os.path.dirname(filepath)):
    # 폴더가 이미 있는경우 makedirs하면 오류나기 때문에 exist_ok 옵션을 True로 주어 처리
    os.makedirs(os.path.dirname(filepath), exist_ok=True)
  # 디렉토리 여부 확인
  if not os.path.isdir(filepath):
    # 파일 작성 시 인코딩 지정 
    f = open(filepath, 'w', encoding='utf-8')
    f.write("test")
    f.close()
```



# 경로에서 정보 추출
## 현재 코드가 참조중인 폴더 경로를 반환
```
import os

current_path = os.getcwd()
print("현재 위치 : " + current_path)
```

## 파일명 추출
```
import os

current_path = os.path.basename(filename)
```

## 디렉토리 경로 추출
```
import os

current_path = os.path.dirname(filename)
```

## 경로와 파일명 분리해 튜블로 반환
```
import os

current_path = os.path.split(filename)
```

## 드라이브명과 나머지 경로 분리
```
import os

current_path = os.path.splitdrive(filename)
```

## 경로에서 확장자 분리
```
import os

current_path = os.path.splitext(filename)
```

# 문자열을 줄바꿈 기준으로 쪼개기
```
txt = "1열 테스트\n2열 테스트"
x = txt.splitlines()
print(x)
# 결과 = ['1열 테스트', '2열 테스트']
```