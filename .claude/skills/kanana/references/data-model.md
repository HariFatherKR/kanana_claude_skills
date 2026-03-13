# 카나나 앰배서더 SNS 허브 - 데이터 모델

## Ambassador 스키마

```typescript
interface Ambassador {
  id: string;            // 고유 식별자
  name: string;          // 이름
  role: Role;            // 역할 분류
  bio: string;           // 한 줄 소개
  instagram: string;     // Instagram URL
  linkedin: string;      // LinkedIn URL
  velog: string;         // Velog URL
  tistory: string;       // Tistory URL
  xUrl: string;          // X (Twitter) URL
  threads: string;       // Threads URL
  facebook: string;      // Facebook URL
  youtube: string;       // YouTube URL
  github: string;        // GitHub URL
}
```

## 필드 목록

앱 내부에서 관리하는 필드 배열:
```javascript
const fields = [
  'ambassadorId', 'name', 'role', 'bio',
  'instagram', 'linkedin', 'velog', 'tistory',
  'xUrl', 'threads', 'facebook', 'youtube', 'github'
];
```

## Role (역할) 열거형

```typescript
type Role = 'expert' | 'student' | 'creator';
```

### 역할 메타데이터
```javascript
const roleMeta = {
  expert:  ['AI 전문가', 'expert'],
  student: ['대학생', 'student'],
  creator: ['크리에이터', 'creator']
};
```

| 값 | 한글 라벨 | 설명 |
|----|----------|------|
| `expert` | AI 전문가 | AI/기술 분야 전문가 |
| `student` | 대학생 | 대학생 앰배서더 |
| `creator` | 크리에이터 | 콘텐츠 크리에이터 |

## SNS 플랫폼 필드 상세

| 필드명 | 플랫폼 | URL 형식 | 비고 |
|--------|--------|----------|------|
| `instagram` | Instagram | `https://www.instagram.com/{username}` | |
| `linkedin` | LinkedIn | `https://www.linkedin.com/in/{username}` | |
| `velog` | Velog | `https://velog.io/@{username}` | 개인 블로그 URL도 허용 |
| `tistory` | Tistory | `https://{username}.tistory.com/` | |
| `xUrl` | X (Twitter) | `https://x.com/{username}` | 필드명 주의: `xUrl` |
| `threads` | Threads | `https://www.threads.com/@{username}` | |
| `facebook` | Facebook | `https://www.facebook.com/{username}` | |
| `youtube` | YouTube | `https://www.youtube.com/@{username}` | 채널 URL도 허용 |
| `github` | GitHub | `https://github.com/{username}` | |

## 유효성 규칙

1. **이름**: 필수, 빈 문자열 불가
2. **역할**: 필수, `expert` / `student` / `creator` 중 하나
3. **소개**: 선택, 38자 초과 시 UI에서 말줄임 처리
4. **SNS URL**: 선택, 입력 시 반드시 `https://`로 시작해야 함
