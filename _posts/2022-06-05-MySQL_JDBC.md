

# [MySQL] JDBC 

 

### JDBC (Java Database Connectivity)

\-   다양한 종류의 관계형 데이터베이스에 접근할 때 사용하는 자바 표준 SQL 인터페이스

\-   자바 프로그램이 DBMS에 접근하여 작업할 수 있게 해주는 API를 제공하는 클래스 모음

\-   모든 DBMS에서 공통적으로 사용할 수 있는 인터페이스와 클래스로 구성

\-   실제 구현 클래스는 각 DBMS 벤더가 구현했기 때문에 거의 모든 벤더가 JDBC 드라이버 제공

\-   각 DBMS에 맞는 JDBC 드라이버 사용

 

#### JDBC 드라이버

\-   JDBC 인터페이스를 구현한 클래스 파일 모음 (jar 파일)

\-   각 DBMS 벤더에서 제공되는 구현 클래스

 

#### JDBC 구성

\-   JDBC 인터페이스

\-   JDBC 드라이버

#### JDBC의 역할

\-   응용프로그램과 DBMS 사이에서 연결 역할

\-   SQL문을 DBMS에 전달하고 그 결과값을 응용프로그램에 전달하는 역할 

![clip_image002](https://user-images.githubusercontent.com/101630615/173413398-573e19f3-c4b2-4df1-9a1c-847e17b76e23.jpg)

 

#### JDBC를 사용했을 때의 효용성

\-   사용하는 RDBMS에 독립적인 프로그래밍이 가능

\-   쉽게 RDBMS의 교체가 가능

\-   자바는 단순히 문자열로 QUERY를 전달할 뿐이고 해석은 각 벤더가 구현한 DRIVER에서 담당하기 때문에

\-   표준 SQL 뿐 아니라 각 JDBC Driver를 제공하는 DBMS 벤더별로 최적의 성능을 발휘할 수 있는 벤더 종속적인 SQL에 대한 처리도 가능



#### JDBC를 이용한 연결 과정

(1) 드라이버 로드

(2) Connection 객체 생성

(3) Statement 객체 생성

(4) SQL 문에 결과 반환이 있는 경우 ResultSet 객체 생성 (결과 획득)

(5) 쿼리 수행

(6) 모든 객체(자원) close()

\-   ResultSet

\-   Statement 

\-   Connection (접속 종료)

 

![clip_image004](https://user-images.githubusercontent.com/101630615/173413404-327a5e6e-b0af-47d4-8360-b0ec8f20c136.jpg)

 

##### 패키지 import

\-   JDBC는 java.sql 패키지에 포함되어 있음

![clip_image006](https://user-images.githubusercontent.com/101630615/173413407-1585d1eb-b386-44ec-bf80-dbe6aa1ac782.jpg)

 

\-   JDBC는 데이터베이스에 접속하기 위해

\-   한 개의 클래스 (java.sql.DriverManager)와

\-   두 개의 인터페이스 (java.sql.Driver, java.sql.Connection)를 사용

 

1.  JDBC 드라이버 로드

\-   Java에서 MySQL Driver를 사용하기 위해 드라이버를 JVM에 로딩하는 과정

\-   동적으로 MySQL JDBC Driver 클래스의 객체를 생성해서 런타임 시 메모리에 로딩

\-  `` Class.forName(“com.mysql.cj.jdbc.Driver”);``



2. Connection 객체 생성

\-   DriverManager 클래스의 static 메소드인 getConnection() 메소드를 이용해서 Connection 객체를 얻어 옴

\-   MySQL 서버 실제 연결

\-   Connection 객체가 생성되면 DBMS 접속 성공

```
String url = “jdbc:mysql://localhost:3306/sqldb3?serverTimezone-UTC”;

String user = “root”;

String pwd = “1234”;

DriverManager.getConnection(url, user, pwd);
```



3.  Statement 객체 생성

\-   쿼리문 전송을 위한 Statement 객체 생성

\-   또는 PreparedStatement 객체 생성

\-   Statement 인터페이스

\-   Connection 인터페이스의 createStatement() 메소드를 사용하여 객체 생성

```
Statement stmt = con.createStatement();

PreparedStatement pstmt = con.prepareStatement(sql);

Statement 객체를 통해 SQL 전송 가능
```



4. 쿼리 수행

SQL 쿼리 전송에 사용되는 메소드

\-   executeQuery() / executeUpdate()

\-  `` pstmt.executeUpdate();``

 

***2가지로 구분하는 이유***

\-   SQL 문 실행 결과가 다르기 때문

 

#### executeUpdate()

\-   쿼리문이 insert, update, delete 구문인 경우 사용

\-   영향을 받은 행의 수 반환

\-   ``String sql = “insert ……”;``

\-  `` int result = pstmt.executeUpdate(sql);``

\-   result가 0보다 크면 insert 성공

\-   result가 0이면 insert 되지 않았음(실패)

#### executeQuery()

\-   select 구문의 경우 사용

\-   ResultSet 객체로 반환 (select 문 결과에 해당되는 여러 행 (또는 한 개 행) 반환)

\-   ``String sql = “select …..”;``

\-  `` ResultSet rs = pstmt.executeQuery(sql);``

 

5. ResultSet 객체로부터 결과 획득

\-   select 구문의 경우

\-   executeQuery() 메소드 결과로 ResultSet 반환

\-   ResultSet에서 데이터 추출

\-   ResultSet의 next() 메소드를 사용해서 논리적 커서를 이동해가며 각 열의 데이터를 바인딩해 옴

\-  `` ResultSet rs = pstmt.executeQuery(sql);``

\-  `` boolean b = rs.next();``

\-   여러 행인 경우 반복 사용 : ``while(rs.next) { … }``

 

#### ResultSet 메소드

\-   ``next()``

\-   커서를 이동하면서 다음 행 지정

\-   시작 시 첫 번째 행 이전에 위치해 있다가 next() 메소드가 호출되면 이동하면서 첫 데이터를 가리킴

\-   리턴 타입은 boolean

\-   다음 행이 있으면 true, 없으면 false 반환

\-   모든 행을 가져오려면 반복문 사용

```
getXXX()
실제 값을 가져오는 메소드
데이터 타입에 맞춰 사용

getString() / getInt() / getDate()

String bookNo = rs.getString(1);

int bookPrice = rs.getInt(2);

Date bookDate = rs.getDate(3);
```

![clip_image008](https://user-images.githubusercontent.com/101630615/173413408-f8b63c2f-b90d-4389-a9b6-861767af3cf5.jpg)

 

6. 모든 객체 close()

\-   ResultSet

\-   Statement(PreparedStatement)

\-   Connection

```
 rs.close() / pstmt.close() / con.close()

if(rs != null) rs.close(); rs=null;
```

 

### DTO (Data Transfer Object)

\-   데이터 저장용 클래스

\-   데이터베이스에 데이터 저장하거나 데이터베이스로부터 데이터를 조회할 때 데이터를 담아놓기(저장하기) 위해 사용

\-   멤버 필드 / 생성자 / Getters/Setters

 

### DAO (Data Access Object)

\-   데이터베이스에 액세스하는 클래스

\-   데이터베이스에 데이터를 저장하거나 데이터베이스로부터 데이터를 가져올 때 사용

\-   (1) DB 연결 (DBConnect라고 DB 연결 담당 클래스 사용해도 됨)

\-   (2) select() / insert() / update() / delete() 기능의 메소드 포함
