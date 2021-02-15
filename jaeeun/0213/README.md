## 📆 2021-02-13

### 📖 리액트를 다루는 기술

###

#### 3장. Component

- 클래스형 vs 함수형 컴포넌트의 차이

#####

- props 및 state 사용 방법과 활용

#####

- state 와 useState

_새로운 컴포넌트를 만들 때는 **useState**를 사용할 것을 권장❗_

##

#### 4장. Event Handling

####

- 리액트 이벤트 시스템

  - 이벤트 이름은 카멜표기법으로 작성

  - 이벤트를 설정 시, ~~자바스크립트 코드가 아닌~~ **함수 형태의 객체**를 전달

  - DOM요소에만 이벤트를 설정할 수 있음
    _직접 만든 컴포넌트에는 이벤트를 자체적으로 설정할 수 없음_

######

```javascript
<MyComponent onClick={hello} />

// MyComponent를 클릭할 때, hello함수를 실행하는 것이 아니라,
// 그냥 이름이 onClcik인 props를 MyComponent에게 전달만 함!
```

- 함수형 컴포넌트로 이벤트 구현 실습
