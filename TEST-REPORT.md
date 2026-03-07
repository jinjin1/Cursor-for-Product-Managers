# Cursor for Product Managers - 테스트 리포트

**테스트 일자:** 2026-03-06
**테스트 범위:** 전체 18개 스킬, 3개 에이전트, 1개 룰, plugin.json
**테스트 방법:** 임의 데이터를 기반으로 워크플로 시뮬레이션 및 코드 리뷰

---

## 요약

총 **37개 문제점**을 발견했으며, 심각도별로 분류하면 다음과 같습니다:

| 심각도 | 개수 | 설명 |
|--------|------|------|
| Critical | 7 | 워크플로가 중단되거나 잘못된 결과를 생성하는 문제 |
| High | 12 | 기능이 의도대로 작동하지 않을 수 있는 문제 |
| Medium | 11 | 사용성이나 일관성에 영향을 주는 문제 |
| Low | 7 | 개선하면 좋은 사항 |

---

## 1. 에이전트(Agent) 동작 문제점

### [Critical] 1-1. `disable-model-invocation: true` 스킬을 에이전트가 호출

**파일:** `initiative-planner` agent → `setup-initiative`, `generate-figma-prompt` skills

`setup-initiative/SKILL.md`와 `generate-figma-prompt/SKILL.md`에는 `disable-model-invocation: true`가 설정되어 있습니다. 그런데 `initiative-planner` 에이전트는 Phase 1에서 `/setup-initiative`, Phase 5에서 `/generate-figma-prompt`를 호출하도록 지시합니다.

- `disable-model-invocation: true`는 AI 모델이 해당 스킬을 직접 실행하지 않겠다는 의미인데, 에이전트 워크플로에서는 이를 무시하고 호출을 시도합니다.
- **결과:** 에이전트가 이 스킬들을 호출할 때 실행되지 않거나 예측 불가능한 동작 발생 가능

**제안:** `disable-model-invocation` 플래그를 제거하거나, 에이전트 워크플로에서 해당 스킬이 비활성화된 경우의 대체 흐름을 정의해야 합니다.

---

### [Critical] 1-2. 에이전트 간 핸드오프(Handoff) 미정의

**파일:** `discovery-researcher.md`, `initiative-planner.md`

`discovery-researcher`는 디스커버리 완료 후 "Recommended next steps and timeline"을 출력하고 종료합니다. `initiative-planner`는 "Phase 1: Initiative Setup"부터 시작합니다. 두 에이전트 간의 전환 지점이 명확히 정의되어 있지 않습니다.

- 디스커버리 결과물(기회, 솔루션, 가정)이 이니셔티브 플래너로 어떻게 전달되는지 정의 없음
- 어떤 시점에서 discovery → planning으로 전환해야 하는지 판단 기준 없음
- **결과:** 사용자가 두 에이전트를 수동으로 연결해야 하며, 컨텍스트 손실 가능

**제안:** 에이전트 간 전환 프로토콜을 정의하거나, 상위 오케스트레이션 에이전트를 추가해야 합니다.

---

### [High] 1-3. `discovery-researcher`가 `company-level-context/` 스캔을 생략

**파일:** `discovery-researcher.md` vs `create-opportunities/SKILL.md`

`create-opportunities` 스킬은 "0.5) Context Source Analysis (MANDATORY PRE-STEP)"로 `company-level-context/` 디렉토리를 반드시 스캔하도록 지시합니다. 그러나 `discovery-researcher` 에이전트의 Step 3에서는 이 사전 단계를 언급하지 않습니다.

- **결과:** 에이전트를 통해 호출 시 전략적 맥락 없이 기회가 도출될 수 있음

---

### [High] 1-4. `strategy-reviewer`의 Evidence Readiness Check 불완전

**파일:** `strategy-reviewer.md`

에이전트 워크플로 Step 3에서 "Run the Evidence Readiness Check before scoring"이라고만 되어 있고:
- HOLD 판정 시 어떻게 해야 하는지 정의 없음
- 최소 4개 Core Evidence 항목의 구체적 검증 방법 미지정
- 사용자에게 Evidence Sprint를 제안하는 프로세스 누락

---

### [High] 1-5. 에이전트에서 `process-task-list` 미참조

**파일:** `initiative-planner.md`

Phase 6에서 `/generate-tasks`로 태스크를 생성하지만, 그 태스크를 실행하는 `/process-task-list` 스킬은 에이전트 워크플로에 포함되지 않았습니다.

