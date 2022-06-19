

# [MySQL] 조인 (JOIN)



> 여러 개의 테이블을 결합하여 조건에 맞는 행 검색



#### INNER JOIN (내부 조인) - 가장 많이 사용

\-   공통되는 열이 있을 때

\-   공통 속성의 속성값이 동일한 튜플만 반환

   

![clip_image002](https://user-images.githubusercontent.com/101630615/173409964-d97caadf-9b76-44e3-bf6f-806fb1f60ffb.jpg)

![clip_image004](https://user-images.githubusercontent.com/101630615/173409970-b439a7a2-5d1c-461f-9de6-e9ca84eb81e1.jpg)

#### OUTER JOIN (외부 조인)

\-   공통되는 열이 없을 때

\-   공통된 속성을 매개로 하는 정보가 없더라도 버리지 않고 연산의 결과를 릴레이션에 표시

\-   값이 없는 대응 속성에는 NULL 값을 채워서 반환

\-  **좌측 외부 조인 (Left Outer JOIN)**

​	\-   좌측 릴레이션의 정보 유지

\-   **우측 외부 조인 (Right Outer Join)**

​	\-   우측 릴레이션의 정보 유지

\-   **완전 외부 조인 (Full Outer JOIN)**

​	\-   두 릴레이션의 모든 정보 유지 

![clip_image006](https://user-images.githubusercontent.com/101630615/173409976-54c69d79-f009-4ef8-b176-1f534ff7ff75.jpg)

### 조인 기본 형식

```
SELECT 열리스트

FROM 테이블명1

INNER JOIN 테이블명2

ON 조인조건 (기본키=외래키);
```



3개 테이블 결합

\-   조인 조건 2개

![clip_image008](https://user-images.githubusercontent.com/101630615/173409979-0f53b27d-443a-41ff-9fbf-4988cadb85cd.jpg)



### 서브 쿼리 (Subquery)

\-   하위 질의 또는 부속질의 라고도 함

\-   하나의 SQL 문 안에 다른 SQL 문이 중첩(nested)

\-   쿼리를 1차 수행한 다음, 반환값(결과)을 다음 쿼리에 포함시켜서 사용

\-   다른 테이블에서 가져온 데이터로 현재 테이블에 있는 정보를 찾거나 가공할 때 사용



#### 조인과 서브 쿼리의 차이점

#### 조인

\-   여러 테이블의 데이터를 모두 합쳐서 연산

\-   카티전곱 (15 x 3 = 45 행 반환) 후 조건에 맞는 행 검색

\-   데이터가 15행이 있는 테이블과 3행이 있는 테이블의 카티전곱 결과는 45행

\-   카티전 곱 연산 + SELECT 연산

#### 서브 쿼리

\-   필요한 데이터만 찾아서 제공

\-   15행을 검색한 결과를 가지고 3행에서 검색 

\-   총 18행 검색

\-   경우에 따라 조인보다 성능이 더 좋을 수 도 있지만

\-   대량의 데이터에서 서브 쿼리를 수행할 때 성능이 더 나쁠 수 있음

서브 쿼리의 구성 및 형식

\-   메인 쿼리와 서브 쿼리로 구성

 

![clip_image012](https://user-images.githubusercontent.com/101630615/173409980-226ce728-1cb9-453c-bbbc-b49ebddf56ac.jpg)

 

**단일 행 서브 쿼리**

\-   서브 쿼리 결과 같이 단일 행

\-   = 연산자 사용

 

**다중 행 서브 쿼리**

\-   서브 쿼리 결과 값이 여러 행

\-   IN, ANY, ALL, EXISTS 연산자 사용



**서브 쿼리 연산자**

\-   WHERE 절에서 사용

\-   데이터를 선택하는 조건 또는 술어와 같이 사용

![clip_image014](https://user-images.githubusercontent.com/101630615/173409983-a61a1eb2-636b-4ef8-99c9-1ec977772437.jpg)



# 관리 기능

 

### DCL (Data Control Language) : 데이터 제어어

\-   데이터의 사용 권한을 관리하는 데 사용

\-   데이터베이스 트랜잭션 명시 (완료/취소)

\-   권한 부여 및 취소

\-   GRANT : 데이터베이스 객체에 권한 부여

\-   REVOKE : 이미 부여된 데이터베이스 객체 권한 제거

 

#### 권한 (Privilege)

\-   특정 유형의 SQL 문을 실행하거나 다른 사용자의 객체를 사용할 수 있는 권리

권한의 종류

\-   시스템 권한

\-   객체 권한

​	\-   특정 객체를 조작할 수 있는 권한

​	\-   DML 사용 권한

​	\-   ``SELECT / INSERT / UPDATE / DELETE``

 

#### 백업 및 복구 (EXPORT / IMPORT)

\-   DB를 주기적으로 백업해 두거나 다른 서버로 이관할 때 사용

\-   백업 (EXPORT)

\-   복구 (IMPORT)

 

#### 백업 방법

\-   전체 단위 백업

\-   사용자 단위 백업

\-   테이블 단위 백업

 

### 백업 (EXPORT)

\-   메뉴 Server / Data Export

\-   백업할 데이터베이스/테이블 선택

\-   Export to Self-Contained File 선택하고

\-   파일 경로 및 파일명 지정

\-   Create Dump in a Single Transaction 체크

\-   [Start Export] 버튼 클릭

 

### 복구 (IMPORT)

\-   메뉴 Server / Date Import

\-   Import from Self-Contained File 

\-   복구할 파일 지정

\-   [New] 버튼 누르고 스키마 이름 정 (주의! 없는 이름으로 지정) / OK

\-   [Start Import]