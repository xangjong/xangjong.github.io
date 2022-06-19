

# [Java] JDK 설치 & 환경변수 설정

> jdk 설치 

brew 패키지가 설치 가 되있는 가정으로 진행한다.



1. 다음 명령어를 입력해 brew 패키지를 업데이트한다.

```
brew update
```



2. Adoptopenjdk/openjdk 추가 

``` 
brew tap adoptopenjdk/openjdk 

혹은 

brew install adoptopenjdk8 --cask
```

대부분 게시글에서 brew cask.. 명령어를 사용하였는데 --cask 옵션으로 변경되었다.



2-1 설치 가능한 모든 jdk 찾기 

```
brew search jdk
```

<img width="832" alt="brew_search" src="https://user-images.githubusercontent.com/101630615/173240688-309415c1-6ebe-43cc-831f-4546f4bf65f1.png">

현재 나는 jdk 8 버전을 사용하고 있으며 이 중 원하는 버전을 설치하면 된다. 



3. 버전 설치

원하는 버전을 선택해서 아래와 같이 입력한다.

```
brew install --cask adoptopenjdk(원하는 숫자)
ex :) brew install --cask adoptopenjdk8
brew install --cask adoptopenjdk11
```



3-1 버전 확인

```
java --version 
```

<img width="832" alt="java_version" src="https://user-images.githubusercontent.com/101630615/173240699-898a16b8-2c24-4d26-bc30-c2ca27ae3b1e.png">

여러 자바 버전을 설치하면 가장 최신 버전의 자바 버전으로 세팅된다.



3-2  자바가 설치된 경로 확인

```
/usr/libexec/java_home -V
```

<img width="832" alt="java_process" src="https://user-images.githubusercontent.com/101630615/173240695-7af958fa-a177-49c5-9881-1344b401f7b8.png">

4. 자바 환경변수 설정

경로를 확인했으면 터미널에서 아래 명령어를 입력하여 편집기를 실행한다.

```
vi ~/.bash_profile
```

터미널 vi 편집기에 ``i``를 눌러 insert 모드로 변경해주고 

아래 본인이 받은 jdk버전의 폴더 이름으로 변경하여 작성한다.

<img width="728" alt="java_environment" src="https://user-images.githubusercontent.com/101630615/173240691-03257fe3-b34c-4f24-b6a0-67475cfb9a2e.png">

```
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk-8.jdk/Contents/Home
```

```
export PATH=${PATH}:/Library/Java/VirtualMachines/jdk-8.jdk/Contents/Home
```

두 문장을 작성한 후 ``ESC``를 눌러 insert 모드를 종료하고 

``:wq``(종료 후 저장)을 눌러 편집기를 종료한다.



이후 아래 명령어를 적어 환경변수를 설정한다.

```
source ~/.bash_profile
```



설정 확인을 위해 아래 명령어를 입력하고

```
echo $PATH
```

<img width="882" alt="java_final" src="https://user-images.githubusercontent.com/101630615/173240692-027c93ec-5d93-4e9b-b024-c5cb085646d1.png">

결과처럼 나오면 환경변수 설정 완료.



[출처] : [https://abit.ly/f6nwdr]( https://abit.ly/f6nwdr  )  , [https://abit.ly/nx0k98](https://abit.ly/nx0k98)