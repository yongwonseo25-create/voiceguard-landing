# VoiceGuard 랜딩페이지 에이전트 핸드오프 문서 v2.0

> **작성일:** 2026-05-08  
> **작업 완료 기준 브랜치:** `master`  
> **GitHub:** https://github.com/yongwonseo25-create/voiceguard-landing  
> **대상 파일:** `D:\Voice Gusrd_OS\모두의창업_랜딩페이지_VoiceGuard.html`  
> **이 문서의 목적:** 다음 에이전트가 현재 상태를 완벽히 파악하고 즉시 작업을 이어받을 수 있도록 한다.

---

## 1. 제품 핵심 맥락 (절대 변경 금지)

```
VoiceGuard는 STT 앱이 아니다.
VoiceGuard는 요양보호사의 현장 발화를 먼저 증거 원장에 선저장하고,
AI 구조화 후 운영 조치로 연결하는 CareOps 운영·증빙 플랫폼이다.
```

**발표 맥락:** 모두의 창업 대회 심사위원 대상. 30초 안에 "STT 앱이 아닌 증빙 플랫폼"을 설득해야 함.

---

## 2. 파일 구조 (현재 상태 확정)

```
D:\Voice Gusrd_OS\
├── 모두의창업_랜딩페이지_VoiceGuard.html   ← 메인 작업 파일 (단일 HTML)
├── 모두의창업_최종제출서_VoiceGuard.html   ← 별도 제출서 (건드리지 않음)
└── public/
    ├── logo.png                            ← 헤더·푸터 로고
    ├── hero_image.png                      ← Section 01 비디오박스 썸네일 (요양보호사+어르신)
    ├── 2번 thumbnail.png                   ← Section 02 데모비디오박스 썸네일
    ├── 대표.png                            ← Section 03 창업자 사진 (배경제거 완료)
    ├── 전략기획 에이전트.png               ← Section 03 에이전트①로봇 (배경제거 완료)
    ├── 리서치 에이전트.png                 ← Section 03 에이전트②로봇 (배경제거 완료)
    ├── 제작운영 에이전트.png               ← Section 03 에이전트③로봇 (배경제거 완료)
    ├── 검수 에이전트.png                   ← Section 03 에이전트④로봇 (배경제거 완료)
    ├── 조직도.png                          ← 디자인 레퍼런스 이미지 (실제 사용 안 함)
    ├── new here image.png                  ← Section 01 배지 디자인 레퍼런스
    └── (기타 md 기획서 파일들)
```

> **중요:** HTML에서 공백 포함 파일명은 URL 인코딩 필수  
> 예: `전략기획 에이전트.png` → `public/전략기획%20에이전트.png`

---

## 3. 디자인 시스템 (CSS 변수 — `:root` 정의)

```css
--bg:           #F5EFE4;    /* 전체 배경 크림 웜 */
--bg-alt:       #EFE8DA;    /* Section 02 배경 */
--panel:        #FAF5EC;    /* Section 03 배경 */
--card:         #FFF9F1;    /* 카드·노드 배경 */
--card-hover:   #FFFCF5;    /* 카드 호버 배경 */
--orange:       #D86A23;    /* 포인트 오렌지 (강조, 버튼, 활성 상태) */
--orange-deep:  #C95C18;    /* 딥 오렌지 (버튼 그라디언트 시작) */
--orange-light: #FDEBD8;    /* 연한 오렌지 (활성 카드 배경) */
--orange-glow:  rgba(216,106,35,0.18);
--brown:        #8A6A4A;    /* 브라운 (창업자 카드 테두리, 화살표) */
--border:       #CDBA9F;    /* 기본 테두리 */
--border-hover: #D86A23;    /* 호버 시 테두리 */
--text:         #201A16;    /* 본문 텍스트 */
--text-sub:     #7B6A5B;    /* 보조 텍스트 */
--header-h:     100px;      /* 헤더 높이 (섹션 padding-top에 사용) */
--max-w:        1200px;
--ease-out:     cubic-bezier(0.22, 1, 0.36, 1);
```

