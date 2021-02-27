## 📆 2월 27일 공부 기록

원래 공부하려고했던게 useRef랑 useMemo, useCallback, useReducer
등 이였는데 이게 제로초 강좌에 있어서 앞에서부터 차근차근 강좌를
보는중

    ZeroCho의 React강좌를 통해 Create-react-app을 사용하지 않고
    react 프로젝트가 어떻게 돌아가는지에 대한 이해를 배운다.

<br/>

> React Babel

- jsx문법을 지원하기 위해 사용,  
  최신문법을 옛날문법으로 바꿔주는 역할

---

<br/>

> React WebPack

- react를 통해 작성된 분리된 컴포넌트들을  
  index.html에서 하나의 js파일에 합쳐서 쓰기 위해 사용

---

<br/>

### Import와 Require의 차이

    require은 node의 모듈 시스템이다.
    (module.exports = something;하면 다른파일에서 사용 가능)

    {}는 구조분해(디스트럭처링)문법
    exports되는 게 객체나 배열이면 구조 분해 할 수 있다.

    ex)
    export default로 된것은 import something from "something";
    (default는 한번만 쓸 수 있음, module.exports와 export 는 다름)
    export something으로 된것은 import {something} from "something";

    바벨이 뒤에서 import를 require로 변경해준다.

    쉽게 생각하면 node에서는 require, module.exports쓰고,
    React에서는 import와 export 쓴다고 생각하면 된다.
    거의 둘은 호환이 된다. 엄밀히는 다르긴하다.
