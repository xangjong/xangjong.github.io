



# [JQuery] 개요



>  ### jQuery란?

- 2006년 존 레식 (John Resig)이 디자인 자바스크립트 라이브러리
- 자바스크립트를 이용해 만든 다양한 함수들의 집합
- 무료 사용 가능한 오픈 소스 라이브러리
- 모든 웹 브라우저에서 동작

### jQuery 특징

- jQuery 용량이 약 100KB로 가벼움
- 동적으로 HTML이나 CSS 컨트롤 능력 탁월
- 짧고 간결하게 코딩 가능
- 웹 표준과 타 브라우저 호환성 뛰어남 (크로스-브라우저 지원)
- 편리한 ``Ajax`` 호출 방법
- 메소드 체인 방식 (여러 메소드를 연결하여 사용)으로 효율적인 코딩 가능, 간결하고 효과적인 코드 수정 가능
- 다양한 플러그인 제공

#### jQuery 사용 목적

- 쉬운 DOM 처리
- 쉽고 일관된 이벤트 연결 구현
- 쉬운 시각적 효과 구현
- Ajax 기능 쉽게 구현



#### jQuery 개발 환경

1. jQuery 파일 다운로드 방식
   - 웹 애플리케이션에 HTML, CSS, JavaScript 파일들과 같이 jQuery 파일 있어야 함

2. CDN 이용하는 방식
   - Content Delivery Network
   - 사용자가 요청한 콘텐츠를 사용자와 가장 가까운 곳에 위치한 캐시 서버에서 전달해 주는 방식



### jQuery 기본

jQuery 코드 형태

- 객체 구조로 객체.메소드 형태
- 객체 선택
  - ``$(“선택자”).메소드``
- 사용자가 생성한 객체 사용
  - ``var obj = $(“선택자”).메소드;``
  - ``obj.메소드;``
- 메소드 체이닝
  - 여러 개의 메소드를 연결해서 사용하는 것
  - 객체.메소드1.메소드2. …



#### jQuery 치환

- jQuery의 모든 함수 및 객체는 jQuery에서 제공되는 것이라는 점을 나타내기 위해 코드 앞에 jQuery 키워드 사용

```js
jQuery(document).ready(function(){ … });
```

- 쉽게 하기 위해 $ 문자로 치환해서 사용

```js
$(document).ready(function(){ … });
```



#### ``$(document).ready(함수)``  명령어

- 화면에 페이지가 로딩되어 실행
- HTML 문서가 화면에 보여진 후에 자동으로 포함된 함수 실행
- 자바스크립트의 ``window.onload = function() { };``에 해당



#### ``$(document).ready()``와 ``window.onload = function()`` 

- 공통점
  - 콜백 함수가 호출되는 시점에서 DOM 요소에 접근 가능
- 차이점
  - ``$(document).ready()``
    - DOM 요소가 로드 되었을 때 이벤트 발생하면서 호출 (외부 리소스, 이미지 또는 사운드 등이 로드 되기 전)
  - ``window.onload = function() ``
    - DOM 요소 뿐 아니라 외부 리소스, 이미지, 사운드 등 모든 콘텐츠의 로드가 끝나는 시점에서 이벤트가 발생하면서 호출





### Query 변수

- 변수명 앞에 $ 붙임
  ``var $box1 = $(‘#box1’);``
- $box1의 타입은 Object로 jQuery 메소드 사용 가능
- ``$box1.css(‘color’, ‘red’);``

- ``var $divLen = $(‘div’).length;`` // ``<div>`` 태그 개수 저장
- $divLen의 타입은 Number 
- 이 경우 일반적으로 $ 붙이지 않음 (자바스크립트 변수)
- ``var divLen = $(‘div’).length;``



### jQuery DOM 요소 조작

- 동적으로 DOM 요소 조작
- jQuery를 이용하면 쉽고 간단하게 조작 가능
- DOM 요소 삽입 / 삭제 / 속성 추가 및 삭제 



#### DOM 요소 관련 주요 메소드

<img width="600" alt="image-20220621201156000" src="https://user-images.githubusercontent.com/101630615/174786356-7d450de6-2f79-4b07-92a0-42d843972ff8.png">



#### ``text()``와 ``html()`` 메소드

- 자바스크립트의 innerHTML 속성과 유사
- 선택한 DOM 요소에 글자(텍스트)를 설정하거나 반환
- ``html()``
  - HTML 태그 인식 (태그 효과 적용)
- ``text()``
  - HTML 태그 인식하지 못하고 글자로 인식



### DOM 요소의 속성 추가 및 삭제
- ``attr(속성명,값)`` : 속성 추가 (prop())
- ``removeAttr(속성명)`` : 속성 제거
- ``attr()`` : 속성 설정, 조회
- ``prop()`` : 활성화, 체크, 선택여부 등 동적 적용

