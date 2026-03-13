# Contributing to Kanana Skills

카나나 스킬에 기여해주셔서 감사합니다! 아래 가이드를 참고해주세요.

## 기여 방법

### 1. 이슈 등록

- 버그 리포트, 기능 요청, 개선 제안은 [GitHub Issues](https://github.com/HariFatherKR/kanana_claude_skills/issues)에 등록해주세요.
- 이슈 템플릿을 활용해주세요.

### 2. PR 제출

1. 레포지토리를 **포크**합니다.
2. 작업용 **브랜치**를 생성합니다.
   ```bash
   git checkout -b feature/새로운-기능
   ```
3. 변경 사항을 **커밋**합니다.
   ```bash
   git commit -m "feat: 새로운 기능 추가"
   ```
4. 포크한 레포에 **푸시**합니다.
   ```bash
   git push origin feature/새로운-기능
   ```
5. **Pull Request**를 생성합니다.

### 3. 기여 가능한 영역

| 영역 | 경로 | 설명 |
|------|------|------|
| 레퍼런스 문서 | `plugins/kanana/references/` | 사이트 구조, API, 데이터 모델, UI 문서 개선 |
| 스킬 로직 | `plugins/kanana/skills/` | 기존 스킬 개선 또는 새 스킬 추가 |
| 플러그인 설정 | `.claude-plugin/` | 마켓플레이스 메타데이터 |
| 문서 | `README.md`, `CONTRIBUTING.md` | 문서 개선 |

## 커밋 컨벤션

[Conventional Commits](https://www.conventionalcommits.org/)를 따릅니다:

- `feat:` 새로운 기능
- `fix:` 버그 수정
- `docs:` 문서 변경
- `refactor:` 리팩토링
- `chore:` 기타 변경

## 코드 리뷰

- 모든 PR은 리뷰 후 머지됩니다.
- 레퍼런스 문서 변경 시, 실제 kanana.it.com 데이터와 일치하는지 확인해주세요.

## 라이선스

기여하신 코드는 [MIT License](LICENSE)로 배포됩니다.
