---
title: "Javascript Legacy 코드 Refactoring"

categories:
  - study
tags:
  - [js, legacy, refactoring]

date: 2023-06-27 15:00:00 +0900
last_modified_at: 2023-06-27 15:00:00 +0900
published: false
---

# IE에서만 사용가능한 javascript 문법
IE에서만 사용가능한 javascript 함수 및 문법들과 CrossBrowsing을 위해 변환하는 방법을 기술합니다.



## 1) window.showModalDialog()

→ 모달팝업 전환개발 가이드 (showModalDialog 대체) 문서를 참고하여 window.open()을 이용한 Modeless 팝업으로 전환 합니다.
* 해당 페이지에서 모달팝업기능이 반드시 필요한 경우에는 jqueryModal을 이용하여 레이어 모달로 전환하여야 합니다.
    → 이 경우 Modeless 팝업으로 전환하는 것 보다 작업공수가 대폭 증가하게 되므로 작업전 운영팀/개발팀/PMO 의 검토를 거쳐 작업공수 재산정을 필수적으로 하셔야 합니다.


## 2) jquery를 이용하여 textarea의 값을 가져올 때 사용되는 text() 함수

$("#textareaId").text(); → $("#textareaId").val();


## 3) attachEvent → addEventListener 로 전환

object.attachEvent (eventName, function);
    - IE, 오페라
    - 이벤트는 "on"+event명

object.addEventListener (eventName, function, useCapture);
    - 표준 브라우저(IE9, 파이어폭스, 오페라, 사파리, 크롬)
    - 이벤트는 event명



아래 코드샘플과 같이 attachEvent가 사용가능 할 때와 사용 불가능 할 경우를 모두 지원하게 방어코드를 구성합니다.

attachEvent 전환샘플
```
<script type="text/javascript">
if(window.attachEvent){
    window.attachEvent('onload',function(){
        alert('attachEvent!');
    });
} else {
    window.addEventListener('load',function(){
        alert('addEventListener!');
    },false);
}
```


## 4) getYear() → getFullYear()

myDate = new Date();
year = myDate.getYear();

와 같이 년도를 구하는 함수를 사용하게 되면 year의 값은 올해인 2022가 아니라 122를 반환합니다.

이는 getYear()가 1990년대 2자리수 년도를 사용하기 위해 올해년도에서 1900을 뺀 값을 리턴하도록 설계된 함수이기 때문입니다.

그러나 IE8 까지는 getYear()가 4자리 년도를 정상 리턴하고 있었기 때문에 IE8이하버전에서는 getYear()와 getFullYear()가 모두 "2022"를 반환합니다.

따라서 호환성보기 설정 등으로 IE8이하버전을 사용하고 있는 시스템은 getYear()를 getFullYear()로 수정해야 "2022"와 같은 4자리 년도를 사용할 수 있습니다.

