# CSS
# 1-1. CSS 선언방법

### CSS 선언
selector { property : value; }

### style을 html에 적용하는 방법
1. inline
   - html태그 안에 넣음
    - 구조와 스타일이 섞여있어서 유지보수,관리가 어렵
2. internal
    - head에 style태그로 지정
   - 별도의 css 파일을 관리하지않아도 됨(서버의 요청 줄어듦)
3. external
   - css파일을 include시키는 방식  
   
*우선순위는 위에서부터 부여됨 (같은 속성을 추가하면 inline부터 적용됨)

# 1-2. 상속과 우선순위 결정

### 상속
- 상위에서 적용한 스타일이 하위엘레먼트에도 적용됨
- box-model 속성(width,height,margin,padding,border)와 같이 배치 관련 속성은 상속되지않음

### 우선순위
- inline > internal > external
- 동일한 속성에 대해 정의가 이루어지면 나중의 것이 적용됨
- 구체적으로 표현된 속성이 표현됨 (div > span과 span 이 있다면 전자가 적용됨)
- id > class > element
- css specificity

# 1-3. CSS Selector
: 트리구조로 되어있는 데이터를 빠르게 찾아가는 방법
- tag로 지정
```css
<style>
     span {
       color : red;
     }
 </style>
 ```
 
- id로 지정
```css
<style>
     #spantag {
       color : red;
     }
</style>

<body>
     <span id="spantag"> HELLO World! </span>
</body>
```

- class로 지정
```css
<style>
     .spanClass {
     color : red
     }
</style>

<body>
     <span class="spanClass"> HELLO World! </span>
</body>
```

- id,class 요소 선택자 함께 사용
```css
myid { color : red }
div.myclassname { color : red }
```

- 그룹 선택
```css
h1, span, div { color : red }
h1, span, div#id { color : red }
h1.span, div.classname { color : red }
```

- 자손 요소 선택
```css
#jisu span { color : red }
```
```html
<div id="jisu">
  <div>
    <span> span tag </span>
  </div>
  <span> span tag 2 </span>
</div>
```
- 자식 선택
```css
#jisu > span { color : red }
```
```html
<div id="jisu">
  <div>
    <span> span tag </span>
  </div>
  <span> span tag 2 </span>
</div>
```
- n번째 자식요소 선택
```css
#jisu > p:nth-child(2) { color : red }
```
```html
<div id="jisu">
  <h2>단락 선택</h2>
  <p>첫번째 단락입니다</p>
  <p>두번째 단락입니다</p>
  <p>세번째 단락입니다</p>
  <p>네번째 단락입니다</p>
</div>
```
- nth-of-type : 같은 태그의 n번째를 찾아서 적용  
   예시의 결과는 "두번째 단락입니다"가 red
- nth-child : 태그 상관 없이 n번째를 찾아서 적용(자식태그)  
  예시의 결과는 "첫번째 단락입니다"가 red
  
# 1-4. CSS 기본 Style 변경하기
### font 색상 변경
- color : red;
- color : rgba(255, 0, 0, 0.5);
- color : #ff0000;   //16진수 표기법으로 가장 많이 사용됨

### font 사이즈 변경
- font-size : 16px;
- font-size : 1em;  
  
  *em : 16px이 기본값, 부모의 font-size를 상속받음

### 배경색
- background-color : #ff0;
- background-image, position, repeat 
- background : #0000ff url(“.../gif”) no-repeat center top; //한 줄로 정의도 가능

### 글씨체
- font-family:"Gulim";
- font-family : monospace;

# Element가 배치되는 방법(CSS layout)

### layout
: element를 화면에 배치하는 것(rendering 과정)
- 위에서 아래로 순서대로 블록을 이루며 배치되는 것이 기본

1. display
    - block : 위에서 아래로 쌓이듯이 채워짐
    - inline : 오른쪽으로 채워짐
    - inline-block
2. position
    - static : 순서대로 배치됨
    - absolute : 기준점에 따라서 특별한 위치에 자리함(top/left/right/bottom)  
                 상위 element중에 static이 아닌 position이 기준점(없다면 body가 기준)
    - relative : 원래 자신이 위치해야할 곳을 기준으로 이동
    - fixed : 전체화면 좌측,맨위를 기준으로 동작(scroll로 이동해도 고정)
3. float
    - flow에서 벗어날 수 있고 떠다닐 수 있음
    - block element는 float element를 인식하지 못하고 중첩되어서 배치됨
4. margin
    - 배치를 다르게 해줌
    
5. box 모델
    - margin : element 간의 간격(시계방향으로 설정)
    - border : 테두리
    - padding : element 내의 간격  
                padding값을 늘리면 element크기가 커질 수 있음

* element의 크기는 부모의 크기가 기본

### layout 구현 방법
- float을 사용해서 컬럼 배치를 구현
- css-grid나 flex속성 사용
- 특별한 배치를 위해서는 position absolute 사용
- 네비게이션같은 엘리먼트는 inline-block으로 변경해서 가로로 배치하기도 함
- 엘리먼트안의 텍스트 간격,다른 엘리먼트 간의 간격은 padding과 margin속성을 활용해서 위치
