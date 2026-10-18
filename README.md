# harness-coding-skills

> **📦 최신 버전은 [kkh2114/claude-skills-public](https://github.com/kkh2114/claude-skills-public)으로 옮겨졌습니다.** 이 저장소의 스킬과 다른 공개 스킬이 한곳에 모여 있고, 앞으로는 그곳만 업데이트됩니다. (The latest versions now live in [claude-skills-public](https://github.com/kkh2114/claude-skills-public).)

Claude Code 스킬 3종 — 코딩 에이전트용 하네스(작업 환경)를 설계·검증하고, 그 안에서 에이전트가 안정적으로 코드를 쓰게 하는 세트.

| 스킬 | 역할 | 호출 시점 |
|---|---|---|
| [harness-designer-coding](./harness-designer-coding) | Planner→Generator→Evaluator 순환으로 코딩 하네스(AGENTS.md·CLAUDE.md·검증 루프·CI)를 설계·구축 | "코딩 하네스 만들어줘", "에이전트 개발 환경 구축" |
| [cartesian-review](./cartesian-review) | 데카르트 5렌즈(열거·명증·종합·분석·방법적 회의)로 문서·설계를 검토. Evaluator 90점+ PASS 후 자동 호출됨 | "데카르트 분석", "빠진 것 찾아줘" |
| [karpathy-guidelines](./karpathy-guidelines) | LLM 코딩 실수를 줄이는 4원칙 행동 지침. 생성된 하네스의 CLAUDE.md에 주입되어 운영 단계에서 참조됨 | 코드 작성·리뷰·리팩터 시 |

## 설치

```bash
git clone https://github.com/kkh2114/harness-coding-skills.git
cp -R harness-coding-skills/{harness-designer-coding,cartesian-review,karpathy-guidelines} ~/.claude/skills/
```

프로젝트 단위로 쓰려면 `~/.claude/skills/` 대신 `<project>/.claude/skills/`에 복사한다.

## 관계도

```
harness-designer-coding (L1 설계)
 ├─ Phase 0  : harness-100 exemplar 패턴 매칭
 ├─ Generator: CLAUDE.md에 Karpathy 4원칙 주입 ──▶ karpathy-guidelines (L2 운영 시 참조)
 └─ Evaluator: 7대 기둥 채점 90점+ ──▶ cartesian-review 자동 실행 (미설치 시 건너뜀)
```

## 출처·라이선스

- `karpathy-guidelines` — [forrestchang/andrej-karpathy-skills](https://github.com/forrestchang/andrej-karpathy-skills) 기반, MIT License.
- `harness-designer-coding`은 [revfactory/harness-100](https://github.com/revfactory/harness-100) (Apache-2.0)의 exemplar를 참조 기준으로 사용한다.
- `harness-designer-coding`, `cartesian-review` — © kkh2114.
