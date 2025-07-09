## 1. 소개 (Introduction)

### 1.1 목적 (Purpose)
이 문서는 **[프로젝트명]**의 소스 코드 작성 시 일관성과 가독성을 높이고, 유지보수성을 확보하기 위한 코드 작성 표준을 정의합니다.

### 1.2 적용 범위 (Scope)
프론트엔드, 백엔드, 공통 모듈(공유 라이브러리 및 타입 정의 등)의 모든 코드 작성에 적용됩니다.  
사용 언어: TypeScript, JavaScript, SQL, HTML, CSS 등

---

## 2. 공통 코딩 스타일 (General Coding Style)

### 2.1 들여쓰기 및 줄바꿈
- 스페이스 2칸 사용 (탭 금지)
- 최대 줄 길이: 100자
- 중괄호 `{}`는 같은 줄에서 열기

```ts
if (isActive) {
  run();
}
```

### 2.2 주석 규칙
- 함수/클래스에는 JSDoc 스타일 사용
```ts
/**
 * 유저 정보를 반환합니다.
 * @param userId 사용자 ID
 */
function getUser(userId: number): User {
  ...
}
```
- 코드 중간 설명은 간단한 한 줄 주석 `//` 사용

---

## 3. 네이밍 규칙 (Naming Conventions)

|항목|규칙|예시|
|---|---|---|
|변수|camelCase|`userList`, `isVisible`|
|상수|UPPER_SNAKE_CASE|`MAX_COUNT`, `DEFAULT_URL`|
|함수|camelCase|`getUserById()`|
|클래스|PascalCase|`UserService`|
|파일/폴더|kebab-case|`user-service.ts`|
|DB 테이블|snake_case(복수형)|`users`, `todo_items`|
|DB 컬럼|snake_case|`user_id`, `created_at`|

---

## 4. 디렉터리 및 파일 구조 (Project Structure)
```
src/
  ├── api/            # 외부 API 호출
  ├── components/     # UI 컴포넌트
  ├── controllers/    # 요청 처리
  ├── services/       # 비즈니스 로직
  ├── models/         # DB 모델
  ├── middlewares/    # 공통 미들웨어
  ├── utils/          # 유틸리티 함수
  └── types/          # 타입 정의
```

---

## 언어별 코드 스타일

### 5.1 TypeScript / JavaScript
- ESLint + Prettier 사용
- `any` 사용 지양
- `async/await` 사용
- 명확한 타입 선언 필수

### 5.2 SQL
- 키워드 대문자 (`SELECT`, `FROM`)
- 테이블/컬럼: 소문자 + 스네이크 케이스
```sql
SELECT user_id, created_at
FROM users
WHERE status = 'active';
```

---
### 5.3 HTML / CSS
- BEM 네이밍 규칙 사용 권장
- 시맨틱 태그 사용
- CSS 클래스는 kebab-case

---

## 6. Git 커밋 규칙 (Commit Convention)

### 6.1 형식 (Conventional Commits)
```
<type>(<scope>): <subject>
```
- `type`: feat, fix, docs, style, refactor, test, chore
- `scope`: 기능/모듈 단위 (`login`, `todo-api` 등)
- `subject`: 간결한 변경 내용 (영문 소문자, 마침표 생략)

### 6.2 예시
```
feat(user): 유저 로그인 기능 추가
fix(todo): 완료 체크 오류 수정
docs(readme): 실행 방법 추가
```

---

## 7. 코드 리뷰 가이드 (Code Review)
- PR은 작게 (200줄 이하 권장)
- 모든 변경사항은 설명 필수
- 리뷰어는 성능, 보안, 유지보수성 기준으로 확인
- 테스트 코드 포함 권장
- 병합 전 모든 CI 테스트 통과 필요

---

## 8. 도구 및 자동화 설정

|도구|역할|
|---|---|
|ESLint|문법 검사|
|Prettier|코드 포매팅|
|Husky|Git hook 적용|
|Commitlint|커밋 메시지 검사|
|Jest|단위 테스트 프레임워크|
|Swagger|API 문서화|

---

## 9. 부록 (Appendices)
- `.eslintrc.js` 예시
- `.prettierrc` 예시
- `.editorconfig` 예시
- `tsconfig.json` 기본 설정

---

## 📌 문서 정보
- 문서 버전: v0.1
- 작성일: YYYY-MM-DD
- 작성자: [이름 / 팀명]
- 검토자: [이름]