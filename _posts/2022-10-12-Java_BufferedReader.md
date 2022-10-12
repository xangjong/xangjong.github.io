# [Java] BufferedReader





### BufferedReader / BufferWriter

- 버퍼를 이용해서 읽고 쓰는 함수
- 입출력의 속도가 Scanner보다 빨라서 효율적





![스크린샷 2022-10-12 오후 2 43 23](https://user-images.githubusercontent.com/101630615/195267295-0ebd2b59-7726-41ea-8823-6fa108458a79.png)



버퍼를 한 번 거쳐가는데 빠른 이유는 하드뿐만 아니라 키보드, 모니터 등 외부장치의 

데이터 입출력은 시간이 걸리는 작업이다.

버퍼링없이 키보드가 눌릴 때마다 문자의 정보를 목적지로 바로 이동시키는 것보다

중간에 메모리 버퍼를 둬서 데이터를 한 곳에 묶어서 이동시키는 것이 보다 효율적이고 빠르다.



##### 버퍼(Buffer)

- 데이터를 한 곳에서 다른 한 곳으로 전송하는동안 일시적으로 그 데이터를 보관하는 임시 메모리 영역
- 입출력 속도 향상을 위해 버퍼 사용 



##### 버퍼 플러시(Buffer flush)

- 버퍼에 남아있는 데이터를 출력(버퍼를 비우는 동작)



#### BufferedReader

- 버퍼를 이용한 입력
- 엔터만 경계로 인식하고 받은 데이터가 String으로 고정되기 때문에 형변환 필수



사용 방법 

```java
import java.io.*;

public class Main{
  public static void main(String[] args) throws IOException{
    // 예외 처리 필수 try catch~ 혹은 thorws IOException 
    
    // 콘솔에서 입력받을 경우
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    
    // 파일에서 입력받을 경우 
    FileReader fr = new FileReader("파일명.파일형식");
    BufferedReader br_f = new BufferedReader(fr);
    
    // String을 리턴하기 때문에 형변환 필수 
    // readLine() : 데이터를 라인 단위로 읽는 함수
    int num = Integer.parseInt(br.readLine());
     
    // 입출력이 끝난 후 닫기 
    br.close(); 
    
  }
}
```

한 줄 단위로 읽기때문에 공백 단위로 데이터를 알려면 StringTokenizer의 nextToken() 함수를 이용하거나

String 클래스의 split 함수를 이용하는 방법이 있다.



```java
StringTokenizer st = new StringTokenizer(br.readLine());
int num = Integer.parseInt(st.nextToken());

String array[] = br.readLine().split(" ");
```







![스크린샷 2022-10-12 오후 3 18 22](https://user-images.githubusercontent.com/101630615/195267301-e04dec1f-c5dc-4511-ab74-5527febc110e.png)







#### BufferedWriter

- 버퍼를 이용한 출력
- ``System.out.println("");`` 와 동일하게 사용 가능한 함수



사용 방법

```java
import java.io.*;

public class Main {
  public static void main(String[] args) throws IOException{
		// 예외처리 
    BufferedWriter bw = new BufferedWriter(new FileWriter("BufferedWriter.txt"));
    
    bw.write("hellon\n");
    bw.newLine();
    bw.write("Write practice\n");
    bw.flush();
    bw.close();
    
  }
}
```

BufferedWriter의 경우 버퍼를 할당했기 때문에 반드시 flush() / close()를 반드시 호출하여 마무리한다.

``System.out.println("");``처럼 함수가 문자열 출력과 개행을 동시에 지원하지 않기 때문에

개행을 하려면 write에 ``\n`` 을 넣어주거나 ``newLine();`` 함수를 사용한다.



![스크린샷 2022-10-12 오후 3 18 39](https://user-images.githubusercontent.com/101630615/195267305-7fb36efc-39c3-4dce-84f3-e29d847981ff.png)



[출처] : [https://jhnyang.tistory.com/92](https://jhnyang.tistory.com/92)