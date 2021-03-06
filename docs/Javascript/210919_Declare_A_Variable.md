# 변수 선언하기
- 이전 Javascript는 var가 변수 선언의 유일한 방법이었음

### 1. const 키워드
- 상수(constant)는 알다시피 값을 변경할 수 없는 변수
- 상수가 없던 시절에는 모든 값을 변수에 넣어 사용했었음
``` javascript
// 상수가 없던 시절
var pizze = true;
pizza = false;
console.log(pizza); // ** false **
```
``` javascript
// 상수가 추가된 후
const pizza = true;
pizza = false; // ** Uncaught TypeError: Assignment to constant variable. **
```

### 2. let 키워드
- <b>구문적인 변수 영역 규칙(lexical variable scoping)</b> 지원
- Javascript에서는 중괄호(**{ }**)를 사용해 코드 블록을 만듬
- 함수의 경우 코드 블록이 별도의 변수 영역, 하지만 **if/else** 문은 다르다.<br>
  (신기하게도 Javascript는 다른 언어와 다르게 if/else 문의 블록이 별도의 영역을 구성하지 않는다.)
- 아래 예시와 같이 if 블록 안의 topic 변수를 변경하면 if 블록 밖의 topic 변수 값도 변경됨<br>
(실제로는 두 변수가 같은 변수 - 호이스팅(Hoisting))
``` javascript
var topic = "자바스크립트";
if (topic) {
    var topic = "리액트";
    console.log('블록', topic) // ** 블록 리액트 **
}
console.log('글로벌', topic) // ** 글로벌 리액트 **
```
- let 키워드를 사용하면 변수의 영역을 코드 블록 안으로 한정시킬 수 있음
``` javascript
var topic = "자바스크립트";
if (topic) {
    let topic = "리액트";
    console.log('블록', topic); // ** 블록 리액트 **
}
console.log('글로벌', topic) // ** 글로벌 자바스크립트 **
```

- 위와 같이 중괄호로 새로운 영역을 만들어내지 못하는 다른 부분은 for 루프가 있음
- 아래 루프에서 컨테이너 안에 5개의 div를 만들고 각 div에 onclick 핸들러가 할당됨<br>
  for 루프 안에서 i를 선언해도 글로벌 영역에 i가 생성되므로 5개의 div 박스 중 어느 것을 클릭하건,<br>
  i의 값은 5로 표시됨
``` javascript
// i는 항상 5로 표시됨
var div, container = document.getElementById('container');
for (var i=0; i<5; i++) {
    div = document.createElement('div');
    div.onclick = function() {
        alert('이것은 박스 #' + i + '입니다.');
    }
    container.appendChild(div);
}
```
``` javascript
// let으로 i의 영역 제한
const container = document.getElementById('container');
let div;
for (let i=0; i<5; i++) {
    div = document.createElement('div');
    div.onclick = function() {
        alert('이것은 박스 #' + i + '입니다.');
    }
    container.appendChild(div);
}
```

### 호이스팅(Hoisting) 이란?
- 위 내용을 읽다보면 호이스팅이라는 개념이 나와서 찾아보았다.

- 말그대로 끌어올린다는 의미로, 변수와 함수의 선언부분이 최상단으로 끌어올려지는 Javascript의 특성


### 3. 템플릿 문자열
- 템플릿 문자열을 문자열 연결 대신 사용할 수 있음
- 문자열 중간에 변수를 삽입 (<b>${ }</b>를 사용)
``` javascript
// 전통적 방법
console.log(lastName + ", " + firstName + " " + middleName);
```
``` javascript
// 템플릿 사용
console.log(`${lastName}, ${firstName} ${middleName}`);
```
- ${ }에는 값을 만들어내는 자바스크립트 식은 어떤것이든 들어갈 수 있음
- 공백, 탭, 개행문자 등을 유지
``` javascript
// 템플릿 문자열은 공백을 유지해줌
const email = `
주문 상세 정보:
  ${lastNmae} ${firstName} ${MiddleName}
  ${qty} x $${price} = $${qyt*price} 공연 : ${event}
`
```
- 과거 Javascript에서 HTML 문자열을 직접 사용하려면 모든 문자열을 +로 연결하여 한줄로 처리해야했었음
- 이제는 문자열 안의 공백 문자가 제대로 처리되기 떄문에 코드에 이해하기 쉽게 잘 정렬한 HTML을 넣을 수 있음

``` javascript
// HTML코드가 잘 정렬되어 이해하기 쉬움
document.body.innerHTML = `
<section>
  <header>
    <h1>The HTML5 Blog</h1>
  </header>
  <article>
    <h2>${article.title}</h2>
    ${article.body}
  </article>
  <footer>
    <p>copyright ${new Date().getYear()} | THE HTML5 Blog</p>
  </footer>
</section>
```