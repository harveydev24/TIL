# HTML

## HTML이란?

- Hyper Text Markdown Language
- 파이썬 같은 프로그래밍 언어는 아니고, 마크업 언어의 일종
- 웹 브라우저가 HTML을 읽고 우리에게 보여줌
- 현재의 웹 표준은 WHATWG의 HTML Living Standard
- 웹 페이지의 구조를 작성



## HTML의 기본 구조

- html

  - 문서의 최상위(root) 요소

- head

  - 문서 메타데이터 요소

  - 문서 제목, 인코딩, 스타일, 외부 파일 로딩 등

  - 일반적으로 브라우저에 나타나지 않는 내용

    - title
      - 브라우저 상단 타이틀
    - meta
      - 문서 레벨 메타데이터 요소
      - Open Graph Protocl
        - 메타 데이터를 표현하는 새로운 규약
        - HTML 문서의 메타 데이터를 통해 문서의 정보 전달
        - 메타 정보에 해당하는 제목, 설명 등을 쓸 수 있도록 정의

    - link
      - 외부 리소스 연결 요소(CSS, favicon 등)
    - script
      - 스크립트 요소(JavaScript 파일/코드)
    - style
      - CSS 직접 작성

- body

  - 문서 본문 요소
  - 실제 화면 구성과 관련된 내용

- DOM(Document Object Model) 트리

  - 텍스트 파일인 HTML 문서를 브라우저에서 렌더링 하기 위한 구조

  - HTML 문서에 대한 모델을 구성함

  - HTML 문서 내의 각 요소에 접근/수정에 필요한 프로퍼티와 메서드를 제공

    ```html
    <!DOCTYPE html>
    <html lang='ko'>
      <head>
        <meta charset="UTF-8">
        <title>Document</title>
      </head>
      <body>
        <h1>안녕하세요</h1>
      </body>
    </html>
    ```

    

- 요소(element)

  - 요소는 여는/닫는 태그와 내용으로 구성되어 있다.

  - 태그명은 대소문자 구문 없음

  - 태크는 컨텐츠를 감싸는 것으로 그 정보의 성격과 의미를 정의

  - 내용이 없는 태그들

    - br, hr, img, input, link, meta

  - 요소는 중첩될 수 있음

    - 요소의 중첩을 통해 하나의 문서를 구조화

    - 여는 태그와 닫는 태크의 쌍을 잘 확인해야함

      - 에러가 나지 않고 레이아웃이 깨지게 됨

        

- 속성(attribute)

  - 속성을 통해 태그의 부가적인 정보를 설정할 수 있음

  - 요소는 속성을 가질 수 있으며, 경로나 크기와 같은 추가적인 정보를 제공

  - 요소의 시작 태그에 작성하며 보통 이름과 값이 하나의 쌍으로 존재

  - 태그와 상관없이 사용 가능한 속성(HTML Global Atrribute)들도 있음

  - HTML Global Atrribute

    - id

      - 문서 전체에서 유일한 고유 식별자 지정

    - class

      - 공백으로 구분된 해당 요소의 클래스의 목록

    - data-*

      - 페이지에 개인 사용자 정의 데이터를 저장하기 위해 사용

    - style

      - inline 스타일

    - title

      - 요소에 대한 추가 정보 지정(툴팁)

    - tabindex

      - 요소의 탭 순서

        

- 시맨틱 태그

  - HTML5에서 의미론적 요소를 담은 태그의 등장
    - 기존 영역을 의미하는 div태그를 대체하여 사용
  - 대표적인 태그 목록
    - header
      - 문서 전체나 섹션의 헤더(머리말 부분)
    - nav
      - 네비게이션
    - aside
      - 사이드에 위치한 공간, 메인 콘텐츠와 관련성이 적은 콘텐츠
    - section
      - 문서의 일반적인 구분, 컨텐츠의 그룹을 표현
    - article
      - 문서, 페이지, 사이트 안에서 독립적으로 구분되는 영역
    - footer
      - 문서 전체나 섹션의 푸터(마지막 부분)
  - 검색엔진최적화(SEO)를 위해서 메타태그, 시맨틱 태그 등을 통한 마크업을 효과적으로 활용 해야함



