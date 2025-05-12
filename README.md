# JavaScript 기초

- 반드시 스스로 개념을 정리해야함
- 타인에게 특히, 초등학생에게 설명할 정도로 쉽게 개념을 정리하면 좋다

## 1. 기초 상식

- html : 웹브라우저에 데이터를 보여주는 형식을 지정한 문법구조
- css3 : 데이터를 잘 보여주기 위해서 꾸며주는 용도의 문법
- js

```
1. css 제어 : 레이아웃 변경 하도록 지시
2. html 제어 : 데이터의 결과를 CRUD 하도록 지시
3. Server, DB, 데스크탑 Application 을 제어 : Node.js로 가능함
```

## 2. JS의 종류는 2가지

### 2.1. 웹브라우저용 JS (web API)

- web API는 웹 브라우저에 미리 기능이 만들어져 있는 JS 기능
- 주로 직접 코딩하는 것이 아니고 미리 만들어진 기능을 사용하는 것

### 2.2. 데이터 관리 JS (ES6)

- 이전 JS는 웹브라우저 마다 모두 달랐아
- 이에 대한 불편함을 해소하기 위해서 JS의 문법을 통일함
- 기준이 ECMAScript 라고하며 ES6가 가장 기준이 된다

## 3. 실습

### 3.1. 웹브라우저에서 JS 실행하기

- `F12` 실행 > `Console` 탭을 실행 : console 탭은 js의 `결과, 오류`를 보는 곳
- 1줄 이상 작성하는 경우는 `Shift + Enter`키를 입력해야 함

```js
console.log("안녕");
```

```js
console.clear();
```

```js
alert("안녕");
```

### 3.2. html에서 JS 실행하기

- index.html 파일을 생성합니다.

## 4. Script 작성 위치 고민하기

- `<script></script>` 태그를 지원합니다.

```html
<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>자바스크립트</title>
    <script>
      console.log("1. 안녕");
    </script>
  </head>
  <body>
    <script>
      console.log("2. body 입니다.");
    </script>
  </body>
</html>
<script>
  console.log("3.html 끝 입니다.");
</script>
```

### 4.1. 3번 자리 즉 html의 끝이 좋다.

- 일반적으로 css와 html을 제어하는 것이 js 의 목적이다.
- `웹 브라우저가 css와 html을 모두 읽고 난 후의 자리`

### 4.2. 1번자리 즉 head 자리는 `기능`의 정의

- 개발자가 만든 많은 `기능`들을 코딩하기 좋은 자리
- 다른 개발자가 만든 많은 `기능`들을 불러와서 사용하기 좋은자리

## 5. js도 외부에 파일로 만들어서 관리하자

- js 폴더 생성
- js 폴더에 `lib.js` 파일 생성
- html head부분에 파일연결

```html
<script src="js/lib.js"></script>
```

- js/lib.js 내용

```js
function say(_msg) {
  console.log(_msg);
}
console.log("1. 안녕");
```

# JavaScript 문법

## 1. 변수(variables)

- 웹브라우저에 `값 보관 시 사용할 공간`

### 1.1.변수가 왜 필요할까?

#### 1.1.1. 단계 1 (필요로 한 기능에 대해서 서술 - 피그마, UI 다이어그램)

- `사용자 정보`를 입력 받아서 `DB에 보관`하고 싶을 때
- 사용자가 로그인을 하고 나면 사용자 정보를 화면에 출력하고 싶을 때

#### 1.1.2. 단계 2 (어떤 정보를 보관할지 결정한다 - 요구사항명세서)

```
이름, 나이, 주민등록번호, 전화번호, 주소(우편번호, 상세주소), 이메일, 아이디, 비밀번호, 동의체크
```

#### 1.1.3. 단계 3 (각각의 정보를 보관할 공간을 마련)

```
이름 : 글자 20자 제한
주민등록번호 : 글자 13자 제한
전화번호 : 글자 11자 제한
우편번호 : 글자 5자 제한
상세주소 : 글자 50자 제한
이메일 : 글자 20자 제한
아이디 : 글자 16자 제한
비밀번호 : 글자 16자 제한
동의 체크 : 참/거짓 숫자 1자 제한
```

### 1.2. 각 항목에 대해서 웹브라우저에서 임시로 보관하는 작업

- 웹브라우저 메모리 `빈 공간` 요청

```js
var ;
let ;
const ;
```

### 1.2.2. `var` 라고 작성을 하면 `변수`로 인정

- `hoisting`으로 오류가 발생할 소지가 높음
- 미리 만들지 않고 사용해도 되는 문제
- 이건 옛날 js 버전에서만 씁니다.

```
무조건 공간에다가 undefined를 넣어버린다.
호이스팅의 대상이 된다.
```

#### 1.2.3. `let` 라고 작성 하면 `변수`로 인정

- `hoisting`의 문제를 사전에 차단한다
- `let` 으로 작성 시 미리 사용하면 오류로 알려준다
- 수시로 내용이 바뀐다 (변할 수 있는 값)

#### 1.2.4. `const`라고 작성하면 `상수`로 인정

- `hoisting`의 문제를 사전에 차단한다
- `const` 으로 작성 시 미리 사용하면 오류로 알려준다
- 절대로 내용이 변하지 않는다(고정된 값)

### 1.2.5. 실제로 var, let, const중에 선택합니다.

- 값이 사용자 마다 변할 것이다. 그래서 `let`을 선택

```js
let 이름 : 글자 20자 제한
let 주민등록번호 : 글자 13자 제한
let 전화번호 : 글자 11자 제한
let 우편번호 : 글자 5자 제한
let 상세주소 : 글자 50자 제한
let 이메일 : 글자 20자 제한
let 아이디 : 글자 16자 제한
let 비밀번호 : 글자 16자 제한
let 동의 체크 : 참/거짓 숫자 1자 제한
```

### 1.3. 메모리 공간에 이름 짓는 법 (명명법)

- 매우 중요하다. 이름을 잘못 지으면 다른 개발자에게 혼란을 줌
- 개발자들은 코딩 컨벤션이 있다
- 변수의 철자는 `명사+명사` `영어`로 해야한다
- 숫자로 시작 안됨
- 공백 안됨
- `_` , `$`를 제외한 특수기호는 안됨

