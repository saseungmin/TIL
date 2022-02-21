## 📆 2021-02-28(일) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [ ] 알고리즘 공부
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기 (회원 인증 페이지 구현)
  - [PR Link](https://github.com/saseungmin/Recoil_ToDo/pull/42)
- [ ] 오브젝트 책 Chapter 1 읽기 (아마 못할 수도 있다.)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 알고리즘 공부
- [x] ~~앨래강트 오브젝트~~
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기
- [ ] 개인 프로젝트(스터디 후기)

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 Recoil를 사용한 ToDo 앱 만들기 진행하기
- `form`에 대한 submit action 작업을 위해 `react-hook-form`를 사용해보았다.
- 굉장히 간편하고 편리했다.. onChange에 대한 작업을 해야하는데 그 작업을 하지 않아도된다. 심지어 에러 처리도 가능하다.

```bash
> npm install -S react-hook-form
```

```js
import React from "react";

import { useForm } from "react-hook-form";

export default function App() {
  const { register, handleSubmit, watch, errors } = useForm();
  const onSubmit = data => console.log(data);

  console.log(watch("example")); 

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input name="example" defaultValue="test" ref={register} />
      <input name="exampleRequired" ref={register({ required: true })} />
      {errors.exampleRequired && <span>This field is required</span>}
      <input type="submit" />
    </form>
  );
}
```


- `cors` 를 해결하기 위해 웹팩 devServer proxy 설정을 해줬다.

```js
// 생략

module.exports = {
  // 생략
  module: {
    // 생략..
  },
  // 생략..
  devServer: {
    hot: true,
    overlay: true,
    historyApiFallback: true,
    proxy: {
      '/api': {
        target: 'http://localhost:3001',
      },
    },
  },
  plugins: [
    // 생략..
  ],
};
```

- recoil의 `selectorFamily`를 사용해보았다.
- `selectorFamily`를 사용하면 셀렉터 객체를 그대로 전달하는 대신 셀렉터 패밀리에 파라미터를 전달하여 실행하여 셀렉터를 생성하도록 할 수 있다.

```js
const authWithRegister = selectorFamily({
  key: 'authWithRegister',
  get: (user) => async () => {
    const response = await register(user);

    return response;
  },
});
```

- 다음과 같이 `selectorFamily`에도 `get`을 사용할 수 있다.

```js
const authWithRegister = selectorFamily({
  key: 'authWithRegister',
  get: (user) => async ({ get }) => {
    const { type } = get(authStatusAtom);

    const response = await register(user);

    return response;
  },
});
```

- `axios`를 사용할 때 default url를 다음과 같이 설정 할 수 있다.
- 개발일 때와 서버 배포일 때에 따라 `baseURL`를 다르게 설정 할 수 있다.

```js
import axios from 'axios';

import { BASE_URL } from '../../utils/constants/url';

const client = axios.create();

axios.defaults.baseURL = process.env.NODE_ENV === 'development' ? '/' : BASE_URL;

export default client;

```

### ⚡ 아쉬운 점 및 회고
- 오늘 한심하다. 너무 많이 못했다. 사실 많이 못한 거 보다 시간 관리를 못했다.
- 시간 관리가 정말 어려다고 느꼈다.
- 벌써 취준?했을까? 한걸까? 어쨌든.. 회사를 관둔지 1달이 되었다. 사실 한 달 동안 안일하게 공부했다.
- 하고싶은 공부를 더 많이 했다고 해도 과언이 아니다. 즐겁게 공부했다. recoil 프로젝트 얼른 끝내자.
- 시간 너무 잡아먹는다. 거의 다 왔다. 생각보다 처음 접하는 부분이 많아 오래걸리고 있다.
- 이렇게 오래걸리는 것으로 보아 아직 내가 시간을 투자해 시도하기에는 실력이 부족한가 보다.
- 면접을 위해 CS공부랑 javascript 이론? 공부도 시작해야한다.
- 내일은 쉬는 날이라는데 나는 쉬는날인지도 몰랐다. 날짜 개념이 없어지고 있다.

### 🚀 내일 할 일
- 알고리즘 공부
- Recoil를 사용한 ToDo 앱 만들기 진행하기 (회원 인증 페이지 구현)
- 오브젝트 책 Chapter 1 읽기

### 🎯 이번주 목표
- 알고리즘 공부
- 오브젝트 책 Chapter 3 까지 읽기 및 스터디 참여
- Recoil를 사용한 ToDo 앱 만들기 진행하기
- 긍적적 사고방식과 할 수 있는 것과 할 수 없는 것을 구분 잘하기
- 시간 분배 잘하기와 쓸대 없이 시간낭비하는 시간 아끼기