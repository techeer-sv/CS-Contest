1. **React에서 `setState` 함수는 동기적으로 동작하나요, 아니면 비동기적으로 동작하나요? `setState`가 적용되는 동작 방식에 대해 설명해주세요.**

- 답 : 리액트에서 setState는 불 필요한 리렌더링을 방지하기위해 한번에 데이터를 일괄처리합니다. 때문에 비동기적으로 동작합니다.
  setState안에 데이터를 넣으면 state가 바뀝니다. 하지만 불변성을 지키지않는다면 또는 같은 값을 넣는다면 데이터가 바뀌지않습니다.
  그 이유는 setState에서 불 필요한 리렌더링을 setState hook안에서 방지를 하기때문입니다.
  예를 들자면 state가 기존 데이터고 newState가 들어온 데이터라면 hook안에는 이런 코드가 들어있습니다.
  if (newState === state) return;
  if (JSON.stringify(newState) === JSON.stringify(state)) return;
  또한 batch처리라고 불리는데 동시에 여러 setState가 실행될 경우가 있습니다.
  setState는 데이터를 일괄처리한다고 했는데 이 경우 예를 들자면
  const [count,setCount]=useState(1);
  setState(count+1);
  setState(count+1);
  을 한다면 state의 값은 3이 아니라 2가 나오게 됩니다.
  이 코드를 뜯어보면 일괄처리하기 때문에 {count:1 , count:count+1, count:count+1}; 이 되기 때문입니다.
  객체가 겹쳐져서 결국 {count:count+1}이 결과값으로 나오게 됩니다.
  이걸 방지하기 위해서 비동기 처리를 할 수 있는 콜백 함수를 써야 batch처리로인한 실수를 방지할 수 있습니다.

      setState(()=>count+1);
      setState(()=>count+1);

<br>

---

2. **React의 가상 DOM은 실제 DOM에 비해 어떤 장단점을 가지나요? 가상 DOM의 개념과 실제 DOM과의 차이점, 성능상의 장점 및 단점을 설명해주세요.**

- 답 : 동적 어플리케이션에서 동작하는 가상 DOM은 실제 DOM에 비해 성능이 좋은 장점을 가지고 있습니다.
  그 이유는 트리형태로 만들어진 dom이 렌더링되었을 때 모든 dom요소가 업데이트되는데 가상 dom을 사용하면 렌더링된 dom을 기점으로 자식요소들만
  부분적으로 렌더링되기 떄문입니다.
  단점으로는 부분렌더링이 성능상 엄청난 이점이 있는건 사실이지만 부분렌더링되는 부분을 찾아야하기떄문에 가상 dom로직 내부에서 diff알고리즘이라는 무거운
  함수를 써서 바뀐부분을 찾게됩니다. 그렇기떄문에 렌더링이 많이 발생하지않는 정적 어플리케이션 (블로그 , 소개페이지) 등에서는 오히려 가상 DOM을 쓰는 이유가 적어지며
  오히려 어플리케이션 성능이 안좋아질 수 있습니다.

<br>

---

3. **클로저는 무엇이며, React에서 Hooks와 함께 사용될 때 어떤 이점을 가지나요? 실제 React Hooks에서 클로저를 사용하는 사례를 설명해주세요.**

- 답 : 클로저는 자신이 선언될 당시의 환경을 기억하는 함수입니다.
  React에서 hook과 함께 클로저를 같이 사용한다면 전역변수를 최소화하며 클로저 함수 내부 변수에 접근할 수 있는 장점을 가지고 있습니다.

  useState hook으로 예를 들어보겠습니다.

let state = undefined;
const useState=(initState)=>{

//초기화가 안되었다면 초기화
if(state===undefined){
state===initState
}

setState(newState)=()=>{
//값이 같다면 리턴
if(state===newState) return;
state = newState;
}
return [state,setState]
}

useState의 기능을 하는 간단한 hook입니다. useState의 렉시컬 환경에서 전역 렉시컬환경의 전역변수인 state에 접근하고 있습니다.
