# [Java] 배열



### 배열이란?

-	같은 타입의 데이터를 연속된 공간에 저장하는 자료구조
-	크기와 데이터 타입이 같으며 동일한 이름을 갖는 원소들의 연속적 저장 영역
-	배열의 원소는 메모리 내에서 순서대로 저장
-	각 배열의 원소는 인덱스([0]부터 시작)로 구별

<img width="292" alt="image-20220618224733494" src="https://user-images.githubusercontent.com/101630615/174442407-f62ccaae-7a53-4bff-afbf-c737c271395d.png">

### 배열 이름

-	배열의 저장 위치를 가리키는 참조(레퍼런스) 변수
-	즉, 배열이 저장된 곳의 시작 주소 번지를 갖고 있음
-	따라서 배열은 기본 타입이 아닌 참조 타입(레퍼런스 타입)

<img width="500" alt="image-20220618224741175" src="https://user-images.githubusercontent.com/101630615/174442411-e017e523-0a0b-45b5-aad8-d1cacbf5f106.png">

### 배열을 사용하는 이유

-	같은 타입의 변수 사용 시 변수 선언 개수를 줄일 수 있음
-	``int num1, num2, ……, ,num100;``
-	``int[] num = new int[100];``
-	반복문(``for``문)을 활용하여 프로그램을 간단히 작성할 수 있기 때문

<img width="452" alt="image-20220618224755986" src="https://user-images.githubusercontent.com/101630615/174442412-bcc6fded-637a-4edf-9983-6fd62b56b18b.png">

### 배열 선언 형식 (2가지)
(1) 데이터 타입[ ] 변수;

```
int[] num;
double[] average;
String[] name;
```


(2) 데이터 타입 변수[ ];

```
int num[];
double average[];
String name[];
```

***주의!!!!***

-	배열은 선언 후 메모리 공간을 할당 받아야만 사용할 수 있음
-	참조 변수만 선언하면 사용할 수 없음
-	``int[] num;``  아직 사용할 수 없음



#### 배열의 메모리 공간 할당

new 키워드를 사용하여 메모리 공간 할당

```
int[] a = new int[5]; // 선언과 동시에 할당
int[] b; // 선언만 (아직 사용할 수 없음)
b = new int[5]; // 메모리 할당
```




#### 배열의 초기값

-	메모리를 할당 받을 때 자료형의 기본값으로 초기화
-	숫자 : 0 (정수), 0.0 (실수)
-	boolean : false
-	참조 타입 : null

```
int[] a = new int[5]; // 초기값 : 0

double[] a = new double[5]; // 초기값 : 0.0

boolean[] b = new boolean[5]; // 초기값 : false

String[] s = new String[5]; // 초기값 : null
```

<img width="600" alt="image-20220618225305869" src="https://user-images.githubusercontent.com/101630615/174442413-a63727b8-eb56-45df-8782-184e194ea159.png">





#### 배열의 초기화 리스트

-	배열을 선언할 때 값을 바로 할당
-	선언 + 기억 장소 할당 + 원소에 값 저장을 한 번에 수행

<img width="700" alt="image-20220618225629503" src="https://user-images.githubusercontent.com/101630615/174442416-cb54464d-0fbc-4cd3-af1e-35450e255239.png">

***주의!!***


-	배열의 전체 원소에 값을 저장하거나 출력하기 위해서는 반복문 사용
-	배열은 크기가 정해져 있기 때문에 반복 횟수를 정할 수 있으므로 for 문 사용
-	반복문 시작은 반드시 0부터 (첨자가 [0]부터 시작하므로) 시작



#### 배열의 길이

-	배열에 저장할 수 있는 전체 항목의 수 (배열 크기)
-	배열명.length
-	배열의 길이는 for문의 조건식에서 주로 사용

```
for(int i =0; i <num.length; i++) {}
```



#### 다차원 배열

-	2차원 이상의 배열 형식

```
int [][] 변수명 = new int[][];
```

-	선언과 동시에 할당
-	2차원 배열 예
-	``int[ ][ ] a = new int[3][4]``;  행3개, 열4개

