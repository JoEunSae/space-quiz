# Project Plan

**Status**: Planning
**Created**: 2026-11-03
**Mode**: AUGMENT

---

## 1. Project Overview

**Goal**: 기존 `index.html` 한 파일에 한국어로 진행되는 접근성 있는 우주 탐험 퀴즈를 구성합니다. 10개 질문, 진행률과 점수 표시, 정답·오답 안내, 결과 및 다시 시작 기능을 제공하며, 별 배경과 행성의 은은한 움직임, 화면 전환 애니메이션을 더합니다. 애니메이션은 `prefers-reduced-motion` 설정을 존중합니다.

**App Type**: 정적 웹사이트 (프런트엔드 전용)

**API Login**: No

**Mode**: AUGMENT

**Deployment Plan**: No deployment plan found

---

## 2. Frontend — Web App

| Component | Technology |
|-----------|-----------|
| **Language** | JavaScript |
| **Framework** | Plain HTML, CSS, and JavaScript |
| **Package Manager** | None — no dependencies or build step |
| **Test Runner** | None — manual browser verification |
| **Mocking Library** | None |
| **Test Command** | 해당 없음 — 브라우저에서 `index.html`을 열어 퀴즈 흐름과 애니메이션을 확인 |

---

## 3. Services Required

| Azure Service | Role in App | Environment Variable | Default Value (Local) | Classification |
|---------------|------------|---------------------|----------------------|----------------|
| None | The quiz runs locally in the browser and does not require Azure services | — | — | Not applicable |

---

## 4. Prerequisites

### Run

| Tool | Service(s) | Installed | Version |
|------|------------|-----------|---------|
| Microsoft Edge | frontend | ✅ | 156.0.4314.58 |

### Debug

| Tool | Service(s) | Installed | Version |
|------|------------|-----------|---------|
| Microsoft Edge | frontend | ✅ | 156.0.4314.58 |

---

## 5. Design System & UI

**Component Library**: Native HTML/CSS and browser controls (no external library, per the no-dependency requirement)
**Style Direction**: 짙은 남색의 별이 빛나는 배경, 은은한 유리 질감 패널, 둥근 모서리, 라벤더·민트·골드 포인트로 친근하고 몰입감 있는 우주 분위기를 만듭니다. 별 배경은 천천히 움직이고 행성 일러스트는 부드럽게 떠오르며, 카드와 피드백은 짧게 나타납니다. 작은 화면에서도 읽기 쉽고 `prefers-reduced-motion` 사용자의 애니메이션은 줄이거나 끕니다.
**Typography**: Inter(사용 가능한 경우), system-ui 및 플랫폼 기본 산세리프 글꼴

### Color Palette

| Token | Hex | Usage |
|-------|-----|-------|
| `primary` | `#A68AFF` | 브랜드 포인트와 주요 버튼 |
| `accent` | `#78F0CB` | 질문 라벨, 정답 피드백, 진행률 강조 |
| `surface` | `#10102A` | 깊은 우주를 표현하는 페이지 배경 |
| `text` | `#F7F5FF` | 질문과 주요 안내 문구 |
| `muted` | `#B7B6D2` | 보조 설명과 정답 해설 |
| `border` | `#3B395E` | 퀴즈 패널과 답안 선택지의 은은한 테두리 |

### Pages

| Page | Route | Purpose | Layout |
|------|-------|---------|--------|
| 우주 탐험 퀴즈 | `/` | 한국어로 퀴즈를 시작하고 10개 질문, 진행률, 답안 피드백 및 최종 점수를 보여줍니다. 다시 시작할 수 있습니다. | `header + hero + main + actions` |

### Sample Content

우주 탐험 퀴즈 — 질문 예시:
| 질문 | 정답 | 해설 | 상태 |
|------|------|------|------|
| 태양에 가장 가까운 행성은 무엇인가요? | 수성 | 수성은 지구 시간으로 88일 만에 태양을 한 바퀴 돕니다. | 준비됨 |
| 붉은 행성이라고 불리는 행성은 무엇인가요? | 화성 | 철 성분이 풍부한 먼지가 화성을 붉게 보이게 합니다. | 준비됨 |
| 가장 뚜렷한 고리를 가진 행성은 무엇인가요? | 토성 | 토성의 고리는 대부분 수많은 얼음 조각으로 이루어져 있습니다. | 준비됨 |
| 지구의 자연 위성 이름은 무엇인가요? | 달 | 달은 지구에서 평균 약 384,400km 떨어져 있습니다. | 준비됨 |
| 우리 태양계가 속한 은하는 무엇인가요? | 우리은하 | 태양계는 우리은하의 나선팔 중 하나에 자리 잡고 있습니다. | 준비됨 |

---

## 6. Project Structure

```
space-quiz/
├── index.html
└── .azure/
    ├── requirements.json
    └── project-plan.md
```

퀴즈 화면의 한국어 문구, 스타일, 질문 데이터, 애니메이션 및 상호작용은 `index.html` 한 파일에 둡니다. 계획 미리보기 파일은 임시 `.azure/.preview-temp/`에만 두며 앱 의존성으로 추가하지 않습니다.

---

## 7. Route Definitions

| # | Method | Path | Description | Request Body | Response Body | Status Codes |
|---|--------|------|-------------|-------------|--------------|-------------|
| 1 | GET | `/` | 한국어 퀴즈 페이지 표시 | — | 스타일과 퀴즈 로직이 포함된 `index.html` | 200 |

No API endpoints are required.

---

## 8. Next Steps

1. 승인 후 **azure-project-scaffold**에서 기존 단일 파일 퀴즈를 유지하며 한국어 UI와 애니메이션을 반영합니다.
2. 데이터베이스 마이그레이션이나 API 연결은 필요하지 않습니다. 브라우저에서 시작, 정답·오답 피드백, 진행률, 결과, 다시 시작 및 모션 감소 설정을 확인합니다.
3. VS Code 디버깅 설정이 필요할 때만 **azure-debug-plan** → **azure-debug-generate**를 사용합니다.
4. 퀴즈를 공개해야 할 때 정적 호스팅을 선택합니다. 로컬 실행에는 Azure 리소스가 필요하지 않습니다.
