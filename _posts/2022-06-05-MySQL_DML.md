

# [MySQL] 데이터 조작어 (DML)

  

### INSERT 문

\-   테이블에 새로운 행을 삽입하는 명령어

INSERT 문 기본 형식

```

INSERT INTO 테이블명 (열이름 리스트) VALUES (값리스트);

INSERT INTO 테이블명 VALUES (값리스트); 

: 모든 열에 값 저장

예시 : student 테이블에 행 삽입

INSERT INTO student (stdNo, stdName, stdYear, dptNo)
VALUES (‘2022001’, ‘홍길동’, 4, ‘1’);
```

 

### UPDATE 문

\-   특정 열의 값을 수정하는 명령어

\-   조건에 맞는 행을 찾아서 열의 값 수정

UPDATE 문 기본 형식

```
UPDATE 테이블명 SET 열=값 WHERE 조건;

예시 : 상품번호가 5인 행의 상품명을 ‘UHD TV’로 수정

UPDATE product SET prdName=’UHD TV’ WHERE prdNo=’5’;
```



### DELETE 문

\-   테이블에 있는 기존 행을 삭제하는 명령어

DELETE 문 기본 형식

```
DELETE FROM 테이블명 WHERE 조건;

예시: 상품명이 ‘그늘막 텐트’인 행 삭제

DELETE FROM product WHERE prdName=’그늘막 텐트’;

테이블의 모든 행 삭제

DELETE FROM product;
```



### SELECT 문

\-   테이블에서 조건에 맞는 행 검색

SELECT 문 기본 형식

![clip_image004](https://user-images.githubusercontent.com/101630615/173407121-2b2ad093-a2b8-47ed-bd2a-01f34c4a5b9b.jpg)

 

![clip_image006](https://user-images.githubusercontent.com/101630615/173407128-23d73822-a115-430d-b45f-63e2734c609d.jpg)

![clip_image008](https://user-images.githubusercontent.com/101630615/173407134-e219aa78-90ec-4d43-9bee-5928ede31fc8.jpg)

#### 중복 제거

\-   * 모든 열 출력

\-   ``DISTINCT``

\-   속성값이 중복되는 것이 있으면 한 번만 출력

![clip_image010](https://user-images.githubusercontent.com/101630615/173407139-ff5f0556-7f01-43ef-bd66-804047d6bd49.jpg)

IMPORT 할 시 **주의!**

\-   숫자 : INT

\-   나머지 : text 하고 나중에 변경

\-   모든 테이블에 기본키 제약조건 추가

\-   외래키 있는 테이블에 외래키 제약조건 추가



![clip_image012](https://user-images.githubusercontent.com/101630615/173407141-c8f470d1-3d98-45f0-b61c-ce6e13fd4704.jpg)

### 패턴 매칭 (LIKE)

![clip_image014](https://user-images.githubusercontent.com/101630615/173407143-606716f8-2169-4982-bac8-5f6fb7f26fba.jpg)

![clip_image016](https://user-images.githubusercontent.com/101630615/173407144-6d1e89a8-276e-43c7-9b7c-8547087e1a62.jpg)



#### ORDER BY

\-   특정 열의 값을 기준으로 질의 결과 정렬

\-   ASC : 오름차순 (생략 가능)

\-   DESC : 내림차순 



#### 집계 함수

```
SUM() : 합계

AVG() : 평균

COUNT() : 선택된 열의 행 수 (널 값은 제외)

COUNT(*) : 전체 행의 수

MAX() : 최대

MIN() : 최소
```



### GROUP BY 절

GROUP BY <속성>

\-   그룹 질의를 기술할 때 사용

\-   특정 열로 그룹화한 후 각 그룹에 대해 한 행씩 질의 결과 생성

   **주의!**

\-   SELECT 절에는 GROUP BY에서 사용한 열과 집계 함수만 나올 수 있음

![clip_image018](https://user-images.githubusercontent.com/101630615/173407147-4b439321-b10d-4dcb-a1b6-362bdf8be23c.jpg)



### HAVING 절

HAVING <검색 조건>

\-   GROUP BY 절에 의해 구성된 그룹들에 대해 적용할 조건 기술

\-   ``SUM, AVG, MAX, MIN, COUNT`` 등의 집계 함수와 함께 사용

\-   주의!

\-   반드시 GROUP BY 절과 같이 사용

\-   WHERE 절보다 뒤에

\-   <검색 조건>에는 SUM, AVG, MAX, MIN, COUNT 등의 집계 함수만 와야 함



### DDL (Data Definition Language, 데이터 정의어)

\-   CREATE / ALTER / DROP

\-   데이터베이스, 테이블, 뷰, 인덱스 등의 데이터베이스 개체를 생성/삭제/변경하는 역할

\-   직접 데이터베이스의 테이블에 영향을 미치기 때문에

\-   DDL 명령어를 입력하는 순간 처리 작업이 즉시 완료

\-   AUTO COMMIT

\-   따라서 작업 취소(ROLLBACK)이나 완료(COMMIT)을 수행할 필요 없음

### DML (Data Manipulation Language, 데이터 조작어)

\-   INSERT / UPDATE / DELETE / SELECT

\-   데이터를 삽입/수정/삭제/조회 하는데 사용

\-   대상은 테이블의 행

\-   조작 작업이 메모리 버퍼에서 수행되어 실시간으로 테이블에 영향을 미치 않음 (실수가 있었을 경우 작업 취소 가능) - 트랜잭션 발행

\-   DML 명령어가 실제 테이블에 반영되게 하기 위해서는 COMMIT 명령어를 입력하여 작업을 종료해야 함

 

### 트랜잭션 (Transaction)

\-   DBMS에서 데이터를 다루는 논리적인 작업의 단위

\-   데이터베이스 관리 시스템에서 회복 및 병행 수행 시 처리되는 작업의 논리적 단위로 사용

\-   하나의 트랜잭션은 정상적으로 종료될 경우 COMMIT 연산이 수행되고

\-   비정상적으로 종료될 경우 ROLLBACK 연산 수행해서 작업을 취소



### COMMIT 연산

\-   트랜잭션 처리가 정상적으로 종료되어

\-   트랜잭션이 수행한 변경 내용을 데이터베이스에 반영하는 연산

\-   내용을 변경한 트랜잭션이 완료되면 그 트랜잭션에 의해 데이터베이스는 새롭게 일관된 상태로 변경되고

\-   이 상태는 시스템에 오류가 발생되더라도 취소되지 않음

 

### ROLLBACK 연산

\-   하나의 트랜잭션 처리가 비정상으로 종료되어

\-   데이터베이스의 일관성이 깨졌을 때 트랜잭션이 행한 모든 변경 작업을 취소하고 이전 상태로 되돌리는 연산