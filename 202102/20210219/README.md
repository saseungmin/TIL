## 📆 2021-02-19(금) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 알고리즘 공부
  - section 2를 끝냈다.
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기 (백앤드 api 만들기)
  - 회원인증시 필요한 JWT를 적용하였다. ([PR Link](https://github.com/saseungmin/Recoil_Todo_Backend/pull/7))
- [ ] 엘레강트 오브젝트 책 읽기

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 알고리즘 공부 시작하기
- [ ] TypeScript, 앨레강트 오브젝트, Pro Git 책 읽기
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기 (백앤드)
- [ ] 개인 프로젝트(스터디 후기)

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 Recoil를 사용한 ToDo 앱 만들기(백앤드)
- 회원인증에 사용할 토큰 방식인 JWT를 적용하였다.
- JWT는 유저가 로그인을 하면, 서버는 유저의 정보에 기반한 토큰을 발급하여 유저에게 전달해주고 유저가 서버에 요청을 할 때 마다 JWT를 포함하여 전달한다.
- JWT는 서버가 클라이언트에게서 요청을 받을때 마다, 해당 토큰이 유효하고 인증됐는지 검증을 하고, 유저가 요청한 작업에 권한이 있는지 확인하여 작업을 처리한다.
- 그래서 서버측에서는 유저의 세션을 유지 할 필요가 없어지게 된다. 즉, 유저가 로그인되어있는지 안되어있는지 신경 쓸 필요가 없고, 유저가 요청을 했을때 **토큰만 확인하면** 되서, 세션 관리가 필요 없어서 서버 자원을 많이 아낄 수 있게 된다.
- 이걸 간편하게 사용하게 해주는 `jsonwebtoken` 라이브러리를 사용해서 간단하게 적용할 수 있다.

```
> npm i -S jsonwebtoken
```

- 회원가입시 토큰을 제공해줘야햐되게 때문에 스키마 메서드를 정의하여 토큰 서명을 만든다.

```javascript
UserSchema.methods.generateToken = function () {
  const token = jwt.sign(
    { // 저장하고 싶은 정보
      _id: this._id,
      id: this.id,
    },
    process.env.JWT_SECRET, // 비밀키
    {
      expiresIn: '5d', // 5일 뒤 세션 만료
    },
  );

  return token;
};
```
- 회원가입시 토큰을 발급하여 쿠키에 저장한다. 

```javascript
const token = user.generateToken();

ctx.cookies.set('access_token', token, { // access_token 이름으로 토큰을 저장
  maxAge: 1000 * 60 * 60 * 24 * 5, // 쿠키 만료일은 5일 뒤
  // httpOnly는 자바스크립트의 document.cookie를 이용해서 쿠키에 접속하는 것을 막는 옵션으로 쿠키를 훔쳐가는 행위를 막기 위한 방법이다.
  httpOnly: true,
});
```

- 그리고 회원인증을 위한 middleware를 등록해준다.

```javascript
import jwt from 'jsonwebtoken';

import User from '../models/user';

const jwtMiddleware = async (ctx, next) => {
  const token = ctx.cookies.get('access_token'); // access_token으로 된 토큰을 가져온다.

  if (!token) { // 없으면 패스
    return next();
  }

  try {
    // 토큰과 비밀키를 사용해 복호화한다. 
    const decoded = jwt.verify(token, process.env.JWT_SECRET); 

    ctx.state.user = { // user 정보에 담는다.
      _id: decoded._id,
      id: decoded.id,
    };

    const now = Math.floor(Date.now() / 1000);

    if (decoded.exp - now < 60 * 60 * 24 * 2) { // 만약 만료일이 2일보다 적게 남았으면
      const user = await User.findById(decoded._id); // 해당 objectId의 유저를 찾는다.
      const token = user.generateToken(); // 토큰을 재발급한다.

      ctx.cookies.set('access_token', token, { // 다시 쿠키를 5일로 설정 한다.
        maxAge: 1000 * 60 * 60 * 24 * 5,
        httpOnly: true,
      });
    }

    return next();
  } catch (error) {
    return next();
  }
};

export default jwtMiddleware;
```

### ⚡ 아쉬운 점 및 회고
- 오늘도 역시 잠이 안와서 4시반쯤에 잤다. 그래서 또 11시에 일어났다.
- 오늘도 엘레강트 오브젝트를 읽지 못했다. 내일 가기전에라도 좀 읽고 가야겠다.
- 백앤드부분은 속돋가 잘 안난다. 처음이라 시간 투자가 많은 거 같다. 이젠 진짜 힘든 산은 다 넘었다고 생각한다.
- 얼른 recoil_todo를 끝내야겠다. 아마 다음주까지 하면 할 수 있지 않을까? 싶다.
- 알고리즘 공부도 처음에는 너무 쉽다 생각해서 괜히 들었나? 싶었지만, 그래도 점점 어려워지고 있어 충분히 도움이 될 만한 강의라고 생각한다. 물론 강사님은 코드는 readability와 복잡성, 결합도, immutable등을 전혀 신경쓰지 않고 풀어서 솔직히 의아하다. 때문에 내가 먼저 문제를 풀고 모르면 강의에서 힌트를 얻고 내 방식대로 풀고 있다.
- 내일은 아마 공부를 한자도 못할 듯 싶다. 놀러가기 때문에.. 가서 조금이라도 할까? 생각은 했지만 말도안되는 소리다. 그래도 내일 놀러가서 쉬고 오면 기분은 좋아지겠지!

### 🚀 내일 할 일
- 내일은 놀러가요!

### 🎯 이번주 목표
- 알고리즘 공부 시작하기
- TypeScript, 앨레강트 오브젝트, Pro Git 책 읽기 (다 읽는다는 뜻이 아님.)
- Recoil를 사용한 ToDo 앱 만들기 진행하기
- 개인 프로젝트(스터디 후기)