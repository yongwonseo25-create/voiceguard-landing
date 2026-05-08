# VoiceGuard 랜딩페이지 디자인 시스템 가이드

> **기준 파일:** `모두의창업_랜딩페이지_VoiceGuard.html`  
> **버전:** v2.0 (2026-05-08)  
> **목적:** 이 랜딩페이지의 시각 언어를 완전히 정의한다. 신규 컴포넌트 추가, 이미지 교체, 카피 수정 시 이 가이드를 기준으로 삼는다.

---

## 1. 브랜드 톤 & 무드

```
따뜻한 신뢰감 + 전문 의료·복지 영역 + 기술 플랫폼
크림-웜 베이지 배경 위에 오렌지 강조색을 사용해
"안전하고 믿을 수 있는 디지털 증빙 시스템"을 표현한다.
```

**피해야 할 무드:**
- 사이버펑크 / 파란 네온 / 어두운 해커 대시보드
- 과도하게 밝은 흰색 배경 (차갑게 느껴짐)
- 붉은 위험 계열 강조 (신뢰 훼손)

---

## 2. 컬러 팔레트

### 2-1. 기본 배경 계열 (Warm Cream)

| 토큰 | Hex | 용도 |
|------|-----|------|
| `--bg` | `#F5EFE4` | 전체 기본 배경, Section 01 |
| `--bg-alt` | `#EFE8DA` | Section 02 배경 (약간 어두운 크림) |
| `--panel` | `#FAF5EC` | Section 03 배경 (약간 밝은 크림) |
| `--card` | `#FFF9F1` | 카드·노드 배경 |
| `--card-hover` | `#FFFCF5` | 카드 호버 상태 배경 |

### 2-2. 오렌지 강조 계열 (Brand Orange)

| 토큰 | Hex | 용도 |
|------|-----|------|
| `--orange` | `#D86A23` | 포인트 오렌지 — 버튼, 활성 상태, 섹션 번호 |
| `--orange-deep` | `#C95C18` | 딥 오렌지 — 버튼 그라디언트 시작점 |
| `--orange-light` | `#FDEBD8` | 연한 오렌지 — 활성 카드/배지 배경 |
| `--orange-glow` | `rgba(216,106,35,0.18)` | 오렌지 글로우 그림자 |

**CTA 버튼 그라디언트:**
```css
background: linear-gradient(135deg, #C95C18 0%, #E07830 60%, #D86A23 100%);
```

### 2-3. 중립 계열 (Neutral Brown)

| 토큰 | Hex | 용도 |
|------|-----|------|
| `--brown` | `#8A6A4A` | 창업자 카드 테두리, 조직도 연결선 |
| `--border` | `#CDBA9F` | 기본 카드·노드 테두리 |
| `--border-hover` | `#D86A23` | 호버 시 테두리 (오렌지) |

### 2-4. 텍스트 계열

| 토큰 | Hex | 용도 |
|------|-----|------|
| `--text` | `#201A16` | 제목, 본문 — 다크 브라운블랙 |
| `--text-sub` | `#7B6A5B` | 서브카피, 설명 — 웜 그레이 |

### 2-5. 칩 태그 계열 (Section 02 AI 구조화 노드)

| 클래스 | 배경 | 텍스트 | 용도 |
|--------|------|--------|------|
| `.chip-a` | `#E3F0FF` | `#2A6ACC` | 급여 분류 |
| `.chip-b` | `#FFF5D6` | `#8A6400` | 특이 분류 |
| `.chip-c` | `#FFE8E6` | `#C44736` | 위험 분류 |

---

## 3. 타이포그래피

**폰트 패밀리:**
```css
font-family: 'Noto Sans KR', -apple-system, BlinkMacSystemFont, sans-serif;
```

### 3-1. 타입 스케일