- **결과:** 태스크 생성까지만 자동화되고, 실행은 사용자가 별도로 `/process-task-list`를 수동 호출해야 함

---

### [Medium] 1-6. 3개 스킬이 어떤 에이전트에서도 참조되지 않음 (Orphaned Skills)

다음 스킬들은 독립적으로만 사용 가능하고, 에이전트 오케스트레이션에 통합되지 않음:
- `/process-task-list` - 태스크 실행 워크플로
- `/one-on-one-meeting` - 1:1 미팅 노트
- `/writing-guide` - 작성 가이드

`/writing-guide`는 PRD, 1-Pager, 합성 문서 등 모든 문서 작성 스킬에서 참조되어야 하지만, 어떤 스킬에서도 cross-reference하지 않습니다.

---

### [Medium] 1-7. `model: inherit`의 모호성

**파일:** 모든 에이전트 파일

3개 에이전트 모두 `model: inherit`를 사용하지만, 어떤 모델을 상속받는지 명시적 문서가 없습니다. Cursor 환경에서는 부모 컨텍스트의 모델을 상속받는 것으로 추정되지만, 다른 환경에서는 혼란을 유발할 수 있습니다.

---

## 2. 스킬(Skill) 동작 문제점

### [Critical] 2-1. `synthesize-snapshots`의 파일 네이밍 모순

**파일:** `synthesize-snapshots/SKILL.md` (Line 70 vs Line 80)

동일 문서 내에서 상충되는 지시사항:
- Line 70: `"Use current initiative folder name as primary identifier"`
- Line 80: `"Use extracted topic instead of initiative name as primary identifier"`

둘 다 "primary identifier"로 지정되어 있어 AI가 어떤 것을 따라야 하는지 혼란을 유발합니다.

- Line 586 Best Practice에서는 "INITIATIVE-BASED NAMING" 강조
- Line 80에서는 "extracted topic" 사용 지시
- **결과:** 같은 이니셔티브에 대해 서로 다른 파일명이 생성될 수 있음

**제안:** 하나로 통일 필요. 이니셔티브 폴더명 기반이 더 일관적입니다.

---

### [Critical] 2-2. `generate-solutions`의 Step 2 강제 중단 로직의 실효성 부족

**파일:** `generate-solutions/SKILL.md`

"CRITICAL: AI MUST NOT SKIP STEP 2" - 사용자가 먼저 최소 3개 아이디어를 제시해야 AI가 진행한다고 되어 있습니다. 그러나:
- 이것은 텍스트 지시사항일 뿐, 실제 기술적 강제 메커니즘이 없음
- `discovery-researcher` 에이전트는 이 제약을 명시적으로 인지하지 않음
- **결과:** AI가 이 지시사항을 무시하고 바로 솔루션을 생성할 가능성이 높음

---

### [Critical] 2-3. `calculate-ice-score`의 팬텀 기본값 문제

**파일:** `calculate-ice-score/SKILL.md`

> "Automatic fallback: If no explicit percentage is provided, assume a default +1.5% improvement → Impact 2"

데이터가 없을 때 기본값 2를 자동 적용하면:
- 사용자에게 기본값이 적용되었다는 경고 없음
- 근거 없는 점수가 의사결정에 사용될 위험
- **결과:** 팬텀 데이터 기반 우선순위 결정 → 잘못된 의사결정 유도

---

### [High] 2-4. 버전 관리 로직의 비결정적 동작

**파일:** `create-opportunities`, `generate-solutions`, `identify-test-assumptions`, `synthesize-snapshots`

4개 스킬에서 동일한 버전 관리 프로세스를 사용하지만:
1. 기존 파일이 패턴과 다른 이름일 경우 (예: `solutions-old.md`) 처리 방법 없음
2. 비순차적 버전 (v1, v2, v5) 시 다음 버전이 v3인지 v6인지 불명확
3. 사용자가 명시적으로 덮어쓰기를 원할 때의 프로토콜 없음
4. 토픽 추출이 비결정적 (동일 내용에서 다른 토픽이 추출될 수 있음)
- **결과:** 파일 버전 관리가 불안정해져 이전 버전과 추적이 어려워짐

---

### [High] 2-5. 스킬 간 파일 네이밍 불일치

