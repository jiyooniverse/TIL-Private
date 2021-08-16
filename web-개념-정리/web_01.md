### 00_HTML&CSS

- 현재의 웹 표준 : HTML5, WHATWG

- HTML : Hyper Text Markup Language

  - Hyper : 텍스트 등의 정보가 동일 선상에 있는 것이 아니라 다중으로 연결되어 있는 상태
  - Hyper Text : 참조(하이퍼링크)를 통해 사용자가 한 문서에서 다른 문서로 즉시 접근할 수 있는 텍스트
  - Markup Language : 태그 등을 이용하여 문서나 데이터 구조 명시하는 언어, 프로그래밍 언어와 다르게 단순하게 데이터를 표현하기만 한다.

  > HTML은 웹페이지를 작성하기 위한 언어로 **웹 컨텐츠의 의미와 구조를 정의**

  

### 01_HTML기본구조

- `head` 요소 : 문서 제목, 문자코드(인코딩)와 같이 해당 문서 정보를 담고 있으며, 브라우저에 나타나지 않는다. 

- 메타 데이터를 표현하는 새로운 규약, Open Graph Protocol

  - HTML 문서의 메타 데이터를 통해 문서의 정보 전달

- `body` 요소: 브라우저 화면에 나타나는 정보로 실제 내용에 해당한다.

- DOM(Document Object Model)트리 : 부모 관계, 형제 관계

  - 문서의 구조화된 표현
  - Web Page의 객체 지향 표현

- **요소(element)** : HTML의 요소는 `태그`와 `내용`으로 구성되어있다.

  > <시작 태그>내용<닫는 태그>

  - 내용이 없는 태그 : br, hr, img, input, link, meta
  - 요소는 중첩될 수 있음

- **속성(attribute)** : 태그별로 사용할 수 있는 속성은 다르다.

  - HTML Global Attribute : 모든 HTML 요소가 공통으로 사용할 수 있는 속성
    - id, class, hidden, lang, style, tabindex, title

- **시맨틱 태그** : HTML5에서 의미론적 요소를 담은 태그의 등장

  - `header` : 문서 전체나 섹션의 헤더
  - `nav` : 내비게이션
  - `aside` : 사이드에 위치한 공간, 메인 콘텐츠와 관련성이 적은 콘텐츠
  - `section` : 문서의 일반적인 구분, 컨텐츠의 그룹을 표현
  - `article` : 문서, 페이지, 사이트 안에서 독립적으로 구분되는 영역
  - `footer` : 문서 전체나 섹션이 푸터(마지막 부분)

  > Non semantic 요소는 div, span등이 있으며 h1, table 태그들도 시맨틱 태그로 볼 수 있음



### 02_문서구조화

- 인라인/ 블록 요소
- 그룹 컨텐츠 : <p>, <hr>, <ol>, <ul>, <pre>, <blockquote>, <div>
- 텍스트 관련 요소 : <a>, <b>, <strong>, <i>, <em>, <span>,  <img>, \<br>
- table : <tr>, <td>, <th>, <col>, <colgroup>
- form : <form>은 서버에서 처리될 데이터를 제공하는 역할
  - 기본 속성 : action, method
- input : 다양한 타입을 가지는 입력 데이터 필드 
  - <label> : 서식 입력 요소의 캡션
  - <input> 공통 속성 : name, placeholder, required, autofocus



### 03_CSS

- css(casacading style sheets) : 스타일, 레이아웃 등을 통해 문서(HTML)를 표시하는 방법을 지정하는 언어

  ```css
  h1 {	/* 선택자(selector) */
      color: blue;	/* 선언(Declaration) */
      font-size: 15px; 	/* 속성(Property), 값(Value) */
  }
  ```

- CSS 정의 방법

  - 인라인 : 해당 태그에 직접 `style` 속성활용

    ```html
    <h1 style="color: blue; font-size: 15px;">Hello</h1>
    ```

  - 내부 참조 - <style> : head 태그 내에 <style> 지정

    ```html
    <head>
        <style>
            h1 {
                color: blue;
                font-size: 15px;
            }    
        </style>
    </head>
    ```

  - 외부 참조 - 분리된 CSS파일 : 외부 CSS파일을 <head>내 <link>를 통해 불러오기

    ```html
    <head>
        <link rel="stylesheet" href="mystyle.css">
    </head>
    ```

    

### 04_CSS Selectors

