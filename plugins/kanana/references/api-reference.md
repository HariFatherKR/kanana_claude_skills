# 카나나 앰배서더 SNS 허브 - API 레퍼런스

## Base URL

```
https://kanana.it.com/api/ambassadors
```

## 엔드포인트

### 1. 전체 앰배서더 목록 조회

```http
GET /api/ambassadors
```

**응답 예시:**
```json
[
  {
    "id": "string",
    "name": "장진형",
    "role": "expert",
    "bio": "백엔드 개발과 AI AGENT에 관심이 많은 대학생입니다",
    "instagram": "https://www.instagram.com/jjh020426/",
    "linkedin": "https://www.linkedin.com/in/...",
    "velog": "",
    "tistory": "https://coldmans.tistory.com/",
    "xUrl": "",
    "threads": "",
    "facebook": "",
    "youtube": "",
    "github": "https://github.com/coldmans"
  }
]
```

### 2. 새 앰배서더 생성

```http
POST /api/ambassadors
Content-Type: application/json
```

**요청 본문:**
```json
{
  "name": "이름",
  "role": "expert|student|creator",
  "bio": "한 줄 소개",
  "instagram": "https://...",
  "linkedin": "https://...",
  "velog": "https://...",
  "tistory": "https://...",
  "xUrl": "https://...",
  "threads": "https://...",
  "facebook": "https://...",
  "youtube": "https://...",
  "github": "https://..."
}
```

### 3. 앰배서더 정보 수정

```http
PUT /api/ambassadors/{id}
Content-Type: application/json
```

요청 본문은 POST와 동일합니다.

### 4. 앰배서더 삭제

```http
DELETE /api/ambassadors/{id}
```

## 유효성 검증 규칙

### URL 검증
모든 SNS 링크는 HTTPS 프로토콜로 시작해야 합니다:
```javascript
function isValidHttpsUrl(url) {
  return /^https:\/\//i.test(String(url).trim());
}
```

### 필수 필드
- `name`: 이름 (필수)
- `role`: 역할 (필수, expert/student/creator 중 하나)
- `bio`: 한 줄 소개

### 선택 필드
- 모든 SNS 링크 필드는 선택사항
- 빈 문자열 허용

## 에러 처리

### API 서버 미연결 시
- 프론트엔드에서 빈 배열로 폴백
- 상태 메시지: "현재는 데모 모드입니다. Spring Boot 서버 실행 후 저장할 수 있어요."

### 네트워크 에러
```javascript
catch(e) {
  ambassadors = [];
  // 샘플 데이터로 폴백
}
```

## 프론트엔드 필터링

API 레벨이 아닌 클라이언트 사이드 필터링:
- **역할 필터**: `role` 필드 기반 (all / expert / student / creator)
- **검색**: `name`과 `bio` 필드에서 텍스트 매칭
