



# [MarkDown] 문법



- ▶️ 버튼을 누르시면, 노션에 해당하는 **Markdown 으로 블록 만들기**를 한 번에 확인하실 수 있습니다.

  **글꼴**

  - 텍스트 양쪽에 `**`을 입력하면 **굵게** 표시됩니다.
  - 텍스트 양쪽에 `*`를 입력하면 *이탤릭체*로 표시됩니다.
  - 텍스트 양쪽에 ``` 을 입력하면 `인라인 코드`로 표시됩니다(숫자키 1 왼쪽에 있는 기호입니다).
  - 텍스트 양쪽에 `~`를 입력하면 취소선이 그어집니다.

  **텍스트 시작 부분에서,**

  - `*`나 `-`, `+` 다음에 `space`를 입력하면 글머리 기호를 만듭니다.
  - `[]`를 입력하면 체크박스가 있는 할 일 목록을 만듭니다(사이에 `띄어쓰기`가 없습니다).
  - `1.` 다음에 `space`를 입력하면 번호 매기기 목록을 만듭니다.
  - `#` 다음에 `space`를 입력하면 대제목을 만듭니다.
  - `##` 다음에 `space`를 입력하면 중제목을 만듭니다.
  - `###` 다음에 `space`를 입력하면 소제목을 만듭니다.
  - `>` 다음에 `space`를 입력하면 토글 목록을 만듭니다.
  - `"` 다음에 `space`를 입력하면 인용구 블록을 만듭니다.

------

### **제목 (Headings)**

- `h1 ~ h6` 에 해당하는 제목을 표현합니다.

- `#`을 사용합니다.

  - 노션에서는 3번째 수준까지 제공합니다.

  ```markdown
  # 제목 1
  ## 제목 2
  ### 제목 3
  #### 제목 4
  ##### 제목 5
  ###### 제목 6
  ```

  ![https%3A%2F%2Fs3-us-west-2 amazonaws com%2Fsecure notion-static com%2Fb1534e2b-b67f-47d0-b966-76b3f50d09ad%2FUntitled](https://user-images.githubusercontent.com/101630615/177072797-4ea1c004-1938-4826-b75a-61dbb6ac2fb5.png)

  

### **목록 (List)**

- 순서가 없는 목록과 순서가 있는 목록을 표현합니다.

- 순서가 없는 목록은 `- * +` 를 사용합니다.

- 순서가 있는 목록은 `1. 2. 3.` 과 같은 숫자를 사용합니다.

  - `tab 키`를 이용해서 들여쓰기, `shift + tab`을 통해 내어쓰기를 할 수 있습니다.

  ```markdown
  - 순서가 없는 목록
  	- 서브 목록
  	- 서브 목록
  
  + 순서가 없는 목록
  	+ 서브 목록
  	+ 서브 목록
  
  * 순서가 없는 목록
  	* 서브 목록
  	* 서브 목록
  
  1. 순서가 있는 목록
  	1. 서브 목록
  	2. 서브 목록
  
  1. 혼합 해보기 1
  	- 순서 없음
  	+ 순서 없음
  	* 순서 없음
  2. 혼합 해보기 2
  	1. 순서 있음
  	- 순서 없음
  	2. 순서 있음
  ```

  ![https%3A%2F%2Fs3-us-west-2 amazonaws com%2Fsecure notion-static com%2F00bafa7d-6880-4280-a763-e65d1c6356ca%2FUntitled](https://user-images.githubusercontent.com/101630615/177072782-f60525c6-ba8b-4f2e-bee7-cf8a547e61a3.png)

### **강조 (Emphasis)**

- 글자의 스타일링을 표현합니다.

  1. **기울임** : `*글자*` 혹은 `_글자_`
  2. **굵게** : `**글자**` 혹은 `__글자__`
  3. **취소** : `~~글자~~`

  ```markdown
  *이탤릭체1* 
  _이탤릭체2_
  
  **볼드체1**
  __볼드체2__
  
  ~~취소선~~
  ```

  ![https%3A%2F%2Fs3-us-west-2 amazonaws com%2Fsecure notion-static com%2F77e83882-4710-4bcd-a010-8b2e88cfb543%2FUntitled](https://user-images.githubusercontent.com/101630615/177072792-b2f1f14b-c3c2-4612-8e13-7bdea345cca6.png)

### **코드 (Code)**

- 한 줄 코드인 **인라인 코드**와 여러 줄 코드인 **블록 코드**로 나눌 수 있습니다.

1. 인라인(Inline) 코드 : `inline code`처럼 백틱을 통해 코드를 감싸줍니다.

2. 블록(Block) 코드 : ````python` 처럼 백틱을 3번 입력하고 코드의 종류를 작성합니다.

   ~~~markdown
   파이썬의 print는 `print("Hello World!")` 과 같이 사용합니다.
   
   ```python
   for i in range(10):
   	print(i)
   ~~~

   ```bash
   $ touch test.txt
   ```

   ```
   Just plain text
   ```

   

### **인용 (Blockquote)**

- 주석이나 인용 문구를 표현합니다.

- `>` 를 사용합니다. 갯수에 따라 중첩이 가능합니다.

  - 노션에서는 `>` 는 토글로 사용되며, `“` 혹은 `|`로 인용문을 생성합니다.

  ```markdown
  > 인용문을 작성합니다.
  >> 중첩된 인용문 1
  >>> 중첩된 인용문 2
  >>>> 중첩된 인용문 3
  >>>>> 중첩된 인용문 4
  ```

  ![https%3A%2F%2Fs3-us-west-2 amazonaws com%2Fsecure notion-static com%2Fae65cfd3-5a2d-49f9-bb6f-45ee987dda66%2FUntitled](https://user-images.githubusercontent.com/101630615/177072795-6ba5438b-3350-4581-badb-8c83989a3098.png)

### **수평선 (Horizontal Rule)**

- 구분선을 생성합니다.

- `- * _` 을 3번 이상 연속으로 작성합니다.

  ```markdown
  ---
  ***
  ___
  ```

  ![https%3A%2F%2Fs3-us-west-2 amazonaws com%2Fsecure notion-static com%2F5eaf7db0-394b-406a-ae1c-c4ebdf52b905%2FUntitled](https://user-images.githubusercontent.com/101630615/177072789-60e06706-ff22-4547-9eb0-8ab011af975c.png)