## HTML 문서 구조화

- 텍스트 요소

  |  태그  |                           설명                           |
  | :----: | :------------------------------------------------------: |
  |   a    | href 속성을 활용하여 다른 URL로 연결하는 하이퍼링크 생성 |
  |   b    |           굵은 글씨 요소, 강조하고자 하는 요소           |
  | strong |    굵은 글씨 요소, 강조하고자 하는 요소, 시맨틱 태그     |
  |   i    |                     기울임 글씨 요소                     |
  |   em   |              기울임 글씨 요소, 시맨틱 태그               |
  |   br   |                 텍스트 내에 줄 바꿈 생성                 |
  |  img   |             src 속성을 활용하여 이미지 표현              |
  |  span  |                의미 없는 인라인 컨테이너                 |

  

- 그룹 컨텐츠

  |    태그    |                             설명                             |
  | :--------: | :----------------------------------------------------------: |
  |     p      |          하나의 문단, 인라인 요소만 들어올 수 있음           |
  |     hr     | 문단 레벨 요소에서의 주제의 분리를 의미하며 수평선으로 표현됨 |
  |     ol     |                      순서가 있는 리스트                      |
  |     ul     |                      순서가 없는 리스트                      |
  |    pre     | HTML에 작성한 내용을 그대로 표현, 보통 고정폭 글꼴이 사용되고 공백문자를 유지 |
  | blockquote |      텍스트가 긴 인용문, 주로 들여쓰기 한 것으로 표현함      |
  |    div     |                 의미 없는 블록 레벨 컨테이너                 |



- 테이블

  ```html
  <body>
    <table>
      <thead>
        <tr>
          <th>ID</th>
          <th>Name</th>
          <th>Major</th>
          </tr>
      </thead>
      <tbody>
        <tr>
          <td>1</td>
              <td>홍길동</td>
              <td>Computer Science</td>
          </tr>
          <tr>
            <td>2</td>
              <td>김철수</td>
              <td>Business</td>
          </tr>
      </tbody>
      <tfoot>
        <tr>
            <td>총계</td>
            <td clospan="2">2명</td>
          </tr>
      </tfoot>
      <caption>1반 학생 명단</caption>
    </table>
  </body>
  ```



- form

  - 정보(데이터)를 서버에 제출하기 위한 영역

  - form의 기본 속성

    - action

      - form을 처리할 서버의 URL

    - method

      - form을 제출할 때 사용할 HTTP 메서드(GET or POST)

        


- input
  - 다양한 타입을 가지는 입력
  - ionput의 속성
    -  name
      - form control에 적용되는 이름
    - value
      - form control에 적용되는 값
    - required, readonly, autofocus, aotucomplete, disabled 등



- input label
  - label을 클릭하여 input 자체의 초점을 맞추거나 활성화 시킬 수 있음
  - 웹/모바일 환경에서 편함
  - input에 id속성을, label에는 for 속성을 활용하여 상호 연관 시킴



- input type

  |   Type   |                        설명                        |
  | :------: | :------------------------------------------------: |
  |   text   |                  일반 텍스트 입력                  |
  | password |  입력시 값이 보이지 않고 문자를 특수기호 *로 표현  |
  |  email   |       이메일 형식이 아닌 경우 form 제출 불가       |
  |  number  | min, max, step 속성을 활용하여 숫자 범위 설정 가능 |
  |   file   |     accept 속성을 활용하여 파일 타입 지정 가능     |
  | checkbox |                     다중 선택                      |
  |  radio   |                     단일 선택                      |
  |  color   |                     색상 선택                      |
  |   date   |                        달력                        |
  |  hidden  |            사용자에게 보이지 않는 input            |



# CSS

- Cascading Style Sheets

- 스타일을 지정하기 위한 언어

- 선택하고, 지정한다.