| 스킬 | 파일명 패턴 | 식별자 | 날짜 포함 | 버전 관리 |
|------|------------|--------|-----------|-----------|
| create-interview-snapshots | `snapshot-[name]-[date].md` | participant name | O | X |
| synthesize-snapshots | `synthesis-[initiative]-v[N].md` | initiative name | X | O |
| create-opportunities | `opportunities-[topic]-v[N].md` | extracted topic | X | O |
| generate-solutions | `solutions-[topic]-v[N].md` | extracted topic | X | O |
| identify-test-assumptions | `assumptions-[opportunity]-v[N].md` | opportunity name | X | O |
| calculate-ice-score | `ice-[date]-[title].md` | slugified title | O | X |
| create-prd | `prd-[feature].md` | feature name | X | X |
| create-one-pager | `1-pager-[initiative].md` | initiative name | X | X |
| create-design-brief | `design-brief-[feature].[ext]` | feature name | X | X |

**문제점:**
- 식별자 기준이 5종류 (participant name, initiative name, extracted topic, opportunity name, slugified title)
- 날짜 포함 여부가 일관적이지 않음 (2개만 날짜 포함)
- 버전 관리가 선택적 (5개만 버전 관리)
- PRD, 1-Pager, Design Brief에는 버전 관리가 없어 수정 시 덮어쓰기 발생 가능

---

### [High] 2-6. `create-opportunities`의 `company-level-context/` 의존성

**파일:** `create-opportunities/SKILL.md`

"MANDATORY PRE-STEP"으로 `company-level-context/` 디렉토리 스캔이 요구되지만:
- 현재 `company-level-context/okrs/`와 `product-vision-and-strategy/`에는 `.gitkeep` 파일만 존재
- 실제 전략 문서가 없을 때의 폴백(fallback) 처리 미정의
- **결과:** 빈 디렉토리를 스캔하고도 "전략적 정렬"을 진행하려 시도할 가능성

---

### [High] 2-7. `create-design-brief`의 존재하지 않는 디자인 시스템 참조

**파일:** `create-design-brief/SKILL.md`

`design-system/`, `tokens/design-tokens.json`, `components/component-library.json` 경로를 참조하지만:
- 이 파일/디렉토리가 프로젝트에 존재하지 않음
- 초기 설정이나 생성 프로세스가 없음
- **결과:** 디자인 브리프 생성 시 디자인 시스템 매핑이 항상 실패

---

### [High] 2-8. `identify-test-assumptions`의 LoFA 제한 모순

**파일:** `identify-test-assumptions/SKILL.md`

- "Maximum 3 LoFA per assumption document"로 제한
- 그러나 상위 우선 사분면에 5개 이상의 중요한 가정이 있을 경우의 처리 방법이 부적절
- **결과:** 중요한 가정이 문서에서 누락될 수 있음

---

### [High] 2-9. `process-task-list`의 타임아웃/에스컬레이션 없음

**파일:** `process-task-list/SKILL.md`

"Do NOT start next sub-task until user says yes" - 사용자 확인을 대기하지만:
- 사용자가 응답하지 않을 경우의 타임아웃 없음
- 테스트 실패, 머지 충돌 시의 에스컬레이션 경로 없음
- 태스크가 불완전할 때의 복구 방법 없음

---

### [Medium] 2-10. `writing-guide`가 문서 작성 스킬에서 참조되지 않음

**파일:** `writing-guide/SKILL.md`

79개의 금지 단어, LLM 특유의 표현 회피 규칙, 톤 & 스타일 가이드라인이 정의되어 있지만:
- `create-prd`, `create-one-pager`, `synthesize-snapshots` 등 문서 작성 스킬에서 이를 참조하지 않음
- **결과:** 각 스킬이 독자적 작성 스타일로 문서를 생성하여 일관성 부족

---

### [Medium] 2-11. `product-strategy-review`의 HOLD vs PROCEED 경계 모호

**파일:** `product-strategy-review/SKILL.md`

- "HOLD prohibits scoring" - Core Evidence ≤ 3이면 점수 매기기 금지
- "PROCEED: Core ≥ 4" - 4개 이상이면 진행
- **문제:** 4개가 있지만 품질이 낮을 경우의 판단 기준 없음 (수량만으로 PROCEED 판정)

---

### [Medium] 2-12. 디렉토리 미존재 시 자동 생성 로직 부재

다수의 스킬이 특정 디렉토리에 파일을 저장하도록 지시하지만:
- 해당 디렉토리가 존재하지 않을 경우 자동 생성할지에 대한 지시 없음
- `/setup-initiative`를 실행하지 않은 상태에서 스킬을 직접 호출할 경우 파일 저장 실패 가능
- **결과:** 단독 스킬 호출 시 파일 저장 경로 오류

