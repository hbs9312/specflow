# specflow

에이전트 기반 개발 명세서 생성 · 검증 · 수정 · 구현 계획 워크플로우

## 설치

```bash
claude --plugin-dir /path/to/specflow
# 또는 마켓플레이스에서:
# /plugin marketplace add soymedia/specflow
# /plugin install specflow@soymedia-specflow
```

## 초기화

```bash
bash /path/to/specflow/scripts/init-project.sh
```

## 사전 조건 (선택)

P5(도구 동기화) 스킬을 사용하려면 MCP 서버 연결이 필요합니다:

| 도구 | 환경 변수 | 발급 위치 |
|------|----------|----------|
| Linear | `LINEAR_API_KEY` | Linear 설정 > API > Personal API Keys |
| Notion | `NOTION_API_KEY` | notion.so/my-integrations |

MCP 없이도 P1~P4(태스크 분해~스프린트 배치)는 정상 동작합니다.
P5만 MCP가 필요하며, MCP 없이 실행 시 sync_plan을 파일로 출력합니다.

## 커맨드

### 전체 워크플로우
```
/specflow:orchestrate [PRD 경로]
```

### G — 생성
| 커맨드 | 설명 |
|--------|------|
| `/specflow:generate-fs` | 기능 명세서 |
| `/specflow:generate-wf` | 와이어프레임 |
| `/specflow:generate-ts` | 기술 명세서 |
| `/specflow:extract-ui` | 화면설계서 |
| `/specflow:generate-qa` | 테스트 명세서 |

### V — 검증 (격리 세션)
| 커맨드 | 설명 |
|--------|------|
| `/specflow:validate` | 단일 문서 품질 |
| `/specflow:validate-cross` | 교차 일관성 |
| `/specflow:validate-boundary` | 경계 침범 |

### R — 수정
| 커맨드 | 설명 |
|--------|------|
| `/specflow:patch` | 부분 수정 |
| `/specflow:regenerate` | 구조적 재생성 |

### P — 구현 계획
| 커맨드 | 설명 |
|--------|------|
| `/specflow:decompose` | 태스크 분해 |
| `/specflow:analyze-deps` | 의존성 분석 |
| `/specflow:estimate` | 공수 추정 |
| `/specflow:plan-sprints` | 스프린트 배치 |
| `/specflow:sync-tools` | 도구 동기화 |

### U — 유틸리티
| 커맨드 | 설명 |
|--------|------|
| `/specflow:extract-refs` | 참조 ID 인덱스 |
| `/specflow:state-matrix` | 상태 매트릭스 |
| `/specflow:change-impact` | 변경 영향 분석 |

## 아키텍처

```
오케스트레이터
  ├── G (생성) — "무엇을 만들 것인가"
  ├── V (검증) — "기준에 맞는가" (격리 세션)
  ├── R (수정) — "어떻게 고칠 것인가"
  ├── P (계획) — "어떤 순서로, 누가, 언제"
  └── U (유틸) — 참조 추출, 상태 매트릭스, 영향 분석
```

## 라이선스
MIT
