# MySQL 설치

> Homebrew 패키지를 다운로드 후 설치 

아직 homebrew가 설치되어 있지 않다면

 https://brew.sh/index_ko

링크를 통해 설치가 가능합니다. 

설치 후, command + space bar를 눌러 터미널을 실행시킵니다.

터미널에 입력하시면 가장 최신버전의 mysql을 설치 할 수 있습니다.

```zsh
brew install mysql
```



설치한 mysql의 버전을 확인할 수 있습니다.

```zsh
mysql- -v
```



아래 명령어를 입력하면 서버를 켭니다.

``` zsh
mysql.server start
```

<img src="Db.assets/screenshot.png" width=500px height=30%></img>

설치 후, 초기 설정을 수행하는 명령어입니다. 

```zsh
mysql_secure_installation
```



### 비밀번호

<img src="Db.assets/password.png" width=100%></img>

비밀번호 복잡성 유무에 대한 질문입니다. 

복잡한 비밀번호를 하려면 yes, 아니면 no로 입력하면 됩니다.

보통 비밀번호 분실시 초기화하는 어려움을 겪을 수 있으니 no로 간단히 설정합니다.



### 익명유저

<img src="Db.assets/annonymous.png" width=100%></img>

기본 설정으로 익명 유저를 만드는데 제거를 원한다면 yes, 아니면 no를 입력합니다.



### root 접속 권한

<img src="Db.assets/remote.png" width=100%></img>

localhost에서 root만 접속할 수 있는지 외부에서도 root로 접속 가능 한 지에 대한 질문입니다. 원격에서 root 계정 접속이 불가능하게 하려면 yes, 아니면 no를 입력합니다.


<img src="Db.assets/database.png" width=100%></img>

테스트 database를 삭제할 지에 대한 질문이며 삭제하려면 yes, 아니면 no를 입력합니다.



<img src="Db.assets/setclear.png" width=100%></img>

처음 설정 값을 저장할 것인지에 대한 질문입니다. 저장하려면 yes 아니면 no를 입력하시면 설정이 완료됩니다. 



언제든지 명령어를 입력해서 재설정이 가능합니다.

```zsh
mysql_secure_installation
```



### 접속

``` 
mysql -u root -p
```

mysql에 접속하려면 명령어를 입력하고,  비밀번호를 합니다.



<img src="Db.assets/final.png" width=100% height=30%></img>



모든 셋팅이 완료되었다면 접속이 가능합니다. 

exit를 입력하면 mysql을 종료할 수 있습니다.



### 서버 종료

``` zsh
mysql.server stop
```

서버를 종료하고 싶을 때는 입력합니다.



## 워크벤치 설치

https://downloads.mysql.com/archives/workbench/

1. 위 링크에 접속하여 사양과 버전에 맞는 파일을 다운로드합니다.

<img src="Db.assets/homepage.png">

**주의! ** 전에 설치한 mysql과 같은 버전으로 설치해야 합니다. 

<img src ="Db.assets/manage.png">

2. 워크벤치를 연 후 local instance 3306을 우클릭 하고 Edit Connection을 클릭합니다.



<img src="Db.assets/setmanage.png">

3. Store in keychain을 통해 비밀번호를 작성 후 우측 하단의 Test Connection을 누릅니다.

   성공적으로 수행했다면 아래 창이 나옵니다. 

<img src="Db.assets/setcomplete.png" width=30%>

4. local instance 3306을 클릭해 만들어진 것을 확인합니다.

<img src="Db.assets/setmain.png">

**주의 ! **

워크벤치 연결은 mysql 서버에 접속해야 연결이 가능합니다. 

그러므로 실행 전 터미널에서 입력 후 비밀번호를 친 후에 접속합니다.

``` 
mysql.server start
```

