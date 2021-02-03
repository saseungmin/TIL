## 📆 2021-02-01(수) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 루비로 배우는 객체지향 디자인 Chapter 9 읽고 정리하기 및 스터디
  - [PR Link](https://github.com/saseungmin/reading_books_record_repository/pull/33)
  - 9장을 다 읽고 스터디에 참여했다.
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기
  - 많이 진행하지 못했지만, todo item 삭제, toggle checkbox를 구현했다.


### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 알고리즘 공부 계획 세우기
- [ ] 리플레쉬 및 정리
- [x] 긍정적이게 생각하기 😤
  - 흠.. 반 정도..?

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 루비로 배우는 객체지향 디자인
- 스터디를 통해 상속, 오리 타입, 조합에 대해서 정리를 할 수 있어서 좋았다.
- 6, 7, 8 장에 대한 정리 참고 ([Link](https://github.com/saseungmin/reading_books_record_repository/tree/master/%EB%A3%A8%EB%B9%84%EB%A1%9C%20%EB%B0%B0%EC%9A%B0%EB%8A%94%20%EA%B0%9D%EC%B2%B4%EC%A7%80%ED%96%A5%20%EB%94%94%EC%9E%90%EC%9D%B8/Question))


#### 🎈 Recoil을 사용한 ToDo 앱 만들기
- 테스트를 위한 mook 컴포넌트를 생성 후 atom에 주입해주는 방식을 알게 되었다.
- 아래와 같이 테스트만을 위한 `atom`객체에 값을 넣어준다.

```jsx
import { useEffect } from 'react';

import { useSetRecoilState } from 'recoil';

import todosAtom from '../../recoil/todos/atom';

const InjectTestingRecoilState = ({ state }) => {
  const setState = useSetRecoilState(todosAtom);

  useEffect(() => {
    setState(state);
  }, []);

  return null;
};

export default InjectTestingRecoilState;
```

- 그 후 테스트를 하는 컴포넌트를 `RecoilRoot`로 감싸고 `InjectTestingRecoilState`에 테스트할 값을 주입해준다.

```jsx
import React from 'react';

import { render } from '@testing-library/react';

import { RecoilRoot } from 'recoil';

import InjectTestingRecoilState from '../common/InjectTestingRecoilState';

import TodoList from './TodoList';

describe('TodoList', () => {
  const renderTodoList = (state) => render((
    <RecoilRoot>
      <InjectTestingRecoilState state={state} />
      <TodoList />
    </RecoilRoot>
  ));
  // ... 생략
});
```

- 그리고 `Recoil` 사용시 프로젝트 구조에 대해서 의문점이 많았는데 해결해준 글을 찾게되었다.
- Recoil 프로젝트 진행시 Best Practices에 관한 글이였다. 뭐.. 정답은 없는 거 같지만, 그래도 모르니까 잘하시는 분들의 글을 보고 구조를 맞춰나가는 방법도 하나의 방법이라고 생각한다. ([Link](https://wes-rast.medium.com/recoil-project-structure-best-practices-79e74a475caa))
- 그리고 Recoil 공식 issue 참고 ([Link](https://github.com/facebookexperimental/Recoil/issues/27))

### ⚡ 아쉬운 점 및 회고
- 평탄한 하루였다.
- 스터디에서 말을 잘 못해서 아쉽다. 준비를 해도 해도 부족하다고 생각든다. 말을 왜 이렇게 못하는건지..
- 하다보니 너무 늦어버렸다. 규칙적인 생활을 하고싶은데. 자꾸 자는 시간이 늦어지는 거 같다. 그러면 내일도 또 그만큼 늦게 일어나게 되는 거 같다. 나는 너무 야행성이다..
- 방정리를 또 미루게 되었다.. 언제하지..

### 🚀 내일 할 일
- Recoil를 사용한 ToDo 앱 만들기 진행하기
- 개인 프로젝트 진행(스터디 후기 😓)

### 🎯 이번주 목표
- 알고리즘 공부 계획 세우기
- 리플레쉬 및 정리
- 긍정적이게 생각하기 😤