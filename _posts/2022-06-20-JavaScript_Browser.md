

# [JavaScript] 브라우저 객체 모델



> 자바스크립트에서는 웹 페이지를 구성하는 HTML 태그의 모든 요소와 웹 브라우를 구성하는 요소들을 객체로 정의하여 제공
>
> 객체들을 계층구조로 분류

### 브라우저 객체 모델 (Browser Object Model)

- 웹 브라우저를 대상으로 이루어진 객체
- window : 창
- document : 문서
- history : 웹 브라우저 기록 정보
- location : 주소 정보
- navigator : 웹 브라우저의 종류 정보



#### 브라우저 객체의 계층 구조

<img width="600" alt="image-20220620214945461" src="https://user-images.githubusercontent.com/101630615/174605807-0cf0e909-f140-4c2c-a309-ccbffe173055.png">



#### window 객체

- 창에 대한 전반적인 상황을 제어하는 최상위 객체
- 자바스크립트에서 사용되는 모든 객체는 window 객체의 하위에 존재
- Navigator 객체만 제외하고 모든 객체는 window 객체를 통해서 접근하여 사용
- 그러나 사용시 window는 생략 가능

```
window.document.pic.src = “a.jpg”;

document.pic.src = “a.jpg”;
```

문서 내에서 name 속성이 pic인 객체의 src 속성

`````
<img name="pic" src="a.jpg">
`````



#### window 객체의 주요 속성

<img width="500" alt="image-20220620214956436" src="https://user-images.githubusercontent.com/101630615/174605824-5b74dd29-0da2-496e-a8ca-d0a720559329.png">





#### window 객체의 주요 메소드

<img width="500" alt="image-20220620215007593" src="https://user-images.githubusercontent.com/101630615/174605830-faef7ef5-6d93-4fb2-b4f5-de67ab8d619f.png">



#### window 객체의 ``open()`` 메소드

```
window.open(“URL”, “창이름”, “창 속성”);
```

- 새로운 창을 만들거나 기존 창을 열어서 화면에 출력하는 기능
- URL : 웹페이지 주소 및 HTML  파일명
  - 파일명이 없으면 새로 만들고 
  - 있으면 기존 파일 열기
- 창이름 : 새로 만들어지는 창 이름
- 창 속성 : 창의 모양이나 특징

```
window.open(“test.html”, “test”, “width=200, height=200, status=yes, scrollbars=yes, resizable=yes”);  

: test.htm 문서를 새창에서 열기
```



#### 타이머 설정  : ``setTimeout()``

```
setTimeout(‘호출함수’, 지연시간)

예: setTimeout(‘winClose()’, 1000);

1초 후에 winClose() 함수 호출
```

- 시간 설정
- 일정 시간이 지난 후에 호출함수를 1번만 실행

#### 타이머 해제 : ``clearTimeout(타이머ID)``

```
타이머ID = setTime(‘호출함수’, 지연시간);

setTimeout() 메소드가 반환하는 타이머ID를 받아서 타이머ID에 해당되는 타이머 설정 해제
```



#### 타이머 설정 : ``setInterval()``

```
setInterval(‘호출함수’, 지연시간)
: 일정 시간 간격 안에 반복 실행

예 : setInterval(‘showTime()’, 1000);
1초 간격으로 showTime() 함수 호출
```



#### 타이머 해제 : ``clearInterval(타이머ID);``

```
타이머ID = setInterval(‘호출함수’, 지연시간)
: 시간 설정한 것 해제
```



#### history 객체

- 최근 방문한 주소에 관한 정보를 기억하고 있는 객체



### 메소드

```
back() : 이전에 열었던 페이지로 이동

forward() : 이전 페이지로 이동 후 다시 앞으로 이동

go() : 몇 단계 뒤에 있는 페이지로 이동
go(3) : 3단계 앞의 페이지로 이동 
go(-2) : 2단계 다음 페이지로 이동
```



#### location 객체

- 현재 브라우저의 주소창에 표시된 주소값에 관련된 내용을 다루는 객체

<img width="500" alt="image-20220620215032058" src="https://user-images.githubusercontent.com/101630615/174605832-be6f399d-f298-4d1b-b88a-4119005384bf.png">



### 문서 객체 모델 (Document Object Model : DOM)

- 객체 지향 모델로써 구조화된 문서를 표현하는 방식
- HTML 문서에 접근하기 위한 표준 모델
- 표준은 대부분의 브라우저에서 DOM을 구현하는 기준
- 문서 내의 모든 요소를 정의하고, 각각의 요소에 접근하는 방법을 제공
- 웹 브라우저에 보여지는 HTML 문서 태그 요소에 대한 정보와 문서에 대한 여러 가지 속성 제공
- document 객체의 하위 객체를 이용하여 문서 내에서 일어나는 다양한 기능 제어
- document 객체의 하위 객체
  - ``layer, image, area, anchor, form`` 



#### DOM 사용 시기

