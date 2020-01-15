# JSTL & EL

# 6-1.EL(Experssion Language)

### EL
- 표현 언어는 값을 표현하는데 사용되는 스크립트 언어
- JSP의 기본 문법으 보완하는 역할

#### 기능
- JSP의 scope에 맞는 속성 사용
- 집합 객체에 대한 접근 방법 제공
- 수치 연산,관계 연산,논리 연산자 제공
- 자바 클래스 메소드 호출 기능 제공
- 표현 언어만의 기본 객체 제공

### 문법
``` EL
${expr}
```
![EL](https://user-images.githubusercontent.com/48993188/72408453-56e26d80-37a6-11ea-99bc-9ba98e386213.png)

### 데이터 타입
- Boolean 타입
- 정수타입
- 실수타입
- 문자열 타입
- null 타입

### 객체 접근 규칙
```
  ${<표현1>.<표현2>}
```
- 표현 1이나 2가 null이면 null 반환
- 표현 1이 Map일 경우 표현2를 key로 한 값을 반환
- 표현 1이 List나 배열이면 표현2가 정수일 경우 정수번째 index에 해당하는 값 반환
- 표현 1이 객체일 경우 표현2에 해당하는 getter메소드가 호출한 결과를 반환

### 수치 연산자
- +
- -
- *
- / 또는 div
- % 또는 mod

### 비교 연산자
- == 또는 eq
- != 또는 ne
- < 또는 lt
- > 또는 gt
- <= 또는 le
- >= 또는 ge
- 문자열 비교 : ${str=='값'} str.compareTo("값")==0

### 논리 연산자
- && 또는 and
- || 또는 or
- ! 또는 not

### empty 연산자
```
empty<값> // null,"",길이 0인 배열,빈 map,빈 collection이면 true리턴

### EL 비활성화
```jsp
<%@ page isELIgnored = "true" %>
```

```jsp
<%
    pageContext.setAttribute("p1", "page scope value");
    request.setAttribute("r1", "request scope value");
    session.setAttribute("s1", "session scope value");
    application.setAttribute("a1", "application scope value");
%>    

pageContext.getAttribute("p1") : ${pageScope.p1 }<br>
request.getAttribute("r1") : ${requestScope.r1 }<br>
session.getAttribute("s1") : ${sessionScope.s1 }<br>
application.getAttribute("a1") : ${applicationScope.a1 }<br>
<br><br>
pageContext.getAttribute("p1") : ${p1 }<br>
request.getAttribute("r1") : ${r1 }<br>
session.getAttribute("s1") : ${s1 }<br>
application.getAttribute("a1") : ${a1 }<br>
```

```jsp
k : ${k } <br>
k + 5 : ${ k + 5 } <br>
k - 5 : ${ k - 5 } <br>
k * 5 : ${ k * 5 } <br>
k / 5 : ${ k div 5 } <br>


k : ${k }<br>
m : ${m }<br>
k > 5 : ${ k > 5 } <br>
k < 5 : ${ k < 5 } <br>
k <= 10 : ${ k <= 10} <br>
k >= 10 : ${ k >= 10 } <br>
m : ${ m } <br>
!m : ${ !m } <br>
```

# 6-2. JSTL(JSP Standard Tag Library)

### JSTL
- JSP페이지에서 조건문 처리,반복문 처리 등을 html tag형태로 작성할 수 있게 도와줌
- [jstl 다운로드](http://tomcat.apache.org/download-taglibs.cgi)
- WebContent/WEB-INF-lib 밑에 jar 파일 3개 넣어줌

![jstl](https://user-images.githubusercontent.com/48993188/72408481-72e60f00-37a6-11ea-98a5-e6882fa17d8d.png)
![core](https://user-images.githubusercontent.com/48993188/72408493-7aa5b380-37a6-11ea-8647-04d1cf4349ca.png)

### 문법
```jsp
<c:set var = "varName" scope = "session" value = "someValue"/>
${varName}<br>
<c:remove var = "varName" scope = "session"/>
```

### 변수 지원 태그
```jsp
<c:set target = "${some}" property = "propertyName" value = "anyValue"/>
// some 객체가 자바빈일 경우 some.setPropertyName(anyvalue)
// some 객체가 맵일 경우 some.put(propertyName.anyvalue);
```

### 흐름제어 태그
```jsp
<c:if test="조건">
</c:if>

<c:choose>
  <c:when test = "조건1">
  </c:when>
  <c:when test = "조건2">
  </c:/when>
</c:chooes>
``` 

### 흐름제어 태그
```jsp
//forEach
<c:forEach var = "변수" items = "아이템" [begin = "시작번호"][end = "끝번호"]>
${변수}
</c:forEach>

//import
<c:import url = "URL" charEncoding = "인코딩" var = "변수명" scope = "범위">
  <c:param name = "파라미터이름" value = "파라미터값"/>  //url 뒤에 쿼리문 넣는 부분
</c:import>

//redirect
<c:redirect url = "리다이렉트할 URL">
  <c:param name = "파라미터 이름" value = "파라미터값"/>
</c:redirect>

### 기타태그 
```jsp
<c:out value = "value" escapeXml = "{true|false}" default = "defaultValue"/>
```



