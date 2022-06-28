



# [Java] 예외 처리



### 예외 (Exception)

-	사용자의 잘못된 조작 또는 개발자의 잘못된 코딩으로 인한 오류
-	예외가 발생되면 프로그램 종류
-	예외 처리(Exception Handling)를 통해 정상 실행 상태로 돌아갈 수 있음
-	오류 중에서 대처가능한 오류



#### 예외의 종류

-	일반 예외 (Exception)
  -	컴파일 체크
  -	예외 처리 코드가 없으면 컴파일 오류 발생
-	실행 예외 (RuntimeException)
  -	예외 처리 코드를 생략하더라도 컴파일이 되는 예외
  -	경험에 따라 예외 처리 코드 작성 필요

#### 자바에서의 예외 관리

-	자바에서는 예외를 클래스로 관리
-	JVM은 프로그램을 실행하는 도중에 예외가 발생하면 해당 예외 클래스 객체 생성하여
-	예외 처리 코드에서 예외 객체를 이용할 수 있도록 함
-	모든 예외 클래스들은 ``java.lang.Exception`` 클래스를 상속 받음

<img width="500" alt="image-20220628212711197" src="https://user-images.githubusercontent.com/101630615/176180417-c799ad39-b677-4880-9188-a959de247a36.png">



#### 실행 예외

- ``NullPointerException``

  -	객체 참조가 없는 상태

  -	null 값을 갖는 참조변수로 객체 접근 연산자인 도트(.) 사용했을 때 발생

  -	```
    String data = null;
    System.out.println(data.equals(“자바”);
    ```

    

- ``ArrayIndexOutOfBoundsException``

  -	배열에서 인덱스 범위 초과하여 사용할 경우 발생

- ``NumberFormatException``

  -	숫자로 처리에서 발생하는 예외

- ``ClassCastException``

  -	타입 변환이 되지 않을 경우 발생
  -	타입 변환 발생
    -	상위 클래스와 하위 클래스 간 발생
    -	구현 클래스와 인터페이스 간에 발생
    -	자동 타입 변환 / 강제 타입 변환




<img width="500" alt="image-20220628212821238" src="https://user-images.githubusercontent.com/101630615/176180434-63859507-d01b-4cd9-bacf-f13a0a179057.png">



##### 정상 코드 : 자동 타입 변환 후 강제 타입 변환

<img width="600" alt="image-20220628212832309" src="https://user-images.githubusercontent.com/101630615/176180441-b614c21c-99e1-4a28-80f8-3686edd9f91c.png">



**예외 발생 코드**

<img width="600" alt="image-20220628212841556" src="https://user-images.githubusercontent.com/101630615/176180445-dbc6b420-4b2d-4f84-805e-153c01a39d37.png">

- 강제 타입 변환 시 ``ClassCastException`` 예외 발생시키지 않으려면
- 강제 타입 변환 전에 타입 변환이 가능한지 ``instanceof`` 연산자로 확인





#### 예외 처리 코드

-	예외 발생 시 프로그램 종료되지 않게 하고, 정상 실행을 유지할 수 있도록 처리하는 코드
-	일반 예외 : 반드시 작성해야 컴파일 가능
-	실행 예외
  -	컴파일러가 체크해주지 않으며 개발자의 경험에 의해 작성
  -	일부는 이클립스가 주의를 주기 때문에 미리 알 수 있음
  -	``try ~ catch ~ finally`` 블록을 이용해서 예외 처리 코드 작성




#### 예외 처리 형식 : try ~ catch ~ finally 구문



<img width="452" alt="image-20220628213245993" src="https://user-images.githubusercontent.com/101630615/176180446-c45302fd-24eb-4a7e-ba66-11dff515f4fe.png">





#### try ~ catch 구문 자동 삽입

-	(1) 컴파일러 제시할 경우 
  -	빨간 줄 위에 마우스 대고 Surround with try / catch 선택

-	(2) 직접 삽입할 경우 
  -	메뉴 Source / Surround with try / catch 
  -	예외 처리할 문장 모두 드래그해서 선택한 후 (선택 안 하면 선택하라고 메시지 출력)


