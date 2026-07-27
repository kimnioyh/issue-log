# issue-log

현재 Claude Code 세션에서 겪은 문제들을 Notion DB에 문제별로 요약해 기록하는 스킬이다.
DB가 없으면 스키마대로 만들어준다.

## 무엇을 하나

세션이 끝날 때 `/issue-log`(또는 "오늘 세션 정리해줘")라고 하면, 대화를 훑어 실제로 막혔거나 판단이 필요했던 문제만 골라 문제마다 한 행으로 Notion에 남긴다. 각 행은 이렇게 채워진다.

| 필드 | 내용 |
|---|---|
| 작업명 | 어떤 작업이었는가 |
| 상황 | 당시 상황과 배경 |
| 문제 | 해결해야 했던 문제 (goal과 gap) |
| 이슈 | 고민한 기술적 이슈와 판단 |
| 실행한것, 다음 계획 | 실제로 한 일과 다음 계획 |
| 태그 | 업무 / 학습 / 프로젝트 |
| 중요도 | ⭐ ~ ⭐⭐⭐ |

## 사전 조건

Claude Code에 **Notion MCP가 연결**돼 있어야 한다. (`/mcp`로 확인)

## 설치

```
/plugin marketplace add kimnioyh/issue-log
/plugin install issue-log@issue-log-skills
/reload-plugins
```

## 사용

```
/issue-log
```

첫 실행 때 "이슈로그" DB가 없으면 어느 페이지 아래에 만들지 물어본 뒤 스키마대로 생성한다. 이미 있으면 그 DB에 행을 추가한다.

## 커스터마이징

- **DB 이름**: 기본값은 "이슈로그". 다른 이름을 쓰려면 `plugins/issue-log/skills/issue-log/SKILL.md`에서 이름을 바꾼다.
- **스키마는 한국어 필드명 기준**이다. 영어 등으로 바꾸려면 SKILL.md의 스키마 표와 필드 설명을 함께 수정한다.
- Notion select(태그, 중요도)는 등록 안 된 값을 자동 추가하지 않는다. 옵션을 늘리려면 Notion에서 먼저 추가하거나 스킬이 `update-data-source`로 추가하게 둔다.

## 참고

기록 필드 구성(작업명·상황·문제·이슈·실행한것)은 아래 글의 업무로그 형식을 참고했다.
https://velog.io/@gusdudco6/doYouWantToBeCohe

## 라이선스

MIT