- 선택자 : HTML 문서에서 **특정한 요소**를 선택하여 스타일링하기 위해 **선택자** 필요

  - 기본 선택자 : 전체 선택자, 요소 선택자, 클래스 선택자, 아이디 선택자, 속성 선택자
  - 결합자 : 자손 결합자, 자식 결합자, 일반 형제 결합자, 인접 형제 결합자

  ```css
  <style>
  	/* 전체 선택자 */
      * {
          color: red;
      }
      
      /* 요소 선택자 */
      h2 {
          color: orange;
      }
      
      h3,
      h4 {
          font-size: 10px;
      }
      
      /* 클래스 선택자 */
  	.green {
          color: green;    
  	}
      
      /* id 선택자 */
      #purple {
          color = purple;
      }
      
      /* 자식 결합자 */
      .box > p {
          font-size: 30px;
      }
      
      /* 자손 결합자 */
      .box p {
          color: blue;
      }
  
  </style>
  ```

  > 우선 순위 : !important > 인라인 > id 선택자 > class 선택자 > 요소 선택자 > 소스 순서



<img src="../../../../임시-폴더/image-20210814235343681.png" alt="image-20210814235343681" style="zoom:50%;" />

> 1. 요소 선택자 → orange
> 2. 클래스 선택자 → blue
> 3. 클래스 선택자 → green
> 4. **클래스 선택자 →green**  *css파일 내부에 있는 순서에 따라 마지막 클래스인 green클래스* 
> 5. id 선택자 → red
> 6. !important → darkviolet
> 7. 인라인 → yellow
> 8. !important → darkviolet

- CSS 상속 : CSS 상속을 통해 부모 요소의 속성을 *모두 상속 받지는 않는다.*

  - 상속 되는 것 : Text 관련 요소
  - 상속 되지 않는 것 : Box model관련 요소, position 관련 요소

- 결합자 : *자식/자손은 하위 항목 개념이고 형제는 같은 줄에 있는 개념*

  - 자손 결합자 : selectorA 하위의 모든 selectorB요소

    ```css
    div span { color: red;}
    ```

    ```html
    <div>
        <span>이건 빨강</span>
        <p>이건 빨강 아님</p>
        <P>
            <span>이건 빨강</span>        
        </P>
    </div>
    ```

  - 자식 결합자 : selectorA 바로 아래의 selectorB 요소

    ```css
    div > span {color: red;}
    ```

    ```html
    <div>
        <span>이건 빨강</span>
        <p>이건 빨강 아님</p>
        <p>
            <span>이건 빨강 아님</span>
        </p>
        <span>이건 빨강</span>
    </div>
    ```
  
  - 일반 형제 결합자 : selectorA의 형제 요소 중 **뒤**에 위치하는 selectorB 요소를 모두 선택 
  
    ```css
    p ~ span {color: red;}
    ```
  
    ```html
    <span>p태그 앞에 위치하기 때문에 빨강이 아님</span>
    <p>여기 문단이 있습니다.</p>
    <b>그리고 코드도 있습니다.</b>
    <span>p태그와 형제이기 때문에 빨강!</span>
    <b>다른 코드도 있습니다.</b>
    <span>p태그와 형제이기 때문에 빨강!</span>
    ```
  
  - 인접 형제 결합자 : selectorA의 형제 요소 중 **바로 뒤**에 위치하는 selectorB 요소를 선택 (바로 뒤 하나만!)
  
    ```css
    p + span {color: red;}
    ```
  
    ```html
    <span>p태그 앞에 위치하기 때문에 빨강이 아님</span>
    <p>여기 문단이 있습니다.</p>
    <span>p태그와 인접한 형제이기 때문에 이건 빨강!</span>
    <b>코드가 있습니다.</b>
    <span>p태그와 인접한 형제가 아니기 때문에 이건 빨강이 아님</span>
    ```
  
    

### 05_CSS 단위

- 크기 단위 
  - px(픽셀)
    - 모니터 해상도의 한 화소인 '픽셀'을 기준
    - 픽셀의 크기는 변하지 않기 때문에 고정적인 단위
  - %
    - 백분율 단위
    - 가변적인 레이아웃에서 자주 사용
  - em
    - (바로 위, 부모 요소에 대한) 상속의 영향을 받음
    - 배수 단위, 요소에 지정된 사이즈에 상대벅인 사이즈를 가짐
  - rem
    - (바로 위, 부모 요소에 대한) 상속의 영향을 받지 않음
    - 최상위 요소(html)의 사이즈를 기준으로 배수 단위를 가짐
  - viewport
    - 웹 페이지를 방문한 유저에게 바로 보이게 되는 웹 컨텐츠의 영역
    - 주로 스마트폰이나 테블릿 디바이스의 화변을 일컫음
    - 글자 그대로 디바이스의 viewport를 기준으로 상대적인 사이즈가 결정됨
    - vw, vh, vmin, vmax
- 색상 단위
  - 색상 키워드 : 대소문자 구분 x, 'red', 'blue', 'black'과 같은 특정 색을 직접 나타냄
  - RGB 색상 : 16진수 표기법 혹은 함수형 표기법을 사용해서 특정 색을 표현하는 방식
  - HSL 색상 : 색상, 채도, 명도를 통해 특정 색을 표현하는 방식



