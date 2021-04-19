## 📆 2021-04-19(월) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 알고리즘 Section8 풀기
  - 두 문제 풀었다.
  - [중복순열 구하기](https://github.com/saseungmin/daily_coding_dojo/tree/master/inflearn_algorism/section8/solution8)
  - [동전교환](https://github.com/saseungmin/daily_coding_dojo/tree/master/inflearn_algorism/section8/solution9)
- [x] 테스트 주도 개발로 배우는 객체 지향 설계와 실천 5장 6장 읽기
  - [Chapter 5 PR](https://github.com/saseungmin/reading_books_record_repository/pull/60)
  - [Chapter 6 PR](https://github.com/saseungmin/reading_books_record_repository/pull/61)
- [x] 스터디 준비 및 스터디 참여
  - 기술 면접 준비 스터디를 준비하였고 참여하였다.
- [x] 코드숨에서 진행했던 프로젝트 더 꾸며보기 (반응형)
  - [PR Link](https://github.com/CodeSoom/ConStu/pull/172)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 알고리즘 Section 7 끝내고 Section 8 풀기
- [x] 기술 면접 준비 스터디 관련 준비 및 스터디 참여
- [x] 테스트 주도 개발로 배우는 객체 지향 설계와 실천 4장까지 읽기
- [x] 코드숨에서 진행했던 프로젝트 더 꾸며보기
- [ ] 코어 자바스크립트 Chapter 4까지 읽기

### 🤔 공부하면서 배운것이 있다면?
- [테스트 주도 개발로 배우는 객체 지향 설계와 실천 Chapter 5 정리](https://github.com/saseungmin/reading_books_record_repository/tree/master/%ED%85%8C%EC%8A%A4%ED%8A%B8%20%EC%A3%BC%EB%8F%84%20%EA%B0%9C%EB%B0%9C%EB%A1%9C%20%EB%B0%B0%EC%9A%B0%EB%8A%94%20%EA%B0%9D%EC%B2%B4%20%EC%A7%80%ED%96%A5%20%EC%84%A4%EA%B3%84%EC%99%80%20%EC%8B%A4%EC%B2%9C/Chapter%205)
- [테스트 주도 개발로 배우는 객체 지향 설계와 실천 Chapter 6 정리](https://github.com/saseungmin/reading_books_record_repository/tree/master/%ED%85%8C%EC%8A%A4%ED%8A%B8%20%EC%A3%BC%EB%8F%84%20%EA%B0%9C%EB%B0%9C%EB%A1%9C%20%EB%B0%B0%EC%9A%B0%EB%8A%94%20%EA%B0%9D%EC%B2%B4%20%EC%A7%80%ED%96%A5%20%EC%84%A4%EA%B3%84%EC%99%80%20%EC%8B%A4%EC%B2%9C/Chapter%206)
- [CORS란 무엇인가에 대해서 정리](https://github.com/Fortuna-Study/Frontend-Interview-Library/tree/main/week_4/seungmin#-cors%EC%97%90-%EB%8C%80%ED%95%B4%EC%84%9C-%EC%84%A4%EB%AA%85%ED%95%98%EC%84%B8%EC%9A%94)
- [this에 대해서 정리](https://github.com/Fortuna-Study/Frontend-Interview-Library/tree/main/week_4/seungmin#-this%EC%97%90-%EB%8C%80%ED%95%B4%EC%84%9C-%EC%84%A4%EB%AA%85%ED%95%B4%EC%A3%BC%EC%84%B8%EC%9A%94)
- [Redux-toolkit에 대해 정리](https://github.com/Fortuna-Study/Frontend-Interview-Library/tree/main/week_4/seungmin#-redux-toolkit%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%B4%EB%B3%B4%EA%B3%A0-%ED%8A%B9%EC%A7%95-%EC%9D%B4%EC%95%BC%EA%B8%B0%ED%95%98%EA%B8%B0)
- 코드숨 프로젝트를 진행하면서 드롭다운시 바깥쪽 클릭시 사라지게 하는 이벤트를 설정해주는 방법을 배웠다. 근데 이게 라이브러리가 존재해서 금방할 줄 알았는데 react 17 버전에서는 호환이 안되서... 결국 직접 만들어서 사용했다.

```js
const UserHeaderStatus = ({ user, onClick }) => {
  const isMobileScreen = useMediaQuery({ query: '(max-width: 450px)' });

  const [isVisible, setVisible] = useState(false);
  const userIconRef = useRef();

  const isLoggedIn = isMobileLoggedIn(isMobileScreen);

  const handleClickOutside = useCallback((e) => {
    if (!userIconRef.current) { // ref에 current 가 존재하지 않으면
      return;
    }

    // 현재 ref의 current 값과, e.target의 값이 같으면 드롭다운이라는 소리기 떄문에 사라지면 안된다.
    if (_.isEqual(userIconRef.current, e.target) || userIconRef.current.contains(e.target)) {
      return;
    }

    // 드롭다운 없애기
    setVisible(false);
  }, [userIconRef]);

  useEffect(() => {
    if (isLoggedIn(user)) {
      //  마우스 다운시 호출.
      document.addEventListener('mousedown', handleClickOutside);
    }
  }, [user, handleClickOutside]);

  useUnmount(() => {
    if (isLoggedIn(user)) {
      document.addEventListener('mousedown', handleClickOutside);
    }
  });

  if (isMobileScreen) {
    return (
      <div
        ref={userIconRef}
      >
        <UserIcon
          onClick={() => setVisible(!isVisible)}
          data-testid="user-icon"
        />
        <DropDown
          user={user}
          visible={isVisible}
          onLogout={onClick}
        />
      </div>
    );
  }

  // ...
};

export default UserHeaderStatus;
```


### ⚡ 아쉬운 점 및 회고
- 와우! 언블리버블 정신나간거지..
- 아니 잠깐만 할려했는데 왜! 6시간이 지났지.. 제발.. 얼른 쓰고 자야겠다.. 오늘 너무 피곤한 하루. 너무 정신나가게 공부했다.
- 좀 시간을 정해서 해보자.. 어쨌든.. 얼른 자자..

### 🚀 내일 할 일
- 알고리즘 Section8 풀기
- 테스트 주도 개발로 배우는 객체 지향 설계와 실천 7장 8장 읽기
- 코드숨에서 진행했던 프로젝트 더 꾸며보기 (반응형)

### 🎯 이번주 목표
- 인프런 알고리즘 Section 8 풀기
- 기술 면접 준비 스터디 관련 준비 및 스터디 참여
- 코드숨에서 진행했던 프로젝트 더 꾸며보기 (반응형)
- 테스트 주도 개발로 배우는 객체 지향 설계와 실천 9장까지 읽고 스터디 참여
- Core JavaScript 4장 읽기
