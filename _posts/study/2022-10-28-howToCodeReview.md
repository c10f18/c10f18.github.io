---
title: "코드 리뷰"

categories: 
  - study
tags:
  - [js, legacy, refactoring]

date: 2023-06-27 15:00:00 +0900
last_modified_at: 2023-06-27 15:00:00 +0900
published: false
---

# 클린코드 룰셋
1. 코드 주석 삭제
2. 모호한 변수명 의미있게 변경 (ex. obj, i, j, s)
3. 매직넘버 상수화
4. 모호한 함수명 기능 포함하도록 변경
5. 에러 처리의 경우 console.log 말고 console.error 사용
6. 개발을 위해 로그 찍은 System.out.println는 삭제하고 로그가 추후에도 필요하다면 Logger 사용
7. 들여쓰기 시 탭과 스페이스 혼용 지양

# 코드 리뷰 개요
## 코드 리뷰란
코드 리뷰란 한 개발자가 코드를 작성하면 다른 개발자가 정해진 방법으로 피드백을 주고받는 과정을 말합니다.
이 과정을 통해 본인이 발견하지 못한 실수를 다른 사람이 발견하여 코드의 부작용(Side effect)과 오류를 조기에 대응할 수 있으며,
개발 내 정해진 컨벤션 규칙을 유지하고 기술 부채를 줄일 수 있습니다.
또한 여러 명의 개발자가 참여함으로써 문제 해결을 위한 기술 구현 방법론에 대해 공유하기도 합니다.


## 코드 리뷰의 중요성
팀 내에서 코드 품질이 항상 이슈가 됩니다.
그러나 모두들 바빠지면서, 코드 품질에 대한 관심은 금세 식어버리고 매번 코드 품질이 이슈화가 반복 됩니다.

## 코드리뷰로 얻을 수 있는 가장 대표적인 장점으로는
‘버그의 조기 발견’, ‘개발 표준(convention) 준수’, ‘중복 코드를 방지하고 모듈의 재사용성 증대’ 가 있습니다.

본인은 쉽게 발견하지 못하는 실수를 다른 사람은 금방 발견하여 코드의 부작용(side effect)과 오류를 좀 더 일찍 조치할 수 있으며,
정해진 표준 준수를 통해서 많은 사람들의 개발 결과물이 일관된 스타일을 유지할 수 있도록 도와줍니다.
또한, 동일한 역할을 수행하는 중복 코드를 빨리 발견하고 이미 만들어진 코드를 재사용할 수 있도록 수정할 수 있습니다.

다른 사람의 잘 만들어진 코드를 보면서 배울 기회를 얻습니다.
같은 환경에서 개발을 진행하더라도 개인별로 해당 언어나 프레임워크에 대한 이해도와 경험은 크게 차이가 날 수 있습니다.  
이러한 개인 간의 격차를 해소하는 가장 좋은 방법이 바로 코드리뷰이며 이를 통해 조금 더 좋은 방법을 제시해주고 이해 수준을 상향 평준화하는 것입니다.
전체적인 조직의 역량을 강화하는 중요한 역할을 합니다.

코드리뷰가 없고, 다른 사람이 어떤 부분을 어떻게 개발하고 있는지 모르는 상황에서는 특정한 문제가 발견했을 때 그 원인이 누구의 코드에 있는 지를 찾으려는 모습을 자주 확인할 수 있습니다.
코드리뷰 문화가 정착되면 특정 코드에 문제가 발생했을 때 누군가에게 책임을 묻거나 비난하는 문화를 없앨 수 있습니다.
즉, 배포된 코드에 문제가 있어서 서비스의 장애나 이슈가 발생한 경우 그 문제는 코드를 개발한 사람뿐 만 아니라, 해당 변경사항을 확인한 모든 사람이 연관되어 있기 때문에 그 책임이 누구에게 있는지를 찾기보다 왜 그 문제를 사전에 발견할 수 없었는지에 초점을 맞출 수 있게 됩니다.
다시 말해, 코드리뷰의 핵심은 ‘개발 결과물에 대한 책임이 그 코드를 만든 사람 개인에게 있지 않고, 우리 모두에게 있다는 문화를 정착하는 것’에 있습니다.


