# COOPERATION

이 문서는 이 저장소에서 작업할 수 있는 여러 에이전트(Claude Code, Codex 등)가 같은 그림을 보게 하기 위한 공용 문서입니다.

## 역할 분담
- **Claude Code가 메인**: 이 저장소의 모든 코드(=`index.html`)는 기본적으로 Claude Code가 직접 작성한다.
- **Codex는 오버플로우**: Claude Code의 토큰/예산이 소진되어 남은 작업이 있을 때만 투입. 이 경우 설계는 Claude Code가 먼저 끝내두고, 실행 지시서를 `docs/handoff/`에 남겨서 Codex는 "실행만" 담당한다.

## 현재 진행 방식
- 사용자는 **Claude Code**로 이 저장소에서 직접 작업한다 (나트랑 프로젝트에서 이어받은 방식).
- 배포는 `git add && git commit && git push` → GitHub Pages 자동 재배포. GitHub 웹 UI "Upload files"는 더 이상 쓰지 않음.

## 최근 결정 사항
- 2026-10-26: `nhatrang-trip`에서 복제해 시작. 인계는 `docs/PROGRESS.md` + 프로젝트 `CLAUDE.md`로 한다.

## 에이전트 간 공유 규칙
- 어떤 에이전트든 작업을 마치면 `docs/PROGRESS.md` 맨 위에 1건 기록 (무엇을·왜·다음 할 일).
- 결정/스펙이 바뀌면 관련 문서(`PROJECT.md`/`ARCHITECTURE.md`/`ROADMAP.md`)를 그 자리에서 갱신 — 코드와 문서가 어긋난 채 두지 않는다.
- Codex에게 작업을 넘길 일이 생기면 `docs/handoff/`에 지시서를 만들어 여기에 링크를 남긴다 (현재는 해당 사항 없음).
