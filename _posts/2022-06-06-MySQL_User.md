

 # [MySQL] 계정 명령어



### 사용자 계정 생성 

```
use mysql;
```

### 사용자 계정 조회

```
SELECT * FROM user;
```

### 사용자 계정 생성

```
CREATE USER '계정'@'호스트' identified by '비밀번호';

호스트

localhost : 로컬에서 접근 가능

192.168.172.1 : 특정 IP에서 접근 가능

'%' : 어디에서나 접근 가능

ex )  CREATE USER newuser1@'%' identified by '1111';
	CREATE USER 'newuser2'@'%' identified by '1111'; 
```

 

### 비밀번호 변경

```
SET PASSWORD for '계정명'@'%' = '새 비밀번호';

ex ) SET PASSWORD for 'newuser1'@'%' = '1234';
```



### 계정 삭제  

```
DROP USER '계정명'@호스트;

DROP USER 'newuser1'@'%';
```



### 권한 조회 

```
SHOw GRANTS for '계정명';

ex ) SHOW GRANTS for dbuser;
```

### 권한 부여 

``` 
GRANT 권한 ON 데이터베이스.테이블 TO 계정@호스트;

GRANT all privileges ON *.* TO 계정@호스트
: 모든 권한 부여  

GRANT select, insert, update, delete ON 특정DB.* TO 계정@호스트;
: 특정 DB의 모든 테이블에 특정 권한 부여

ex ) GRANT all privileges ON *.* TO newuser2@'%';
: newuser2에게 모든 권한 부여  

SHOW GRANTS for newuser2;
newuser2로 접속 : 모든 스키마/테이블 접근 가능
```

### 권한 삭제 

```
REVOKE 권한 ON 데이터베이스.테이블 TO 계정@호스트;

REVOKE all privileges ON *.* FROM 계정@호스트;
: 모든 권한 삭제 

REVOK select, insert, update, delte ON 특정DB.* FROM 계정@호스트;
: 특정 DB의 모든 테이블에 대한 특정 권한 삭제

REVOKE all privileges ON 특정DB.* FROM 계정@호스트;
: 특정 DB의 모든 테이블에 대한 모든 권한 삭제

REVOKE select ON *.* FROM newuser2@'%';
: SELECT 권한 삭제

SHOW GRANTS for newuser2;
: 권한 조회
```

