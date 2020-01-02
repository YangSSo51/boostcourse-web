# 1-1. 웹 프로그래밍을 위한 프로그램 언어들

#### 웹 관련 인기 언어

- Python : 프로그래밍 입문자가 읽기 쉽고 적은 코드를 사용하여 프로그램을 개발할 수 있습니다. 많은 사람에게 추천되는 언어이며, 
            데이터 과학에서도 자주 사용되며 웹사이트 개발에서도 많이 사용되고 있습니다.
- PHP : 웹의 80% 이상이 PHP로 만들어졌다고 말합니다. 그만큼 PHP는 웹 개발에서 많이 사용됩니다. 
- __JavaScript__ : 자바 스크립트는 처음 시작이 브라우저에서 동작하는 언어였습니다. 현재는 서버에서도 작성하는 프로그램으로 점차 영역을 넓혀가고 있습니다.                프론트 개발자라면 반드시 알아야 할 언어입니다. 자바스크립트 커뮤니티도 점점 더 거대해지고 있습니다.
- __JAVA__ : 엔터프라이즈 소프트웨어 환경에 잘 맞는 언어입니다. 큰 규모의 소프트웨어 개발에 자바언어가 많이 사용되고 있습니다. 
         JAVA언어를 지원하는 수많은 커뮤니티에 위해서, 지속적으로 발전되어 훌륭한 구조와 설계 기법들이 잘 갖춰져 있습니다.
- Ruby : 빠른 개발에 널리 사용되며, 단순함과 세련된 웹 어플리케이션을 만들 수 있기 때문에 인기 있는 언어 중의 하나입니다.

#### 생각해보기

1. 프론트 엔드부터 서버 개발까지 한 가지 프로그래밍 언어를 사용하여 개발한다면 어떤 언어를 사용하는 것이 좋을까요?  
     JavaScript
2. 다양한 라이브러리, 쉬운 개발, 읽기 쉽고 적은 코드를 장점으로 한다면 어떤 언어를 사용하는 것이 좋을까요?  
     Python
3. 프로그래밍 언어에게 좋은 커뮤니티가 있다는 것은 어떤 장점을 가질까요?  
      오류해결이 용이하고 더 나은 코드를 탐색할 수 있다

# 1-2. 웹의 동작(HTTP 프로토콜 이해)
#### 인터넷 
- TCP/IP기반의 네트워크 결합체
#### HTTP 
- 서버와 클라이언트가 인터넷상에서 데이터를 주고받기 위한 프로토콜
- 클라이언트가 요청을 보내면 서버가 응답을 보내줌
##### 장점
 - 불특정 다수를 대상으로 하는 서비스에 적합함
 - stateless하기 때문에 최대 연결수보다 훨씬 많은 요청과 응답 처리 가능
##### 단점
 - 서버는 응답을 보내고 연결을 끊기 때문에 클라이언트의 이전상황을 알 수 없음
 - 이러한 특징 때문에 쿠키와 같은 기술이 등장함
