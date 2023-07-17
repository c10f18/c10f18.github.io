---
title: "tkinter 파이썬 GUI 모듈"

categories:
  - Python
tags:
  - [python]

date: 2023-07-17 15:00:00 +0900
last_modified_at: 2023-07-17 15:00:00 +0900
published: true
---
# tkinter 모듈 import
```
import tkinter
```

# tkinter 모듈 사용법
## 기본 선언 및 적재
```
import tkinter

root = Tk()
root.title("test gui title")
root.geometry("1000x730+2000+50")

## 프레임 선언
test_frame = LabelFrame(root, text="test frame")

## 라벨 선언
test_lab = Label(test_frame, text = "test label")

## 입력 Entry 선언 및 기본값 세팅(경로 특수문자 앞에 r을 붙여야 문제없이 세팅됨)
test_entry = Entry(test_frame, width=30)
test_entry.insert(0, r"C:\Users\test")

## 입력 Text (Textbox) 선언
test_text = Text(test_frame, width=70, height=13)

## Progress bar 선언 및 게이지용 변수 선언, 세팅
p_var = tkinter.DoubleVar()
test_progressbar = ttk.Progressbar(root, length=500, maximum=100, mode="determinate", variable=p_var)
def progressUpdate(i):
    global p_var
    p_var.set(i)
    test_progressbar.update()
    
## 버튼 선언(노란색)
test_button = Button(root, text="Test", padx=3, pady=3, bg="yellow", command={함수 이름})

## gui 적재
## grid 방식
test_frame.grid(row=0, column=0, sticky="w")
test_lab.grid(row=0, column=1, sticky="w")
test_entry.grid(row=1, column=1, sticky="w")
test_text.grid(row=1, column=0, sticky="e")
test_progressbar.grid(row=1, column=1, sticky="w")
## pack 방식
test_button.pack()

root.mainloop()
```

## grid 방식 gui 적재 방향
* sticky 옵션을 통해 grid 배치 Anchor 정렬을 설정할 수 있음
  * CENTER : 중앙
  * N : 북
  * E : 동
  * S : 남
  * W : 서
  * NE : 북동
  * SE : 남동
  * SW : 남서
  * NW : 북서
