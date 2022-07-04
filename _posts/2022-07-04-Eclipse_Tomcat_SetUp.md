# [Eclipse] Mac m1 Tomcat 설치 



#### 톰캣 설치

[https://tomcat.apache.org/download-80.cgi](https://tomcat.apache.org/download-80.cgi) 설치를 위해 홈페이지에 접속합니다.



좌측 사이드바에서 설치할 버전을 클릭한 뒤 

![스크린샷 2022-06-18 오후 4 11 48](https://user-images.githubusercontent.com/101630615/174876697-0742d1f7-778c-4896-848c-efe13835cbe7.png)



Tar.gz 파일을 선택해 다운로드합니다.



![스크린샷 2022-06-18 오후 4 12 32](https://user-images.githubusercontent.com/101630615/174876704-53da039b-167b-44dd-9498-47342a2207f4.png)

Tar.gz 형식으로 받은 톰캣 버전을 더블 클릭하면  설치됩니다.



설치 후 터미널을 실행합니다.

터미널 안에서 cd 명령어로 위치를 이동할 필요없이 아래 명령어를 입력합니다.

설치된 버전에 따라 변경하여 입력하시면 됩니다.

```
sudo mv ~/Downloads/apache-tomcat-8.5.81 /usr/local  
: 압축을 푼 파일을 ~Downloads 폴더에서 /usr/local (파일 위치 이동)

sudo rm -f ~/Library/Tomcat (디렉터리 내 파일 또는 디렉터리가 있는 경우 rm -rf 사용)
: 기존 파일 삭제
sudo ln -s /usr/local/apache-tomcat-8.5.81 /Library/Tomcat. 
(file exists가 나오는 경우 ln -sf 사용)
: 파일 링크 연결

sudo chown -R 사용자계정 /Library/Tomcat
: 권한 설정

sudo chmod +x /Library/Tomcat/bin/*.sh
: 실행 권한 할당
```

​           

순서대로 입력 후 톰캣을 실행합니다.

```
sudo /Library/Tomcat/bin/startup.sh 
: 톰캣 실행
```



브라우저에 http://127.0.0.1:8080 또는 http://localhost:8080 을 입력하여

아래의 창이 뜨면 설치 완료입니다.

![스크린샷 2022-06-22 오전 3 33 39](https://user-images.githubusercontent.com/101630615/174876709-69b5d9e1-a691-4508-a23c-4046c7bcdf13.png)





```
sudo /Library/Tomcat/bin/shutdown.sh
```

 명령어를 입력해 톰캣을 종료합니다.



<img width="994" alt="스크린샷 2022-06-22 오전 3 34 20" src="https://user-images.githubusercontent.com/101630615/174876713-9fa0312a-da79-49db-9ac8-a7e2c9b934ed.png">





이제 이클립스에 적용해봅시다.



1. 이클립스 실행 후 우측 상단 open perspective 클릭 

Java EE(default)를 클릭 -> Severs 탭 활성화

<img width="138" alt="스크린샷 2022-07-04 오전 9 58 28" src="https://user-images.githubusercontent.com/101630615/177067498-9870046f-8bc4-42f2-9a53-2c52a33d1668.png">



<img width="633" alt="스크린샷 2022-07-04 오전 10 06 27" src="https://user-images.githubusercontent.com/101630615/177067496-97998f1c-9306-4494-9b6a-218be46131ad.png">

저는 이미 설치되어 있어서 톰캣 버전이 나오나 처음 설치하시는 분들은



![image-503](https://user-images.githubusercontent.com/101630615/177067756-f1d06ff6-e6d1-4c82-896e-05a755e4d80a.png)



이런 창이 나올 것입니다. 



클릭하시면 

<img width="589" alt="스크린샷 2022-07-04 오전 10 37 31" src="https://user-images.githubusercontent.com/101630615/177067490-1c747e78-da95-479e-974d-d0330ca33b62.png">



설치한 버전에 맞게 톰캣 버전을 선택하시면 됩니다.(저는 9를 선택했습니다.)



<img width="589" alt="스크린샷 2022-07-04 오전 10 37 45" src="https://user-images.githubusercontent.com/101630615/177067481-c37d07cf-ad82-4d94-80fc-db2e3248bd68.png">



톰캣의 경로를 지정해줘야 합니다.

Browse 버튼을 눌러 톰캣을 설치한 경로에 맞춰 경로를 지정해줍니다.

신규 경로를 지정해주고 실행하면 됩니다. 



톰캣의 버전을 변경하는 경우 

Preferences -> Server -> Runtime Environments 창에서 언제든 변경, 추가, 삭제 가능합니다.

<img width="630" alt="스크린샷 2022-07-04 오전 10 37 05" src="https://user-images.githubusercontent.com/101630615/177067495-53be10a2-c293-46cd-9536-1bcd2531bee5.png">



출처 : [https://es2sun.tistory.com/188](https://es2sun.tistory.com/188) , [https://clgnsdl94.tistory.com/42](https://clgnsdl94.tistory.com/42)

​		[https://goldsony.tistory.com/26](https://goldsony.tistory.com/26) , [https://playcode.tistory.com/20](https://playcode.tistory.com/20)
