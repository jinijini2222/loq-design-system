# LOQ 상세페이지 디자인 시스템 (코드)

게이밍 노트북 상세페이지(레노버 LOQ Essential 15IPH11E)용 다크 + 바이올렛 그라데이션 디자인 시스템. **가로 860px 고정**, 서체는 **SUIT Variable** 한 가족.

## 구조

| 경로 | 내용 |
|---|---|
| `tokens/tokens.json` | 원본 토큰(색·타입·간격·반경·모서리 컷·레이아웃·그라데이션·그림자, 항목마다 usage) |
| `tokens/tokens.css` | 위 토큰의 CSS 변수(`--violet-500` 등), 타입 스타일 클래스(`.display`, `.body-lg` …), `@font-face` |
| `components/loq.css` | 컴포넌트 스타일(`.loq-*` 클래스). 토큰 변수만 참조 |
| `components/*.html` | 컴포넌트별 예시 마크업. 파일 맨 위 주석이 사용 가이드 |
| `index.html` | 전체 컴포넌트 미리보기 |
| `fonts/SUIT-Variable.woff2` | SUIT Variable(100–900), SIL OFL |
| `reference/` | 원본 상세페이지 화면(01–08 시안 JPG, 09–13 원본 PSD 섹션) |
| `GUIDELINES.md` | 사용 규칙(그리드·색·타입·형태·섹션 레시피·카피·금지) |
| `PROMPT.md` | 다른 AI에 붙여 넣는 생성용 프롬프트 |

## 사용

```html
<link rel="stylesheet" href="tokens/tokens.css">
<link rel="stylesheet" href="components/loq.css">
<body class="loq">
  <div class="loq-canvas">
    <section class="loq-section">
      <div class="loq-divider">…엠블럼 SVG…</div>
      <header class="loq-head">
        <span class="loq-tag tag">Cooler</span>
        <h2 class="loq-head__title display"><span>강력한 쿨링</span><span class="loq-grad">흔들림 없는 퍼포먼스</span></h2>
        <p class="loq-head__body body-lg">본문 …</p>
      </header>
      <div class="loq-wrap">…카드·차트…</div>
    </section>
  </div>
</body>
```

## 핵심 규칙

- 캔버스 860, 좌우 여백 49, 콘텐츠 762. 2열 375 + 12 + 375, 세로 스택 10.
- 섹션 간격: 경계 → 125 → 태그 → 35 → 헤드라인 → 30 → 본문 → 50 → 비주얼 → 120.
- 헤드라인은 2줄: 1줄 흰색, 2줄 `gradient-headline`(#9f6ee9 → #fba0e2). 그라데이션은 면·버튼·배경에 쓰지 않는다.
- 카드는 둥글리지 않고 좌상단·우하단 18px 컷(`.loq-cut`), 면 `gradient-card`, 1px `gradient-edge`.
- 거의 모든 텍스트 자간 -0.05em. 본문 24/38 Medium #cfcfcf, 강조 SemiBold 흰색.
- 히어로·그래픽·서포트 섹션 값은 시안 JPG 기준(토큰 usage에 표시), 나머지는 원본 PSD 실측.
