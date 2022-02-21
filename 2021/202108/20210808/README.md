## 📆 2021-08-08(일) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 집 알아보기
- [x] 함께자라기 책 읽기
  - [Chapter 2](https://github.com/saseungmin/reading_books_record_repository/tree/master/summarize_books_in_markdown/%ED%95%A8%EA%BB%98%20%EC%9E%90%EB%9D%BC%EA%B8%B0/Chapter%202#-%ED%95%98%ED%96%A5%EC%8B%9D-%EC%A0%91%EA%B7%BC%EC%9D%98-%ED%95%A8%EC%A0%95)
- [x] reading_books_record_repository 사이트에 정리한 책 추가하기
  - [루비로 배우는 객체지향 디자인 적용 PR](https://github.com/saseungmin/reading_books_record_repository/pull/100)
- [x] ConStu 내 정보 페이지 구현 (시간 남으면)
  - [firebase 이메일 검증(인증) 추가 PR](https://github.com/CodeSoom/ConStu/pull/226)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 스터디 참여 및 오브젝트 2장까지 읽기
- [x] reading_books_record_repository 사이트에 정리한 책 추가하기
- [x] ConStu 내 정보 페이지 구현 시작하기
- [x] 함께 자라기 책 읽기
- [x] 집 알아보기

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 함께 자라기 Chapter 2
구굴이 밝힌 탁월한 팀의 비밀

1. 팀에 누가 있는지(전문가, 내향/외향, 지능 등)보다 팀원들이 서로 어떻게 상호작용하고 자신의 일을 어떻게 바라보는지가 훨씬 중요했다.
2. 5가지 성공적 팀의 특징을 찾았는데, 그중 압도적으로 높은 예측력을 보인 변수는 팀의 **심리적 안전감**(**Psychological Safety**)이였다.
3. 팀 토론 등 특별히 고안된 활동을 통해 심리적 안전감을 개선할 수 있었다.

여기서 말하는 심리적 안전감이란, **내 생각이나 의견, 질문, 걱정, 혹은 실수가 드러났을 때 처벌받거나 놀림받지 않을 거라는 믿음**을 말한다.

#### 🎈 react-toastify
- https://fkhadra.github.io/react-toastify/introduction

```jsx
import React from 'react';

import { ToastContainer, toast } from 'react-toastify';

import 'react-toastify/dist/ReactToastify.css';

function App(){
  const notify = () => toast("Wow so easy!");

  return (
    <div>
      <button onClick={notify}>Notify!</button>
      <ToastContainer />
    </div>
  );
}
```

#### 🎈 react-dnd
- https://github.com/react-dnd/react-dnd
- https://channel.io/ko/blog/react-dnd-tips-tricks

### ⚡ 아쉬운 점 및 회고
아쉬운 점은 쉬지 못했다는 점. 계획을 줄일 필요가 있다. 공부도 중요하지만, 앞으로 회사가면 더 힘들어질테니까 그 전까지 좀 쉬면서 할 필요가 있어보인다.   

내일은 스터디를 위해서 오브젝트 2장만 읽고 스터디만 참여하고 쉬자. 집 알아봐야지..   

지속적으로 유지보수하고 있는 개인 프로젝트가 점점 크기가 커지고 코드 수도 많아지고 있다. 점점 커질 수록 리팩토링을 하기 무서워진다. 하지만, 테스트코드가 있다. 리팩토링을 무서워하지말자. 오늘은 TDD를 잘 따라서 구현해서 만족스럽다. 아쉬운점은 PR단위를 더 작게 나눌 필요가 있어보인다. 충분히 지금도 큰 거 같다. 더 잘게 잘게 나누려고 노력하자. 작은 피쳐 단위로 빠르게 구현하고 빠르게 배포하고 빠르게 사용자의 피드백을 얻는것이 중요.   

### 🚀 내일 할 일
- 집 알아보기
- 오브젝트 2장 읽기 및 스터디 참여
- reading_books_record_repository 사이트에 정리한 책 추가하기

### 🎯 이번주 목표
- 스터디 참여 및 오브젝트 2장까지 읽기
- reading_books_record_repository 사이트에 정리한 책 추가하기
- ConStu 내 정보 페이지 구현 시작하기
- 함께 자라기 책 읽기
- 집 알아보기
