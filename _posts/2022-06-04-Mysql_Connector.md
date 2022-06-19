# [MySQL] Mac jdbc 드라이버 다운로드

[https://dev.mysql.com/downloads/connector/j/](https://dev.mysql.com/downloads/connector/) 사이트에 접속합니다.

\-   Select Operation System 옵션을 Platform Independent 선택합니다.

![스크린샷 2022-06-18 오전 2 38 01](https://user-images.githubusercontent.com/101630615/174354134-475facf0-5eb4-4560-aaf5-31059fafaea0.png)

본인의 버전에 맞게 두 개의 파일중 하나를 선택하여 다운로드하고,

다운로드 폴더로 들어가서 압축 해제 후 mysql-connector-java-8.0.29(버전에 따라 변경).jar 파일을 복사합니다.



아래 이미지를 참고하여 자바를 설치한 경로로 들어갑니다.

jdk 버전이 2가지 이상인 경우 현재  사용하고 있는 jdk 폴더로 들어갑니다.

<img width="1117" alt="스크린샷 2022-06-18 오전 2 43 17" src="https://user-images.githubusercontent.com/101630615/174354140-b66812f8-cd9f-4032-a704-f363f45baab2.png">

 



<img width="1117" alt="스크린샷 2022-06-18 오전 2 43 42" src="https://user-images.githubusercontent.com/101630615/174354144-86391363-c3a3-47f5-ae94-3562774e421b.png">





이클립스를 실행 후 환경 설정 패널로 들어가

Preference -> Java -> Installed JREs -> 주로 사용하는 버전 선택 후 Edit을 선택한다.

<img width="606" alt="스크린샷 2022-06-18 오전 2 46 33" src="https://user-images.githubusercontent.com/101630615/174354146-bbb3ef26-17be-48de-9158-d7001447c335.png">





<img width="829" alt="스크린샷 2022-06-18 오전 2 47 06" src="https://user-images.githubusercontent.com/101630615/174354153-26f964a8-c6a3-495a-91d2-c6ff21acefe0.png">



Add External JARs 선택

<img width="875" alt="스크린샷 2022-06-18 오전 2 47 33" src="https://user-images.githubusercontent.com/101630615/174354155-9b174b63-90cf-430c-b7b0-42072a3a74ef.png">



<img width="929" alt="스크린샷 2022-06-18 오전 2 47 51" src="https://user-images.githubusercontent.com/101630615/174354157-152860b6-d246-4f13-a801-70a21594b359.png">

폴더에 붙여 넣었던 jar 파일을 선택후 open -> finish -> Apply and Close 선택하여 창을 닫는다.





Db가 연결되었는지 코드를 통해 확인해보자.

패키지와 클래스,  id와 pwd는 사용자가 설정한 값을 입력한다.

<img width="677" alt="스크린샷 2022-06-18 오전 2 56 24" src="https://user-images.githubusercontent.com/101630615/174354163-05030421-7e0c-41c8-ac7a-293aa430e55a.png">



이미지의 코드 값입니다.

```
package db1;

import java.sql.Connection;
import java.sql.DriverManager;

public class DBConnect {

	public static void main(String[] args) {
		try {
			Class.forName("com.mysql.cj.jdbc.Driver"); 

//		연결 url, 사용자 계정, 패스워드 문자열로 지정 
			String url = "jdbc:mysql://localhost:3306/sqldb3?serverTimezone-UTC";
			String user = "root";
			String pwd = "1234";

		Connection con = DriverManager.getConnection(url, user, pwd);
		
		if(con!=null) {
			System.out.println("Db 연결 성공");
		}
		
		} catch (Exception e) {
			System.out.println("오류 발생");
			e.printStackTrace();
		}

	}

}
```

``Connection`` 와``DriverManager`` 패키지는 ctrl + shift +O 단축키를 통해 패키지를 삽입한다.





아래와 같이 결과가 나오면 성공적으로 연결된 것이다.

<img width="630" alt="스크린샷 2022-06-18 오전 2 55 39" src="https://user-images.githubusercontent.com/101630615/174354161-8b6b0dd2-2afd-4bba-ac52-ce5fd5f6fec4.png">

[출처] : [https://dev-ku.tistory.com/212](https://dev-ku.tistory.com/212)