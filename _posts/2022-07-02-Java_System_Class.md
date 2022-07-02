



# [Java] 시스템 클래스




### System 클래스 용도

-	운영체제의 기능 일부 이용 가능
-	프로그램 종료, 키보드로부터 입력, 모니터 출력, 메모리 정리, 현재 시간 읽기 등
-	시스템 프로퍼티 읽기, 환경 변수 읽기 등



#### ``exit()`` 메소드 

-	프로그램 종료
-	강제적으로 JVM 종료
-	int 매개값 지정 - 종료 상태 값 
-	``exit(0) / exit(1)``
-	정상 종료 : 0
-	비정상 종료 : 0 이외의 값
-	어떤 값 주더라도 종료
-	``System.exit(0)``



##### 특정값이 입력되었을 경우에만 종료 

-	자바의 보안 관리자를 직접 설정해서 종료 상태값 확인 (System.setSecurityManager())
-	System.exit()이 실행되면 보안 관리자의 checkExit() 메소드가 자동 호출되는데
-	이 메소드에서 종료 상태값을 조사해서 특정 값이 입력되지 않으면 SecurityException을 발생시켜 System.exit()을 호출한 곳에서 예외 처리할 수 있도록 함
-	checkExit() 메소드 재정의



##### 현재 시간 읽기

-	``currentTimeMillis()`` : 밀리 세컨드
-	``nanoTime()`` : 나노 세컨드 단위의 값 리턴
-	주로 프로그램 실행 소요 시간 구할 때 이용



**시스템 프로퍼티 읽기 ``(getProperty())``**

-	시스템 프로퍼티 : JVM이 시작할 때 자동으로 설정되는 시스템의 속성값
-	대표적인 키와 값 (key, value)



<img width="700" alt="image-20220702155623989" src="https://user-images.githubusercontent.com/101630615/176991153-ccbab093-7a94-43ac-a90f-b4ffe704113e.png">



**환경 변수 읽기 : ``getenv()``**

-	운영체제가 제공하는 환경 변수 값(문자열)을 읽음





# String 클래스



### String 생성자

-	String()
-	바이트 배열(byte[])을 문자열로 변환
  -	파일을 읽거나 네트워크를 통해서 받은 데이터는 보통 바이트 배열

-	지정한 문자셋으로 디코딩



**키보드로부터 읽은 바이트 배열을 문자열로 변환**

<img width="700" alt="image-20220702155721602" src="https://user-images.githubusercontent.com/101630615/176991156-b08d2c81-e561-4dc4-a4e4-5729cc74884d.png">




윈도우 
-	영문 : 1바이트, 한글 : 2바트, 엔터 : 2바이트

맥

-	영문 : 1바이트, 한글 : 3바이트. 엔터 : 1바이트



### String 메소드

- 문자열의 추출, 비교, 찾기, 분리, 변환 등과 같은 다양한 메소드 포함

  

### 사용 빈도 높은 메소드

<img width="700" alt="image-20220702155829968" src="https://user-images.githubusercontent.com/101630615/176991158-a20ebcf6-3591-4492-a52a-2bf46c1c08de.png">





**문자 추출 : ``charAt(인덱스)``**

-	주어진 인덱스의 문자 리턴



<img width="600" alt="image-20220702155853034" src="https://user-images.githubusercontent.com/101630615/176991160-f9baf117-b840-4633-ba83-9db0de7cee6d.png">





**바이트 배열로 변환 ``(getBytes())``**

-	시스템의 기본 문자셋으로 인코딩된 바이트 배열 얻기
  -	``byte[] bytes = “문자열”.getBytes();``

-	특정 문자셋으로 인코딩 된 바이트 배열 얻기
  - ``“문자열”.getBytes(“UEC-KR”)``
  - ``“문자열”.getBytes(“UTF-8”)``



**문자열 찾기 ``(indexOf(“문자열”))``**

-	매개값으로 주어진 문자열이 시작되는 인덱스 반환
-	주어진 문자열이 포함되어 있지 않으면 -1 리턴
-	특정 문자열이 포함되어 있는지 여부에 따라 실행 코드 달리할 때 사용



<img width="600" alt="image-20220702160109272" src="https://user-images.githubusercontent.com/101630615/176991161-e0a4f6ed-5469-4de1-a61d-fc94393ac86b.png">



***주의! 문자열 길이 (length()) - 공백도 문자에 포함***





**문자열 대치 : ``replace(“문자열1”, “문자열2”)``**

-	첫 번째 매개값인 문자열을 찾아서
-	두 번째 매개값인 문자열로 대치
-	새로운 문자열 리턴