<img width="600" alt="image-20220628213306195" src="https://user-images.githubusercontent.com/101630615/176180450-d5b05350-27f2-4bc7-bdfd-55f5c71939da.png">



#### 다중 catch

-	예외 별로 예외 처리 코드 다르게 구현
-	catch 블록 여러 개 포함
-	주의! - 단 하나의 catch 블록만 수행
  -	try 블록에서 여러 예외가 동시에 발생하지 않고 문장 순서대로 수행하면서 첫 번째 하나의 예외가 발생하면
  -	즉시 실행을 멈추고 해당 catch 블록 이동




<img width="600" alt="image-20220628213327786" src="https://user-images.githubusercontent.com/101630615/176180452-33a10df6-bb1f-4271-b2f0-f3a75d72d546.png">



***catch 순서***

- try 블록에서 예외가 발생했을 때 예외를 처리할 catch 블록은 위에서부터 차례대로 검색

- 만일 상위 클래스의 catch 블록이 위에 있다면 하위 클래스의 catch 블록은 실행 불가

  

#### 자바의 예외 클래스

<img width="600" alt="image-20220628213431835" src="https://user-images.githubusercontent.com/101630615/176180454-0163efe3-fd15-4557-9657-99500436f5ce.png">



### 예외 처리 떠넘기기 : ``throws``

``throws ``

-	메소드에서 처리하지 않은 예외를 호출한 곳으로 떠넘기는 역할
-	메소드 선언부 끝에 추가해서 작성

<img width="600" alt="image-20220628213505066" src="https://user-images.githubusercontent.com/101630615/176180455-a26ca4a2-5927-49be-b044-08ad454fee36.png">

-	발생할 수 있는 예외 종류별로 throws 뒤에 나열하는 것이 일반적이지만
-	throws Exception만으로 간단히 예외를 떠넘길 수 있음
-	throws가 붙어 있는 메소드는 반드시 try 블록 내에서 호출되어야 하고
-	catch 블록에서 예외를 처리해야 함

<img width="500" alt="image-20220628213530406" src="https://user-images.githubusercontent.com/101630615/176180460-c062cf81-f490-4ff6-8248-3c7d1ce36e42.png">



### 사용자 정의 예외와 예외 발생

#### 사용자 정의 예외 클래스 선언

- 자바 표준 API에서 제공하지 않는 예외 처리

- 개발자가 직접 정의해서 처리

- 애플리케이션 서비스와 관련된 예외

  

#### 사용자 정의 예외 클래스 선언 방법

-	예외 클래스를 상속받는 클래스로 생성
-	(1) 컴파일러가 체크하는 일반 예외로 선언하거나
  -	Exception 상속

-	(2) 컴파일러가 체크하지 않는 실행 예외 선언
  -	RuntimeException 상속


<img width="500" alt="image-20220628213747003" src="https://user-images.githubusercontent.com/101630615/176180473-c6b5cb19-8541-4415-8422-001ad18126c1.png">

 

#### 예외 발생시키기 :`` throw``

-	호출된 곳에서 발생한 예외를 처리하도록
-	코드에서 예외 발생시키는 법

<img width="600" alt="image-20220628213807267" src="https://user-images.githubusercontent.com/101630615/176180474-221620f1-6d43-438a-bbba-f53d918bd0b2.png">

``throw`` : 예외 발생
``throws`` : 자신을 호출한 곳에서 예외를 처리하도록 예외를 떠 넘기는 것



#### ``getMessage()``

-	예외 발생시킬 때 생성자 매개값으로 전달해서 예외 객체 내부에 저장된 메시지 리턴
-	원인 세분화하기 위해 예외 코드 포함
-	catch 절에서 활용

<img width="600" alt="image-20220628213633996" src="https://user-images.githubusercontent.com/101630615/176180468-209ee224-aa77-4b69-81d4-ae07a04e5f47.png">



#### ``printStackTrace()``

-	예외 발생 코드를 추적한 내용을 모두 콘솔에 출력
-	프로그램 테스트하면서 오류 찾을 때 유용하게 활용

<img width="600" alt="image-20220628213615707" src="https://user-images.githubusercontent.com/101630615/176180461-1072d4d8-1138-4d32-9ea8-b8eba5993f51.png">

