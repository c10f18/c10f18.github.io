---
title: "명령 프롬프트 파일, 폴더 경로 확인 명령어"

categories:
  - window
tags:
  - [window, cmd]

date: 2023-07-10 16:00:00 +0900
last_modified_at: 2023-07-10 16:00:00 +0900
published: true
---
# 파일 디렉토리 확인 명령어
명령 프롬프트에서 `dir` 명령어를 통해 프롬프트 위치의 파일 및 디렉토리 정보를 확인할 수 있다.
옵션을 추가하여 추가 정보를 출력하거나 결과를 텍스트 파일로 저장할 수 있다.

## 디렉토리 명령어 help 
* 명령 프롬프트에서 `help dir` 명령어를 통해 파일 디렉토리 정보를 확인할 수 있다.

![CMD Dir](/assets/images/post/programming/cmd-help-dir.PNG)

## 현재 디렉터리의 폴더, 파일 보기
* `dir`

## 현재 디렉토리의 파일, 폴더 이름만 추출
* `dir /b`

## 현재, 하위 디렉토리의 파일, 폴더 보기
* `dir /s`

## 현재, 하위 디렉토리의 파일, 폴더를 경로 형태로 보기
* `dir /b /s`

## 현재, 하위 디렉토리의 파일, 폴더 경로를 텍스트 파일로 출력 저장
* `dir /b /s > fileList.txt`