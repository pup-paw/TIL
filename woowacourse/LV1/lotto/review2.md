# 두번째 PR에 대한 희봉의 리뷰

### getter를 지양해야 할까?

    ❓ 야호
    setter의 경우 값을 변경할 경우를 막아야하니 지양하는 것이 이해됨
    하지만 getter의 경우 값을 변경할 수도 없는데 왜 지양해야 할까?

    ❗️ 희봉
    객체지향에서는 객체에게 메세지를 보내는 것을 지향함

    💡 Solution
    getter를 사용하면 안되는 것이 아닌,
    getter를 사용하지 않으면서 자연스럽게 메세지를 보내는 연습을 하는 것이 중요

### distinct()가 되지 않는 경우

    ❓ 야호
    Number 객체를 만들고 나니, distinct()가 되지 않음
    equals()와 hashCode() 를 오버라이딩 후 수정해서 사용해야 할까?

    ❗️ 희봉
    equals()와 distinct()는 인텔리제이에서 자동으로 만들어주는 기능을 활용하기

    💡 Solution
    1. Number equals 테스트 (생성자로 같은 값의 객체 생성 후 equals로 확인)

    2. WinningNumber equals 테스트 (생성자로 같은 값의 객체 생성 후 equals로 확인)

    3. getDistinctCount() 에서 map 부분을 지우고, 기존의 테스트 코드가 통과하는지 확인

    🛠 Fix
    map을 사용하지 않고 WinningNumber 자체가 중복인지 확인
    getNumber() 메서드가 필요하지 않다면, 삭제하기

### 테스트에서 사용된 for 문

    ❗️ 희봉
    테스트에서는 for 문 등을 사용하지 않고,
    정확한 값을 넣어주는 것이 테스트의 의도와 맞음

    🛠 Fix
    WinningNumbersTest 에서 사용된 for 문 삭제 후 정확한 값 입력

### 테스트마다 새로운 given이 필요할 떄

    ❗️ 희봉
    각 테스트마다 새로운 given 값이 필요하다면,
    각각 새로 만드는 것이 한 눈에 알아보기 더 쉬움

    🛠 Fix
    WinningNumbersTest 에서 각 테스트마다 새로 given 작성

### equals() 오버라이딩

    ❗️ 희봉
    지금 레벨에서는 equals() 오버라이딩을 인텔리제이의 자동완성으로 사용하는 것이 좋음

    🛠 Fix
    WinningNumber의 equals()를 기본 제공되는 것으로 변경
