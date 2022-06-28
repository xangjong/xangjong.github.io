



# [Java] 컬렉션 프레임워크



### 컬렉션 프레임워크 (Collection Framework)

-	컬렉션(다수의 객체)을 다루기 위한 표준화된 프로그래밍 방식
-	많은 양의 데이터를 저장, 삭제, 검색, 비교, 정렬 등의 작업을 편리하고 쉽게 수행
-	객체들을 효율적으로 추가, 삭제, 검색 등을 할 수 있도록 제공되는 컬렉션 라이브러리
-	인터페이스를 통해서 정형화된 방법으로 다양한 컬렉션 클래스 이용
-	java.util. 패키지에 포함



#### 여러 개의 값을 저장해서 사용하는 구조

-	배열
  -	애플리케이션 개발 시 다수의 객체를 저장해 두고 필요할 때 꺼내서 사용하는 경우 가장 간단하게 사용하는 방법

-	배열의 문제점
  -	생성 시 크기 고정되고 사용 시 크기 변경 불가
  -	불특정 다수의 객체를 저장하기에는 문제

-	객체 삭제했을 때 해당 인덱스가 비게 됨
  -	객체를 저장하려면 어디가 비어있는지 확인해야 하는 코드 필요




<img width="400" alt="image-20220629002356361" src="https://user-images.githubusercontent.com/101630615/176222761-d3f07005-e668-458b-9833-6f11a4ce5788.png">





#### 컬렉션 프레임워크의 주요 인터페이스

<img width="600" alt="image-20220629002431836" src="https://user-images.githubusercontent.com/101630615/176222781-47a267fc-bb8b-48ef-b006-713c624f4006.png">



#### List / Set / Map 인터페이스

<img width="600" alt="image-20220629002441661" src="https://user-images.githubusercontent.com/101630615/176222796-1420d4e6-72f8-4c83-b199-3b54880a966a.png">



### List 컬렉션

List(인터페이스) 컬렉션의 특징

-	순서가 있는 데이터의 집합
-	인덱스로 관리
-	중복해서 객체 저장 가능
-	구현 클래스
  -	``ArrayList``
  -	``Vector``
  -	``LinkedList``



<img width="500" alt="image-20220629002529330" src="https://user-images.githubusercontent.com/101630615/176222803-cc733cfd-6c66-4157-8ef9-4475ef46abe4.png">



#### List 컬렉션의 주요 메소드

<img width="600" alt="image-20220629002602441" src="https://user-images.githubusercontent.com/101630615/176222810-7979dbd3-fe0b-4d76-b411-4eb2d6847c6d.png">



#### ``ArrayList ``

-	List 인터페이스의 구현 클래스
-	크기가 가변적으로 변하는 선형 리스트
-	배열과 유사
  -	순차 리스트, 인덱스 사용

-	배열과 차이
  -	배열 : 크기 고정

-	``ArrayList ``
  -	객체 추가 가능
  -	저장 용량 초과 시 자동으로 저장 용량 증가
  -	기본 10개
  -	``new ArrayList(30);``  처음부터 크게 설정 가능




#### 제네릭을 사용하지 않을 경우

-	강제 타입 변환 필요

```java
List list = new ArrayList();

list.add("hello");

String str = (String)list.get(0);
```

#### 제네릭 사용할 경우

```java
ArrayList<String> / ArrayList<Integer>
```

-	ArrayList 객체 생성 시 타입 파라미터로 저장할 객체의 타입 지정함으로써
-	강제 타입 변환 불필요





#### 객체 추가

- 인덱스 0부터 차례로 저장

#### 객체 제거

-	제거된 객체의 바로 뒤 인덱스부터 마지막 인덱스까지 앞으로 1씩 당겨짐
-	따라서 빈번한 객체 삭제와 삽입이 일어나는 경우 ArrayList 사용하는 것이 바람직하지 않음

<img width="363" alt="image-20220629002904920" src="https://user-images.githubusercontent.com/101630615/176222820-4eaaf718-257d-41a9-ac64-5860a99fa9e2.png">




#### ``Iterator``

-	java.util 패키지의 Iterator``<E>`` 인터페이스
-	요소가 순서대로 저장된 컬렉션에서 요소를 순차적으로 검색할 때 사용

```java
Vector<Integer> v = new Vector<Integer>();

Iterator<Integer> it = v.iterator();
```

-	벡터 v의 요소를 순차적으로 검색할 ``Iterator`` 객체 반환
-	``hasNext()`` / ``next()`` 메소드



#### ``LinkedList``

