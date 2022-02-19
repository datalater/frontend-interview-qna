# var, let, const

## 💁‍♂️ 질문 목록

```txt
Q1. block scope란 무엇인가요?
Q2. var, let, const의 차이는 무엇인가요? (function scope와 block scope의 개념에서)
```

## 💁‍♀️ 답변 목록

<details>
<summary><strong>Q1. block scope란 무엇인가요?</strong></summary>

- 블록 스코프는 블록 내부에 선언한 변수는 블록 내부에서만 사용할 수 있는 것을 뜻합니다.
- 스코프는 변수를 참조할 수 있는 유효 범위를 뜻하는데, 블록 스코프는 변수의 유효 범위가 블록 내부인 것입니다.

</details>

<details>
<summary><strong>Q2. var, let, const의 차이는 무엇인가요? (function scope와 block scope의 개념에서)</strong></summary>

스코프 측면에서 `let`이나 `const`는 블록 스코프를 갖지만 `var`는 함수 스코프를 갖습니다. 변수가 블록 스코프를 따르면 블록 외부에 선언한 변수와 블록 내부에 선언한 변수가 이름이 동일하더라도 서로 다른 변수로 취급됩니다.

```js
let a = 3;
{
  let a = 100;
  console.log(a); // 100
}
console.log(a); // 3
```

하지만 `var`로 선언한 변수는 블록을 무시하기 때문에 블록 내부에 새롭게 선언하더라도 블록 외부에 동일한 이름의 변수가 있다면 이를 덮어쓰게 됩니다.

```js
var a = 3;
{
  var a = 100;
  console.log(a); // 100
}
console.log(a); // 100
```

또한 호이스팅의 형태가 다른데, `var`로 선언한 변수는 선언과 동시에 초기화가 되지만, `let`이나 `const`로 선언한 변수는 선언만 호이스팅 됩니다. 따라서 `var`로 선언한 변수는 변수를 정의하기 전에 값을 참조할 수 있지만, `let`이나 `const`로 선언한 변수는 변수를 정의하기 전에 참조하려고 하면 값이 초기화되어 있지 않으므로 `ReferenceError`가 발생합니다.

```js
console.log(a); // undefined

var a = 3;
```

```js
console.log(a); // ReferenceError

let a = 3;
```

</details>

## 💁 추가 질문

> 질문 목록 외에 스터디하면서 새로 생긴 질문을 답변과 함께 적습니다.

없음

## 📚 함께 읽기

- [오래된 var](https://ko.javascript.info/var#ref-1849)
- [변수의 유효범위와 클로저](https://ko.javascript.info/closure)
