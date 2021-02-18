## 📆 2021-02-17(수) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 알고리즘 공부
  - inflearn 강의의 section1을 마무리했다.
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기 (mongoDB 연결)
  - mongoose를 사용한 mongoDB를 연결했고, 테스트도 coverage 100%를 달성헀고 Heroku에 배포까지 끝냈다.
  - [PR Link](https://github.com/saseungmin/Recoil_Todo_Backend/pull/4)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 알고리즘 공부 시작하기
- [ ] TypeScript, 앨레강트 오브젝트, Pro Git 책 읽기
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기 (백앤드)
- [ ] 개인 프로젝트(스터디 후기)

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 알고리즘 공부를 하면서 배운것은?
- 오늘은 풀다가 성능에 대한 고민을 하게되었다.
- `for`, `foreach`, `reduce`, `map`, `for of`등등.. 어떤게 제일 빠를까? 라는 고민이다.
- https://jsben.ch/ 성능을 측정해주는 사이트가 존재했다. 하지만 확실한건지는 잘모르겠다.
- 어쨋든 블로그의 글을 참고한 결과 성능 최적화한 for문이 가장 빨랐고, `for of`, `foreach`, `for`문 순이였지만, 이 마저도 상황에 따라서 브라우저에 따라서 다르기 때문에 뭐가 정답인지는 모르겠다. 일단 위의 결과는 순차적일 때에 해당하는 점이다. 브라우저는 크롬

#### 🎈 Recoil를 사용한 ToDo 앱 만들기(백앤드)
- mongoose를 사용한 mongoDB연걸을 했다.
- mongoDB는 로컬을 사용할 수 없기 때문에 mongodb atlas 서버를 사용하였다. 무료 버전이 존재해서 사용하였다.
- 원래 heroku에 무료로 사용할 수 있는 add-on mongodb 서버가 있었는데 2020년 10월? 부터 서비스를 중단하였다. heroku add-on mongodb는 유로버전만이 존재했다. ([문서 참고](https://devcenter.heroku.com/articles/mongolab))
- heroku add-on에서만 중단한거지 [mlab](https://mlab.com/) 사이트에 가면 서버를 무료로 사용할 수 있다. 하지만, mongodb공식 사이트에서 제공하는 cloud서버를 사용하였다.
- mongoose 테스트를 적용하려고 애를 많이 먹었다. 그래도 이제 어떻게 해야할지 조금은 알았다. 그리고 테스트도 100%를 달성해서 만족한다.
- 일단 mongodb 테스트를 진행하기 위해서 mongodb mock서버가 필요했다. 해당 테스트 라이브러리가 존재하여 사용하였다. 다시 말하자면 mongodb의 memory server를 할당 받는 것이였다.

```bash
> npm i -D @shelf/jest-mongodb
```

- 그리고 `jest-mongodb-config.js`에 다음과 같이 설정해줘야 한다.

```javascript
module.exports = {
  mongodbMemoryServerOptions: {
    instance: {
      dbName: 'jest',
    },
    binary: {
      version: '4.0.2', // Version of MongoDB
      skipMD5: true,
    },
    autoStart: false,
  },
};
```

- 그리고 `jest.config.js` 파일에 `preset`을 추가해준다.

```javascript
module.exports = {
  preset: '@shelf/jest-mongodb',
  // 생략..
};
```

- 다음으로 `mongoose schema`를 테스트를 할 수 있다.
- 아래와 같이 `global.__MONGO_URI__`를 사용하여 `global`로 테스트를 할 수 있다. 이 설정은 아까 테스트가 실행되면 `globalConfig.json`파일이 생성되는데 여기안에 들어있는 `mongoUri`가 들어가게 된다.
- 이 `mongoUri` 정보는 테스트가 실행될 때 마다 바뀐다.

```javascript
describe('User model', () => {
  let connection;

  beforeAll(async () => {
    connection = await mongoose.connect(global.__MONGO_URI__,
      { useUnifiedTopology: true, useNewUrlParser: true, useCreateIndex: true },
      (err) => {
        if (err) {
          process.exit(1);
        }
      });
  });

  afterAll(async () => {
    await connection.close();
  });
  // 생략..
});
```
- 다음은 `models`를 테스트 한 것이다.

```javascript
const userData = {
  id: 'test',
  hashedPassword: 'test123',
  createdAt: new Date(),
};

it('create & save user successfully', async () => {
  const validUser = new User(userData);

  const {
    _id, id, hashedPassword, createdAt,
  } = await validUser.save();

  expect(_id).toBeDefined();
  expect(id).toBe(userData.id);
  expect(hashedPassword).toBe(userData.hashedPassword);
  expect(createdAt).toBe(userData.createdAt);
});
```

- mongodb connect 테스트는 다음과 같이 mocking해서 테스트 할 수 있었다.

```javascript
const mongooseConnectSpyOn = (done) => (call) => jest
  .spyOn(mongoose, 'connect')
  .mockImplementationOnce((uris, options, callback) => {
    if (callback) {
      callback(call);
      done();
    }
    return Promise.resolve(mongoose);
  });
```

### ⚡ 아쉬운 점 및 회고
- 오늘은 어제 잠을 설치고 일어나 축구를 보고 잤고 일어났더니 1시였다.
- 아침에 일어날려고 일부러 12시에 잤는데 자다깨다를 반복해서 잠을 잘 못 자버렸다.
- 뭐가 그리 불안한건지 모르겠다.
- 그래서 결국 할당량을 채우기 위해서 12시가 다되버렸다. 만족한다 할 수는 없지만, 나쁘지 않은 하루였다고 생각한다.
- 오늘은 일찍 잘 수 있을까 의문이 든다.. 그래도 mongoDB 세팅까지 끝내서 기분은 좋다. 이제 해봤던 부분들이라 금방 금방 할 수 있을 거라고 생각한다.

### 🚀 내일 할 일
- 알고리즘 공부
- Recoil를 사용한 ToDo 앱 만들기 진행하기 (백앤드 api 만들기)
- 엘레강트 오브젝트 책 읽기

### 🎯 이번주 목표
- 알고리즘 공부 시작하기
- TypeScript, 앨레강트 오브젝트, Pro Git 책 읽기 (다 읽는다는 뜻이 아님.)
- Recoil를 사용한 ToDo 앱 만들기 진행하기
- 개인 프로젝트(스터디 후기)