<img width="400" alt="image-20220702160154009" src="https://user-images.githubusercontent.com/101630615/176991162-e2d44cff-c487-419a-929b-631d5abaebb0.png">





**문자열 잘라내기 : ``substring()``**

-	문자열 일부 추출
-	``substring(int beginIndex, int endIndex)``
  -	주어진 시작과 끝 인덱스 사이의 문자열 추출

-	beginIndex부터 endIndex-1까지
  -	``substring(int beginIndex)``
  -	beginIndex부터 끝까지 문자열 추출


<img width="500" alt="image-20220702160228347" src="https://user-images.githubusercontent.com/101630615/176991163-c05d96d6-3ec7-4701-aef0-ae83dd6681e2.png">





**알파벳 소/대문자 변경 : ``toLowerCase() / toUpperCase()``**

-	문자열을 모두 소문자/대문자로 바꾼 새로운 문자열을 생성한 후 반환
-	원래 문자열이 변경된 것은 아님



##### 문자열의 앞뒤 공백 잘라내기 : ``trim()``

-	문자열의 앞뒤 공백을 제거한 새로운 문자열을 생성해서 리턴


##### 문자열 변환 : ``valueOf()``

-	기본 타입의 숫자값을 문자열로 변환
-	String 클래스에 매개변수 타입별로 메소드 오버로딩되어 있음
-	static  메소드 : ``String.valueOf()``

<img width="294" alt="image-20220702160353888" src="https://user-images.githubusercontent.com/101630615/176991166-6d32e3f8-db2c-4d5b-a3c0-80acc967eaf7.png">



#### 문자열 분리 방법

-	String ``split()`` 메소드 이용
-	java.util.StringTokenizer 클래스 이용
-	토큰  : 쪼개진 문자열 단위
  -	특정 구분자로 분리되는 문자열의 구성 요소

-	String ``split()``
  -	구분자로 문자열 분리 (123-456)
  -	정규표현식을 구분자로 해서 부분 문자열 분리
  -	배열에 저장하고 리턴


```java
String tel = “010-1234-1234”;
String[] tels = tel.split(“-”);
```



#### StringTokenizer 클래스

-	문자열에서 구분자로 분리한 토큰을 반환



<img width="600" alt="image-20220702160500773" src="https://user-images.githubusercontent.com/101630615/176991167-ff60bbaa-2b29-4f94-a65d-84fec8408874.png">





##### 문자열 결합 연산자 : +

-	String은 내부의 문자열 수정 불가
-	대치된 새로운 문자열 리턴



##### StringBuffer, StringBuilder 클래스

-	버퍼에 문자열 저장 
-	buffer : 데이터를 임시로 저장하는 메모리
-	버퍼 내부에서 추가, 수정, 삭제 작업 가능
-	멀티 스레드 환경 : StringBuffer 사용
-	단일 스레드 환경 : StringBuilder 사용

 

<img width="400" alt="image-20220702160553308" src="https://user-images.githubusercontent.com/101630615/176991168-dda345e2-f20f-4557-9100-4e6b7a439cfb.png">





#### 정규 표현식 (Regular Expression) 

-	문자열이 정해져 있는 형식으로 구성되어 있는지 검증할 때 사용
-	예 : 이메일, 전화번호, 비밀번호 등 

##### 문자, 숫자, 기호, 반복 기호 등이 결합된 문자열

<img width="500" alt="image-20220702160610348" src="https://user-images.githubusercontent.com/101630615/176991169-cbb52cdf-d5f4-45a4-b646-0b70ff780711.png">



##### Pattern 클래스

-	정규 표현식으로 문자열을 검증하는 역할
-	``matches(“정규식”, “입력된 문자열”);``
-	결과는 boolean 타입


#### Arrays 클래스

-	배열 조작 기능을 가지고 있는 클래스
-	복사, 정렬, 검색 등 
-	제공하는 정적 메소드 :`` Arrays.copyOf(), Arrays.sort()``



##### Arrays 클래스 메소드

<img width="700" alt="image-20220702160650260" src="https://user-images.githubusercontent.com/101630615/176991170-5b122d6e-2373-4d00-a401-e221434cc603.png">





#### 배열 복사

-	``Arrays.copyOf(원본배열, 복사할 길이)``
  -	0 ~ (복사할 길이 -1)까지 항목 복사


<img width="400" alt="image-20220702160923616" src="https://user-images.githubusercontent.com/101630615/176991171-11b4582c-0075-48fe-9bc8-52937cec75b5.png">



-	``copyOfRange (원본배열, 시작 인덱스, 끝 인덱스)``
  -	시작 인덱스 ~ (끝 인덱스-1)까지 항목 복사	


