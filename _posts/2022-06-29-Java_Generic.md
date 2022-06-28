

# [Java] 제네릭



### 제네릭

-	클래스(인터페이스)나 메소드를 타입 파라미터를 이용하는 기법
-	클래스 설계 시에 타입 ``<T>``이 아직 결정 되지 않음
-	총칭해서 제네릭 타입
-	public class 클래명``<T>`` {  …. }
-	public interface 인터페이스명``<T>`` {  }



<img width="240" alt="image-20220629001040995" src="https://user-images.githubusercontent.com/101630615/176221463-8c48c140-9e26-4611-911c-e6ee2299630e.png">



```
Gen<String> gen = new Gen<String>();

Gen<Integer> gen2 = new Gen<Integer>();
```

<> : 기본 데이터 타입은 올 수 없음

-	``<int>`` : X
-	``<Integer>`` : Wrapper 클래스 사용
  -	기본 데이터 타입에 대응되는 클래스
  -	기본 데이터 타입을 객체로 포장




#### 제네릭을 사용하는 코드의 이점

-	컴파일 시 강한 타입 체크 가능
  -	실행 시 타입 에러가 나는 것 방지
  -	컴파일 시에 미리 타입을 강하게 체크해서 에러를 사전에 방지
-	강제 타입 변환 제거 가능 (프로그램 성능 향상)
-	제네릭을 사용하지 않을 경우

```java
List list = new ArrayList();

list.add(“hello”);

String str = (String) list.get(0);
```

Object -> String  강제 타입 변환

-	제네릭을 사용할 경우

```java
List<String> list = new ArrayList<String>();

list.add(“hello”);

String str = list.get(0);
```

  강제 타입 변환 불필요



#### 타입 파라미터

-	일반적으로 대문자 알파벳 한 문자로 표현
-	꼭 T라고 하지 않아도 됨

```java
E : Element
T : Type
V : Value
K : Key
```

-	개발 코드에서는 타입 파라미터 자리에 구체적인 타입을 지정해야 함 

<img width="452" alt="image-20220629001336876" src="https://user-images.githubusercontent.com/101630615/176221476-4b763d7a-c0af-4f61-955b-99e21887c993.png">

-	클래스 내부에서 사용할 데이터 타입을 클래스 외부에서 지정



#### 제네릭 타입

-	타입을 파라미터로 가지는 클래스와 인터페이스
-	선언 시 클래스 또는 인터페이스 이름 뒤에 “<>” 부호 붙임
-	“<>” 사이에는 타입 파라미터 위치 : ``<T>``

#### 타입 파라미터

-	일반적으로 대문자 알파벳 한 문자로 표현 : ``<T>``
-	개발 코드에서는 타입 파라미터 자리에 구체적인 타입을 지정

#### 멀티 타입 파라미터


-	제네릭 타입은 두 개 이상의 타입 파라미터 사용 가능
-	각 타입 파라미터는 콤마로 구분

```
class …<K, V, …> { … } 

interface .. <K, V, …> { …} 
```



<img width="700" alt="image-20220629001509281" src="https://user-images.githubusercontent.com/101630615/176221485-d8451041-96c0-4070-a97c-f6a089ae7e56.png">



자바 7 버전 이상부터 다이아몬드 연산자를 사용해 간단히 작성하고 사용 가능 

<img width="452" alt="image-20220629001529820" src="https://user-images.githubusercontent.com/101630615/176221493-c6c12904-08f8-4f3b-bd4d-2e4943775d71.png">



### 제네릭 메소드

- 매개변수 타입과 리턴 타입으로 타입 파라미터를 갖는 메소드

#### 제네릭 메소드 선언 방법

-	리턴 타입 앞에 “<>” 기호를 추가하고 타입 파라미터 기술
-	타입 파라미터를 리턴 타입과 매개변수에 사용
-	호출할 때 ``<T>``가 결정나면 Box``<T>``와 매개변수 (T t)가 결정



<img width="452" alt="image-20220629001622525" src="https://user-images.githubusercontent.com/101630615/176221497-6b2c60db-00be-42e8-b89c-e08cf3d3f218.png">



<img width="452" alt="image-20220629001823161" src="https://user-images.githubusercontent.com/101630615/176221501-f6afe465-2671-4442-8b4f-bc00a84bcd93.png">

#### 제네릭 메소드를 호출 방법

(1)	명시적으로 구체적 타입 지정

-	리턴타입 변수 = <구체적 타입>메소드명(매개값);

```java
Box<Integer> box = <Integer>boxing(100);
```



(2)	구체적 타입 생략. 매개값을 보고 구체적 타입을 추정 (더 많이 사용)

-	리턴타입 변수 = 메소드명(매개값);

```java
Box<Integer> box = boxing(100); 
```



#### 제네릭 타입의 상속과 구현

제네릭 타입을 부모 클래스로 사용할 경우
-	타입 파라미터는 자식 클래스에도 기술

```java
public class ChildProduct<T,M> extends Product<T,M< {...}

public class ChildProduct<T,M,C> extends Product<T,M< {...}
```

-	자식 클래스는 추가적인 타입 파라미터 가질 수 있음



#### 제네릭 인터페이스를 구현할 경우

-	제네릭 인터페이스를 구현한 클래스도 제네릭 타입

```java
public class StoageImpl<T> implements Storage<T> {...}
```