- CSS 정의 방법

  - 인라인

  - 내부 참조

  - 외부 참조(link file) - 분리된 CSS 파일

    ```html
    <!DOCTYPE html>
    <html lang="ko">
    <head>
      <meta charset="UTF-8">
      <meta http-equiv="X-UA-Compatible" content="IE=edge">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Document</title>
      <style>
        h1 {
          color: green;
          font-size: 200;
        }</style>
    </head>
    <body>
      <h1>Hello :></h1>
    </body>
    </html>
    ```
    
    



## 선택자(Selector) 유형

- 기본 선택자
  - 전체 선택자, 요소 선택자
  - 클래스 선택자, 아이디 선택자, 속성 선택자
- 결합자(Combinators)
  - 자손 결합자, 자식 결합자
  - 일반 형체 결합자, 인접 형제 결합자
- 의사 클래스/요소(Pseudo Class)
  - 링크, 동적 의사 클래스
  - 구조적 의사 클래스, 기타 의사 클래스, 의사 엘리먼트, 속성 선택자



## CSS 적용 우선순위(cascading order)

1. 인라인
2. id
3. class, 속성, pseudo-class
4. 요소, pseudo-element



## CSS 상속

- CSS는 상속을 통해 부모 요소의 속성을 자식에게 상속

- 상속되는 속성
  - Text 관련 요소(font, color, text-align), opacity, visibility 등
- 상속되지 않는 속성
  - Box model 관련 요소(width, height, margin, padding, border, box-sizing, display), position 관련 요소(position, top, right, bottom, left, z-index) 등



## CSS  기본 스타일

### 크기 단위

- px(픽셀)
  - 모니터 해상도의 한 화소인 '픽셀' 기준
  - 픽셀의 크기는 변하지 않기 때문에 고정적인 단위
- %
  - 백분율 단위
  - 가변적인 레이아웃에서 자주 사용

- em
  - 바로 위, 부모 요소에 대한 상속의 영향을 받음
  - 배수 단위, 요소에 지정된 사이즈에 상대적인 사이즈를 가짐
  - 1em = 100%
- rem
  - 바로 위, 부모 요소에 대한 상속의 영향을 받지 않음
  - 최상위 요소(html)의 사이즈를 기준으로 배수 단위를 가짐
  - 1rem = 100%

- viewport
  - 웹 페이지를 방문한 유저에게 바로 보이게 되는 웹 컨텐츠의 영역 (디바이스 화면)
  - 디바이스의 viewport를 기준으로 상대적인 사이즈가 결정됨
  - 1vw, 1vh = viewport widht, height의 1%



## Box model

- 모든 요소는 네모(박스모델)이고, 위에서부터 아래로, 왼쪽에서 오른쪽으로 쌓인다.
- 하나의 박스는 네 부분으로 이루어짐
  - content
    - 글이나 이미지 등 요소의 실제 내용
  - padding
    - 테두리 안쪽의 내부 여백, 요소에 적용된 배경색, 이미지는 padding까지 적용
  - border
    - 테두리 영역
  - margin
    - 테두리 바깥의 외부 여백, 배경색을 지정할 수 없음

### box-sizing

- 기본적으로 모든 요소의 box-sizing은 content-box
  - Padding을 제외한 순수 contents 영역만을 box로 지정
- 다만, 우리가 일반적으로 영역을 볼 때는 border까지의 너비를 100px로 보는 것을 원함
  - 그 경우 border-box 사용



## CSS Display

- display: block
  - 줄 바꿈이 일어나는 요소
  - 화면 크기 전체의 가로 폭을 차지한다
  - 블록 레벨 요소 안에 인라인 레벨 요소가 들어갈 수 있음
- display: inline
  - 줄 바꿈이 일어나지 않는 행의 일부 요소
  - content 너비만큼 가로 폭을 차지함
  - widht, height, margin-top, margin-bottom을 지정할 수 없음
  - 상하 여백은 line-height로 지정
- display: inline-block
  - block과 inline 레벨 요소의 특징을 모두 가짐
  - inline처럼 한 줄에 표시 가능하고, block 처럼 widht, height, margin 속성을 모두 지정할 수 있음