| 요소 | 클래스/선택자 | 크기 | 굵기 | 색상 |
|------|--------------|------|------|------|
| 섹션 H1 | `.section-h1` | 40px | 800 | `--text` |
| 섹션 서브카피 | `.section-sub` | 16px | 400 | `--text-sub` |
| 히어로 배지 | `.hero-badge` | 16px | 700 | `--text` / `--orange` (active) |
| 플로우 노드 라벨 | `.node-label` | 13px | 700 | `--text` |
| 플로우 노드 설명 | `.node-desc` | 11px | 400 | `--text-sub` |
| 에이전트 카드 이름 | `.agent-name` | 13px | 700 | `--text` |
| 에이전트 카드 설명 | `.agent-desc` | 11px | 400 | `--text-sub` |
| 창업자 타이틀 | `.founder-title` | 15px | 700 | `--text` |
| 창업자 역할 | `.founder-role` | 12px | 400 | `--text-sub` |
| 가치 배지 제목 | `.value-title` | 14px | 700 | `--text` |
| 가치 배지 설명 | `.value-desc` | 12px | 400 | `--text-sub` |
| 핵심 문장 | `.core-msg` | 16px | 700 | `--orange` |

### 3-2. 타이포그래피 규칙
- `word-break: keep-all` — 한국어 단어 중간 줄바꿈 방지 (필수)
- `letter-spacing: -0.7px` — H1 자간 좁힘
- `line-height: 1.28` — H1 줄간격
- `line-height: 1.8` — 서브카피 줄간격

---

## 4. 그림자 시스템

| 토큰 | 값 | 사용 상황 |
|------|-----|----------|
| `--shadow-xs` | `0 1px 4px rgba(80,55,30,0.06)` | 레이블 태그, 스텝 바 |
| `--shadow-sm` | `0 2px 12px rgba(80,55,30,0.08)` | 기본 카드, 노드 |
| `--shadow-md` | `0 6px 24px rgba(80,55,30,0.10)` | 창업자 카드 |
| `--shadow-lg` | `0 16px 40px rgba(80,55,30,0.14)` | 창업자 카드 호버 |
| `--shadow-hover` | `0 14px 36px rgba(80,55,30,0.14)` | 카드·노드 호버 공통 |

---

## 5. 인터랙션 & 애니메이션

### 5-1. 이징 함수
```css
--ease-out: cubic-bezier(0.22, 1, 0.36, 1);
```
모든 hover transition에 이 이징을 사용한다.

### 5-2. 호버 규칙

| 컴포넌트 | 호버 효과 |
|----------|----------|
| 카드 (`.node`, `.agent-card`, `.value-card`) | `translateY(-5px)` + shadow 증가 + 테두리 오렌지 |
| 히어로 배지 (`.hero-badge`) | `translateY(-3px)` + shadow 증가 + 테두리 오렌지 |
| CTA 버튼 (`.btn-demo`) | `translateY(-2px)` + shadow 증가 |
| 플레이 버튼 (`.play-btn`) | `scale(1.10)` + glow shadow 확대 |
| 창업자 카드 (`.founder-card`) | `translateY(-5px)` + shadow 증가 |

**Transition 표준:**
```css
transition: transform 0.22s var(--ease-out), box-shadow 0.22s, border-color 0.22s;
```

### 5-3. 파형 애니메이션 (`.waveform`)
```css
@keyframes wwave {
  0%, 100% { transform: scaleY(1); opacity: 0.6; }
  50%       { transform: scaleY(1.75); opacity: 1; }
}
/* 각 바(.wbar)에 개별 animation-delay 적용 */
```
- 바 개수: 8개 (Section 01), 6개 (Section 02)
- 애니메이션: `1.2s ease-in-out infinite`

---

## 6. 레이아웃 시스템

### 6-1. 기본 규칙
```
max-width: 1200px (--max-w)
헤더 높이: 100px (--header-h)
섹션 padding-top: var(--header-h) — 고정 헤더 보정
섹션 padding: 60px 56px
```

### 6-2. 섹션 구조

```
<section class="section section-0N" id="section-0N">
  <div class="section-inner">
    <div class="badge">0N</div>
    <h1 class="section-h1">...</h1>
    <p class="section-sub">...</p>
    <!-- 섹션별 콘텐츠 -->
  </div>
</section>
```

### 6-3. 섹션별 배경

