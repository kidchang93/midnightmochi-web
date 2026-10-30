# CODE_STYLE — midnightmochi-web

## HTML

| 규칙 | 예시 (index.html) |
|------|-------------------|
| 들여쓰기 2칸 | 전체 |
| 섹션은 `<section id="영문" class="wrap">` + `.sec-head` | `<section id="works" class="wrap">` |
| 섹션 머리: 영문 이탤릭 `.kicker` + 한국어 `h2` | `<p class="kicker">Works</p><h2>만든 것들</h2>` |
| 장식 이미지는 `alt=""`, 의미 있는 이미지는 한국어 alt | `<img src="logo.svg" alt="">`, `alt="케어테이블 진료 리포트 화면"` |
| 이미지에 `width`·`height` 명시, 스크린샷은 `loading="lazy"` | `width="560" height="1213" loading="lazy"` |
| 외부 링크는 새 탭 + `rel="noopener"` | `target="_blank" rel="noopener"` |
| 날짜는 `<time datetime>` | `<time datetime="2026-10-29">10.29</time>` |
| 삽입 지점 주석은 한국어 | `<!-- 새 프로젝트는 이 아래, 최신순으로 추가한다 -->` |

## CSS

| 규칙 | 예시 |
|------|------|
| 클래스명은 짧은 영문 소문자, 두 단어는 하이픈 | `.hero-grid` `.sec-head` `.work-lead` `.contact-card` |
| 변형은 클래스를 덧붙인다 (BEM 안 씀) | `.btn.primary` `.btn.ghost` `.btn.sm`, `.work.feature` `.work.next`, `.status.live` `.status.wip` |
| 색은 `var(--토큰)` 만. 새 색이 필요하면 `:root` 에 먼저 추가 | `color: var(--muted)` |
| 블록 주석은 영문 섹션 이름 | `/* hero */` `/* works */` |
| 반응형은 파일 끝 `@media (max-width: 900px)` / `560px` 두 곳에 모은다 | — |
| 크기 조절은 `clamp()` | `font-size: clamp(30px, 4vw, 44px)` |

## JS

- 인라인 `<script>` 하나, 라이브러리 없음. `const`, 화살표 함수, 템플릿 문자열.
- DOM 이 없어도 페이지가 동작해야 한다 (JS 는 장식·등장 효과만).

## SVG 자산

- `viewBox` 기반, 고정 픽셀 크기 없음. `role="img"` + 한국어 `aria-label`.

## 금지

- 프레임워크·번들러·빌드 단계 도입
- 폰트 CDN 두 개(Pretendard, Fraunces) 외 외부 스크립트·스타일
- `:root` 토큰 밖의 하드코딩 색 추가 (기존 예외: `.status.live` 의 `#9BE3B5`, `.shots img` 테두리 `#1A1F3F`)
- 라이트 테마 추가
- 공개 금지 정보(상세 주소·휴대폰·계약 문서) 기재
