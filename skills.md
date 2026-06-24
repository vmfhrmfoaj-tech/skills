# GitHub를 통한 Agent Skill 배포 및 설치

`npx skills@latest add mattpocock/skills`와 같은 방식으로 개인 스킬을 설치하려면, npm 패키지를 배포하는 대신 스킬을 공개 GitHub 저장소에 올리면 된다.

## 단일 스킬 저장소

저장소 루트에 `SKILL.md`를 배치한다.

```text
design-feature/
├── SKILL.md
├── design-output-template.md
└── agents/
    └── openai.yaml
```

GitHub의 `yourname/design-feature` 저장소로 push한 뒤 다음과 같이 설치한다.

```bash
npx skills@latest add yourname/design-feature
```

Codex에 전역 설치하려면 대상과 범위를 명시할 수 있다.

```bash
npx skills@latest add yourname/design-feature \
  --agent codex \
  --global
```

## 로컬 디렉터리에서 설치

GitHub에 push하기 전에도 로컬 경로를 설치 소스로 사용할 수 있다. 현재 저장소 루트에서 `design-feature`를 설치하려면:

```bash
npx skills@latest add ./design-feature
```

Codex에 전역 설치하려면:

```bash
npx skills@latest add ./design-feature \
  --agent codex \
  --global
```

확인 질문 없이 설치하려면 `--yes`를 추가한다.

```bash
npx skills@latest add ./design-feature \
  --agent codex \
  --global \
  --yes
```

다른 위치에서 실행할 때는 `./design-feature` 대신 해당 디렉터리의 상대 경로나 절대 경로를 사용한다.

## 여러 스킬을 제공하는 저장소

여러 스킬을 하나의 저장소에서 관리하려면 `skills/<skill-name>/SKILL.md` 구조를 사용한다.

```text
my-skills/
└── skills/
    ├── design-feature/
    │   ├── SKILL.md
    │   └── design-output-template.md
    └── another-skill/
        └── SKILL.md
```

저장소에 포함된 스킬을 탐색하며 설치하려면:

```bash
npx skills@latest add yourname/my-skills
```

특정 스킬만 설치하려면:

```bash
npx skills@latest add yourname/my-skills \
  --skill design-feature
```

## `design-feature`의 필수 의존 스킬

현재 `design-feature/SKILL.md`는 실행 전에 다음 스킬이 설치되어 있는지 확인하도록 요구한다.

- `improve-codebase-architecture`
- `grill-with-docs`
- `tdd`

`skills` CLI는 `SKILL.md` 본문에 적힌 의존 스킬을 자동으로 설치하지 않는다. 따라서 다음 중 하나를 선택해야 한다.

1. 필수 스킬도 같은 저장소에 포함하고 사용자가 함께 설치하도록 안내한다.
2. 저장소의 `README.md`에 각 필수 스킬의 별도 설치 명령을 제공한다.

다른 작성자의 스킬을 저장소에 포함할 때는 해당 스킬의 라이선스와 재배포 조건을 먼저 확인해야 한다.

## 참고

- Skills CLI: <https://github.com/vercel-labs/skills>
- `SKILL.md`에는 최소한 유효한 YAML frontmatter의 `name`과 `description`이 필요하다.
- 저장소 루트의 `SKILL.md`와 `skills/<name>/SKILL.md` 구조가 공식적으로 탐색된다.