#### 1.3.1.카멜 케이스 (Camel Case)

- 반드시 소문자로 시작하고 새로운 명사는 대문자로 시작한다 (예 : userName)
- 많은 프로그래머들이 네이밍을 보고 바로 변수라고 생각한다.
- 소문자만 쓰여있거나, 대문자로 쓰여있거나, 대문자로 시작하거나하면 다른 기능이있는 단어이기 때문.(ex 파스칼케이스)
-

#### 1.3.2. 스네이크 케이스 (Snake Case)

- 변수를 모두 소문자로 작성하고 `_`로 연결한 이름 (예: user_name)

### 1.3.3. 파스칼 케이스 (Pascal Case)

- 이름을 대문자로 작성하고 새로운 단어는 대문자로 시작
- 혹시 객체 변수 아닌가? / 혹시 클래스 정의 아닌가? 라고 유추함

#### 1.3.4 케밥 케이스 (Kebab Case)

- 이름을 소문자로 작성하고 '-'로 연결한 이름 (예: user-name)
- 파일 또는 css 파일에서는 사용한다
- 예 : Next.js의 파일명은 kebab이 표준이다

#### 1.3.5. 대문자

- 상수(변하지 않고, 항상 일정한 값을 갖는 수)명으로 판단함

#### 1.3.6. 적용하기

```js
let userName : 글자 20자 제한
let userNum : 글자 13자 제한
let userPhone : 글자 11자 제한
let userPost : 글자 5자 제한
let userAddress : 글자 50자 제한
let userEmail : 글자 20자 제한
let userId: 글자 16자 제한
let userPassword : 글자 16자 제한
let userAgree 체크 : 참/거짓 숫자 1자 제한
```

### 1.4. 데이터 종류 (원시데이터 : Primitive Data Type)

- number : 숫자
- string : 글자 (문자, 문자열로 구분)
- boolean : true / false (나중에 falshy 한 것 알아야 함.)
- undefined : 값이 없음 (변수 초기값으로 자동 셋팅)
- null : 개발자가 값이 없다고 지정함 (값이 `비었다`로 세팅해라)
- symbol : 절대로 겹치지 않는 변수

- (자바는 데이터타입을 명시할 수 없기에 타입스크립트를 써야한다)

#### 1.4.1 적용하기

- 데이터 길이(문자열의 길이)를 제안할 수 없다 (코딩으로 해결해야함)

```js
let userName = ""; //20자 제한
let userNum = ""; //13자 제한
let userPhone = ""; //11자 제한
let userPost = ""; //5자 제한
let userAddress = ""; //50자 제한
let userEmail = ""; //20자 제한
let userId = ""; //16자 제한
let userPassword = ""; //16자 제한
let userAgree = false; //숫자 1자 제한
```

### 1.5. var, let, const 정확히 제약사항 파악하기

- 웹브라우저에 저장할 내용, 즉 변수가 있다면 아래를 고민하자

#### 1.5.1. `1순위는 const` 입니다.

- 변수를 만든다면 나는 var, let, const 중에 무엇을 선택할까?
- const 는 변하지 않을 것이다라는 작성법.
- 필요하면 즉, 값이 코딩하다 보니 바뀌어야 하는 경우에 let 으로 변경한다.
- const 의 특징
  - 만들기 전에 사용할 수 없다. (호이스팅 문제 해결됨!)
  ```js
  console.log(userName); // Error
  const userName = "홍길동";
  ```
  - 동일한 이름으로 변수를 또 생성할 수 없다. (변수생성 중복 방지)
  ```js
  const userAge = 10;
  const userAge = 40; // Error
  ```
  - 값을 변경할 수 없다.
  ```js
  const userCity = "대구";
  userCity = "서울"; // Error
  ```

#### 1.5.2. `2순위는 let` 입니다.

- 만들기 전에 사용할 수 없다. (호이스팅 문제 해결! : const 와 동일)

```js
console.log(userName); // Error
let userName = "홍길동";
```

- 동일한 이름으로 중복 생성할 수 없다. (중복 에러 생성 : const 와 동일)

```js
let userAge = 20;
let userAge = 30; // Error
```

- 값을 나중에 변경할 수 있다. (const 와의 유일한 차이점)

```js
let userCity = "대구";
userCity = "서울"; // 괜찮다.
```

#### 1.5.3. `var는 사용하지 않는다`

- 호이스팅 통과되어 버림. (추후 오류의 원인)
- 동일한 이름으로도 중복 생성가능. (추후 오류의 원인)
- 값도 변경이 가능하다.
- 기존 코드에서 var 를 사용한 케이스가 있으면 그냥 유지한다.

### 1.6. 참조형 데이터 종류(Reference Data Type)

- 만약 interpark 사이트의 Banner 영역의 데이터를 js 에서 관리하려고 한다.
- 배너는 `링크 주소, 이미지 주소, 고유한 ID` 가 있다.
- 하나의 배너는 변수 3개씩 가지고 있다.
- 총 5개의 배너가 있다.

```js
// 첫 번째 배너
const bannerUrl_1 = "https://~";
const bannerImg_1 = "https://~";
const bannerId_1 = "1";
// 두 번째 배너
const bannerUrl_2 = "https://~";
const bannerImg_2 = "https://~";
const bannerId_2 = "2";
// 세 번째 배너
const bannerUrl_3 = "https://~";
const bannerImg_3 = "https://~";
const bannerId_3 = "3";
// 네 번째 배너
const bannerUrl_4 = "https://~";
const bannerImg_4 = "https://~";
const bannerId_4 = "4";
// 닷 번째 배너
const bannerUrl_5 = "https://~";
const bannerImg_5 = "https://~";
const bannerId_5 = "5";
```

#### 1.6.1. 객체

- 관련 있는 기본형 데이터들을 `묶어서 하나로` 만들기

```js
  const 객체명 = {}; // 1 단계

  // 2단계
  const 객체명 = {
    이름 : 값, // , 로 연결
    이름 : 값,
    이름 : 값
  }

  const 객체명 = {
    key Name : Key Value, // , 로 연결
    이름 : 값,
    이름 : 값
  }


  const 객체명 = {
    Property 속성명 : Value, // , 로 연결
    이름 : 값,
    이름 : 값
  }
```

