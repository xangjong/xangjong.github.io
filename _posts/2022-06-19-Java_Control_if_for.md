

# [Java] 조건문과 반복문



### 코드 실행 흐름 제어

일반적인 코드 실행 흐름

-	main() 메소드의 시작인 중괄호 { 에서 끝 중괄호 } 까지 **위 -> 아래** 방향으로 실행


제어문
-	프로그램의 흐름을 제어
-	코드 실행 흐름을 개발자가 원하는 방향으로 변경할 수 있도록 도와줌

### 제어문의 종류

<img width="400" alt="image-20220618220138100" src="https://user-images.githubusercontent.com/101630615/174440009-5b3ee2d0-6702-42de-8fbf-d860cab46216.png">



<hr>



### 조건문 (선택문)

#### ``if`` 문

```
if (조건식){
	조건식의 결과가 true일 때 수행되는 문장;
}
```



#### ``if ~ else ~`` 문

```
if (조건식){
	조건식의 결과가 true일 때 수행되는 문장;
} else { 
	false일 때 수행되는 문장
}
```



#### 다중 ``if ~ else if ~ else ~``

-	if문 블록 내에 또다른 if문 포함

```
if (조건식){
	조건식의 결과가 true일 때 수행되는 문장;
} else if(조건식2){
	조건식 1의 결과가 false이면서 
	조건식 2의 결과가 true일 때 수행되는 문장
} else { 
	조건식 1, 2 모두 false일 때 수행되는 문장
}
```

***주의!***

``else if`` 문 보다 ``else`` 문이 앞에 오면 오류 



#### 중첩 ``if`` 문

``` 
if(조건식){
		if(조건식2){
			
		} else {
		
		}
} else {

}
```



#### ``switch`` 문

-	변수 또는 연산식의 값에 따라 실행문 선택할 때 사용

```
switch (값 또는 수식){
	case value1 : 처리할 문장-1; break;
	case value1 : 처리할 문장-1; break;
	case value1 : 처리할 문장-1; break;
	
	default : 처리할 문장-n break;
}

```

***주의!!!***

-	수식으로 값의 결과가 정수 또는 문자열 또는 문자 값이어야 함 (실수 사용 불가)
-	``case``  뒤의 ``value``는 반드시 하나의 값만 사용
-	10 < a <= 100 (범위 사용 불가)
-	case 다음에는``콜론(:)`` 사용 
-	case 띄고 value :   (case 다음에 띄어 쓰기 해야 함)
-	``break`` 문이 없는 경우 해당 case에서 실행이 멈추지 않고 다음 case까지 수행됨

 <hr>

### 반복문

-	중괄호{} 블록 내용을 반복적으로 실행할 때 사용



#### ``for`` 문

-	반복 횟수를 알고 있을 때 주로 사용
-	반복 횟수 지정

```
for (초기식; 조건식; 증감식){
	반복 수행되는 문장(조건식의 결과가 true일 때 수행)
}
```

<img width="404" alt="image-20220618221440313" src="https://user-images.githubusercontent.com/101630615/174440011-566edb53-dacf-47f2-821d-98dbf8c49627.png">





<img width="452" alt="image-20220618221545860" src="https://user-images.githubusercontent.com/101630615/174440012-9ea2a16e-14b7-4740-a85c-5e9677691adc.png">

***주의!!***

-	sum 변수 사용 시 반드시 값을 0으로 초기화하고 사용
-	초기화 하지 않으면 오류 발생
-	오류 발생 이유 : sum = sum + i;
-	sum 값에 i를 더해서 다시 sum에 저장하는데 처음에 sum에 값이 없으므로 연산을 수행할 수 없음
-	초기화 되어 있지 않으면 컴파일 시 오류로 처리



#### ``for`` 무한 루프

-	for(;;) : 무한반복
-	주의! : 반복문을 종료할 수 값 필요
-	for 문 전에 반복문을 종료시키기 위한 변수 필요
-	for 문 안에서 종료되기 위한 조건 필요

