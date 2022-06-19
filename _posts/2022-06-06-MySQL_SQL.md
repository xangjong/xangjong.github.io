

# [MySQL] 데이터베이스 표준 질의어 

 

> 데이터 정의어 (DDL)
>
> 데이터 조작어 (DML)
>
> 데이터 제어어 (DCL)

  

### 데이터베이스 질의어

\-   데이터베이스를 구축하기 위한 도구로서

\-   현대 정보시스템에서 매우 중요한 역할 담당

\-   질의어 (Query Language)는 검색 언어라는 의미지만

\-   데이터를 검색하는 역할 외에 데이터의 입력, 수정, 삭제, 제어, 병행 제어, 복구 등 다양한 기능을 제공하는 종합적인 언어

 

### SQL (Structured Query Language)

\-   관계형 데이터베이스 관리 시스템(DBMS)의 데이터를 관리하기 위해 설계된 특수 목적의 프로그래밍 언어

\-   ‘에스큐엘’ 또는 ‘시퀄’로 읽음

\-   1970년대 말 미국 IBM사의 한 연구소에서 데이터베이스 유형에 관계없이 사용자들이 편리하게 사용하게 사용할 수 있는 질의어를 만들기 위해 개발

\-   초기에는 SEQUEL(Structured English Query Language, 구조 영어 질의어)이라는 이름으로 시작

\-   많은 수의 데이터베이스 관련 프로그램들이 SQL을 표준으로 채택하면서 

\-   자신의 제품에 특화 시킨 SQL 사용

![clip_image002](https://user-images.githubusercontent.com/101630615/173404666-b2c86890-c3ab-4480-86de-bdb46e80d350.jpg)

![clip_image004](https://user-images.githubusercontent.com/101630615/173404671-8d69c3ed-e81a-42ec-93db-d83f8560472d.jpg)

 



#### 데이터 정의어 (DDL)

\-   데이터베이스 / 테이블이나 관계의 구조를 생성하는데 사용

![clip_image006](https://user-images.githubusercontent.com/101630615/173404674-08fcd673-dde5-48cc-84ef-941a747710aa.jpg)

#### 데이터 조작어 (DML)

\-   테이블의 데이터를 검색, 삽입, 수정, 삭제하는데 사용

![clip_image008](https://user-images.githubusercontent.com/101630615/173404679-1f4c1a39-ea44-4512-a0d8-d134c68348fa.jpg)

데이터 제어어 (DCL)

\-   데이터의 사용 권한을 관리하는 데 사용

![clip_image010](https://user-images.githubusercontent.com/101630615/173404682-1138ab6d-dedf-4c05-a5ec-a8cb51ceea53.jpg)

 

 

#### 데이터 정의어 (DDL)

\-   CREATE / ALTER / DROP 문

 

##### CREATE 문

\-   테이블, 도메인, 뷰, 인덱스, 스키마 구조 정의 

```
CREATE TABLE

CREATE SCHEMA

CREATE DOMAIN

CREATE INDEX

CREATE VIEW
```



#### CREATE TABLE

\-   테이블 구성

\-   속성(열)과 속성(열)에 관한 제약 정의

\-   기본키 : PRIMARY KEY

\-   외래키 : FOREIGN KEY

 

#### CREATE 문의 기본 형식 (테이블 생성)

```
CREATE TABLE 테이블명(

열이름 데이터타입 [,..제약조건]

   );
   
CREATE TABLE 테이블명(

열이름 데이터타입 [NOT NULL] [UNIQUE] [DEFAULT..]

[PRIMARY KEY 열이름]

[FOREIGN KEY 열이름 REFERENCES 테이블(기본키)  

[CONSTRAINT명] ..

 );
   
```



![clip_image012](https://user-images.githubusercontent.com/101630615/173404686-865c3b73-09f5-42a4-af36-3d5882d0940a.jpg)

 

### PRIMARY KEY 제약조건

\-   기본키 제약조건

\-   열에 지정

\-   중복 안 됨

\-   빈 값 안 됨

![clip_image014](https://user-images.githubusercontent.com/101630615/173404689-438d90b0-1a49-4b7d-92bb-c2a2fc310c80.jpg)



#### 자동 증가

```
AUTO_INCREMENT
: 속성 값을 자동으로 증가

AUTO_INCREMENT = 100 
: 기본값 100부터 증가

SET @@AUTO_INCREMENT_INCREMENT = 3
 : 3씩 증가
```



##### 자동 증가 수정

```
SET @COUNT = 0;

UPDATE board SET boardNo = @COUNT:=@COUNT+1;
```



#### ALTER 문 (테이블 수정)

\-   테이블에 대한 정의 변경

\-   새로운 열 추가, 특정 열의 디폴트 값 변경, 특정 열 삭제 등 수행

### ALTER 문의 기본 형식

```
ALTER TABLE
ADD : 열 추가

RENAME COLUMN : 열의 이름 변경

MODIFY : 열의 데이터 형식 변경

CHANGE : 열의 이름과 데이터 형식 변경

DROP : 여러 개의 열 삭제

DROP COLUMN : 열 삭제

DROP PRIMARY KEY : 기본키 삭제

DROP CONSTRAINT : 제약조건 삭제 
```



#### Safe Updates 모드 해제

```
메뉴 Edit / Preferences ->

SQL Editor ->

Safe Update (rejects …… ) 체크 해제 ->

OK ->

Workbench 종료했다가 다시 시작
```



#### 제약조건 삭제

  \- 기본키 / 외래키 제약조건 삭제

  \- 기본키 / 외래키 제약조건 추가

  \- ON DELETE CASCADE

  \- CHECK 제약조건 추가 / 삭제

  \- DEFAULT 제약조건 추가 / 삭제 

 

#### ON DELETE CASCADE 

\-   기준 테이블(기본키를 갖고 있는 테이블)의 데이터가 삭제되었을 때

\-   이 값을 사용하고 있는 테이블의 외래키 데이터도 자동으로 삭제되도록 설정

 

#### CHECK 제약조건

\-   삭제 시 제약조건 이름 필요

\-   제약조건 확인 

\-    SELECT * FROM information_schema.table_constraints

\-    WHERE table_schema="sqldb" AND table_name = "book"; 

\-   CHECK 제약조건 삭제 / 추가