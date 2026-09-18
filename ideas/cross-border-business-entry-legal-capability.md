# 다국가 법률 AI 기반 해외사업 진출 법률설계 및 현지 실행지원 Capability

## Stored Idea Metadata

- Idea ID: `IDEA-000001`
- Status: `idea`
- Source handoff: `IDEA_OUTPUT_V1` captured 2026-09-18
- Source bundle candidate adoption status: `adopted_candidate` (non-binding storage hint)
- Decision status: `undecided`
- Authority status: `partially_reflected`
- Implementation status: `not_started`
- Route: `project_direction_update`
- Workflow status: `awaiting_project_direction_update`
- Needs recheck: `true`
- Authority: `non_authoritative_idea_source`
- Target capability: Multi-Jurisdiction Legal Workbench business-entry legal capability
- Related active requirements: `MJLW-REQ-003`, `MJLW-REQ-004`, `MJLW-REQ-005`, `MJLW-REQ-006`, `MJLW-REQ-008`, `MJLW-REQ-009`, `MJLW-REQ-014`, `MJLW-REQ-015`, `MJLW-REQ-017`, `MJLW-REQ-022`
- Related authority: `ARCHITECTURE_BRIEF.md` common-core, source-provider, legal-document projection, and external-integration boundaries
- Storage note: the existing authority already covers the multi-jurisdiction common core and source/translation boundaries, but it does not yet approve the business-entry-specific capability, local execution-role model, cost/period model, or Company OS provider contract.

This document is idea/reference material only. It does not authorize implementation, source acquisition, external execution, legal representation, filing, payment, provider engagement, requirement changes, architecture changes, or PLAN changes.

## 1. Purpose Or Opportunity

해외에서 사업을 시작하려는 사람에게 필요한 것은 단순한 외국법 검색이 아니다.

실제 사업 진출에는 다음과 같은 질문이 연속해서 발생한다.

- 외국인이 해당 사업을 할 수 있는가?
- 외국인 100% 소유가 가능한가?
- 어떤 회사 또는 사업 형태를 이용할 수 있는가?
- 현지 파트너가 필요한가?
- 투자·회사·사업 등록은 어떤 순서로 진행되는가?
- 자본과 사업장에는 어떤 법적 조건이 있는가?
- 업종별 허가나 라이선스가 필요한가?
- 직원을 고용할 때 어떤 규제가 적용되는가?
- 외국인 대표자나 직원에게 어떤 비자·워크퍼밋 규정이 적용되는가?
- 어떤 계약과 문서가 필요한가?
- 어떤 절차는 본인 또는 일반 현지인이 할 수 있고 어떤 절차는 변호사·회계사·공증인 등 자격자가 해야 하는가?
- 공식 비용과 외부 견적 비용은 무엇이며 처리기간은 어느 정도인가?
- 어떤 법률적 위험 때문에 사업 구조를 바꿔야 할 수 있는가?

이 문제를 국가별 공식 법률 자료와 연결하여 구조화하면 `Multi-Jurisdiction Legal Workbench`는 단순한 외국법 검색 도구를 넘어 실제 해외사업 준비를 위한 Legal Capability가 될 수 있다.

초기 관심 대상은 베트남과 필리핀이고, 향후 태국 등 다른 동남아 국가로 확장할 수 있는 구조를 지향한다.

## 2. Proposed Direction

### 2.1 Jurisdiction-aware Business Entry Legal Capability

하나의 공통 법률 코어 위에 각 국가의 법률 source와 legal-system semantics를 별도 adapter로 연결한다.

개념적 흐름은 다음과 같다.

```text
사용자 해외사업 목표
→ 사업 활동 및 핵심 사실 구조화
→ 적용 jurisdiction 식별
→ 해당 국가 공식 source 검색·검증
→ 사업 가능성 및 외국인 규제 분석
→ 사업구조 선택지 분석
→ 등록·허가·신고 절차 구성
→ 계약·문서·전문가 필요성 분석
→ 비용/기간/리스크/미확인사항 분리
→ Business Entry Legal Dossier
→ 현지 실행 역할별 handoff
```

### 2.2 Minimum Legal Intake

법적 결론에 영향을 주는 최소 사실을 우선 수집한다.

후보 fact pivots에는 다음이 포함될 수 있다.

- 대상 국가 및 필요시 지방/도시
- 실제 영위할 사업 또는 서비스
- 온라인/오프라인 여부
- 외국인 100% 소유 요구 여부
- 현지 파트너 허용 여부
- 예상 투자구조
- 사업장 임차·소유 여부
- 현지 직원 채용 여부
- 해외에서 제품을 수입하는지 여부
- 외국인 대표자 또는 직원이 현지에서 근무하는지 여부
- B2C/B2B 등 주요 거래형태
- 규제업종 여부를 판단하는 데 필요한 사업 세부사항

질문 수를 늘리는 것이 목적이 아니라 결론을 바꿀 수 있는 사실을 식별하는 것이 목적이다.

### 2.3 Legal Analysis Areas

국가와 사업에 따라 필요한 항목만 선택적으로 분석한다.

