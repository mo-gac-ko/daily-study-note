## 📆 2월 17일 공부 기록

> JavaScript 반복문 (for, forEach 등)의 종류와 퍼포먼스 비교

    일반적으로 알고있는 for문, $.each, forEach, map, filter 등 정말 많은 종류가 있다.

    주로 하나의 메서드로 대부분 것들을 할 수 있지만, 어떨때는 each를 써야 하고 또 어떤 경우에는 filter가 좋은지를 정확히 알고 쓰지 못했고 왜 이렇게 따로따로 만들어놨을까 라는 생각도 했다. 아래 포스트에서 각 메서드들을 어떨때 어떻게 사용해야하는지 정리하고 성능비교도 해보자!

    [출처] https://daesuni.github.io/Loop-performance/

<br />

1. for loop

- 가장 빠르고 단순하다. 그래서 효율적이다.
- 모든 자료형에 대해 사용이 가능하다.
- 중간에 loop 건너뛰기나 종료가 가능하다. (continue or - break)
- 반복범위 컨트롤이 가능하다. (i++, i–, i+=2\*i 등)
- 변수를 활용할 수 있다. (var i 값을 사용할 수 있다)

2. forEach

- 빠른편이다.
- Array객체에서 사용이 가능하다.
- 일반 for문보다 가독성이 좋고, 객체형을 다루기가 쉽다.
- for문과 다르게 중간에 끊을 방법이 없다. (return으로 - skip가능)
- return값을 받지 못한다.

3. filter

- 빠른편이다.
- Array객체에서 사용이 가능하다.
- chainable하다.
- 빈 배열 요소를 반환하지 않는다.
- 대용량 배열 처리시 메모리 overflow 가능성이 있다.
- return값은 true/false이며, 요소를 반환한다.

4. map

- 빠른편이다.
- Array객체에서 사용이 가능하다.
- chainable하다.
- 대용량 배열 처리시 메모리 overflow 가능성이 있다.
- return값 자체를 반환한다.

5. reduce

- reduce는 위에 나왔던 반복문들과는 약간 개념과 사용법이 다르다.

```js
var arr = [1, 2, 3, 4, 5];
var newArr = arr.reduce(function (acc, v, i, arr) {
  return acc + v;
});
// 15
```

reduce의 가장 큰 특징으로는 첫번째 인자인 accumulator 이다. accumulator 는 return값을 누적하는데, 계속해서 전달받아서 사용할 수도 있다.

두번째 특징은 accumulator의 초기값을 설정할 수 있다는 점이다. optional하며 생략시에는 첫번째 return값이 된다. 아래 예시를 보자.

```javascript
var arr = [1, 2, 3, 4, 5];
var newArr = arr.reduce(function (acc, v, i, arr) {
  return acc + v;
}, 100);
// 115
```

첫번째 예시와 다르게 초기값 때문에 115라는 값이 나오게 됬다. 어떻게 활용하느냐에 따라 reduce는 강력하고 확장성이 높다. accumulator의 값은 배열이 될수도 있고, object가 될수도 있다.

<br />

> 성능비교 차트
> ![image](https://user-images.githubusercontent.com/55027765/108711658-0583e080-7559-11eb-8bad-841e3df3bd64.png)

<br />
<br />

> 각 브라우저별 반복문의 퍼포먼스  
> [출처] https://velog.io/@zuyonze/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%84%B1%EB%8A%A5-%EC%B5%9C%EC%A0%81%ED%99%94%EC%97%90-%EB%8C%80%ED%95%9C-%EC%9D%98%EB%AC%B8-glk00t4bxk

Chrome
![image](https://user-images.githubusercontent.com/55027765/108711805-3c59f680-7559-11eb-801f-a95f76a9c888.png)

Firefox
![image](https://user-images.githubusercontent.com/55027765/108711876-51cf2080-7559-11eb-934d-cfb7ec0e6add.png)

삼성인터넷브라우저 - 갤럭시S10 5g
![image](https://user-images.githubusercontent.com/55027765/108711946-690e0e00-7559-11eb-8f8f-6c0c8464645d.png)

<br/>

> 결론

    똑같은 코드여도 실행환경에 따라 퍼포먼스는 천차만별이다.
    그러나 대체적으로 for of나 original for문이 퍼포먼스가
    우수하다고 보여진다.
