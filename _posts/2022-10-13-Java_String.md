# [Java] String



### 문자열을 다루는 클래스

- 문자열을 저장하고 관리하는 클래스
- String, StringBuffer, StringBuilder



### String vs StringBuffer / StringBuilder

- String은 불변의 속성을 가짐



사용 예제

```java
String str = "hello";   // String str = new String("hello");
str = str + " world";  // [ hello world ]
```

 위의 예제에서 "hello" 값을 가지고 있던 String 클래스의 참조변수 str이 가리키는 곳에 

저장된 "hello"에 "world" 문자열을 더해 "hello world"로 변경한 것으로 착각할 수 있다.



하지만 기존에 "hello" 값이 들어가있던 String 클래스의 참조변수 str이

 "hello world"라는 값을 가지고 있는 새로운 메모리영역을 가리키게 변경되고,

처음 선언했던 "hello"로 값이 할당되어 있던 메모리 영역은 

Garbage로 남아있다가 GC(garbage collection)에 의해 사라지게 된다. 

String 클래스는 불변하기 때문에 문자열을 수정하는 시점에 새로운 String 인스턴스가 생성된다.



![스크린샷 2022-10-11 오후 7 04 28](https://user-images.githubusercontent.com/101630615/195065362-bbb119ef-7fd4-440f-b1ac-9cf57450fc52.png)



그러나 **문자열 추가,수정,삭제 등의 연산이 빈번하게 발생**하는 알고리즘에 String 클래스를 사용하면 

**힙 메모리(Heap)에 많은 임시 가비지(Garbage)가 생성**되어 

힙메모리 부족으로 어플리케이션 성능에 치명적인 영향을 끼치게 된다.

이를 해결하기 위해  **가변(mutable)성**을 가지는 **StringBuffer** / **StringBuilder** 클래스는 가변성 가지기 때문에

 .append() .delete() 등의 API를 이용하여 **동일 객체내에서 문자열을 변경**하는 것이 가능하다. 



```java
StringBuffer sb= new StringBuffer("hello");
sb.append(" world");
```



![스크린샷 2022-10-11 오후 7 07 07](https://user-images.githubusercontent.com/101630615/195065369-5d49e121-9c11-4548-af8f-bd0bffa690fd.png)





### StringBuffer와 StringBuilder의 차이점

StringBuffer와 StringBuilder클래스는 둘 다 크기가 유연하게 변하는 가변적인 특성을 가지고 있으며 제공하는 메서드도 같고 

사용하는 방법도 동일하지만 두 클래스는 동기화 지원의 유무가 다르다.

StringBuffer는 각 메소드 별로 synchronized keyword가 존재하여 멀티 스레드 상태에서 동기화를 지원하고 

StringBuilder는 단일 스레드 환경에서만 사용하도록 설계되어 있다. 

StringBuilder가 StringBuffer보다 속도는 더 빠르지만, 언제 멀티스레드 환경에서 돌아가는지 알지 못하기에 

안정적인 StringBuffer로 통일하여 코딩하는것이 좋다.



## 정리





![스크린샷 2022-10-11 오후 7 07 48](https://user-images.githubusercontent.com/101630615/195065374-1d28be40-dd42-492f-95f5-47baaf8cf537.png)

#### String

- 불변성을 갖는 문자열 클래스
- 한 번 값을 할당되면 할당된 메모리는 변하지 않음 



#### StringBuffer

- 동기화를 지원하여 멀티 스레드 환경에서도 안전하게 동작 



#### StringBuilder

- 동기화를 지원하지 않음 



 String은 불변성을 가지기 때문에 **변하지 않는 문자열을 자주 읽어들이는 경우 String을 사용**하고 

**문자열의 추가,수정,삭제가 빈번하게 발생할 경우**, String 클래스가 아닌 **StringBuffer/StringBuilder를 사용**한다.



[출처] : [https://ifuwanna.tistory.com/221](https://ifuwanna.tistory.com/221),  [https://coding-factory.tistory.com/546](https://coding-factory.tistory.com/546)

