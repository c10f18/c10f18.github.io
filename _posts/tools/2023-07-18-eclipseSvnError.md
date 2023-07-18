---
title: "Eclipse Java Error - Unable to make field private java.lang.Throwable java.lang.Throwable.cause accessible: module java.base does not "opens java.lang" to unnamed module 해결 방법"

categories:
  - window
tags:
  - [window, cmd]

date: 2023-07-18 16:00:00 +0900
last_modified_at: 2023-07-18 16:00:00 +0900
published: true
---
# Eclipse Java Error
## Error 발생 배경
* SVN Project Share 시도중 실패. 에러 메시지 발생

## Error 메시지
> Unable to make field private java.lang.Throwable java.lang.Throwable.cause accessible: module java.base does not "opens java.lang" to unnamed module

### 해결방법 1
#### eclipse.ini 파일을 수정하여 이클립스 실행 Java 버전을 조정함
* `-vm` 밑의 내용을 Java Path로 변경하면 된다.

> -vm   
> D:\dev\Java\jdk-11\bin

#### 시도 결과
* 이클립스 버전에 따라 적용 가능한 JVM 최소 버전이 있음.
* 11버전으로의 변경을 시도했으나 최신 이클립스는 17 이상 사용이 강제되어 해결 실패함

### 해결방법 2
#### eclipse.ini 파일을 수정하여 옵션을 추가함
* 내용에 `--illegal-access` 와 `--add-opens` 옵션 추가

> --illegal-access=warn   
> --add-opens=java.base/java.lang=ALL-UNNAMED

#### 시도 결과
* 동일한 문제 발생

### 해결방법 3
#### SVN Connector 에러 해결
* SVN Connector 인식 문제가 있는것 같아 먼저 해결 시도
* 자동 설치가 에러나서 수동으로 설치했으나 에러 상태
* Subclipse 설치로는 해결이 되지 않아 Subversive 로 변경

> Eclipse Market Place 에서 Subversive - SVN Team Provider 4.8 설치 후    
> Install New Software 에서 `https://osspit.org/eclipse/subversive-connectors/` url을 통해 SVN Connectors 설치 및 재시작

#### 시도 결과
* 해결에 성공함