```
public class ForLoop {

	public static void main(String[] args) {
		// for 무한 루프

		int count = 0;

		for (;;) {
			count++;
			System.out.println(count);

			if (count >= 5)
				break; // 반복문 종료 조건 : 조건에 해당되면 반복문 종료
		}

	}

}
```



### ``while`` 문

-	반복 횟수를 모를 때 사용 
-	조건에 따라 반복을 계속할지 결정할 때 사용
-	조건식이 true일 경우 계속해서 반복
-	(for 문은 정해진 횟수만큼 반복)

```
(초기값)
while(조건식) {
	조건식의 결과가 true일 때 
	반복 수행되는 문장
	증감
} 다음 문장
```

<img width="452" alt="image-20220618222017532" src="https://user-images.githubusercontent.com/101630615/174440015-6fe68de7-7009-48fa-9973-e90f8b6ac9eb.png">

***while 문 주의!!!***

(1)	**초기값**이 없으면 조건을 알 수 없고
(2)	**증감식** 없으면 반복문을 빠져 나올 수 없어서 무한 반복

-	i가 증가하지 않으면 계속 10이하로 
-	조건이 계속 true 상태 : 계속 반복


#### ``while`` 무한 루프

-	조건이 무조건 true 
-	``if`` 문과 ``break`` 와 함께 사용

```
while(true){
	종료 조건 break; 
	종료되기 위한 증감 
}

public class WhileLoop {

	public static void main(String[] args) {
		int i=0;
		
		while(true) {
			i++;
			System.out.println(i);
			if(i>=3) break;
		}

	}

}
```



#### ``do ~while``문

-	조건에 따라 반복을 계속할지 결정할 때 사용하며 최소 한 번은 수행됨
-	먼저 무조건 중괄호{ } 블록을 한 번 실행 한 후, 조건을 검사해서 반복 결정

<img width="452" alt="image-20220618222514478" src="https://user-images.githubusercontent.com/101630615/174440016-11ef5fba-e673-409a-b5b7-b8f5961db7fa.png">



<hr>



### 기타 제어문 

#### ``break`` 문

-	반복문 하나를 완전히 빠져 나갈 때 사용
-	for 문, while 문, do~while 문 종료 (반복 취소)
-	``switch`` 문 종료 시 사용
-	주로 ``if`` 문과 같이 사용, if 문 조건식에 따라 반복문 종료

```
public class Break {

	public static void main(String[] args) {
		// 중첩된 반복문에서 break문 사용
		// 대문자 -> 소문자
		Outter : for (char upper = 'A'; upper <= 'Z'; upper++) { // 대문자 A-Z
			for (char lower = 'a'; lower <= 'z'; lower++) {
				System.out.println(upper + "-" + lower);

				// 소문자 g인 경우 프로그램 중단
				if (lower == 'g')
					break Outter;
				
				//바깥 for문 중단 : 이름을 Outter로 붙이고 break Outer; 해서 중단
			}

		}
		System.out.println("프로그램 실행 종료");
	}

}

```

***주의!!***

-	반복문이 중첩되어 있는 경우
-	자신이 속한 가장 가까운 하나의 반복문만 벗어남
-	바깥쪽 반복문까지 종료시키려면 반복문에 이름(라벨)을 붙이고 ``“break 이름;”`` 사용



#### ``continue`` 문

-	수행 중인 문장은 중단하고, 다음 반복 계속 수행
-	반복문은 종료하지 않고 계속 반복 수행

```
public class Continue {

	public static void main(String[] args) {
		// Continue
		//홀수인 경우 다음 문장 건너뛰고 다음 번에 계속 
		for (int i = 1; i <= 10; i++) {
			if (i % 2 != 0) {
				continue;
			}
			System.out.println(i);
		}
	}

}

```