

# [jQuery]  선택자 



####  jQuery 선택자 (selector)

- jQuery 코드는 선택자와 메소드의 조합으로 구성되는 경우가 많음
- HTML 태그를 쉽게 선택하기 위해 선택자 사용

#### 선택자 구조

- ``$(“선택자”).메소드(매개변수, 함수 등);``
- ``$(“span”).hide();``
  - 큰 따옴표, 작은 따옴표 다 사용 가능

### 선택자 종류

- 직접 선택자

<img width="400" alt="image-20220621200327406" src="https://user-images.githubusercontent.com/101630615/174784987-ec8413ca-6741-41e4-a11d-b10c658b1a32.png">



#### 부모 요소 선택자



<img width="500" alt="image-20220621200340442" src="https://user-images.githubusercontent.com/101630615/174784992-ed62cbd4-665c-44a5-8f97-8f03feec0a10.png">



#### 형제 요소 선택자



<img width="500" alt="image-20220621200348436" src="https://user-images.githubusercontent.com/101630615/174785002-bbb12133-aad5-4b39-a5ca-30edd93a1c16.png">





### 필터 선택자

- 태그의 상태나 순서 등으로 선택
  - ``$(“태그명:순서필터”)``
  - ``$(“tr:odd”)`` : 홀수 행인경우
- ``$(“태그명:상태필터”)``
- ``$(“input:checked”)`` : 체크 상태인 경우

<img width="500" alt="image-20220621200411999" src="https://user-images.githubusercontent.com/101630615/174785011-95a2fe5c-5db9-43d2-9956-d882c3ff1a8b.png">



<img width="500" alt="image-20220621200419051" src="https://user-images.githubusercontent.com/101630615/174785014-f96e7ea2-f6d6-4c01-980b-ff0c3addde4f.png">



#### 속성 선택자

- 문서에 삽입된 HTML 태그(요소)의 지정된 속성 값에 따라 선택자로 정의

<img width="500" alt="image-20220621200426011" src="https://user-images.githubusercontent.com/101630615/174785016-82a255e3-013b-43df-89be-2da4d03cd41d.png">