

# [Java] 멀티 스레드 



### 멀티 스레드 개념

-	멀티 프로세스
  -	독립적으로 프로그램들을 실행하고 여러 가지 작업 처리

-	멀티 스레드
  -	한 개의 프로그램을 실행하고 내부적으로 여러 가지 작업 처리


<img width="600" alt="image-20220702140928015" src="https://user-images.githubusercontent.com/101630615/176987976-198a9df0-e8e6-49df-9b78-50a2e3fd3a8c.png">



#### 메인(main) 스레드

-	모든 자바 프로그램은 메인 스레드가 main() 메소드 실행하며 시작
-	main() 메소드의 첫 코드부터 아래로 순차적으로 실행
-	실행 조건
  -	마지막 코드 실행
  -	return 문을 만나면 종료

-	main 스레드는 작업 스레드들을 만들어 병렬로 코드를 실행
  -	멀티 스레드 생성해 멀티 태스킹 수행




#### 스레드 종료

**싱글 스레드**

- 메인 스레드가 종료되면 프로세스도 종료

**멀티 스레드**

-	실행 중인 스레드가 하나라도 있으면 프로세스 미 종료



**멀티 스레드로 실행하는 어플리케이션 개발**

-	몇 개의 작업을 병렬로 실행할지 결정하는 것이 선행되어야 함



<img width="500" alt="image-20220702141101053" src="https://user-images.githubusercontent.com/101630615/176987979-cf3e6d49-6b6e-47d7-9c3f-8d9512cea60a.png">





### 작업 스레드 생성과 실행

#### (1) Thread 클래스로부터 직접 생성

-	Runnable 인터페이스 사용 (구현)
-	Runnable 인터페이스를 매개값으로 갖는 생성자 호출

```java
Thread thread = new Thread(Runnable target);
```



<img width="323" alt="image-20220702141727502" src="https://user-images.githubusercontent.com/101630615/176987980-ed618a72-a902-42fb-aad3-a4f499e72ebf.png">



#### Runnable 인터페이스

-	run() 메소드 하나만 정의되어 있음
-	Runnable은 작업 내용을 가지고 있는 객체이지 실제 스레드 아님
-	Runnable 구현 생성한 후
-	이것을 매개값으로 해서 Thread 생성자를 호출하면 비로소 작업 스레드 생성

<img width="350" alt="image-20220702141828529" src="https://user-images.githubusercontent.com/101630615/176987981-8dab6a3e-b1ec-4a3e-937d-ecfbbc15190b.png">



코드 절약하기 위해 Thread 생성자를 호출할 때 Runnable 익명 객체를 매개값으로 사용 가능

<img width="451" alt="image-20220702141838836" src="https://user-images.githubusercontent.com/101630615/176987982-37dec25d-97bb-4957-a062-3acdba892dfa.png">



**작업 스레드는 생성되는 즉시 실행되는 것이 아니라 start() 메소드를 호출해야만 실행**

-	``thread.start()``
-	start() 메소드가 호출되면 작업 스레드는 매개값으로 받은 Runnable run() 메소드를 실행하면서 자신의 작업을 처리



<img width="451" alt="image-20220702141928406" src="https://user-images.githubusercontent.com/101630615/176987983-a8c2ab31-c846-41b6-b0b7-f6b7697a5e41.png">





#### (2) Thread 하위 클래스로부터 생성

-	Thread 클래스 상속
-	Thread 클래스 상속 수 run 메소드 재정의해서 스레드가 실행할 코드 작성

```java
public class WorkerThread extends Thread
```



<img width="400" alt="image-20220702141948964" src="https://user-images.githubusercontent.com/101630615/176987985-73aaa8a7-e01a-4eda-b3b2-8db03fe65ced.png">





### 스레드 우선 순위

#### 동시성

-	멀티 작업을 위해 하나의 코어에서 멀티 스레드가 번갈아 가며 실행하는 성질

#### 병렬성

-	멀티 작업을 위해 멀티 코어에서 개별 스레드를 동시에 실행하는 성질

#### 코어

-	CPU 칩에서 물리적으로 연산하는 유닛 개수
-	입력된 명령어를 계산하고 해석하는 단위



<img width="600" alt="image-20220702142218497" src="https://user-images.githubusercontent.com/101630615/176987988-4fa87163-1efd-48aa-80ea-0e6454d02b15.png">





### 스레드 스케줄링

-	스레드의 개수가 코어의 수보다 많을 경우
-	스레드를 어떤 순서로 동시성으로 실행할 것인가 결정 -> 스레드 스케줄링
-	스케줄링에 의해 스레드들은 번갈아 가면  run() 메소드를 조금씩 실행



<img width="500" alt="image-20220702142233074" src="https://user-images.githubusercontent.com/101630615/176987989-abce8f52-9aad-4f13-98c3-69b1fa3a1cef.png">



#### (1)	우선 순위 방식 (코드로 제어 가능)

-	우선 순위가 높은 스레드가 실행 상태를 더 많이 가지도록 스케줄링

```java
thread.setPriority(Thread.MAX_PRIORITY);
thread.setPriority(Thread.MIN_PRIORITY);
```



#### (2)	순환 할당 방식 (코드로 제어할 수 없음)

-	시간 할당량(Time Slice)을 정해서 하나의 스레드를 정해진 시간만큼 실행



### 동기화 메소드와 동기화 블록

-	단 하나의 스레드만 실행할 수 있는 메소드 또는 블록
-	다른 스레드는 메소드 또는 블록이 실행이 끝날 때까지 대기
-	동기화 메소드 : synchronized 키워드 붙임
-	잠금(lock) 의미

