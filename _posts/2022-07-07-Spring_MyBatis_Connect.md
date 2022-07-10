# [Spring] M1 데이터베이스 연동



### MyBatis 연동 스프링 프로젝트 작성 순서

#### 1. MVC 프로젝트 생성

 New -> Legacy Project -> Spring MVC Project(프로젝트 명) 입력 후 Next -> 패키지 명 입력 -> Finish



<img width="800" alt="spring_mvc_project" src="https://user-images.githubusercontent.com/101630615/177975483-0086a28f-e493-4189-9e13-fa28f574fdb8.png">



<hr>



#### 2. pom.xml 기본설정

- Java : 11

- Spring : 5.2.22.RELEASE

- Maven 1.8

  

pom.xml을 실행 후 Java-version을 11 

Spring-framework-version을  5.2.22 RELEASE 버전으로 변경

<img width="888" alt="pom_xml_set" src="https://user-images.githubusercontent.com/101630615/177975473-0af6164a-7416-405b-86be-e29e8dcaeada.png">

 



스크롤을 내린 후 maven-compiler-plugin의 source와 target을 1.8로 변경

<img width="888" alt="pom_xml_set2" src="https://user-images.githubusercontent.com/101630615/177975477-4f31ba98-5d35-4a9d-a638-d2dd87f42d21.png">





<hr> 



#### 3. 프로젝트 설정

- Java Compiler
- Java Build Path
- Project Facets



생성한 Project에서 우클릭 -> Properties 

Java Compiler -> Compiler compliance level을 수정 후 Apply(Use 체크를 해제 한 후 본인에게 맞는 버전 적용)

<img width="989" alt="Java_Compiler" src="https://user-images.githubusercontent.com/101630615/177975453-27fd669b-992b-4233-b312-e3c3f613cdac.png">



<hr>



Java Build Path  -> Edit ->(현재 사용하고 있는 버전으로 수정) 후 Apply

<img width="994" alt="Java_Buile_Path" src="https://user-images.githubusercontent.com/101630615/177975448-15f82d88-4509-4aa7-9e51-86b29a5fb68e.png">







<img width="665" alt="Java_JRE" src="https://user-images.githubusercontent.com/101630615/177975456-15f1427e-d4bc-4d3c-920f-4a79ed3f8d92.png">





<hr>



Project Facts -> Java 버전을 현재 사용하고 있는 버전(저는 11을 사용중입니다.) 을 바꾼 후 Runtimes 탭의

Apache Tomcat v9.0(본인에게 맞는 버전)을 클릭 후  Apply

<img width="800" alt="Project_facts" src="https://user-images.githubusercontent.com/101630615/177975481-428fe305-b655-42f4-a346-f49b2c5fe1e7.png">





<hr> 

#### MySQL 커넥터 확인

- C:\apache-tomcat-9.0.64\lib 폴더에
- ``mysql-connector-java-8.0.29.jar`` 파일 있는지 확인





#### 4. pom.xml에 데이터베이스 의존성 설정

- (라이브러리 추가 : ``<dependency>`` 추가)
- Spring JDBC 의존성 : spring-jdbc
- Connection Pool 의존성 : commons-dbcp
- mysql 의존성

실행한 pom.xml 파일의 하단에서 Dependencies 탭 클릭 후 Add(dependency 추가)

<img width="903" alt="pom_xml_depend" src="https://user-images.githubusercontent.com/101630615/177975468-80d57151-5ec8-428b-9465-8fa5d6fd6e72.png">





spring JDBC 의존성 : spring-jdbc 검색 후 5.2.22 RELEASE[jar] 선택 후 OK 

<img width="500" alt="spring-jdbc_5 22 Rellease" src="https://user-images.githubusercontent.com/101630615/177975486-0a2e103d-cfe5-4684-840c-a6b699c3cb89.png">







간혹 검색이 되지 않는 경우 pom.xml의  ``<dependencies>`` 탭 안에 아래 코드를 소스 안에 추가 

```jsp
<dependency>
  <groupId>org.springframework</groupId>
  <artifactId>spring-jdbc</artifactId>
  <version>5.2.22.RELEASE</version>
</dependency>
```



<hr>



Connection Pool 의존성 : commons-dbcp



<img width="500" alt="commons-dbcp" src="https://user-images.githubusercontent.com/101630615/177975439-468a5e6b-25d1-49ce-87ff-07db1f2bcc18.png">



소스 코드

```jsp
<dependency>
  <groupId>commons-dbcp</groupId>
  <artifactId>commons-dbcp</artifactId>
  <version>1.4</version>
</dependency>
```



<hr>



mysql 의존성 : mysql-connector 8.0.29

<img width="500" alt="mysql_connector" src="https://user-images.githubusercontent.com/101630615/177975461-808b272b-0a88-4e5c-bfaa-c72ca27e838b.png">



소스코드

```jsp
<dependency>
  <groupId>mysql</groupId>
  <artifactId>mysql-connector-java</artifactId>
  <version>8.0.29</version>
</dependency>
```



<hr>



Mybatis / mybatis-spring 의존성



Mybatis 3.5.10

