

# [Java] 클래스와 메소드



### 클래스 이름 

<img width="500" alt="image-20220619010719264" src="https://user-images.githubusercontent.com/101630615/174447475-95497e2b-8ca1-498b-af4d-e5bc2144f775.png">

#### 클레스 선언과 컴파일

- 소스 파일 생성 : 클래스 이름.java

<img width="452" alt="image-20220619010801923" src="https://user-images.githubusercontent.com/101630615/174447478-810c13f4-928f-4ea1-ad3a-a247e9147167.png">



<img width="500" alt="image-20220619010806151" src="https://user-images.githubusercontent.com/101630615/174447479-0b1f4982-886b-44f4-82e4-5a2313394a48.png">



#### 클래스 구성 : 필드 + 메소드

<img width="500" alt="image-20220619010834929" src="https://user-images.githubusercontent.com/101630615/174447480-994179ba-ad40-4e05-9792-51b2329150be.png">

#### 객체 생성과 참조 변수

-	객체를 생성하기 전에 객체를 가리킬 참조 변수 필요
-	참조 변수 : 객체를 참조하는(가리키는) 변수

```
Car c;	: Car 클래스의 참조 변수 c 선언, 아직 객체 생성되지 않았음
c = new Car(); : Car 타입의 메모리 공간 확보

Car c = new Car();  : 참조 변수 선언과 동시에 객체 생성
: 반드시 new 연산자를 사용하여 객체 생성
```

<img width="500" alt="image-20220619011036299" src="https://user-images.githubusercontent.com/101630615/174447484-80839362-2c62-4d21-8c8f-b2828f65134d.png">

<img width="700" alt="image-20220619011042227" src="https://user-images.githubusercontent.com/101630615/174447485-1f293558-dbfc-4f96-a70b-a74e65a0f2d5.png">

#### 객체 멤버에 접근

-	생성된 객체에 접근하여 사용
-	형식 ``참조변수(객체).멤버``

```
Car c = new Car();

c.carName;     
: 객체.멤버필드

c.showCarInfo(); 
: 객체.멤버메소드()
```



<hr>

### 메소드 (method)

-	객체의 동작(기능, 업무처리)
-	클래스 내에서 작업을 처리하는 단위
-	독립적인 모듈 : {   }
-	특정 기능을 수행하고 결과를 반환하는 독립적인 코드 집합
-	메소드에는 괄호를 붙임 : 메소드명()
-	main()은 프로그램이 실행되면 맨 처음에 수행되는 메소드
-	클래스 내에서 작업을 분리하여 여러 메소드가 처리 (분업)

<img width="321" alt="image-20220619011409489" src="https://user-images.githubusercontent.com/101630615/174447487-04c63235-e592-4d2b-b5c2-9b7358149dfd.png">

-	여러 개의 메소드로 나누어서 작업 시 이점
-	프로그램 재사용 (경제성)
-	필요한 곳에서 여러 번 호출하여 사용
-	상속 시 부모 클래스의 메소드와 멤버 필드 재사용
-	코드 작성 비용 단축 및 시스템 안정성 보장
-	main() 메소드는 클래스의 실행만 담당
-	다른 작업들은 다른 메소드를 만들어 처리 (분업)

<img width="391" alt="image-20220619011431472" src="https://user-images.githubusercontent.com/101630615/174447488-7589de52-796b-4539-b304-1f18bff9cefe.png">



#### 메소드 선언(정의) 형식

-	메소드가 처리하는 작업을 정의하는 것
-	body { } 구현 포함

<img width="333" alt="image-20220619011445425" src="https://user-images.githubusercontent.com/101630615/174447489-6d2e4367-8f55-4c50-9b3f-a67b52f6bbca.png">

#### 접근 제어자

-	클래스 외부에서 메소드에 접근, 사용을 허용할지 제한할지를 정하기 위해 사용
-	public : 완전 허용
-	private : 완전 접근 금지
-	protected : 일부 허용 (상속 받은 클래스만 허용)

#### 반환형 (return 문)

-	메소드가 실행 후 결과값을 반환할 때 사용
-	반환값이 없는 경우 : void
-	이 경우에는 메소드 안에 return 문 없음
-	반환되는 값의 유형과 일치하게 반환형 사용

<img width="375" alt="image-20220619011636257" src="https://user-images.githubusercontent.com/101630615/174447491-a02e2728-bfe3-4f1a-9ac1-f7c5192815f0.png">

#### 메소드 호출

-	메소드 사용
-	메소드를 사용하기 위해서는 메소드가 필요한 곳에서 호출(메소드명을 써주면 됨)
-	호출하지 않으면 메소드는 아무 일도 하지 않음
-	메소드 내에서 다른 메소드 호출 가능

<img width="452" alt="image-20220619011642307" src="https://user-images.githubusercontent.com/101630615/174447493-280b52f1-ac92-4093-861a-1e7dc4bb82e5.png">