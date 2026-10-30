# DESIGN — midnightmochi-web

## 설계 원칙

| 원칙 | 코드에서의 모습 | 이유 |
|------|----------------|------|
| 빌드 없음 | HTML 한 장에 CSS·JS 인라인 | push 만으로 배포. 1인 운영이라 도구 유지비를 없앤다 |
| 밤하늘 테마 하나 | `color-scheme: dark`, 라이트 모드 없음 | 브랜드("Midnight")가 곧 테마 |
| 색은 토큰만 | `:root` 의 `--bg` `--cream` `--moon` `--blush` `--muted` `--ink` 등 | 색이 흩어지지 않게 |
| JS 없어도 내용이 보임 | `.reveal` 숨김은 `.js .reveal` 에만 걸림 | 점진적 향상 |
| 모션은 끌 수 있음 | `prefers-reduced-motion` 에서 animation·transition 전부 끔 | 접근성 |
| 한국어 줄바꿈 | `word-break: keep-all` | 어절 단위로 끊기게 |

## 콘텐츠 규칙

- 포트폴리오(만든 것들)·연혁(걸어온 길)은 **상위 폴더 프로젝트의 실제 이정표**만 쓴다. 근거: `../docs/미드나잇모찌_회사소개서.docx`, 각 프로젝트 git log·docs.
- 공개 저장소다. 상세 주소(동·호수)·개인 휴대폰 번호·계약서·견적서·서명은 넣지 않는다. 푸터 주소는 `서울특별시 동작구` 까지만.
- 고객사 이름·범위는 회사소개서에 공개한 수준까지만.

## 새 콘텐츠 추가 패턴

| 추가할 것 | 위치 | 복사할 마크업 |
|-----------|------|---------------|
| 포트폴리오 | `<!-- 새 프로젝트는 이 아래, 최신순으로 추가한다 -->` 바로 아래 | `<article class="card work reveal">` (대표작만 `work feature`) |
| 상태 배지 | `.tags` 안 | `status live`(운영 중) / `status wip`(진행 중) / 완료는 배지 없음 |
| 연혁 | `<!-- 새 연혁은 해당 연도 바로 아래 … -->` 아래 해당 `<li class="year">` 다음 | `<li><time datetime="YYYY-MM-DD">MM.DD</time><p><b>…</b><span>…</span></p></li>` |
| 스크린샷 | `img/` | `sips -s format jpeg -s formatOptions 85 --resampleWidth 840 원본.png --out img/이름.jpg` (케어테이블 원본: `../../kcal/marketing/appstore-screenshots/`) |

## 브랜드 자산

- 회사 로고는 2026-10-30 확정한 **'달이 뜬 찹쌀떡'**(얼굴 없는 떡 실루엣 + 금색 초승달 창). 원본 SVG 는 상위 폴더 `../docs/로고/`.
- `favicon.svg` 는 이 회사 로고를 남색 둥근 사각형 위에 올린 것이다. 크림 떡 위 금색 달은 16px 에서 대비가 약해 사라지므로, 파비콘에서만 달을 금색 대신 **창으로 뚫어**(evenodd) 남색 바탕이 비치게 했다.
- `logo.svg` 는 같은 로고의 어두운 바탕용(크림 떡 + 금색 달)을 512 정사각 틀에 넣은 것. 떡 아래 끝이 틀의 약 80% 라 히어로 squish 의 `transform-origin: 50% 80%` 와 맞는다. 2026-10-30 이전의 얼굴 있는 찹쌀떡 일러스트를 대체했다.
