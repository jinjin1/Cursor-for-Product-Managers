# 개선 계획서

**작성일:** 2026-03-06
**기반:** TEST-REPORT.md (37개 문제점 분석 결과)
**참고:** `process-task-list` 스킬은 Cursor 등 에이전트가 독자적으로 태스크 실행을 잘 수행하므로 삭제 대상

---

## Phase 1: 스킬 삭제 및 정리

### 1-1. `process-task-list` 스킬 삭제

**대상 파일:**
- `.cursor/skills/process-task-list/SKILL.md` → 삭제

**연쇄 수정:**
- `.cursor-plugin/plugin.json` → skills 설명에서 `process-task-list` 관련 문구 제거
- `initiatives/_templates/initiative-template/README.md` → `/process-task-list` 참조 제거
- `.cursor/skills/setup-initiative/SKILL.md` (Line 80) → Integration Points에서 `/process-task-list` 항목 제거
- `README.md` → `process-task-list` 관련 설명 제거

---

## Phase 2: Critical 문제 수정

### 2-1. `disable-model-invocation` 플래그 제거

**문제:** `setup-initiative`와 `generate-figma-prompt`에 `disable-model-invocation: true`가 설정되어 있어 `initiative-planner` 에이전트에서 호출 시 충돌

**수정 파일:**
- `.cursor/skills/setup-initiative/SKILL.md` → frontmatter에서 `disable-model-invocation: true` 줄 삭제
- `.cursor/skills/generate-figma-prompt/SKILL.md` → frontmatter에서 `disable-model-invocation: true` 줄 삭제

---

### 2-2. `synthesize-snapshots` 파일 네이밍 모순 해결

**문제:** Line 70 "initiative folder name" vs Line 80 "extracted topic" 둘 다 "primary identifier"로 지정

**방침:** initiative folder name으로 통일 (더 결정적이고 일관적)

**수정 파일:** `.cursor/skills/synthesize-snapshots/SKILL.md`

**수정 내용:**
- Line 80 `"Use extracted topic instead of initiative name as primary identifier"` → 삭제
- Line 82 `"No content analysis needed for topic extraction"` → 삭제
- "Initiative Name Process" 섹션 (Line 77-82)을 다음과 같이 단순화:
  ```
  **Initiative Name Process:**
  1. Use current initiative folder name as primary identifier
  2. Ensure initiative name is kebab-case format (e.g., "live-sports-vod-conversion")
  3. Maintain consistency across all synthesis files for same initiative
  ```

---

### 2-3. 버전 연결 관계 정의

**문제:** 기회/솔루션/가정 간 버전이 독립적이라 추적 불가

**수정 파일:**
- `.cursor/skills/create-opportunities/SKILL.md`
- `.cursor/skills/generate-solutions/SKILL.md`
- `.cursor/skills/identify-test-assumptions/SKILL.md`

**수정 내용:** 각 스킬의 Output 섹션에 "Source Reference" 필드 추가

```markdown
**Source Reference (MANDATORY):**
- 문서 상단에 원본 참조를 기록
- 형식: `**Based on:** [원본 파일명]`
- 예: `**Based on:** opportunities-user-onboarding-v2.md`
- 원본이 업데이트되면 새 버전 생성 시 updated source reference 기록
```

이를 통해 `solutions-user-onboarding-v1.md`가 어떤 버전의 기회 문서에 기반하는지 추적 가능.

---

### 2-4. 토픽 추출 규칙 명시

**문제:** `create-opportunities`와 `generate-solutions`의 토픽 추출이 비결정적

**수정 파일:**
- `.cursor/skills/create-opportunities/SKILL.md`
- `.cursor/skills/generate-solutions/SKILL.md`
- `.cursor/skills/identify-test-assumptions/SKILL.md`

**수정 내용:** 각 스킬의 Semantic Naming 섹션에 토픽 추출 규칙 추가