## 코드 리뷰의 규칙
a. 개선이 왜 필요한지 충분한 이유를 같이 설명합니다.
    ex : “data라는 이름은 현재의 자료구조가 무엇인지 그 의도를 알기가 어렵네요. 학점 정보를 담고 있는 자료구조 같은데 이와 관련된 변수명을 짓는다면 현재 정의한 자료구조가 무엇인지 그 의도를 쉽게 파악할 수 있을 것 같아요.”

b. 코드를 클린하게 유지하고, 일관되게 구현할 수 있도록 안내합니다.
    ex : "함수를 선언하는 두 가지 방식(함수 표현식, 함수 선언식)을 사용했는데 특별한 이유가 아니라면 함수를 선언하는 방식을 스스로 정하고 그 컨벤션 규칙을 따르도록 해보세요. 일관되게 동작하는 코드는 훨씬 보기 좋고 쉽게 수정할 수 있습니다.
            그리고 reduce를 통해서 새로운 자료구조를 만든 건 잘했습니다. 하지만 같은 반복처리를 하는 과정에서 calculateEarningRate 에서 for문을 사용한 건 아쉽네요. reduce와 비슷한 방식의 다른 고차 함수를 찾아서 써보면 더 일관된 코드를 유지할 수 있을 거 같습니다."

c. 리뷰를 위한 리뷰를 하지 말고, 피드백 할게 없다면 칭찬해 주세요.
    ex : 

코드량이 적당해서 읽기 편하네요.
많은 고민이 코드에서 엿보이네요.
성능에 아주 유리한 코드라고 생각되네요.
전에 코드보다 훨씬 좋아진 거 같네요.
예외 처리가 꽤 꼼꼼해서 좋네요.
함수, 변수명이 직관적이어서 좋네요.
  번외. 직접적인 리뷰를 하지 않거나, 숙제처럼 느끼지 않도록 소통을 많이 하라는 규칙도 있으나 프로젝트 수행의 납기를 위해 제외합니다.


## 코드 리뷰의 방식
a. 온라인 코드 리뷰
온라인 코드 리뷰는 말 그대로 도구를 이용하여 온라인상에서 진행하는 방식.

일반적으로 한 명의 코드를 리뷰하는 사람은 적게는 1명에서 많게는 5명 이상까지 다양하게 진행하고 버전 관리 시스템, 이슈 트랙킹 시스템과 연동해서 해당 코드가 어떤 부분을 수정했는지, 어떤 이슈와 관련되어 있는지 쉽게 파악할 수 있도록 도와줍니다.

대표적인 코드리뷰 도구로는 Crucible, GitLab, Phabricator, Rhodecode 등이 있다. 만약 버전 관리 도구로 git을 사용하고 있다면 별도의 도구를 사용하지 않아도 github의 기본적인 pull request를 통해서 자연스럽게 온라인 코드리뷰를 진행할 수 있습니다.

일반적으로 온라인 코드 리뷰는 코드의 작성자가 변경사항에 대한 코드 리뷰를 요청하고, 리뷰어들은 해당 코드의 피드백을 작성하는 방식으로 진행됩니다.
만약, 코드 수정이 필요하다면 코드 작성자는 수정 사항들을 반영한다. 이 과정이 완료되면 리뷰어들은 코드의 최종 확인을 완료합니다.

예를 들어,
버전 관리 시스템의 특성에 따라 조금씩 다르지만 github의 경우 리뷰어가 해당 코드를 머지(merge)할 수 있는 권한이 있다면 최종 확인 후 코드를 머지하거나, 해당 코드가 최종적으로 확인되었음을 메시지로 표시합니다.

Github의 경우, ‘PULL_REQUEST_TEMPLATE’ 템플릿 파일을 이용하면 Pull Request의 가이드를 미리 작성할 수 있습니다.
이 가이드에 체크리스트를 미리 추가해두게 되면 개발자는 Pull Request를 보내면서 놓친 부분이 없는지 미리 점검하는 데에 이용할 수 있습니다.

b. 팀 코드 리뷰
온라인 리뷰와 반대로 팀 구성원들이 주기적으로 오프라인에서 진행하는 리뷰입니다.

