# [React] 라우팅(Routing)



### 라우팅 (Routing)

- URL에 따라 해당 화면 출력 가능 (링크)

- 다른 주소에 다른 화면을 보여주는 것

- 리액트 라이브러리 자체에 라우팅 기능이 내장되어 있지 않지만 리액터 라우터 라이브러리를 사용하여 쉽게 구현 가능

- ``react-router-dom`` 라이브러리 설치 

  

기존 index.js

```react
import {BrowserRouter} from ‘react-router-dom’;

<React.StrictMode>
	<App />
</React.StrictMode>
// 기존에서 BrowserRouter로 변경

<BrowserRouter>
  <App />
</BrowserRouter>
```



Route 컴포넌트로 특정 주소에 컴포넌트 연결

```react
<Routes>
	<Route path="/" component={Home} />
	<Route path="/about" component={About} />
</Routes>

<Link to="/about">About 화면 보기</Link>

import {Link, Routes, Rout} from ‘react-router-dom’;
```





#### Link 컴포넌트를 사용하여 다른 주소로 이동

- 리액터 라우터를 사용할 때는 ``<a>`` 태그 사용하지 못함

  -	``<a>`` 태그는 페이지 전환 과정에서 페이지를 새로 불러오기 때문에 애플리케이션이 갖고 있던 상태들이 모두 없어짐
  -	렌더링 컴포넌트도 모두 사라지고 다시 처음부터 렌더링함

- ``<Link>`` 태그 사용 

  -	페이지를 새로 불러오지 않고 애플리케이션을 그대로 유지한 상태에서 페이지의 주소만 변경
  -	페이지 전환 기능이 내장되어 있음
  -	``<Link to='주소'></Link>``
  -	페이지 소스보기에는 ``<a>``로 표시됨

- path를 통해 파라미터 전달

  

```react
<a href="" target="_blank" rel="noreferrer noopener" >...</a>
```

-	리액트 : 보안 문제로 인한 경고 출력,
  -	``rel="noreferrer noopener"``를 추가해야 함
-	noreferrer  
  -	다른 페이지로 이동할 때 링크를 건 페이지의 주소 등의 정보를 브라우저가  refer 해서 HTTP 헤더로 reffer를 송신하지 않게 하는 것
-	noopener
  -	링크된 페이지에서 window.opener를 사용해서 링크를 건 페이지를 참조할 수 없게 함
  -	프로세스가 계속 연결되어 있어서 보안상, 성능상 문제 발생