### 06_CSS Box Model

- 모든 HTML 요소는 box형태로 되어있음

- 하나의 박스는 네부분으로 이루어짐 : content, padding, border, margin

  - content : 글이나 이미지등 요소의 실제 내용
  - padding : 테두리 안쪽의 내부 여백. 요소에 적용된 배경색, 이미지는 padding까지 적용
  - border : 테두리 영역
  - margin : 테두리 바깥의 외부 여백. 배경색을 지정할 수 없다.

- Box model 구성 (margin/ padding) 

  - **shorthand**로 표현 가능

    ```css
    .margin-1 { margin: 10px;}	/* 상,하,좌,우 : 10px */
    .margin-2 { margin: 10px 20px;}	/* 상,하: 10px, 좌,우: 20px */
    .margin-3 { margin: 10px 20px 30px;}	/* 상: 10px,하: 30px, 좌,우: 20px */
    .margin-4 { margin: 10px 20px 30px 40px}	/* 시계 방향으로 상:10px ~*/
    ```

- Box size

  ```html
  <style>
      .box {
          width: 100px;
          margin: 10px auto;
          padding: 20px;
          border: 1px solid black;
          color: white;
          text-align: center;
          background-color: blueviolet;
      }
      
      .box-sizing {
          box-sizing: border-box;
          margin-top: 50px;
      }
  </style>
  ```

  ```html
  <body>
      <div class="box">content-box</div>
      <div class="box box-sizing">border-box</div>
  </body>
  ```

  > *contentb-box*의 총 너비는 **142px**(width + right-padding + left-padding + right-border + left-border)
  >
  > *border-box*의 box-sizing 클래스의 box-sizing 속성값인 **border-box**을 통해 총 영역 값을 width값으로 지정할 수 있다. 이때, content영역의 넓이는 58px이 되고 총 영역의 너비는 **100px**이된다.

- 마진 상쇄 : block A의 top과 block B의 bottom에 적용된 각각의 margin이 둘 중 큰 마진 값으로 결합되는 현상



### 07_CSS Display

- display: `block`

  - 줄 바꿈이 일어나는 요소
  - 화면 크기 전체의 가로 폭을 차지한다.
  - 블록 레벨 요소 안에 인라인 레벨 요소가 들어갈 수 있음.
  - div/ ul, ol, li/ p/ hr/ form 등

- display: `inline`

  - 줄 바꿈이 일어나지 않는 행의 일부 요소
  - content 너비만큼 가로 폭을 차지한다.
  - width, height, margin-top, margin-bottom을 지정할 수 없다.
  - 상하 여백은 `line-height`로 지정한다.
  - span/ a/ img/ input, label/ b, em, i, strong 등

- display: `inline-block`

  - block과 inline 레벨 요소의 특징을 모두 갖는다.
  - inline처럼 한 줄에 표시 가능하며
  - block 처럼 width, height, margin 속성 지정 가능

- display: `none`

  - 해당 요소를 화면에 표시하지 않음.(공간도 사라짐)
  - 이와 비슷한 `visibility: hidden`은 해당 요소의 공간은 있고 화면에 표시만 하지 않음.

- 속성에 따른 수평 정렬

  - 왼쪽 정렬 

    - margin-right: auto;
    - text-align: left;

  - 오른쪽 정렬

    - margin-left: auto;
    - text-align: right;

  - 가운데 정렬

    - margin-right: auto; margin-left: auto;

    - text-align: center;

      

### 08_CSS Position

- position : `static` : 모든 태그의 기본 값(기준 위치)
  - 일반적인 요소의 배치 순서에 따름(좌측 상단)
  - 부모 요소 내에서 배치될 때는 부모 요소의 위치를 기준으로 배치 됨
- position : `relative` : 상대 위치
  - 자기 자신의 static 위치를 기준으로 이동
  - 레이아웃에서 요소가 차지하는 공간은 static일 때와 같음
- position : `absolute` : 절대 위치
  - 요소를 일반적인 문서 흐름에서 제거후 레이아웃에 공간을 차지하지 않음
  - static이 아닌 가장 가까이 있는 부모/ 조상 요소를 기준으로 이동(없는 경우 body에 붙는 형태)
- position : `fixed` : 고정 위치
  - 요소를 일반적인 문서 흐름에서 제거 후 레이아웃에 공간을 차지하지 않음
  - 부모요소와 관계없이 **viewport**를 기준으로 이동
  - 스크롤 시에도 항상 같은 곳에 위치함  
- relative, absolute, fixed는 좌표 프로퍼티(`top`, `bottom`, `left`, `right`)를 사용하여 이동 가능

