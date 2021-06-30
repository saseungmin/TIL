## 📆 2021-06-29(화) TIL

### 📈 오늘 한 일
- [x] 개인 플젝 진행
  - 모든 페이지에 Theme 버튼을 적용하고 prefers-color-scheme를 적용하자
  - https://github.com/CodeSoom/ConStu/issues/207
- [x] 코드숨 CI/CD 강의
- [x] 면접관련 질문에 대해서 공부하기
  - repo 생성
- [ ] 일찍 일어나기

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 12시 이전에 일어나기
- [x] 기술 면접 질문 하루에 하나씩 공부
- [ ] 코테를 위한 알고리즘 공부
- [x] 코드숨 CI/CD 영상 보기
- [ ] Fortuna 스터디 준비
- [ ] 회사 찾아보기
- [ ] 몸관리 잘하기
- [x] 코드숨 개인 프로젝트 (Intersection Observer 적용하기)

### 🤔 공부하면서 배운것이 있다면?
#### 🎈 [matchMedia Mocking](https://jestjs.io/docs/manual-mocks#mocking-methods-which-are-not-implemented-in-jsdom)
- matchMedia를 mocking 할 수 있는 방법이다.
- 한 폴더에 다음과 같이 적용한 다음 

```js
Object.defineProperty(window, 'matchMedia', {
  writable: true,
  value: jest.fn().mockImplementation(query => ({
    matches: false,
    media: query,
    onchange: null,
    addListener: jest.fn(), // deprecated
    removeListener: jest.fn(), // deprecated
    addEventListener: jest.fn(),
    removeEventListener: jest.fn(),
    dispatchEvent: jest.fn(),
  })),
});
```
- test할 상단에 `import` 해주면 된다.
- 맨 상단에 `import` 해주어야 한다.

```js
import './matchMedia.mock'; // Must be imported before the tested file
import {myMethod} from './file-to-test';

describe('myMethod()', () => {
  // Test the method here...
});
```

#### 🎈 [프론트엔드 개발자 면접의 모든것 1탄 - 프론트엔트 지식편](https://clelab.io/course/3?utm_source=email)
- 브라우저 동작 원리
- DOM
- CORS
- SSR
- 올바른 CSS 사용법
- Webpack과 Babel

#### 🎈 코드숨 CI/CD 강의
- 강의 내용은 비공개
- [강의 Repo](https://github.com/CodeSoom/cicd-example)
- [AWS: DevOps란 무엇인가](https://aws.amazon.com/ko/devops/what-is-devops/) 

### ⚡ 아쉬운 점 및 회고
- 자고 일어났더니 몸이 어느정도 괜찮아졌다.
- 완벽하지 않지만, 이정도면 버틸만해서 공부를 좀 했다. 공부를 안하니 너무 불안해서 안되겠더라..
- 아무리 생각해도 지금 이렇게 불안한건 잘 못된 거 같다. 일과 공부에도 벨런스를 유지해야 한다. 그러기 위해서는 잘 쉬고 잘 놀고 해야한다. 너무 불안해 하지 말자.. 나만 힘들다.
- 그리고 규칙적인 생활을 하기 위해 노력을 더 해야 할 것 같다. 몸이 힘들어한다.
- 몸이 좋지 않았던 원인은 역시 이틀동안 정신없이 놀고 잠을 잘 못잔탓이 아닐까 싶다. 역시.. 잠이 보약이다. 근데 머리의 통증은 계속 있다. 한 4일전부터 계속 통증이 유지되는데 어쩌면좋을까? 약을 먹어도 소용이 없다..
- 그래도 뭐라도 끄적여서 마음은 편하다. 아파도 공부못해서 불편한 자신을 보며 너무 한심하다. 마음 편하게 쉴 수 없는 인생.. 여유를 가지자..
- 어차피 평생 이 직업을 하기위해 공부해야 하는데 말이다.

### 🚀 내일 할 일
- 기술 면접 질문 하루에 하나씩 공부
- 코테를 위한 알고리즘 공부
- 코드숨 CI/CD 영상 보기

### 🎯 이번주 목표
- 기술 면접 질문 하루에 하나씩 공부
- 코테를 위한 알고리즘 공부
- 코드숨 CI/CD 영상 보기
- Fortuna 스터디 준비
- 회사 찾아보기
- 몸관리 잘하기
- 코드숨 개인 프로젝트 Intersection Observer 적용하기