<img width="336" alt="image-20220702142501314" src="https://user-images.githubusercontent.com/101630615/176987992-c9ad0326-f73c-4d8b-80ca-b48e0cb9c965.png">

-	synchronized 키워드
  -	인스턴스 메소드와 정적 메소드 다 붙일 수 있음



#### 임계 영역 (critical section)

-	멀티 프로그램에서 단 하나의 스레드만 실행할 수 있는 코드 영역
-	자바에서는 임계 영역을 지정하기 위해 동기화 메소드와 동기화 블록 제공
-	스레드가 객체 내부의 동기화 메소드 또는 블록에 들어가면
-	즉시 객체에 잠금을 걸어 다른 스레드가 임계 영역 코드를 실행하지 못하게 함

#### 동기화 블록



<img width="355" alt="image-20220702142722141" src="https://user-images.githubusercontent.com/101630615/176987993-28334f01-6cdd-48f7-8934-6dac8f4771cf.png">







<img width="451" alt="image-20220702142727308" src="https://user-images.githubusercontent.com/101630615/176987994-39ade644-6589-4ac0-8576-571f0918b681.png">



 

<img width="500" alt="image-20220702142741551" src="https://user-images.githubusercontent.com/101630615/176987995-e1cf3409-845e-43a4-aa59-0a64cd3145b7.png">



***공유 객체를 사용할 때 주의할 점***

-	멀티 스레드가 하나의 객체를 공유해서 생기는 오류



<img width="500" alt="image-20220702142400792" src="https://user-images.githubusercontent.com/101630615/176988168-67f7e43a-78ed-4a60-83b3-f089af31c5df.png">



### 스레드 상태

#### 스레드의 일반적인 상태



<img width="500" alt="image-20220702142827356" src="https://user-images.githubusercontent.com/101630615/176987996-b3fd9c6b-5f28-4437-a406-523d8393d090.png">





#### 스레드 클래스에서는 스레드의 상태를 나타내는 열거 상수



<img width="600" alt="image-20220702142925205" src="https://user-images.githubusercontent.com/101630615/176987998-94753185-be95-4ee8-8e41-fc727418f148.png">



#### 실행 상태에서 정지 상태로 갈 수 있는 3가지 상태

-	실행 상태에서 실행 대기 상태로 가지 않고
-	일시 정지 상태로 가기도 함



<img width="400" alt="image-20220702143002624" src="https://user-images.githubusercontent.com/101630615/176987999-148330e6-65c8-4e1b-b65f-05f1475e042a.png">

#### (1) BLOCKED

- 사용하고자 하는 객체의 락이 풀릴 때까지 기다리는 상태

- 동기화 메소드와 동기화 블록에서

  -	한 스레드가 동기화 메소드를 호출하고 있다면 다른 스레드는 이 동기화 메소드 호출 불가 (이때 다른 스레드는 BLOCKED 상태)

- 동기화 메소드를 다 실행하고 난 후 다른 스레드가 BLOCKED 상태가 해제되면서 실행 대기 상태로 되고, 

- 다시 실행 상태가 되어 동기화 메소드를 호출할 

  

#### (2) WAITING 상태

- 다른 스레드가 통지할 때까지 기다리는 상태

- 실행 중에 Object가 가지고 있는 wait() 메소드를 호출하게 되면 스레드는 일시 정지 상태로 가고

- WAITING된 스레드는 다른 스레드가 notify() 메소드를 호출해야만 실행 대기 상태로 가게 됨

- WAITING 된 스레드는 자기 스스로 또는 자동으로 실행 대기 상태로 갈 수 없고 다른 스레드가 통지를 해줘야만 실행 대기로 갈 수 있음

- (다른 스레드가 알려 줘야만 실행 대기 상태로 갈 수 있는 상태)

  

#### (3) TIMED_WAITING 상태

-	주어진 시간 동안 기다리는 상태
-	sleep(시간) : 주어진 시간 동안 일시 정지 상태
-	주어진 시간이 지나면 자동적으로 실행 대기 상태로 감



#### TERMINATED 상태 (종료)

-	실행을 마친 상태
-	스레드는 한 번 생성되고 종료되면 더 이상 재사용 불가
-	스레드를 재 실행하려면 항상 새로 생성해서 start() 메소드를 호출하여 실행 대기 상태(RUNNABLE)로 만들어 줘야 함



### 스레드 상태 제어

-	실행 중인 스레드의 상태를 변경하는 것
-	메소드를 사용하여 상태 변화시킴
-	상태 변화를 가져오는 메소드의 종류



<img width="600" alt="image-20220702143207565" src="https://user-images.githubusercontent.com/101630615/176988000-b720b794-8b4d-4c86-baf7-7ecb90b17673.png">



### 실행 상태에서 호출 가능한 메소드

##### ``yield()``

-	실행 중인 스레드를 실행 대기 상태로 변경
-	스레드1이 실행 중일 때 스레드1에서 yield() 호출하면 스레드1은 대기 상태로 변경되고
-	스레드1과 동일하거나 높은 우선 순위를 갖는 다른 스레드가 실행 가능
-	무의미한 반복 작업을 수행하는 중에 다른 스레드에게 양보할 때 주로 사용



<img width="400" alt="image-20220702143252608" src="https://user-images.githubusercontent.com/101630615/176988001-03a4a9d8-f1a6-45d7-832f-4b5b5a3389bd.png">



##### ``join()``

-	실행 중인 스레드가 일시 정지했다가 join()을 호출한 스레드가 종료되면 실행 대기 상태로 변경
-	실행 중 잠깐 멈추고 기다렸다가 결과 받아서 다시 시작
-	계산 작업을 하는 스레드가 모든 계산 작업을 마쳤을 때, 결과 값을 받아 이용하는 경우 주로 사용

