# polymedia-review-skill

> AI agent skill for writing deep review notes on books, games, movies, and music
> in Obsidian format — and then converting them into blog-ready posts. Built on
> Socrates' **maieutics (산파술)**: the skill interviews you to draw out the thinking
> already inside, instead of dumping critic-style answers on you.

[![Made with](https://img.shields.io/badge/Made%20with-Claude%20Skills-blueviolet)](https://docs.claude.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Languages](https://img.shields.io/badge/Triggers-8%20languages-blue)](#trigger-keywords)

---

## 무엇을 하는 스킬인가

작품을 보고 그냥 "좋았어"에서 끝내지 않고, **사유를 끌어내는 인터뷰**를 통해 옵시디언에 깊이 있는 리뷰 노트를 작성한다. 노트가 완성되면 같은 데이터를 톤만 바꿔 **블로그용 글로 변환**도 해준다.

핵심 철학은 한 줄로:

> Claude는 **산파**다. 비평가가 아니다.
> 사용자 안에 이미 있는 사유를 *언어화*하도록 돕는 사람.

이 페르소나는 소크라테스의 **산파술(maieutics, μαιευτική)**에서 가져왔다. 소크라테스는 자기 어머니의 직업(산파)을 빌려 자신의 대화법을 산파술이라 불렀다. 산파가 아이를 *낳지는* 않듯, 자신은 답을 *주지* 않는다. 다만 상대 안에 이미 있는 답이 *나올 수 있도록* 도울 뿐이다.

작품에 대한 일반적인 해석이나 평론을 *던지는* 것이 아니라, 사용자가 자기 안에 있는 생각을 풀어내도록 *질문만* 던진다.

## 핵심 기능

- **4 Phase 워크플로우** — 작품 캘리브레이션 → 1차 질문 → 대화형 파고들기 → 노트 생성
- **매체별 템플릿** — 책 / 게임 / 영화 / 음악 각 매체의 특성에 맞춘 질문과 본문 구조
- **4차원 루브릭** — craft / narrative / impact / rewatch 의 10점 척도. 각 차원의 *해석*은 매체별로 다름
- **두 가지 노트 작성 모드**
  - 모드 A: 구조 + 키워드 메모 (사용자가 직접 채움)
  - 모드 B: 사용자 문체 분석 후 대신 초안 작성
- **블로그 변환 (Phase 4)** — 옵시디언 노트를 네이버 블로그·티스토리·벨로그 등 독자용 글로 톤만 바꿔 재작성

## 디렉토리 구조

```
polymedia-review-skill/
├── SKILL.md                    # 페르소나 + 4 Phase + 평점 + 트리거
├── templates/
│   ├── book.md                 # 책 템플릿 (Frontmatter + 질문 + 본문 구조)
│   ├── game.md                 # 게임 템플릿
│   ├── movie.md                # 영화 템플릿
│   └── music.md                # 음악 템플릿
└── ref/
    ├── follow-up-patterns.md   # Phase 2 — 7가지 대화형 파고들기 기술
    └── blog-conversion.md      # Phase 4 — 블로그 변환 가이드
```

## 설치

### 방법 1: `npx skills add` (권장)

```bash
npx skills add rhino-ty/polymedia-review-skill
```

### 방법 2: 직접 패키징

[skill-creator](https://github.com/anthropics/skills/tree/main/skill-creator) 의 `package_skill.py`를 사용:

```bash
python -m scripts.package_skill /path/to/polymedia-review-skill /path/to/output
```

### 방법 3: 릴리스에서 다운로드

[Releases](../../releases) 페이지에서 `polymedia-review-skill.skill` 파일 다운로드.

### Claude.ai에 업로드

1. Claude.ai → **Settings → Capabilities → Skills**
2. **Upload Skill** 선택
3. `polymedia-review-skill.skill` 파일 업로드 후 활성화

## 사용 흐름

```
"[작품명] 리뷰 써줘" 또는 작품 정리 의도
  ↓
Phase 0: 작품 캘리브레이션 (매체 + 작품 결 파악)
  ↓
Phase 1: 1차 질문 dump (한 번에)
  ↓
Phase 2: 대화형 파고들기 (왜? + 감정 어휘 거들기)
  ↓
Phase 3: 노트 생성 — 모드 A (구조+키워드) or 모드 B (문체 모방)
  ↓
[옵션] Phase 4: 블로그 변환
  "블로그용으로도 변환할까?"
  ↓ YES
  후킹 제목 3안 → 사용자 톤 재작성 → 이미지 자리 표시
```

## 트리거 발화 예시

- "[작품명] 리뷰 써줘"
- "방금 [작품] 다 봤어, 정리하자"
- "[작품] 옵시디언에 정리하고 싶어"
- "감상 정리"
- 책/게임/영화/음악 작품명 + 평가·정리 의도

### Trigger Keywords

스킬은 **8개 언어**로 트리거된다. 자기 언어 그대로 말해도 작동.

| Language | Keywords |
|----------|----------|
| 🇰🇷 한국어 | 리뷰, 노트, 감상 정리, 평점, 별점, 다 봤어, 다 읽었어, 다 깼어, 옵시디언, 산파술, 블로그용 |
| 🇺🇸 English | review, write a review, just finished, just watched, just read, just played, obsidian note, blog conversion |
| 🇯🇵 日本語 | レビュー, 感想, ノート, 評価, 観終わった, 読み終わった, クリアした, ブログ用 |
| 🇨🇳 中文 | 评论, 笔记, 感想, 评分, 看完了, 读完了, 通关了, 博客发布 |
| 🇪🇸 Español | reseña, nota, calificación, acabo de ver, acabo de leer, acabo de jugar |
| 🇫🇷 Français | critique, note, évaluation, je viens de voir, je viens de lire |
| 🇩🇪 Deutsch | Rezension, Notiz, Bewertung, gerade gesehen, gerade gelesen |
| 🇮🇹 Italiano | recensione, nota, valutazione, ho appena visto, ho appena letto |

### 트리거하지 않는 경우

이 스킬은 *사유를 끌어내는* 도구다. 다음 상황엔 작동하지 않거나 작동해선 안 된다:

- 별점만 빠르게 매기고 싶을 때 (단순 점수 요청)
- 학술적 평론·논문 형태가 필요할 때
- 작품 정보·줄거리만 단순 조회하고 싶을 때
- SEO 목적의 대량 리뷰 생성
- 스포일러 위주의 줄거리 요약
- 사용자가 아직 경험하지 않은 작품

## 평점 — 4차원 루브릭

각 차원은 10점 척도. 각 차원의 *해석*은 매체별로 다르다.

| 차원 | 책 | 게임 | 영화 | 음악 |
|------|-----|------|------|------|
| **craft** | 문체·언어 | 게임플레이·시스템 | 연출·미장센 | 사운드·프로덕션 |
| **narrative** | 논지·서사 | 스토리·세계관 | 플롯·캐릭터 | 가사·앨범 흐름 |
| **impact** | 사유 자극 | 몰입·체험 | 감정 임팩트 | 정서적 울림 |
| **rewatch** | 재독 가치 | 재플레이 가치 | 재시청 가치 | 재청 가치 |

**종합 점수** = 4차원 평균.

## 권장 사용법

- **Anchor List 운영** — 매체별로 점수 기준작 5~10개를 옵시디언에 따로 둠 (`_Anchor-game.md` 등). 새 작품 평점 매길 때 흔들림 방지.
- **시간차 재평가** — frontmatter의 `revisited_at` 필드 활용. 6개월~1년 후 같은 작품 재평가 시 직관 다듬기 도구로 사용.

## 모델 권장

이 스킬은 단순 포맷이 아니라 **맥락 추론 + 절제된 개입**이 핵심이다.

- ✅ 권장: Claude Opus 4.6 / Gemini 2.5 Pro / GPT-o3
- ❌ 비권장: Haiku, Flash, mini 등 경량 모델

## 라이센스

MIT License. 자세한 내용은 [LICENSE](LICENSE) 참조.

## Credits

- **산파 페르소나** — 소크라테스의 산파술 (μαιευτική, *maieutics*)
- **개발 환경** — Claude Skills SDK