- HTML 문서가 로드되고 나서 파싱 작업을 거쳐 DOM 트리 생성
- DOM 문서가 로드될 때 모든 DOM을 사용할 수 있게 되는 때가 되는 것임





#### document 객체의 주요 속성

<img width="500" alt="image-20220620215041983" src="https://user-images.githubusercontent.com/101630615/174605836-ad097597-3a83-452c-b47b-65ccd6597033.png">



#### document 객체의 주요 메소드

<img width="500" alt="image-20220620215050543" src="https://user-images.githubusercontent.com/101630615/174605837-b885985d-9901-4711-adaa-8f751bcc099f.png">



#### 문서 내의 요소(태그) 제어 메소드

<img width="600" alt="image-20220620215058753" src="https://user-images.githubusercontent.com/101630615/174605838-e3accdd6-5ab2-421b-9d66-577c3c156193.png">



#### 문서 내의 요소(태그) 제어 메소드 사용 시 주의점

- 문서 내에서 요소(객체)들이 생성되기 전에
- 자바스크립트를 선언하게 되면 요소를 선택할 수 없음

<img width="600" alt="image-20220620215107780" src="https://user-images.githubusercontent.com/101630615/174605840-ca2a1fb7-c742-471a-b336-74cef0f5e4c6.png">



#### 윈도우 이벤트 종류

- ``document (ready)``

  - 문서 객체 요소가 모두 로드되었을 때 발생

  - 문서 객체 요소가 자바스크립트에서 사용 가능한 상태인지 확인하고 작동이 가능한 상태일 때 발생

- ``load`` 
  - 문서 객체 요소가 모두 로드되었을 때 발생
  - 리소스, 이미지 또는 음악 등 로드가 완료된 상태



#### 문서 내의 요소(태그) 제어 메소드

- ``getElementById()``
  - id를 통해 문서 내에서 요소(태그)를 참조하는 메소드
  - 지정한 id 속성값을 갖는 개체 중 첫 번째 개체 참조

```
var 참조변수 = document.getElementById('abc');

<xxx id = "abc"...>;
```



#### ``getElementsByTagName(‘태그명’);``
- 문서 내의 모든 요소를 배열 컬렉션으로 전달받아서 참조할 수 있게 해주는 메소드
- 참조 값들은 배열로 만들어져서 전달

```
var tdArr = document.getElementsByTagName(‘td’);
```

- 문서 내의 ``<td>`` 태그 수가 배열 크기가 됨
- for 문 사용



#### 이벤트 핸들러와 이벤트 처리

- 사용자로부터 발생되는 여러 가지 이벤트 처리



#### 자바스크립트에서의 이벤트 처리 방식

<img width="500" alt="image-20220620215121210" src="https://user-images.githubusercontent.com/101630615/174605844-e997c120-34cb-4052-add9-a28c689aaa79.png">



<img width="500" alt="image-20220620215128510" src="https://user-images.githubusercontent.com/101630615/174605847-c1f1b197-4492-4b15-8776-f231bae0255e.png">



### 이벤트 리스너

```
객체.addEventListner(‘이벤트명’, function() {
});

객체.removeEventListner(‘이벤트명’, function() {
});
      
화살표 함수 사용 가능
객체.addEventListener(‘click’, () => {
});
```



#### 폼 유효성 확인

- form 객체
- document 객체의 하위 객체
- form 태그 내에 들어 있는 여러 입력 양식들 제어
- form의 하위 객체들

<img width="600" alt="image-20220620215147780" src="https://user-images.githubusercontent.com/101630615/174605849-57994f7c-9cdc-43e9-9336-53f27f31102f.png">



#### 폼 객체 사용 방법
(1) 태그의 name 속성을 객체로 사용하는 경우

```
<form name=”joinForm”>
<input type=”text” name=”id”>
joinForm.id.focus();
```

(2) 문서 객체 모델(DOM) 방식을 사용하는 경우

```
<input type=”text” id=”name”>
var name = document.getElementById(‘name’);
name.focus();
```



#### ``select``

- 리스트 박스에 있는 여러 항목 중 선택

- 항목 선택하면 selectedIndex 속성에 선택된 항목의 인덱스 값 저장 (0부터 시작)
- 하나도 선택하지 않으면 selectedIndex 값이 -1



#### ``radio`` 객체

- 그룹 중에서 1개만 선택 가능
- 그룹에 속한 여러 개의 라디오 버튼의 이름이 동일하므로 radio 객체는 배열 형태로 사용
- checked 속성이 true면 체크된 상태
- false면 체크되지 않은 상태

```
for(var i=0; i<joinForm.emailRcv.length; i++){
	if(joinForm.emailRcv[i].checked == true)
}
```

미리 선택되어 있다면 유효성 검사 필요X : checked

```
<input type = "radio" name ="emailRcv" value ="yes">예
<input type = "radio" name ="emailRcv" value ="no">아니오
```