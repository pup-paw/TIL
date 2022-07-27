# VO

한 개 또는 그 이상의 속성들을 묶어서 특정 값을 나타내는 객체

### 1. equals & hash code 메서드를 재정의해야 한다.

    속성값이 같은 객체는 같은 객체임을 보장하며 사용할 수 있음

참고 : [동일성과 동등성](https://github.com/pup-paw/TIL/blob/main/woowacourse/LV1/identity_equality.md)

### 2. 수정자(setter)가 없는 불변 객체여야 한다.

    VO 는 속성값 자체가 식별 값임
    ＞ 값이 바뀌면 다른 값이 되어 추적이 불가함
    ＞ 복사될 때는 의도치 않은 객체들이 함께 변경될 수 있음

참고 : [불변 객체]()

### ❓ VO 는 가변이면 안될까?

VO 는 Value Object 라는 말 그대로 `값 객체`를 의미함  
＞ 따라서 하나의 값을 나타내야 하는 VO 가 값이 변화할 수는 없음
