# commit message 작성 규칙

### ❓ 규칙이 필요한 이유

- 더 좋은 커밋 로그 가독성

- 더 나은 협업과 리뷰 프로세스

- 더 쉬운 코드 유지보수

### ❗️ 7가지 규칙

- 제목과 본문을 `빈 행`으로 구분

- `제목`을 `50글자` 내로 제한

- 제목 `첫 글자는 대문자`로 작성

- 제목 끝에 `.` 금지

- 제목은 `명령문`으로 사용하며 과거형 사용하지 않기

- `본문의 각 행`은 `72글자` 내로 제한

- 어떻게 보다는 `무엇`과 `왜`를 설명

### 🛠 구조

```
type(타입) : title(제목)

body(본문, 생략 가능)

Resolves : #issue, ...(해결한 이슈, 생략 가능)

See also : #issue, ...(참고 이슈, 생략 가능)
```

### 💡 유형 지정

- **FEAT** : 새로운 `기능` 추가

- **FIX** : `버그` 수정

- **DOCS** : `문서` 수정

- **STYLE** : `스타일` 관련 기능 (코드 포맷팅, 세미콜론 누락, 코드 자체의 변경이 없는 경우)

- **REFACTOR** : 코드 `리펙터링`

- **TEST** : `테스트 코드, 리펙토링 테스트 코드` 추가

- **CHORE** : `빌드` 업무 수정, `패키지 매니저` 수정 (ex.gitignore 수정 같은 경우)
