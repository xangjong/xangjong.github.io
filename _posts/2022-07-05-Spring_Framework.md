

# [Spring] 스프링 프레임워크



### 스프링 프레임워크 (Spring Framework)

- 엔터프라이즈 애플리케이션 구축을 위한 솔루션
- 자바 애플리케이션 개발을 위한 포괄적인 인프라 지원을 제공하는 자바 플랫폼
- 스프링에서 인프라를 처리하므로 개발자는 애플리케이션 개발에만 집중
- 모듈화되어 있어 필요한 부분만 사용 가능
- 국내에서는 자바 개발자들에게 표준 프레임워크



#### 스프링의 장점

- 생산성 우수
  - 엔터프라이즈 애플리케이션 구축을 위한 솔루션이지만
  - 가볍고 모듈화되어  있어서 필요한 부분만 사용 가능
  - POJO 클래스와 약간의 설정만으로도 개발이 가능하므로 개발 생산성을 높일 수 있음
  - 실제 스프링을 적용하면 적용하지 않은 코드의 ⅓ 정도의 코드만으로 개발 가능
- 품질 보증
  - 스프링 프레임워크는 이미 검증된 많은 아키텍처 또는 디자인 패턴을 적용하여 만들어졌기 때문에
  - 코드에 아키텍처를 구현하기 위한 코드나 디자인 패턴을 사용하기 위한 코드를 개발자가 만들 필요가 없음
  - 이는 개발에 일관성을 제공해 주고 소프트웨어의 품질을 보증
- 유지보수 용이
  - 스프링 프레임워크를 사용하여 작성된 애플리케이션들을 유지보수하는데 소용되는 인력과 시간을 줄일 수 있기 때문에
  - 여러 프레임워크 중에서 스프링 프레임워크가 업계 표준으로 자리잡음



#### EJB (Enterprise JavaBean)
- 규모가 커지고 복잡한 애플리케이션 제작을 위해 만들어진 기술
- 컴포넌트 기반
- extends, implements를 많이 사용해서 클래스 의존도가 높고, 복잡하고 제한이 많은 문제
- 별도로 종속되지 않고 간단한 자바 객체를 사용하자는 의도에서 나온 것이 POJO
- Java EE 등의 중량 프레임워크들을 사용하게 되면서 해당 프레임워크에 종속된 “무거운” 객체를 만들게 되는 것에 반발해서 사용하게 된 용어

#### POJO (Plain Old Java Object)
- 자바 언어 사양 외에 어떠한 제한에도 묶이지 않은 자바 객체
- 특정 환경과 규약에 종속되지 않아 필요에 따라 재사용될 수 있는 방식으로 설계된 객체
- 즉, 다른 클래스를 상속 받거나 인터페이스를 구현해야 하는 규칙이 없는 자바 클래스
- 미리 정의 클래스 확장 예:
  ``public class Test extends javax.serv…..{ }``

##### POJO 대표적인 예

- JavaBean
- 생성자와 Getter/Setters만 지닌 단순 자바 객체
- DTO / VO

##### 대표적인 POJO 기반 프레임워크

스프링 프레임워크

- POJO를 사용하는 장점과 EJB에서 제공하는 엔터프라이즈 서비스와 기술을 그대로 사용할 수 있도록 지원하는 프레임워크



#### <span style=color:blue>스프링 프레임 워크의 특징</span>

- <span style=color:red>POJO 기반 프레임워크</span>
  - 자바 객체의 라이프사이클을 스프링 컨테이너가 직접 관리하고 
  - 스프링 컨테이너로부터 필요한 객체를 얻어 옴
- <span style=color:red>DI (Dependency Injection) 지원</span>
  - 의존성 주입
  - 각 계층이나 서비스들 사이 또는 객체들 사이의 의존성이 존재할 경우에
  - 스프링 프레임워크가 서로 연결시켜 줌 (클래스 간 약한 결합 가능)
- <span style=color:red>AOP (Aspect Oriented Programming) 지원</span>
  - 관점 지향 프로그래밍
  - 트랜잭션 로깅, 보안 등 여러 모듈에서 공통적으로 지원하는 기능을 분리하여 사용 가능
  - 반복적인 코드를 줄이고 개발자가 비즈니스 로직에만 집중할 수 있도록 지원
- 뛰어난 확장성
  - 스프링 프레임워크의 소스는 모두 라이브러리로 분리되어 있어서 필요한 라이브러리만 가져다 사용하면 됨
- Model2 방식의 MVC Framework 지원
  - Model / View / Controller 
  - JSP MVC 때보다 코드가 간결