- display: none
  - 해당 요소를 화면에 표시하지 않고, 공간조차 부여되지 않음
  - 이와 비슷한 visibility: hidden은 해당 요소가 공간은 차지하나 화면에 표시만 하지 않는다.



## CSS position

- 문서 상에서 요소의 위치를 지정
- static
  - 모든 태그의 기본 값(기준 위치)
  - 일반적인 요소의 배치 순서에 따름(좌측 상단)
  - 부모 요소 내에서 배치될 때는 부모 요소의 위치를 기준으로 배치됨
- 다음은 좌표 프로퍼티 top, bottom, left, right를 이용하여 이동 가능
  - fixed
    - 고정 위치
    - 요소를 일반적인 문서 흐름에서 제거 후 레이아웃 공간을 차지하지 않음
      - normal flow에서 벗어남
    - 부모 요소와 관계 없이 viewport를 기준으로 이동
      - 스크롤 시에도 항상 같은 곳에 위치함
  - absolute
    - 절대 위치
    - 요소를 일반적인 문서 흐름에서 제거 후 레이아웃 공간을 차지하지 않음
      - normal flow에서 벗어남
    - static이 아닌 가장 가까이 있는 부모/조상 요소를 기준으로 이동
      - 없는 경우 body 기준
  - relative
    - 상대 위치
    - 자기 자신의 static 위치를 기준으로 이동
      - normal flow 유지
    - 레이아웃에서 요소가 차지하는 공간은 static일 때와 같음
      - normal position 대비 offset



## Float

- 박스를 왼쪽 혹은 오른쪽으로 이동시켜 텍스트를 포함 인라인 요소들이 주변을 wrapping 하도록 함
- 요소가 normal flow를 벗어나게 함
- 속성
  - none
    - 기본값
  - left
    - 요소를 왼쪽으로 띄움
  - right
    - 요소를 오른쪽으로 띄움

- clearfix

  - float의 공간을 임의로 만들어주기 위해 사용

  - clear를 통해 float를 지워줌

    ```html
    <!DOCTYPE html>
    <html lang="ko">
    <head>
      <meta charset="UTF-8">
      <meta http-equiv="X-UA-Compatible" content="IE=edge">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Document</title>
      <style>
        .box1 {
          width: 10rem;
          height: 10rem;
          border: 1px solid aqua;
          background-color: red;
        }
    
        .box2 {
          width: 20rem;
          height: 10rem;
          border: 1px solid aqua;
          background-color: blue;
        }
    
        .left {
          float: left;
        }
    
        .clearfix::after {
          content: "";
          clear: both;
          display: block;
        }
      </style>
    </head>
    <body>
      <div class="clearfix">
        <div class="box1 left">box1</div>
      </div>
      <div class="box2">box2</div>
     </body>
    </html>
    ```

    

## Flex-box

- 행과 열 형태로 아이템들을 배치하는 1차원 레이아웃 모델
- 수동으로 값을 지정하지 않고 수직 정렬 및 아이템의 너비와 높이 혹은 간격을 동일하게 배치
- 축
  - main axis (메인 축)
  - cross axis (교차 축)
- 구성 요소
  - Flex Container (부모 요소)
    - flexbox 레이아웃을 형성하는 가장 기본적인 요소
    - Flex Item들이 놓여있는 영역
    - display 속성을 flex 혹은 inline-flex로 지정
  - Flex Item (자식 요소)
    - 컨테이너에 속해 있는 컨텐츠(박스)

- 속성
  - flex-direction 
    - main-axis 방향 지정
    - row, row-reverse, column, column-reverse
  - flex-wrap
    - 아이템이 컨테이너를 벗어나는 경우 해당 영역 내에 배치되도록 설정
    - nowrap (기본 값)
      - 한 줄에 배치
    - wrap
      - 넘치면 그 다음줄로 배치
  - justify-content
    - main-axis 기준으로 공간 배분
  - align-content
    - cross-aix 기준으로 공간 배분
  - 이 외 정렬 속성 다수











