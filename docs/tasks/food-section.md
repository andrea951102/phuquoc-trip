# 맛집 섹션(#food) 진행 상황

## 워크플로우
1. [docs/data/food-list.csv](../data/food-list.csv)를 엑셀/구글시트에서 편집 (최대 10곳). 컬럼: `식당명, 카테고리, 구글맵링크, 코멘트, 가격대`
2. 엑셀에서 편집했다면 **"다른 이름으로 저장 → CSV UTF-8"**로 저장 (일반 CSV로 저장하면 한글이 깨질 수 있음)
3. 자동 반영 안 됨 — Claude Code 세션에서 **"food-list.csv 반영해줘"**라고 요청할 것
4. 요청받으면: 각 행의 구글맵 링크에서 사진·평점 추출 → `index.html`의 `#food-grid`에 카드 추가(현재 있는 "맛집 후보 모으는 중" placeholder 카드는 제거) → 필요하면 `GALLERIES`에 사진 배열 추가 → 아래 체크리스트 갱신 → `docs/PROGRESS.md` 로그 → 커밋

## 진행 상황
- (아직 없음 — CSV에 추가되는 대로 여기 업데이트)

## 사진 추출 메모 (나트랑 때 확인한 방법, 2026-08-27)
- **Googlebot User-Agent로 `maps/place/.../data=!4m2!3m1!1s{FTID}`를 열면** `<meta property="og:image">`에 대표 사진 1장이 나옴 (`lh3.googleusercontent.com/gps-cs-s/...`, `=w1000` 붙여 사용). 카테고리·주소·평점은 `/maps/preview/place`의 최소 `pb`로 추출.
- 다중 사진 추출은 당시 재현 안 됨 → 카드엔 단일 커버 이미지(`.food-cover`, 클릭 시 구글맵) 사용.
