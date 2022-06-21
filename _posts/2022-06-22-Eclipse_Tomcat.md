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



출처 : [https://es2sun.tistory.com/188](https://es2sun.tistory.com/188)  [https://clgnsdl94.tistory.com/42](https://clgnsdl94.tistory.com/42)

