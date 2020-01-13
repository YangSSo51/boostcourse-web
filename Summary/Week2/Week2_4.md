# Redirect & forward

# 4-1. redirect

### redirect
- http프로토콜로 정해진 규칙
- 서버가 클라이언트의 요청을 받은 후 특정 URL로 이동하라고 요청할 수 있음
- 서버->클라이언트 : Location 헤더(상태코드 302,URL정보) 전송
- 클라이언트는 상태코드가 302이면 Location헤더값으로 재요청을 보내서 전송받은 URL로 가게됨
- jsp는 HttpServletResponse가 가지고 있는 sendRedirect()메소드를 사용

```jsp
<%
    response.sendRedirect("redirect02.jsp");
%> 
```

# 4-2.forward
1. 웹 브라우저에서 Servlet1에게 요청을 보냄
2. Servlet1은 요청을 처리한 후 그 결과를 __HttpServletRequest__ 에 저장
3. Servlet1은 결과가 저장된 HttpServletRequest와 응답을 위한 HttpServletResponse를 Servlet2에게 전송(forwoard)
4. Servlet2는 HttpServletRequest와 HttpServletResponse를 이용하여 요청을 처리한 후 결과 전송

* forward가 실행된 뒤에는 url이 바뀌지않음!
* 같은 웹 어플리케이션 내에서만 가능하고 경로는 "/"로 시작해야함

- request객체에 값 설정하고 forward하는 방법
```java
  request.setAttribute("dice", diceValue);
            
  RequestDispatcher requestDispatehcer = request.getRequestDispatcher("/next");
  requestDispatehcer.forward(request, response);
```

- request객체에서 값 가져오는 방법
```java
  int dice = (Integer)request.getAttribute("dice");
```

### redirect와 forward 차이점

redirect | forward
:---:|:---:|
클라이언트가 서버에 요청보내면 서버는 새로운 요청주소를 알려줌 | 다른 back에게 처리를 맡김
url이 변경됨 | url이 변경되지않음
요청이 2번 이뤄짐 | request,response객체가 한번 만들어짐

# 4-3. servlet & jsp연동

servlet | jsp 
:---:| :---:
프로그램 로직이 수행되기에 유리 | 결과를 출력하기에 유리
자바코드 사용 | html 사용

* Servlet에서 프로그램 로직을 수행시키고 결과는 forward를 통해 jsp에서 출력
