## 📆 2021-11-23(화) TIL

### 📈 오늘 한 일
- [x] Conners 프로젝트
  - 도메인 구입
  - [redux 초기 세팅](https://github.com/jennie-harang/Conners/pull/21)
  - https://github.com/jennie-harang/Conners/pull/23

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 클린 코드 14장 읽기 및 스터디 참여
- [ ] 스칼라로 배우는 함수형 프로그래밍 5장 읽고 스터디 참여
- [ ] 리팩터링 4 ~ 5장 읽고 스터디 참여
- [ ] 테스트와 TDD에 대한 정리
- [ ] 인프런 강의 듣기
- [x] Conners 프로젝트
- [x] Next.js 공부하기

### 🤔 공부하면서 배운것이 있다면?

- `keyof` 옵션을 사용하면 타입에 대한 키값으로 type을 지정할 수 있따.

```ts
export const getAuth = (key: keyof AuthStore) => (obj: AppState) => obj.authReducer[key];
```

- redux-toolkit and next-redux-wrapper with next.js

```tsx
export const makeStore = () => configureStore({
  reducer: rootReducer,
  devTools: !isProdLevel(process.env.NODE_ENV),
});

const wrapper = createWrapper(makeStore, {
  debug: !isProdLevel(process.env.NODE_ENV),
});

const store = makeStore();

export default wrapper;
```

- `_app.tsx` 파일에 HOC방식으로 방식으로 redux를 래핑해준다. 이렇게 하면 next.js의 서버사이드 렌더링해주는 곳에서도 redux store에 접근할 수 있게 된다.

```tsx
import type { AppProps } from 'next/app';

import wrapper from '@/reducers/store';

function MyApp({ Component, pageProps }: AppProps) {
  return (
    <Component {...pageProps} />
  );
}

export default wrapper.withRedux(MyApp);
```

### ⚡ 아쉬운 점 및 회고
미친 하루였다. 할게 너무 많아!!! 정말로!!.. 이대로는 못살거 같다. 스터디 3개에 회사 업무에, 이 프로젝트까지.. 몸이 썩어나간다. 얼른 스터디 끝내야하는데... 어쩌면 좋지..    

회사 일은 전혀 안 힘든데. 부수적인게 너무 많다. 욕심을 너무 부렸어...   

모르겠다. 얼른 자야겠다.

### 🚀 내일 할 일
- 스칼라로 배우는 함수형 프로그래밍 5장 읽고 스터디 참여
- 리팩터링 4 ~ 5장 읽기

### 🎯 이번주 목표
- 클린 코드 14장 읽기 및 스터디 참여
- 스칼라로 배우는 함수형 프로그래밍 5장 읽고 스터디 참여
- 리팩터링 4 ~ 5장 읽고 스터디 참여
- 테스트와 TDD에 대한 정리
- 인프런 강의 듣기
- Conners 프로젝트
- Next.js 공부하기
