# Kanana Skills

[English](#english) | **한국어**

Kanana Skills는 카나나 앰배서더 SNS 허브(kanana.it.com)의 데이터를 Claude Code에서 RAG 기반으로 활용할 수 있도록 도와주는 플러그인 마켓플레이스입니다.

## How it works

카나나 관련 질문을 하면, 스킬이 자동으로 활성화됩니다. "카나나 사이트 구조 알려줘", "앰배서더 목록 보여줘", "API 명세 확인해줘" 같은 요청을 하면 스킬이 해당 레퍼런스 문서를 참조하여 정확한 답변을 제공합니다.

사이트 구조, REST API 명세, 데이터 모델, UI 컴포넌트는 레퍼런스 문서로 제공되며, 앰배서더 데이터는 실시간 API 호출로 최신 정보를 가져옵니다.

> **Read-Only 스킬**: 이 스킬은 정보 조회 전용입니다. 파일 생성/수정/삭제를 수행하지 않습니다.

## Installation

### Claude Code (via Plugin Marketplace)

Claude Code에서 마켓플레이스를 먼저 등록합니다:

```bash
/plugin marketplace add HariFatherKR/kanana_claude_skills
```

그 다음 플러그인을 설치합니다:

```bash
/plugin install kanana@kanana-plugins
```

### Verify Installation

설치 확인:

```bash
/help
```

```
# Should see:
# /kanana - 카나나 앰배서더 SNS 허브 도우미
```

## The Basic Workflow

1. **요청 분류** - 사용자 요청을 분석하여 사이트 구조, API, 데이터 모델, UI 중 해당 영역 파악

2. **레퍼런스 참조** - 해당 영역의 상세 문서를 읽고 정확한 정보 제공

3. **앰배서더 데이터** - 실시간 API 호출(`GET /api/ambassadors`)로 최신 데이터 조회

**스킬이 자동으로 적절한 레퍼런스를 선택합니다.** 그냥 원하는 것을 질문하면 됩니다.

## What's Inside

### 레퍼런스 문서 (정적)

| 문서 | 설명 | 예시 질문 |
|------|------|----------|
| **site-overview.md** | 사이트 전체 구조, 기능, 기술 스택 | "카나나가 뭐야?" |
| **api-reference.md** | REST API 엔드포인트 명세 | "앰배서더 API 호출 방법?" |
| **data-model.md** | 데이터 모델, 스키마, 필드 정의 | "앰배서더 데이터 구조?" |
| **ui-components.md** | UI 컴포넌트, CSS 디자인 시스템 | "카드 레이아웃 구조?" |

### 실시간 데이터

| 데이터 | 조회 방식 | 예시 질문 |
|--------|----------|----------|
| 앰배서더 목록 | `GET /api/ambassadors` 실시간 호출 | "AI 전문가 누구야?" |

### 크롤링 데이터 요약

- **사이트**: 카카오 앰배서더 SNS 허브
- **기술 스택**: Vanilla JS + CSS + Spring Boot REST API
- **지원 SNS**: Instagram, LinkedIn, Velog, Tistory, X, Threads, Facebook, YouTube, GitHub

## Philosophy

- **RAG 기반** - 크롤링한 실제 데이터를 레퍼런스로 활용하여 정확한 답변
- **Read-Only** - 정보 조회 전용, 파일 수정 없음
- **실시간** - 앰배서더 데이터는 API로 항상 최신 상태 유지
- **확장성** - 새 레퍼런스 문서 추가로 지식 확장 가능

## Updating

플러그인 업데이트:

```bash
/plugin update kanana@kanana-plugins
```

마켓플레이스 업데이트:

```bash
/plugin marketplace update kanana-plugins
```

## Contributing

1. 레포지토리 포크
2. 브랜치 생성
3. 레퍼런스 문서 개선 또는 새 데이터 추가
4. PR 제출

## License

MIT License

## Support

- **Issues**: https://github.com/HariFatherKR/kanana_claude_skills/issues
- **카나나 사이트**: https://kanana.it.com/
