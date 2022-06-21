

# [Eclipse] Mac Tomcat Port 8080 Error

> IDE로 톰캣을 실행한 상태에서 응답없음으로 인해 강제 종료 후,
>
>  다시 프로젝트를 실행하면 이미 사용중이라는 오류메 세지가 나오는 에러입니다.



알 수 없는 오류로 인해  프로세스는 종료되지 않아 현재 프로세스는 켜져있는 상태인데, 

기존 포트번가 적힌 포트를 어떤 프로세스가 찾아 점유중인지 확인하여 종료합니다.



먼저 현재 사용하는 포트 번호를 조회합니다.

아래 콘솔창의 ``Servers`` 를 더블 클릭 하시면,

<img width="680" alt="Port_Search" src="https://user-images.githubusercontent.com/101630615/174284553-c97c5306-a69e-40c1-9fbe-bfa0934f9570.png">



우측 메뉴 탭을 보시면 Ports의 HTTP/1.1이 보입니다. 

그 옆의 Port Number를 확인하면 저는 현재 포트번호 8080을 사용중입니다.

<img width="1155" alt="Port_num" src="https://user-images.githubusercontent.com/101630615/174284543-c0528cce-8c1c-479c-96b3-76c7229dc50a.png">



터미널을 실행한 후 아래 명령어를 입력하면 어떤 프로세스가 포트를 점유중인지 확인할 수 있습니다.

```
sudo lsof -i : [PORT NUMBER]

ex )
sudo lsof -i:8080
```

<img width="776" alt="terminal" src="https://user-images.githubusercontent.com/101630615/174284558-a431e224-a1de-4b7f-8dbc-c324e8fe65e9.png">



저는 Port 8080을 조회하기 위해 입력하였습니다.

비밀번호는 화면에 표시되지 않으니 사용하는 mac의 계정 비밀번호를 입력하면 됩니다.





```
kill [PID NUMBER]

ex)
kill 3993
```

점유중인 프로세스의 PID를 kill하면 종료됩니다.



<img width="713" alt="terminal2" src="https://user-images.githubusercontent.com/101630615/174284561-9df45d90-bbf9-422d-b90b-f5367972e8c0.png">

재시작하면 톰캣이 다시 작동하는 것을 볼 수 있습니다.


출처 : https://abit.ly/4jfcyq
