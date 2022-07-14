# [Spring] 파일 업로드



### 스프링 부트 프로젝트에 파일 업로드

- MultipartFile 클래스 사용
  - 스프링 부트에서는 의존성 라이브러리 추가 필요 없음
  - 자동으로 MultipartConfigElement 클래스를 빈으로 등록
- 업로드되는 파일 크기 제한 변경 가능
  - maxFileSize
    - 업로드하는 파일 1개의 크기 : 디폴트 1M
  - maxRequestSize 
    - 요청 크기 제한
    - 모든 파일의 크기를 합한 크기 값 제한



#### (1) 파일명이 중복되지 않게 해서 업로드 - 1개 파일 업로드

- 동일한 파일명으로 업로드 되는 경우 앞의 파일 덮어쓰게 되는 문제
- 파일명이 중복되지 않도록 파일명을 변경해서 업로드
- UUID : 식별자 표준
  - 16 옥텟(128비트)의 수
  - 총 36개의 문자 (32개 문자와 4개의 하이픈)
  - 자바 UUID 클래스의 randomUUID() 메소드를 사용해서 유일한 식별자 생성



#### (2) 여러 개의 파일 업로드

- fileUploadForm.jsp에 추가
  - ``<input type="file" multiple="multiple">``
- 컨트롤러에 추가 : /fileUploadMultiple
  - ``ArrayList<MultipartFile> files``로 받음
  - ``Model 반환 ArrayList<String>``로 반환
- fileUploadMultipleResult.jsp 생성
  - ``<c:forEach>`` 사용



#### (3) 파일명 변경하지 않고 파일 업로드

- 원본 파일명을 그대로 사용하는 경우
- UUID 사용하지 않음
  - 상품 사진 등록하게 하는 경우
  - 상품번호.jpg 업로드하도록
- fileUploadForm.jsp에 추가





#### 파일 업로드 예제



- 파일 업로드할 폴더 생성
  - springWorkspace 안에 upload 폴더 생성
- 파일 업로드 폼 생성
- views 폴더 안에 upload 폴더 만들고 
  - ``fileUploadForm.jsp``

- 파일 업로드 결과 출력 페이지 생성
  - ``fileUploadResult.jsp``
- 패키지 생성
  - com.spring_boot_mybatis.project 아래에
    - file 패키지 생성
- 컨트롤러 생성
  - ``FileUploadController``
- index에 추가



#### 파일 위치



<img width="309" alt="스크린샷 2022-07-14 오후 8 23 40" src="https://user-images.githubusercontent.com/101630615/178977771-bc43c626-d6f5-41bb-988e-cb4fabfc7cb4.png">





##### 파일 크기 제한 설정

- 1M가 넘는 파일 업로드 시 오류 발생
  - The field uploadFile exceeds its maximum permitted size of 1048576 bytes.
- application.properties 파일에서
  - maxFileSize와 maxRequestSize 크기 설정
    - ``spring.servlet.multipart.max-file-size``
    - ``spring.servlet.multipart.max-request-size``
    - 코드는 버전마다 상이



<img width="559" alt="스크린샷 2022-07-14 오후 8 14 20" src="https://user-images.githubusercontent.com/101630615/178977717-00cf0db5-9fc8-483f-90bc-6a46f0996f77.png">







### File Upload Controller

<hr>

#### 파일 업로드 



<img width="900" alt="스크린샷 2022-07-14 오후 8 21 37" src="https://user-images.githubusercontent.com/101630615/178977761-d56ea4e9-3808-4464-ae54-f204f180cdea.png">





#### 멀티 파일 업로드



<img width="852" alt="스크린샷 2022-07-14 오후 8 21 46" src="https://user-images.githubusercontent.com/101630615/178977765-9574b630-9f16-4ebb-a6d3-2f6227035a0b.png">





#### 파일명 변경하지 않고 파일 업로드



<img width="900" alt="스크린샷 2022-07-14 오후 8 22 01" src="https://user-images.githubusercontent.com/101630615/178977768-0d7ba98e-f328-47a1-a542-1123ac22ab3b.png">





##### 파일 업로드 컨트롤러 소스코드