```js
// 첫 번째 배너
const bannerUrl_1 = "https://~";
const bannerImg_1 = "https://~";
const bannerId_1 = "1";

const banner_1 = {
  url: "https://",
  img: "https://",
  id: "1",
};

// 두 번째 배너
const bannerUrl_2 = "https://~";
const bannerImg_2 = "https://~";
const bannerId_2 = "2";

const banner_2 = {
  url: "https://~",
  img: "https://~",
  id: "2",
};
```

- 객체 변수 정보에 담겨진 속성 즉, 키명을 통한 값 사용(호출)

```js
객체명.키명;
banner_1.url;

["객체명"].키명;
["banner_1"].url;
```

#### 1.6.2. 배열

- 하나의 이름으로 여러개의 데이터를 묶어서 관리

```js
const userArray = [1, 2, 3, "안녕", false, null, undefined];
const bannerId = ["1", "2", "3"];
const banner = [
  { url: "http~", img: "http~", id: "1" },
  { url: "http~", img: "http~", id: "2" },
  { url: "http~", img: "http~", id: "3" },
];
```

- 배열의 요소에 값 사용(호출)

```js
배열명[인덱스번호];
banner[0];
banner[1];
```

## 1.7. 변수 종합 예제

- 인터파크 티켓 랭킹 작업

```js
// 섹션의 타이틀
const sectionTitle = "티켓 랭킹";
console.log(sectionTitle);

// 섹션의 설명글
const sectionDesc = "~~~";
console.log(sectionDesc);
//섹션의 카테고리
const sectionCategoryArr = ["뮤지컬", "콘서트", "스포츠"];
console.log(sectionCategory);
console.log(sectionCategory[1]);
console.log(sectionCategory[2]);
console.log(sectionCategory[3]);

// 0 뮤지컬 1 콘서트 2 스포츠 3~~
// 인덱스는 시작점과 도착점을 지정해줘야한다. 0을입력하면 0부터 1미만의 사이에 들어있는 자료를 불러오는 것.

sectionCategory[인덱스번호];
sectionCategory[0];
sectionCategory[1];
sectionCategory[2];
sectionCategory[3]; //에러 (값이 없으니!)

//배열ver  :: 여러번 데이터요청이 일어난다.
// 티켓의 타이틀 정보
const ticketTitleArr = [
  "팬텀 10주년 기념 공연",
  "뮤지컬 <메디슨 카운티의 다리>",
  "뮤지컬 <라이카>",
];
console.log(ticketTitleArr[0]);
console.log(ticketTitleArr[1]);
console.log(ticketTitleArr[2]);

// 티켓의 이미지 경로
const ticketImgArr = ["http://a.jpg", "http://b.jpg", "http://c.jpg"];
// 티켓의 링크 경로
const ticketUrlArr = ["http://a.html", "http://b.html", "http://c.html"];

// 티켓의 순위
const ticketRankArr = [1, 2, 3];

// 티켓의 공연장소
const ticketPlaceArr = ["대구", "서울", "제주"];

// 티켓의 공연일시
const ticketDayArr = ["05/07", "05/09", "05/04"];

// 객체ver
// 위의 사항을 효율적으로 관리하기 위한 작업
const ticket_1 = {
  title: "패텀 10주년 기념 공연",
  img: "https://a.jpg",
  url: "https://a.html",
  rank: 1,
  place: "대구",
  day: "05/07",
};
console.log(ticket_1);
console.log(ticket_1.title);
console.log(ticket_1.img);
console.log(ticket_1.url);
console.log(ticket_1.rank);
console.log(ticket_1.place);
console.log(ticket_1.day);

const ticket_2 = {
  title: "뮤지컬 <메디슨 카운티의 다리>",
  img: "https://b.jpg",
  url: "https://b.html",
  rank: 2,
  place: "서울",
  day: "05/09",
};

console.log(ticket_2);
console.log(ticket_1["title"]);
console.log(ticket_1["img"]);
console.log(ticket_1["url"]);
console.log(ticket_1["rank"]);
console.log(ticket_1["place"]);
console.log(ticket_1["day"]);

const ticket_3 = {
  title: "뮤지컬 <라이카>",
  img: "https://c.jpg",
  url: "https://c.html",
  rank: 3,
  place: "제주",
  day: "05/04",
};
const ticketInfoArr = [ticket_1, ticket_2, ticket_3];

// 보통 아래의 형태로 데이터가 들어오는 것을 JavaScript Object Notation 즉, Json이라고 한다.
const ticketInfoJsonArr = [
  {
    title: "패텀 10주년 기념 공연",
    img: "https://a.jpg",
    url: "https://a.html",
    rank: 1,
    place: "대구",
    day: "05/07",
  },
  {
    title: "뮤지컬 <메디슨 카운티의 다리>",
    img: "https://b.jpg",
    url: "https://b.html",
    rank: 2,
    place: "서울",
    day: "05/09",
  },
  {
    title: "뮤지컬 <라이카>",
    img: "https://c.jpg",
    url: "https://c.html",
    rank: 3,
    place: "제주",
    day: "05/04",
  },
];

ticketInfoJsonArr[0].title;
ticketInfoJsonArr[1].title;
ticketInfoJsonArr[2].title;
```

## 2. 연산자(Operator)

- 연산을 해서 결과값을 만드는 `기호`
- 연산자에 의한 새로운 `결과값이 나오는 것을 연산식`

### 2.1. 사칙연산( `+ - * /` )

- 덧셈(+) 연산자

```js
const numA = 0;
const numB = 1;
const result = numA + numB; // 1
```

```js
const strA = "안녕";
const strB = "hello";
const result = strA + strB; // "안녕hello"
```

```js
const strA = "홍길동";
// "저기~ 홍길동님 반가워요!"
const result = "저기~ " + strA + "님 반가워요!";
```

```js
const strA = "홍길동";
const numAge = 20;
// "저기~ 홍길동님은 나이가 20이군요!"
// 숫자+글자는 글자로 인정함
const result = "저기~ " + strA + "님은 나이가" + numAge + "이군요!";

// 아래처럼 템플릿 문법을  추천한다. 흔히 백틱 이라고 한다.
const resultTemplate = `저기~ ${strA}님은 나이가 ${numAge}이군요!`;
```

