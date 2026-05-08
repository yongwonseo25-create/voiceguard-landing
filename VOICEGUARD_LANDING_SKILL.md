# VoiceGuard 랜딩페이지 스킬 (Agent Skill)

> **스킬 이름:** `voiceguard-landing`  
> **적용 파일:** `모두의창업_랜딩페이지_VoiceGuard.html`  
> **GitHub:** https://github.com/yongwonseo25-create/voiceguard-landing  
> **스킬 목적:** 이 랜딩페이지를 수정·확장할 때 에이전트가 따라야 할 패턴, 금지사항, 작업 절차를 명확히 정의한다.

---

## 1. 이 스킬을 언제 사용하는가

다음 요청이 들어오면 이 스킬을 즉시 활성화한다:

- "랜딩페이지 수정해줘"
- "섹션 추가해줘 / 바꿔줘"
- "카피 바꿔줘"
- "이미지 교체해줘"
- "VoiceGuard 랜딩 작업"
- "배지 / 노드 / 카드 수정"
- "조직도 수정"

---

## 2. 작업 전 필수 확인 절차

### Step 1 — 파일 읽기
```
Read: D:\Voice Gusrd_OS\모두의창업_랜딩페이지_VoiceGuard.html
```

### Step 2 — 이미지 에셋 확인
```
Bash: ls "D:\Voice Gusrd_OS\public"
```

### Step 3 — 작업 범위 확인
사용자에게 정확히 무엇을 바꾸는지 한 문장으로 컨펌받은 뒤 작업 시작.

---

## 3. 핵심 규칙 (절대 위반 금지)

### 3-1. 카피 수정 금지
아래 텍스트는 확정 카피다. 명시적 지시 없이 절대 변경하지 않는다.

| 섹션 | 메인 카피 | 서브 카피 |
|------|-----------|-----------|
| S01 | 돌봄 현장의 말이 운영 증거가 됩니다 | 요양보호사의 현장 발화를 구조화해 증거 원장과 운영 대시보드로 연결합니다. |
| S02 | 말하면, 먼저 증거 원장에 저장됩니다 | 원본은 먼저 증거 원장에 저장되고, AI 구조화 후 담당자 확인을 거쳐 운영 조치로 이어집니다. |
| S03 | 사람은 한 명, 실행은 팀 단위입니다 | 대표는 방향과 최종 승인을 맡고, 역할별 AI 에이전트가 리서치·기획·제작·검수를 분담합니다. |

### 3-2. 절대 금지 표현
```
❌ STT 앱, 음성인식 앱, 녹취, 회의록
❌ 변경 이력, 수정 이력, 편집 가능
❌ AI가 다 합니다, 무인 회사, 완전 자동
❌ Codex, Gemini, ChatGPT, Claude (도구명 노출)
❌ 사이버펑크, 파란 네온, 어두운 배경
❌ 666억, 11만명 등 미검증 수치
```

### 3-3. 디자인 톤 고정
- 배경: 크림-웜 톤 (`#F5EFE4` 계열)
- 강조: 오렌지 (`#D86A23`)
- 폰트: Noto Sans KR (Google Fonts)
- 외부 CSS 라이브러리 추가 금지 (Tailwind, Bootstrap 등)

---

## 4. 파일 구조 규칙

### 4-1. 단일 HTML 파일 원칙
모든 CSS와 JS는 `<style>`, `<script>` 태그 안에 인라인으로 유지.  
별도 `.css` 또는 `.js` 파일 생성 금지.

### 4-2. 이미지 경로 규칙
```
모든 이미지는 public/ 폴더에 위치
파일명에 공백이 있으면 반드시 %20으로 인코딩

예시:
✅ src="public/대표.png"
✅ src="public/전략기획%20에이전트.png"
❌ src="public/전략기획 에이전트.png"  ← 브라우저에서 깨짐
```

### 4-3. 현재 이미지 에셋 목록
| 파일명 | 용도 | 위치 |
|--------|------|------|
| `logo.png` | 헤더·푸터 로고 | 헤더, 푸터 |
| `hero_image.png` | S01 비디오박스 썸네일 | S01 `.thumb-img` |
| `2번 thumbnail.png` | S02 데모박스 썸네일 | S02 `.thumb-img` |
| `대표.png` | 창업자 사진 (배경제거) | S03 `.founder-avatar img` |
| `전략기획 에이전트.png` | 전략기획 로봇 (배경제거) | S03 `.agent-avatar img` |
| `리서치 에이전트.png` | 리서치 로봇 (배경제거) | S03 `.agent-avatar img` |
| `제작운영 에이전트.png` | 제작운영 로봇 (배경제거) | S03 `.agent-avatar img` |
| `검수 에이전트.png` | 검수관리 로봇 (배경제거) | S03 `.agent-avatar img` |