---

### [Medium] 2-13. `create-interview-snapshots`의 날짜 형식 미지정

**파일:** `create-interview-snapshots/SKILL.md`

파일명 패턴 `snapshot-[participant-name]-[date].md`에서 `[date]`의 형식이 지정되지 않음:
- YYYY-MM-DD인지, YYYYMMDD인지, MM-DD인지 불명확
- **결과:** 일관되지 않은 파일명 생성

---

### [Low] 2-14. `okr-sparring-partner`의 조직 크기 변경 미고려

분기 중 조직 크기가 변경될 경우 (예: 50명 → 60명으로 성장) OKR 기준이 어떻게 변경되는지 가이드 없음.

---

### [Low] 2-15. `create-one-pager`의 예시와 프로세스 간 모순

"Always supplement input through Clarifying Questions first"라고 하면서도 템플릿에 미리 채워진 예시 섹션이 존재하여, 질문 없이도 시작 가능한 인상을 줍니다.

---

## 3. 워크플로 체인 문제점

### [Critical] 3-1. 순환적 버전 번호 혼란

**시나리오:** 동일 토픽 "user-onboarding"에 대해:
1. `opportunities-user-onboarding-v1.md` 생성
2. `solutions-user-onboarding-v1.md` 생성
3. `assumptions-user-onboarding-v1.md` 생성
4. 기회를 업데이트 → `opportunities-user-onboarding-v2.md`

**문제:** 기회가 v2로 업데이트되었을 때, 솔루션과 가정도 업데이트해야 하는지? 독립적 라이프사이클인지 연결된 라이프사이클인지 정의 없음.
- **결과:** 어떤 버전의 기회에 대한 솔루션인지 추적 불가

---

### [Critical] 3-2. 토픽 추출의 비결정적 특성

`create-opportunities`와 `generate-solutions`에서 "Topic Extraction"을 수행하지만:
- 알고리즘이 명시되지 않음
- 같은 내용에서 다른 토픽이 추출될 수 있음
- Fallback으로 "generic topic name" 사용 시 (예: `solutions-topic-1.md`) 버전 검색이 불가능
- **결과:** 파일 간 연결 관계가 깨질 수 있음

---

### [High] 3-3. Discovery → Opportunity → Solution 체인에서 기회 선택 메커니즘 부재

`discovery-researcher`가 여러 기회를 도출했을 때:
- 어떤 기회에 대해 솔루션을 생성할지 선택하는 메커니즘 없음
- 여러 기회를 병렬로 탐색하는 워크플로 분기 없음
- **결과:** 사용자가 수동으로 기회를 선택해야 하는 상황이 빈번

---

### [High] 3-4. Synthesis → Opportunities 간 폴더 경로 불일치

**시뮬레이션 결과:**
- `synthesize-snapshots`는 `user-interviews/synthesis/`에 파일 저장
- `create-opportunities`는 `opportunities/[topic]/`에 저장
- 그런데 `synthesize-snapshots`의 예시 폴더 구조 (Line 193)에서는 `user-interviews/opportunities/`에 기회 파일을 저장하는 것으로 표시

이 경로 불일치로 인해 스킬 간 파일 참조가 실패할 수 있습니다.

---

### [Medium] 3-5. 피드백 루프 미정의

`discovery-researcher`에서 "Present intermediate results to user for review"라고 하지만:
- 사용자 피드백이 어떻게 워크플로에 반영되는지 정의 없음
- "조정(adjust)" 또는 "더 깊게(go deeper)" 선택 시의 구체적 분기 없음
- **결과:** 리뷰 체크포인트가 형식적이 되어 실질적 반복(iteration)이 이루어지지 않음

---

### [Medium] 3-6. 독립 스킬 vs 에이전트 호출 시 동작 차이

스킬을 직접 호출할 때와 에이전트를 통해 호출할 때의 동작 차이가 정의되지 않음:
- 에이전트는 이전 단계의 컨텍스트를 가지고 있지만, 직접 호출 시에는 없음
- `create-opportunities`를 직접 호출할 때 `company-level-context/` 스캔을 수행하지만, `discovery-researcher`를 통해 호출할 때는 이 단계가 명시되지 않음

---

## 4. 설정 및 구조 문제점

### [Medium] 4-1. `plugin.json`에 `writing-guide` 스킬의 역할 미정의

`plugin.json`에 18개 스킬이 정확히 등록되어 있지만, `writing-guide`가 다른 스킬의 전제 조건이라는 관계가 정의되지 않음.