```markdown
**Topic Extraction Rules:**
1. Initiative 폴더 내에서 실행 시: initiative 폴더명을 토픽으로 사용
2. 독립 실행 시: 사용자에게 토픽명을 명시적으로 요청
3. 자동 추출 금지 - 토픽명은 항상 명시적으로 결정되어야 함
4. 형식: kebab-case (예: user-onboarding, checkout-optimization)
```

---

### 2-5. `calculate-ice-score` 기본값 경고 추가

**문제:** 데이터 없이 Impact 2를 경고 없이 자동 적용

**수정 파일:** `.cursor/skills/calculate-ice-score/SKILL.md`

**수정 내용:** 기본값 적용 섹션을 다음으로 교체

```markdown
**Missing Data Handling:**
- Impact 데이터가 없을 경우: 사용자에게 추정치를 요청
- 사용자가 추정 불가할 경우: Impact 2 (기본 +1.5%) 적용 + 문서에 경고 표시
- 경고 형식: `⚠️ DEFAULT VALUE APPLIED: Impact score uses assumed +1.5% improvement due to missing data`
- ICE 결과 해석 섹션에도 기본값 사용 사실 명시
```

---

### 2-6. `generate-solutions` Step 2 강제 강화

**문제:** Step 2 (사용자 아이디어 제출) 강제가 텍스트 지시사항으로만 존재

**수정 파일:**
- `.cursor/skills/generate-solutions/SKILL.md`
- `.cursor/agents/discovery-researcher.md`

**수정 내용:**

`generate-solutions/SKILL.md`의 Step 2 섹션 강화:
```markdown
**MANDATORY PROCESS ENFORCEMENT:**
- Step 2 완료 여부 확인: 사용자가 최소 3개 아이디어를 제시했는지 확인
- 미완료 시 응답 형식:
  "솔루션 생성을 위해 먼저 개인 아이디어가 필요합니다.
   이 기회에 대해 떠오르는 아이디어를 최소 3개 공유해 주세요.
   (권장: 10-15개, 빠른 반복: 3-5개)"
- AI가 먼저 아이디어를 제시하는 것은 금지
```

`discovery-researcher.md`의 Step 4에 명시적 추가:
```markdown
- CRITICAL: /generate-solutions 실행 전 사용자에게 개인 아이디어(최소 3개) 제출을 요청
- 사용자 아이디어 없이 솔루션 생성 단계로 진행하지 않음
```

---

## Phase 3: High 문제 수정

### 3-1. 에이전트 간 핸드오프 프로토콜 추가

**수정 파일:**
- `.cursor/agents/discovery-researcher.md`
- `.cursor/agents/initiative-planner.md`

**수정 내용:**

`discovery-researcher.md` 끝에 핸드오프 섹션 추가:
```markdown
## Handoff to Initiative Planning

디스커버리 완료 후:
1. 생성된 산출물 목록 제시 (snapshots, synthesis, opportunities, solutions, assumptions)
2. 사용자에게 Initiative Planning 진행 여부 확인
3. 진행 시: "이니셔티브 기획을 시작하려면 /initiative-planner를 사용하세요" 안내
4. 핵심 컨텍스트 전달: 최우선 기회, 선정된 솔루션 Top 3, 검증이 필요한 가정
```

`initiative-planner.md` 시작 부분에 컨텍스트 수집 단계 추가:
```markdown
### Phase 0: Context Collection
- 기존 디스커버리 결과물 확인 (initiatives/[name]/ 내 파일 스캔)
- 기회, 솔루션, 가정 문서가 있으면 이를 기반으로 기획 진행
- 없으면 Phase 1부터 새로 시작
```

---

### 3-2. `company-level-context/` 빈 디렉토리 폴백 추가

**수정 파일:** `.cursor/skills/create-opportunities/SKILL.md`

**수정 내용:** "0.5) Context Source Analysis" 섹션에 폴백 로직 추가

