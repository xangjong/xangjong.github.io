# [Spring] CRUD 기능 구현 



### 클래스 구성

#### (1) 패키지 생성

-	controller
-	dao
-	model
-	service

#### (2) 클래스 및 인터페이스 생성 : 해당 패키지 안에 생성

-	ProductVO 클래스
-	IProductService 인터페이스 / Product 클래스
-	``import org.springframework.stereotype.Service;``
-	IProductDAO 인터페이스
  -	MyBatis에서는 DAO 인터페이스 필수
-	ProductMapper.xml 생성
  -	application-config.xml에 dao 패키지 추가
  -	``<mybatis-spring:scan base-package="com.spring_mvc.mybatis.dao"/>``
-	ProductController 클래스 생성
-	views 폴더에 index.jsp 생성
-	ProductController 
  -	인덱스 페이지 열기 요청 처리
-	기본 생성된 HomeController와 home.jsp 삭제
-	실행 시켜서 index 페이지 열리는지 확인



<hr>



### CRUD 기능 구현 예제
#### (1) 전체 상품 조회 (SELECT)

- ProductController에서 요청 받아서

- ProductService 클래스의 listAllProduct() 메소드 호출

- IProductDAO의 listAllProduct() 메소드 호출

  -	ProductMapper에서 SQL 처리하고 결과 반환

- ProductService에서 받아서 ProductController에게 반환

- ProductController에서 View 페이지로 전달

- 화면에 결과 출력

- 요청 -> 컨 -> 서비스 -> DAO -> Mapper -> 서비스 -> 컨 -> 뷰

  

- (1) ProductController

- (2) ProductService  -> dao

- (3) ProductMapper : ``<select>``

- (4) views 폴더에 product 폴더 만들고 productAllListView.jsp 생성

  -	``<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>``
  -	``<c:forEach>`` 사용해서 테이블 형태로 출력




#### (2) 상품 등록 (INSERT)

-	(1) 상품 등록 폼 생성 : productNewForm.jsp
-	컨트롤러
  -	상품 등록 폼 열기 요청 처리
    -	컨 -> 뷰 페이지

  -	입력된 내용 insert 처리
    -	컨 -> 서비스 -> DAO -> Mapper -> 서비스 -> 컨 -> 뷰


#### (3) 상품 상세 정보 조회

-	상품번호 클릭하면 상품 상세 정보 조회 화면으로 이동
-	상품번호에 링크 설정
-	``<a href="<c:url value='/product/productDetailView/${prd.prdNo}'/>"> ${prd.prdNo }</a>``
-	컨트롤러에서 @PathVariable로 전달 받음
-	서비스 : ``detailViewProduct()``
-	dao -> Mapper : detailViewProduct
-	결과 : productDetailView.jsp  

#### (4) 상품 정보 수정 (UPDATE)

-	상품 상세 정보 조회에서 상품 정보 수정 요청
-	상품 정보 수정 폼에 데이터 출력 / 수정
  -	productUpdateForm.jsp
  -	컨트롤러에서 detailViewProduct() 결과를 폼에 출력
  -	수정
  -	컨트롤러에게 저장 요청

-	컨트롤러 수정 요청 처리
  -	-> 서비스 -> DAO -> Mapper
  -	전체 상품 조회 화면으로 포워딩


#### (5) 상품 정보 삭제

-	상품 상세 정보 조회에서 상품 정보 삭제 요청
-	삭제 확인 메시지 출력
  -	[삭제] 클릭 했을 때 바로 삭제하지 않고, “삭제하시겠습니까” confirm 창으로 출력하고 [확인] 버튼 누르는 경우에만 삭제 : 자바스크립트
-	자바스크립트 컨트롤러에게 요청
  -	``location.href="/mybatis/product/deleteProduct/${prd.prdNo}";``



***redirect 주의!***

-	``return "redirect:./productAllList";`` 했을 경우 redirect 횟수가 많다는 오류 발생 시
-	``return "redirect:/product/productAllList";`` 로 사용



<hr>



### 이미지 출력

-	이미지 저장
  -	프로젝트 내부에 저장하는 경우
    -	webapp / resources 폴더 안에 저장
    -	프로젝트에서 사용하는 이미지
    -	ervlet-conext.xml의 ``<resources>``에서 mapping  이름 변경 가능
    -	``<resources mapping="/img/**"  location="/resources/image/" />``

  -	프로젝트 외부에 저장하는 경우
    -	상품 이미지 (대량의 이미지)
    -	외부 폴더에 저장하고
    -	외부 폴더에 접근할 수 있도록 설정 필요
    -	servlet-conext.xml의 ``<resources>``에 location 지정




프로젝트 외부에 저장 예제

-	(1) springWorkspace 폴더에 product_images 폴더 생성하고 이미지 저장
-	(2) servlet-conext.xml의 ``<resources>``에 location 지정

```
<resources mapping="/images/**"  location="file:///C:/springWorkspace/product_images/" />
```



-	(3) productListView.jsp에 이미지 출력

```
<img src="<c:url value='/images/${prd.prdNo}.png' />"  width="30" height="20">
```

