## 📆 2021-10-06(수) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] Yarn berry + TypeScript + jest + cypress + github actions CI/CD 세팅에 관한 블로그 작성
- [x] ko.reactjs.org Repo에 PR
  - [fix typo](https://github.com/reactjs/ko.reactjs.org/pull/357)
- [x] Dev-Event PR
  - https://github.com/brave-people/Dev-Event/pull/111

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 코어 자바스크립트 스터디 진행
- [ ] ReScript ToDo 앱 CSS 적용 작업
- [x] Yarn berry + TypeScript + jest + cypress + github actions CI/CD 세팅에 관한 블로그 작성
- [ ] 개인 프로젝트 한피쳐씩 틈틈히
- [x] Cypress e2e 테스트 관련 공부

### 🤔 공부하면서 배운것이 있다면?

#### 토스의 마이크로프론트엔드 아키텍처, 그리고 자동화
- https://speakerdeck.com/raon0211/toseuyi-maikeuropeuronteuendeu-akitegceo-geurigo-jadonghwa

#### redux-toolkit with ts
- https://redux-toolkit.js.org/usage/usage-with-typescript

```ts
import { configureStore } from '@reduxjs/toolkit';

import { isProdLevel } from '@/utils/utils';

import rootReducer from './rootReducer';

const store = configureStore({
  reducer: rootReducer,
  devTools: !isProdLevel(process.env.NODE_ENV),
});

export type AppDispatch = typeof store.dispatch
export type RootState = ReturnType<typeof store.getState>

export default store;
```

### ⚡ 아쉬운 점 및 회고
아쉬운건 시간이 너무 빠르게 흘러간다. 시간이 너무 빠르다. 상대적인 시간..   

오늘 회사에서는 역시 kasa-web의 작업을 계속 했다. 즐겁다. 내가 하고 싶은 것들을 마음것 할 수 있다는 점..! 내일은 미팅이 세 개. 카사 싱가포르에 대해서도 애기가 오갈거 같은데 기대된다. 그리고 CPO인 션이랑도 얘기하는 자리가 있어서 기대가 된다.   

이번주는 내내 회사를 가고 있다. 그냥 뭐 나는 재택보다 회사 가는게 더 좋은 거 같다.   

앞으로 기술적인 문제들을 해결해나가면서 많은 시행착오가 있을텐데 어렵겠지만, 너무 재밌을 거 같다. 일단, 겁먹지말고 해보자. 그치만, 잘 성장해나가자. 주먹구구식 기술을 사용하기 보단 그 기술을 먼저 왜 사용하는지부터 알고 사용하도록 하자.

### 🚀 내일 할 일
- 코어 자바스크립트 스터디 진행
- Yarn berry + TypeScript + jest + cypress + github actions CI/CD 세팅에 관한 블로그 작성 후 블로그 발행

### 🎯 이번주 목표
- 코어 자바스크립트 스터디 진행
- ReScript ToDo 앱 CSS 적용 작업
- Yarn berry + TypeScript + jest + cypress + github actions CI/CD 세팅에 관한 블로그 작성
- 개인 프로젝트 한피쳐씩 틈틈히
- Cypress e2e 테스트 관련 공부
