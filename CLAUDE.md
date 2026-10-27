# midnightmochi-web — 미드나잇모찌 회사 홈페이지

미드나잇모찌(1인 소프트웨어 스튜디오)의 회사 소개 원페이지. 빌드 없는 정적 HTML 한 장이다.
상위 폴더(`../`)에 쌓이는 프로젝트가 이 페이지의 **포트폴리오(만든 것들)·연혁(걸어온 길)** 이 된다.

## 파일

| 파일 | 내용 |
|------|------|
| `index.html` | 페이지 전체 (CSS·JS 인라인). 디자인 토큰은 `:root` 에 있다 |
| `logo.svg` | 로고 마크 (투명 배경, 달을 올려다보는 찹쌀떡) |
| `favicon.svg` | 남색 배경을 깐 로고 — 파비콘용 |
| `og.png` | 링크 공유 미리보기 이미지 (1200×630) |
| `img/` | 포트폴리오 스크린샷 (가로 560px JPG) |
| `CNAME` | GitHub Pages 커스텀 도메인 `midnightmochi.com` — DNS가 GitHub를 가리킨 뒤에 추가한다 (먼저 넣으면 github.io 주소도 그 도메인으로 넘어가 접속이 끊긴다) |

## 실행·배포

- 미리보기: `open index.html` (또는 `python3 -m http.server` 후 http://localhost:8000)
- 배포: GitHub Pages — `main` 에 push 하면 1~2분 뒤 반영된다. 별도 빌드 없음.

## 포트폴리오·연혁 추가

1. **만든 것들**: `index.html` 의 `<!-- 새 프로젝트는 이 아래, 최신순으로 추가한다 -->` 바로 아래에 `<article class="card work reveal">` 를 복사해 넣는다.
   - 대표작만 `work feature`(가로 전체·스크린샷 2장). 나머지는 `work` 카드.
   - 상태 배지: `status live`(운영 중) / `status wip`(진행 중). 완료는 배지 없이 기간만 적는다.
   - 스크린샷은 `sips -s format jpeg -s formatOptions 82 --resampleWidth 560 원본.png --out img/이름.jpg` 로 줄여 넣는다.
2. **걸어온 길**: `<!-- 새 연혁은 해당 연도 바로 아래 ... -->` 아래 `<ol class="timeline">` 의 해당 연도 `<li class="year">` 바로 다음에 최신순으로 넣는다. 새 해가 되면 `<li class="year">2027</li>` 를 맨 위에 추가.
3. 사실은 근거가 있는 것만 쓴다: `../docs/미드나잇모찌_회사소개서.docx`, 각 프로젝트 레포의 git log·docs.

## 규칙

- **공개 금지**: `../docs/` 의 계약서·견적서·서명 이미지·상세 주소(동·호수)·개인 휴대폰 번호는 이 폴더로 복사하거나 페이지에 쓰지 않는다. 이 폴더 전체가 공개 저장소다.
- 고객사 이름·범위는 회사소개서에 이미 공개한 수준까지만 적는다.
- 외부 의존성은 폰트 CDN 두 개(Pretendard, Fraunces)뿐이다. 프레임워크·빌드 도구를 들이지 않는다.
- 색은 `:root` 토큰만 쓴다 (`--cream`, `--moon`, `--blush`, `--muted` 등). 어두운 밤하늘 테마 하나만 둔다.
- 모션은 `prefers-reduced-motion` 에서 꺼진다. `.reveal` 은 JS가 있을 때만 숨겨지므로 JS 없이도 내용이 보인다.
