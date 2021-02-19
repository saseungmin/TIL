## 📆 2021-02-18(목) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 알고리즘 공부
  - infearn section 2 (배열 관련 문제) 4문제를 풀었다.
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기 (백앤드 api 만들기)
  - 회원가입에 대한 api를 구현했다. 
  - [PR Link](https://github.com/saseungmin/Recoil_Todo_Backend/pull/6)
- [ ] 엘레강트 오브젝트 책 읽기

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 알고리즘 공부 시작하기
- [ ] TypeScript, 앨레강트 오브젝트, Pro Git 책 읽기
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기 (백앤드)
- [ ] 개인 프로젝트(스터디 후기)

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 Recoil를 사용한 ToDo 앱 만들기(백앤드)
- mongodb와 api 통신을 하기 위해서 register를 구현했다.
- 회원가입시 필요한 것.
- 한 1년전에 `hapi/joi`를 사용하여 `schema` validate 검증을 했는데, 지금 봐보니 `deprecated`되어있었다. 그래서 찾아봤는데, `Joi`라는 이름으로 되어있는 것을 사용하였다.

```bash
> npm i -S joi
```

- 다음과 같이 넘어온 값을 간단히 validate 해줄 수 있다.

```javascript
import Joi from 'joi';

export const validateUser = (value) => {
  const schema = Joi.object().keys({
    id: Joi.string() // string
      .alphanum() // 알파벳과 숫자
      .min(3) // 최소 길이 3
      .max(20) // 최대 길이 20
      .required(), // 필수 값
    password: Joi.string()
      // // 3 ~ 30 길이에 알파벳 소문자 대문자 또는 숫자 사용가능
      .pattern(new RegExp('^[a-zA-Z0-9]{3,30}$'))
      .required(),
  });

  return schema.validate(value);
};
```

- mongoose에서는 데이터 모델에 임의 메소드, 그리고 쿼리 헬퍼를 만들어서 데이터 작업을 좀 더 용이하게 할 수 있다.
- 모델 메소드는 `.statics` 와 `.methods` 두 종류로 만들 수 있다.
- 둘의 차이점은 서로 가르키는 this 값이 다르다. 전자의 경우엔 모델 자체를 가르키고, 후자의 경우엔 데이터 인스턴스를 가르킨다.

```javascript
UserSchema.statics.findByUserId = function (id) { // 아이디 찾기
  return this.findOne({ id });
};

UserSchema.methods.setPassword = async function (password) {
  const hash = await bcrypt.hash(password, 10); // 비밀번호를 해시값으로 변환

  this.hashedPassword = hash;
};

UserSchema.methods.serialize = function () { // 해시된 비밀번호를 제외하고 return
  const data = this.toJSON();

  delete data.hashedPassword;
  return data;
};
```
- 이렇게 메소드를 만들면, 우리가 원하는 작업마다 이름을 붙여 줄 수있게 되고 코드를 분리시킬 수 있게 되어 가독성도 높아지고, 쿼리를 작성 할 때 데이터 구조를 확인하기 위하여 컨트롤러 파일과 모델 파일을 동시에 볼 필요도 없어서 편해진다.
- 이에 대한 테스트는 다음과 같이 진행할 수 있었다.

```javascript
 it('should findByUserId statics method exist id', async () => {
    const { id } = await User.findByUserId('test');

    expect(id).toBe('test');
  });

  it('should setPassword method Convert to hash value and save', async () => {
    const noneHashedPassword = 'test123';

    const user = new User({ id: 'test11' });

    await user.setPassword(noneHashedPassword);

    const { hashedPassword } = await user.save();

    expect(hashedPassword).not.toBe(noneHashedPassword);
  });

  it('should the hashed password is deleted and returned', async () => {
    const user = new User({ id: 'test123', hashedPassword: '123' });

    const { hashedPassword, id } = await user.serialize();

    expect(id).toBe('test123');
    expect(hashedPassword).toBeUndefined();
  });
```

- 전체적인 `auth` api에 대한 테스트 작성은 `supertest`를 사용해서 할 수 있었다.

```javascript
const payload = {
  id: 'seugmin',
  password: 'test123',
};

it('Response is Success Status', async () => {
  const { body, status } = await request(app.callback())
    .post('/api/auth/register')
    .send(payload);

  expect(status).toBe(201);
  expect(body).toHaveProperty('id', 'seugmin');
});
```

### ⚡ 아쉬운 점 및 회고
- 잠을 4시반쯤에 잤다. 잠을 자기 위해서 12시 반쯤에 누웠지만 소용없었다. 잠을 잘려고 노력해도 잠이 잘 오지 않았다. 이유를 모르겠다.
- 4시반쯤 자서 10시에 일어났다. 잠을 얼마 자지 못해서 피곤하긴 하지만 못 버틸 정도는 아니였다.
- 오늘 Recoil_Todo backend test를 진행하면서 확실하게 느낀게 있었다.
- 이걸 까먹고 있었다는 게 한심하게 느껴졌지만, 몸소 느껴서 확실히 얻었다는 느낌을 받았다.
- 루비로 배우는 객체지향 디자인 책에 있던 내용이였는데 테스트를 하기 어려운 건 없다. 만약 테스트를 하기 어렵다고 느껴진다면 그건 내가 짠 코드가 가지고 있는 역할이 많고 결합도가 높다는 것이다. 그렇기에 응집도가 낮아 유지보수가 힘든 것이다.
- 그래서 역할들을 function마다 분리하여 관리하니 확실히 테스트하기가 수월했다.
- 진행하면서 또 문제가 되는 점이 있따면 현재 백앤드 부분 테스트는 처음이라 TDD가 제대로 안된다는 점이다. 어쩔 수 없이 TDD 사이클은 못따라가지만 테스트를 작성한다는데에 의미를 두는것이 좋을 거 같다. 익숙하지 않다는 점이 가장 큰 문제일 듯 하다.
- 그래도 신기한 건 찾아보면서 꾸역꾸역 다 하고 있다는 점이다. 예전 같았으면 시도하기 두려워 포기를 했겠지만, 계속 해보다보니 점점 만들어져가는게 신기할 따름이다. 나도 모르는 사이에 확실히 실력이 올랐다고 생각한다.
- 이제 백앤드 부분 나머지는 빨리빨리 할 수 있을 것이다. 모르는 부분은 어느정도 해소가 되었기 떄문이다.
- 오늘은 앨레강트 오브젝트 책을 읽으려 했지만 읽지 못했다. 내일은 꼭 읽어야 한다.
- 다음주 스터디를 위해서도 그렇지만, 주말에 친구들과 여행? 놀러가기로 했기 떄문에.. 미리미리 해놔야할 거 같다.

### 🚀 내일 할 일
- 알고리즘 공부
- Recoil를 사용한 ToDo 앱 만들기 진행하기 (백앤드 api 만들기)
- 엘레강트 오브젝트 책 읽기

### 🎯 이번주 목표
- 알고리즘 공부 시작하기
- TypeScript, 앨레강트 오브젝트, Pro Git 책 읽기 (다 읽는다는 뜻이 아님.)
- Recoil를 사용한 ToDo 앱 만들기 진행하기
- 개인 프로젝트(스터디 후기)