---

## 5. 컴포넌트 사용 패턴

### 5-1. 섹션 배지 (번호 뱃지)
```html
<div class="badge">01</div>
```

### 5-2. 히어로 pill 배지 (Section 01 전용)
```html
<div class="hero-badge-row">
  <div class="hero-badge">
    <span class="hero-badge-icon">🎙</span>
    현장 발화
  </div>
  <span class="hero-badge-arrow">→</span>
  <div class="hero-badge active">   <!-- active = 주황 강조 -->
    <span class="hero-badge-icon">🛡</span>
    증거 원장
  </div>
  <!-- ... 동일 패턴 반복 -->
</div>
```

### 5-3. 플로우 노드 카드 (Section 02 전용)
```html
<div class="flow-row">
  <div class="node">                 <!-- 기본 노드 -->
    <span class="node-icon">🎙</span>
    <div class="node-label">현장 발화</div>
    <div class="node-desc">말하면 시작</div>
  </div>
  <div class="flow-arrow">
    <span class="flow-arrow-icon">→</span>
    <span class="flow-arrow-dot"></span>
  </div>
  <div class="node active">          <!-- 강조 노드 -->
    <!-- SVG 아이콘 또는 이모지 -->
    <div class="node-label">증거 원장 선저장</div>
    <div class="node-desc">원본 먼저 저장</div>
  </div>
</div>
```

### 5-4. 조직도 에이전트 카드 (Section 03 전용)
```html
<div class="org-agent-wrap">
  <div class="agent-card">
    <div class="agent-avatar">
      <img src="public/전략기획%20에이전트.png" alt="전략기획 에이전트">
    </div>
    <div class="agent-name">전략기획<br>실장 에이전트</div>
    <div class="agent-desc">우선순위 정리<br>핵심 메시지 설계</div>
  </div>
</div>
```

### 5-5. 가치 배지 카드 (Section 03 하단)
```html
<div class="values-row">
  <div class="value-card">
    <span class="value-icon">⚡</span>
    <div class="value-title">빠른 판단</div>
    <div class="value-desc">AI로 실행하는 작은 인텔리전스</div>
  </div>
</div>
```

### 5-6. 파형 애니메이션
```html
<div class="waveform">
  <div class="wbar"></div>
  <div class="wbar"></div>
  <div class="wbar"></div>
  <div class="wbar"></div>
  <div class="wbar"></div>
  <div class="wbar"></div>
  <div class="wbar"></div>
  <div class="wbar"></div>
</div>
```

---

## 6. 새 섹션 추가 시 체크리스트

새 섹션(S04 이상)을 추가할 때 반드시 아래를 모두 충족해야 한다:

- [ ] `<section class="section section-04" id="section-04">` 구조 사용
- [ ] `<div class="badge">04</div>` 번호 배지 포함
- [ ] 배경: `var(--bg)` 또는 `var(--panel)` 중 선택 (새 색상 추가 금지)
- [ ] 카피: 확정 후 수정 금지 원칙 적용
- [ ] 반응형: `@media (max-width:900px)`, `@media (max-width:600px)` 블록에 해당 섹션 대응 추가
- [ ] 헤더 네비게이션 링크 추가 (현재 CTA 버튼은 S02 링크 고정)

---

## 7. 이미지 교체 시 절차

1. `ls "D:\Voice Gusrd_OS\public"` 로 새 파일명 확인
2. 파일명에 공백 있으면 `%20` 인코딩 계획
3. HTML에서 해당 `src=` 속성만 교체 (주변 구조 건드리지 않음)
4. 이미지 크기 규칙 확인:
   - 창업자(`.founder-avatar`): `140×160px`, `object-fit: contain`
   - 에이전트(`.agent-avatar`): `130×130px`, `object-fit: contain`
   - 비디오 썸네일(`.thumb-img`): `100% × 100%`, `object-fit: cover`

---

## 8. Git 작업 절차

```bash
# 1. 스테이징 (관련 파일만 명시적으로 추가)
git add 모두의창업_랜딩페이지_VoiceGuard.html

# 2. 이미지도 추가한 경우
git add "public/파일명.png"

# 3. 커밋 (co-author 필수)
git commit -m "$(cat <<'EOF'
feat: 작업 내용 한 줄 요약

- 변경사항 1
- 변경사항 2

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>
EOF
)"

# 4. 푸시
git push origin master
```

---

## 9. 작업 완료 후 반드시 할 일

1. 핸드오프 문서(`HANDOFF_랜딩페이지_VoiceGuard_v2.md`) 업데이트
2. 변경된 섹션, 클래스, 이미지 정보 반영
3. GitHub 푸시 확인
