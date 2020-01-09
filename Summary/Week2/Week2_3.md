# JSP

# 3-1. JSP
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>sum10</title>
</head>
<body>

<% 
    int total = 0;
    for(int i = 1; i <= 10; i++){
        total = total + i;
    }
%>

1부터 10까지의 합 : <%=total %>

</body>
</html>
```

# 3-2.JSP 라이프싸이클
- JSP는 톰캣에 의해 서블릿으로 바뀜
- workspace/.metadata/sum10_jsp.java 파일이 생성됨
- _jspService() 메소드안에 jsp파일의 내용이 변환되어서 들어감

### JSP 실행 순서
1. 브라우저가 웹서버에 JSP에 대한 요청 정보 전달
2. 브라우저가 요청한 JSP가 최초로 요청했을 경우만
  1. JSP로 작성된 코드가 서블릿 코드로(java)로 변환됨
  2. 서블릿 코드를 컴파일해서 실행가능한 bytecode(class)로 변환됨
  3. 서블릿 클래스를 로딩하고 인스턴스를 생성한다
3. 서블릿이 실행되어 요청을 처리하고 응답정보를 생성함

- JSP
```jsp
<%
int total = 0;
for(int i = 1; i <= 10; i++){
    total = total + i;
}
%>
<%= total %>
```
- java
```java
public void _jspInit() {
  }

  public void _jspDestroy() {
  }

  public void _jspService(final javax.servlet.http.HttpServletRequest request, final javax.servlet.http.HttpServletResponse response)
      throws java.io.IOException, javax.servlet.ServletException {

    .....

    try {
      .....

      out.write("\n");
      out.write("<!DOCTYPE html PUBLIC \"-//W3C//DTD HTML 4.01 Transitional//EN\" \"http://www.w3.org/TR/html4/loose.dtd\">\n");
      out.write("<html>\n");
      out.write("<head>\n");
      out.write("<meta http-equiv=\"Content-Type\" content=\"text/html; charset=UTF-8\">\n");
      out.write("<title>sum10</title>\n");
      out.write("</head>\n");
      out.write("<body>\n");
      out.write("\n");

	int total = 0;
	for(int i = 1; i <= 10; i++){
		total = total + i;
	}

      out.write("\n");
      out.write("\n");
      out.write("1부터 10까지의 합 : ");
      out.print(total );
      out.write("\n");
      out.write("\n");
      out.write("</body>\n");
      out.write("</html>");
    } catch (java.lang.Throwable t) {
      .....
      }
    } finally {
      _jspxFactory.releasePageContext(_jspx_page_context);
    }
  }
  ```
  
  - 선언식(<%! %>)을 이용하여 메소드를 정의하면 서비스 메서드 밖에 포함됨
  
  ```jsp
<%
	System.out.println("_jspService()");
%>

<%!
public void jspInit() {
	System.out.println("jspInit()!");
}

public void jspDestroy() {
	System.out.println("jspDestroy()");
}
%>
```

# 3-3. JSP 문법
### 선언문
- <%! %>
- 전역변수 선언 및 메소드 선언에 사용
```jsp
id : <%=getId() %>
<%!
    String id = "u001"; //멤버변수 선언
    public String getId( ) { //메소드 선언
        return id;
    }
%>
```
### 스크립트릿
- <% %>
- 프로그래밍 코드 기술에 사용
- 스크립트릿 안에 선언되는 변수는 지역변수
```jsp
<%
for(int i = 1; i <= 5; i++){
%>
<H<%=i %>> 아름다운 한글 </H<%=i %>>
<%
}
%>
```
### 표현식
- <%= %>
- 화면에 출력할 내용 기술에 사용

### 주석
- html 주석 : <!-- --> , 웹에서 서비스할때는 표시되지않고 소스보기에만 표시
- JSP 주석 : <%-- --%> , 웹에서 표시되지않음(소스 보기에도 없음)
- java 주석 : //,/**/,서블릿으로 실행할때 실행되지않음

jsp 주석 > java 주석 > html 주석

# 3-4. JSP 내장객체
- _jspService() 윗 부분에 미리 선언된 객체로 jsp에서도 사용이 가능함
- response,request,application,session,out
![jsp](https://user-images.githubusercontent.com/48993188/72047221-63297f00-32fd-11ea-95d0-a56d90bf7a18.png)

