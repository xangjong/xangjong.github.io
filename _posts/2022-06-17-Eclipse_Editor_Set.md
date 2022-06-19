# [Eclipse] Mac 자바스크립트 에디터 설정



이클립스를 사용하다보면 .js 파일을 열었지만

자동완성, 변수명, 함수명, 예약어 등에 기본 색표기 없이

검정색 글자로만 쓰여져 있습니다.

<img width="441" alt="스크린샷 2022-06-18 오후 3 40 29" src="https://user-images.githubusercontent.com/101630615/174426763-9c6b65ce-1f61-4344-a573-93e5e0b1f088.png">

이는 기본 Text Editor로 열어서 그런것 인데요



현재 사용중인 .js 파일을 Open With -> Generic Text Editor로 바꿔줍니다.

<img width="566" alt="스크린샷 2022-06-18 오후 3 40 56" src="https://user-images.githubusercontent.com/101630615/174426767-e1f45aa9-94fe-44fa-b493-4a4002d40271.png">







Generic Text Editor로 열었을 시 예약어나 컬러가 정상적으로 나오는 것을 볼 수 있습니다.

<img width="374" alt="스크린샷 2022-06-18 오후 3 41 08" src="https://user-images.githubusercontent.com/101630615/174426769-539e1073-c9ac-42fd-aa29-9e5493d35fe0.png">



하지만 일일히 하나씩 바꿔줄 수 없으니 Generic Text Editor를 디폴트 값으로 설정합니다.

<img width="235" alt="스크린샷 2022-06-18 오후 3 41 30" src="https://user-images.githubusercontent.com/101630615/174426770-9fad4d85-da18-40d3-871e-430900e16144.png">



상단의 Preferences -> General -> Editors -> File Associations 순으로 클릭합니다.

<img width="654" alt="스크린샷 2022-06-18 오후 3 42 12" src="https://user-images.githubusercontent.com/101630615/174426772-720e00bb-3244-417e-a0a8-3f3b5d8d3dab.png">

오른쪽 화면에 Add 버튼을 클릭 후 



아래와 같은 창이 나오는데 .js를 입력하고 Ok를 클릭합니다.

<img width="654" alt="스크린샷 2022-06-18 오후 3 43 01" src="https://user-images.githubusercontent.com/101630615/174426773-27b16256-c1ae-4f1e-92bc-e2a781b00df6.png">



아래 창을 보면 Associcated editors 메뉴가 보이는데 

해당 메뉴에서 Add 버튼을 클릭 후 Generic Text Editor룰 추가합니다.

다시 아래 메뉴에 추가된 Generic Text Editor를 포커스를 둔 후 오른쪽 Default 버튼을 클릭합니다.

<img width="654" alt="스크린샷 2022-06-18 오후 3 43 50" src="https://user-images.githubusercontent.com/101630615/174426775-932c873d-cd07-4cc5-9e04-9c9724ea9296.png">



버튼을 눌러주면 위와 같이 순서가 변경되며 Apply and Close 버튼을 클릭해 변경한 설정을 저장하고 

창에서 벗어납니다.

앞으로 .js 파일을 열면 Generic Text Editor가 디폴트 값으로 설정되어 변경된 것을 알 수 있습니다.



[출처] : [https://html6.tistory.com/415](https://html6.tistory.com/415)