후보 영역은 다음과 같다.

- foreign investment restrictions
- foreign ownership restrictions
- company/entity forms
- branch or representative-office availability
- joint venture requirements
- incorporation and business registration
- capital-related legal conditions
- sector-specific licenses and permits
- premises and lease-related legal issues
- employment and labor
- foreign-worker/representative visa and work-permit law
- commercial contracts
- shareholder or partner agreements
- consumer regulation
- privacy and data protection
- e-commerce rules
- advertising and sector-specific promotion restrictions
- import/product regulation where relevant
- dispute-resolution and governing-law issues where relevant

### 2.4 Source Authority

최종 법률 판단은 jurisdiction별 검증된 공식 source와 연결되어야 한다.

다음 상태를 명확히 구분한다.

```text
authoritative_original
official_translation
unofficial_translation
machine_assisted_translation
aggregation_or_discovery_source
candidate_only
unverified
```

세계법제정보센터는 외국법 discovery, 한국어 번역, metadata 및 초기 corpus 확보에 유용할 수 있으나 해당 국가 전체 법률 corpus나 최종 법적 authority를 자동으로 대신하지 않는다.

### 2.5 Business Entry Legal Dossier

최종 결과는 단순한 채팅 답변보다 구조화된 dossier 형태가 적합하다.

예상 구성:

```text
case / project context
jurisdiction
business activity

legal feasibility
foreign ownership / investment constraints
available business structures
required registrations
required licenses / permits

step-by-step legal procedure
required information
required documents
draftable documents

official fees
externally quoted costs
cost unknowns

statutory / official processing periods
estimated / variable processing periods

legal risks
prohibited or unsafe structures
unresolved facts
professional confirmation required

official sources
source versions
translation status
currentness

execution tasks
responsible role
required qualification
expected evidence to return
```

### 2.6 Local Execution Role Classification

법률 AI가 현지에서 누가 실제 행동을 수행할 수 있는지 구분할 수 있어야 한다.

후보 분류:

```text
AI_ONLY
CLIENT_ACTION
GENERAL_LOCAL_RUNNER
AUTHORIZED_AGENT
LICENSED_LAWYER
LICENSED_ACCOUNTANT_OR_TAX_PROFESSIONAL
NOTARY
OTHER_LICENSED_PROVIDER
GOVERNMENT_ONLY
UNRESOLVED
```

이는 특정 역할의 법적 권한을 임의로 만들어내기 위한 것이 아니다.

각 jurisdiction의 실제 법률에 따라 역할과 자격요건을 검증하고, 불명확할 경우 `UNRESOLVED` 또는 professional confirmation으로 남겨야 한다.

### 2.7 Documents

법률 AI가 향후 준비할 수 있는 문서는 국가별 source-backed 검증과 planning을 거쳐 단계적으로 확대한다.

후보는 다음과 같다.

- incorporation preparation checklist
- registration information sheet
- document request list
- shareholder/partner issue checklist
- lease review checklist
- employment/compliance checklist
- contract clause draft or agreement draft
- license application preparation packet
- authority/professional question packet
- local-runner task sheet
- evidence-return checklist

법률 AI가 생성한 초안이 현지 변호사의 공식 법률의견 또는 자격자의 인증·공증을 대체한다고 표현하지 않는다.

## 3. Confirmed Decisions

- 새 다국가 법률 프로젝트와 기존 한국 법률 프로젝트는 독립적으로 유지한다.
- 기존 `Legal_Coding_Agent_Workbench`는 read-only reference 및 selective-copy source로만 사용한다.
- 새 다국가 프로젝트는 여러 국가를 하나의 공통 코어에 연결하는 방향으로 설계한다.
- 초기 핵심 jurisdiction은 한국·필리핀·베트남이며, 해외사업 관점에서는 태국 등 동남아 확장도 고려한다.
- 사용자에게 해외사업 관련 법률 절차, 주의사항, 필요한 준비, 비용과 기간 정보를 구조적으로 제공하는 방향을 원한다.
- 법률문서 초안 작성 지원을 포함하는 방향을 원한다.
- 실제 현지에서 사람이 해야 하는 작업은 현지 실행자 또는 전문가에게 넘길 수 있는 구조를 원한다.
- 상위 사업 운영 아이디어와 법률 Capability 아이디어를 분리하여 보존한다.
- AI Company OS가 상위 해외사업 프로젝트를 운영할 수 있고, 다국가 법률 AI는 그 프로젝트의 독립 Legal Capability Provider가 되는 구조를 지향한다.

## 4. Recommendations

### 4.1 Keep The Legal Boundary Deep But Narrow

법률 워크벤치가 시장조사·수익성·광고·브랜드·사업 전체 운영을 모두 소유하지 않는다.

법률 워크벤치의 핵심 책임은:

```text
legal feasibility
legal structure
legal procedure
legal source
legal risk
legal documents
legal execution requirements
professional escalation
```

으로 유지한다.

### 4.2 Separate Official Facts From Estimates

비용과 기간은 다음과 같이 구분한다.

```text
official_or_statutory
externally_quoted
estimated
variable
unknown
```

