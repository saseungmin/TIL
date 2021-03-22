## 📆 2021-03-22(월) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기
  - TO Do Filter 적용시 생기던 오류를 해결
  - [PR Link](https://github.com/saseungmin/Recoil_ToDo/pull/70)
- [x] 오브젝트 Chapter 10 다 읽기
  - [PR Link](https://github.com/saseungmin/reading_books_record_repository/pull/46)
- [x] 취업 준비 스터디 참여하기
  - 앞으로 어떻게 진행해해야할 것인가에 대해서 얘기를 하였다.

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 알고리즘 공부 (Section 6)
- [x] 오브젝트 책 Chapter 11 까지 읽기 및 스터디 참여
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기
- [x] 취업 준비 스터디 관련 준비 및 스터디 참여

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 Recoil을 사용한 To DO 애플리케이션 만들기
- 이 놈의 cors... 드디어 원인을 찾은거 같다. cookie가 safari와 ios에서 안되는 이유를..
- chrome에서만 되는 것이였다.
- `secure` 쿠키 전달을 하려면 프론트(React)와 로그인 API를 제공할 백엔드(서버 API)는 같은 도메인을 공유해야한다. 즉, `abc.test.com` , `dfg.test.com` 이런식으로 되어야 한다. 그리고 cookie 도메인 부분에 domain: '.test.com' 이런식으로 가능한 것이다.
- [참고 링크](https://stackoverflow.com/questions/1062963/how-do-browser-cookie-domains-work)
- 여태까지 `.github.io` 도메인과 `.heroku.com` 도메인으로 하니까 당연히 안될 수 밖에 없었다. 제 3자의 도메인은 수정과 읽기도 불가능했기 때문이다. 물론 생성은 가능하다. 하지만 사용할 수 없기 때문에 이런 문제가 생겼다. 도메인을 서브 도메인 같이ㅣ 위 예제 처럼 같게 하면 수정은 불가능 하지만, 읽기는 가능하다.
- [참고 링크](http://blog.naver.com/PostView.nhn?blogId=gomland&logNo=221492821285)
- [참고 링크](https://velog.io/@yaytomato/%ED%94%84%EB%A1%A0%ED%8A%B8%EC%97%90%EC%84%9C-%EC%95%88%EC%A0%84%ED%95%98%EA%B2%8C-%EB%A1%9C%EA%B7%B8%EC%9D%B8-%EC%B2%98%EB%A6%AC%ED%95%98%EA%B8%B0)

#### 🎈 오브젝트 Chapter 10
- 오브젝트 Chapter 10 정리 [링크](https://github.com/saseungmin/reading_books_record_repository/tree/master/%EC%98%A4%EB%B8%8C%EC%A0%9D%ED%8A%B8/Chapter%2010)

### ⚡ 아쉬운 점 및 회고
- 후 여태까지 문제의 원인조차 모르고있었다는 사실에 다시 한번더 충격이고, 공부를 해야겠다는 생각이든다.
- 괜히 알지도 못하고 기본도 공부하지 않은 것을 써먹어서 애를 먹고 있는지 싶다. 그냥 마음 편하게 jwt토큰 인증을 안할껄 그랬나보다..
- 이제 원인은 찾은거 같다. 해결방법은 프론트 부분도 백앤드부분을 이미 heroku로 했기 때문에 그냥 프론트부분도 heroku로 변경할 생각이다.
- 이거때문에 여태까지 삽질했는데 내일 다시 도전해본다. 이제 구현은 끝났다.
- 오늘 새로운 스터디를 처음 시작했는데 나름 재밌을 거 같고 여태까지 지나치고 공부안하던 것들을 다시 차근차근한다는 생각으로 도전해야할거 같다.
- 끝.

### 🚀 내일 할 일
- Recoil를 사용한 ToDo 앱 만들기 진행하기 (배포 Heroku로 변경)
- 오브젝트 Chapter 11 반 읽기
- 스터디 질문 선정하기
- 알고리즘 공부(Recoil이 금방 해결되면)

### 🎯 이번주 목표
- 알고리즘 공부 (Section 6)
- 오브젝트 책 Chapter 11 까지 읽기 및 스터디 참여
- Recoil를 사용한 ToDo 앱 만들기 진행하기
- 취업 준비 스터디 관련 준비 및 스터디 참여