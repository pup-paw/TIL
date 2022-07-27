# 생성자 (Constructor)

## 생성자란?

1️⃣ 몇 개의 인자들을 전달받아  
&emsp; ex) LottoNumber(`int value`)

2️⃣ 이들을 이용해 어떤 일을 수행한 후,  
&emsp; ex) 유효성 판단(validate), 적절한 타입으로 파싱(parse)

3️⃣ 객체가 자신의 의무를 수행할 수 있도록 준비시킴  
&emsp; ex) this.value = value;

---

## 주 생성자(primary constructor)

```JAVA
Public class Player {
    private final Name name;
    private final Money money;

    public Player(Name name, Money money) {
        this.name = name;
        this.money = money;
    }
}
```

### 제공된 인자를 사용해서 캡슐화된 프로퍼티를 초기화

＞ 오직 주 생성자에만 초기화 로직을 위치시킴
＞ 주 생성자는 인스턴스 필드를 모두 포함하는 가장 간결하고 완전한 생성자여야 함

---

## 부 생성자(secondary constructor)

### 👎 나쁜 예

: 주 생성자를 사용하지 않고 직접 필드를 초기화

```JAVA
Public class Player {
    ...

    public Player(String name, int money) {
        this.name = new Name(name);
        this.money = new Money(money);
    }

    ...
}
```

### 👍 좋은 예

: 주 생성자를 사용해 초기화(constructor chaining)

```JAVA
Public class Player {
    ...

    public Player(String name, int money) {
        this(new Name(name), new Money(money));
    }

    ...
}
```

---

## 🤔 생성자를 여러개 만들어도 괜찮을까?

### 생성자가 여러개일 때 이점

1️⃣ 생성자의 수가 많아질수록 클라이언트가 클래스를 더 유연하게 사용할 수 있음

2️⃣ 중복 코드를 방지하고 설계를 더 간결하게 만들 수 있음

**🌟 응집도가 높고 견고한 클래스에는 적은 수의 메서드와 상대적으로 더 많은 수의 생성자가 존재**

### But, 생성자가 너무 많다면...

클래스가 너무 많은 일을 하고 있는게 아닌지 생각해보기

---

[생성자의 역할을 하는 정적 팩터리 메서드에 대해 알고싶다면?]()
