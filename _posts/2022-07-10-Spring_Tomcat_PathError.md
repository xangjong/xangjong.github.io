# [Spring] M1 Tomcat 404 에러





### 방법 1. 

Server 탭 - Tomcat Server - Module path가 ``/``인지 확인



<img width="920" alt="스크린샷 2022-07-10 오전 2 46 27" src="https://user-images.githubusercontent.com/101630615/178117288-e5c09629-e219-4a2f-85ff-00bbead844dc.png">



### 방법 2.

Tomcat 서버 우클릭 - Properties

General Location workspace -> Switch Location 



<img width="624" alt="스크린샷 2022-07-10 오전 2 43 23" src="https://user-images.githubusercontent.com/101630615/178117277-8e3394b4-dfef-42f2-8d5d-a2b29db659af.png">



### 방법 3.

프로젝트 우클릭 - Properties - Web Project Settings - Context root ``/``인지 확인

Project Facets - Java버전이 사용하는 JDK버전과 맞는지 확인





<img width="839" alt="스크린샷 2022-07-10 오전 2 43 45" src="https://user-images.githubusercontent.com/101630615/178117287-4d07ddc8-123e-4432-bde3-4f5327469952.png">





#### Spring Project의 Home.jsp 실행 시, 404 Error가 발생하는 이유

home.jsp로 접근하여 Run 시켰을 때, 404 에러가 났던 이유는

home.jsp가 위치한 WEB-INF 폴더는 설정 파일을 담고 있는 중요한 폴더이기 때문에

외부에서의 직접적인 접근을 막고 있기 때문이다.

**프로젝트(SampleProject)를 기준으로 Run하면 정상 동작한다.**



[출처] : [https://hello-walnuty.tistory.com/16]([https://hello-walnuty.tistory.com/16]), [https://all-record.tistory.com/157](https://all-record.tistory.com/157)