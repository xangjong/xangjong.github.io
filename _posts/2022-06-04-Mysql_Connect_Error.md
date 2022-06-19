# [MySQL] 오류 & 해결 방법

### mysql 접속 오류

1. ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: **NO**)

   **1번**의 경우 비밀번호를 입력하지 않은 경우입니다.

   `mysql -u [user name] -p [your password]` 을 통해 입력합니다.
   ex. mysql -u root -p 1234

   

2. ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: **YES**)

   **2번**의 경우 입력한 비밀번호가 틀린 경우입니다. 비밀번호 분실 시 초기화하고 

   그것을 적용시켜 줍니다.

   mysql> `use mysql` 
   mysql> `update user set password=password('바꿀 비밀번호') where user='사용자 이름'; ` 

   mysql> `flush privileges;`

하지만 여기서 오류가 해결되지 않는다면, mysql에서 root 패스워드를 지우고 재설정합니다.

```
update mysql. user set authentication_string = null where user='root'; 
flush privileges;
exit;
```

mysql에서 root 패스워드를 지우고 종료하는 과정인데 순차적으로 한 줄씩 입력합니다.



``` 
mysql -u root
```

터미널에서 다시 접속합니다.



```
alter user 'root'@'localhost' identified with caching_sh2_password by 'yourpasswrd';
flush privileges;
```

비밀번호를 다시 입력하고 적용합니다.



![mysql_error](https://user-images.githubusercontent.com/101630615/172049914-a517c00e-b91a-4eab-9a15-0c7cde93e36d.png)

전체 과정입니다.



[출처] : [https://toytvstory.tistory.com/1617](https://toytvstory.tistory.com/1617 ) 





