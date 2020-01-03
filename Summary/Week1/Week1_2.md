# HTML
# 1-1. HTML Tags

### HTML Tags
: html은 semantic한 태그다 (각각의 쓰임새에 따른 의미를 가짐)
- 링크
- 이미지
- 목록
- 제목

#### 예시
- div : 영역 표현
- ul : 순서없는 리스트
- li : 각각의 리스트 내용
- a : hyperlink로 연결

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JS Bin</title>
</head>
<body>
  <div>
    <h1>반갑습니다</h1>
    여기 여러분들이 좋아하는 과일이 있어요.
    <ul>
      <li><a href="http://www.apple.com">사과</a></li>
      <li>사과</li>
      <li>메론</li>
      <li>귤</li>
    </ul>
  </div>
</body>
</html>
```

# 1-2. HTML Layout 태그

### 레이아웃
: html 화면을 구성하는 모습  
![layout tag](https://user-images.githubusercontent.com/48993188/71709881-f3b71980-2e3c-11ea-9a71-2dbf121813db.jpg)
- header
- section
- nav
- footer
- aside 

# 1-3. HTML 구조 설계
```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JS Bin</title>
</head>
<body>
  <header>
  <h1>Company Name</h1>
  <img src="..." alt="logo">
  </header>
  
  <div>  <!-- section태그를 사용했었지만, 별 의미없는 container에는 section태그가 적절하지 않아서 수정합니다 -->
    <nav><ul>
      <li>Home</li>
      <li>Home</li>
      <li>About</li>
      <li>Map</li>
      </ul></nav>
    
    <div>  
      <button></button>
      <div><img src="dd" alt=""></div>
      <div><img src="dd" alt=""></div>
      <div><img src="dd" alt=""></div>
      <button></button>
    </div>
    <div>
      <ul>
        <li>
          <h3>What we do</h3>
          <div>Lorem ipsum dolor sit amet, consectetur adipisicing</div>
        </li>
        <li>
          <h3>What we do</h3>
          <div>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Similique accusamus, corporis, dolorum fugiat tenetur porro. Aspernatur commodi, ea suscipit non? Molestiae nulla explicabo debitis provident nostrum dolorem minima reiciendis suscipit?</div>
        </li>
        <li>
          <h3>What we do</h3>
          <div>Lorem ipsum dolor sit amet, consectetur adipisicing</div>
        </li>
      </ul>
    </div>
  </div>
  <footer>
    <span>Copyright @codesquad</span>
  </footer>
</body>
</html>
```
# 1-4. class와 id 속성
### id 
- 고유한 속성
- id로 쉽게 찾을 수 있음
### class 
- 중복해서 여러군데 같이 사용
- 동일한 css를 적용시킬 수 있음

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JS Bin</title>
</head>
<body>
  <header>
  <h1>Company Name</h1>
  <img src="..." alt="logo">
  </header>
  
  <section id="nav-section">
    <nav><ul>
      <li>Home</li>
      <li>Home</li>
      <li>About</li>
      <li>Map</li>
      </ul>
    </nav>
    
    <section id="roll-section">
      <button></button>
      <div><img src="dd" alt=""></div>
      <div><img src="dd" alt=""></div>
      <div><img src="dd" alt=""></div>
      <button></button>
    </section>
    <section>
      <ul>
        <li class="our_diescriptipn">
          <h3>What we do</h3>
          <div>Lorem ipsum dolor sit amet, consectetur adipisicing</div>
        </li>
        <li class="our_diescriptipn">
          <h3>What we do</h3>
          <div>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Similique accusamus, corporis, dolorum fugiat tenetur porro. Aspernatur commodi, ea suscipit non? Molestiae nulla explicabo debitis provident nostrum dolorem minima reiciendis suscipit?</div>
        </li>
        <li class="our_diescriptipn">
          <h3>What we do</h3>
          <div>Lorem ipsum dolor sit amet, consectetur adipisicing</div>
        </li>
      </ul>
    </section>
  </section>
  <footer>
    <span>Copyright @codesquad</span>
  </footer>
</body>
</html>
```

#### BEM 방식으로 클래스 이름 짓기 
- Block-Element-Modifier  
예) header__navigation--secondary  
[BEM방식](https://webclub.tistory.com/263)

