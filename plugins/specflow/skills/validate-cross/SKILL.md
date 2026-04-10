---
name: validate-cross
description: 두 개 이상의 명세서 간 교차 일관성을 검증합니다. "교차 검증", "문서 간 일관성" 요청 시 사용.
argument-hint: [문서1 경로] [문서2 경로] [...추가]
disable-model-invocation: true
context: fork
allowed-tools: Read Grep Glob Write
model: claude-opus-4-6
effort: max
---

# 교차 일관성 검증 (V2)

ultrathink

독립적인 교차 검증자입니다. `context: fork` 격리 실행.

## 컨텍스트: [conventions.md](../../context/conventions.md)

## 입력: $ARGUMENTS 의 모든 문서를 Read. ID 접두사로 쌍 판별 후 규칙 로드:

- FS + TS → [fs-ts-rules.md](rules/fs-ts-rules.md)
- FS + WF → [fs-wf-rules.md](rules/fs-wf-rules.md)
- WF + UI → [wf-ui-rules.md](rules/wf-ui-rules.md)
- 3개 이상 + QA → [all-qa-rules.md](rules/all-qa-rules.md)

## 출력

```yaml
검증 유형: V2 (교차 일관성)
findings:
  - id: "V2-001"
    severity: critical
    source_a: "{문서ID} > {위치}"
    source_b: "{문서ID} > {위치}"
    issue: "{불일치}"
    suggestion: "{수정 제안 — 어느 문서를 고칠지 명시}"
```

## 수정 방향: 상위 문서 우선, Approved > Draft, 원본 > 파생

## 저장: specs/reviews/CROSS-{ID1}-{ID2}-{timestamp}.md