<img width="400" alt="image-20220702160933873" src="https://user-images.githubusercontent.com/101630615/176991172-a94bc0e4-3dd3-4513-9e83-8f1a8b98b9b9.png">



-	``System.arraycopy()``

<img width="800" alt="image-20220702161045549" src="https://user-images.githubusercontent.com/101630615/176991173-8405a4e8-dd7f-4e12-b808-8a2b02329e6e.png">

##### 배열 항목 정렬 :`` Arrays.sort(배열)``

-	항목 오름차순으로 정렬
-	기본 타입이거나 String 배열 자동 정렬



##### 배열 항목 검색 : ``Arrays.binarySearch()``

-	특정 값 위치한 인덱스 얻는 것
-	Arrays.sort(배열)로 먼저 정렬하고
-	``Arrays.binarySearch(배열, 찾는 값)``  메소드로 항목 찾기 



### Math 클래스

-	수학 계산에 사용할 수 있는 정적 메소드 제공

<img width="700" alt="image-20220702161957711" src="https://user-images.githubusercontent.com/101630615/176991175-5934a9ec-c4be-4d36-8a6f-f575325bb202.png">



### Random 클래스

-	boolean, int, long, float, double 난수 리턴
-	난수를 생성하는 알고리즘에 사용되는 종자값(seed) 설정 가능
  -	종자값이 같으면 동일한 난수 발생


```java
Random r = new Random():
int x = r.nextInt(10) +1; // 1~10 정수

int num = (int)(Math.ramdom() * 10 ) +1;
```



##### Random 클래스로부터 Random 객체 생성하는 방법

<img width="700" alt="image-20220702162027972" src="https://user-images.githubusercontent.com/101630615/176991176-e3e5c199-d6ea-4d5b-a19d-ec39b5176c8d.png">



##### Random() // seed 값 없을 경우

-	현재 시간을 초기값으로 하는 난수 발생
-	실행할 때마다 다른 난수 발생

##### Random(seed)

-	seed 값을 초기값으로 하는 난수 발생
-	실행할 때마다 동일한 난수 발생



#### Random  클래스가 제공하는 메소드



<img width="700" alt="image-20220702162052770" src="https://user-images.githubusercontent.com/101630615/176991177-35a6860a-f2cc-45c6-9cf2-7d938270631a.png">

 


#### Date 클래스 

-	날짜를 표현하는 클래스

```java
import java.util.Date;

Date now = new Date();
```



##### SimpleDateFormat

-	날짜 형식 클래스
-	``import java.text.SimpleDateFormat;``

<img width="700" alt="image-20220702162237413" src="https://user-images.githubusercontent.com/101630615/176991178-7e287162-321b-4ebb-9d26-377e3cfdd05d.png">



##### Calendar 클래스

-	달력을 표현한 추상 클래스
-	OS에 설정된 시간대(TimeZone) 기준의 Calendar 객체 얻기
-	``Calendar now = Calendar.getInstance();``
-	다른 시간대의 Calendar 객체 얻기

<img width="500" alt="image-20220702162301239" src="https://user-images.githubusercontent.com/101630615/176991179-06156463-cc82-48bb-8260-9b9acc91e7a8.png">



#### 날짜 및 시간 정보 얻기



<img width="700" alt="image-20220702162311984" src="https://user-images.githubusercontent.com/101630615/176991180-1d2acfba-299f-4192-8412-58db05988b77.png">



#### Format 클래스

-	숫자와 날짜를 원하는 형식의 문자열로 변환
-	종류
  -	숫자 형식 : DecimalFormat
    -	적용할 패턴 선택해 생성자 매개값으로 지정 후 객체 생성

  -	날짜 형식 : SimpleDateFormat
  -	매개변수화된 문자열 형식 : MessageFormat




#### 매개변수화된 문자열 형식 : MessageFormat 클래스

-	일정한 형식으로 문자열 포맷
-	문자열 데이터가 들어갈 자리를 표시해 두고
-	프로그램 실행 중에 동적으로 데이터를 삽입해 문자열 완성

<img width="600" alt="image-20220702162349091" src="https://user-images.githubusercontent.com/101630615/176991181-9a12494d-fb3d-496d-a54f-e30c96bfccb8.png">



### 날짜와 시간을 표현하는 5개 클래스 



<img width="700" alt="image-20220702162401240" src="https://user-images.githubusercontent.com/101630615/176991183-4989d814-85bd-4c16-b000-c23ba1b3f628.png">



<img width="700" alt="image-20220702162406681" src="https://user-images.githubusercontent.com/101630615/176991184-e7bfdb4d-784f-47ef-a7a4-89218894fe69.png">