팀 리뷰는 반드시 특정 코드에 대한 검토 형식으로 진행할 필요는 없습니다.
팀 리뷰 자체도 크게 보면 ‘자유롭고 가벼운 방식의 코들 리뷰’이기 때문에 다양한 주제를 가지고 진행할 수 있습니다.

예를 들어, 온라인 코드리뷰 과정에서 나왔던 내용을 기반으로 자유로운 토론을 진행할 수도 있고, 좋은 사례를 전체적으로 공유하는 시간으로 진행할 수도 있다. 또한, 자신이 궁금했던 점을 질문하거나 온라인 코드리뷰 과정에서 개선되었으면 하는 점을 제안할 수도 있습니다.



## 코드 리뷰의 유형
a. 클린 코드

    가독성이 좋고, 유지 보수가 뛰어나며 코드를 작성한 의도와 목적이 명확하여 다른 사람이 쉽게 읽을 수 있는 소스코드

b. 코드 스멜 제거
    코드스멜 : 소스코드에서 문제(Problem)가 될 수 있는 부분. 나쁜 소프트웨어 디자인 또는 나쁜 프로그래밍 습관으로 인해 발생하는 소스코드

c. 시큐어 코딩
    보안취약점(vulnerability)을 배제하기 위한 코딩 기법



## 코드 리뷰의 주의점
a. 코드의 맥락(CONTEXT)을 이해할 수 있는 설명을 추가할 것

    개발자에게 PR 메시지나 커밋 메시지에 개발한 코드의 목적이나 다른 개발건과 연결된 이슈들을 적도록 가이드

b. 하나의 이슈(버그, 기능추가)당 하나의 코드리뷰
    개발자에게 리뷰가 산만해지지 않도록 하나의 PR이나 커밋에 너무 많은 내용을 넣지 않도록 가이드

c. 리뷰 받는 코드는 한 번에 500줄 이하
    너무 많은 개선을 한번에 넣을 경우 개발 및 리뷰할 때 놓치는 경우가 생기므로, 개발자에게 개선하는 코드 양이 너무 많아지지 않도록 가이드

d. 주관적인 의견을 표현하는 방식을 주의
    코드 리뷰를 진행하다 보면 각자의 견해 차이가 발생할 수 있으므로 자신의 방식이 정답이라는 생각을 버리고, “나의 의견은 이러한데 당신은 어떻게 생각하시나요?”와 같이 부드럽게 표현하며 코드 리뷰 진행

e. 리뷰를 너무 미루지 말 것

    한창 일이 바쁠 때 코드 리뷰를 해야 하는 상황이 생기면 누구나 잠시 뒤로 미루게 되지만, 리뷰가 미뤄지면 개발자의 불편함을 초래하고 코드 충돌에 의해 리뷰 번복이 발생할 수 있으므로 온라인 코드 리뷰의 경우 24시간 내, 팀 리뷰의 경우 최대한 빨리 코드 리뷰 진행

# 클린 코드
## 클린 코드란
"클린 코드는 '한 가지'를 제대로, 잘 한다." - 비야네 스트롭스트룹(Bjarne Stroustup), C++ 창시자 
"클린 코드는 단순하고 직접적이다. 클린 코드는 잘 쓴 문장처럼 읽힌다.(가독성)" - 그래디 부치(Grady Booch), 객체지향 전문가
"클린 코드에는 의미 있는 이름이 붙는다." - 데이브 토마스(Dave Thomas), OTI 창시자
"클린 코드를 읽으며 짐작했던 기능을 각 루틴이 그대로 수행한다." - 워드 커닝햄(Ward Cunningham), 위키 창시자
"코드를 읽는 시간 : 짜는 시간 = 10 : 1 의 비율만큼 코드를 읽는 시간이 길다." - 로버트 C. 마틴(Rober C. Martin), 클린 코드 전문가
→ 가독성이 좋고, 유지 보수가 뛰어나며 테스트 코드가 존재하는 코드로 코드를 작성한 의도와 목적이 명확하여 다른 사람이 쉽게 읽을 수 있습니다


