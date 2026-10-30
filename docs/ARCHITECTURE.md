# ARCHITECTURE — midnightmochi-web

빌드 없는 정적 원페이지. 서버·데이터베이스·API 없음. GitHub Pages 가 파일을 그대로 서빙한다.

## 파일 구조

```
midnightmochi-web/
├── index.html      페이지 전체: <head> 메타 + 인라인 <style> + 본문 + 인라인 <script>
├── logo.svg        페이지 안 일러스트(달을 올려다보는 찹쌀떡) — 투명 배경
├── favicon.svg     브라우저 탭 아이콘 — 남색 둥근 사각형 위 회사 로고
├── og.png          링크 공유 미리보기 (1200×630)
├── img/            포트폴리오 스크린샷 (가로 560px JPG)
├── CNAME           커스텀 도메인 midnight-mochi.com
└── .nojekyll       GitHub Pages 의 Jekyll 처리 끄기
```

## index.html 안의 층

| 층 | 위치 | 내용 |
|----|------|------|
| 메타 | `<head>` | title·description, `theme-color`, Open Graph(`og:image` 는 절대 URL), canonical, `rel="icon"` → `favicon.svg` |
| 폰트 | `<head>` `<link>` | Pretendard(jsDelivr), Fraunces(Google Fonts) — 외부 의존성은 이 둘뿐 |
| 스타일 | `<style>` | `:root` 디자인 토큰 → 공통(`.wrap` `.btn` `.card`) → 섹션별 블록 → 반응형(900px·560px) → `prefers-reduced-motion` |
| 본문 | `<body>` | `header.top` → `main#top` 안 섹션 순서: `.hero` · `#about` · `#services` · `#works` · `#history` · `#maker` · `#contact` → `footer` |
| 스크립트 | `<script>` 끝 | `html.js` 클래스 추가 · `.sky` 에 별 70개 생성 · `IntersectionObserver` 로 `.reveal` 에 `.in` 부여 |

## 자산 사용처

| 자산 | 쓰는 곳 |
|------|---------|
| `logo.svg` | 헤더 브랜드(40px), 히어로 `.mochi`(440px, squish 애니메이션), 만든 것들 마지막 `.work.next` 카드(72px), 문의 카드(120px), 푸터(32px) |
| `favicon.svg` | `<link rel="icon">` 한 곳 |
| `og.png` | `og:image` (`https://midnight-mochi.com/og.png`) |
| `img/*.jpg` | `.work.feature` 의 `.shots` |

## 외부 연결

| 대상 | 방식 |
|------|------|
| 호스팅 | GitHub Pages — `main` push 가 곧 배포 |
| 도메인 | AWS Route 53 (`midnight-mochi.com`, apex A 4개 + www CNAME) |
| 검색 | Google Search Console 도메인 속성 (Route 53 apex TXT 로 소유권 확인) |
| 문의 | `mailto:` 링크만. 폼·백엔드 없음 |
| 외부 링크 | `target="_blank" rel="noopener"` |