```java
package com.spring_boot_mybatis.project.file;

import java.io.File;
import java.io.IOException;
import java.util.ArrayList;
import java.util.UUID;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.multipart.MultipartFile;

@Controller
public class FileUploadController {
	// 파일 업로드 폼
	@RequestMapping("/fileUploadForm")
	public String fileUploadFormView() {
		return "upload/fileUploadForm";
	}

	// 파일 업로드
	@RequestMapping("/fileUpload")
	public String fileUpLoadView(@RequestParam("uploadFile") MultipartFile file, Model model) 
				throws IOException {
		
		
		// 1. 파일 저장 경로 설정 : 실제 서비스되는 위치(프로젝트 외부에 저장)
		String uploadPath = "/Library/springWorkspace/upload/";
		// 마지막에 / 있어야함
		
		// 2. 원본 파일 이름 알아오기
		String originalFileName = file.getOriginalFilename();
		
		// 3. 파일 이름이 중복되지 않도록 파일 이름 변경 : 서버에 저장할 이름
		// UUID 클래스 사용
		UUID uuid = UUID.randomUUID();
		String savedFileName = uuid.toString() + "_" + originalFileName;
		
		// 4. 파일 생성
		File newFile = new File(uploadPath + savedFileName);
		
		// 5. 서버로 전송
		file.transferTo(newFile);
		
		// Model 설정 : 뷰 페이지에서 원본 파일 이름 출력
		model.addAttribute("originalFileName", originalFileName);
		
		return "upload/fileUploadResult";
	}
	
	// 멀티 파일 업로드
	@RequestMapping("/fileUploadMultiple")
	public String fileUpLoadView(@RequestParam("uploadFileMulti") ArrayList<MultipartFile> files, 
								Model model) throws IOException {
		
		
		// 1. 파일 저장 경로 설정 : 실제 서비스되는 위치(프로젝트 외부에 저장)
		String uploadPath = "/Library/springWorkspace/upload/";
		// 마지막에 / 있어야함
		
		// 여러 개의 파일 이름 저장할 리스트 생성
		ArrayList<String> originalFileNameList = new ArrayList<String>();
		
		for(MultipartFile file :files) {
			
			// 2. 원본 파일 이름 알아오기
			String originalFileName = file.getOriginalFilename();
			// 파일 이름을 리스트에 추가
			originalFileNameList.add(originalFileName);
			
			// 3. 파일 이름이 중복되지 않도록 파일 이름 변경 : 서버에 저장할 이름
			// UUID 클래스 사용
			UUID uuid = UUID.randomUUID();
			String savedFileName = uuid.toString() + "_" + originalFileName;
			
			// 4. 파일 생성
			File newFile = new File(uploadPath + savedFileName);
			
			// 5. 서버로 전송
			file.transferTo(newFile);
			
			// Model 설정 : 뷰 페이지에서 원본 파일 이름 출력
			model.addAttribute("originalFileNameList", originalFileNameList);
		}
		return "upload/fileUploadMultipleResult";
	}
	
	// 파일명 변경하지 않고 파일 업로드
		@RequestMapping("/fileOriginNameUpload")
		public String fileOriginNameUpLoadView(@RequestParam("uploadFile") MultipartFile file, Model model) 
						throws IOException {
			
			
			// 1. 파일 저장 경로 설정 : 실제 서비스되는 위치(프로젝트 외부에 저장)
			String uploadPath = "/Library/springWorkspace/upload/";
			// 경록 마지막에 "/" 있어야함
			
			// 2. 원본 파일 이름 알아오기
			String originalFileName = file.getOriginalFilename();
			
			// 3. 파일 생성
			File newFile = new File(uploadPath + originalFileName);
	
			// 4. 서버로 전송
			file.transferTo(newFile);
			
			// Model 설정 : 뷰 페이지에서 원본 파일 이름 출력
			model.addAttribute("originalFileName", originalFileName);
			
			return "upload/fileUploadResult";
		}
		
}

```



<hr>



#### 파일 업로드 form.jsp

(컨트롤러에서 출력할 창)

<img width="900" alt="스크린샷 2022-07-14 오후 8 18 12" src="https://user-images.githubusercontent.com/101630615/178977738-e533c55a-d7d5-415f-b3e5-17ad60e3e8e5.png">