## 의미있는 이름
a. 의도를 분명히 밝혀라
    코드를 읽었을 때 어떤 의미인지 알 수 없다면, 정보가 충분하지 않다는 것이며, 변수를 보자마자 의미가 명확해야 합니다.
   int x, List list1 처럼 무의미한 변수명을 피하고 status_value, cell 처럼 직관적인 변수명을 씁니다.

b. 그릇된 정보를 피해라
    변수명을 뜻이 있게 축약하거나 유사한 단어를 사용하여 혼동을 주면 안됩니다.
    hypotenuse(직각삼각형)을 hp 로 축약하거나 account를 담는 컨테이너가 List가 아니라면 accountList라고 명명하지 않습니다.

c. 의미있게 구분하라
    변수 이름으로 a1, a2 같게 사용하지 말고, productInfo가 존재한다고 의미 차이가 없는 productData를 변수명으로 사용하지 않음며, 읽는 사람이 차이를 알 수 있도록 명명합니다.

d. 발음하기 쉬운 이름을 사용하라
    genymdhms 처럼 의미만 우겨넣은 변수명 보다 generationTimestamp 같은 변수명을 사용합니다

e. 검색하기 쉬운 이름을 사용하라
    sum += 5; 같은 경우 5의 의미를 확인할 수 없으므로 상수 const int WORK_DAYS_PER_WEEK = 5; sum += WORK_DAYS_PER_WEEK; 처럼 검색하기 쉬운 상수로 사용하여 여러 곳에서 사용할 수 있도록 해야 합니다.


f. 유형이나 범위를 넣지 말라
    변수 이름에 타입이나 자료형을 넣지 않습니다. 타입이나 자료형을 바꾸면서 변수명을 바꿔야 하며, 적어놓아도 크게 유의미 하지 않습니다.

g.  한 개념에 한 단어를 사용하라
     추상적인 개념에 단어 하나를 선택해 이를 고수합니다.
     똑같은 메서드를 클래스마다 fetch, retrieve, get으로 각각 부르면 혼란스럽습니다. 

h, 기술 영역에서 가져온 이름을 사용하라
     전산 용어, 알고리즘 이름, 패턴 이름, 수학 용어 등은 굳이 번역하지 말고 그대로 사용합니다.
     적절한 기술용어가 없다면, 도메인 영역에서 이름을 가져와서 추후 도메인 전문가에게 의미를 파악할 수 있도록 합니다.

i. 의미 있는 맥락을 추가하고, 불필요한 맥락을 없애라
   변수들이 모두 우편주소와 관련되어 있다면, addr을 접두어로 붙이면 이해하기 좋아지고, 휘발유 충전소라는 프로그램을 짰을 때 모든 클래스명에 Gas Station → GS를 넣겠다는 생각은 바람직하지 않습니다.

## 주요 원칙
a. Follow Standard Conventions
    Coding 표준, 아키텍처 표준 및 설계 가이드 준수

b. Keep It Simple, Stupid (KISS)
    단순한 것이 효율 적이며, 복잡함을 최소화

c. Boy Scout Rule
    캠프장은 처음 왔을 때보다 더 깨끗하게 해놓고 떠나라. → 참조되거나 수정되는 코드는 원래보다 깨끗하게 유지 → 변수 이름 하나 개선, 긴 함수를 분할, 중복을 제거, 복잡한 if 문 하나 정리하면 충분

d. Root Cause Analsis
    근본적인 문제를 체계적으로 예방하고 해결하는 것이 훨씬 더 효과적

e. Do Not Multiple Languages in One Source File
    하나의 파일은 하나의 언어로 작성


## 디자인 원칙 (SOLID)
a. SRP (Simple Resopnsibility Principle)
   하나의 클래스는 하나의 책임만 가져야 합니다.

b. OCP  (Open/Closed Principle)
    클래스는 확장에 대하여 열려 있어야 하고, 변경에 대해서는 닫혀 있어야 합니다.

c. LSP (Liskov Substitution Principle)
    파생 클래스의 메소드는 기반 클래스의 메서드를 대체하여 사용될 수 있어야 합니다.

d. ISP (Interface Segregation Principle)
    클라이언트가 사용하지 않는 메서드에 의존하지 않아야 합니다.