- 참고 예제

```html
<div class="section">
  <div class="box_wrap">
    <a href="https:~">뮤지컬 팬텀</a>
    <img src="https:~" alt="뮤지컬 팬텀 배너이미지" />
  </div>
</div>
```

```js
const link = "https~";
const img = "https~";
const title = "뮤지컬 팬텀";
const alt = "뮤지컬 팬텀 배너이미지";
let tag = '<div class="section">';
tag = tag + '  <div class="box_wrap">';
tag = tag + '    <a href="' + link + '"https:~">' + title + "</a>";
// 가독성이 많이 떨어진다.
```

```js
const link = "https~";
const img = "https~";
const title = "뮤지컬 팬텀";
const alt = "뮤지컬 팬텀 배너이미지";
const tag = `
<div class="section">
  <div class="box_wrap">
    <a href="${link}">${title}</a>
    <img src="${img}" alt="${alt}" />
  </div>
</div>
`;
```

```js
const numA = 5;
const numB = 8;
const resultA = `${numA} + ${numB} = ${numA + numB}`;
const resultB = `${numA} - ${numB} = ${numA - numB}`;
const resultC = `${numA} * ${numB} = ${numA * numB}`;
const resultD = `${numA} / ${numB} = ${numA / numB}`;
```

```js
const a = 1; // number
const b = "1"; // string
// 1단계 number ===> string 으로 물어보지 않고 변환(암묵적 데이터 타입 변환)
// string + string ====> string
const result = a + b;
```

- `- 연산자`

```js
const numA = 100;
const numB = 10;
const result = numA - numB; // 90
```

```js
const numA = "100"; // string
const numB = 10; // number
// string 을 number 로 암묵적 변환
// number - number
const result = numA - numB; // 90
```

```js
const numA = "ABC"; // string
const numB = 10; // number
// string 을 number 로 암묵적 변환 실패
// string - number
const result = numA - numB; // NaN  ( Not a Number )
```

- `*  /  연산자`

```js
const numA = 4;
const numB = 2;
const resultMulti = numA * numB; // 8
const resultDevide = numA / numB; // 2
```

### 2.2. 나머지 연산 (`%`)

- 총 게시글 52개
- 한 페이지당 5개 목록
- 몇페이지가 필요한가?
- 마지막 페이지에서 보여주어야 하는 게시글 수?

```js
const total = 52;
const count = 5;
const totalPage = total / count; // 소숫점 나옴
const totalPageNumber = Math.ceil(totalPage); // 올림
const lastCount = total % count; // 나머지 나옴
```

### 2.3. 복합연산자 (연산 타이핑 수를 줄인다.)

```js
const numA = 5;
let result = numA + 3; // 5 + 3 = 8

// 코딩에 의한 가독성이 떨어집니다.
// 그런데 PG 들은 많이 사용하는 방식입니다.
// result = result + 10; 줄여서 작성함.
result += 10; // 18

// result = result - 5;
result -= 5; // 13

// result = result * 4;
result *= 4; // 52

// result = result / 2;
result /= 2; // 26

// result = result % 2; %는 나머지 연산자, (모듈러 연산자)
result %= 2; // 0
```

### 2.4. 증감연산자 (++ --)

- 개발자는 타이핑 수를 줄이려고 노력한다
- #1씩 증가,감소한다 #후치방식 전치방식이 있고 연산의 방식은 다르다.

```js
let num = 5;
num = num + 1;
num += 1;

// 후치연산자 (뒤에 위치한) , 1씩 증가한다
num++;

// 전치연산자 (앞에 위치한)
++num;
```

```js
let num = 5;
num = num - 1;
num -= 1;

// 1씩 감소한다
num--;
--num;
```

```js
let num = 20;
// 후에 배치된 후치연산 이라서
let numA = num--; // numA 에는 20입니다. 그리고 연산
num; // 19
```

```js
let num = 20;
// 전에 배치된 전치연산 이라서
let numA = --num; // numA 에는 19입니다. 그리고 연산
num; // 19
```

### 2.5. 논리연산자

#### 2.5.1. OR 연산자 (또는)

- `무조건 이해`해야한다.
- `falsy`한 값의 종류 (js에서 false 라고 판단하는 값)

```js
""; // 빈 문자열
0;
undefined;
null;
NaN;
false;
```

- 최종 결과가 true 인지 false 인지 결과를 변수에 저장
- OR 연산자 : 2개중 1개만 ture 이면 ture, 나머지 false

```js
//
let result = ture || ture; // = 등호 다음 트루가 와서 그 뒤는 참거짓 판별x
result = false || false; // = 등호 다음 펄스가 와서 그다음 참거짓 판별한다
result = false || true; // = 등호 다음 펄스가 와서 그다음 참거짓 판별한다

// 참일 것 같은것이 등호 가까이 오는것이 연산 횟수를 줄인다. (최적화)

result = "" || true;

let userPass;
result = userPass || "비밀번호 넣으세요.";
```

#### 2.5.2. And 연산자 (그리고)

- 둘다 true 면 true, 아니면 false
- 변수에 결과값은 true, false 가 담겨진다

```js
let result = true && true;
result = false && true; // = 등호 다음 펄스가 와서 그 뒤는 참 거짓판별X
result = false && false;
// 거짓일 것 같은것을 등호 가까이 오는 것이 연산횟수를 줄인다 (최적화)
```

#### 2.5.3. Not 연산자 (반대)

```js
let result = !true;
result = !false;
```

#### 2.5.4. 실습 예제

```js
let nickName = "";
let displayName = nickName || "Guest";
console.log(displayName); //Guest
```

```js
let title = null;
let result = title || "제목 없음";
console.log(result);
```

```js
let totalMoney = 0;
let result = totalMoney || "장바구니가 비었습니다.";
console.log(result);
```

```js
let isLogin = true;
let result = isLogin && "환영합니다.";
console.log(result);
```

```js
let isAdmin = false;
let result = isAdmin && "관리자 메뉴 표시";
console.log(result); //false뜬다
```

```js
// 초기값세팅할때 많이쓰는 코딩
let config = {};
config.theme = config.theme || "light";
console.log(config); // { theme : "light" }

let config = { theme: "red" };
config.theme = config.theme || "light";
console.log(config); // { theme : "red" }
```

