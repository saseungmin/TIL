## 📆 2021-02-16(화) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 알고리즘 공부
  - 인프런 알고리즘 강의 문제 9문제를 풀었다. ([PR Link](https://github.com/saseungmin/daily_coding_dojo/pull/1))
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기 (백앤드 세팅)
  - 기본적인 koa 세팅은 했고 Heroku에 배포까지 해놨다. CI / CD 세팅

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 알고리즘 공부 시작하기
- [ ] TypeScript, 앨레강트 오브젝트, Pro Git 책 읽기
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기 (백앤드)
- [ ] 개인 프로젝트(스터디 후기)

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 알고리즘 공부를 하면서 배운것은?
- 아직 기본적인 문제들이라 쉽다.
- 더 속도좀 내야겠다.

#### 🎈 Recoil를 사용한 ToDo 앱 만들기
- 백앤드 세팅을 진행했다. 하면서 새롭게 알게된 점들도 많았다.
- 백앤드를 배포하는 곳을 Heroku라는 것을 찾았다. 많이 사용하는 거 같았다.
- Heroku 무료버전을 사용했는데 무료버전은 30분 동안 접속이 없으면 잠자기 모드에 들어간다. 때문에 처음 접속하면 많이 느리다.
- 백앤드를 세팅하려고 생각보다 많은 시간을 소비했다.
- 일단, `package.json`에 `"type":"modules"`을 `import/export`를 babel 작업없이 사용할 수 있었다. node 버전이 12이상이여야 했고, jest는 지원을 하지 않아 에러가 발생했다.
- 그래서 `esm`을 사용하였다. dev server는 `babel-node`를 사용하였다.

```json
{
  "scripts": {
    "start": "node -r esm index.js",
    "start:dev": "nodemon --watch src/ src/index.js --exec babel-node",
    "test": "jest",
    "test:watch": "npm run test -- --watch-all",
    "coverage": "npm run test -- --coverage",
    "lint": "eslint ."
  },
  "devDependencies": {
    "@babel/cli": "^7.12.16",
    "@babel/core": "^7.12.16",
    "@babel/node": "^7.12.16",
    "@babel/preset-env": "^7.12.16",
    "babel-jest": "^26.6.3",
  },
  "dependencies": {
    "esm": "^3.2.25",
  }
}
```

- `koa`을 사용하였다. `express`보다 `koa`를 선택한 이유는 `async/await`를 공식적으로 지원하기 때문에 사용였다. 또한, `express` 보다 `koa`가 익숙했다. 그리고 필요한 것만 가져다 쓸 수 있는게 단점일 수도 있겠지만 나는 장점처럼 느껴져서 `koa`가 좀더 가볍게 다룰 수 있다고 생각하였다.
- 백앤드 테스트는 처음 적용해보았다. 때문에 시간이 오래걸렸다. 아직 뭐 시작도 안했지만.. 어떤 걸 써야할지 기본적인 느낌은 알 수 있었다.
- 제일 대중적이고 가장 많이 사용하는 외부 라이브러리는 `supertest`로 `jest`와 같이 사용하였다.

```js
// app.js
import Koa from 'koa';

import Router from 'koa-router';
import logger from 'koa-logger';
import bodyParser from 'koa-bodyparser';

const app = new Koa();
const router = new Router();

app.use(logger());

router.get('/', (ctx) => {
  ctx.body = 'Hello World!';
});

app.use(bodyParser());
app.use(router.routes());
app.use(router.allowedMethods());

export default app;
```
- 다음은 `router.get('/',` 이부분을 테스트한 것이다.

```javascript
import request from 'supertest';

import app from './app';

test('Hello world works', async () => {
  const { status, text } = await request(app.callback()).get('/');

  expect(status).toBe(200);
  expect(text).toBe('Hello World!');
});
```


### ⚡ 아쉬운 점 및 회고
- 오늘도 예정대로 8시반에 기상했고 9시부터 대충 9시까지 공부했다.
- 시간은 오래 했지만, 그만큼의 성과는 없었다고 생각한다. 그 이유가 Recoil 백앤드 부분은 처음이라 그렇다고 생각한다. 그래도 지금 좀 고통받으면 다음번에 적용할 때 더 빨리 할 수 있다고 생각한다.
- 하지만, 시간 분배를 조금은 아쉽게 했다. 안되서 많이 붙잡고 있던 거 같다.
- 내일은 mongodb까지 연결한 뒤 mongoose를 적용해볼 예정이다.
- 일찍 일어나니 확실히 하루가 길어진 느낌이고 늦게까지 하지 않아도 되서 훨씬 좋다. 오늘도 쉬고 일찍 일어나야겠다.

### 🚀 내일 할 일
- 알고리즘 공부
- Recoil를 사용한 ToDo 앱 만들기 진행하기 (mongoDB 연결)

### 🎯 이번주 목표
- 알고리즘 공부 시작하기
- TypeScript, 앨레강트 오브젝트, Pro Git 책 읽기 (다 읽는다는 뜻이 아님.)
- Recoil를 사용한 ToDo 앱 만들기 진행하기
- 개인 프로젝트(스터디 후기)