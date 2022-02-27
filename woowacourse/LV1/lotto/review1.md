# 첫번째 PR에 대한 희봉의 리뷰

### main과 Controller

    ❓ 야호
    모든 실행을 총괄해주는 역할이라고 생각함
    그렇다면 lotto와 같이 하나의 프로그램만 실행될 경우 Controller 내에 main을 두어 사용하면 되지 않을까?

    ❗️ 희봉
    Application은 야호가 생각한 것처럼 실행을 총괄하는, 정확히는 실행하는 역할임
    자바에서는 main부터 프로그램이 시작하기 때문에 필요한 값들을 Application의 main()에서 설정하고 실행함

    헷갈린다면, 각각의 장점을 생각해보기

    💡 Solution
    Controller의 main이 실행될 때의 장점
    관리할 클래스가 줄어듦

    Application의 main이 실행될 때의 장점
    Controller의 캡슐화를 지킬 수 있음
    Controller의 역할이 아닌 다른 역할을 실행할 수 있음

    🛠 Tip
    Controller도 하나의 객체임
    Application이라는 다른 class에서 controller 객체를 생성하면 public 함수만 접근할 수 있음

    + 의존성 주입에 대해 알아보기

### TDD 중 생성자에 대한 테스트

    ❓ 야호
    Lotto의 역할을 TDD 하면서 자연스럽게 생긴 Lotto 생성자에 대한 테스트도 필요할까?

    ❗️ 희봉
    굳이 생성자 테스트 코드가 있을 필요는 없음

    하지만 TDD 중간에는 생성자 테스트가 있는게 좋음
    (TDD는 테스트코드를 먼저 짜고 운영 코드를 작성하므로 모든 운영 public 함수는 테스트코드를 가져야함)

    💡 Solution
    Lotto lotto1 = new Lotto();
    Lotto lotto2 = new Lotto();

    assertThat(lotto1).isEqualTo(lotto2);

    지금 바로 테스트를 진행하면 테스트가 실패할 것임
    -> equals(), hashCode() 함수 알아보기
    + 테스트가 힘든 코드인 Collection.shuffle() 분리하기

    [이펙티브 자바]
    아이템 10 : equals는 일반 규약을 지켜 재정의하라
    아이템 11 : equals를 정의하려거든 hashCode도 재정의하라
    아이템 12 : toString을 항상 재정의하라

    🛠 Fix
    Lotto 생성자에 대한 테스트 진행하기

### TDD 중 생성자에 대한 테스트

    ❓ 야호
    Lotto의 역할을 TDD 하면서 자연스럽게 생긴 Lotto 생성자에 대한 테스트도 필요할까?

    ❗️ 희봉
    굳이 생성자 테스트 코드가 있을 필요는 없음

    하지만 TDD 중간에는 생성자 테스트가 있는게 좋음
    (TDD는 테스트코드를 먼저 짜고 운영 코드를 작성하므로 모든 운영 public 함수는 테스트코드를 가져야함)

    💡 Solution
    Lotto lotto1 = new Lotto();
    Lotto lotto2 = new Lotto();

    assertThat(lotto1).isEqualTo(lotto2);

    지금 바로 테스트를 진행하면 테스트가 실패할 것임
    -> equals(), hashCode() 함수 알아보기
    + 테스트가 힘든 코드인 Collection.shuffle() 분리하기

    [이펙티브 자바]
    아이템 10 : equals는 일반 규약을 지켜 재정의하라
    아이템 11 : equals를 정의하려거든 hashCode도 재정의하라
    아이템 12 : toString을 항상 재정의하라

    🛠 Fix
    Lotto 생성자에 대한 테스트 진행하기

### `Arrays.asList()` 의 패키지

    ❗️ 희봉
    assertj.core에 있는 Arrays.asList()는
    인자로 배열을 받고,
    리턴 타입이 List<Object> 임 (이 경우는 지양하는 것이 좋음)

    💡 Solution
    java.util에 있는 Arrays.asList()는
    인자로 vararg, 즉 Arrays.asList(1, 2, 3, 4, 5, 6) 형태로 사용할 수 있고,
    리턴타입이 List<Integer>로 제네릭의 효과를 온전히 사용할 수 있음

    🛠 Fix
    ShuffleTest의 Arrays.asList() import 수정

### 인터페이스의 목적

    ❗️ 희봉
    LottoNumber가 인터페이스로 구현된 이유는 무엇일까?

    💡 Solution
    함수 재사용이 목적이라면 [이펙티브 자바 : 상속보다 조합을 사용하자] 읽어보기

    🛠 Fix
    프로그램 내의 모든 Lotto와 관련된 숫자를 처리하기
    interface vs composition

### static의 목적

    ❗️ 희봉
    Controller의 함수를 모두 static으로 만든 이유가 무엇일까?

    💡 Solution
    고민해보기

    🛠 Fix
    ...