```markdown
**Empty Directory Handling:**
- `company-level-context/` 내 실제 문서가 없을 경우 (.gitkeep만 존재):
  1. 사용자에게 알림: "전략 문서가 아직 등록되지 않았습니다"
  2. 사용자에게 간략한 전략 컨텍스트를 구두로 요청 (회사 비전, 현재 OKR, 핵심 제약사항)
  3. 구두 입력을 기반으로 전략적 정렬 평가 진행
  4. 결과물에 "전략 문서 미등록 상태에서 작성됨" 표시
```

---

### 3-3. 파일 네이밍 컨벤션 통일

**문제:** 스킬마다 식별자, 날짜, 버전 관리 기준이 다름

**수정 파일:** 아래 5개 스킬의 Output 섹션

**통일 규칙:**
```
[document-type]-[initiative-name]-v[version].md
```

| 스킬 | 현재 | 변경 후 |
|------|------|---------|
| create-interview-snapshots | `snapshot-[name]-[date].md` | `snapshot-[initiative]-[name]-[YYYYMMDD].md` (유지하되 날짜 형식 명시) |
| synthesize-snapshots | `synthesis-[initiative]-v[N].md` | 유지 (이미 올바름) |
| create-opportunities | `opportunities-[topic]-v[N].md` | `opportunities-[initiative]-v[N].md` |
| generate-solutions | `solutions-[topic]-v[N].md` | `solutions-[initiative]-v[N].md` |
| identify-test-assumptions | `assumptions-[opportunity]-v[N].md` | `assumptions-[initiative]-v[N].md` |
| calculate-ice-score | `ice-[date]-[title].md` | `ice-[initiative]-[YYYYMMDD].md` |
| create-prd | `prd-[feature].md` | `prd-[initiative]-v[N].md` (버전 관리 추가) |
| create-one-pager | `1-pager-[initiative].md` | `1-pager-[initiative]-v[N].md` (버전 관리 추가) |
| create-design-brief | `design-brief-[feature].[ext]` | `design-brief-[initiative]-v[N].[ext]` (버전 관리 추가) |

**핵심 원칙:**
- 식별자는 항상 initiative 폴더명 사용
- 날짜가 필요한 경우 YYYYMMDD 형식
- 반복 가능한 문서는 모두 버전 관리 적용

---

### 3-4. `create-design-brief`의 디자인 시스템 참조 수정

**수정 파일:** `.cursor/skills/create-design-brief/SKILL.md`

**수정 내용:** 존재하지 않는 경로 참조를 조건부로 변경

```markdown
**Design System Reference (Optional):**
- 프로젝트에 디자인 시스템이 있는 경우 해당 토큰/컴포넌트 참조
- 디자인 시스템이 없는 경우: 사용자에게 브랜드 컬러, 타이포그래피, 그리드 시스템을 직접 요청
- 하드코딩된 경로 (`design-system/`, `tokens/design-tokens.json`) 참조 제거
```

---

### 3-5. `writing-guide` 크로스레퍼런스 추가

**문제:** 문서 작성 스킬들이 writing-guide를 참조하지 않음

**수정 파일:**
- `.cursor/skills/create-prd/SKILL.md`
- `.cursor/skills/create-one-pager/SKILL.md`
- `.cursor/skills/synthesize-snapshots/SKILL.md`
- `.cursor/skills/create-design-brief/SKILL.md` (Markdown 출력)

**수정 내용:** 각 스킬의 Quality Standards 또는 가이드라인 섹션에 추가

```markdown
**Writing Standards:**
- `/writing-guide` 스킬의 voice, tone, banned words 규칙을 준수
- LLM 특유 패턴 (em-dash, "Let's dive in" 등) 사용 금지
- 구체적 수치와 예시 사용, 모호한 표현 회피
```

---

### 3-6. `identify-test-assumptions`의 LoFA 제한 보완

**수정 파일:** `.cursor/skills/identify-test-assumptions/SKILL.md`

**수정 내용:**

```markdown
**LoFA Selection (Maximum 3):**
- 상위 우선 사분면(High Importance × Low Evidence)에서 최대 3개 선택
- 3개 초과 시: 나머지는 "Watch List"로 분류하여 문서에 별도 기록
- Watch List 항목은 현재 LoFA 테스트 완료 후 순차적으로 검증
```