```js
let options = {
  lang: null,
  fontSize: 0,
};
let lang = options.lang || "ko";
let fontSize = options.fontSize || 20;
```

### 2.6. 비교연산자

- 매우 중요!

```js
// 데이터 값의 종류는 비교하지 않음 ()
let result = "1" == 1; // true

// 데이터 값과 데이터 종류도 비교함 (동시연산자 , 자주 씀!)
result = "1" === 1; // false

let resultC = 1 > 2;
let resultD = 1 < 2;
let resultE = 1 >= 2;
let resultF = 1 <= 2;
let resultG = 1 != 2;
let resultH = 1 !== 2;
```

### 2.7. 병합연산자

- 내가 FE라면 반드시 알아야 한다
- 일반적으로 기본값 셋팅에서 활용
- falsy가 아니라 `null, undefined`일때만 값을 비교할 경우
- 아래에서 코드는 `0`값이 나오길 기대하고 코드 진행함

- null 은 개발자가 값이 없다고 지정하는것
- undefined는 js에서 초기값으로 값이 없다고 지정해주는 것

```js
let userPoint = 0;
let displayPoint = userPoint || 500000;
console.log(displayPoint); // 500000

let userPoint = undefined;
let displayPoint = userPoint || 500000;
console.log(displayPoint); // 500000
```

- `??`연산자는 null과 undefined 만 비교한다
- 나머지는 `||` 과 같다
- falsy의 조건null 과 undefined 외에 참으로 인식한다.

```js
let userPoint = 0;
let displayPoint = userPoint ?? 500000;
console.log(displayPoint); // 0
```

```js
let formInput = {
  name: "",
  email: null,
  phone: undefined,
};
const name = formInput.name ?? "이름 없음"; // "" 출력
const email = formInput.email ?? "이메일 없음"; // 이메일 없음 출력
const phone = formInput.phone ?? "전화 없음"; // 전화 없음 출력
```

### 2.8. 옵셔널체이닝 (?.)

- FE라면 필수!
- 대상은 객체이다 `{ 속성: 값, }`
- 객체의 `속성 존재 여부`에 따라 코드 진행

```js
const user = {
  profile: null,
};
const age = user.profile.age; //  null Error 발생 후 서비스 멈춤

const user = {
  profile: { name: "홍길동" },
};
const age = user.profile?.age ?? "정보가 없어서 나이를 알 수 없습니다.";
// profile안에 age속성이 있는지 파악 후 없다면 undefined를 띄우므로 서비스를 유지한다
// age 에 null이거나 undefined 이므로 "정보가 없어서..."를 출력
```

### 2.9. 3항 연산자

- 연산자가 3개라서 3항 연산자라고 한다
- `결과 = 조건식 ? 참일때 결과 : 거짓일때 결과;`
- 활용 빈도가 매우 높다

```js
const userRole = "ADMIN"; // 사용자 등급
// const url = 조건 ? 참 : 거짓 ;
const url = userRole === "ADMIN" ? "admin.html" : "guest.html";
// ADMIN이면 admin.html 띄우고, 아니면 guest.html을 뜨운다
```

```js
const age = 10;
const result = age < 19 ? "동의서필요" " "성인 인증"
```

```js
const goodCount = 10;
const resule = goodCount > 0 ? "재고가 있어요" : "재고가 없어요";
```

```js
const user = {
  isLogin: true,
  name: "dkdldb",
};
const result = user.isLogin ? `${user.name}님 반가워요.` : "로그인 해 주세요.";
```

```js
let num = 5;
let result = num % 2 === 0 ? "짝수" : "홀수";
```

## 3. 조건문(Condition)

### 3.1. if 문

- `참/거짓`을 판단하여 코드 분기 실행함.
- 모양 1.

```js
if(조건) {

  조건이 참이면 실행;

}
```

- 모양 2.

```js
if(조건) {

  조건이 참이면 실행;

}else{

  조건이 거짓이면 실행;

}
```

- 모양 3.

```js
if(조건1) {

  조건1 이 참이면 실행;

}else if(조건2){

   조건2 가 참이면 실행;

}else if(조건3){

   조건3 이 참이면 실행;

}else{

  모든 조건에 거짓이면 실행;

}
```

```
<한줄 요약>
if: 조건이 참일 때 실행

else: 조건이 거짓일 때 실행

else if: 여러 조건을 순차적으로 체크

if는 단독으로 가능하지만 else는 반드시 if와 함께 사용
```

- 예제) 로그인이 된 경우의 메시지 출력하기

```js
const islogin = true;

if (isLogin) === true){
  console.log("로그인하셨네요. 반갑습니다.");
}

// 실무에선 이렇게 쓰임
const islogin = true;
if (isLogin){
  console.log("로그인하셨네요. 반갑습니다.");
}

//조건이 심플(1줄정도)하다면 중괄호생략가능, 코드가독성 떨어짐
if (isLogin)  console.log("로그인하셨네요. 반갑습니다.");

```

- 예제) 로그인 된 경우의 메시지와 로그인 안된 경우의 메시지 출력하기.

```js
const isLogin = true;
if (isLogin) {
  console.log("어서오세요.");
} else {
  console.log("로그인 하셔야 합니다.");
}
```

- 예제) 나이에 따라서 다른 메시지 출력하기 (조건이 2개이상인 경우)

```js
const age = 19;
if (age >= 19) {
  console.log("20 대 이시네요.");
} else if (age >= 30) {
  console.log("30대 이시네요.");
} else if (age >= 40) {
  console.log("40대 이시네요.");
} else if (age >= 50) {
  console.log("50대 이시네요.");
} else if (age >= 60) {
  console.log("어르신 이시네요.");
} else {
  console.log("미성년 이시네요.");
} // 20 넘어가면 20대 이시네요만 뜬다 (오류)

//수정ver
const age = 100;
if (age >= 60) {
  console.log("어르신 이시네요.");
} else if (age >= 50) {
  console.log("50대 이시네요.");
} else if (age >= 40) {
  console.log("40대 이시네요.");
} else if (age >= 30) {
  console.log("30대 이시네요.");
} else if (age >= 20) {
  console.log("청년 이시네요.");
} else {
  console.log("미성년 이시네요.");
}
```