**폰트:** `Noto Sans KR` (Google Fonts CDN, 400/500/600/700/800)

---

## 4. 각 섹션 현재 상태 상세

### Section 01 — HERO (`#section-01`)

**현재 구현 상태: 완료**

| 요소 | 상태 | 세부 |
|------|------|------|
| 메인 카피 | ✅ 완료 | "돌봄 현장의 말이 운영 증거가 됩니다" |
| 서브 카피 | ✅ 완료 | "요양보호사의 현장 발화를 구조화해..." |
| 비디오 박스 | ✅ 완료 | `hero_image.png` 썸네일, 플레이 버튼, 파형 애니메이션, max-width 880px |
| 4개 배지 | ✅ 완료 (최신) | pill 스타일, 880px 폭 정렬, flex:1 균등 배치 |

**배지 구조 (CSS 클래스: `.hero-badge-row` → `.hero-badge`):**
```html
<div class="hero-badge-row" id="hero-flow">
  <div class="hero-badge">🎙 현장 발화</div>
  <span class="hero-badge-arrow">→</span>
  <div class="hero-badge active">🛡 증거 원장</div>  <!-- 주황 강조 -->
  <span class="hero-badge-arrow">→</span>
  <div class="hero-badge">⚙️ AI 구조화</div>
  <span class="hero-badge-arrow">→</span>
  <div class="hero-badge">📋 운영 조치</div>
</div>
```

**배지 CSS 핵심:**
```css
.hero-badge-row { display:flex; width:100%; max-width:880px; margin:0 auto; }
.hero-badge { flex:1; padding:16px 10px; border-radius:50px; font-size:16px; font-weight:700; }
.hero-badge.active { background:var(--orange-light); border-color:var(--orange); color:var(--orange); }
```

---

### Section 02 — DEMO FLOW (`#section-02`)

**현재 구현 상태: 완료 (이번 세션에서 수정 없음)**

| 요소 | 상태 | 세부 |
|------|------|------|
| 메인 카피 | ✅ 완료 | "말하면, 먼저 증거 원장에 저장됩니다" |
| 서브 카피 | ✅ 완료 | "원본은 먼저 증거 원장에 저장되고..." |
| 데모 비디오 박스 | ✅ 완료 | `2번%20thumbnail.png`, max-width 760px |
| 4개 노드 플로우 | ✅ 완료 | `.flow-row` + `.node` 카드 스타일 (Section 01과 다름!) |
| 스텝 인디케이터 | ✅ 완료 | `.step-bar` / `.step-item.on` 강조 |
| 핵심 문장 | ✅ 완료 | "⭐ 핵심: 말하면, 먼저 증거가 됩니다." |

> **주의:** Section 02의 4노드는 `node` 클래스의 **카드 스타일**이고, Section 01의 배지는 `hero-badge` 클래스의 **pill 스타일**로 서로 다른 컴포넌트다. 혼동 금지.

---

### Section 03 — TEAM SYSTEM (`#section-03`)

**현재 구현 상태: 완료 (이번 세션에서 이미지 교체)**

| 요소 | 상태 | 세부 |
|------|------|------|
| 메인 카피 | ✅ 완료 | "사람은 한 명, 실행은 팀 단위입니다" |
| 서브 카피 | ✅ 완료 | "대표는 방향과 최종 승인을 맡고..." |
| 창업자 카드 | ✅ 완료 | `대표.png` 140×160px, `founder-card` 클래스 |
| 4개 에이전트 카드 | ✅ 완료 | 각 로봇 이미지 130×130px, 텍스트 유지 |
| 가치 배지 3종 | ✅ 완료 | 빠른판단/병렬실행/승인통제 |

**조직도 구조 (HTML):**
```
.org-tree
  └── .founder-card  (창업자 / 대표.png)
  └── .org-trunk  (세로 연결선 2px)
  └── .org-branches (flex row)
        ├── .org-agent-wrap → .agent-card (전략기획%20에이전트.png)
        ├── .org-agent-wrap → .agent-card (리서치%20에이전트.png)
        ├── .org-agent-wrap → .agent-card (제작운영%20에이전트.png)
        └── .org-agent-wrap → .agent-card (검수%20에이전트.png)
```

