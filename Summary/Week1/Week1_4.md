# 개발환경 설정

- 프로젝트 생성  
file > new > Java Project

- WAS url 규칙  
http:// localhost:8080 / {프로젝트이름}/ {URL Mapping 값}

- doGet
```java
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		response.setContentType("text/html;charset=UTF-8");
		PrintWriter out = response.getWriter();
		out.println("<h1>Hello World</h1>");
	}
```