#### URL(Uniform Resource Locator)
- 인터넷 상의 자원 위치
- 접근 프로토콜://IP 주소 or 도메인 주소(물리적 컴퓨터)/문서의 경로/문서이름
#### HTTP 
![http](https://user-images.githubusercontent.com/48993188/71652705-acf8ef00-2d6a-11ea-8688-2b017c89a594.png)
1. 클라이언트가 서버에 접속 (Connect)
2. 클라이언트가 서버에게 요청 (Request)
    - 요청 헤더 : 요청 메소드/요청 URI/HTTP 프로토콜 버전
3. 서버가 클라이언트에게 응답 (Response)
    - 응답 헤더 : HTTP 프로토콜 버전/응답메세지
    - 응답 바디 : 실제 내용

##### 요청 메소드
- GET : 정보 요청
- POST : 정보 삽입
- PUT : 정보 업데이트
- DELETE : 정보 삭제
- HEAD : HTTP 헤더 정보만 요청, 해당 자원 존재여부,서버의 문제발생여부 확인
- OPTIONS : 웹서버가 지원하는 메서드의 종류를 요청
- TRACE : 클라이언트의 요청 반환

#### 생각해보기
1. HTTP에 S가 붙은 HTTPS 는 어떤 용도로 사용되는 건가요? HTTP와 무엇이 다른가요?  
   HTTP에 보안적인 요소가 추가된 것이다

# 1-3. 웹Front-End와 웹 Back-End
#### 웹 Front-End
- 사용자에게 웹을 통해 다양한 콘텐츠(문서, 동영상, 사진 등)를 제공  
- 또한, 사용자의 요청(요구사항)에 반응해서 동작
##### 역할
- 웹 콘텐츠를 잘 보여주기 위한 __구조__ (HTML)
- 적절한 배치와 __디자인__ 제공 (CSS)
- 사용자 요청을 잘 반영하여 __동작__ 해야함 (JavaScript)
#### 웹 Back-End
- 클라이언트의 요청에 대한 응답을 전달해줘야함
##### 백엔드 개발자가 알아야할 것들
- 프로그래밍 언어(JAVA,Python,PHP,JavaScript)
- 웹 동작 원리
- 알고리즘,자료구조 등 프로그래밍 기반 지식
- 운영체제,네트워크 등에 대한 이해
- 프레임워크에 대한 이해 
- DBMS에 대한 이해와 사용방법

# 1-4. Browser의 동작
[브라우저 동작](https://www.html5rocks.com/en/tutorials/internals/howbrowserswork/)
#### Browser Components
![Browser components](https://user-images.githubusercontent.com/48993188/71653506-1deed580-2d70-11ea-8656-426425927c9c.png)
1. User Interface
2. Browser Engine
3. Rendering Engine
4. Data Persistence
5. Networking module
6. JavaScript interpreter
7. UI Backend
#### Rendering engine
![rendering engine](https://user-images.githubusercontent.com/48993188/71653487-0ca5c900-2d70-11ea-9d94-1933a949773e.png)

#### Webkit flow (브라우저에서 렌더링엔진 처리과정)
![webkit flow](https://user-images.githubusercontent.com/48993188/71653466-ef70fa80-2d6f-11ea-85dc-236cb4987861.png)
- HTML을 DOM 트리로 parsing
- CSS 정보를 Parsing
- Dom Tree와 Sytle Rules을 attach -> Render Tree (객체)
- layout이 결정되고 painting하고 display해줌

#### HTML Parse
```html
<html>
  <body>
    <p>
      Hello World
    </p>
    <div> <img src="example.png"/></div>
  </body>
</html>
```
![dom tree](https://user-images.githubusercontent.com/48993188/71653867-07497e00-2d72-11ea-8b7e-cdebe4ea6b5d.png)
#### CSS Parse
![css parse](https://user-images.githubusercontent.com/48993188/71653881-17f9f400-2d72-11ea-8654-624bba963349.png)  
selector : declaration

#### 생각해보기
1. 우리가 흔히 브라우저 탐색을 할 때 스크롤을 하거나, 어떤 것을 클릭하면서 화면의 위치를 바꿀 때, 브라우저는 어떻게 다시 화면을 그릴까요?  
변화된 부분에 대해서만 repainting이 일어날 것이다
2. 위에서 표현된 그림처럼 다시 렌더링 되지 않을까요?  
계속 렌더링 되는 것은 비효율적이다

# 1-5. Browser에서의 웹 개발
- Ctrl+Shift+i 로 개발자도구 사용
- HTML문서는 html태그로 시작해서 html태그로 끝남
- head는 html문서에 대한 추가적인 설명을 포함
- HTML은 계층적이고 tag를 사용해서 표현함  

- style태그는 head부분에 넣거나 다른 문서로 작성
- script태그는 body 뒤에 넣는게 좋음 (html로딩 속도에 영향을 줄 수 있기 때문)
```html
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>저를소개해요</title>
    <link rel="stylesheet" href="css/style.css">
    <script src="js/start.js"></script>
  </head>
  <body>
    <h1>안녕하세요</h1>
    <div>양소영이예요</div>
    <script src="js/library.js"></script>
    <script src="js/main.js"></script>
  </body>
</html>
```
[JS bin](https://jsbin.com/?html,js,console,output)
