# save vs saveAll

## 궁금해진 이유

- JpaRepository를 상속받으면 기본적으로 save와 saveAll이 제공되던데, 어떤 차이가 있을까??

- 잘 사용하면 성능의 이점이 있지 않을까??

## 실험해보자!

### 100000개의 데이터를 저장할 때

- save
  ![스크린샷 2022-07-27 오후 1 33 27](https://user-images.githubusercontent.com/69156709/181170462-73368431-fe4e-448f-808e-aee589441a2e.png)

- saveAll
  ![스크린샷 2022-07-27 오후 1 33 40](https://user-images.githubusercontent.com/69156709/181170466-643fce86-1eef-4ce4-86f3-92cb55224944.png)

- 2배가 조금 안되게 saveAll이 빠르다!

### 1000개의 데이터를 저장할 때

- save
  ![스크린샷 2022-07-27 오후 1 34 39](https://user-images.githubusercontent.com/69156709/181170470-f24e3143-9c2d-44b2-a376-f40731100883.png)

- saveAll
  ![스크린샷 2022-07-27 오후 1 34 48](https://user-images.githubusercontent.com/69156709/181170473-20366adf-517f-45d7-b980-5cf2a02a8cfc.png)

- 근소한 차이로 saveAll이 빠르다!

### 100개의 데이터를 저장할 때

- save
  ![스크린샷 2022-07-27 오후 1 35 07](https://user-images.githubusercontent.com/69156709/181170476-5b07010a-4597-4f2d-a810-377202f563e4.png)

- saveAll
  ![스크린샷 2022-07-27 오후 1 35 22](https://user-images.githubusercontent.com/69156709/181170478-8a3b903c-8fa5-41f0-80a6-1025f2ec7c3d.png)

- 거의 비슷하지만 save가 조금 더 빠르다!

### 10개의 데이터를 저장할 때

- save
  ![스크린샷 2022-07-27 오후 1 36 01](https://user-images.githubusercontent.com/69156709/181170480-3f3743bf-a2ef-4714-8109-74c28eb626ca.png)
- saveAll
  ![스크린샷 2022-07-27 오후 1 36 10](https://user-images.githubusercontent.com/69156709/181170483-bc1dffab-24cf-46fc-ad63-bc465f88bd5c.png)

- 역시나 save가 조금 더 빠르다!

### 결론

- 데이터가 많은 경우 saveAll이 빠름

- 데이터가 적은 경우 List에 entity를 담는 시간 때문에 save가 빠른 듯(나의 추측)

- 무조건 100개 이하의 데이터가 들어간다고 가정하면 save를 사용해도 상관 없을 듯

- 확장성을 고려하면 데이터가 많아질 경우를 대비해 saveAll을 사용하는게 좋을 듯!

## 그래서 왜 데이터가 많을수록 saveAll이 빠른거지??

### 나의 추측

- JdbcTemplate에서 사용하던 batch와 같이 동작하지 않을까??

- save 메서드와 saveAll 메서드를 까보자!

    - save
      ![스크린샷 2022-07-27 오후 2 15 08](https://user-images.githubusercontent.com/69156709/181170485-05e78115-3135-4e62-a4f3-ebacd4809129.png)

    - saveAll
      ![스크린샷 2022-07-27 오후 2 15 25](https://user-images.githubusercontent.com/69156709/181170490-05f5b2ad-855c-43e0-8c17-8112efb17b4d.png)

    - 😮saveAll에서도 save 메서드를 n번 호출해 사용하고 있었다!!

### 검색 찬스

- @Transactional에 주목해봐야 함!

    - [ ] @Transactional은 뭐지..?

- save의 경우 저장하는 데이터의 수만큼 프록시 과정을 거치게 됨

    - 프록시가 뭐지..?

        - [ ] @Transactional과 프록시는 어떤 관계지?

- saveAll의 경우 save 호출시 단지 내부 메서드를 호출한 효과를 주게됨

    - 즉, saveAll의 save 호출은 save 메서드의 @Transactional 프록시를 동작하게 하지 않음

- 따라서 프록시 참조를 통한 호출이 아니게 됨!!

## 새로운 의문

### 정말 큰 데이터의 경우 batch를 사용해야 성능의 이점을 가질 수 있는건가?

- 실제로 로그를 살펴보면 saveAll은 하나씩 insert를 하고 있음

- 결국 DB에 데이터의 갯수만큼 접근하는 비용 문제는 해결하지 못한 것!

- [ ] JpaRepository에서 batch를 이용할 수 없을까?
