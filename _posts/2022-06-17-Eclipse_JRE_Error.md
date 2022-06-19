# [Eclipse] JRE System Library unbound



>  JRE System Library unbound 오류 발생시 

(1) 상단 탭의 Project -> Properties 순으로 이동

<img width="438" alt="스크린샷 2022-06-18 오전 3 25 56" src="https://user-images.githubusercontent.com/101630615/174376800-6a5d5a94-fcb1-4ab8-9c99-2fa81c87d083.png">





(2) 임의의 프로젝트 우클릭 -> Build Path -> Configure Build Path 순서로 이동

<img width="500" alt="스크린샷 2022-06-18 오전 3 23 32" src="https://user-images.githubusercontent.com/101630615/174376276-678d156d-5cec-42de-88c4-013ed487ac44.png">





<img width="1012" alt="스크린샷 2022-06-18 오전 3 24 05" src="https://user-images.githubusercontent.com/101630615/174376579-8a8bc3ea-c113-4ea5-86a6-5d964b3c4b6d.png">

상단 탭에 Libraries을 클릭하면 현재 설치한 버전이 보입니다.

저는 지금 오류가 없으나, 만약  unbound 오류가 있을 시 

**JRE System Library [Jre 버전정보] (unbound)**라는 상태가 보입니다.



오류가 있다는 가정하에, 이를 수정하기 위해 우측에  Add Library 탭을 선택해 라이브러리를 추가헙니다.

<img width="1012" alt="스크린샷 2022-06-18 오전 3 24 17" src="https://user-images.githubusercontent.com/101630615/174376662-3b65e9ae-1894-4278-805e-f05108b7608a.png">

JRE System Library를 선택 후 Next를 클릭합니다.



<img width="1012" alt="스크린샷 2022-06-18 오전 3 24 55" src="https://user-images.githubusercontent.com/101630615/174376724-23a8e9a0-cae4-456d-8e20-d0517a8ca2f7.png">

Alternate JRE > installed JREs를 클릭하여 현재 설치된 JRE 항목이 같이 검색됩니다. 



<img width="696" alt="스크린샷 2022-06-18 오전 3 25 23" src="https://user-images.githubusercontent.com/101630615/174376770-f31aab93-4836-4302-864e-d22734b0c4f1.png">



저의 경우 두 가지가 있지만 원하는 java 버전을 선택하시면 됩니다. 



<img width="1012" alt="스크린샷 2022-06-18 오전 3 24 05" src="https://user-images.githubusercontent.com/101630615/174376579-8a8bc3ea-c113-4ea5-86a6-5d964b3c4b6d.png">

다시 처음 창으로 돌아와 원하는 JRE를 선택 등록이 정상 처리 되었다면

JRE System Libraryr가 두 개가 됩니다. 

Unbound 상태인 해당 JRE를 선택 후 Remove 버튼을 클릭하여 삭제합니다.



[출처] : [https://jamesdreaming.tistory.com/164](https://jamesdreaming.tistory.com/164)