### 스프링 프레임워크의 핵심 기능
- 의존관계에 있는 객체를 생성 조립해 주는 기능
- <span style=color:red>DI (Dependency Injection) : 의존성 주입</span>
  - 객체 간의 의존성을 개발자가 설정하는 것이 아니라
  - 스프링 컨테이너가 주입시켜 주는 기능
  - 장점 : 객체를 쉽게 확장하고 재사용할 수 있음
- <span style=color:red>IoC (Inversion of Control) : 제어의 역전 </span>



#### <span style=color:blue>DI (Dependency Injection) : 의존성 주입</span>

- 객체 간의 의존성을 개발자가 설정하는 것이 아니라
- 스프링 컨테이너가 주입시켜 주는 기능
- 장점 : 객체를 쉽게 확장하고 재사용할 수 있음
- new 연산자를 통해 다른 클래스의 객체 생성 사용
- 외부에서 빈(객체)을 만들어 필요로 하는 곳에 전달해 주도록 하는 것
- 즉, 개발자가 new 연산자를 사용하여 직접 객체를 생성하지 않고
- 외부에서 생성된 bean(객체)을 IoC 컨테이너가 넣어 주는 방식 (주입 : injection)
- 일반적으로 부품(빈)을 조립(의존성 주입)해서 사용한다고 함

#### DI (의존성 주입) 방법을 사용하는 이유

-	의존하는 객체의 클래스가 변경되거나 다른 클래스의 객체를 사용하게 될 경우
-	의존 관계(결합 관계)에 있는 다른 모든 클래스들의 소스 코드도 변경해야 하는데
-	의존성 주입 방법을 사용하면, 클래스 결합 상태를 변경하거나 객체를 주입하는 부분만 수정하면 되므로
-	수정할 코드의 양을 줄일 수 있다는 장점



#### 스프링에서 의존성 주입 방법

-	XML을 이용한 방법
-	XML 설정 파일에 ``<bean>`` 설정
-	Annotation을 이용한 방법
-	자바 코드에서 ‘@어노테이션이름’으로 설정



#### 의존 관계



<img width="452" alt="image-20220701203541223" src="https://user-images.githubusercontent.com/101630615/176888864-ea24afd7-55f7-45a9-a3dc-a0a70c20dea1.png">





#### <span style=color:blue>IoC (Inversion of Control) : 제어의 역전 </span>

- 객체에 대한 제어권 문제
- 기존에는 개발자에게 제어권이 있었음
- new 연산자를 사용해서 객체 생성
- 스프링 프레임워크에서는 객체의 제어권이 스프링에 있고
- 인스턴스의 라이프 사이클(생성에서 소멸까지)을 개발자가 아닌 스프링 프레임워크에서 담당



#### (1) 스프링을 사용하지 않는 DI (DI를 사용하는 코드)

-	<span style=color:red>(1-1) 생성자 기반 DI</span>
  -	의존성 관계에 있는 객체를 new를 통해 직접 생성하지 않고
  -	생성자를 통해 외부에서 전달 (주입 : injection)



-	<span style=color:red>(1-2) Setter 기반 DI</span>
-	Setter 메소드를 이용하여 의존성 주입 수행




#### (2-1) XML을 이용한 DI - 스프링 DI

-	XML 파일에 빈(bean : 부품)을 정의(생성)하고
  -	``<bean id="이름" class="패키지명.클래스명">``

-	의존성 설정 (부품 조립)
  -	``<ref bean=”의존하는 빈”>``


-	XML을 이용해서 의존성을 주입하기 위해서는 클래스에 생성자 또는 Setter 메소드가 있어야 함
-	스프링은 Pre-loading 방식 사용
  -	ApplicationContext를 이용해서 컨테이너를 구동하면
  -	컨테이너가 구동되는 시점에 스프링 설정 파일에 등록된 빈을 생성하고 컨테이너에 로드




#### (2-2) XML을 이용한 DI - 생성자 기반 DI

-	클래스에 생성자가 있어야 하고 스프링 설정 파일(xml)에서 빈을 정의할 때
-	``<constructor-arg ref=”의존하는 bean”>`` 태그를 이용하여 의존성 주입
-	Main에서 객체 생성하지 않고 XML 설정 파일에서 빈 생성
-	main() 하는 역할
  -	컨테이너 객체 생성
  -	컨테이너에서 컴포넌트(빈) 가져옴



#### Annotation을 이용한 DI

