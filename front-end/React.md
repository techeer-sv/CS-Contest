1. **React에서 `setState` 함수는 동기적으로 동작하나요, 아니면 비동기적으로 동작하나요? `setState`가 적용되는 동작 방식에 대해 설명해주세요.**

- 답 :

비동기적으로 동작합니다.
setState를 호출하면, 제공된 객체 또는 함수는 현재 상태에 대한 업데이트를 예약하고 이 업데이트는 React가 실행을 최적화할 수 있는 시점에 처리합니다. 따라서 여러 setState호출을 그룹화 하고 한번에 업데이트하게됩니다. (매번 화면을 다시 그리면 성능 이슈가 생길수 있기 때문)

<br>

---

2. **React의 가상 DOM은 실제 DOM에 비해 어떤 장단점을 가지나요? 가상 DOM의 개념과 실제 DOM과의 차이점, 성능상의 장점 및 단점을 설명해주세요.**

기상 DOM은 실제 DOM을 추상화 하고 복제한것으로 실제 DOM을 직접 조작하는 것보다 가볍습니다.
따라서 가상 DOM을 사용해 변경사항을 적용 후 실제 DOM과 비교해 변경된 부분만 반영해 최소한의 DOM조작으로 UI를 업데이트 하기 위해 사용됩니다.

하지만 사본을 메모리에 유지하기때문에 추가적인 메모리와 처음 가상 DOM트리 생성에 따른 초기 렌더링의 오버헤드가 발생합니다.

흔치 않지만 예외적인 케이스(매우 단순한 변경사항과 성능이 민감한 환경)에서는 직접적인 DOM조작이 빠를 수도 있습니다.

<br>

---

3. **클로저는 무엇이며, React에서 Hooks와 함께 사용될 때 어떤 이점을 가지나요? 실제 React Hooks에서 클로저를 사용하는 사례를 설명해주세요.**

- 답 :

클로저는 함수와 그 함수가 선언될 때의 당시의 환경(렉시컬 환경)에 접근할 수 있게 하는 기능입니다. 이를 통해, 함수는 선언된 환경 외부에서 호출되어도 그 환경에 속한 변수에 접근할 수 있습니다.

이는 컴포넌트 간에 상태를 공유하거나 상태 변경 로직을 재사용하는 등의 기능을 처리하는데 용이하고 변수의 영속성을 유지하는데 효과적입니다.

```javascript
import React, { useState, useEffect } from "react";

function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    const intervalId = setInterval(() => {
      setCount(count + 1);
    }, 1000);

    return () => {
      clearInterval(intervalId);
    };
  }, [count]);

  return <div>{count}</div>;
}

export default Example;
```

useEffect 안의 setInterval 함수는 클로저로, count 상태를 기억합니다.
이때 count가 바뀔 때마다 새 setInterval이 생성되고, 예전 것은 clearInterval로 제거됩니다. 이로써 항상 최신 count를 참조할 수 있습니다.