e. DIP (Dependency Inversion Principle)
    추상화된 것은 구체적인 것에 의존하면 안됩니다. (자주 변경되는 구체적인 것에 의존하지 말고 추상화된 것을 참조)


## 주석
a. 주석은 나쁜 코드를 보완하지 못합니다.
    코드 품질이 나쁠 때 주석을 추가 하지 말고 코드를 정리해야 함

b. 코드로 의도를 표현해야 합니다.
    주석을 장황하게 적기 보다 변수, 함수명으로 충분히 의도를 표현해야 함

c. 좋은 주석
    - 법적인 주석                                                                                 ex) copyright
    - Pattern의 결과를 표현하는 주석                                                 ex) kk:mm:ss EEE, MMM dd, yyyy 형식
    - 구현 의도를 설명하는 주석                                                         ex) 스레드를 대량 생성하는 방법으로 경쟁 조건을 만듭니다.
    - 모호한 인수나 반환값을 명료하게 밝히는 주석                          ex) a.compareTo(a) == 0; // a == a
    - 결과를 다른 개발자에게 경고하는 주석                                      ex) 여유 시간이 충분하지 않다면 실행하지 마세요.
    - 자칫 대수롭지 않게 여겨질 중요성을 강조하기 위한 주석         ex) trim으로 공백을 제거하여 다른 문자열로 인식될 위험을 제거합니다.

d. 나쁜 주석
   내용이 없거나, 같은 이야기를 중복하거나, 오해할 여지가 있거나, 당연한 사실을 언급하거나, 함수나 변수로 표현할 수 있거나, 위치를 표현하거나, 과거 코드를 주석 처리하거나, 전역 정보를 포함하거나, 너무 많은 정보를 기술한 주석


## 코드 컨벤션
a. 본인이 작성한 코드는 반드시 다른 사람이 읽고 사용하기 때문에 누구나 쉽게 읽을 수 있는 코드를 작성해야 합니다.
    읽고, 관리하기 쉬운 코드를 작성하기 위한 일종의 코딩 스타일 규약을 코드 컨벤션이라고 합니다.
    프로그램의 성능을 해치지 않은 범위 내에서 가독성과 관리 용이성을 우선해야 합니다.

b. 표기법
    - 카멜 표기법 : 처음에는 소문자로 시작하며 2번째 단어부터는 첫글자가 대문자로 시작. 조합하는 단어는 보통 명사를 사용해야 하나, 메서드에서 첫번째 시작하는 단어는 동사로 시작하는 것을 권장. JAVA 진영에서 주로 사용.
    - 파스칼 표기법 : 모든 단어의 첫글자가 대문자로 시작. 쌍봉낙타법이라고도 함. 파스칼 진영에서 주로 사용.
    - 헝가리안 표기법 : 변수명의 앞에 자료형을 붙이는 것.  C언어 진영에서 주로 사용했으나 지금은 지양하는 분위기.
    - 스네이크 표기법 : 단어는 모두 소문자로 쓰되 단어간의 구분은 밑줄로 대체를 하는 방식. 전역변수나 상수 등을 구분하기 위해서 사용.
    - 케밥 표기법 : 단어는 모두 소문자로 쓰되 단어간의 구분은 하이픈으로 대체를 하는 방식. 많은 언어가 하이픈을 지원하지 않기 때문에 사용하는 예는 상당히 제한적. 주로 프로퍼티(properties)에 값 설정, CSS, 일부 HTML에서 사용.

