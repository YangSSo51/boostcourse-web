# Servelet

# 5-1. Servlet 이란?

### 자바 웹 어플리케이션

- WAS에 설치(deploy)되어 동작하는 어플리케이션
- HTML,CSS,이미지,자바클래스,각종 설정 파일 등이 포함됨

#### 폴더구조
- WEB-INF
  - web.xml : 배포기술자, 애플리케이션 정보를 가지고있음
  - lib : jar파일들
  - classes : java 패키지,class
- 각종 폴더,이미지,다양한 리소스

### 서블릿
- 자바 웹 어플리케이션의 우성요소 중 동적인 처리를 하는 프로그램
- WAS에서 동작하는 자바 클래스
- HttpServlet 클래스를 상속받아야함
- 서블릿과 JSP를 조화롭게 사용해야함

# 5-2. Servlet 작성 방법

### 서블릿 작성 방법
1. servlet 3.0 spec 이상
  - web.xml파일을 사용하지않음
  - 자바 어노테이션을 사용
2. servlet 30. spec 미만
  - servlet을 등록할 때 web.xml 파일에 등록
  - url-pattern에서 url 변경가능

# 5-3. Servlet 라이프 싸이클

### 서블릿 생명주기
- WAS는 서블릿 요청을 받으면 해당 서블릿이 메모리에 있는지 확인
- 메모리에 없으면 서블릿 클래스를 메모리에 올림 (객체 생성)
- init()메소드 실행
- service()메소드 실행 : 응답에 대한 내용
- destroy()메소드 실행:웹 애플리케이션 갱신 or WAS가 종료될 때 호출 

### service 메소드
- HttpServlet의 service()메소드가 호출됨
- 템플릿 메소드 패턴으로 구현되어있음 
  - 클라이언트 요청이 get이면 doGet() 호출
  - 클라이언트 요청이 post이면 doPost() 호출

#. 5-4 Resquest,Response 객체 이해하기

### 요청과 응답
![request_response](https://user-images.githubusercontent.com/48993188/71802869-7b519200-30a2-11ea-80ee-8ce3efd5cbf5.png)
- 클라이언트로부터 요청이 들어오면 WAS에서 HttpServletRequest,HttpServletResponse 객체 생성
- HttpServletRequest : 요청할 때 가지고 들어온 정보들, request정보 서블릿에게 전달
- HttpServletResponse : 정보를 담을 수 있는 객체에 생성
- 요청 정보에 있는 path로 매핑된 서블릿에 두 개의 객체 전달

### 헤더정보
```java
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		response.setContentType("text/html");
		PrintWriter out = response.getWriter();
		out.println("<html>");
		out.println("<head><title>form</title></head>");
		out.println("<body>");

		Enumeration<String> headerNames = request.getHeaderNames();
		while(headerNames.hasMoreElements()) {
			String headerName = headerNames.nextElement();
			String headerValue = request.getHeader(headerName);
			out.println(headerName + " : " + headerValue + " <br> ");
		}		
		
		out.println("</body>");
		out.println("</html>");
	}
```
### 요청 파라미터
```java
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		response.setContentType("text/html");
		PrintWriter out = response.getWriter();
		out.println("<html>");
		out.println("<head><title>form</title></head>");
		out.println("<body>");

		String name = request.getParameter("name");
		String age = request.getParameter("age");
		
		out.println("name : " + name + "<br>");
		out.println("age : " +age + "<br>");
		
		out.println("</body>");
		out.println("</html>");
	}
  ```
