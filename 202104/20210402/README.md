## 📆 2021-04-02(금) TIL

### 🚀 내일 할 일
- [ ] 알고리즘 section 7 풀기
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기 (Theme 설정)
  - Dark 모드를 만들었다. ([PR Link](https://github.com/saseungmin/Recoil_ToDo/pull/82))
  - Toggle Button을 만들었다. ([PR Link](https://github.com/saseungmin/Recoil_ToDo/pull/83))

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 알고리즘 공부 (Section 6과 Section 7시작하기)
- ~~오브젝트 책 Chapter 14 까지 읽기 및 스터디 참여~~
- [ ] 취업 준비 스터디 관련 준비 및 스터디 참여
- [ ] 코드숨에서 진행했던 프로젝트 더 꾸며보기

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 Recoil를 사용한 ToDo 앱 만들기 진행하기

- dark 모드를 설정하기 위해 `ThemeProvider`를 사용했다.

```jsx
import React, { useEffect } from 'react';

import styled from '@emotion/styled';
import { ThemeProvider } from '@emotion/react';

import { lightTheme, darkTheme } from './styles/theme';

const App = () => {
  const theme = useRecoilValue(themeModeAtom);

  return (
    <ThemeProvider theme={theme ? darkTheme : lightTheme}>
    {/*...*/}
    </ThemeProvider>
  );
};

export default App;
```

- 그리고 다음과 같이 `light`와 `dark`버전으로 나눠서 주입시켜줄 수 있다.

```jsx
// theme.js
export const lightTheme = {
  baseTone: '#FFDFDE',
  subTone: '#6A7BA2',
  // ...
};

export const darkTheme = {
  baseTone: '#6A7BA2',
  subTone: '#FFDFDE',
  // ...
};
```

- 그리고 `theme`이라는 객체로 가져다 사용하면 된다.

```jsx
const FilterButtonWrapper = styled.button`
  color: ${({ theme }) => theme.gray};

  ${({ value, status, theme }) => value === status && css`
    color: ${theme.baseTone};
  `};
`;
```

- 이번에 초기 css를 잡아줄 수 있다. Global로 CSS를 설정해줄때 다음과 같이 사용할 수 있다.

```jsx
import React from 'react';

// 초기 emotion에서 사용하는 CCS 설정
import emotionReset from 'emotion-reset';

import { Global, useTheme, css } from '@emotion/react';

const setGlobalStyles = (theme) => css`
  ${emotionReset}

  * {
    box-sizing: inherit;
  }

  body {
    font-family: 'Noto Sans KR', sans-serif;
    transition: all 0.25s linear 0s;
    background: ${theme.baseTone};
  }
`;

const GlobalStyles = () => {
  const theme = useTheme(); // theme 가저오기

  return (
    // Global로 CSS 설정
    <Global styles={setGlobalStyles(theme)} />
  );
};

export default GlobalStyles;
```


### ⚡ 아쉬운 점 및 회고
- 오늘도 알고리즘 공부 실패.
- 알고리즘 공부 하기 싫어서 자꾸 피하게된다. 어쩌면 좋을까.. 솔직히 너무 하기 싫다.
- 하지만.. 코테를 위해서 해야대...
- 이제 진짜 면접 준비랑 알고리즘 공부해야겠다.
- 오늘도 한 10시간 정도 공부를 했지만, 뭐 Recoil 구현에 의존해서.. 잘모르겠다.
- 내일은 알고리즘 공부랑 면접 질문 3문제를 공부하고 오브젝트 마지막 장을 읽어야겠다.
- 오늘은 친구들과 놀았다.
- 그래서 늦게 쓴다. 끝.
- 내일은 알고리즘 공부좀 하자.

### 🚀 내일 할 일
- 알고리즘 section 7 풀기
- 면접 질문 3문제 공부하고 정리하기
- 오브젝트 15장 반 읽기
- 시간 남으면 Recoil 백앤드 README.md 작성하기

### 🎯 이번주 목표
- 알고리즘 공부 (Section 6과 Section 7시작하기)
- ~~오브젝트 책 Chapter 14 까지 읽기 및 스터디 참여~~
- 취업 준비 스터디 관련 준비 및 스터디 참여
- 코드숨에서 진행했던 프로젝트 더 꾸며보기