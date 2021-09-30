# CSS Layout Techniques

> display, position, **float, flexbox, grid system**

### 09_Float

- 본래는 이미지 좌, 우측 주변으로 텍스트를 둘러싸는 레이아웃을 위해 도입

- Float 속성 : none(기본값), left(요소를 왼쪽으로 띄움), right(요소를 오른쪽으로 띄움)

- Float clear 

  - 선택한 요소의 맨 마지막 자식으로 가상 요소를 하나 생성
  - 보통 content속성과 함께 짝지어, 요소에 장식용 콘텐츠 추가할 때 사용
  - 기본값은 inline

  ```css
  .clearfix::after {
  	content: "";
      display: block;
      clear: both;	
  }
  ```

  ```html
  <header class="clearfix">
      <div class="left">float left</div>
  </header>
      <div>div</div>
  ```

  

### 10_Flexbox

- CSS Flexible Box Laybout
  - 요소 간 공간 배분과 정렬 기능을 위한 1차원(단방향) 레이아웃
  - **요소** : Flex Container(부모 요소), Flex Item(자식 요소)
  - **축** : main axis(메인 축), cross axis(교차 축)

<img src="../../../../임시-폴더/image-20210816214131825.png" alt="image-20210816214131825" style="zoom:50%;" />

- flexbox의 시작 : 부모 요소(flex containter)에 `display: flex` 혹은 `inline-flex`를 작성하는 것부터 시작!
- `flex-direction` : main-axis 방향 설정
  - row(default), row-reverse, column, column-reverse
- `justify-` : 메인축 방향 정렬
- `align-` : 교차축 방향 
- `content` : 여러줄, `items` : 한 줄, `self` : flex item 개별 요소
  - justify-content : 메인축 기준 여러줄 정렬 
  - align-items : 교차축 기준 한 줄 정렬
  - align-self : 교차축 기준 선택한 요소 하나 정렬
  - flex-start, flex-end, center, space-between, space-around, space-evenly, baseline, stretch

> *** 정리 *** 
>
> - display : flex 
>
>   - 정렬하려는 부모 요소에 작성
>   - inline-flex : flex 영역을 블록으로 쓰지 않고 인라인 블록으로 사용
>
> - flex-dircetion
>
>   - item이 쌓이는 방향 설정
>   - main-axis가 변경됨 
>     - row(기본값) : 주축의 방향이 왼쪽에서 오른쪽
>     - row-reverse : 주축의 방향이 오른쪽에서 왼쪽
>     - column : 주축의 방향이 위에서 아래
>     - column-reverse : 주축의 방향이 아래에서 위
>
> - flex-wrap
>
>   - 요소들이 강제로 한 줄에 배치 되게 할 것인지 여부 설정
>   - nowrap(기본값) : 모든 아이템을 한 줄에 나타내려고 함
>   - wrap : 넘치면 그 다음 줄로
>   - wrap-reverse : 넘치면 그 윗줄로(역순)
>
> - flex-flow 
>
>   - flex-direction과 flex-wrap의 shorthand
>   - 예시) flex-flow: row nowarp;
>
> - justify-content
>
>   - main축 정렬
>
>   - flex-start(기본 값): 시작 지점부터 차례로 쌓임
>
>     [1 2 3                     ]
>
>   - flex-end : 쌓이는 방향이 뒤쪽부터 시작
>
>     [                     1 2 3]
>
>   - center : 정중앙
>
>   - space-between : 좌우 정렬(item들 간격 동일)
>
>   - space-around : 균등 좌우 정렬 (내부 요소 여백은 외곽 여백의 2배)
>
>   - space-evenly : 균등 정렬 (내부 요소 여백과 외곽 여백 모두 동일)
>
> - align-items
>
>   - cross 축 정렬
>   - stretch (기본값) : 컨테이너를 가득 채움
>   - flex-start : 위
>   - flex-end : 아래
>   - center : 가운데
>   - baseline : item 내부의 text에 기준선을 맞춤
>
> - order 
>
>   - 작은 숫자 일수록 앞(우선 쌓이는 방향)으로 이동
>   - 기본 값 : 0
>
> - flex-grow 
>
>   - 주축에서 남는 공간을 항목들에게 분배하는 방법
>   - 각 아이템의 상대적 비율을 정하는 것은 아님
>   - 기본 값 : 0
>   - 음수 불가능



### 11_Bootstrap 

​	UI 라이브러리

- flexbox in bootstrap
  - `d-flex` 

- grid system

  - bootstrp grid system은 flexbox로 제작됨
  - `container`, `rows`, `column`으로 컨텐츠 배치하고 정렬
  - **12개**의 `column`, **6개**의 `grid breakpoints`

  ```html
  <div class="container">
      <div class="row">
          <div class="col"></div>
          <div class="col"></div>
          <div class="col"></div>
          </div>
      </div>
  </div>
  ```

  



