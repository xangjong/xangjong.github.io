# [React] 설치



### 리액트 설치

리액트 홈페이지 : https://reactjs.org

다운로드

- Node.js
- Visual Studio Code



#### Node.js

- Chrome V8 JavaScript 엔진(V8 Engine)으로 빌드된 JavaScript 런타임
- 자바스크립트를 웹 브라우저 영역 외에 서버, 모바일 애플리케이션, 데스크탑 애플리케이션 등 영역에서 사용 가능하게 해 줌
- React 애플리케이션은 웹 브라우저에서 실행되는 코드이므로 Node.js와는 직접적인 연관은 없지만
  프로젝트 개발하는데 필요한 도구들이 Node.js 사용하기 때문에 설치 필요



#### NPM (Node Package Manager)

- 자바스크립트 패키지 관리자 도구
- Node.js에서 사용할 수 있는 모듈들을 패키지화하여 모아둔 저장소 역할과 패키지 설치 및 관리 
- 리액트 역시 하나의 패키지



#### Node.js / NPM 설지

- https://nodejs.org
- Long Term Support 버전 다운로드

- 모두 디폴트로 설치
- 명령 프롬프트 창에서 버전 확인 
  - node -v
  - npm -v



#### npm과 npx 차이

- npm : 프로그램을 설치하는 프로그램
- npx 
  - create-react-app 이라는 프로그램을 임시로 한 번만 실행시키고 지운다는 개념
  - 장점
    - 컴퓨터 공간을 낭비하지 않음
    - 설치 실행할 때마다 새로 다운로드 하기 때문에 항상 최신 상태