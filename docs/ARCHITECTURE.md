# ARCHITECTURE

## 개요
정적 사이트 1개 파일(`index.html`) — 별도 빌드 과정 없음. 배포는 GitHub Pages가 `main` 브랜치 root를 그대로 서빙.

## 구조 (index.html 내부)
- `<style>`: `:root` CSS 변수로 컬러 토큰 정의(`--ink`, `--paper`, `--coral`, `--gold`, `--teal`, `--sky` 등), 이후 컴포넌트별 클래스
- `<body>`: 섹션 순서 — 히어로(#top) → `#about` → `#budget` → `#itinerary` → `#stay` → `#food` → `#activity` → footer → lightbox 모달
- `<script>` (IIFE, 바닐라 JS): 스크롤 진행바, 탭 active 상태(IntersectionObserver), reveal 애니메이션, 타임라인 SVG 라인 드로잉, 날짜 아코디언, 스플릿플랩 항공 보드 애니메이션, 낮·밤 날씨/롱비치·북부·남부 토글, 포토 갤러리 라이트박스(`GALLERIES` 객체, 현재 비어 있음)

## 외부 의존성
- Google Fonts CDN (Jua, Gowun Dodum, Fraunces, JetBrains Mono) — 유일한 외부 리소스
- 사진: 아직 없음. 넣게 되면 외부 CDN 핫링크 또는 `images/` 로컬 파일

## 배포 파이프라인
로컬에서 `index.html` 수정 → `git add . && git commit && git push origin main` → GitHub Pages가 자동 재배포 → https://andrea951102.github.io/phuquoc-trip/ 반영. CI/빌드 스텝 없음.