법정 수수료와 변호사·회계사·대행업체 시장가격을 하나의 숫자로 섞지 않는다.

### 4.3 Preserve Country-Specific Meaning

공통 schema는 필요하지만 모든 나라의 법률을 억지로 한국식 용어 하나에 맞추지 않는다.

공통 semantics와 jurisdiction-specific fields를 함께 유지한다.

### 4.4 Fail Closed On Missing Authority

법적 근거나 최신성이 부족할 때는 그럴듯한 답을 완성하지 않는다.

다음과 같은 상태가 허용되어야 한다.

```text
confirmed_from_authoritative_source
conditional
needs_currentness_check
needs_local_professional_confirmation
insufficient_source
unresolved_jurisdiction
```

### 4.5 Provider Integration Later

AI Company OS와 연결할 경우 법률 워크벤치 내부 schema를 Company OS에 그대로 노출하지 않는다.

개념적 연결은:

```text
AI Company OS
→ provider-neutral Legal Work Order
→ adapter
→ Multi-Jurisdiction Legal Workbench
→ source-backed Legal Result
→ adapter
→ provider-neutral Legal Department Result
→ AI Company OS synthesis
```

로 한다.

## 5. Boundaries And Risks

### Legal-service boundary

각 국가에서 AI 또는 비변호사가 어느 수준까지 법률정보·법률문서·회사설립 지원을 제공할 수 있는지 확인해야 한다.

현지 변호사법 또는 관련 전문직 규제가 적용될 수 있다.

### Unauthorized practice

변호사, 회계사, 공증인, 등록대리인 등 자격이 필요한 작업을 일반 현지 실행자에게 할당하지 않는다.

### Illegal circumvention

명의대여, 허위 소유구조, 외국인 규제 우회 등 위법하거나 위험한 수단을 정상적인 사업설립 방법으로 안내하지 않는다.

### Source completeness

공식 aggregator 또는 번역 DB의 자료건수가 많더라도 해당 국가 전체 법령을 확보했다고 간주하지 않는다.

### Collection and redistribution

웹에서 읽을 수 있다는 사실과 자동수집·재배포·상업적 재사용 권리는 별개의 문제다.

### Translation authority

번역본은 원문의 authority status와 분리한다.

### Currentness

회사설립, 라이선스, 외국인투자, 수수료, 처리기간 등은 변경될 수 있으므로 effective/currentness 정보를 유지해야 한다.

### No guaranteed approval

정부 인허가, 회사등록, 비자, 라이선스 등의 승인 결과나 처리기간을 보장하지 않는다.

### External execution

실제 신청, 서명, 제출, 지급, 계약, 공증, 방문 등은 별도의 승인과 실행 경계를 거친다.

## 6. Unknowns And Decisions Still Needed

- 첫 deep implementation jurisdiction의 우선순위
- 필리핀·베트남·태국 각 국가의 회사설립 지원과 법률서비스 제공 규제
- 각 국가 공식 source의 bulk/API acquisition 범위
- 현지 실행자 네트워크 운영 방식
- 현지 전문직 자격 검증 방법
- 서비스 책임범위와 보험 또는 면책 구조
- 제공할 법률문서 family의 초기 범위
- 공식 수수료와 시장견적 데이터의 갱신 방법
- AI가 여러 구조를 비교만 할지 조건부 추천까지 할지
- 다중 jurisdiction 사건에서의 responsibility split
- AI Company OS ↔ Legal Workbench 양방향 provider contract
- 태국 공식 source 및 legal-system acquisition 조사
- 실제 유료서비스 이전의 jurisdiction별 전문직 검토 필요범위

## 7. Relationship To AI Company OS

이 아이디어는 해외사업 전체 운영체계가 아니다.

`Multi-Jurisdiction Legal Workbench`는 해당 운영체계에 source-backed legal capability를 제공한다.

예:

```text
Cross-Border Business Project
       |
       +-- Research / Market
       +-- Finance
       +-- Trade / Product Regulation
       +-- Operations
       +-- Marketing
       |
       +-- Multi-Jurisdiction Legal Workbench
             |
             +-- legal feasibility
             +-- foreign ownership
             +-- entity structure
             +-- permits/licenses
             +-- legal procedure
             +-- legal documents
             +-- legal risks
             +-- execution-role requirements
```

법률 AI 자체는 독립 사용 가능성을 유지한다.

## 8. Future Adoption Path

이 아이디어를 실제 구현으로 올릴 때는:

1. 현재 다국가 프로젝트의 source acquisition 상태를 검증한다.
2. 기존 한국 법률 워크벤치에서 재사용할 공통 법률 코어를 source-backed remake analysis로 분류한다.
3. Business Entry Capability에 필요한 jurisdiction contracts와 source families를 요구사항으로 좁힌다.
4. 가장 작은 국가/사업 end-to-end slice를 PLAN에서 정한다.
5. 구현·검증 후 다른 국가와 사업유형으로 확장한다.

이 문서는 그 구현을 승인하지 않는다. 현재는 향후 요구사항·PLAN 후보를 위한 아이디어 소스이다.
