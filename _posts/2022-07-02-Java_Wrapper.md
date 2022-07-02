



# [Java] 박싱 & 언박싱



### Wrapper 클래스 (포장 클래스)

- 기본 타입에 대응되는 클래스



<img width="600" alt="image-20220702161919477" src="https://user-images.githubusercontent.com/101630615/176991188-46dd88a2-5fa8-48bf-96bd-4eb5baf71a8f.png">



#### Wrapper 객체

-	기본타입(byte, char, short, int, long, float, double, boolean) 값을 내부에 두고 포장하는 객체
-	기본 타입의 값은 외부에서 변경
  

### 박싱(Boxing)과 언박싱(Unboxing)
#### 박싱(Boxing)

-	기본 타입의 값을 Wrapper 객체(포장 객체)로 만드는 과정

- 기본 타입 (int) : 100

- Wrapper 클래스 : Integer

- ``Integer obj1 = new Integer(100);``

  

#### 언박싱(Unboxing)

-	포장 객체에서 기본 타입의 값을 얻어 내는 과정
-	``int value = obj.intValue();``





### 박싱(Boxing) 하는 방법
#### (1)	생성자 이용

<img width="700" alt="image-20220702161925775" src="https://user-images.githubusercontent.com/101630615/176991190-f0abc903-e49e-4c60-a864-b77c174c0609.png">



#### (2) valueOf() 메소드 이용

```java
Integer obj = Integer.valueOf(1000);
Integer obj = Integer.valueOf(“1000”);
```



#### 언박싱 코드

-	각 포장 클래스마다 가지고 있는 클래스 호출
-	기본타입명+Value()



<img width="400" alt="image-20220702161932357" src="https://user-images.githubusercontent.com/101630615/176991192-50f13ac7-7cd2-4129-b8a3-1f72f7e64be2.png">



#### 자동 박싱과 언방식

-	자동 박싱 
  -	포장 클래스 타입에 기본값이 대입될 경우 발생
  -	``Integer obj = 100;`` // 자동 박싱

-	자동 언박싱
  -	기본 타입에 포장 객체가 대입될 경우 발생 


<img width="350" alt="image-20220702161939394" src="https://user-images.githubusercontent.com/101630615/176991194-4f6cce38-30e5-47a1-a49a-dfc4b68aacc6.png">



#### 숫자 문자열을 기본 타입 값으로 변환

-	parse + 기본타입명() : 정적 메소드
-	``int num = Integer.parseInt(“1000”);``



#### 포장값 비교

-	포장 객체는 내부 값을 비교하기 위해 ==와 != 연산자 사용 불가
-	값을 언박싱 비교하거나, equals() 메소드로 내부값 비교