<img width="500" alt="org-mybatis" src="https://user-images.githubusercontent.com/101630615/177975466-a71bbdee-e879-469e-beed-091c2fd5db8a.png">



Mybatis 소스 코드 

```jsp
<dependency>
  <groupId>org.mybatis</groupId>
  <artifactId>mybatis</artifactId>
  <version>3.5.10</version>
</dependency>
```



<hr>



Mybatis-spring 2.0.7

<img width="500" alt="mybatis_spring" src="https://user-images.githubusercontent.com/101630615/177975460-8bfe149e-fa0e-45f9-a1bb-0bfa7fba963a.png">





Mybatis-spring 소스코드

```jsp
<dependency>
  <groupId>org.mybatis</groupId>
  <artifactId>mybatis-spring</artifactId>
  <version>2.0.7</version>
</dependency>
```



<hr>

위의 과정을 다 거쳤다면, 



<img width="900" alt="pom_xml_depend" src="https://user-images.githubusercontent.com/101630615/177975468-80d57151-5ec8-428b-9465-8fa5d6fd6e72.png">



추가 후 저장한 후에 pom.xml의 소스 창을 확인합니다.



성공적으로 추가한 것을 알 수 있습니다.

<img width="700" alt="pom_xml" src="https://user-images.githubusercontent.com/101630615/177975480-fa58f9d5-88f3-49a5-bc9d-19dd4a70a4bb.png">





<hr>



#### 데이터베이스 연결 정보설정

- jdbc.properties 파일 생성
  - jdbc.driverClassName
  - url / username / password
- 스프링 설정 파일 생성 : application-config.xml
  - DataSource / Mapper 지정
- web.xml에 변경된 내용 설정



아래 코드를 복사하여 web.xml ``</web-app>`` 안에 넣어 추가하여

한글 출력을 잘 나오게 합니다.

```
<!-- 한글설정 -->
<filter>
   <filter-name>encodingFilter</filter-name>
   <filter-class>
      org.springframework.web.filter.CharacterEncodingFilter
   </filter-class>

   <init-param>
   	<param-name>encoding</param-name>
   	<param-value>UTF-8</param-value>
   </init-param>

	<init-param>
  	<param-name>forceEncoding</param-name>
	  <param-value>true</param-value>
	</init-param>
</filter>

<filter-mapping>
	<filter-name>encodingFilter</filter-name>
  <url-pattern>/*</url-pattern>
</filter-mapping>

<!-- 한글설정 END -->
```





src/main/resource -  database 폴더 생성 - file  ->  jdbc.properties

spring 폴더 생성 - Spring bean Configuration file 생성 -> application-config

<img width="300" alt="스크린샷 2022-07-08 오전 2 35 03" src="https://user-images.githubusercontent.com/101630615/177975403-7c301490-0768-40f2-a117-9ad74bebb1c9.png">



db연결을 위해 아래 코드를  jdbc.properties 파일에 작성합니다.

현재 저는 mySql의 root 계정과 패스워드를 사용중이며

3306 호스트의 springs 테이블을 기본 값으로 적용했습니다.

<img width="835" alt="스크린샷 2022-07-08 오전 2 35 36" src="https://user-images.githubusercontent.com/101630615/177975424-044360da-132e-46bd-82c0-54a1e1559aec.png">



<hr>



#### DataSource / Mapper 지정

Application-config.xml 생성 후 하단 Namespaces 탭에서 beans, context, mybatis-spring을 체크합니다.

생성하기 전에 Next에서 체크할 수 있으나 여기서도 수정이 가능합니다.

<img width="500" alt="NameSpace" src="https://user-images.githubusercontent.com/101630615/177975464-04a26eed-b76e-45ce-a99b-f4a307563a78.png">







<img width="896" alt="스크린샷 2022-07-08 오전 2 35 52" src="https://user-images.githubusercontent.com/101630615/177975432-ede982c7-825d-4eeb-8b86-a416a11cd69b.png">



연동 소스코드

```jsp
<context:property-placeholder location="classpath:database/jdbc.properties"/>
<context:component-scan base-package="com.spring_mvc.mybatis" />

<bean id="dataSource"  class="org.apache.commons.dbcp.BasicDataSource">
  <property name="driverClassName" value="${jdbc.driverClassName}" />
  <property name="url" value="${jdbc.url}" />
  <property name="username" value="${jdbc.username}" />
  <property name="password" value="${jdbc.password}" />
</bean>

<bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
  <property name="dataSource" ref="dataSource" />
  <property name="mapperLocations" value="classpath:com/spring_mvc/mybatis/**/*.xml" />
</bean>

<mybatis-spring:scan base-package="com.spring_mvc.mybatis.dao"/>
```



\-   **web.xml에** **변경된** **내용** **설정**

​	\-   **application-config.xml** **사용한다고** **설정**

<img width="600" alt="image-20220708025157089" src="https://user-images.githubusercontent.com/101630615/177975442-7bc23cee-c841-436a-bb6b-7df025160292.png">



마무리 되었다면 아래 결과와 같이 정상적으로 작동합니다.



<img width="500" alt="image-20220708025254829" src="https://user-images.githubusercontent.com/101630615/177975444-e0c8e1e5-2eee-47e6-b1d2-dddf481382e4.png">





