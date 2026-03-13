# 카나나 앰배서더 SNS 허브 - 사이트 개요

## 기본 정보

- **사이트명**: 카나나 앰배서더 SNS 허브
- **URL**: https://kanana.it.com/
- **브랜드**: KAKAO AMBASSADOR
- **언어**: 한국어 (ko)
- **호스팅**: Cloudflare (beacon.min.js 포함)

## 사이트 목적

카카오 앰배서더 프로그램의 멤버들이 자신의 프로필과 SNS 채널을 등록하고 공유할 수 있는 허브 플랫폼입니다. "빠르게 등록하고 바로 공유"라는 슬로건으로 운영됩니다.

## 기술 스택

- **프론트엔드**: Vanilla JavaScript (프레임워크 없음)
- **스타일**: 순수 CSS (CSS Variables 활용)
- **백엔드**: Spring Boot (REST API)
- **배포**: Cloudflare
- **파일 구조**:
  - `app.js` - 메인 애플리케이션 로직
  - `styles.css` - 스타일시트
  - 버전 관리: `?v=20260313d` 쿼리 파라미터

## 핵심 기능

### 1. 앰배서더 프로필 관리
- 이름, 역할, 한 줄 소개 등록
- 9가지 SNS 플랫폼 링크 연결
- CRUD (생성/조회/수정/삭제) 지원

### 2. 역할 기반 분류
- **AI 전문가** (expert): AI/기술 분야 전문가
- **대학생** (student): 대학생 앰배서더
- **크리에이터** (creator): 콘텐츠 크리에이터

### 3. 검색 및 필터링
- 역할별 탭 필터 (전체 / AI 전문가 / 대학생 / 크리에이터)
- 이름 및 소개글 기반 실시간 검색

### 4. 반응형 디자인
- 데스크톱: 4열 카드 그리드
- 태블릿 (768px 이하): 1열 레이아웃
- 모바일 (420px 이하): 필터 2열 그리드

## 지원 SNS 플랫폼

| 순서 | 플랫폼 | 필드명 |
|------|--------|--------|
| 1 | Instagram | instagram |
| 2 | LinkedIn | linkedin |
| 3 | Velog | velog |
| 4 | Tistory | tistory |
| 5 | X (Twitter) | xUrl |
| 6 | Threads | threads |
| 7 | Facebook | facebook |
| 8 | YouTube | youtube |
| 9 | GitHub | github |

## 현재 상태

- 데모 모드로 운영 중 (Spring Boot 서버 미연결 시 샘플 데이터 표시)
- 등록된 앰배서더: 14명 (2026년 3월 기준)
- API 불가 시 빈 배열로 폴백 처리