---

## Phase 4: Medium 문제 수정

### 4-1. 디렉토리 자동 생성 가이드 추가

**수정 파일:** 파일 저장을 수행하는 모든 스킬 (공통 패턴)

**수정 내용:** 각 스킬의 Output 섹션에 추가

```markdown
**Directory Handling:**
- 저장 경로가 존재하지 않으면 자동 생성
- Initiative 폴더 미존재 시: 사용자에게 `/setup-initiative` 실행 권고
```

---

### 4-2. 피드백 루프 구체화

**수정 파일:** `.cursor/agents/discovery-researcher.md`

**수정 내용:** Interaction Guidelines 섹션 보강

```markdown
## Interaction Guidelines

각 단계 완료 후 사용자 리뷰:
1. 결과물 요약 제시
2. 사용자 선택지 명시:
   - **진행 (Proceed):** 다음 단계로 이동
   - **수정 (Revise):** 현재 결과물의 특정 부분 수정 요청 → 수정 후 다시 리뷰
   - **심화 (Go Deeper):** 현재 단계를 더 깊이 탐구 → 추가 분석 후 다시 리뷰
   - **되돌아가기 (Go Back):** 이전 단계로 돌아가 재작업
3. 수정/심화 시 변경 사항을 새 버전으로 저장 (기존 버전 보존)
```

---

### 4-3. 독립 스킬 vs 에이전트 호출 동작 명시

**수정 파일:** 에이전트에서 호출되는 모든 스킬 (공통 패턴)

**수정 내용:** 각 스킬 상단에 추가

```markdown
**Invocation Context:**
- 독립 호출 시: 모든 전제 조건(입력 검증, 컨텍스트 스캔)을 스킬 자체에서 수행
- 에이전트 경유 시: 에이전트가 전달한 컨텍스트를 활용하되, 필수 전제 조건은 여전히 검증
```

---

### 4-4. `pm-strategic-copilot.mdc` 룰 범위 조정

**수정 파일:** `.cursor/rules/pm-strategic-copilot.mdc`

**수정 내용:** 다른 스킬/에이전트 실행 중에는 간섭하지 않도록 범위 한정

```markdown
**Activation Scope:**
- 스킬이나 에이전트가 활성화된 상태에서는 이 룰의 코칭 기능을 비활성화
- 일반 대화에서만 전략 코파일럿 역할 수행
```

---

### 4-5. 한국어/영어 일관성

**수정 파일:** 3개 에이전트 파일의 description

**방침:** description을 영어로 통일 (스킬 본문, 템플릿과 일치시킴)

---

## Phase 5: README.md 업데이트

### 5-1. README 반영 사항

**수정 파일:** `README.md`

- `process-task-list` 관련 내용 제거
- 스킬 수 18 → 17로 업데이트
- 파일 네이밍 컨벤션 통일 내용 반영
- 에이전트 간 워크플로 연결 다이어그램 추가
- `writing-guide` 크로스레퍼런스 안내 추가

---

## Phase 6: plugin.json 업데이트

### 6-1. plugin.json 반영 사항

**수정 파일:** `.cursor-plugin/plugin.json`

- `process-task-list` 제거 반영
- 스킬 수 관련 설명 업데이트

---

## 실행 순서 요약

| 순서 | Phase | 작업 내용 | 수정 파일 수 |
|------|-------|----------|-------------|
| 1 | Phase 1 | `process-task-list` 삭제 및 참조 정리 | 5 |
| 2 | Phase 2 | Critical 문제 6건 수정 | 10 |
| 3 | Phase 3 | High 문제 6건 수정 | 15 |
| 4 | Phase 4 | Medium 문제 5건 수정 | ~10 |
| 5 | Phase 5 | README 업데이트 | 1 |
| 6 | Phase 6 | plugin.json 업데이트 | 1 |

**총 예상 수정 파일:** ~25개
