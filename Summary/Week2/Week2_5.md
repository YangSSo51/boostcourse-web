# Scope

# 5-1.scope란?
- Application 
- Session
- Request
- Page

![scope](https://user-images.githubusercontent.com/48993188/72237104-b7de3a00-361c-11ea-8749-c9ee4650c169.jpg)

- setAttribute(),getAttribute() 메소드를 사용함

# 5-2.page scope
### page scope
- PageContext 추상클래스를 사용
- JSP에서는 pageContext라는 내장 객체로 사용가능
- forward가 될 경우 해당 page scope에 지정된 변수는 사용 불가능
- 지역변수처럼 사용됨
- 하나의 page내에서 사용가능

# 5-3.request scope
### request scope
- http 요청을 WAS가 받아서 웹 브라우저에게 응답할때까지 변수값을 유지하고자하는 경우 사용
- HttpServletRequest객체를 사용함
- JSP에서는 request내장 변수를 사용
- forward시 값을 유지하고자 사용함
- 요청이 들어와서 응답이 나갈 때까지 유지됨

# 5-4.session scope
- 클라이언트마다 상태정보를 유지하기 위해 사용하는 객체
- HttpSession 인터페이스를 구현한 객체 사용
- JSP에서는 session 내장 변수를 사용함
- 서블릿에서는 HttpServletRequest의 getSession()메소드를 이용하여 session객체를 얻어옴

# 5-5.application scope
- 웹 어플리케이션이 시작되고 종료될때까지 변수를 사용가능
- ServletContext 인터페이스를 구현한 객체를 사용함
- JSP에서는 application 내장 객체를 사용함
- 서블릿의 경우 getServletConext()메소드를 이용하여 application 객체를 이용함
- 모든 클라이언트가 공통으로 사용해야할 값이 있을 때 사용함


```java
  ServletContext application = getServletContext();
  int value = 1;
  application.setAttribute("value", value);
  
   try {
      int value = (int)application.getAttribute("value");
      value++;
      application.setAttribute("value", value);
      out.println("<h1>value : " + value + "</h1>");
   }catch(NullPointerException ex) {
      out.println("value가 설정되지 않습니다.");
   }
```