- 예) 사용자가 입력한 항목이 값이 `없을 경우` 메시지 보내기 (필수 입력 사항)

```js
const name = "홍길동";
const pass = "1234";
const useInfoCheck = false; // 사용자 정보 활용동의
const useEmailCheck = false; // 이메일 수신 동의

if (name === "") {
  alert("이름을 입력하세요.");
}
if (!name) {
  alert("이름을 입력하세요.");
} // 두번 쓰기에 가독성 떨어지니..

// 이렇게 조건을 나열해도된다.
if (name === "" || !name) {
  alert("이름을 입력하세요.");
}

// return : 특정조건을 실행하면 더이상 실행하지 않도록 한다.
if (name === "") {
  alert("이름을 입력하세요.");
  return;
}
if (!name) {
  alert("이름을 입력하세요.");
  return;
}

if (pass === "") {
  alert("비밀번호 입력하세요.");
  return;
}
if (!pass) {
  alert("비밀번호 입력하세요.");
  return;
}

if (useInfoCheck === false) {
  alert("개인정보 동의를 체크하세요.");
  return;
}
if (!useInfoCheck) {
  alert("개인정보 동의를 체크하세요.");
  return;
}
if (useEmailCheck === false) {
  alert("이메일 수신 동의를 체크해주세요.");
  return;
}
if (!useEmailCheck) {
  alert("이메일 수신 동의를 체크해주세요.");
  return;
}

console.log("저희 서비스를 자유롭게 활용하세요.");
```

### 3.2. switch 문

- `여러 개의 값` 중 하나의 `값`이 같은지 판단 후 실행
- 즉 (조건)과 같은 값을 찾아 해당 구문 실행

```js
switch (값) {
  case 비교값1:
                실행 코드
    break;
  case 비교값2:
                실행 코드
    break;
  case 비교값3:
                실행 코드
    break;
  default:
              실행 코드
    break;
}
```

- 예) 엘리베이터 층 예제

```js
const layer = 5; // 값

switch (layer) {
  case 1:
    console.log("1층 내리세요.");
    break;
  case 2:
    console.log("2층 내리세요.");
    break;
  case 3:
    console.log("3층 내리세요.");
    break;
  case 4:
    console.log("4층 내리세요.");
    break;
  case 5:
    console.log("5층 내리세요.");
    break;
  default:
    console.log("당신은 내릴 층이 없습니다.");
    break;
}
```

```js
switch (userRole) {
  case "MEMBER":
    console.log("회원");
    break;
  case "ADMIN":
    console.log("관리자");
    break;
  default:
    console.log("비회원");
    break;
}
```

## 4. 반복문(Loop)

- 동일한 실행을 반복하는 문법

### 4.1. for 구문

- 주어진 `횟수만큼` 반복 실행 (`개발자가 반복횟수를 아는 경우`)
- for문 안에 중첩으로 for문을 쓸 수 있다.

```js
for(초기값; 조건식; 증감식) {
  할일 코드 작성
}

* 초기값은 단 한 번만 실행
* 조건식은 결과가 true/false , 반복을 계속할지 여부를 판단 (참이면 반복, 거짓이면 종료)
* 증감식은 반복이 끝날 때마다 실행하여 값을 변화시킴 (for문은 참이면 계속 실행해서 컴퓨터다운되니 조건식을 false 로 만들어 종료시키는 것)

```

```js
for (let i = 0; i < 10; i = i + 1) {
  console.log(`현재 ${i} 입니다.`);
}

const total = 10; //반복횟수 , 보통은 변수로 따로 빼둔다.

for (let i = 0; i < total; i++) {
  console.log(`현재 ${i} 입니다.`);
}
```

```js
// 장바구니 담긴 제품 가격 모음
const bucketsArr = [1000, 500, 700, 400];
const total = bucketsArr.length; //반복횟수 , length 는 배열의 길이를 알려준다
let totalPriceFor = 0;
for (let i = 0; i < total; i++) {
  totalPriceFor = totalPriceFor + bucketsArr[i];
  //totalPriceFor += bucketsArr[i]
}
```

- 예) 제품의 이름과 가격 및 재고를 html 태그로 출력하는 예제
- 예) 백엔드에서 제품의 목록은 jsom으로 주어진다

```js
// 백엔드에서 가져온 자료 json
const goodData = [
  { id: 542, name: "사과", price: 1000, stock: 10 },
  { id: 5557, name: "딸기", price: 1000, stock: 0 },
  { id: 2147, name: "키위", price: 1000, stock: 5000 },
];

//반복횟수
const total = goodData.length;
for (let i = 0; i < total; i++) {
  // 제품 1개를 뽑아서 보관한다.
  const good = goodData[i];
  // html 만들기
  const tag = `<div id="${good.id}" class="good-box">
      <p>제품명 : ${good.name}</p>
      <p>가격 : ${good.price}</p>
      <p>재고수량 : ${good.stock || "재고가 없어요"}</p>
    </div>`;
}
```

- 예 ) 구구단
- `break`는 가까운 for반복문에서 빠져나오고 종료하기
- `continue`는 가까운 for반복문에서 해당조건은 건너띄고 계속 실행.

```js
const total = 9;
for (let i = 1; i <= total; i++) {
  if (i === 6) {
    break; //종료하기
  }
  console.log(i + "단");
  for (let j = 1; j <= total; j++) {
    console.log(`${i} * ${j} = ${i * j}`);
  }
}

const total = 9;
for (let i = 1; i <= total; i++) {
  if (i % 3 === 0) {
    continue; // 3으로 나눠서 떨어지는 것들은 건너띈다
  }
  console.log(i + "단");
  for (let j = 1; j <= total; j++) {
    console.log(`${i} * ${j} = ${i * j}`);
  }
}
```

### 4.2. for in 구문

- for 문으로 모두 가능핟.
- for 를 `객체를 대상`으로 편리하게 사용하도록 지원하는 문법