| 섹션 | 배경 | 상단 테두리 |
|------|------|-------------|
| S01 | `var(--bg)` | 없음 |
| S02 | `linear-gradient(180deg, var(--bg-alt) 0%, var(--bg) 100%)` | `1px solid rgba(205,186,159,0.4)` |
| S03 | `var(--panel)` | `1px solid rgba(205,186,159,0.4)` |

### 6-4. 비디오 박스 규격

| 박스 | 클래스 | max-width | aspect-ratio |
|------|--------|-----------|--------------|
| 히어로 박스 | `.video-frame-outer` | 880px | 16/9 |
| 데모 박스 | `.demo-frame-outer` | 760px | 16/9 |

**외부 프레임 테두리 처리:**
```css
/* 히어로 박스 */
background: linear-gradient(135deg, #E4D4BC 0%, #C8B49A 50%, #D8C4A8 100%);
padding: 6px;
border-radius: 26px;
```

---

## 7. 컴포넌트 라이브러리

### 7-1. 히어로 Pill 배지 (Section 01)

**구조:**
```html
<div class="hero-badge-row">
  <div class="hero-badge [active]">
    <span class="hero-badge-icon">{이모지}</span>
    {라벨}
  </div>
  <span class="hero-badge-arrow">→</span>
  <!-- 반복 -->
</div>
```

**핵심 CSS:**
```css
.hero-badge-row {
  display: flex;
  width: 100%;
  max-width: 880px;  /* 비디오 박스와 동일 폭 */
  margin: 0 auto;
}
.hero-badge {
  flex: 1;           /* 균등 분배 */
  padding: 16px 10px;
  border-radius: 50px;
  font-size: 16px;
  font-weight: 700;
}
.hero-badge.active {
  background: var(--orange-light);
  border: 2px solid var(--orange);
  color: var(--orange);
}
```

**규칙:**
- 배지 개수는 항상 4개 유지 (4개가 880px에 균등 배치되도록 설계됨)
- active 배지는 반드시 1개만 (현재: 증거 원장)

---

### 7-2. 플로우 노드 카드 (Section 02)

**구조:**
```html
<div class="flow-row">
  <div class="node [active]">
    <span class="node-icon">{이모지 또는 SVG}</span>
    <div class="node-label">{라벨}</div>
    <div class="node-desc">{설명}</div>
  </div>
  <div class="flow-arrow">
    <span class="flow-arrow-icon">→</span>
    <span class="flow-arrow-dot"></span>
  </div>
  <!-- 반복 -->
</div>
```

**히어로 배지와의 차이:**
| 항목 | 히어로 배지 (S01) | 플로우 노드 (S02) |
|------|------------------|------------------|
| 모양 | pill (border-radius: 50px) | 카드 (border-radius: 14px) |
| 크기 | flex:1 균등 | flex:1 + min-width:120px |
| 내용 | 이모지 + 라벨만 | 이모지 + 라벨 + 설명 |
| SVG | 없음 | 마이크·방패 커스텀 SVG |
| 화살표 | `<span>→</span>` | `.flow-arrow` div (점 포함) |

---

### 7-3. 조직도 시스템 (Section 03)

**계층 구조:**
```
.org-tree (flex-column, align-center)
  ├── .founder-card (창업자 단독 카드, 210px)
  ├── .org-trunk (수직 연결선, 2px×36px)
  └── .org-branches (flex-row, 100%)
        ├── .org-agent-wrap (::before=수직선, ::after=수평선)
        │     └── .agent-card
        ├── .org-agent-wrap
        │     └── .agent-card
        ├── .org-agent-wrap
        │     └── .agent-card
        └── .org-agent-wrap
              └── .agent-card
```

**창업자 카드 규격:**
```css
.founder-card { width: 210px; border: 1.5px solid var(--brown); border-radius: 18px; }
.founder-avatar { width: 140px; height: 160px; object-fit: contain; }
```

**에이전트 카드 규격:**
```css
.agent-card { border-radius: 14px; padding: 20px 10px; }
.agent-avatar { width: 130px; height: 130px; object-fit: contain; }
```

