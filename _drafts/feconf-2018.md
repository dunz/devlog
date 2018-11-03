# Prologue
매년 프론트엔드 개발자 최대의 컨퍼런스로 자리매김하고 있는
2018년 feconf 포스팅입니다
총 두 트랙으로 나뉘어서 선택하여 들을 수 있었습니다.

### 1세션) 미국개발자 vs 한국개발자 - Ken Huh
##### Programming Skills
- 실력면에서는 차이가 없다
- 미국개발자의 장점은 영어능력, 한국 개발자도 영어를 잘해야 한다(영어 독해 능력)

##### Collaboration
- 협업에 있어서는 미국개발자 win
> 아마존에 3개월만에 서비스 하나를 런칭했던 팀에 들어갔는데 생각보다 개개인의 실력이 뛰어나지 않았다.
다만 각자의 역할에 대한 이해와 책임감이 명확하고 협업 능력이 뛰어나 하나의 유기체처럼 움직였다

##### Individual Mindset
- 내가 단순한 코드몽키가 아니고 나만의 기준, 도덕적 기준이 개발자인가 생각을 해야한다

### 2세션)_Redux-Saga - 제너레이터, 사이드이펙트, 채널 - 이민규
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

##### saga Thread 활용
채널을 이용해서 낭비되는 시간을 절약 가능