```js
// for in 구문 예제 (대상은 객체 속성 반복)
const singer = {
  id: "123",
  name: "아이유",
  age: 30,
  city: "서울",
};
// 개발자가 직접 알아내는 경우 , city가 있는줄모르면 알아내기 힘들다
console.log(singer.id);
console.log(singer.name);
console.log(singer.age);

// 반복문 활용
for (let key in singer) {
  console.log(key); //키명(칼럼명)을 볼수있다
  // console.log(singer.key);
  // for in 에서는 . 찍지않고
  console.log(singer[key]); // []로 쓴다  점찍고 접근하는건 직접접근이기 때문에.
}

//예제 2

const bts = {
  id: "123",
  name: "bts",
  age: [30, 20, 33],
  city: "서울",
};

for (let key in bts) {
  console.log(`${[key]} : ${bts[key]}`);
}
```

### 4.3. for of 구문

- for 문으로 모두 가능하다.
- for 를 `배열, 문자열등을 대상`으로 편리하게 사용하도록 지원하는 문법
- iterator 즉, `순서가 있는 데이터형`에서 사용

```js
const citiesArr = ["대구", "서울", "부산"];
for (let city of citiesArr) {
  console.log(city);
}

const words = "안녕하세요. 반가워요.";
for (let i of words) {
  console.log(i);
}
```

### 4.4. while 구문

- `조건이 참`인 동안 무한히 반복함.
- 반복에 횟수를 모르는 경우

```js
while (조건) {
  할일;
  반드시 거짓으로 만들어야 끝난다
}

let count = 0;

while (count < 5) {
  count = count + 1;
  console.log(count);
}


```

### 4.5. do while 구문

- while 과 다르게 일단 실행하고 조건 검사

```js
let count = 0;

do {
  count = count + 1;
  console.log(count);
} while (count < 5);
```

## 5. 함수(Function)

- 독립된 역할별 기능을 `{}` 묶고 `function 함수명()` 을 주어서 관리
- 여러번 재활용(`호출, call`)한다 : `함수명()`
- 문서 즉 설명서(JSDoc)가 잘 만들어져야 함
- 기능 예외처리를 잘 해야 한다

### 5.1. 함수가 왜 필요하지?

- 반복되는 1줄 이상의 코드가 있을 때
- 코드에 대한 가독성이 필요할 때
- 한번에 코드를 수정하여 다양한 곳에 동시에 반영되는 것을 원할 때
- 코드에 안정성을 생각할 때
- 협업을 한다면 기능을 만들어서 재활용하여야 하며 이때 함수를 만들 것을 고려해보자

```js
// 아래는 사용자의 명단과 반가워요라는 메시지를 출력하는 기능이다
let user_1 = "홍길동";
let user_2 = "김길동";
let user_2 = "박길동";
let user_2 = "고길동";
let user_2 = "정길동";
console.log(user_1 + "님 반가워요!");
console.log(user_2 + "님 반가워요!");
console.log(user_3 + "님 반가워요!");
console.log(user_4 + "님 반가워요!");
console.log(user_5 + "님 반가워요!");
```

- ↑ 기능을 구분해서 관리하고 싶다 (여기서는 회원 명단 및 인사 기능)

```js
// 아래는 사용자의 명단과 반가워요라는 메시지를 출력하는 기능이다

function useMember() {
  let user_1 = "홍길동";
  let user_2 = "김길동";
  let user_2 = "박길동";
  let user_2 = "고길동";
  let user_2 = "정길동";
  console.log(user_1 + "님 반가워요!");
  console.log(user_2 + "님 반가워요!");
  console.log(user_3 + "님 반가워요!");
  console.log(user_4 + "님 반가워요!");
  console.log(user_5 + "님 반가워요!");
}

// 함수 활용, 함수 호출, 함수 call
userMember();
```

### 5.2. 함수 만들기

```js
// 함수 이름은 '동사'로 짓는다
function 함수명() {
  기능1;
  기능2;
  기능3;
}

function 함수명(재료1, 재료2, 재료3) {
  재료1 처리 기능1;
  재료2 처리 기능2;
  재료3 처리 기능3;
}

```

### 5.3. 계산기 만들기

- 단계 1 필요한 작업 나열

```js
//계산기 만들기
const result_1 = 5 + 4;
const result_2 = 8 + 3;
const result_3 = 7 + 2;
const result_4 = 6 + 1;
```

- 단계 2 함수화 하기

```js
//계산기 만들기

function result_1() {
  5 + 4;
}
function result_2() {
  8 + 3;
}
function result_3() {
  7 + 2;
}
function result_4() {
  6 + 1;
}
```

- 단계 3 재료만 다르고 하는 일은 + 기능 파악

```js
//계산기 만들기

function add(재료, 재료2) {
  재료1 + 재료2;
}
add(5, 4);
add(8, 3);
add(7, 2);
add(6, 1);
```

- 단계 4 minus 기능 만들기

```js
//계산기 만들기

function minus(매개변수1, 매개변수2) {
  매개변수1 - 매개변수2;
}
minus(5, 4);
```

- 단계 5. 기능에 예외처리(오류 처리) 적용하기
- 오류 : Error 및 원하지 않는 결과

```js
function add(매개변수1, 매개변수2) {
  매개변수1 + 매개변수2;
}
function minus(매개변수1, 매개변수2) {
  매개변수1 - 매개변수2;
}

add(5, "100"); // 원하지 않는 결과이므로 오류 (숫자+글자)
add(5, undefined); // 원하지 않는 결과이므로 오류
add(5); //원하지 않는 결과이므로 오류
```

```js
function add(매개변수1, 매개변수2) {
  //방어코드 (예외처리)
  if (매개변수1 === undefined) {
    return alert("매개변수 1을 입력하세요.");
  }
  if (매개변수2 === undefined) {
    return alert("매개변수 2을 입력하세요.");
  }
  매개변수1 + 매개변수2;
}
function minus(매개변수1, 매개변수2) {
  매개변수1 - 매개변수2;
}
```

### 5.4. JSDoc 으로 함수 사용에 대해서 안내(설명서)하기

- jsDoc 기본 이해
- jsDoc 작성이 번거롭더라도 팀내에서는 협의를 통해 작성여부를 결정하자
- 더불어 ESLint도 설정해야한다. ESLint는 JSDoc과 맞지 않으면 오류를 띄워서 JS실행을 못하게 한다
- 매개변수를 parameter 라고한다 (@param)

