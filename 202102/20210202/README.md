## 📆 2021-02-01(화) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 루비로 배우는 객체지향 디자인 Chapter 9 읽고 정리하기 (9장 양이 많아서 아마 반씩 나눠야할 듯 싶다.)
  - 양이 많아서 나눠서 진행한다. 반정도 했다. ([PR Link](https://github.com/saseungmin/reading_books_record_repository/pull/33))
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기
  - 처음 해보다보니 삽질을 많이 했다. 리덕스와 달리 어떻게 구조를 잡아야할지 감이 안와서 고민을 많이 하였고, 또한, 공식 문서와 다른 분들이 어떻게 했나를 참고를 많이 하였다.

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 알고리즘 공부 계획 세우기
  - 일단 처음부터 다신한다는 생각으로 인프런 강의를 들으며 공부해볼려한다. 물론 강의만 무작정 듣는다는게 아니라 모르는 부분만 골라서 들을 예정이다. ([Link](https://www.inflearn.com/course/%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EA%B0%95%EC%A2%8C#curriculum))
- [ ] 리플레쉬 및 정리
- [x] 긍정적이게 생각하기 😤

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 루비로 배우는 객체지향 디자인 Chapter 9-1: 비용-효율적인 테스트 디자인하기
- 테스트를 작성하는 의도는?
    - 테스트만이 디자인에 대한 믿을 수 있는 문서를 제공한다.
    - 초기에 버그를 찾을 수 있다.
    - 디자인 결정을 안전하게 미룰 수 있도록 해준다.
    - 테스트는 모든 추상화된 인터페이스의 기록이기 때문에 우리의 작업을 지지해주는 기반이 된다.
    - 최소한의  비용으로 테스트가 제공하는 이점을 누리는 것이고 이걸 이루기 위해서 느슨하게 결합된 테스트를 작성한다.
- 무엇을 테스트할까?
    - 모든 객체에서 가장 안정적인 것은 퍼블릭 인터페이스로 우리가 테스트하는 것은 퍼블릭 인터페이스에서 정의된 메시지
    - 테스트는 객체의 경계를 넘나드는 메시지에 집중하고 오직 퍼블릭 인터페이스에 속하는 메시지의 상태만 검증
- 언제 테스트할까?
    - 테스트를 먼저 작성하는 것이 좋다.
- 어떻게 테스트할까?
    - 대중적인 테스트 프레임워크 사용
    - TDD와 BDD중 각자의 경험과 보다 중요하게 생각하는 가치에 준해 결정한다.
    - 테스트는 테스트중인 객체의 가장자리를 따라 시선을 고정하고 그 경계를 넘나드는 메시지만 알고 있어야 한다.
- 테스트 더블?
    - 테스트만을 위한 각자 객체 stub이라고 부르고 mock은 아니다.
    - 테스트를 간단하고 빠르고 독립적이며 의도를 명확하게 드러낼 수 있다.
- 프라이빗 메서드 테스트?
    - 프라이빗 메서드는 이미 테스트를 붙여 놓은 퍼블릭 메서드에 의해 호출된다.
    - 프라이빗 메서드는 불안정하다. 때문에 테스트를 하면 안된다. 의미없다.
    - 프라이빗 메서드를 테스트할 때 기본 원칙은 절대 테스트하지 마라. 만약 테스트해야 한다면, 그래도 하지말고. 물론 꼴 해야 하는 상황에서는 테스트해도 된다.

#### 🎈 Recoil을 사용한 ToDo 앱 만들기
- 삽질을 하며 배운 것은 은근 많다. recoil관련된 훅도 많이 배웠고, 왜 recoil이 나오게 되었나도 알게 되었다.
- 일단 기존 redux와 같은 개념은 상태를 업데이트 또는 상태를 사용하기 위해서 공통 조상 컴포넌트로 끌어올려야 하는데, 이 과정 너무 큰 트리가 리렌더링 될 수 있다.
- recoil은 Context API 기반으로 구현되어 있고 함수형 컴포넌트에서만 사용할 수 있다.
- Recoil API 대부분은 훅으로 구현되어 있다. 때문에 클래스 컴포넌트에서는 사용할 수 없다.
- 리덕스와 마찬가지로 Provider가 있어야 한다. 떄문에 루트 컴포넌트인 `App`를 감싸준다.

```jsx
import React from 'react';

import ReactDOM from 'react-dom';
import { RecoilRoot } from 'recoil';

import App from './App';

import '../assets/global.css';

ReactDOM.render(
  (
    <RecoilRoot>
      <App />
    </RecoilRoot>
  ),
  document.getElementById('app'),
);
```

- recoil은 단위 데이터로 스토어에 저장되고 추출되는 데이터는 모두 Atom을 기반으로 하고 있따.`atom`은 `key`와 `default`를 전달해서 작성할 수 있다.

```jsx
const initialTodoState = atom({
  key: 'initialTodoState',
  default: [],
});
```

- 이 Atom 객체를 훅에 전달하여 값을 가져오고 설정할 수 있다.
- `useSetRecoilState`는 값을 전달할 수만 있다.
- `useRecoilState`는 `get`과 `set` 둘다 가능하다.
- `useRecoilValue`는 `get`으로 값을 가져올 수만 있다.
- `useResetRecoilState`는 초기값으로 만들 수 있다.

```jsx
import React, { useState } from 'react';

import { useSetRecoilState } from 'recoil';

import { v4 as uuidv4 } from 'uuid';

import { initialTodoState } from '../../utils/recoil/atomState';

const TodoInput = () => {
  const [input, setInput] = useState('');
  const setTodo = useSetRecoilState(initialTodoState);

  const handleSubmit = (e) => {
    e.preventDefault();

    setTodo((oldTodoList) => [
      ...oldTodoList,
      {
        id: uuidv4(),
        task: input,
        isComplete: false,
      },
    ]);

    setInput('');
  };

  const handleChange = (e) => {
    const { value } = e.target;

    setInput(value);
  };

  return (
    <>
      <form onSubmit={handleSubmit}>
        <input
          value={input}
          onChange={handleChange}
          placeholder="오늘의 할 일을 입력하세요!"
        />
      </form>
    </>
  );
};

export default TodoInput;
```

- 하면서 느꼈던 점은 redux사용시에 reducer와 action을 작성할 필요가 없다. 그래서 container가 필요없다고 느껴져서 뺐다. 구조를 굳이 맞출 필요가 있을까 느껴졌다.
- 삽질을 많이했지만, 그래도 얻은 건 많아 나쁘지 않다. 페이스북에서 만드는 것이다보니 조금은 배워놔도 나쁘지 않을 거 같다.
- 그리고 recoil도 이미 devtool이 존재했다. 리덕스를 devtool 사용할 떄는 미들웨어로 주입해주어야 했지만 recoil은 스냅샷기능으로 자동으로 chrome extension을 설치만하면 사용가능하다.
([TotalRecoilJS](https://totalrecoiljs.com/))

### ⚡ 아쉬운 점 및 회고
- 오늘도 역시 쉬지는 못했다. 흠..쉬고싶은데 쉬고싶은데 생각이들다가도 이게 마음처럼 안되는거 같다.
- 그래도 재밌어서 이렇게 할 수 있다고 생각이 든다.
- 오늘 recoil에 대해서 삽질을 많이 했는데 그래도 얻은건 있어서 좋다.
- recoil 테스트 작성도 공식문서가 있긴하니(너무 간단.) 다뤄봐야겠다. 사실 훅이라 atom과련 훅은 필요없을 거 같다. selector가 문제일 거 같긴하다.
- 방정리는 언제할까

### 🚀 내일 할 일
- 루비로 배우는 객체지향 디자인 Chapter 9 읽고 정리하기 및 스터디
- Recoil를 사용한 ToDo 앱 만들기 진행하기

### 🎯 이번주 목표
- 알고리즘 공부 계획 세우기
- 리플레쉬 및 정리
- 긍정적이게 생각하기 😤