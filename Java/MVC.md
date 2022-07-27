# MVC 패턴 (Model-View-Controller)

## MVC는 왜 생겨난걸까?

### ❓ MVC가 생겨나기 전

    코드가 많아지면 많아질수록 코드 파악하기 힘듦
    기능 수정할때마다 대부분의 코드 갈아 엎어야 함

    = 유지보수가 불편함

### 💡 MVC가 생겨난 과정

    '이렇게 코드를 구성하니 유지보수가 편하더라' 하는 패턴의 규칙성이 보이기 시작
    그 패턴을 하나의 공식처럼 만들어 논문으로 발표

    -> 프로그래머들 사이에서 MVC가 유명해짐

    즉, MVC는 유지보수가 편해지는 코드 구성 방식 즉, 디자인 패턴 중 하나임

### 디자인 패턴

    유지보수 쉽고 편리하게 만들어주는 디자인패턴에는 어떤 것이 더 있을까?

<hr>

## MVC 맛보기

1. `User` -> `Controller(구글)`에 '코딩' 검색

2. `Controller` : '코딩'에 대한 검색 결과 데이터를 `Model`에게 요청

3. `Model` : 검색 결과 데이터를 `Controller`에게 전달

4. `Controller` : `View`에게 받은 검색 결과 데이터를 전달

5. `View` : `User`가 노는 UI(레이아웃)에 검색 결과 데이터를 넣어 보여줌

### Model

    데이터와 관련된 부분

### View

    사용자한테 보여지는 부분

### Controller

    Model과 View를 이어주는 부분

<hr>

## MVC를 지키면서 코딩하는 방법

### 1. Model은 Controller와 View에 의존하지 않아야 함

    Model 내부에 Controller와 View에 관련된 코드가 있으면 안됨

### 2. View는 Model에만 의존해야 하고, Controller에는 의존하면 안됨

    View 내부에 Model의 코드만 있을 수 있음
    Controller의 코드가 있으면 안됨

### 3. View가 Model로부터 데이터를 받을 때는, 사용자마다 다르게 보여주어야 하는 데이터에 대해서만 받아야 함

    View = UI(레이아웃) + Model로부터 받은 데이터

    UI(레이아웃) : 사용자에게 공통적으로 보여주어야 함
    즉, UI(레이아웃)은 View가 자체적으로 가지고 있어야 하는 정보

### 4. Controller는 Model과 View에 의존해도 됨

    Controller 내부에는 Model과 View의 코드가 있을 수 있음

### 5. View가 Model로부터 데이터를 받을 때, 반드시 Controller에서 받아야 함
