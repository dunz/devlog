# Prologue
매년 프론트엔드 개발자 최대의 컨퍼런스로 자리매김하고 있는
2018년 feconf 포스팅입니다
총 두 트랙으로 나뉘어서 선택하여 들을 수 있었습니다.

### 1세션) 미국개발자 vs 한국개발자 - Ken Huh(바닐라 코딩)
##### Programming Skills
- 실력면에서는 차이가 없다
- 미국개발자의 장점은 영어능력, 한국 개발자도 영어를 잘해야 한다(영어 독해 능력)

##### Collaboration
- 협업에 있어서는 미국개발자 win
> 아마존에 3개월만에 서비스 하나를 런칭했던 팀에 들어갔는데 생각보다 개개인의 실력이 뛰어나지 않았다.
다만 각자의 역할에 대한 이해와 책임감이 명확하고 협업 능력이 뛰어나 하나의 유기체처럼 움직였다

##### Individual Mindset
- 내가 단순한 코드몽키가 아니고 나만의 기준, 도덕적 기준이 개발자인가 생각을 해야한다

### 2세션)_Redux-Saga - 제너레이터, 사이드이펙트, 채널 - 이민규(토스)
#####defferd 패턴
```js
const createDefferd = () => {
    const def = {};
    def.promise = new Promise((resolve, reject) => {
       def.resolve = resolve;
       def.reject = reject;
    });
    return def;
}
```
> - promise의 resolve, reject처리를 외부로 꺼냄
> - defferd패턴 일반화 => CSP
##### takeLatest Effect
같은 action이 반복해서 들어올 경우 
먼저 들어온 액션이 끝나기전에 새로운 액션이 호출되면 기존액션을 자동을 취소시킴
> 두개의 게시판을 연속해서 번갈아가며 클릭할경우 리스트가 계속 변경될텐데 그럴 경우 사용 가능

> 참고: Redux-Saga[Link](https://drive.google.com/file/d/1ttAVFSIo_2VANI-KIJIn0Sv2NUOKJI4m/view?usp=sharing)

##### saga Thread 활용
채널을 이용해서 낭비되는 시간을 절약 가능

### 3세션) 생각보다 쉬운 webGL (feat. three.js) - 전기환(중앙일보)
1. WebGL 뭔데?
- 웹브라우저에서 gpu를 활용하여 렌더링을 함

> 참고: 생각보다 쉬운 WebGL[Link](https://docs.google.com/presentation/d/1dAX9mid8tf2JaVGusy6rN_GeZPHcI3M9sY9Q2z02huU/edit?usp=sharing)

### 4세션) 웹폰트의 사용과 최적화 - 이상진(엔테크서비스)
1. 사용현황
약 68% 의 사이트가 웹폰트를 사용

```css
font-face {
    font-family: 'name';
    src: url() format();
}
div {
    font-family:'name';
}
```

2. 문제점
네트워크 상태가 안좋거나 웹폰트의 용량이 클 경우 텍스트페인팅 블록 현상이 발생 가능

해결책
 - 용량 줄이기 
   - woff2 포맷
   - subset폰트 사용, 한글 한글 조합형의 경우의 수(11,172자 => 2,350자(안쓰는글자제거 ksx1001) => subset font maker
   - unicode range 사용 => 쓰는폰트만 다운받기 때문에 불필요한 리소스 낭비를 막을 수 있음
 - 보이지 않는 텍스트
   - 브라우저별 처리방식
     - 모던브라우저: FOIT => 다운로드 될때까지 텍스트를 렌더링 하지 않는다, 타임아웃 설정 가능
     - IE: FOUT => 다운로드 될때까지 기본폰트로 렌더링 후 다운로드 완료시 웹폰트로 렌더링한다
     - 텍스트는 항상 보이게 => fontLoader 라이브러리 => fontFaceObserver
     - 로딩전과 후의 클래스를 설정 후 자바스크립트 에서 폰트 완료시 클래스적용
     - font-display옵션 => auto, block, swap(FOUT동작) , fallback, optional
     - 항상 보이게 하려면 => swap, fallback, optional
 - 폰트간 차이 줄이기
   - font syle matcher
     - webfont와 fallback폰트 차이가 없도록 css적용
   - preload 옵션
     - 링크태그 안에 preload 옵션을 줌(신중히 적용해야 함)

> 참고: 웹폰트 최적화[Link](https://slides.com/sangjinlee/webconf-2018-5#/)
            
 
