## 📆 2월 16일 공부 기록

## 비교 연산자

### 문자열 비교

    사전 순으로 문자열 비교

### 다른 형을 가진 값의 비교

    비교 대상의 값들을 숫자형으로 변환하여 숫자형 값을 비교

```js
let a = 0,
  b = "0";
Boolean(a); // fasle, 논리 연산에서 0은 falsy
Bollean(b); // true, 빈값이 아니라면 truthy
a == b; // true, 숫자형으로 변환하여 값만 비교
```

### 일치 연산자

    형 변환 없이 값과 형태를 비교

### null / undefined 비교

```js
null == undefined; // true
null === undefined; // false

null; // return 0
undefined; // return NaN
```

- 일치 연산자를 제외한 비교 연산자의 피연산자에 <code>undefined</code>나 <code>null</code>이 오지 않도록 주의
- <code>undefined</code>나 <code>null</code>이 될 가능성이 있는 변수가 비교 연산의 피연산자가 되지 않도록 주의

## 조건부 연산자 '?'

    if else를 더욱 짧고 간결하게 표현할 수 있는 연산자

```js
let result = condition ? value1 : value2;
// condition이 truthy 하면 value1, falsy 하다면 value2를 반환
```
