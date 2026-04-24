# 새우깡으로 한계돌파 🐦💥

근육질 비둘기가 새우깡을 투척하며 도시·동굴·우주·지옥을 돌파하는 탑뷰 로그라이크 불릿 헤븐 (Survivors-like).

## 플레이

- **온라인**: 배포된 Vercel URL에서 바로 플레이
- **로컬**: `index.html`을 브라우저로 열기만 하면 됩니다 (의존성 없음)

## 특징

- **30개 챕터**, 각 8스테이지 + 챕터 보스
- 6개 티어 테마 (Day City / Neon Night / Underground / Ice / Cosmic / Hellfire), 각 전용 팔레트·BGM·환경 프롭
- 6종 기본 적 + 5종 고챕터 해금 적 (ghost, bomber, reaper, sniper, summoner)
- 17종 레벨업 카드 (멀티샷·관통·회오리·폭탄·번개 등 빌드 조합)
- 5종 드롭 아이템 (💖 heal / 🧲 magnet / 💣 bomb / 🌟 golden / 🪙 coin) + pity 시스템
- 썸네일과 동일한 디자인의 **근육질 비둘기** 캐릭터 (idle 호흡 / walk bob / attack wind-up / blink 애니메이션)
- 모바일 완전 대응 (가상 조이스틱, safe-area-inset, visualViewport 추적)

## 조작

| 플랫폼 | 조작 |
| --- | --- |
| PC | WASD / 방향키 이동, ESC 일시정지 (자동 공격) |
| 모바일 | 좌하단 가상 조이스틱 + 우하단 `⏸/✕/🔊` 버튼 |

## 기술 스택

- 단일 HTML 파일, 의존성 없음
- Canvas 2D 렌더링
- Web Audio API (tier별 BGM 팩 + SFX)
- localStorage 진행 저장 (`saeukkang_progress_v1`)

## 문서

자세한 게임 디자인은 [SAEUKKANG_DESIGN.md](./SAEUKKANG_DESIGN.md) 참고.
