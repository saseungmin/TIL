## 📆 2021-07-05(화) TIL

### 📈 오늘 한 일
- [x] Fortuna 스터디 준비 및 참여
  - [정리](https://github.com/saseungmin/frontend-tech-interview/tree/main/react/React%20Clean%20Architecture)
- [x] Codesoom 개인 프로젝트 한 피처
  - [PR](https://github.com/CodeSoom/ConStu/pull/213)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 12시 이전에 일어나기
- [ ] 기술 면접 질문 하루에 하나씩 공부
- [ ] 코테를 위한 알고리즘 공부
- [x] Fortuna 스터디 준비
- [ ] 회사 찾아보기
- [x] 몸관리 잘하기
- [x] 코드숨 개인 프로젝트

### 🤔 공부하면서 배운것이 있다면?

- [react-router 404 페이지](https://yoogomja.github.io/2020/04/29/reactjs-nested-route-404/)
- [react-router redirect](https://reactrouter.com/web/api/Redirect)
- [React | 로그인 정보 없을 경우 로그인 페이지로 redirect하기 ( react-router, PrivateRoute, 로그인 권한 )](https://gaemi606.tistory.com/entry/React-%EB%A1%9C%EA%B7%B8%EC%9D%B8-%EC%A0%95%EB%B3%B4-%EC%97%86%EC%9D%84-%EA%B2%BD%EC%9A%B0-%EB%A1%9C%EA%B7%B8%EC%9D%B8-%ED%8E%98%EC%9D%B4%EC%A7%80%EB%A1%9C-redirect%ED%95%98%EA%B8%B0-react-router-PrivateRoute)

#### 🎈 [React-hook-form에서 useFormContext](https://react-hook-form.com/api/useformcontext)

```jsx
import React from "react";
import { useForm, FormProvider, useFormContext } from "react-hook-form";

export default function App() {
  const methods = useForm();
  const onSubmit = data => console.log(data);

  return (
    <FormProvider {...methods} > {/* pass all methods into the context */}
      <form onSubmit={methods.handleSubmit(onSubmit)}>
        <NestedInput />
        <input type="submit" />
      </form>
    </FormProvider>
  );
}

function NestedInput() {
  const { register } = useFormContext(); // retrieve all hook methods
  return <input {...register("test")} />;
}
```

#### 🎈 React에서 좋은 컴포넌트 설계란?
- [공부하며 정리했다.](https://github.com/saseungmin/frontend-tech-interview/tree/main/react/React%20Clean%20Architecture)
- [클린코드 의미 있는 이름](https://velog.io/@dnr6054/Clean-Code-2-%EC%9D%98%EB%AF%B8-%EC%9E%88%EB%8A%94-%EC%9D%B4%EB%A6%84)

### ⚡ 아쉬운 점 및 회고
- 아이고야.. 이렇게 늦게까지 할 생각이 없는데.. 개발이 이게 참.. 시간가는줄 모르고 해버린다. 그래도 한 피처는 끝내야되기 때문에.. 하지만 한 피쳐를 너무 크게 잡아버렸기 떄문에 또 내 실수다. 아니 내 잘못이다.
- 스터디를 했는데 굉장히 만족스럽다. 그리고 좀 인정받는? 느낌이 들어서 좋았다. 그래도 공부를 좀 열심히 한 보람을 느꼈다. 더 열심히 해야겠다. 책을 많이 읽자. 책에는 엄청난 지식이 담겨있다!
- 어우 졸려.. 내일도 화이팅! 오늘은 만족스러운 하루였다. 늦게 자는거 빼고..

### 🚀 내일 할 일
- 코드숨 불필요한 전역 state 걷어내기
- 코테를 위한 알고리즘 공부
- 기술 면접 질문 하루에 하나씩 공부

### 🎯 이번주 목표
- 기술 면접 질문 하루에 하나씩 공부
- 코테를 위한 알고리즘 공부
- Fortuna 스터디 준비
- 회사 찾아보기
- 몸관리 잘하기
- 코드숨 개인 프로젝트
