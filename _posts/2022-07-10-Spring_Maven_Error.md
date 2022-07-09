



# [Spring] Tomcat Maven Build



### maven build 에러 해결방법

1. 메이븐 업데이트 

프로젝트에 오른쪽 마우스 버튼 클릭 -> maven -> update project

 -> (force update of snapshot/release를 체크) -> OK



<img width="1236" alt="스크린샷 2022-07-10 오전 3 02 24" src="https://user-images.githubusercontent.com/101630615/178117793-252b438e-62f1-4e75-a962-b64281575b16.png">





<img width="585" alt="스크린샷 2022-07-10 오전 3 02 51" src="https://user-images.githubusercontent.com/101630615/178117795-30958047-1e8f-47d9-b32c-933855b844f6.png">





2. clean project

프레임워크(스프링 혹은 이클립스) 위의 작업표시줄에 project 클릭 -> clean



<img width="230" alt="스크린샷 2022-07-10 오전 3 03 17" src="https://user-images.githubusercontent.com/101630615/178117796-37eb4a59-3a36-45da-a52c-365cbee50e77.png">





3. .m2 repository 삭제 후 다시 빌드

사용자 -> .m2 -> repository 있는 파일들을 쿨하게 모두 삭제.

스프링을 다시 시작하면 pom.xml에 선언되어있는 maven들이 다시 build 되기 시작함.



4. buil path -> configure build path 에서 jre system library에서 jre가 아닌 jdk로 변경

jre나 jdk의 문제보다는 실제로 jre나 jdk의 폴더가 정말로 있는 경로인지를 확인해야한다. 

**build path에 설정한 jre나 jdk의 경로가 실제 내 컴퓨터에 있는지 확인**



<img width="1002" alt="스크린샷 2022-07-10 오전 3 03 43" src="https://user-images.githubusercontent.com/101630615/178117797-cf43815c-c530-45c4-8374-c6fcb31f2d23.png">





[출처] : [https://zorba91.tistory.com/22](https://zorba91.tistory.com/22)