---
name: sync-tools
description: 구현 계획을 Linear, Notion 등에 동기화합니다. "도구 동기화" 요청 시 사용.
argument-hint: [스프린트 배치 파일 경로]
disable-model-invocation: true
allowed-tools: Read Grep Glob Write
model: claude-opus-4-6
effort: high
---

# 프로젝트 도구 동기화 (P5)

## 입력: P4 스프린트 배치 (승인 완료)

## ★ 사전 확인 필수 ★
1. sync_plan 출력 (dry-run) → 생성할 이슈 목록 표시
2. 사용자 확인 → "{N}건 생성합니다. 진행?" 
3. 확인 후 실행

## 도구별 매핑
- Linear: task→Issue, sprint→Cycle, milestone→Project
- Notion: 전체 계획→페이지, task→DB 항목

## 저장: specs/PLAN-{YYYY}-{NNN}-sync.md
