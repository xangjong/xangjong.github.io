



# [Java] Object 클래스



### Object 클래스

-	자바의 최상위 부모 클래스
-	다른 클래스를 상속하지 않으면 java.lang.Object 클래스 상속 암시
-	Object의 메소드는 모든 클래스에서 사용 가능



<img width="500" alt="image-20220702154342366" src="https://user-images.githubusercontent.com/101630615/176991089-d705d275-1bde-4da9-82df-4eb63eae3cf7.png">





### Object 클래스의 메소드

-	Object 클래스는 필드는 없고 메소드로들로 구성
-	모든 클래스가 Object 클래스를 상속하기 때문에 Object 클래스의 메소드는 모든 클래스에서 사용 가능
-	equals()
-	hasCode()
-	toString()
-	clone()
-	finalize()





#### ``equals()`` 메소드

-	객체 비교
-	기본적으로 == 연산자와 동일한 결과 



<img width="452" alt="image-20220702154733927" src="https://user-images.githubusercontent.com/101630615/176991090-71699801-3485-4db0-9b8e-9bfec4fdf934.png">



#### ``hashCode()``

-	객체의 해시코드 반환
-	객체 해시코드
-	객체를 식별할 하나의 정수값
-	Object의 hashCode() 메소드는 객체의 메모리 번지를 이용해 해시코드를 만들어서 리턴
-	개별 객체는 해시코드가 모두 다름



#### ``toString()``

-	객체 문자정보 반환
-	객체를 문자열로 표현한 값
-	Object 클래스의 toString() 메소드는 객체의 문자정보 리턴
  -	Object 하위 클래스에서 메소드 재정의해서 사용
    -	String  클래스 : 문자열 리턴
    -	Date 클래스 : 현재 시스템의 날짜와 시간 정보 리턴



#### ``clone()`` : 객체 복제

-	원본 객체의 필드 값과 동일한 값을 가지는 새로운 객체를 생성

**객체 복제 이유**

-	객체를 안전하게 보호하기 위해 
-	신뢰하지 않는 영역으로 원본 객체를 넘겨할 경우 원본 객체의 데이터가 훼손될 수 있기 때문에 복제된 객체를 만들어서 넘겨 객체 보호
-	복제된 객체의 데이터가 훼손되더라도 원본 객체는 아무런 영향을 받지 않기 때문에 데이터를 안전하게 보호할 수 있음





### 객체 복제 방법

#### 얕은 복제

- 단순히 필드값을 복사해서 객체를 복제하는 방법

- 기본 타입 : 값 복사

- 참조 타입 : 객체의 번지 복사 (같은 객체 참조)

- Object 클래스의 clone() 메소드

  -	자신과 동일한 필드값을 가진 얕은 복제된 객체 리턴

  -	clone() 메소드로 객체를 복제하려면 원본 객체는 반드시 java.lang.Cloneable 인터페이스를 구현하고 있어야 함

     (클래스 설계자가 복제를 허용한다는 의미 표시)

  -	Cloneable 인터페이스를 구현하지 않으면 clone() 호출 시 

  -	``CloneNotSupportedException`` 예외 발생되어 복제 실패

  -	Clone() 메소드는 호출 시 예외 처리 필요

    -	try ~ catch 구문 사용



<img width="450" alt="image-20220702153804304" src="https://user-images.githubusercontent.com/101630615/176991085-22d1efb9-8c18-41e3-9f53-adac7b613c12.png">





#### 깊은 복제 (deep clone) : 참조하고 있는 객체도 복제

-	얕은 복제에서 참조 타입의 경우 객체의 번지 복사 (같은 객체 참조)
-	복제 객체를 변경하면 원본 객체도 변경됨 (얕은 복제의 단점)
-	깊은 복제는 참조하고 있는 객체도 복제
-	clone() 메소드를 재정의해서 참조 객체를 복제하는 코드 직접 작성



<img width="500" alt="image-20220702153811926" src="https://user-images.githubusercontent.com/101630615/176991088-8690516f-5710-4cc0-afb5-2488fcd448ed.png">



#### ``finalize()``

-	객체 소멸자
-	참조하지 않는 배열이나 객체는 쓰레기 수집기(Garbage Collector : GC)가 자동으로 힙영역에서 소멸시킴
-	GC는 객체를 소멸하기 전에 객체 소멸자(finalize()) 실행
-	Object의 finalize()는 기본적으로 실행 내용이 없음
-	객체 소멸되기 전에 실행 코드가 있다면 Object의 finalize() 재정의



#### ``System.gc()``

-	Garbage Collector 호출
-	Garbage Collector를 호출하여 JVM에게 요청하면
-	바로 Garbage Collector가 실행되는 것은 아님
-	Garbage Collector는 메모리가 부족하거나 CPU가 한가할 때 JVM에 의해서 자동 실행
-	따라서 finalize()가 언제 호출될지는 확실히 알 수 없음
-	주의!
  -	될 수 있으면 소멸자는 사용하지 않음
    -	GB는 메모리의 모든 쓰레기를 객체를 소멸하지 않음
    -	GC의 구동 시점이 일정하지 않음



Objects 클래스
-	Object의 유틸리티 클래스



<img width="700" alt="image-20220702155014565" src="https://user-images.githubusercontent.com/101630615/176991091-5d4cd39b-e456-401c-b188-d27c653051b2.png">