**연결선 구현 (CSS pseudo-element):**
```css
.org-agent-wrap::before { /* 수직선 - 각 카드 위 */ }
.org-agent-wrap:first-child::after { left: 50%; right: 0; } /* 오른쪽 절반만 */
.org-agent-wrap:last-child::after  { left: 0; right: 50%; } /* 왼쪽 절반만 */
.org-agent-wrap:not(:first-child):not(:last-child)::after { left: 0; right: 0; } /* 전체 */
```

---

### 7-4. 섹션 번호 배지

```html
<div class="badge">01</div>
```
```css
.badge {
  width: 30px; height: 30px;
  background: var(--orange);
  color: #fff;
  border-radius: 50%;
  font-size: 12px; font-weight: 700;
}
```

---

### 7-5. CTA 버튼

```html
<button class="btn-demo">
  30초 데모 보기 <span class="btn-arrow">▶</span>
</button>
```
- 항상 헤더 우측에 고정
- 클릭 시 Section 02로 스크롤 이동

---

### 7-6. 스텝 인디케이터 (Section 02)

```html
<div class="step-bar">
  <div class="step-item">🎙 현장 발화</div>
  <span class="step-sep">→</span>
  <div class="step-item on">🛡 증거 원장</div>  <!-- on = 강조 -->
  <span class="step-sep">→</span>
  <div class="step-item">⚙️ AI 구조화</div>
  <span class="step-sep">→</span>
  <div class="step-item">📋 운영 조치</div>
</div>
```

---

### 7-7. 가치 배지 카드 (Section 03 하단)

```html
<div class="values-row">
  <div class="value-card">
    <span class="value-icon">{이모지}</span>
    <div class="value-title">{제목}</div>
    <div class="value-desc">{설명}</div>
  </div>
</div>
```
- `max-width: 240px`
- 3개 균등 배치 (flex:1)

---

## 8. 반응형 시스템

### 8-1. 브레이크포인트

| 기준 | 화면 | 변화 |
|------|------|------|
| 기본 | > 900px | 데스크탑 풀 레이아웃 |
| 태블릿 | ≤ 900px | 헤더 패딩 축소, 조직도 2×2 그리드, 가치배지 줄바꿈 |
| 모바일 | ≤ 600px | 로고 30px, 플로우 줄바꿈, 조직도 단일열 |

### 8-2. 태블릿 (≤ 900px)
```css
header { padding: 0 24px; }
.section-inner { padding: 44px 24px; }
.section-h1 { font-size: 30px; }
.org-branches { flex-wrap: wrap; }
.org-agent-wrap { flex: 0 0 calc(50% - 0px); }  /* 2×2 그리드 */
.org-agent-wrap::before, .org-agent-wrap::after { display: none; }  /* 연결선 숨김 */
```

### 8-3. 모바일 (≤ 600px)
```css
.section-h1 { font-size: 24px; }
.flow-row { flex-wrap: wrap; justify-content: center; gap: 8px; }
.flow-arrow { display: none; }
.org-agent-wrap { flex: 0 0 100%; }  /* 단일 열 */
```

### 8-4. 미처리 반응형 (다음 에이전트 작업 필요)
```
히어로 배지 (.hero-badge-row) 모바일 대응:
현재 flex-wrap 없음 → 600px 이하에서 배지 줄바꿈 추가 필요

추천 수정:
@media (max-width: 600px) {
  .hero-badge-row { flex-wrap: wrap; gap: 8px; }
  .hero-badge { flex: 0 0 calc(50% - 4px); font-size: 13px; padding: 12px 8px; }
  .hero-badge-arrow { display: none; }
}
```

---

## 9. 이미지 처리 규칙

### 9-1. 썸네일 (비디오 박스)
```css
.thumb-img {
  position: absolute; inset: 0;
  width: 100%; height: 100%;
  object-fit: cover;
  z-index: 1;
}
```
- 배경을 꽉 채우는 커버 방식
- `z-index: 1` — 비디오 배경 위, UI 요소 아래