```js
/**
 * 두개의 변수를 받아서 덧셈하는 기능
 * @param {number} numA - 첫번째 숫자
 * @param {number} numB - 두번째 숫자
 * @returns {number} 두 숫자의 덧셈결과
 */
function add(numA, numB) {
  if (numA === undefined) {
    return alert("첫번째 매개변수 입력해주세요");
  }
  if (numB === undefined) {
    return alert("두번째 매개변수 입력해주세요");
  }
  return numA + numB;
}
```

### 5.5 JSDoc 을 이용한 계산기 함수 만들어보기

````js
/**
 * 숫자 더하기 기능
 * @param {number} a
 * @param {number} b
 * @returns {number} 덧셈 결과
 */

function add(a, b) {
  return a + b;
}

/**
 * 숫자 빼기 기능
 * @param {number} a
 * @param {number} b
 * @returns {number} - 뺄셈 결과
 */
function minus(a, b) {
  return a - b;
}

/**
 * 숫자 곱하기 기능
 * @param {number} a
 * @param {number} b
 * @returns {number} - 곱셈 결과
 */
function multi(a, b) {
  return a * b;
}
/**
 * 숫자 나누기 기능
 * @param {number} a
 * @param {number} b
 * @returns {number} - 나눗셈 결과
 * ------ 호출예 -----
 * ```javascript
 * let result = divide(5, 4)
 * ```
 */

function divide(a, b) {
  if (b === 0) {
    return alert("분모는 0이 아니어야 합니다");
  }
  //데이터 알아내고, 타입 비교하기
  if (typeof a !== "number") {
    return alert("분자는 숫자여야 합니다");
  }
  if (typeof b !== "number") {
    return alert("분모는 숫자여야 합니다");
  }

  return a / b;
}

// 덧셈 사용
const resultAdd = add(5, 4);
const resultMinus = minus(5, 4);
const resultMulti = multi(5, 4);
const resultDevide = divide(5, 4);
````

- 추가 함수

````js
// 외부로 공개할 함수 생성
/**
 * 계산기 기능
 * 계산기 기능은 +, -, *, / 기능이 있습니다.
 * @param {string} symbol +, -, *, / 기호중 1개 입력
 * @param {number} a 숫자 입력
 * @param {number} b 숫자 입력
 * @returns {number} 결과값은 숫자
 *
 * 사용 예)==============
 * ```jsvascript
 * const result = calcurator("+", 5, 4);
 * ```

*/

function calcurator(symbol, a, b) {
  if (typeof symbol !== "string") {
    return alert("기호를 입력하세요");
  }

  let result = 0;

  switch (symbol) {
    case "+":
      result = add(a, b);
      break;
    case "-":
      result = minus(a, b);
      break;
    case "/":
      result = divide(a, b);
      break;
    case "*":
      result = multi(a, b);
      break;
    default:
      return alert("올바른 기호를 입력해 주세요.");
  }
  return result;
}
````

```js
/**
 * 메시지를 콘솔에 출력하기
 * @param {string} message - 출력할 메시지
 */

function showMessage(message) {
  console.log(message);
}
showMessage("안녕");
showMessage("홍길동 반가워");
```

```js
/**
 * 배열을 받아서 요소를 출력하는 함수
 * @param { number[] } arr - 숫자모음 배열
 */
function showArr(arr) {
  for (let i = 0; ㅑ < arr.length; i++) {
    console.log(arr[i]);
  }
}
```

```js
/***
 * 객체의 속성값을 출력하는 기능
 * @param { { id:number, nicName:string, age:number } }
 */

function showUser(user) {
  console.log(user.id);
  console.log(user.nickName);
  console.log(user.age);
}
```

### 5.7. 함수의 기본 값 설정하기

````js
/***
 * 나이를 10살 더하여서 출력함.
 * @param {munber} age - 현재나이 입력
 * ```jsvascript
 * const result = showAge(10); // 20
 * ```
 */

// (매개변수명=기본값)  : 매개변수에 초기 기본값을 설정할 수 있다
function showAge(age = 0) {
  return age + 10;
}
````

### 5.8. 매개변수의 총 갯수 자동으로 알아내기

- js에서 여러가지(가변) 매개변수를 알아서 불러오게할 수 있다
- aguments -

```js
/**
 * 입력된 매개 변수 만큼 총합계산하기
 * Rest 파라메터 이용하기
 * @param {...number} numbers - 숫자 값
 */
function showTotal(a, b, ...rest) {
  console.log(a);
  console.log(b);
  console.log(rest);
  let total = 0;
  for (let i = 0; i < rest.length; i++) {
    total = total + rest[i];
  }
  return total;
}

const result = showTotal(4, 5, 6, 7, 8, 9, 1, 2, 0);
```

- ...변수명 : Rest Parameter , 전달된 매개변수에 정확한 값만 배열로 만든다 (2015이후로나온 신규문법)
- Rest Parameter는 기본 매개변수 적용 후, `나머지를 배열로 추출` 한다. (↔ arguments는 전체 다 추출)

## 6. 함수 선언법

- 1. 일반적 함수 만드는 법

```js
function 함수명(매개변수) {
  return 결과값;
}

함수명(매개변수);
```

- 2. `변수의 값`으로 함수 만드는 법
- 이름없는 함수 (익명함수?)

```js
const 변수명 = function (매개변수) {
  return 결과값;
};

변수명(매개변수);
```

- 2-1. 왜 `변수명 = function` 형태가 필요할까?
- 콜백 : 부르고 후에 실행
- 불러와놓고 조건에 따라 실행한다.

```js
function add() {
  return 1 + 2;
}
// add();

const addFun = function () {
  return 1 + 2;
};
// addFun();

const minusFun = function () {
  return 1 - 2;
};
// minusFun();

function test(_func) {
  _func();
}

test(add); // 값이 아니라서 안된다.
test(addFun);
test(minusFun);
```

- 아래코드는 특히 취리를 살펴보자

```js
add(); // 호이스팅이 되므로 괜찮다
addFN(); // 호이스팅 에러 발생한다 (주의하자)
function add() {}
const addFN = function () {};
```

- 결론 : 완성하고 사용하자, 함수는 코드 젤 윗줄에 적어야 한다. (호이스팅이 되서 실행은 되지만..)
