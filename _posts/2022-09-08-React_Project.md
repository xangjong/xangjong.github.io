# [React] 프로젝트 생성



1. reactWorkspace 폴더 생성
2. VSCode : 터미널 / 새 터미널
3. reactWorkspace로 이동
   - ``cd 경로\reactWorkspace``
4. ``npx create-react-app 프로젝트명``
5. my-app 폴더로 이동 : ``cd my-app``
6. 프로젝트 실행 : ``npm start``
7. 실행 종료 : Ctrl + C

- 함수형 컴포넌트 : rsc 입력하고 엔터
- 클래스형 컴포넌트 : rcc 입력하고 엔터



#### 프로젝트 구성

- index.html : ``<div id="root">``여기에 렌더링

- index.js : 앱의 진입점 역할

  - ```react
    const root = ReactDOM.createRoot(document.getElementById('root'));
    
    <App /> 
    
    import App from './App';
    ```

  - App.js : 기본 컴포넌트,  컴포넌트에 새로 추가한 컴포넌트 추가

    


#### 컴포넌트 추가

- 각 컴포넌트를 js 파일로 분리

- src 폴더 안에 components 폴더 생성

- App.js에서 각 컴포넌트 import

  

#### 컴포넌트 생성 시 주의점

- 컴포넌트 이름은 대문자로 시작
- 반드시 return 포함
- return 안에는 반드시 하나의 최상위 태그로 시작해야 함
- 오류나는 경우

```react
<div></div>
<div></div>
```



모든 태그는 최상위 태그 내에 포함

```html
<div>
	<div></div>
	<h3></h3>
	<div></div>
</div>
```



##### 태그의 클래스 속성 설정 시 주의

- class 가 아니라 className 사용
- ``<div className="nav">``





#### props

- 컴포넌트의 속성 (값 설정)

- 부모 컴포넌트에서 자식 컴포넌트로 값을 전달할 때 사용 (읽기 전용)

- 컴포넌트 렌더링할 때 값을 전달해 주고 싶을 때 사용

- 부모 컴포넌트 : App.js

- 값을 직접 보내도 되고, 변수의 값을 보내도 됨

- ``<Subject title="제목"></Subject>`` 또는 

- ``let title = “제목”;``

- ``<Subject title={title}></Subject>``

- 자식 컴포넌트에서 받음 : Subject.js

  ```react
  const Subject = ({title}) => {
  … {title} 
  }
  ```



#### 이미지 출력

- (1) public 안에 assets 폴더 생성하고 이미지 파일 저장
  - js파일에서 기본으로 public 경로 찾아감
- (2) src 폴더 안에 images 폴더에 이미지 저장하고  import 해서 사용
- public 폴더 안의 생성된 폴더의 이미지는 import 사용 안 함



#### state 

- 변수 (변경 가능)

- 컴포넌트 내부에서 변경될 수 있는 값

- 이 값이 변경될 때 리 렌더링 됨

- 함수형 컴포넌트에서는 useState() 함수 사용해서 state 값 변경

- Hooks 
  - 기존의 함수형 컴포넌트에서 할 수 없었던 다양한 기능을 제공
  
    ``useState()`` : 상태 관리
  
  - ``useEffect()`` : 렌더링 직후 작업 설정



##### useState() 사용법

```react
import React, {useState} from ‘react’;
const [state명(변수명), setter함수명] = useState(초기값);
```



#### 이벤트 처리

- 이벤트 처리 시 주의점

- 이벤트 이름은 카멜 표기법 사용 : onClick, onKeyUp

- 이벤트에 함수 형태의값 전달

  ```react
  onClick = {onClickEnter}
  onClick = {() => setColor(‘green’)}
  ```

- DOM 요소에만 이벤트 설정 가능

- 사용자가 직접 만든 컴포넌트에는 이벤트 설정 불가

- 예 : 	MyComponent에 onClick 설정 시

- ``<MyComponent onClick={doSomthing} />``

- 클릭 시 doSomthing() 함수를 호출하는 것이 아니라

- (속성) 이름이 onClick인 props를 MyComponent 컴포넌트에 전달하는 것

- 전달받은 props를 컴포넌트 내부의 DOM 이벤트로 설정 

- ``<div onClick={props.onClick}></div>``



#### ``<input>`` 태그의 입력 값 처리 이벤트

- onChange 이벤트 발생
- 입력된 값 : e.target.value



#### 배열 출력 : ``map()`` 사용

- 배열 내장 함수 
- 각 배열의 요소에 대해 처리된 새로운 결과를 새로운 배열에 담아 반환하는 함수
- value, index 전달 

```react
titles.map( (title, index) => (

<p>{title}</p>

 ) )
```



#### 자바스크립트 스프레드 연산자 : …

- 기존값 유지
- 객체나 배열의 값을 복제할 때 사용
- 기존배열에 새 항목 추가
- [...기존배열, 새항목]
- newArr = oldArr; // newArr 변경하면 oldArr도 변경
- newArr = [...oldArr]; // oldArr 기존값 유지
  - newArr 변경하면 oldArr 변경 안 됨



#### 배열 내장 함수 filter() 함수

- 컴포넌트에서 배열의 불변성을 유지하면서 배열 원소를 제거해야 할 경우 사용
- 기존의 배열은 그대로 둔 상태에서 특정 조건을 만족하는 원소들만 따로 추출하여 새로운 배열 생성
- 조건을 확인하는 함수를 파라미터로 설정
- 이 함수에서 true를 반환할 경우에만 새로운 배열에 포함
