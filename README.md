# Personal Skills

개인적으로 사용하는 에이전트 스킬을 보관하는 저장소입니다.

## 빠른시작

```sh
# mattpocock스킬 추가
npx skills@latest add mattpocock/skills

# vmfhrmfoaj스킬 추가
git clone <repository name> vmfhrmfoaj-skills
npx skills@latest add ./vmfhrmfoaj-skills
```

## 스킬 목록

| 스킬 | 설명 | 필수 설치 스킬 |
| --- | --- | --- |
| `decision-question` | 기술/설계/정책 결정 하나를 이해 문서로 설명하고, 결과 표·선택지 비교·추천과 함께 사람이 직접 고르게 질문한다. | `understanding-doc` |
| `design-feature` | 상세 요구사항을 책임 배치·인터페이스·데이터 흐름·TDD 전략까지 담은 구현 가능한 설계로 바꾼다. | 없음 |
| `improve-docs` | 문서의 분절·중복·불명확한 역할을 찾아 SSOT 중심 문서 구조로 정리한다. | 없음 |
| `improve-understanding` | 이해 문서로 숲(전체 지도)과 나무(개념)를 설명하고, 대화에서 한 덩이씩 적용 질문·판정·다시 가르치기와 확인 시험으로 이해를 확인한다. | `understanding-doc` |
| `understanding-doc` | 결정·이해 질문 전에 사람이 읽을 이해 문서(MD + mermaid)를 만든다. 1층 전체 큰 흐름 → 2층 세부 흐름 → 3층 결정에 걸린 것(문제 지점 빨간 표시). | 없음 |
| `wildcard-architect` | 기존 결정을 제약이 아닌 선택으로 보고, 목표만 유지한 채 구조적으로 다른 대안과 와일드카드를 제시한다. | 없음 |