---

### [Medium] 4-2. `pm-strategic-copilot.mdc` 룰과 스킬 간 중복

**파일:** `.cursor/rules/pm-strategic-copilot.mdc`

글로벌 룰로 "전략 코치" 역할이 정의되어 있는데, `strategy-reviewer` 에이전트와 기능이 상당 부분 중복됩니다. 룰은 항상 적용되므로 다른 스킬 실행 시 간섭 가능.

---

### [Low] 4-3. 템플릿 README에 이모지 사용

**파일:** `initiatives/_templates/initiative-template/README.md`

템플릿에 이모지 (🎯, 📊, 🗂️, 🔗, 📝)가 사용되고 있으나, `writing-guide`에서는 이모지 사용에 대한 가이드가 없습니다. 일관성 관점에서 통일 필요.

---

### [Low] 4-4. `company-level-context/` 내 실제 콘텐츠 부재

`okrs/`와 `product-vision-and-strategy/`에 `.gitkeep`만 존재하여, `create-opportunities`의 MANDATORY 전략 스캔이 실질적 의미 없음. 예시 데이터 또는 가이드라인 제공 필요.

---

### [Low] 4-5. Archive 프로세스 문서의 불완전

`initiatives/archive/README.md`에 이니셔티브 이동 프로세스가 설명되어 있으나, 이를 자동화하는 스킬이 존재하지 않음.

---

### [Low] 4-6. 한국어/영어 혼용

에이전트 description은 한국어로 작성되어 있으나 (예: `discovery-researcher.md`의 description), 스킬 본문과 템플릿은 모두 영어입니다. 이중 언어 사용이 의도적인지 불명확.

---

## 5. 임의 데이터 시뮬레이션 결과

### 테스트 시나리오: "모바일 앱 온보딩 개선" 이니셔티브

**시뮬레이션 흐름:**
1. `/setup-initiative` → 폴더 생성 시도 → `disable-model-invocation: true`로 인해 동작 불확실
2. 가상 인터뷰 데이터 3건으로 `/create-interview-snapshots` 실행 → 날짜 형식 미지정으로 파일명 불일치 가능
3. `/synthesize-snapshots` → "initiative name vs extracted topic" 모순으로 파일명 불확실
4. `/create-opportunities` → `company-level-context/` 빈 디렉토리 스캔 → 전략적 정렬 실패
5. `/generate-solutions` → Step 2 (사용자 아이디어 제출) 강제가 기술적으로 불가능
6. `/calculate-ice-score` → 데이터 없이 기본 Impact 2 적용 → 팬텀 점수 생성

**결론:** 6단계 중 5단계에서 문제 발생 가능

---

## 6. 개선 권고사항

### 즉시 수정 (Critical)
1. `setup-initiative`와 `generate-figma-prompt`의 `disable-model-invocation` 플래그 처리 방법 결정
2. `synthesize-snapshots`의 파일 네이밍 모순 해결 (initiative name vs extracted topic 중 하나로 통일)
3. 스킬 간 버전 연결 관계 정의 (기회 v2 → 솔루션 v2 관계 등)
4. 토픽 추출 알고리즘 또는 규칙 명시

### 높은 우선순위 (High)
5. 에이전트 간 핸드오프 프로토콜 정의
6. `company-level-context/` 빈 디렉토리 시 폴백 로직 추가
7. 파일 네이밍 컨벤션 통일 (식별자, 날짜, 버전 관리 기준)
8. `calculate-ice-score`의 기본값 적용 시 사용자 경고 추가
9. `writing-guide`를 문서 작성 스킬에서 참조하도록 연결

### 중간 우선순위 (Medium)
10. 디렉토리 자동 생성 로직 또는 존재 확인 가이드 추가
11. 피드백 루프 구체화 (사용자 피드백 → 워크플로 반영 방법)
12. 독립 스킬 호출 vs 에이전트 경유 호출 시의 동작 차이 명시
13. Orphaned 스킬 (`process-task-list`, `one-on-one-meeting`, `writing-guide`) 에이전트 통합

### 낮은 우선순위 (Low)
14. 예시 데이터/샘플 추가 (company-level-context, 테스트용 인터뷰 데이터)
15. 이모지 사용 가이드라인 통일
16. Archive 자동화 스킬 추가
17. 한국어/영어 사용 기준 정리

---

*이 리포트는 코드 리뷰와 임의 데이터 기반 워크플로 시뮬레이션을 통해 작성되었습니다.*
