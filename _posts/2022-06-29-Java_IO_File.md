



# [Java] 입출력



#### java.io 패키지

-	자바의 기본적인 데이터 입출력(IO: Input/Output) API 제공

<img width="600" alt="image-20220629013102002" src="https://user-images.githubusercontent.com/101630615/176235248-c7b9dd22-7abd-4c05-a42e-0d80429642d4.png">



### 자바의 스트림 (Stream)

-	입출력 장치와 자바 응용 프로그램 연결 통로
-	입력 스트림
  -	입력 장치로부터 자바 프로그램으로 데이터 전달하는 소프트웨어 모듈

-	출력 스트림
  -	자바 프로그램에서 출력 장치로 데이터를 보내는 소프트웨어 모듈

-	입출력 스트림 기본 단위 : 바이트 (Byte)

#### 자바 입출력 스트림 특징

-	단방향
-	선입선출구조 (FIFO)



#### 입력 스트림과 출력 스트림

<img width="600" alt="image-20220629013213557" src="https://user-images.githubusercontent.com/101630615/176235265-430d70f2-5e3b-4414-b4cb-30c573d437ab.png">

 

#### 바이트 기반 스트림

-	이미지, 멀티미디어, 문자 등 모든 종류의 데이터를 받고 보내는 것 가능
-	입출력되는 데이터를 단순 바이트의 스트림으로 처리
-	예 : 바이너리 파일을 읽는 입력 스트림

#### 문자 기반 스트림

-	문자만 입출력하는 스트림
-	문자만 받고 보낼 수 있도록 특화
-	문자가 아닌 바이너리 데이터는 스트림에서 처리하지 못함
-	예 : 텍스트 파일을 읽는 입력 스트림

#### 데이터 입출력 구분

<img width="700" alt="image-20220629013314882" src="https://user-images.githubusercontent.com/101630615/176235268-20650d16-0854-46a7-8023-5ca3e6cbef05.png">



#### ``InputStream`` 

-	바이트 기반 입력 스트림의 최상위 클래스로 추상 클래스

<img width="500" alt="image-20220629013351340" src="https://user-images.githubusercontent.com/101630615/176235272-f0717977-2b5b-483f-8c3f-8c2e625c35c4.png">



#### InputStream 클래스의 주요 메소드

<img width="700" alt="image-20220629013528550" src="https://user-images.githubusercontent.com/101630615/176235274-a2c983b5-8d09-4b38-a316-165eb66b106f.png">



#### ``OutputStream``

-	바이트 기반 출력 스트림의 최상위 클래스로 추상 클래스

<img width="500" alt="image-20220629013554782" src="https://user-images.githubusercontent.com/101630615/176235276-600b4165-344c-4db7-88af-f9a746d86c67.png">

 

#### OutputStream의 주요 메소드

<img width="600" alt="image-20220629013639793" src="https://user-images.githubusercontent.com/101630615/176235277-0272a8c5-d1ce-48dd-9a16-f317902a8206.png">

#### ``Reader``

-	문자 기반 입력 스트림의 최상위 클래스로 추상 클래스

<img width="500" alt="image-20220629013656880" src="https://user-images.githubusercontent.com/101630615/176235284-052e1f70-5a67-43b9-aaec-74b8d0319b76.png">



<img width="600" alt="image-20220629013702253" src="https://user-images.githubusercontent.com/101630615/176235285-04679a4b-7425-4e59-a7d6-7d4925f3aa5c.png">





#### ``Writer``

-	문자 기반 출력 스트림의 최상위 클래스로 추상 클래스

<img width="500" alt="image-20220629013909751" src="https://user-images.githubusercontent.com/101630615/176235287-d3bd4d69-487b-4464-b4c3-4abb652347b6.png">



<img width="700" alt="image-20220629013916891" src="https://user-images.githubusercontent.com/101630615/176235289-7b99da3c-1e74-4a4e-826a-b20dc60449db.png">



### File 클래스

-	파일 시스템의 파일을 표현하는 클래스
-	파일 크기, 파일 속성, 파일 이름 등의 정보 제공
-	파일 생성 및 삭제 기능 제공
-	디렉토리 생성, 디렉토리에 존재하는 파일 리스트 얻어내는 기능 제공
-	파일 객체 생성



#### File 클래스 메소드

<img width="700" alt="image-20220629014149906" src="https://user-images.githubusercontent.com/101630615/176235292-998ea493-dcf9-4493-bd0b-47710f0fe2df.png">



#### ``mkdir()``

-	새로운 디렉토리 생성 후 결과 반환 (true/false)
-	최하위 디렉토리만 생성 가능
-	바로 위의 디렉토리가 존재하지 않으면 생성 불가

#### ``mkdirs()``

-	새로운 디렉토리 생성 후 결과 반환 (true/false)
-	상위 디렉토리 존재하지 않으면 상위 디렉토리 생성하고 지정한 디렉토리 생성



#### 파일 및 디렉토리의 정보를 리턴하는 메소드



<img width="700" alt="image-20220629014210447" src="https://user-images.githubusercontent.com/101630615/176235297-8be94f15-f012-482d-b159-8957eac156cb.png">