c. 변수명 작성 가이드
    - 클래스나 메소드명은 파스칼 표기법을 따른다                    ex) HelloWordl, NameViva
    - 변수, 파라미터 등은 카멜 표기법을 따른다.                         ex) helloWordl, nameViva
    - 메서드 이름은 동사/전치사로 시작한다.                              ex) countNumber, withUserId
    - 상수는 영문 대문자 스네이크 표기법을 따른다.                  ex) public final int SPECIAL_NUMBER = 1;
    - (지역 변수 or private 변수)명은 '_'로 시작한다.                   ex) _privateVariableName
    - URL, HTML 같은 범용적 대문자 약어는 그대로 사용한다.   ex) parseHTML

    - 명사는 주어(클래스), 목적어(매개변수,변수)로 사용됨을 인식하고 변수명을 정해야 합니다.
    - 동사(매서드)는 행위를 나타냅니다.
       동사 원형을 사용하는 경우는 함수의 메서드를 첫 단어로 사용한다.(동사와 명사가 하나에 복합어로 사용될 때는 동사가 앞에 나옵니다.)
       과거분사는 형용사라고 생각하고 사용하자, 수동의 의미 , boolean 변수에 사용됩니다.
    - 일반적으로 리스트는 복수, 리스트의 아이템은 단수로 사용한다. 리스트는 가급적 복수형으로 작성합니다.
    - 중복된 단어를 제거합니다

d. 그외 가이드
   - 들여쓰기 : space와 tab을 섞어서 사용하지 않습니다.
   - 문장의 종료 : 한 줄에 하나의 문장만 허용하며, 문장 종료 시에는 반드시 세미콜론(;)을 사용한다.
   - 전역변수 지양 : 전역 변수는 언제든지 프로그램의 모든 부분에서 접근할 수 있기 때문에 편하지만, 바꿔 말하면 프로그램의 모든 부분에서 변경될 수 있고, 그로 인해 프로그램에 치명적인 오류를 발생시킬 수 있다.

# 코드 스멜
## 코드스멜이란
소스 코드에서 더 심오한 문제를 일으킬 가능성이 있는 부분

나쁜 소프트웨어 디자인이나 나쁜 프로그래밍 습관으로 인해 발생함
컴파일 시 나타나는 문법적 오류나 경고를 말하지 않음
버그가 아니기에 동작이 문제 없고, 알려주더라도 잘못된 것인지 인지하기 어려움
여러가지 기준과 체크 방법이 있으며 코드리뷰나 PR 시에 이러한 기준을 두고 상대방과 코드에 대한 소통하는 편이 여러가지로 도움이 됨



## 코드스멜의 종류
a. 중복된 코드
    기능이나 데이터, 코드가 중복 → 중복의 제거

b. 긴 메서드
    메서드의 내부가 너무 김 (20라인 이상) → 메서드를 적정 수준의 크기로 분할

c. 커다란 클래스
    한 클래스에 너무 많은 속성과 메서드가 존재 (200라인 이상) → 클래스 몸집을 줄임

d. 너무 많은 매개변수
    메서드의 매개변수가 너무 많음 (3개 이상) → 매개변수의 개수를 줄임

e. 확산적 변경 ( Divergent Change )
    하나의 클래스가 다른 이유로 인해 다른 방법으로 자주 변경 → 하나의 클래스가 하나의 책임을 가지도록 수정

f. 여러 클래스 동시 수정 ( Shotgun Surgery )
    특정 클래스 변경을 할 때마다 많은 클래스를 조금씩 수정해야 함 → 여러 클래스에 흩어진 유사 기능을 하나의 클래스로 모음

g. 기능에 대한 욕심 ( Feature Envy )
    메서드가 자신이 속한 클래스보다 다른 클래스의 데이터를 가져와서 기능 수행 → 메서드가 애용하는 데이터가 있는 클래스로, 메서드를 이동

h. 데이터 뭉치 ( Data Clumps )
    같은 구조의 매개변수 그룹들이 있음 → 해당 메서드의 매개변수 리스트를 추출한 후 일정한 패턴의 매개변수 그룹을 추출

i. 기본형에 대한 집착 ( Primitive Obsession )
   관련 데이터 들을 그룹을 만들지 않고, 기본형으로만 사용 → 자료구조를 정의하고, 그 자료구조를 다루는 함수를 같이 제공

g. Switch 문
    여러 코드에서 비슷한 조건에 따른 분기가 자주 발생 → 다형성 활용. 그러나 하나의 메서드에서만 영향을 끼친다면 바꿀 필요 없음

h. 평행 상속 구조 ( Parallel Inheritance Hierarchies )
    Shotgun Surgery의 특별 케이스로 한 클래스의 서브클래스를 만들면, 다른 곳에도 모두 서브클래스를 만들어 주어야 함 → 한쪽 상속 구조의 인스턴스가 다른 쪽 구조의 인스턴스를 참조하도록 만듬

