---
title: "pyautogui 키보드 마우스 제어 모듈"

categories:
  - Python
tags:
  - [python]

date: 2023-07-11 15:00:00 +0900
last_modified_at: 2023-07-11 15:00:00 +0900
published: true
---
# pyautogui 모듈 import
```
import pyautogui
```

# 마우스 정보 확인 프로그램 실행
```
import pyautogui

pyautogui.mouseInfo()
```

# pyautogui 주요 함수
## 마우스 제어
### 현재 마우스 포인트의 X,Y좌표
```
import pyautogui

mouseX, mouseY = pyautogui.position()
```

### 모니터 해상도
```
import pyautogui

screen_width, screen_height = pyautogui.size()
```

### 마우스 커서 좌표 이동
```
import pyautogui

pyautogui.moveTo(500, 500)
```

### 마우스 클릭 이벤트
```
import pyautogui

# 마우스 클릭
pyautogui.click()

# 마우스 왼쪽 버튼 더블클릭 
pyautogui.doubleClick()
pyautogui.click(clicks=2)

# 마우스 오른쪽 버튼 클릭
pyautogui.click(button='right')
pyautogui.rightClick()

# 마우스 휠 클릭
pyautogui.middleClick()

# 마우스 버튼다운
pyautogui.mouseDown()

# 마우스 버튼업
pyautogui.mouseUp()

# 마우스로 특정좌표 클릭
pyautogui.click(x=500, y=500)

# 1초 안에 더블 클릭 1회
pyautogui.click(clicks=2, interval=1)

#마우스 왼쪽 버튼 10회 클릭
pyautogui.click(clicks=10)
```

### 마우스 드래그 및 스크롤
```
import pyautogui

# 마우스 드래그
pyautogui.mouseDown(x=100, y=100)
pyautogui.mouseUp(x=200, y=200)

# 마우스 드래그
# 마우스 현재 위치에서 x=100, y=100로 드래그
pyautogui.dragTo(x=100, y=100)

# 2초안에 마우스 현재 위치에서 x=100, y=100로 드래그
pyautogui.dragTo(x=100, y=100, duration=2)

# 2초안에 마우스 현재위치에서 -100, -100위치로 드래그
pyautogui.dragRel(-100, -100, duration=2)

# 마우스 스크롤 (위로)
pyautogui.scroll(-100)

# 마우스 스크롤 (아래로)
pyautogui.scroll(100)

# 특정 위치로 이동(x=100, y=100) 후 스크롤
pyautogui.scroll(100, x=100, y=100)
```

## 키보드 제어
### 마우스 클릭 이벤트
```
import pyautogui


```

## 부가 기능
### 스크린샷
```
import pyautogui

#전체화면 스크린샷
img = pyautogui.screenshot()
img.save('screenshot.png')

#화면의 일부영역 스크린샷 
img2 = pyautogui.screenshot('region.png', region=(0,0,500,500))
```

### 픽셀 색상값 비교
```
import pyautogui

# 특정 위치(x,y) 좌표의 색상값 비교
p = pyautogui.pixel(1000,100)
print(p)
if pyautogui.pixelMatchesColor(1000, 100, p):
 print('일치')
else:
 print('불일치')
```

### 키 누르기
```
import pyautogui

# 엔터키 누르기
pyautogui.press('enter')

# 여러 키 연속으로 입력하기
pyautogui.press(['enter','enter','enter','enter'])
 
# 키보드의 쉬프트를 누르고 유지
# pyautogui.keyDown('shift')
# 쉬프트키 누름 해제
# pyautogui.keyUp('shift')

# 복사 붙이기
pyautogui.hotkey('ctrl', 'c')
pyautogui.hotkey('ctrl', 'v')

# enter 키를 2초에 한번씩 5번 입력합니다.
pyautogui.press('enter', presses=5, interval=2)
```

### 텍스트 입력
```
import pyautogui

# 텍스트 입력
pyautogui.write('Hello python')
pyautogui.typewrite('Hello python')
```

## 오류 처리
```
import pyautogui

# 마우스 제어의 오동작으로부터 벗어날 수 있도록 True로 설정
pyautogui.FAILSAFE = True 

#마우스 제어시 오류 발생시에도 실행을 멈추지않고 유지
pyautogui.FAILSAFE = False
```