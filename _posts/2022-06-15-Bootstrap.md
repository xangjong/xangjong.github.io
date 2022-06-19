# [Bootstrap]

>  ### Bootstrap Framework

- jQuery 기반의 HTML5 Web Framework
- HTML, CSS,  JS 라이브러리
- 프론트엔드(웹 브라우저)에서 작동되는 프레임워크 
- 트위터에서 사용하던 각종 레이아웃, 버튼, 입력 요소 등의 UI 요소들을 누구나 사용할 수 있도록 만들어진 오픈 소스 프레임워크
- HTML/CSS 기반의 템플릿 양식, 버튼, 내비게이션 등 다양한 UI 요소 포함

>  #### Bootstrap 특징

- 쉽고 편리하게 사용할 수 있음
  - HTML/CSS 기본 지식만 있으면 누구나 사용 가능
- 반응형 웹 디자인 지원
  - PC 또는 스마트폰이나 태블릿 등의 모바일용 디자인 지원
- 모든 최신 브라우저와 호환

>  #### Bootstrap 기능

- CSS 기능 : 디자인이나 스타일 적용
- 컴포넌트 기능
  - 내비게이션바, 탭, 버튼 등의 기능을 간단하게 수정해서 사용 가능
- 자바스크립트 기능
  - 사용자의 액션과 상호작용하는 기능 제공

> #### Bootstrap 장점

- 쉽고 빠르게 다양한 기능 개발 가능
- 모바일 환경과 반응형 웹 제작 가능
- 수준 높은 퀄리티 제공
- 개발 시간 단축으로 개발 비용 절감
- 오픈소스이지만 상업적 이용 가능

> #### Bootstrap 단점

- 정형화된 디자인
- jQuery 의존성 높은 - 없어도 됨



#### Bootstrap 사용 방법

- **파일을 다운로드 받아서 사용**
- Bootstrap 파일 구성
  - css / js
  - jQuery 파일 필요
- CDN 이용
  - 링크를 통해 서버에서 제공 받는 방법

- Bootstrap 다운로드 : 4.61 버전으로 다운로드
- jQuery 다운로드 : https://jquery.com/
- 프로젝트 생성 : Bootstrap01
- Bootstrap 압축 해제한 후
  - css와 js 폴더 복사해서 
  - webapp 폴더에 붙여 넣기
  - js 폴더에 jQuery 파일 넣기

> #### 부트스트랩 사용법

- 정의된 다양한 클래스들을 HTML 태그에 적용하고 (class 속성에 지정)

- 부가적인 속성을 정의한 클래스들을 조합해서 사용

- ``<태그 class=”bs_class1 bs_class2 …”>``

- ```
  <button type=”button” class=”btn btn-primary”>
  
  <div class=”container bg-primary text-white”>
  ```

  

##### Layout

- containers
- Jumbotron
- Grid
- Button
- Table 
- Image
- Form

#### 컨테이너

- 레이아웃 최상위 요소로서 다른 요소 포함

```
<div class=”container”>

.container 
: 반응형 고정 폭 컨테이너

.container-fluid
:뷰포트 전체 폭까지 늘어나는 최대폭 컨테이너
```



#### Bootstrap 색상

<img alt="image-20220615165125944" src="https://user-images.githubusercontent.com/101630615/173782299-2c3a1f75-5bb1-43ff-8273-c0dbd5696ad2.png">

더 많은 컬러 참고 : [https://somgle.tistory.com/123](https://somgle.tistory.com/123)



##### Jumbotron

- 일종의 대형 전광판
- 특정 콘텐츠나 관심 있는 정보를 눈에 뜨게 보여주기 위한 큰 박스

##### Grid (그리드)

- 격자 모양으로 영역 분할 가능
- 1행을 12 등분해서 비율로 배치
- ``행 : class=”row”``
- ``열 : class=”col-숫자”``	
- 숫자 : 12 칸 중 차지하는 칸 수
- 필요에 따라 열을 묶어 더 큰 크기의 열로 사용 가능

##### col-scale-숫자 

```
col-scale-숫자 
: 12칸 중 차지하는 칸 수

col-숫자 : 가로 방향으로 배치

col-sm-숫자 
: 576px 이하이면 세로로 배치

col-md-숫자 
: 768px 이하이면 세로로 배치

col-lg-숫자 
: 992px 이하이면 세로로 배치

col-xl-숫자 
: 1200px 이하이면 세로로 배치
```



#### Button

- 버튼으로 사용할 수 있는 요소들에 ``class=”btn”`` 적용
- ``<a>, <button>, <input type="button">``
- ``<input type="submit">, <input type="reset"> ``
- 기본 : ``class=”btn”``
- 색상 설정 : ``class=”btn btn-primary”``
- 크기 설정
  - ``btn-lg, btn-md (디폴트), btn-sm``
- 테두리 표시
  - ``btn-outline-dark, btn-outline-primary``



#### 이미지 

- ``<img>`` 태그

```
rounded-circle
: 둥근 이미지

img-thumbnail 
: 썸네일 이미지, Rounded 1px border

float-left / float-right 
: 좌/우 정렬

mx-auto + d-block 
: 가운데 정렬

img-fluid 
: 브라우저 크기에 따라 변경
```



#### 테이블

- ``class=“table”``

```
table-bordered 
: 테두리 있음

table-borderless 
: 테두리 없음

table-striped 
: td 태그 흰색행/회색행 

table-hover 
: 행에 마우스 올리면 색상 변경

table-dark 
: 배경색을 검정색으로 설정
```