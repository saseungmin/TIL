## 📆 2021-12-15(목) TIL

### 📈 오늘 한 일
- [x] Conners 프로젝트 구현
  - [x] 팀 모집하기 글 작성 URL Path를 new에서 write로 변경하기
  - [x] 홈화면에 스터디, 프로젝트 리스트를 볼 수 있다

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- ~~스칼라로 배우는 함수형 프로그래밍 7장 읽고 스터디~~
- Conners 프로젝트 구현
  - ~~디테일 페이지에서 작성자 정보와 마감 일시를 볼 수 있다.~~
  - ~~팀 모집하기 등록 모달창에서의 등록 플로우 수정~~
  - [x] 팀 모집하기 글 작성 URL Path를 new에서 write로 변경하기
  - [x] 홈 화면에 스터디, 프로젝트 리스트를 볼 수 있다
- [ ] 리팩터링 7장 읽고 스터디

### 🤔 공부하면서 배운것이 있다면?
- https://github.com/vercel/turborepo
- https://github.com/reactwg/server-components

#### Yarn berry를 사용한 문제되었던 사항 (Next.js and react-hook-form)

1. yarn berry를 사용하여 Next.js 12.0.5 버전 이상을 사용했을 때 next dev, next build가 깨지는 현상
- https://github.com/vercel/next.js/issues/32115
- Next.js를 12.0.4버전으로 다운그레이드

2. `@hookform/resolvers`의 `yupResolver`의 모듈을 못찾는 현상
- https://github.com/react-hook-form/resolvers/issues/271
- 해결방법은 import 변경 및 
```js
// 원래 방법
import { yupResolver } from '@hookform/resolvers';

// 변경한 방법
import { yupResolver } from '@hookform/resolvers/yup/dist/yup';
```

3. yarn berry 사용시 `react-hook-form` 모듈을 찾지 못하는 현상
- `react-hook-form`을 v.7.22.0 이하 버전으로 다운그레이드

### ⚡ 아쉬운 점 및 회고
오늘은 웹 POC 플레닝을 했다. 2시간 가량 진행되었고, 앞으로 MVP에 어떤 것들을 정리하고 할지를 정하는 자리였다. 새로운 PO 분도 굉장히 좋으신 분인 거 같다. 앞으로 재밌게 web을 뚝딱 뚝딱 만들 수 있을 거 같다!    

제니랑 하고 있는 코너스 역시 아직까진 순조롭게 진행중이다. 분먕 앞으로 기술적으로 막히는 부분이 있겠자만, 이전에 해놨던 것도 constu 프로젝트도 있고, 레퍼런스 삼을만한게 있어서 괜찮다.   

하루하루 새로운것들을 머리속에 집어넣는중.. 성장을 잘하고 있는지? 아직까진 괜찮은 거 같다. 하지만, 뭔가 주먹구구식으로 개발을 진행하면 역시나 의문이 들거고, 회의감과 번아웃이 올 것이다. 어렵겠지만 기본에 충실하려고 노력하고 항상 "왜"에 집중하려고 노력하자.

### 🚀 내일 할 일
- 리팩터링 7장 읽고 스터디
- Conners 프로젝트 구현

### 🎯 이번주 목표
- 스칼라로 배우는 함수형 프로그래밍 7장 읽고 스터디
- Conners 프로젝트 구현
  - 디테일 페이지에서 작성자 정보와 마감 일시를 볼 수 있다.
  - 팀 모집하기 등록 모달창에서의 등록 플로우 수정
  - 팀 모집하기 글 작성 URL Path를 new에서 write로 변경하기
  - 홈화면에 스터디, 프로젝트 리스트를 볼 수 있다
- 리팩터링 7장 읽고 스터디
