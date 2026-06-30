# Personal Skills

개인적으로 사용하는 에이전트 스킬을 보관하고 점차 확장하기 위한 저장소입니다.

## Matt Pocock Skills

새 환경에서는 다음 명령으로 스킬 선택 화면을 엽니다.

```sh
npx skills@latest add mattpocock/skills
```

아래 항목은 현재 PC의 글로벌 스킬(`/home/vmfhrmfoaj/.agents/skills`)과 이름이 정확히 일치하는 필수 설치 대상입니다. 설치 화면에서 `◼` 항목을 선택합니다.

```text
Mattpocock Skills
│  ◼ codebase-design
│  ◼ domain-modeling
│  ◼ grill-me
│  ◼ grill-with-docs
│  ◼ grilling
│  ◼ handoff
│  ◼ improve-codebase-architecture
│  ◼ tdd
│  ◼ teach
│  ◼ to-issues
└  ◼ to-prd
```

## 이름이 유사한 글로벌 스킬

다음 스킬은 기능이나 이름이 유사하지만 설치 식별자가 다르므로 위 필수 목록에는 포함하지 않습니다.

- 글로벌 `diagnose` ↔ Matt Pocock `diagnosing-bugs`
- 글로벌 `write-a-skill` ↔ Matt Pocock `writing-great-skills`

> `.codex/skills/.system`에 기본 제공되는 시스템 스킬은 이 목록의 대상이 아닙니다.


```bash
npx skills@latest add https://github.com/vmfhrmfoaj-tech/skills --skill design-feature
```
