

# MySQL 외부접속 허용



>  ``secure_file_priv ``에 특정 경로가 설정되어 있다면 해당 경로에 있는 파일만 import, export 할 수 있습니다.



1. 아래 명령어를 통해 my.cnf의 위치를 파악합니다.

```
mysql --verbose --help | grep my.cnf
```

<img width="829" alt="mysql_my_cnf" src="https://user-images.githubusercontent.com/101630615/173245103-5477199c-9f06-4d24-8804-f79011f175dd.png">

2. 아래 명령어를 입력후, 경로로 접속합니다.

```
vi /opt/homebrew/etc/my.cnf
```



<img width="663" alt="mysql_content" src="https://user-images.githubusercontent.com/101630615/173245096-8d9b5379-b4a8-4571-96ca-38c9f8d9b334.png">



``esc``키를 누르고 ``i``키를 눌러 insert 모드로 변환합니다.

```
bind-addresss = 0.0.0.0
mysqlx-bind-address = 0.0.0.0 

값을 0으로 입력하여 외부 입력을 허용해주고 

secure-file-prive=""

명령어를 따로 추가 입력해 경로를 초기화합니다.

경로 설정을 하고 싶다면 원하는 경로를 ""안에 입력합니다.
```

입력을 다 하셨다면,  ``esc``키를 누르고 ``:wq`` (저장하고 종료) 키를  입력합니다.



3. mysql을 재시작합니다. (저는 홈브루를 통해 설치하여 brew를 사용하였습니다.)

```
brew services restart mysql

혹은 

mysql services restart
```



4. mysql 계정에 접속 후 비밀번호를 입력합니다.

```
mysql -u root -p
```



5. 확인을 위해 mysql>

아래 명령어를 입력해 확인합니다.

```
SELECT @@GLOBAL.secure_file_priv;
```



<img width="776" alt="mysql_final" src="https://user-images.githubusercontent.com/101630615/173245100-38f12576-63f3-4a91-8150-365971cfd555.png">

화면과 같은 창이 나오면 외부 경로 설정이 완료 되었습니다.





6. 보안을 위해 새로운 계정을 하나 만들어줍니다.

### 새로운 MySQL 계정 생성

```
모든 ip 허용
create user '아이디'@'%' IDENTIFIED by '비밀번호';

localhost만 허용
create user '아이디'@'localhost' IDENTIFIED by '비밀번호';

특정 아이피 영역 허용
create user '아이디'@'192.168.0.%' IDENTIFIED by '비밀번호';
```



### 생성한 MySQL 계정의 권한 적용 

```
grant all privileges on 데이터베이스명.* to '유저명'@'호스트명';

모든 데이터베이스 접근 허용
grant all privileges on *.* to '유저명'@'호스트명';

모든 데이터베이스 , 모든 호스트 허용
grant all privileges on *.* to '유저명'@'%;
```





예시 ) mysql에 접속 후 저는 username을 계정으로 생성하고 비밀번호는 1234로, 모든 권한을 부여하였습니다.

<img width="776" alt="mysql_newuser" src="https://user-images.githubusercontent.com/101630615/173245104-a3d321e4-346c-470a-b5ba-143b04344029.png">





출처 : https://patiencelee.tistory.com/609

​			https://abbo.tistory.com/241

​			https://sjwiq200.tistory.com/83