##### 파일 업로드 폼 소스코드

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>   
// tag library
<!DOCTYPE html>
<html>
	<head>
	<meta charset="UTF-8">
		<title>파일 업로드 폼</title>
	</head>
	<body>
		<h3>파일 업로드</h3>
		<form id="fileUploadForm" method="post" action="<c:url value='/fileUpload'/>" 
				enctype="multipart/form-data">
			파일 : <input type="file" id="uploadFile" name="uploadFile">		
			<input type="submit" value="업로드">
		</form>
		
		<h3>여러 개의 파일 업로드</h3>
		<form id="fileUploadFormMulti" method="post" 
			action="<c:url value='/fileUploadMultiple'/>" 
								enctype="multipart/form-data">
			파일 : <input type="file" id="uploadFileMulti" name="uploadFileMulti" 					   																		multiple="multiple">
			<input type="submit" value="업로드">
		</form>
		
		<h3>파일명 변경하지 않고 파일 업로드</h3>
		<form id="fileOriginNameUploadForm" method="post" 
			action="<c:url value='/fileOriginNameUpload'/>"
				enctype="multipart/form-data">
			파일 : <input type="file" id="uploadFile" name="uploadFile">		
			<input type="submit" value="업로드">
		</form>

	</body>
</html>
```





<hr>



#### 파일 업로드 결과 폼 



<img width="583" alt="스크린샷 2022-07-14 오후 8 18 58" src="https://user-images.githubusercontent.com/101630615/178977747-23de5784-3250-44b6-a59d-b6f34ada6176.png">



##### 파일 업로드 입력 결과 소스코드

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%> 

<!DOCTYPE html>
<html>
	<head>
	<meta charset="UTF-8">
		<title>파일 업로드 결과</title>
	</head>
	<body>
		${originalFileName } 파일을 업로드 하였습니다.<br>
		/Library/springWorkspace/upload 폴더에서 확인하세요.
	</body>
</html>
```





<hr>



#### 멀티 파일 업로드 결과 폼



<img width="638" alt="스크린샷 2022-07-14 오후 8 19 14" src="https://user-images.githubusercontent.com/101630615/178977750-5b420371-4bce-4a2e-93e3-26b7f40676a2.png">





##### 멀티 파일 업로드 결과 폼 소스코드

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<!DOCTYPE html>
<html>
	<head>
	<meta charset="UTF-8">
		<title>여러 개의 파일 업로드 결과</title>
	</head>
	<body>
	
		${originalFileNameList } 파일을 업로드 하였습니다.<br>
		/Library/springWorkspace/upload 폴더에서 확인하세요.<br><br>
			
		<c:forEach var="file"  items="${originalFileNameList}">
			${file }<br><br>	
		</c:forEach>
	</body>
</html>
```



<hr>



### 파일 다운로드 

- 폴더 내 모든 파일 목록 출력하고
- 목록에서 파일 선택해서 다운로드
- 파일명에 한글 들어 있는 경우 한글 출력 안 됨
  - 다운로드 컨트롤러에서 인코딩 처리

#### 파일 다운로드 예제

- FileDownloadController 생성
- fileDownloadListView.jsp 생성
- index에 추가



#### FileCopyUtils 클래스
파일 및 스트림 복사를 위한 유틸리티 클래스

#### ``FileCopyUtils.copy()``

- 스프링 프레임워크에 내장된 파일 다운로드 기능
- InputStream의 내용을 지정한 OutputStream에 복사하고 스트림을 닫음
  - InputStream/OutputStream
    - 바이트 기반 입/출력 스트림 클래스
- 스트림을 열고, 복사, flush, close 기능 수행



#### 다운로드 컨트롤러에서 인코딩 처리

- ``String encodedFileName = new String (file.getBytes("UTF-8"), "ISO-8859-1");``





#### 파일 다운로드 컨트롤러



<img width="900" alt="스크린샷 2022-07-14 오후 8 51 51" src="https://user-images.githubusercontent.com/101630615/178977774-3988dea0-f5a8-4e1c-bb05-d5ee2731709b.png">



```java
package com.spring_boot_mybatis.project.file;

import java.io.File;
import java.io.FileInputStream;
import java.io.IOException;
import java.io.OutputStream;

