# 세번째 PR에 대한 희봉의 리뷰

### 같은 일급 컬렉션이 두개 존재할 때

    ❓ 희봉
    WinningBalls 와 Lotto 객체는 둘다 List<LottoBall> 의 일급 컬렉션임
    같은 일급 컬렉션이 두개나 있어야 할까?

    ❗️❓ 야호
    같은 일급 컬렉션이 두개나 있을 필요는 없는 것 같음

    하지만 WinningBalls 라는 객체는 Lotto 와 다르게 우승 번호라는 역할을 가지고 있음
    이에 Lotto 와의 match 기능도 있어야 한다고 생각함

    💡 Idea
    WinningBalls 를 List<LottoBall> winningBalls 이 아닌
    Lotto winningBalls 로 만들면 어떨까?

### 테스트가 없는 메서드

    ❗️ 희봉
    Money 의 rate() 메서드에 대한 테스트가 없음

    🛠 Fix
    테스트 코드 추가하기

### 너무 많은 역할을 하는 메서드

    ❗️ 희봉
    Lottos 의 purchase() 메서드에 대한 테스트가 없음
    너무 많은 걸 하고 있어 테스트가 어려운 것으로 보임

    💡 Solution
    1. 함수로 나누기
    2. 클래스로 나누기

    🛠 Fix
    purchase() 의 역할을 분리해 테스트 진행하기

### 배열보다는 리스트를 사용하자

    ❗️ 희봉
    배열보다는 리스트를 사용할 것

    🛠 Fix
    배열이 사용된 곳 모두 리스트로 바꾸기

### 보너스 번호를 포함한 5등

    ❗️ 희봉
    1,2,3,4,5,6 로또를 샀지만 당첨번호 1,2,3,11,12,13 보너스번호 4일 경우 5등을 못할 것 같음

    🛠 Fix
    Prize 의 getPrize 수정하기
