# 푸꾸옥 환갑 여행 브리프 — 프로젝트 가이드

> 이 파일은 이 저장소 전용. 전역 `~/.claude/CLAUDE.md` 규칙 위에 얹혀서 세부를 보충한다.

## 프로젝트 개요
- **무엇**: 2027년 환갑 기념 베트남 푸꾸옥 여행 계획을 함께 가는 사람들에게 공유하는 브리핑 웹페이지
- **출발점**: `andrea951102/nhatrang-trip`(나트랑 여행 페이지)을 2026-10-26에 복제해서 시작 — 구조·디자인·컴포넌트는 그대로, 문구·데이터만 푸꾸옥용으로 교체
- **형태**: 단일 `index.html` 파일 (CSS/JS 전부 인라인, 외부 의존은 Google Fonts CDN뿐)
- **배포**: GitHub Pages — `main` 브랜치 root를 그대로 서빙
- **Repo**: `andrea951102/phuquoc-trip` (public)
- **라이브 URL**: https://andrea951102.github.io/phuquoc-trip/

## 작업 방식
- 이 저장소에서 Claude Code로 직접 작업 → `git add . && git commit -m "..." && git push`. `main`에 푸시하면 Pages가 자동 재배포됨.
- 문서 구조: [docs/PROJECT.md](docs/PROJECT.md)(목적/이해관계자) · [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md)(구조) · [docs/ROADMAP.md](docs/ROADMAP.md)(확정/미정/다음 단계) · [docs/PROGRESS.md](docs/PROGRESS.md)(작업 로그) · [docs/COOPERATION.md](docs/COOPERATION.md)(Codex 등 다른 에이전트와 공유하는 진행 방식) · `docs/tasks/`(작업이 커지면 단위별로 분리).
- 작업 로그는 [docs/PROGRESS.md](docs/PROGRESS.md) — 의미 있는 작업을 마칠 때마다 맨 위에 1건씩 기록할 것.

## 코드 구조 (index.html 안에서)
- `:root` CSS 변수로 컬러 토큰 정의: `--ink`, `--paper`, `--coral`, `--gold`, `--teal`, `--sky` 등
- 폰트: 제목 `Jua`, 본문 `Gowun Dodum`, 영문 악센트("Phu Quoc" 이탤릭) `Fraunces`, 숫자/데이터 `JetBrains Mono`
- 섹션 순서: 히어로(#top, 스플릿플랩 항공 보드) → `#about`(푸꾸옥은? — 건기/우기 토글, 북부/남부 토글, 환갑여행 체크포인트) → `#budget`(항공) → `#itinerary`(일정 초안) → `#stay`(숙소 — 북부/남부 후보 카드 + 1인당 숙박비 총합) → `#food`(맛집) → `#activity`(액티비티 후보)
- 현재 상태: 날짜·항공·숙소 **전부 미정** → 해당 자리는 "미정"/"—"/"TBD"로 표시. 정해지면 채운다.
- 가격 단위 관례(나트랑 때부터 유지): 사용자가 숙박비 숫자 하나만 줄 때는 **2인·1박 기준**으로 해석, 1인당은 ÷2. 카드마다 "2인 총액"·"2인·1박"·"1인당"·"1인당·1박" 4개 항목 표기. (인원 구성이 달라지면 이 관례부터 다시 확인할 것)
- 주요 컴포넌트: 스플릿플랩 항공 보드(히어로, `data-flap`), 타임라인 아코디언(일정), 숙소 카드 + 포토 갤러리 라이트박스
- 항공 예산 미터: `#meter-fill`의 `data-fill`(0~100, %) 값으로 채움 정도를 정함
- 스크립트 하단 `GALLERIES` 객체 — 현재 비어 있음. 카드에 `data-gallery="키"` 갤러리 행을 넣고 여기에 같은 키로 사진 URL 배열을 추가하면 동작

## 알려진 이슈 / TODO
1. 날짜·항공·숙소·맛집 콘텐츠 미정 — [docs/ROADMAP.md](docs/ROADMAP.md) 참고.
2. 미사용 `.resort-*` / `.opinion` CSS 규칙이 나트랑 시절부터 남아 있음(나중에 의견 블록 재사용 가능성 있어 보존).
3. 사진을 넣게 되면 외부 CDN 핫링크는 만료될 수 있음 — 안정성 원하면 `images/`에 저장해 로컬 경로로.

## 검증
- 별도 빌드 도구 없음(순수 HTML/CSS/JS) — 수정 후엔 브라우저로 직접 열거나 로컬 서버 띄워서 확인.
- 자동화된 lint/test 스크립트 없으므로 "테스트 통과"라고 말하지 말 것 — 육안 확인 여부를 그대로 말할 것.
