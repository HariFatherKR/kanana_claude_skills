---
name: kanana
description: 카나나 앰배서더 SNS 허브(kanana.it.com)에 대한 RAG 기반 지식을 제공합니다. 사이트 구조, API, 앰배서더 데이터, UI 컴포넌트 관련 질문에 사용하세요.
---

# 카나나 앰배서더 SNS 허브 도우미

카나나(kanana.it.com) 플랫폼의 구조, API, 데이터 모델, UI 컴포넌트, 앰배서더 정보를 RAG 레퍼런스 기반으로 제공합니다.

## 허용 도구 (Read-Only)

이 스킬은 **정보 조회 전용**입니다. 다음 도구만 사용할 수 있습니다:

- **Read** - 레퍼런스 문서 읽기
- **Glob** - 레퍼런스 파일 검색
- **Grep** - 레퍼런스 내 키워드 검색
- **WebFetch** - 앰배서더 실시간 데이터 API 호출
- **mcp__claude-in-chrome__*** - 브라우저를 통한 사이트 데이터 조회 (API 폴백)

**금지 도구**: Edit, Write, Bash, NotebookEdit 등 파일 수정/생성/실행 도구는 사용하지 않습니다.

## 요청 분류

사용자 요청을 분석하여 해당하는 레퍼런스 문서를 참조합니다:

| 키워드 | 참조 방식 | 설명 |
|--------|----------|------|
| 사이트, 플랫폼, 개요, 구조 | [references/site-overview.md](references/site-overview.md) | 사이트 전체 구조 및 기능 |
| API, 엔드포인트, CRUD, REST | [references/api-reference.md](references/api-reference.md) | REST API 명세 |
| 데이터, 모델, 스키마, 필드 | [references/data-model.md](references/data-model.md) | 데이터 모델 및 스키마 |
| UI, 컴포넌트, 카드, 모달, CSS | [references/ui-components.md](references/ui-components.md) | UI 컴포넌트 및 스타일 |
| 앰배서더, 멤버, 프로필 | **실시간 API 호출** | 최신 앰배서더 데이터 (아래 참조) |

## 앰배서더 데이터 조회 (실시간)

앰배서더 데이터는 수시로 추가/수정/삭제되므로 **정적 파일이 아닌 실시간으로 조회**합니다.

### 조회 방법

앰배서더 관련 질문을 받으면 다음 순서로 최신 데이터를 가져옵니다:

**방법 1: API 호출 (우선)**
```
WebFetch로 https://kanana.it.com/api/ambassadors 호출
→ JSON 배열로 전체 앰배서더 목록 반환
```

**방법 2: 웹 페이지 크롤링 (API 실패 시 폴백)**
```
WebFetch로 https://kanana.it.com/ 페이지 내용 가져오기
→ 또는 브라우저 MCP 도구(mcp__claude-in-chrome__*)로 직접 접속하여 데이터 추출
```

### 응답 데이터 구조
```json
{
  "id": "string",
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

### 역할 분류
| role 값 | 한글 라벨 |
|---------|----------|
| `expert` | AI 전문가 |
| `student` | 대학생 |
| `creator` | 크리에이터 |

## 작업 흐름

1. 사용자 질문에 해당하는 영역 판별
2. 사이트/API/데이터모델/UI → 해당 reference 문서 읽기
3. 앰배서더 관련 → 실시간 API 호출로 최신 데이터 조회
4. 레퍼런스 + 실시간 데이터 기반으로 정확한 답변 제공

## 활용 예시

### 사이트 정보 질문
"카나나 사이트가 뭐야?" → `references/site-overview.md` 참조

### API 연동 개발
"앰배서더 목록 API 어떻게 호출해?" → `references/api-reference.md` 참조

### 앰배서더 조회 (실시간)
"AI 전문가 앰배서더 누가 있어?" → API 호출 후 role=expert 필터링

### 앰배서더 통계 (실시간)
"앰배서더 역할 분포가 어떻게 돼?" → API 호출 후 역할별 집계

### UI 커스터마이징
"카드 컴포넌트 구조 알려줘" → `references/ui-components.md` 참조
