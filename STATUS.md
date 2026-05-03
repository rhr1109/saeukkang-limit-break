# 새우깡 한계돌파 — 배포 상태

## 라이브
- **Production URL**: https://saeukkang-limit-break.vercel.app
- **Repo**: https://github.com/rhr1109/saeukkang-limit-break
- **Vercel project**: `saeukkang-limit-break` (rhr1109s-projects)
- **빌드 방식**: 정적 호스팅 (단일 `index.html`, package.json/빌드 스텝 없음)

## 최근 배포
| 버전 | 일자 | 요약 |
|---|---|---|
| v12.34 | 2026-05-03 | **천국 확장** — 원정 Ⅴ(천국 1층천 ch131-160) + 원정 Ⅵ(천국 2층천 ch161-200) 추가. MAX_CHAPTERS 130→200. 14 신규 보스, 70 신규 챕터, tier 9/10 배경, SS등급 코스튬(남편/아내/아기 부위별 + 친구 5종 천국 세트), 7-8단계 스킬, 천국 BG 스킨 2종(유료). 시네마틱 엔딩 4종 추가. 남편 왕관 위치 버그 픽스. **원정 보상 스킨 가격 책정** — 자동 무료 지급 제거 (해금 후 코인 결제 필요). |
| v12.33 | 2026-05-03 | 시네마틱 엔딩 layout 픽스 — modal 실제 top 동적 측정 + globe 반경 확대(W*0.36) + 2버튼 단순화. 모바일에서 globe·비둘기 가려지던 문제 해결. |
| v12.32a | 2026-05-03 | 효과 토글 desc 명확화 — "공격력 기여" + "OFF 시 데미지 0" 표기. |
| v12.32 | 2026-05-03 | 통합 설정 모달 (음소거 + 가족·동료 보이기/효과). HUD ⚙ + 시작화면 ⚙. |
| v12.31 | 2026-05-03 | 지옥문 2단계 시네마틱 — 팝업 → 풀스크린 + 회전 지옥문 + 5종 친구 + 전용 BGM/SFX. |
| v12.30 | 2026-05-03 | 원정 3 시네마틱 globe(우주 특이점) 가시화 — solid sphere + 표면 별. |
| v12.29 | — | 시네마틱 — 원정별 등장 캐릭터 정확화 + 발이 globe 표면에 닿게. |
| v12.28 | — | 시네마틱 globe 가시성 + 원정별 가족·동료 합류. |

## v12.32 — 통합 설정 모달 상세

### 진입점
- **인게임 HUD**: 좌측 ⚙ 버튼 (구 🔊 음소거 자리)
- **시작화면**: 좌상단 ⚙ 버튼 (우상단 🛒 상점 pill 의 미러 위치)
- 두 버튼 모두 음소거 ON 시 우상단 작은 빨간 dot indicator 표시

### 모달 구성 (UX 순서)
1. **사운드 — 🔊 음소거**: 항상 노출. BGM + 효과음 모두 끔. localStorage 영구 저장.
2. **비둘기 가족 · 동료 — 👁 보이기**: ch51 아내 합류 후 노출. 시작화면 / 게임 / 시네마틱 / 스킨 미리보기 모두에 적용.
3. **비둘기 가족 · 동료 — ✨ 효과**: ch51 아내 합류 후 노출. **자동 사격 · 공격력 기여 · 사격음** 모두 OFF (사격이 동료의 유일한 공격 메커니즘이라 OFF 시 가족·동료 데미지 기여 0). **보이기 OFF 면 자동 비활성** (UI 도 disabled 표현).

### 기술 구현
- `progress.settings = { muted, showFamily, familyFx }` 영구 저장. 구버전 progress 자동 마이그레이션 (Object.assign 머지).
- helpers: `settingsMuted()`, `showFamilyOn()`, `familyFxPref()`, `familyFxEffective()`, `familyToggleAvailable()`.
- 적용 위치 (모두 가드 추가):
  - `drawTitlePigeonFrame` / `drawSkinPreviewPigeonFrame` → `drawFamilyGroup(..., showFamilyOn())`
  - 게임 메인 렌더 → `if(showFamilyOn()) for(const c of state.companions) drawCompanion(...)`
  - 시네마틱 victory (ch50/70/100) → expedition 별 가족·동료 draw 가드
  - `drawHellGateScene` → 갇힌 5종 친구 + 철창 가드 (지옥문은 항상 회전)
  - `updateCompanions` → `if(familyFxEffective()) fireCompanionShrimp(c)`
- 부팅 시 `muted = settingsMuted()` 동기화 + `_refreshSettingsBtnIndicator()` 호출 (TDZ 회피 위해 progress 초기화 직후).

### 구출 친구·가족 전투 합류 챕터
| 동료 | 합류 trigger | 실제 전투 합류 |
|---|---|---|
| 💗 아내 비둘기 | ch51 클리어 | ch52~ |
| 👶 아기 비둘기 | ch60 클리어 | ch61~ |
| 🐦 참새 | ch105 클리어 | ch106~ |
| 🦜 까치 | ch110 클리어 | ch111~ |
| 🦉 부엉이 | ch115 클리어 | ch116~ |
| 🦚 앵무새 | ch120 클리어 | ch121~ |
| 🐿️ 다람쥐 | ch125 클리어 | ch126~ |

각자 `player.damage × 0.20~0.45`, fireRate 1.0~2.2 (자동 새우깡 사격). 보스 HP는 합류 보너스 분(~10-20%) 가산되어 순기여만큼 보상.

## 검수 (v12.32)
- 캡쳐 매트릭스: PC 1280×800 + Mobile 390×844 × 10 시점 = 20장 (`.tmp_pc_*.png`, `.tmp_mo_*.png`).
  - 잠금/언락 × 모달 열림/닫힘 × show on/off × mute on/off × 인게임 모달.
- 콘솔 오류 0건 (puppeteer 자동 검증, `pageerror` + `console.error` 캡쳐).
- 회귀: side_effects 영향 없음 (기존 로직 가드만 추가, 함수 시그니처 동일).

### 발견·수정한 이슈 (v12.32 작업 중)
1. **TDZ ReferenceError**: `_refreshSettingsBtnIndicator()` 부팅 호출이 `const progress` 선언보다 먼저 실행돼 페이지 전체 스크립트 halt.
   - 수정: 부팅 호출을 `progress` IIFE 직후로 이동. helpers 정의는 그 자리.

## 알려진 미해결 / 후속
- (없음) — v12.32 검수 통과.

## 작업 흔적 (커밋 제외 권장)
- `.tmp_*.png` / `.tmp_*.html` / `.tmp_*.js` — 디버그·캡쳐 산출물.
- `preview_*.html` — UI 프리뷰 임시 파일.
- `node_modules/` + `puppeteer` — 캡쳐 검증용 임시 의존성. `package.json` 도 같이 생성됐다 제거.
- `.vscode/` — 로컬 에디터 설정.

## Vercel 배포 절차 (참고)
1. `git add index.html STATUS.md` — 검증된 파일만 stage.
2. `git commit -m "feat(v12.X): ..."` — Conventional + 한글 본문.
3. `git push origin main` → Vercel 자동 빌드 + 별칭 alias 갱신.
4. `vercel inspect saeukkang-limit-break.vercel.app --scope rhr1109s-projects` 로 status `● Ready` 확인.
