---
title: "Python 개발환경 세팅 및 모듈 설치"

categories:
  - Python
tags:
  - [python]

date: 2023-07-10 15:00:00 +0900
last_modified_at: 2023-07-10 15:00:00 +0900
published: true
---
# Python 설치
* [Python](https://www.python.org) 에서 Python 설치
* Latest 버전 설치
* 설치 과정에서 'Add Python {버전} to PATH' 체크박스를 체크하고 설치 진행
* ‘Disable path length limit’를 선택하여 PATH 길이 제한 해제를 동의
 
![python version check](/assets/images/post/programming/python-cmd-check.PNG)
* 설치 완료 후 명령 프롬프트에서 python을 `python` 을 입력하여 버전을 확인

# Python IDE Pycharm 설치
* [Pycharm](https://www.jetbrains.com/pycharm/download) 에서 Community 버전 Pycharm 설치
* 초기 설정에서 기존 사용중이던 환경 설정을 불러올 수 있음

# Python 모듈 설치
## 명령 프롬프트를 통한 Python 모듈 설치
* 모듈 설치 위치로 이동하여 `pip install pyautogui` 콘솔 실행

## Pycharm 에서의 Python 모듈 설치
* `File - Settings` 진입 후 `Project: {프로젝트명} - Python Interpreter` 탭으로 진입
* 좌측 상단의 `+` 를 클릭하여 패키지 명으로 검색 후 모듈 설치

![python install module](/assets/images/post/programming/python-install-module.PNG)