- xml 설정 파일에서 ``<bean>`` 태그를 이용해서 설정하였던 빈 설정을
- Annotation(메타데이터)을 이용해서 자바 코드에서 설정
  - 예 : xml 설정 파일에서 빈을 설정하지 않고 스프링 자바 소스 코드를 읽어서
  - 클래스에 @Componet 어노테이션이 붙은 클래스를 객체화 (bean 설정)
  - A1 클래스의 객체를 A2 클래스의 객체로 변경하려면 A1 클래스에서 @Component를 제거하고 A2 클래스에 
  - @Component를 붙이면 됨
  - @Autowired 어노테이션을 사용하여 bean을 자동 삽입



#### <span style=color:blue>xml 설정 파일에 context 네임스페이스 추가</span>

- 빈 설정을 위한 어노테이션을 사용하기 위해서는
- 설정 파일에 context 네임스페이스가 추가되어있어야 함 ([Namespaces] 탭에서 추가
- ``<context:component-scan>`` 태그를 이용하여 빈으로 등록된 클래스를 찾아서(scan) 클래스를 객체화(빈 설정)



#### 스프링에서 사용하는 Annotation

##### <span style=color:blue>Annotation 종류</span>

- <span style=color:blue>DI(의존성 주입) 관련 Annotation</span>

  - <span style=color:red>@Autowired</span> / @Inject

  - <p style=color:red>@Qualifier

  - @Resource

- <span style=color:blue>빈 생성 관련 Annotation</span>

- <p style=color:red>@Component

  - <span style=color:red>@Controller</span>
  - <span style=color:red>@Service</span>
  - <span style=color:red>@Repository</span>

- @Configureation

  - @Bean

- Spring MVC 



#### DI(의존성 주입) 관련 Annotation

- xml 설정 파일에 있는 ``<bean>``에 대해 DI하거나
- 자바 코드에서 생성된 bean에 대해 DI할 수 있음
- <span style=color:red>@Autowired</span>	
  - 타입을 기준으로 의존성 주입
  - 스프링 빈에 의존하는 <span style=color:blue>다른 빈을 자동으로 주입</span>할 때 사용
  - 스프링에서 지원
- <span style=color:red>@ Inject </span>
  - @Autowired와 동일
  - 자바에서 지원
- <span style=color:red>@Qualifier</span>
  - <span style=color:red>특정 빈의 이름을 지정</span>
  - <span style=color:blue>동일한 interface 구현한 클래스가 여러 개 있는 경우</span>
  - 사용하고자 하는 빈의 이름을 지정할 때 사용
  - 설정 파일 : ``<bean>`` 추가
- <span style=color:red>@Resource</span>
  - <span style=color:red>@Autowired</span>와 <span style=color:red>@Qualifier</span>를 같이 사용하는 것과 동일
  - @Resorce(name=”빈 이름”)
  - 자바에서 지원
  - pom.xml에 라이브러리 추가 
    - javax.annotation



#### 빈 생성 관련 Annotation

- 빈 생성(설정)을 위해 클래스 위에 추가되는 어노테이션
- 클래스 이름 위에 붙이면 클래스 파일에 대한 bean이 자동 생성(xml 파일에서 bean 생성 X)
- 빈의 이름은 <span style=color:red>클래스 이름에서 첫 문자만 소문자</span>로 지정
- 어노테이션을 이용하기위해 xml 설정 파일에서 필요한 작업 
  - xml 설정 파일에 context 네임스페이스 추가 필요
  - <<span style=color:red>context-component-scan</span> <span style=color:blue>base-package="패키지명"</span>>
    - @Component  어노테이션이 적용된 클래스를 빈으로 등록
    - 빈으로 등록될 클래스가 들어 있는 패키지 지정
    - 상위 패키지를 지정하면 하위 패키지까지 빈으로 등록될 클래스 찾음
    - ``<context:annotation-config /> `` 필요 X



#### @Component

- 클래스를 빈으로 등록(부품 등록)
- 빈 id 지정 가능
- @Component("빈이름")
  - ``<bean id="빈이름">``에 해당



##### @Component 어노테이션의 의미론적 어노테이션

- @Component : 일반적인 컴포넌트 의미
- 특화된 @Component 어노테이션
  - 클래스의 역할에 따라 의미론적으로 구분
    - @Controller 컴포넌트
    - @Service 컴포넌트
    - @Repository 컴포넌트



<img width="452" alt="image-20220705131049795" src="https://user-images.githubusercontent.com/101630615/177247845-b8eb5196-c8de-4ab1-bf3f-8a7d8743d066.png">



#### Spring MVC 구성에 따른 어노테이션 사용



<img width="452" alt="image-20220705131054893" src="https://user-images.githubusercontent.com/101630615/177247851-f568aa02-49b1-4bf8-b509-3f44ebcda5d5.png">


