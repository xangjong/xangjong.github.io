# Hombrew

>  Homebrew(흠브루) 란?

macOS 용 패키지 관리자입니다. 터미널(Terminal)에서 명령어를 작성하여 자신이 필요한 프로그램을 설치, 삭제, 업데이트를 손쉽게 관리할 수 있습니다.



> Homebrew를 사용 하는 이유

- 해당 사이트에 접속해서 프로그램을 다운하는 경우 사용자가 원치 않는 프로그램을 설치할 수도 있고 나중에 기존 데이터가 남아있는 경우  mac이 버벅일 가능성이 있습니다.

- 홈브루로 패키지를 설치하는 경우 가장 최신 버전이 설치됩니다.

- 불필요한 프로그램 등 추가 설치 없이 원하는 앱만 설치해서 사용할 수 있습니다.

- brew로 설치한 앱들은 ``brew list``  를 통해 따로 확인할 수 있어 관리적인 측면에서 좋습니다.

  

> Homebrw 설치 

1. Command + spaecebar를 통해 spotlight 필드를 활성화합니다.

2. terminal 앱을 검색하여 실행시킵니다.

3. https://brew.sh/index_ko 링크에 접속하여 맨 첫줄을 터미널에 복사합니다.

   ![homebrewmain](https://user-images.githubusercontent.com/101630615/172046059-bf14cf9b-6115-4325-ad98-ed77c73dae66.png)

   ```zsh
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

4. 복사해 붙여 넣으면 계정 password를 입력하라는 창이 나옵니다. 열쇠 아이콘만 보이고 입력한 값은 표시되지 않습니다. 입력 후 return(enter)를 눌러줍니다.

   ![homebrew-enter-password](https://user-images.githubusercontent.com/101630615/172046056-5f527ea2-31bd-4648-b949-2be25b05b46d.png)

   ![install-homebrew](https://user-images.githubusercontent.com/101630615/172046060-9f992510-21ea-4aaf-a645-049eae31e891.png)

   설치가 진행중이며 계속 설치를 원하면 return(enter) 키, 중단을 원하면 아무 키나 입력하시면 됩니다.

   <hr>

5. 설치 완료

   ![homebrew-complete](https://user-images.githubusercontent.com/101630615/172046053-ab5c34a5-c1fe-4976-98cb-d7a2f7f1506d.png)

   설치가 완료된 모습입니다.

   

   <img width="665" alt="homebrew-list" src="https://user-images.githubusercontent.com/101630615/172046057-05aadb2c-d5d8-4efa-88bb-33f8112f9062.png">

   ``brew list`` 를 입력하시면 homebrew로 설치된 파일 목록들을 볼 수 있습니다.



아래는 그 이외의 단축키입니다.

```zsh
- brew ~ : 커맨드 라인 프로그램 (c, java, python)

- brew cask ~ : GUI 프로그램 (Safari, Chrome, Word)

brew update : 홈브류 최신버전으로 업데이트

brew upgrade [프로그램명]: 홈브류에 설치된 프로그램 최선버전으로 업데이트

brew search [프로그램명] : 홈브류를 통해 설치 가능한 프로그램 찾기

brew cask list : 홈브류에 설치된 그래픽을 통해 작업하는 프로그램 목록 (Safari, Chrom, Word)

brew cask install [프로그램명] : 프로그램 설치

brew cask remove [프로그램명] : 홈브류에 설치된 프로그램 삭제

brew cleanup : 업데이트 후 필요없는 이전 버전의 패키지 삭제
```
