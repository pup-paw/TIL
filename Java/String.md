# String (문자열)

### 문자와 문자열

    문자열(String)은 자바 프로그램이 실행되는 동안 가장 많이 생성되는 객체임

    문자열은 객체이지만 각각의 문자의 나열로 구성됨
    char capitalA = 'A'; // 문자
    String a = "abc"; // 문자열 == 문자의 배열

    문자열을 생성할 때 new 키워드 사용하지 말 것
    ex) String b = new String("abc");
    -> 기존에 만들어놓은 스트링 풀을 사용하는데, new 키워드를 사용하면 매번 객체가 생성

<hr>

## String vs StringBuffer/StringBuilder

### 차이점

🐾 String : 불변(immutable)의 속성을 가짐

```JAVA
String str = "hello";
str = str + " world";
```

![스크린샷 2022-03-04 오전 1 05 32](https://user-images.githubusercontent.com/69156709/156603440-2619c296-69c2-43eb-af86-2ced647e2eaf.png)

🙅‍♀️ str이 기존에 갖고있던 "hello" 에 " world" 를 더해 "hello world" 로 변경한 것으로 보일 수 있음

🙆‍♀️ "hello" 값이 들어 있던 String 클래스의 참조변수 str이 "hello world" 라는 값을 가지고 있는 새로운 메모리 영역을 가르키게 된 것

➡️ 처음 선언했던 "hello" 로 값이 할당되어 있던 메모리 영역은 Garbage 로 남아있다가  
 GC(Garbage Collection) 에 의해 사라지게 되는 것

🐾 StringBuffer/StringBuilder : 가변(mutable)성을 가짐

```JAVA
StringBuffer sb = new StringBuffer("hello");
sb.append(" world");
```

![스크린샷 2022-03-04 오전 1 06 13](https://user-images.githubusercontent.com/69156709/156603567-d1abbb00-7283-4f97-8b04-f1b141aef95b.png)

<hr>

## StringBuffer vs StringBuilder

### 차이점

    StringBuffer : 동기화 키워드를 지원
    -> 멀티쓰레드 환경에서 안전 (thread-safe)
    +) String도 불변성을 가지고 있기 때문에 thread-safe 함

    StringBuilder : 동기화를 지원하지 않음
    -> 단일쓰레드에서의 성능은 StringBuffer 보다 뛰어남 (동기화를 고려하지 않기 때문)

<hr>

## 정리

String : 문자열 연산이 적고 멀티쓰레드 환경일 경우  
StringBuffer : 문자열 연산이 많고 멀티쓰레드 환경일 경우  
StringBuilder : 문자열 연산이 많고 단일쓰레드이거나 동기화를 고려하지 않아도 되는 경우

<img width="463" alt="스크린샷 2022-03-04 오전 1 12 16" src="https://user-images.githubusercontent.com/69156709/156604789-97260caf-2ee4-41d3-951b-35786b75c466.png">

[참고 자료](https://ifuwanna.tistory.com/221)