import javax.servlet.http.HttpServletResponse;

import org.springframework.stereotype.Controller;
import org.springframework.util.FileCopyUtils;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.servlet.ModelAndView;

@Controller
public class FileDonwloadController {
	
	// 파일 목록 보여주기
	@RequestMapping("/fileDownloadList")
	public ModelAndView fileDownloadList(ModelAndView mv) {
		File path = new File("/Library/springWorkspace/upload/");
		String[] fileList = path.list();
		
		mv.addObject("fileList", fileList);
		mv.setViewName("upload/fileDownloadListView");
		
		return mv;
	}
	
	// 파일 다운로드 
	@RequestMapping("/fileDownload/{file}")
	public void fileDownload(@PathVariable String file, 
								HttpServletResponse response) throws IOException {
		
		File f = new File("/Library/springWorkspace/upload/", file);
		// 파일명 인코딩
		String encodedFileName = new String (file.getBytes("UTF-8"), "ISO-8859-1");

		// file 다운로드 설정
		response.setContentType("application/download");
		response.setContentLength((int)f.length());
		response.setHeader("Content-Disposition", "attatchment;filename=\"" + encodedFileName + "\"");
		
		// 다운로드 시 저장되는 이름은 Response Header의 "Content-Disposition"에 명시
		OutputStream os = response.getOutputStream();
		
		FileInputStream fis = new FileInputStream(f);
		FileCopyUtils.copy(fis, os);
		
		// fis.close();
		// os.close();
		
	}
}
```





#### 파일 다운로드 리스트 폼



<img width="854" alt="스크린샷 2022-07-14 오후 8 19 29" src="https://user-images.githubusercontent.com/101630615/178977754-e55ab897-14ca-4cb3-86b0-fc4e77f9a4e5.png">



##### 파일 다운로드 리스트 폼 소스코드

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<!DOCTYPE html>
<html>
	<head>
	<meta charset="UTF-8">
		<title>파일 다운로드 목록</title>
	</head>
	<body>
		<h3>폴더 내의 모든 파일 목록 출력</h3>
		
		<c:forEach var="file" items="${fileList}">
			<a href="<c:url value='/fileDownload/${file }'/>">${file } 파일 다운로드</a><br><br>
		</c:forEach>
		
	</body>
</html>
```





<hr>



#### 파일 업로드 실행 폼 



![스크린샷 2022-07-14 오후 9 14 16](https://user-images.githubusercontent.com/101630615/178981173-8149b0f6-72ae-4996-bfe8-00034620e90f.png)





#### 파일 업로드 실행 결과 폼



![스크린샷 2022-07-14 오후 9 16 04-7801198](https://user-images.githubusercontent.com/101630615/178981191-58e09306-d622-439b-9cfa-faa68066ef70.png)



##### 파일 업로드 결과



![스크린샷 2022-07-14 오후 9 14 34](https://user-images.githubusercontent.com/101630615/178981234-2dfea63a-f2af-495f-a317-0093f9fff151.png)



##### 멀티 파일 업로드 결과



![스크린샷 2022-07-14 오후 9 15 52-7801117](https://user-images.githubusercontent.com/101630615/178981264-ac46e79f-1304-4f35-8e47-ef51c7a972c5.png)

#####  파일명 변경하지 않고 업로드 결과



![스크린샷 2022-07-14 오후 9 16 10](https://user-images.githubusercontent.com/101630615/178981291-b663975f-4adb-4199-b888-f86ecb1f3cc5.png)





#### 실행 결과



<img width="800" alt="스크린샷 2022-07-14 오후 9 16 18" src="https://user-images.githubusercontent.com/101630615/178981310-f583bf0d-526b-451c-b42e-1e88a752d052.png">





<hr>



#### 파일 다운로드 목록 출력



![스크린샷 2022-07-14 오후 9 20 21](https://user-images.githubusercontent.com/101630615/178981341-3f75b74b-18d6-4271-9f29-dde669556443.png)





##### 클릭 시 파일 다운



![스크린샷 2022-07-14 오후 9 25 02](https://user-images.githubusercontent.com/101630615/178981768-bd3dab29-5741-4f10-b43f-79091fa4ed94.png)
