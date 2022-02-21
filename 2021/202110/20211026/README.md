## 📆 2021-10-26(화) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] [인프런 강의 듣기](https://github.com/saseungmin/practice-vanilla-js/tree/master/inflearn-apple-clone)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 클린 코드 3~5장 읽기 및 스터디 참여
- [ ] 테스트와 TDD에 대한 정리
- [ ] 개인 프로젝트 한피쳐씩 틈틈히
- [ ] 코어 자바스크립트 스터디 진행
- [x] 인프런 강의 듣기
- [ ] 건강 검진

### 🤔 공부하면서 배운것이 있다면?

- 윈도우 객체에 Mocking 후 테스트 하는 방법

```ts
describe('shareToKakao', () => {
    const { title, kakaoThumbnail, kakaoUrl } = mockSnsData;

    const mockSendDefault = jest.fn();

    window.Kakao = {
      Link: {
        sendDefault: mockSendDefault,
      },
    };

    it('Kakao 공유 이벤트가 호출된다', () => {
      shareToKakao(mockSnsData);

      expect(mockSendDefault).toBeCalledWith({
        objectType: 'feed',
        content: {
          title,
          description: '',
          imageUrl: kakaoThumbnail,
          link: {
            mobileWebUrl: kakaoUrl,
            webUrl: kakaoUrl,
          },
        },
        buttons: [
          {
            title: '',
            link: {
              mobileWebUrl: kakaoUrl,
              webUrl: kakaoUrl,
            },
          },
        ],
      });
    });
  });
```

#### Cypress Github Actions Yarn berry에서 안되는 문제 해결방법
- https://github.com/cypress-io/github-action/issues/430#issuecomment-949936528

#### tensei
- https://github.com/tenseijs/tensei
- Netlify CMS 대안??
- Gatsby에서 지원되는지는 미지수. (되면 아주 좋음)

### ⚡ 아쉬운 점 및 회고
즐거운 회사 생활. 오늘도 재밌고 즐거운 하루였다! 이제 많이 친해져서 자연스럷게 농담도 주고받고 얘기도 너무 많이 한다. 좋다! 그래도 나이때가 대부분 어려서 그런지 뭔가 잘 맞고 재밌다.   

내일은 아쉽게도 건강검진. 아무탈없었으면 좋겠다. 내일은 공가로 하루 쉬고 다시 목요일부터 출근!   

이번주 토요일에는 feconf2021 프론트엔드 컨퍼런스와 liftIO 2021 함수형 프로그래밍 컨퍼런스가 있다. 둘 다 열심히 들어야지. 내용을 보니 다 도움이 될만해보였다.   

아쉬운점 없음! 앞으로도 오늘만 같은 행복하고 즐거운 하루였으면 좋겠다!

### 🚀 내일 할 일
- 건강검진
- 인프런 강의 듣기
- 클린 코드 3장 읽기

### 🎯 이번주 목표
- 클린 코드 3~5장 읽기 및 스터디 참여
- 테스트와 TDD에 대한 정리
- 개인 프로젝트 한피쳐씩 틈틈히
- 코어 자바스크립트 스터디 진행
- 인프런 강의 듣기
- 건강 검진
- FeConf 2021, liftIO 2021 컨퍼런스 참여