i. 게으른 클래스
   어떠한 메서드에서도 객체 생성이 되지 않고 메서드 호출을 당하지 않는 클래스가 존재 → 슈퍼클래스와 서브클래스의 하는 일 차이가 없다면 슈퍼클래스로 병합하고, 거의 필요 없는 클래스는 인라인 클래스를 적용

j. 추측성 일반화
    충분한 일을 하지 않는 추상 클래스가 존재 →  어떤 클래스나 메소드가 적절한 기능을 이용하는 테스트 케이스에 대한 헬퍼(helper)인 경우를 제외하고 병합하거나 인라인 클래스 적용

k. 임시 필드
    복잡한 알고리즘이 여러 변수를 필요로 할 때 특정 상황에만 사용되는 인스턴스 변수가 존재 → 필요한 변수와 메서드를 묶어 클래스로 추출

l. 메시지 체인
    긴 줄의 getThis 메소드 또는 임시변수의 시퀀스로 표현되는 메서드의 호출 연결고리가 너무 복잡함 → 클라이언트가 객체의 위임 클래스를 직접 호출하고 있는 경우 서버에 위임 메서드 생성 후 서버 호출

m. 미들 맨
     무분별한 캡슐화로 인해  메서드의 대부분을 다른 클래스로 위임 → 위임을 제거하거나 인라인 메서드를 적용

n. 부적절한 친밀
    두 클래스가 밀접하게 연결됨. 다른 클래스에 지나치게 의존하는 클래스. → 공통된 부분을 별도의 클래스를 만듬. 서브 클래스를 위임 메서드를 통해 슈퍼 클래스로 부터 분리

o. 다른 인터페이스를 가진 대체 클래스
    다른 클래스의 두 메서드가 같은 일을 하지만 다른 메서드 명을 가짐 → 메서드 명 변경. 그것으로 부족할 경우 메서드의 구현이 동일하게 되도록 메서드 추출 후 동일하게 동작하게 한 뒤 클래스 하나를 삭제

p. 불완전한 라이브러리 클래스
    라이브러리에 있었으면 하는 메서드가 없음 → 해당 서버 클래스의 인스턴스를 첫번째 인자로 가지는 메서드를 클라이언트 클래스에 만듬

q. 데이터 클래스
     클래스의 메서드가 get/set 메서드로만 이루어짐 → 해당 데이터가 존재하는 위치로 메서드 추출

r. 거부된 유산 ( Refused Bequest )
    상속 받은 것들을 모두 사용하지 않음 → 사용하지 않는 부분이 있다면 서브클래스로 위임을 하고 슈퍼클래스는 공통적인 부분 남김

s. 주석
   주석을 써야 할 것 같은 생각이 들면, 먼저 코드를 리팩토링 하여 주석이 불필요하도록 함


## 추가 사항
### 클래스 내부
주석을 달아야 한다면 항상 What보다는 Why에 대해 적도록 하고 기계를 향해 적는 것이 아니라 사람을 향해 적는 것임을 잊지 말아야 하며 최대한 주석이 필요 없는 구조가 좋음
너무 로직이 거대해지지 않도록 하며 객체 지향 프로그래밍을 지향함
메서드 명으로 무슨 메서드인지 설명하기 어렵다면 명칭을 바꾸거나 재작성
표준 용어를 사용
필요하지 않은 코드들 및 미래에 쓸 것이라고 예상되는 코드들, 매개변수들은 제거
같은 동작을 다르게 구현했다면 중복코드와 같음


### 클래스와 클래스 간
가능한 public을 제거
모든 작업을 Delegating 시키는 클래스는 중간 클래스 혹은 Wrapper들을 제거
클래스의 주요 목적과 달리 비대해지는 기능이 있다면 따로 분리

# github 온라인 코드 리뷰 가이드
Git 브랜치 생성 권한이 개발자에게 있는 경우, Git 브랜치 만들어 작업하기

