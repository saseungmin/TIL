## 📆 2021-09-24(금) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [ ] ReScript ToDo 앱 차근차근 봐보기

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 스터디를 위한 자바스크립트 코딩의 기술 8장까지 훑어보기
- [ ] ReScript ToDo 앱 차근차근 봐보기
- [ ] 블로그에 이직 후기 회고 작성
- [ ] 개인 프로젝트 한피쳐씩 틈틈히

### 🤔 공부하면서 배운것이 있다면?

#### Sentry ErrorBoundary 적용

```tsx
import { Component, ErrorInfo, ReactNode } from 'react';

import * as Sentry from '@sentry/react';

import { isProdLevel } from './utils/utils';

interface Props {
  children: ReactNode;
}

interface State {
  hasError: boolean;
}

class ErrorBoundary extends Component<Props, State> {
  public state: State = {
    hasError: false,
  };

  static getDerivedStateFromError(_: Error): State {
    return { hasError: true };
  }

  componentDidCatch(error: Error, errorInfo: ErrorInfo):void {
    if (!isProdLevel(process.env.NODE_ENV)) {
      console.error('Uncaught error:', error, errorInfo);
      return;
    }

    Sentry.captureException({
      error,
      errorInfo,
    });
  }

  render(): ReactNode {
    if (this.state.hasError) {
      return <h1>에러가 발생했어요!</h1>;
    }

    return this.props.children;
  }
}

export default ErrorBoundary;
```

#### 🎈 참고할만한 링크
- [Netflix에서 만든 data fetching library](https://github.com/Netflix/falcor)
- [Cypress](https://www.cypress.io/)

### ⚡ 아쉬운 점 및 회고
8월달까지 포함한 월급을 받았다. 8월달거까지는 생각도 안했는데 기대보다 더 많이 들어와서 좋았다. 좋은만큼 세금도 많이 때가서 깜짝 놀랐다..   

오늘은 딱히 공부한 건 없지만, Sentry ErrorBoundary를 다시 적용해봐서 재밌었다. TypeScript에서는 처음해봤는데 테스트 작성할때, ErrorBoundary 적용하는것이 조금씩 달라서 시간이 걸렸지만, 원하는 만큼의 할 일을 끝내서 만족스럽다.   

개인 공부를 아무것도 못했지만, 어쩔 수 없다. 매일 할 수는 없으니. TIL만 적는 Commit은 솔직히 좋지 못하다. 이건 공부한것도 없다는 뜻이여서 의미없는 커밋이나 다름없다. 뭔가라도 끄적였어야했나? 하지만, 그거또한 의미없는 커밋이 되기 때문에 그러지 않을 것이다.   

블로그는 언제쓰나.. 후...

### 🚀 내일 할 일
- ReScript ToDo 앱 차근차근 봐보기
- 개인 프로젝트 한 피쳐씩 틈틈히

### 🎯 이번주 목표
- 스터디를 위한 자바스크립트 코딩의 기술 6장까지 훑어보기
- ReScript ToDo 앱 차근차근 봐보기
- 블로그에 이직 후기 회고 작성
- 개인 프로젝트 한 피쳐씩 틈틈히
- 추석연휴! 리플레쉬!
