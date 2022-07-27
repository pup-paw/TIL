# ThreadLocal

쓰레드 단위로 로컬 변수를 할당하는 기능 제공

## ThreadLocal 이란?

### 일반적인 변수

특정 코드 블록(메서드 범위, for 블록 범위, ...) 범위 내에서만 유효

```JAVA
{
    int a = 10; // 블록 내에서 a 변수 사용 가능
    ...
}
// 변수 a는 코드 블록이 끝나면 수명을 다함
```

### ThreadLocal을 이용한 변수

쓰레드 영역에 변수를 설정해 특정 쓰레드가 실행하는 모든 코드에서 해당 변수 사용 가능

<img width="514" alt="스크린샷 2022-03-28 오후 4 40 34" src="https://user-images.githubusercontent.com/69156709/160349838-f34b38a4-9357-462d-8ab0-d2f445b0f269.png">

쓰레드 1에서 실행할 경우 관련 값이 쓰레드 1에 저장  
(쓰레드 2에서 실행할 경우 쓰레드 2에 저장)

---

## ThreadLocal의 기본 사용법

### 사용 방법

1. ThreadLocal 객체를 생성한다.
2. ThreadLocal.set() 메서드를 이용해서 현재 쓰레드의 로컬 변수에 값을 저장한다.
3. ThreadLocal.get() 메서드를 이용해서 현재 쓰레드의 로컬 변수 값을 읽어온다.
4. ThreadLocal.remove() 메서드를 이용해서 현재 쓰레드의 로컬 변수 값을 삭제한다.

### 예시

ThreadLocal 타입의 static 필드를 갖는 클래스

```JAVA
public class Context {
    public static ThreadLocal<Date> local = new ThreadLocal<>();
}
```

Context 클래스를 사용해 쓰레드 로컬 변수를 설정, 사용하는 코드

```JAVA
class A {
    public void a() {
        Context.local.set(new Date());

        B b = new B();
        b.b();

        Context.local.remove();
    }
}

class B {
    public void b() {
        Date date = Context.local.get();

        C c = new C();
        c.c();
    }
}

class C {
    public void c() {
        Date date = Context.local.get();
    }
}
```

실행되는 순서

    1. A.a() 실행
    2. A.a() 메서드에서 현재 쓰레드 로컬 변수에 Date 객체 저장

    3. B.b() 실행
    4. B.b() 메서드에서 현재 쓰레드의 로컬 변수에 저장된 Date 객체를 읽어와 사용

    5. C.c() 실행
    6. C.c() 메서드에서 현재 쓰레드의 로컬 변수에 저장된 Date 객체를 읽어와 사용

    7. A.a() 메서드에서 현재 쓰레드의 로컬 변수 삭제

---

### ThreadLocal의 활용

＞ 쓰레드와 관련된 코드에서 파라미터를 사용하지 않고 객체를 전파하기 위해 사용  
한 쓰레드에서 실행되는 코드가 동일한 객체를 사용할 수 있음

- 사용자 인증정보 전파 - Spring Security에서는 ThreadLocal을 이용해서 사용자 인증 정보를 전파
- 트랜잭션 컨텍스트 전파 - 트랜잭션 매니저는 트랜잭션 컨텍스트를 전파하는 데 ThreadLocal을 사용
- 쓰레드에 안전해야 하는 데이터 보관

### ThreadLocal 사용시 주의 사항

＞ 쓰레드 풀 환경에서 ThreadLocal을 사용하는 경우 변수 사용이 끝나면 반드시 삭제 필요  
재사용되는 쓰레드가 올바르지 않은 데이터를 참조할 수 있음
