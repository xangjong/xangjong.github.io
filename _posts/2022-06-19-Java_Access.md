# [Java] 접근 제한자



### 접근 제한자

-	클래스, 멤버 필드, 메소드의 접근을 제어하기 위해 사용
-	클래스 내부의 정보 은폐 (정보 은닉 가능)
-	접근 제한 대상에 따라
-	클래스 접근 제한
-	클래스 멤버 접근 제한 : 필드, 메소드

<img width="600" alt="image-20220619032824576" src="https://user-images.githubusercontent.com/101630615/174451941-49a1b5c3-b40c-4915-8865-7cf12a2e9994.png">

#### ``public``

-	공용 멤버임을 표시하는 키워드 (완전 공개)
-	패키지 상관없이 모든 클래스 외부에서 이 클래스의 멤버에 접근하여 사용하는 것을 허용

#### ``private``

-	전용 멤버 (비공개)
-	클래스 내의 멤버 메소드만 접근 가능
-	클래스에서 외부에서 접근 불가

#### ``protected``

-	보호 멤버 (보호된 일부 공개)
-	허용 범위
-	같은 패키지 내의 모든 클래스에서 접근 가능
-	패키지 상관없이 상속받은 서브 클래스에서 접근 가능

***상속의 경우***

-	public과 default의 중간 정도에 해당
-	같은 패키지에서는 default 처럼 접근 제한이 없지만
-	다른 패키지에서는 상속 받은 자식 클래스만 접근 허용

#### ``디폴트(default)`` : 접근 제한자 생략

-	같은 패키지 내의 모든 클래스에서 접근 가능
-	다른 패키지에 있는 클래스에서 접근 불가능

<img width="500" alt="image-20220619032856365" src="https://user-images.githubusercontent.com/101630615/174451945-f2db1b0b-7512-46c8-b02f-40f86a14c8d9.png">

같은 클래스 내의 멤버는 ``public / private / protected / 디폴트(default)`` 상관 없이 모두 사용 가능



<img width="600" alt="image-20220619032917591" src="https://user-images.githubusercontent.com/101630615/174451947-a8488d0a-53ed-4123-9d9b-179d90a813fa.png">



#### 생성자의 접근 제한

-	클래스 멤버 접근 제한과 동일
-	단, 클래스가 default이면 생성자가 public이라도 같은 패키지에서만 생성자 호출 가능
-	자동으로 추가되는 기본 생성자는 클래스의 접근 제한과 동일
-	클래스가 public 이면 생성자도 public
-	클래스가 default 이면 생성자도 default

<img width="700" alt="image-20220619032947141" src="https://user-images.githubusercontent.com/101630615/174451950-3c645056-2d0e-4b42-b174-82b677de4afd.png">