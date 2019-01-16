# HTML (Hyper-Text Markup Language) and CSS



## 1. Semantic Markup
의미있는 HTML

HTML, CSS, JS 를 분리 (inline-style / inline-js 사용 X)



### 1-1. 시맨틱 마크업의 이점

- 접근성이 좋아짐
- 수정이 용이
- 코드 가독성 좋아짐
- 코드 재사용성 높아짐



### 1-2. 좋은 마크업을 위한 방법

- Heading Tag 사용
- List 태그 사용 (ol, ul, dl)
- Label 사용
- 표현을 위한 태그를 사용하지 않는다. (스타일은 css 가 담당)
- HTML/CSS Validator 사용





## 2. CSS 축약형

### 2-1. Font

```css
font: [-style] [-variant] [-weight] [font-size/line-height] [-family];

font: [스타일] [소문자를 작은 대문자로] [두께] [사이즈/높이] [글꼴];
```

### 2-2. Background

```css
background: [-color] [-image] [-repeat] [-attachment] [-position];
```

### 2-3. Margin / Padding

```css
margin: 0, 0, 0, 0;
padding: 0, 0, 0, 0;
// top->right->bottom->left (위에서부터 시계방향)

margin: 0, 0;
// 위 / 아래

margin: 0, 0, 0;
// 위 / 좌우 / 아래
```

### 2-4. Border

```css
//border 가 들어가는 위치는 margin 과 동일
border: [-width] [-color] [-style];
```



## 3. Attribute

### 3-1. \<a> 태그

```html
<a href="" target="">Link</a>
```

- href : 이동할 주소
- target : 창을 어떻게 열지 지정
  - _self : 현재 페이지에서 열기 (기본값)
  - _blank : 새창에서 열기
  - _parent : 부모(상위) 창에서 열기 (부모가 없으면 _self)
  - _top : 가장 상위 창에서 열기
  - frame name : 지정된 프레임에서 열기
- title : 링크에 대한 설명



### 3-2. \<img> 태그

```html
<img src="" alt="" />
```

- alt 요소는 접근성을 위해 반드시 필요한 요소이다.



## 4. Block VS Inline

### 4-1. Block

- 한 줄에 하나의 요소를 표시 (box 를 생성)
- 수직으로 쌓인다. (위에서 아래로 흐름)
- 너비/높이 지정 가능 (미지정시 부모 너비 / 컨텐츠 높이)
- margin / padding 사용 가능 (margin: auto 가능)
- 양 옆에 요소를 둘 수 없다.



### 4-2. Inline

- 한 줄에  여러개의 요소를 표시 (왼쪽에서 오른쪽으로 흐르는 보통 흐름)
- Inline level 은 Block level 을 자식을 가질 수 없다. (예외 : \<a> 태그)
- 컨텐츠 영역만큼 크기를 갖는다.
- 텍스트 정렬에 영향을 받는다.
- 포지션이 텍스트처럼 처리된다.



### 4-3. Inline-block

- 너비/높이 지정 가능
- 턱스트 정렬에 영향을 받음
- margin / padding 사용 가능 (margin: auto 불가)
- 포지션이 텍스트처럼 처리된다.



## 5. Float

[사전] 띄우다.

[CSS] 요소가 보통흐름으로부터 빠져 인라인 요소가 그 주위를 감싸도록 배치함. 기본 속성은 \"block level\" 이 된다.



## 6. Block Fomatting Context (BFC)

```
블록 박스의 레이아웃이 결정되며 float 끼리 영향을 받는다.
BFC는 float 의 위치를 정하고 해제하는 중요한 역할을 한다.
```

### 6-1. BFC 만들어지는 경우

- float
- position: absolute / fixed
- display (inline 제외)
- Block-level-box (overflow 를 제외한 경우)
- overflow (visible 제외)



## 7. Float 해제하기

1. 부모 요소에서 float 된 자식만큼 높이 값을 적용한다. (고정 높이)
2. clear 속성 사용 (가상요소, 빈태그 사용 - display: block, table)
3. 부모에게 overflow: hidden (BFC 로 만들어버림)
4. 부모 요소에 inline-block 속성 부여



## 9999. 기타 이슈 

- 마크업은 문서를 작성하듯이 위에서 아래로 글 쓰듯 작성
- 접근성을 고려하여 문서 작성 (WCAG)
- block 요소는 기본 width: 100%
- absolute 사용 시 기준이 되는 요소를 지정 (relative)
- absolute 사용 시 기준점 반드시 지정 (top/bottom, left/right)
- position: fixed 는 브라우저를 기준으로 위치를 잡음
- float 후에는 반드시 clear
- 가상요소도 DOM 임
- table/table-cell 사용 시 table-layout: fixed 하면 좋음 (셀 너비 고정, 렌더링 속도 향상)
- div 를 inline-block 으로 변경 시 IE8 에서 변경되지 않는 이슈 있음
- 숨김 처리가 필요한 요소는 blind 클래스 이용