### 9-2. 창업자 사진 (배경제거 이미지)
```css
.founder-avatar { width: 140px; height: 160px; overflow: visible; }
.founder-avatar img { object-fit: contain; object-position: bottom center; }
```
- 배경제거 PNG 사용 시 `overflow: visible` 필수 (이미지가 컨테이너 밖으로 나올 수 있음)
- `object-position: bottom center` — 하체가 카드 바닥에 닿도록 정렬

### 9-3. 에이전트 로봇 이미지 (배경제거)
```css
.agent-avatar { width: 130px; height: 130px; }
.agent-avatar img { object-fit: contain; }
```
- `object-fit: contain` — 로봇 전체 보이도록 비율 유지

---

## 10. 텍스처 & 배경 처리

### 10-1. Grain 텍스처 (body)
```css
body::before {
  content: '';
  position: fixed; inset: 0;
  z-index: 0; pointer-events: none;
  background-image: url("data:image/svg+xml,...");  /* SVG noise */
  background-size: 200px 200px;
  opacity: 1;
}
```
미세한 필름 그레인 효과로 온기감 추가. 제거 금지.

### 10-2. 헤더 블러
```css
header {
  background: rgba(245,239,228,0.92);
  backdrop-filter: blur(14px);
}
```

### 10-3. 비디오 박스 내 비네트
```css
.video-box::after {
  content: '';
  background: radial-gradient(ellipse at center, transparent 50%, rgba(140,110,70,0.15) 100%);
  z-index: 2;
}
```

---

## 11. 아이콘 시스템

### 11-1. 유니코드 이모지 (기본)
외부 아이콘 라이브러리 불필요. 이모지로 처리.
```
🎙 마이크 — 현장 발화
🛡 방패 — 증거 원장
⚙️ 톱니 — AI 구조화
📋 클립보드 — 운영 조치
⚡ 번개 — 빠른 판단
✓ 체크 — 승인 통제
```

### 11-2. SVG 인라인 아이콘 (Section 02 전용)
Section 02의 현장발화·증거원장 노드는 커스텀 SVG 사용.
색상: `#D86A23` (--orange), 배경: `#FDEBD8` (--orange-light)

```
마이크 SVG: viewBox="0 0 42 42" — 캡슐 바디 + 그릴 + 스탠드
방패+잠금 SVG: viewBox="0 0 42 42" — 방패 외곽 + 자물쇠 바디 + 열쇠구멍
```

---

## 12. 디자인 확장 가이드

### 12-1. 새 컴포넌트 추가 시 준수 규칙
1. 기존 CSS 변수(`--bg`, `--orange` 등)만 사용, 하드코딩 신규 색상 금지
2. `border-radius: 14px` (카드) 또는 `50px` (pill) 중 선택
3. 호버 시 `translateY(-4~5px)` + shadow 증가 패턴 유지
4. `transition: 0.22s var(--ease-out)` 이징 통일

### 12-2. 새 섹션 배경 결정 기준
```
홀수 섹션 → var(--bg) 또는 var(--bg-alt)
짝수 섹션 → var(--panel)
섹션 간 구분 → border-top: 1px solid rgba(205,186,159,0.4)
```

### 12-3. 강조 요소 사용 기준
- 섹션당 강조 요소는 1개만 (`active` 클래스 또는 오렌지 배경)
- 오렌지 강조가 여러 개면 시선이 분산됨

---

## 13. 체크리스트 — 수정 후 검증

- [ ] 크림-웜 배경 톤 유지 (하얀색, 파란색, 어두운 색 없음)
- [ ] 오렌지 강조 요소가 섹션당 1개
- [ ] 모든 텍스트에 `word-break: keep-all` 적용
- [ ] 이미지 파일명 공백 → `%20` 인코딩
- [ ] 확정 카피 변경 없음
- [ ] 금지 표현 미포함
- [ ] 외부 CSS 라이브러리 미추가
- [ ] 900px·600px 브레이크포인트 대응 확인
- [ ] 파형 애니메이션 정상 작동
- [ ] 헤더 고정 + 스크롤 시 shadow 변화 정상
