## 📆 2021-10-05(화) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] Yarn berry + TypeScript + jest + cypress + github actions CI/CD 세팅에 관한 블로그 작성
- [x] awesome-design-systems PR
  - [fix typo](https://github.com/alexpate/awesome-design-systems/pull/255)
- [x] Dev-Event PR
  - https://github.com/brave-people/Dev-Event/pull/110
- [x] yarn berry repo
  - https://github.com/saseungmin/yarn-berry-example/pull/3

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] Object 스터디 참여 및 15장 및 부록 읽기
- ~~스터디를 위한 자바스크립트 코딩의 기술 10장까지 훑어보기~~
- [ ] ReScript ToDo 앱 차근차근 봐보기
- ~~블로그에 이직 후기 회고 작성~~
- [ ] 개인 프로젝트 한피쳐씩 틈틈히
- [x] Cypress e2e 테스트 관련 공부

### 🤔 공부하면서 배운것이 있다면?

블로그 작성에 모든 신경을 다썼다.

#### yup
- https://github.com/jquense/yup

```ts
import * as yup from 'yup';

let schema = yup.object().shape({
  name: yup.string().required(),
  age: yup.number().required().positive().integer(),
  email: yup.string().email(),
  website: yup.string().url(),
  createdOn: yup.date().default(function () {
    return new Date();
  }),
});
```

#### React-hook-form
- https://react-hook-form.com/
- with ts

```ts
import * as React from "react";
import { useForm } from "react-hook-form";

type FormData = {
  firstName: string;
  lastName: string;
};

export default function App() {
  const { register, setValue, handleSubmit, formState: { errors } } = useForm<FormData>();
  const onSubmit = handleSubmit(data => console.log(data));

  return (
    <form onSubmit={onSubmit}>
      <label>First Name</label>
      <input {...register("firstName")} />
      <label>Last Name</label>
      <input {...register("lastName")} />
      <button
        type="button"
        onClick={() => {
          setValue("lastName", "luo");
          setValue("firstName", true);
        }}
      >
        SetValue
      </button>
    </form>
  );
}
```

### ⚡ 아쉬운 점 및 회고
오늘 블로그를 발행하려고 했는데 vscode 버전 때문에 안되는거 때문에 시간을 많이 허비했다. 그래도 해결해서 다행. 내일 쓰고 발행할 수 있으려나... 할 수 있기를..!

3일만에 회사를 가서 일하니 재밌게 했다. 지금 시기가 좀 여유로운 시점이여서 하고 싶은것들을 마구잡이로 하고 싶다. 레거시 코드를 리팩터링을 하고 싶은데 테스트 코드가 없어서 역시 쉽지가 않다. 문제될 수도 있을 거라는 생각에 함부로 건들기가 좀 무섭다. 다시 한번 테스트 코드가 필요하다는 생각이 들었다.   

TDD관련 공부도 더 해야겠다. 아무리생각해도 더 공부가 필요하다. 또한, 사내에서 발표하려면 책에 있는 내용들을 개인적으로 정리도 필요해보인다.   

### 🚀 내일 할 일
- Yarn berry + TypeScript + jest + cypress + github actions CI/CD 세팅에 관한 블로그 작성 후 블로그 발행

### 🎯 이번주 목표
- 코어 자바스크립트 스터디 진행
- ReScript ToDo 앱 CSS 적용 작업
- Yarn berry + TypeScript + jest + cypress + github actions CI/CD 세팅에 관한 블로그 작성
- 개인 프로젝트 한피쳐씩 틈틈히
- Cypress e2e 테스트 관련 공부