**에이전트 이미지 매핑 (역할↔파일명 완전 확정):**
| 역할 | 파일명 (URL 인코딩) | 로봇 특징 |
|------|---------------------|-----------|
| 전략기획 실장 에이전트 | `public/전략기획%20에이전트.png` | 태블릿+그래프 차트 들고 있음 |
| 리서치 분석 에이전트 | `public/리서치%20에이전트.png` | 돋보기+분석 화면 들고 있음 |
| 제작운영 에이전트 | `public/제작운영%20에이전트.png` | 노트북 사용 중 |
| 검수관리 에이전트 | `public/검수%20에이전트.png` | 체크리스트 클립보드 들고 있음 |

---

## 5. 전체 CSS 클래스 맵 (주요 컴포넌트)

| 클래스 | 위치 | 설명 |
|--------|------|------|
| `.section` | 전체 | 섹션 기본 (min-height:100vh, flex center) |
| `.section-inner` | 전체 | max-width:1200px, padding:60px 56px |
| `.badge` | 전체 | 섹션 번호 원형 뱃지 (01/02/03) |
| `.btn-demo` | 헤더 | CTA 버튼 오렌지 그라디언트 |
| `.video-frame-outer` | S01 | 비디오 박스 외부 프레임 (880px) |
| `.video-box` | S01 | 16:9 비율 썸네일 컨테이너 |
| `.thumb-img` | S01/S02 | 비디오 박스 내 썸네일 이미지 |
| `.play-btn` | S01 | 80px 원형 플레이 버튼 |
| `.waveform` / `.wbar` | S01/S02 | 파형 애니메이션 |
| `.hero-badge-row` | S01 | 배지 4개 컨테이너 (880px, flex) |
| `.hero-badge` | S01 | pill 배지 개별 아이템 (flex:1) |
| `.hero-badge.active` | S01 | 활성 배지 (주황 강조) |
| `.hero-badge-arrow` | S01 | 배지 사이 화살표 |
| `.demo-frame-outer` | S02 | 데모 비디오 박스 외부 (760px) |
| `.flow-row` | S02 | 4노드 가로 배열 컨테이너 |
| `.node` | S02 | 플로우 카드 노드 |
| `.node.active` | S02 | 강조 노드 (증거 원장) |
| `.step-bar` | S02 | 하단 스텝 인디케이터 바 |
| `.step-item.on` | S02 | 활성 스텝 아이템 |
| `.org-tree` | S03 | 조직도 전체 컨테이너 |
| `.founder-card` | S03 | 창업자 카드 (브라운 테두리) |
| `.founder-avatar` | S03 | 창업자 이미지 영역 (140×160px) |
| `.org-trunk` | S03 | 수직 연결선 |
| `.org-branches` | S03 | 에이전트 4카드 가로 배열 |
| `.org-agent-wrap` | S03 | 에이전트 개별 슬롯 (::before/::after 연결선) |
| `.agent-card` | S03 | 에이전트 카드 |
| `.agent-avatar` | S03 | 에이전트 이미지 영역 (130×130px) |
| `.values-row` | S03 | 하단 가치 배지 3종 가로 배열 |
| `.value-card` | S03 | 가치 배지 개별 카드 |

---

## 6. 반응형 브레이크포인트

| 브레이크포인트 | 변화 내용 |
|----------------|-----------|
| `≤ 900px` (태블릿) | 헤더 패딩 축소, Section03 조직도 2×2 그리드, values-row 줄바꿈 |
| `≤ 600px` (모바일) | 로고 30px, Section01/02 flow-row 줄바꿈, 조직도 단일 열 |

> **현재 미처리:** `hero-badge-row`의 모바일 대응 (600px 이하에서 배지가 줄바꿈되면 레이아웃 깨질 수 있음) — 필요 시 다음 에이전트가 처리

---

## 7. 금지 표현 (절대 위반 금지)

