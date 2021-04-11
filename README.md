# egov_test
egov_test 버전 


### 1. 정적인 페이지는 생성 되지만, 데이터베이스 값은 가져와 지지않음
dispathcher-servelet, context-mapper
 <mvc:view-controller path="/main.do" view-name="main"/>

### 2. jsp위치 수정
<bean class="org.springframework.web.servlet.view.UrlBasedViewResolver" p:order="1"
	    p:viewClass="org.springframework.web.servlet.view.JstlView"
	    p:prefix="/WEB-INF/jsp/" p:suffix=".jsp"/>

### 3. 매퍼 패키지로 수정
<bean class="egovframework.rte.psl.dataaccess.mapper.MapperConfigurer">

### 4. 따로 DAO를 만들 필요가 없었다. 
context-mapper에 mapper위치를 이미 지정해놓고 어노테이션으로 boardMapper클래스 지정해놓음

### 5. 쿼리스트링으로 delete update구현

### 6. 한글 깨짐 현상
### -고친것-
1) 톰캣 서버:<Connector URIEncoding="euc-kr"~>
2) DB 수정: ALTER TABLE board_tb convert to charset utf8;
3) var board_id=${board_id}에서 =>
var board_id='<c:out value="${board_id}"/>';

### 7. css적용문제

<link rel="stylesheet" type="text/css" href="./resources/css/form.css">

### 8. 정리
1) context-datasource : 디비 name , pw
2) context-mapper: mapper위치
3) context-common: context:component-scan 위치
4) WEB-INF/config~/springmvc/dispatcher-servlet.xml: p:prefix="/WEB-INF/jsp/" p:suffix=".jsp"/> 위치 지정
