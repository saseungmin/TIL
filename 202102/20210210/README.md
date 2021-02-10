## 📆 2021-02-10(수) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 앨레강트 오브젝트 복기 및 스터디 참여
  - 스터디를 참여했다.
- [x] 알고리즘 공부하기
  - 공부를 했다기 보단 공부를 하기위해 준비과정과 알고리즘 repository를 정리했다.
  - https://github.com/saseungmin/daily_coding_dojo
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기 (CSS 작업)
  - SVG 파일을 적용시켰다. ([PR Link](https://github.com/saseungmin/Recoil_ToDo/pull/19))

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 알고리즘 공부 시작하기
- [x] 리플레쉬 및 정리
  - 리플레쉬는 지금 해야지
- [x] 긍정적이게 생각하기 😤
- 설날

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 앨레강트 오브젝트
- 스터디를 참여했다.
- 질문과 해당 질문에 대한 답을 만들었다. [Question](https://github.com/saseungmin/reading_books_record_repository/tree/master/%EC%97%98%EB%A0%88%EA%B0%95%ED%8A%B8%20%EC%98%A4%EB%B8%8C%EC%A0%9D%ED%8A%B8/Question)


#### 🎈 Recoil을 사용한 ToDo 앱 만들기

- svg 파일을 사용하기 위해 webpack 설정을 배웠다.
- dependency를 설치해준다.

```shell
npm i -D @svgr/webpack
```

- rules에 추가해준다.


```js
module.exports = {
  // 생략..
  module: {
    rules: [
      // 생략..
      {
        test: /\.svg$/,
        use: ['@svgr/webpack'],
      },
    ],
  },
};
```

- svg 테스트를 위해 `jest-svg-transformer`를 설치해준다.

```shell
npm i -D jest-svg-transformer
```

- `jest.config.js`에 `transform`에 추가해준다.

```js
module.exports = {
  // 생략..
  transform: {
    '^.+\\.jsx?$': 'babel-jest',
    '^.+\\.svg$': 'jest-svg-transformer',
  },
};
```

- 이제 다음과 같이 `import` 시켜 테스트도 안깨지게 할 수 있게 되었다.

```jsx
import React from 'react';

import CheckedIcon from '../assets/icons/checked.svg';
import UnCheckedIcon from '../assets/icons/un-checked.svg';

const Checkbox = () => {
  return (
    <>
      <CheckedIcon />
      <UnCheckedIcon />
    </>
  );
};

export default Checkbox;
```

### ⚡ 아쉬운 점 및 회고
- 오늘은 설날 하루전날이지만 나한테는 똑같은 하루였다. 언제까지 백수생활할지 모르겠다.
- 여유를 가지고 생각하자.
- 오늘은 일찍 쉬자.
- 아마 설날때는 평소랑 똑같은 하루일 거 같다.

### 🚀 내일 할 일
- 알고리즘 공부하기
- Recoil를 사용한 ToDo 앱 만들기 진행하기 (CSS 작업)
- 개인 프로젝트 진행하기

### 🎯 이번주 목표
- 알고리즘 공부 시작하기
- 리플레쉬 및 정리
- 긍정적이게 생각하기 😤
- 설날