| 금지 | 이유 |
|------|------|
| "STT 앱", "음성인식 앱", "녹취", "회의록" | 제품 정체성 훼손 |
| "변경 이력", "수정 이력", "편집 가능" | 증거 원장의 불변성 훼손 |
| "AI가 다 합니다", "무인 회사", "완전 자동" | 심사위원 신뢰 저하 |
| "Codex", "Gemini", "ChatGPT", "Claude" | 도구명 노출 금지 |
| "666억", "11만명" 등 미검증 수치 | 근거 없는 과장 |
| 사이버펑크, 파란 네온, 어두운 배경 | 디자인 톤 위배 |

---

## 8. GitHub 정보

| 항목 | 값 |
|------|-----|
| 레포 URL | https://github.com/yongwonseo25-create/voiceguard-landing |
| 계정 | yongwonseo25-create |
| 브랜치 | master |
| 최신 커밋 | `feat: 랜딩페이지 UI 개선 - 배지 스타일 및 조직도 이미지 교체` |
| 원격 이름 | origin |
| 커밋 방법 | `git add 파일명` → `git commit -m "메시지"` → `git push origin master` |

---

## 9. 이번 세션에서 완료한 작업 목록

1. **Section 01 히어로 배지 교체**  
   - 기존: `.node` 카드 4개 (큰 사각 박스)  
   - 변경: `.hero-badge` pill 스타일 4개 (880px 폭 균등 배치, flex:1)  
   - 레퍼런스: `public/new here image.png`

2. **Section 03 조직도 이미지 교체**  
   - 창업자: 👤 이모지 → `대표.png` (배경제거 실사진)  
   - 에이전트 4종: 이모지 → 역할별 로봇 이미지 (배경제거)  
   - 에이전트 아바타 크기: 90px → 130px  
   - 창업자 아바타: 원형 76px → 직사각 140×160px (전신 표시)

3. **GitHub 최초 커밋 및 푸시**  
   - git init → 첫 커밋 → gh repo create → push 완료

---

## 10. 다음 에이전트 가능 작업 (우선순위순)

| 순위 | 작업 | 위치 | 세부 |
|------|------|------|------|
| 1 | 모바일 배지 반응형 처리 | CSS `@media (max-width:600px)` | `.hero-badge-row`에 `flex-wrap:wrap` + 배지 최소 너비 설정 |
| 2 | 실제 영상 연결 | S01 `.video-box`, S02 `.demo-video-box` | 현재 플레이 버튼 클릭 시 4초 후 자동 복귀. 실제 `<video>` 태그 또는 유튜브 임베드로 교체 필요 |
| 3 | 스크롤 애니메이션 추가 | 전 섹션 | IntersectionObserver로 카드 fade-in 효과 |
| 4 | 메타태그 SEO 보강 | `<head>` | og:image, description, title 최적화 |
| 5 | GitHub Pages 배포 | 레포 설정 | Settings → Pages → main/master 브랜치 root 설정 |

---

## 11. 작업 시 주의사항

1. **파일명 공백 처리:** `public/` 내 에이전트 이미지 파일명에 공백 있음 → HTML 내 항상 `%20` 인코딩 사용
2. **단일 HTML 파일:** 외부 JS/CSS 파일 없음. 모든 스타일과 스크립트가 `<style>`, `<script>` 태그 내에 인라인으로 존재
3. **Section 01 vs Section 02 노드 스타일:** 같아 보이지만 다른 컴포넌트. S01=`.hero-badge`, S02=`.node`. 혼동하면 스타일 충돌
4. **메인/서브 카피 절대 변경 금지:** 모든 섹션의 메인 카피와 서브 카피는 확정 텍스트. 대표의 명시적 지시 없이 수정 금지
5. **이미지 교체 시:** `public/` 폴더 내 파일명 확인 후 HTML 경로 정확히 일치시킬 것

---

> **이 문서는 `D:\Voice Gusrd_OS\HANDOFF_랜딩페이지_VoiceGuard_v2.md` 에 저장됨**  
> **다음 세션 시작 시 이 문서를 먼저 읽고 작업을 시작할 것**