한 프로젝트에 참여하는 사람들은 모두 다른 일을 합니다.
누군가는 새로운 기능을 만들고, 또 다른 누군가는 버그를 고칩니다.
그래서 각자의 작업을 할 때 서로의 영향을 받지 않고 독립적으로 작업할 수 있도록 브랜치를 사용하는 것입니다.
브랜치는 나중에 다른 브랜치에 병합(Merge)하여 작업을 모을 수 있습니다.

git switch 명령어로 브랜치를 생성하거나
eclipse 에서 repository 와 연동된 프로젝트 선택 후. 우클릭 후 new branch를 이용합니다.


개발을 마친 후 commit, push를 진행합니다.



Pull Request 생성하기

Pull Request를 만드는 방법은 여러가지가 있습니다. 처음 브랜치를 푸쉬할때 나오는 링크를 따라가셔도 되고,
푸쉬를 한 뒤 GitHub 프로젝트 저장소에 들어가면 나오는 알림을 따라가셔도 되고,
직접 GitHub 프로젝트 저장소의 Pull Request 탭에 들어가 New pull request 버튼을 누르셔도 됩니다.
브랜치를 확인한 뒤 Create pull request 버튼을 클릭합니다.


이제 리뷰를 받기 위해 내가 한 작업에 대해 적을 시간입니다. 제목은 내가 한 작업을 간략히 요약해서 적고 내용에는 작업한 내용과 중점적으로 확인 받았으면 하는 부분 등을 상세하게 적습니다.

예시)
## 작업 개요
- 회원 가입 페이지 구현

## 상세 내용

기존에 만들어진 Input, Button, Checkbox 컴포넌트를 이용해서 회원 가입 페이지를 구현했습니다.

- 기존 Input 컴포넌트를 Composition 해서 회원 가입 폼에 쓸 컴포넌트를 만들었는데 이렇게 해도 되는걸까요?
- 지금 폼의 상태 관리 로직을 개선할 방법이 있을까요?


우측에 있는 Reviewers를 클릭하고 리뷰를 요청할 사람들을 선택합니다.
마지막으로 Create pull request 버튼을 클릭하면 Pull Request가 만들어집니다.



## 코드 리뷰 하기

코드 줄의 맨 앞 공간을 클릭하면 아래와 같이 해당 줄에 의견을 남길 수 있습니다.

Add single comment 를 클릭하면 바로 의견이 남겨집니다.

Start a review 를 클릭하면 작성자에게 보이지 않는 임시 등록 상태가 되고 나중에 리뷰를 완료하면 작성한 의견들이 한번에 등록됩니다.



앞에서 했던 것처럼 클릭하는 대신 드래그를 하면 여러 줄에 대한 의견도 남길 수 있습니다.


의견을 다 남겼다면 우측 상단의 Finish your review 버튼을 클릭하여 리뷰를 끝마칠 수 있습니다. 여기서는 리뷰를 끝냈다는 코멘트를 남기거나, 고생했다는 말을 합니다. 물론 코드에 대한 얘기를 더 해도 됩니다.

마지막으로 일반적인 피드백을 주는 Comment , 이제 합쳐도 괜찮을 것 같다는 Approve , 확실하게 코드를 수정하고 넘어가야 하는 경우에는 Request changes를 선택하고 Submit review를 클릭하시면 됩니다.



리뷰 요청을 받았다면 해당 Pull Request내의 Files changed 탭에 들어가 리뷰를 시작할 수 있습니다.




## 코드 리뷰 반영하기
코드 리뷰를 받으면 Pull Request 페이지에서 아래와 같은 식으로 리뷰들이 남겨집니다. 여기서 더 대화를 하면서 개선 방향을 찾아 나가거나 바로 의견을 수렴하여 코드를 수정해도 됩니다.

반영된 부분은 Resolve conversation 을 클릭하여 처리 완료됨을 표시해 주면 좋습니다.



리뷰를 마친 뒤에 코드가 더 수정되었다면 리뷰어에게 다시 리뷰를 요청할 수 있습니다.


리뷰어가 Pull Request를 승인하고 병합이 가능한 시점이 온다면 Merge pull request 혹은 그 옆의 화살표를 클릭하고 Squash 나 Rebase 등의 방식으로 브랜치 병합이 가능합니다. 여기까지가 한 번의 코드 리뷰 사이클입니다.