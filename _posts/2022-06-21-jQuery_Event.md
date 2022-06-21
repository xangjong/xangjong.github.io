

# [jQuery] 이벤트



### jQuery 이벤트

- 기존의 자바스크립트에서 사용했던 이벤트 대부분 사용
- jQuery를 이용하여 이벤트를 처리하면 훨씬 간단하고 쉽게 이벤트 처리 가능

#### 이벤트 사용 기본 구조

- ``$(‘#btn’).click(function() { .... });``

- (1) 이벤트 대상 : $(‘#btn’)

- (2) 이벤트 등록 메소드 (이벤트 유형) : click()

- (3) 이벤트 핸들러 (이벤트 처리 함수) : function() {..}

  

#### 이벤트 등록 메소드 유형

(1) 단독 이벤트 등록 메소드

```html
$(‘#btn’).click(function() { .... });
```

(2) 그룹 이벤트 등록 메소드 (여러 이벤트 적용)

```
$(‘#btn’).on(‘mouseover focus’, function() { .. } );
```



#### 이벤트 연결 방식

- 정적 연결
  - 현재 HTML 화면에 있는 태그에만 이벤트 연결
  - jQuery를 통해 새로 삽입되는 태그에는 이벤트 연결 안됨
- 동적 연결
  - 현재 HTML 화면에 표시된 요소와 앞으로 생성될 요소에 전부 이벤트 연결 가능



### 윈도우 이벤트 종류

<img width="500" alt="image-20220621195731921" src="https://user-images.githubusercontent.com/101630615/174783814-7a227dc5-22b3-4019-828b-569c5e325205.png">



### 마우스 이벤트 종류

<img width="500" alt="image-20220621195742452" src="https://user-images.githubusercontent.com/101630615/174783826-64474319-1647-4b1d-826d-952ed85ca4f1.png">



### 키보드 이벤트 종류

<img width="500" alt="image-20220621195749055" src="https://user-images.githubusercontent.com/101630615/174783836-a90b752d-15f4-4981-9f9d-77f1c242e8a7.png">



### 입력 양식 이벤트 종류

<img width="500" alt="image-20220621195756249" src="https://user-images.githubusercontent.com/101630615/174783838-3de310dc-56f8-4080-a9dc-88e87b61d0c3.png">



#### input 입력란에서 엔터키 쳤을 때 문제

- ``<input>`` 태그의 입력란에서 엔터키를 치면
- 무조건 submit 이벤트가 발생하면서 submit() 호출하고 서버로 전송되는 문제 발생

=> 엔터키 쳤을 때 submit 되지 않도록 문서 전체에 이벤트 처리 : [Enter] 키의 아스키 코드 값 : 13

```js
if(e.keyCode == 13) return false;
```

- 문서 전체에 이벤트 처리