<img width="600" alt="image-20220618225844673" src="https://user-images.githubusercontent.com/101630615/174442417-3c134c71-0651-4258-82d5-1f752e67f1d4.png">



**2차원 배열의 초기화**

-	배열을 선언할 때 값을 바로 저장
-	선언 + 기억 장소 할당 + 원소에 값 저장을 한 번에 수행



**2차원 배열의 크기**

-	배열의 크기 (원소의 개수) : length 속성

```
byte[ ][ ]  a = new byte[3][2];

a.length : 행의 개수 (3)

a[0].length : 0행의 열의 개수 (2)
a[1].length : 1행의 열의 개수 (2)
a[2].length : 2행의 열의 개수 (2)
```

<img width="300" alt="image-20220618230034641" src="https://user-images.githubusercontent.com/101630615/174442418-a859cdf5-e324-4b1e-be95-fa8528dd76e4.png">



#### 비정방형 배열

-	각 행마다 열의 개수가 다른 배열
-	즉, 메모리 할당 시 열의 개수를 정하지 않고
-	동적으로 열의 개수 할당

```
int[ ][ ] a = new int[4][ ]; // 열의 개수 정하지 않음
a[0] = new int[1]; // 0행에 1개의 원소 생성
a[1] = new int[2]; // 1행에 2개의 원소 생성
a[2] = new int[2]; // 2행에 2개의 원소 생성
a[3] = new int[4]; // 3행에 4개의 원소 생성
```

<img width="300" alt="image-20220618230230345" src="https://user-images.githubusercontent.com/101630615/174442419-1e2412bf-cb24-4601-a5ac-0ae7d2a5c94f.png">



**비정방형 배열 초기화**

-	각 행마다 열의 개수를 다르게 값 설정
-	``int[][] a = {{1}, {2, 3}, {4, 5, 6}};``

**주의!!** - 배열의 index 범위를 벗어날 때 : ``ArrayIndexOutOfBoundsException``오류 발생



### 배열 복사

-	배열은 한 번 생성하면 크기 변경 불가
-	더 많은 저장 공간이 필요하면 더 큰 배열을 새로 만들고 이전 배열로부터 항목 값들을 복사
배열 복사 방법
(1)	``for``문 사용해서 각 원소의 값을 하나씩 복사
(2)	``System.arrayCopy()`` 메소드 이용

```
System.arrayCopy(원본배열, 시작인덱스, 대상배열, 시작인덱스, 복사할 항목 개수);
```



#### 향상된 for 문

-	배열 및 컬렉션의 항목 요소를 순차적으로 처리
-	인덱스 이용하지 않고 바로 항목 요소 반복
-	``for( 변수 : 배열 ){ … }; ``
-	변수에 배열 항목 하나씩 저장해서 사용
-	배열의 원소의 개수만큼 반복 수행

<img width="600" alt="image-20220618230403390" src="https://user-images.githubusercontent.com/101630615/174442421-55ddba5b-9732-4ffb-a880-5959908f3700.png">



# 객체 배열

하나의 배열로 객체 관리

 객체 배열 : 객체를 가리키기 위한 레퍼런스 배열

-	객체를 가리키는 레퍼런스를 원소로 갖는 배열

-	``Person[] p = new Person[5]; ``   // 레퍼런스(참조 변수) 5개 생성

<img width="350" alt="image-20220619025338437" src="https://user-images.githubusercontent.com/101630615/174450741-5c7e7731-4dd6-4e39-b47a-63476035c513.png">

-	``p[i] = new Person();``  // 객체 생성
-	객체 생성되고 레퍼런스 배열의 각 원소가 객체를 가리킴

<img width="400" alt="image-20220619025350611" src="https://user-images.githubusercontent.com/101630615/174450742-6ab24ac1-9958-4e15-989b-178dbbfc5364.png">

p : 레퍼런스 배열을 가리키는 참조 변수
p[i] : 객체를 가리키는 참조 변수

<img width="500" alt="image-20220619030650887" src="https://user-images.githubusercontent.com/101630615/174451165-fd37a911-3a50-4393-a592-11f675b29cb5.png">

