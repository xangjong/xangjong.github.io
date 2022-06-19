# [MySQL] 설치

> Homebrew 패키지를 다운로드 후 설치 

아직 homebrew가 설치되어 있지 않다면

[https://brew.sh/index_ko](https://brew.sh/index_ko) 링크를 통해 설치가 가능합니다. 

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

<img width="461" alt="screenshot" src="https://user-images.githubusercontent.com/101630615/172042091-b4336805-463d-4a3a-92dc-8ed6f2e9e7d4.png">

설치 후, 초기 설정을 수행하는 명령어입니다. 

```zsh
mysql_secure_installation
```



### 비밀번호

<img width="660" alt="password" src="https://user-images.githubusercontent.com/101630615/172042089-9e833267-7ecd-48ba-a2e0-af0444427f2a.png">

비밀번호 복잡성 유무에 대한 질문입니다. 

복잡한 비밀번호를 하려면 yes, 아니면 no로 입력하면 됩니다.

보통 비밀번호 분실시 초기화하는 어려움을 겪을 수 있으니 no로 간단히 설정합니다.



### 익명유저

<img width="524" alt="annonymous" src="https://user-images.githubusercontent.com/101630615/172042076-6aaf7580-2c44-4615-81b4-464c43364790.png">

기본 설정으로 익명 유저를 만드는데 제거를 원한다면 yes, 아니면 no를 입력합니다.



### root 접속 권한

<img width="552" alt="remote" src="https://user-images.githubusercontent.com/101630615/172042090-bd64aee1-de1a-42b8-9e54-fab1a671a885.png">

localhost에서 root만 접속할 수 있는지 외부에서도 root로 접속 가능 한 지에 대한 질문입니다. 원격에서 root 계정 접속이 불가능하게 하려면 yes, 아니면 no를 입력합니다.

<img width="643" alt="database" src="https://user-images.githubusercontent.com/101630615/172042077-396c68ff-5b8e-42ef-b5f8-2a296491670f.png">

테스트 database를 삭제할 지에 대한 질문이며 삭제하려면 yes, 아니면 no를 입력합니다.



<img width="643" alt="setclear" src="https://user-images.githubusercontent.com/101630615/172042092-d7b2a7e3-e2fe-4fc8-bb69-6ed3fa9f072b.png">

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



<img width="643" alt="final" src="https://user-images.githubusercontent.com/101630615/172042081-f1a615b5-6ace-4731-98d4-924541d7edcf.png">



모든 셋팅이 완료되었다면 접속이 가능합니다. 

exit를 입력하면 mysql을 종료할 수 있습니다.



### 서버 종료

``` zsh
mysql.server stop
```

서버를 종료하고 싶을 때는 입력합니다.



## 워크벤치 설치

[https://downloads.mysql.com/archives/workbench/](https://downloads.mysql.com/archives/workbench/)

1. 위 링크에 접속하여 사양과 버전에 맞는 파일을 다운로드합니다.

![homepage](https://user-images.githubusercontent.com/101630615/172042082-7c694876-7e8c-4bf3-89f6-7e7172cce5eb.png)

**주의!** 전에 설치한 mysql과 같은 버전으로 설치해야 합니다. 

<img width="1192" alt="manage" src="https://user-images.githubusercontent.com/101630615/172042085-4a98fb6b-a724-42f4-9e8b-3dd625de11d8.png">

2. 워크벤치를 연 후 local instance 3306을 우클릭 하고 Edit Connection을 클릭합니다.



<img width="890" alt="setmanage" src="https://user-images.githubusercontent.com/101630615/172042095-1e1e7332-ad83-4d5c-a649-21cfd5854c27.png">

3. Store in keychain을 통해 비밀번호를 작성 후 우측 하단의 Test Connection을 누릅니다.

   성공적으로 수행했다면 아래 창이 나옵니다. 

<img width="256" alt="setcomplete" src="https://user-images.githubusercontent.com/101630615/172042093-c8d61b6a-ecc1-4817-a655-067a98fb871b.png">

4. local instance 3306을 클릭해 만들어진 것을 확인합니다.

<img width="1192" alt="setmain" src="https://user-images.githubusercontent.com/101630615/172042094-1bfa4740-bc34-4020-a8e2-8570c0167198.png">

**주의 !**

워크벤치 연결은 mysql 서버에 접속해야 연결이 가능합니다. 

그러므로 실행 전 터미널에서 입력 후 비밀번호를 친 후에 접속합니다.

``` 
mysql.server start
```