-	List 구현 클래스로 ArrayList와 사용 방법은 동일
-	내부 구조가 다름
-	인접 참조를 링크해서 체인처럼 관리 (이전/다음 객체의 주소를 갖고 있음)
-	특정 인덱스에서 객체를 제거하거나 추가하게 되면 바로 앞위 링크만 변경
-	빈번한 객체 삭제와 삽입 일어나는 곳에서는 ArrayList보다 좋은 성능



<img width="500" alt="image-20220629003122513" src="https://user-images.githubusercontent.com/101630615/176222822-165c2d0a-6ef6-4d52-ad31-e49464a2fb96.png">



#### ``Vector``

```java
List<E> list = new Vector<E>();
```

- ArrayList와 동일한 내부 구조

-	스레드 동기화 (synchronization)되어 있기 때문에
-	복수의 스레드가 동시에 Vector에 접근해 객체를 추가, 삭제하더라도 스레드에 안전 (thread safe)



<img width="322" alt="image-20220629003200257" src="https://user-images.githubusercontent.com/101630615/176222825-0fbde52c-f3b5-460b-b264-050fc78da1f4.png">





### Set 컬렉션

Set 컬렉션 특징

-	수학의 집합에 비유
-	저장 순서가 유지되지 않음
  -	인덱스로 객체를 검색해서 가져오는 메소드 없음
  -	``get()`` 메소드 없음

-	객체를 중복 저장 불가
-	구현 클래스
-	``HashSet`` 
-	``LinkedHashSet`` 
-	``TreeSet``



#### Set 컬렉션의 주요 메소드



<img width="600" alt="image-20220629003238917" src="https://user-images.githubusercontent.com/101630615/176222826-b315abba-fa1d-481d-aadc-218c66f5a562.png">



#### ``HashSet``

```
Set<E> set = new HashSet<E>();
```

- Set 인터페이스의 구현 클래스

-	객체를 순서없이 저장
-	동일 객체 및 동등 객체는 중복 저장하지 않음
-	동등 객체 판단 방법
-	객체 저장하기 전에 ``hasCode()``를 호출해서 해시코드를 얻어내어
-	저장되어 있는 객체들의 해시코드와 비교해서 동일일 해시코드가 있다면
-	``equals()`` 메소드로 두 객체를 비교해서 true가 나오면 동일한 객체로 판단하고 중복 저장하지 않음



<img width="500" alt="image-20220629003411903" src="https://user-images.githubusercontent.com/101630615/176222829-7c9f23fb-9653-4a59-8423-95897c997b9c.png">





##### 사용자 정의 클래스 중복 안 되게 저장

-	사용자 정의 클래스에서 객체가 중복 저장되지 않게 하려면
-	``hashCode()``와 ``equals()`` (둘 다) 재정의 해서 동등 객체가 될 조건을 정해야 함





### Map 컬렉션

Map 컬렉션의 특징

-	키(key)와 값(value)의 쌍으로 이루어진 데이터의 집합
-	키와 값은 모두 객체
-	키는 중복될 수 없지만 값은 중복 저장 가능
-	구현 클래스 
-	``HashMap``
-	 ``HashTable``
-	 ``LinkedHashMap``
-	``TreeMap``
-	``  Properties``



<img width="600" alt="image-20220629003451529" src="https://user-images.githubusercontent.com/101630615/176222833-b81be768-35f1-46e9-bcda-9b163ac558c9.png">



#### Map 주요 메소드

<img width="600" alt="image-20220629003544652" src="https://user-images.githubusercontent.com/101630615/176222834-70784141-7762-45ca-a590-5af3bb233452.png">





<img width="600" alt="image-20220629003552802" src="https://user-images.githubusercontent.com/101630615/176222838-6da50c8b-f650-4dd3-a3ed-8d61bd3be9c3.png">



키 객체는 hashCode()와 equals() 메소드를 재정의해 동등객체가 될 조건을 정함

<img width="500" alt="image-20220629003602911" src="https://user-images.githubusercontent.com/101630615/176222840-1b0de90b-1f9f-4c0e-8b44-616f244f2363.png">



##### 키 타입은 String 많이 사용

-	String 문자열이 같을 경우 동등 객체가 될 수 있도록 hashCode()와 equals() 메소드가 재정의되어 있기 때문



#### ``Hashtable``

-	키 개체 만드는 법은 HashMap과 동일
-	Hashtable은 스레드 동기화(synchronization)가 된 상태
  -	복수의 스레드가 동시에 Hashtable에 접근해서 객체를 추가, 삭제하더라도 스레드에 안전 
-	Hashtable : 멀티 스레드 환경에서 주로 사용
-	HashMap : 단일 스레드 환경에서 사용
  -	synchronization하면 객체 잠금이 발생하므로 성능 저하

