# 3-1. 반응형 웹 소개

### 반응형 웹

- 디스플레이 종류에 따라 크기가 자동으로 최적화되도록 조절하는 웹페이지
- 하나의 소스로 관리하고 유지보수에 용이

### 살펴보기
- 개발자도구를 사용해서 웹 관찰하기
- 모바일로 화면이 어떻게 보이는지 확인할 수 


# 1-2. 반응형 웹-제작 가이드
- HTML : div,header,footer,nav,section
- CSS : 미디어쿼리의 특성(사이즈별 조건을 줌)

### html
```html
<html>
  <head>
  	<meta charset="utf-8">
		<meta name="viewport" content="width==device-width, initial-scale=1.0">
  </head>
  <body>
    <div class="wrap">  
      <header>
        <a href="#" class="logo"><h1>Logo</h1></a>
        <nav>
          <a href="#">Menu1</a>
          <a href="#">Menu2</a>
          <a href="#">Menu3</a>
          <a href="#">Menu4</a>
        </nav>
      </header>
      <section>
        <ul class="list">
          <li>
            <a href="#" class="inner">
              <div class="thumb">
                <img src="thumb.png" alt="썸네일이미지">
              </div>
              <div class="title>
                타이틀
              </div>
        </ul>
      </section>
      <footer>
        Copyright
      </footer>
    </div>
  </body>
</html>
```

### CSS
#### overflow
: 요소의 박스에 내용이 더 길 때 어떻게 보일지 선택하는 속성
 - visible : 기본값으로 내용이 더 길어도 그대로 보임
 - hidden : 내용이 길면 자름
 - scroll : 내용이 넘치지않아도 항상 스크롤바가 보임
 - auto : 내용이 잘릴 때만 스크롤바가 보임

#### float
: 정렬을 하기 위한 속성
- left : 왼쪽에 띄움
- right : 오른쪽에 띄움
- inital : 기본값으로 설정
- inherit : 부모요소 상속
부모는 float된 자식의 너비 높이를 고려하지않기 때문에 부모에 overflow:hidden;을 줘서 영억을 부여해야한다.

#### text-overflow
: 박스 안에 내용이 넘칠 때 택스트를 어떻게 처리할지 지정
- clip : 기본값으로 텍스트를 자름
- ellipsis : 잘린 텍스트를 생략부호(...)로 표시함

#### white-space
: 스페이스와 탭,줄바꿈,자동줄바꿈을 어떻게 처리할지 지정
- nowrap - 스페이스,탭,줄바꿈 병합,자동 줄바꿈은 병합 안함

# 1-4. 반응형 웹 - Tablet 제작

학습 출처 : [BoostCourse](https://www.edwith.org/boostcourse-ui)
