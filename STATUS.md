# 새우깡 한계돌파 — 배포 상태

## 라이브
- **Production URL**: https://saeukkang-limit-break.vercel.app
- **Repo**: https://github.com/rhr1109/saeukkang-limit-break
- **Vercel project**: `saeukkang-limit-break` (rhr1109s-projects)
- **빌드 방식**: 정적 호스팅 (단일 `index.html`, package.json/빌드 스텝 없음)

## 최근 배포
| 버전 | 일자 | 요약 |
|---|---|---|
| v12.36b | 2026-05-04 | **난이도 검수 + 부모 코스튬 측면별 분리 + UI 명확화 + 디자인 픽스.** (1) **chm 곡선 평탄화** (ch130 이후 ×1.0008/ch 거의 동결, ch290+ ×1.025/ch ramp), (2) **base HP 공식 ch200 clamp** — 이후 boss base HP 일정, (3) **ch201-300 보스 hpMult 범위 축소** — ch300 dread_sovereign 175→105, (4) **신규 chapter-gated 카드 12종** (ch101/115/131/161/181/201/221/241/251/271/286/296), (5) **부모 코스튬 측면별 분리 구매** — 남편 부모 / 아내 부모 각자 따로 구매·장착·해제 (`buyParentsSet(setId, side)`), (6) **시어머니 모노클 줄 제거** (머리털처럼 보임 픽스) + **장모 보넷 정수리에만 dome** (눈 안 가리게), (7) **설정 카테고리별 토글 컬럼 헤더** [👁 보이기 / ✨ 효과] 일치 + 텍스트 시작점 정렬, (8) **부모 4명 모두 단안 통일**, 시어머니/장모 base eye 끄고 자체 단안 + 모노클/감은눈 + 분홍 눈썹. 검수 결과: ch200 SSS 풀세트 3분, ch290 SSS 1.2분, ch300 SSS 0.6분. ch130-200 곡선 4× 완화 (이전 ch200 보스 ~3시간 → 현재 ~3분). |
| v12.36 | 2026-05-04 | **부모 비둘기 디자인·통일감 픽스 + 카테고리별 설정 토글.** (1) **이중 눈 버그 수정**: motherInLaw/motherOfWife 가 base eye 위에 추가 eye 그려 두 눈처럼 보이던 문제 — `_drawElderPigeonInternal` 에 `noBaseEye` 옵션 추가하고 엄마 personality 가 자체 단안 + 모노클(시어머니)/감은눈(장모) 그리도록. 통일감 위해 모든 부모·조상 단안. (2) **조상 부리 색**: #E67700(갈색) → #FFA500(표준 오렌지). (3) **카테고리별 설정 토글**: `progress.settings` 에 `showWife/fxWife/showChild/fxChild/showFriends/fxFriends/showParents/fxParents/showAncestors/fxAncestors` 10개 필드 추가 + 자동 마이그레이션. 설정 모달에 카테고리별 [보이기][효과] 미니 토글 행 5개. (4) **합류 게이트**: 합류 안 된 카테고리 행 `display:none` (설정 자체 불가). (5) **렌더 가드 통합**: 인게임/시작화면/시네마틱 모든 drawCompanion 이 `companionVisible(kind)` + `companionFxOn(kind)` 사용. |
| v12.35 | 2026-05-03 | **원정 Ⅶ·Ⅷ 추가 — MAX_CHAPTERS 200→300.** (1) 원정 Ⅶ 천국 3층천 침범 (ch201-250): 부모 비둘기 pair 2종 합류(ch205/210, 천사 디폴트 무료 + 3 세트 유료 일괄). (2) 원정 Ⅷ 아마겟돈 (ch251-300): 악의 세력이 천국 침공 → 가족 + **창조주 동맹**으로 격퇴. 조상 비둘기 2종 합류(ch255 구구나르도 다 둘치 / ch260 비리스토둘레스, 다빈치·아리스토텔레스 패러디), 직업 코스튬 다종 개별 구매. (3) **SSS 등급 아마겟돈 코스튬** ch251 해금: 가족 자동 무료 / 친구·부모·조상 유료. 풀세트 시너지 ×1.40 dmg + ×1.30 maxHp + +35% holyBossBonus + projCount/pierce/regen. 부분 세트도 1pc 부터 의미있는 효과. 친구 5pc=90% / 부모 2pair=85% 부분 캡 (절대 100% X). (4) ch290+ 컨트롤 강요 곡선 (HP×1.030/dmg×1.025 per ch). SSS 풀세트로도 아슬아슬한 클리어선. (5) 20 신규 보스 변종(ch201-300, 5챕터 단위) — 악의 세력 톤(타락 천사·심연 군주·악의 군주 dread_sovereign 게임 최종). (6) tier 11(3층천 자색 광휘) + tier 12(아마겟돈 황금 전쟁터) BG, 100 신규 BGM, 20 신규 챕터 컬러. (7) 시네마틱 Ⅶ(천국 3층천 침범 완료) + Ⅷ(천상의 새우깡 — 창조주와 함께 악을 격퇴). (8) ch300 최종 클리어 시 영구 글로우 눈 + 천상의 새우깡 스킨 자동 무료 해금. (9) 첫 세트 멤버 합류 시 setIntroModal 미리보기 팝업. (10) 코인 보상 ch201+ 곡선 완만화로 SSS 풀세트(70k+) 구매 부담. |
| v12.34b | 2026-05-03 | **시네마틱 왕관 + 챕터선택 UI 픽스** — (1) floating crown body extent 정확히 반영해 머리/목 침범 회피(안전영역 부족시 skip). (2) 모바일 챕터선택 원정 탭(6개) flex-wrap 으로 2-3줄 분배 + font/padding 축소 + nowrap. 시네마틱 다시보기 row 챕터선택에서 제거. |
| v12.34a | 2026-05-03 | 천국 폴리시 — BGM 70 신규 pack(원정 Ⅴ/Ⅵ 챕터별), 천국 보스 SFX(sfxHeavenBoss — 종+major chord arp+합창), drawSkyline tier 9(구름+sparkle+깃털)/tier 10(오로라+광휘+광선) 배경 props, drawArenaFloor groundCol tier 9/10 추가. 기존 ch131+ 입장 시 groundCol undefined page error 도 동시 픽스. |
| v12.34 | 2026-05-03 | **천국 확장** — 원정 Ⅴ(천국 1층천 ch131-160) + 원정 Ⅵ(천국 2층천 ch161-200) 추가. MAX_CHAPTERS 130→200. 14 신규 보스, 70 신규 챕터, tier 9/10 배경, SS등급 코스튬(남편/아내/아기 부위별 + 친구 5종 천국 세트), 7-8단계 스킬, 천국 BG 스킨 2종(유료). 시네마틱 엔딩 4종 추가. 남편 왕관 위치 버그 픽스. **원정 보상 스킨 가격 책정** — 자동 무료 지급 제거 (해금 후 코인 결제 필요). |
| v12.33 | 2026-05-03 | 시네마틱 엔딩 layout 픽스 — modal 실제 top 동적 측정 + globe 반경 확대(W*0.36) + 2버튼 단순화. 모바일에서 globe·비둘기 가려지던 문제 해결. |
| v12.32a | 2026-05-03 | 효과 토글 desc 명확화 — "공격력 기여" + "OFF 시 데미지 0" 표기. |
| v12.32 | 2026-05-03 | 통합 설정 모달 (음소거 + 가족·동료 보이기/효과). HUD ⚙ + 시작화면 ⚙. |
| v12.31 | 2026-05-03 | 지옥문 2단계 시네마틱 — 팝업 → 풀스크린 + 회전 지옥문 + 5종 친구 + 전용 BGM/SFX. |
| v12.30 | 2026-05-03 | 원정 3 시네마틱 globe(우주 특이점) 가시화 — solid sphere + 표면 별. |
| v12.29 | — | 시네마틱 — 원정별 등장 캐릭터 정확화 + 발이 globe 표면에 닿게. |
| v12.28 | — | 시네마틱 globe 가시성 + 원정별 가족·동료 합류. |

## v12.35 — 원정 Ⅶ·Ⅷ 상세

### 신규 동료 (4)

| 동료 | 합류 챕터 | 사이즈 | 위치 | damageMult | 디폴트 |
|---|---|---|---|---|---|
| 🪽 남편 부모님 (pair) | ch205 | scale 0.62 (남편-아내 평균) | 남편 뒤, ox±110, oy 위쪽 | 0.40 | angel (천사옷 무료) |
| 🪽 아내 부모님 (pair) | ch210 | scale 0.62 | 남편 뒤, ox±110 | 0.40 | angel |
| 📐 구구나르도 다 둘치 | ch255 | scale 0.85 (아내 사이즈) | 가족-부모 사이, 곱슬머리+깃털 펜 (다빈치 풍) | 0.50 | inventor (발명가복 무료) |
| 📜 비리스토둘레스 | ch260 | scale 0.85 | 가족-부모 사이, 풍성 흰 수염+두루마리 (아리스토텔레스 풍) | 0.48 | scholar (철학자복 무료) |

부모/조상 모두 `_back:true` 플래그 → render loop 에서 player 보다 먼저 그려져 남편 뒤에 위치.

### SSS 아마겟돈 코스튬 (ch251 해금)

| 대상 | 가격 | 풀세트 효과 |
|---|---|---|
| 남편 (h/b/w) | 자동 무료 | mult 1.62 + 풀세트 ×1.40 dmg / ×1.30 maxHp / +35% holyBossBonus / +1 projCount / +1 pierce / +0.5 regen |
| 아내·아기 (head+body) | 자동 무료 | wife/mini_armageddon_halo+robe |
| 친구 5종 일괄 | 4,000 × 5 = 20k코인 | armageddonHostSet, partial 1~5pc=20/40/60/78/90% |
| 부모 2pair 일괄 | 11,000 × 2 = 22k | armageddonElder, partial 1pair 45% / 2pair 85% |
| 조상 개별 | 13k × 2 = 26k | gugunardo_armageddon / bristotodul_armageddon (개별 dmgBoost 1.18) |

총 SSS 풀세트 (가족 외 모두) = ~68k코인. ch300 클리어 보상 ~1370 코인 → ~50 챕터 farming.

### 난이도 곡선 (chapterMult)

- ch200까지: 기존 1.014/1.011 곡선
- ch201-289: 1.0125/1.0095 (소폭 가파름)
- ch290-300: **1.030/1.025 (가파름)** — SSS 풀세트 기준 아슬아슬한 클리어선

### 보스 (ch201-300, 20 변종)

- **ch201-250 천국 3층천 침범**: covenant_warden / archon_blade / throne_judicator / nameless_oracle / wrath_legion / grace_marshal / sanctum_examiner / third_heaven_warden / herald_archon / third_heaven_sovereign — hpMult 64→84
- **ch251-300 아마겟돈 (악의 세력)**: fallen_vanguard / dread_legion / ravager_warden / nightlance_marshal / armageddon_invader / fallen_choir / abyss_marshal / liar_legion / dread_apex / **dread_sovereign (게임 최종 보스)** — hpMult 88→175, dmgMult 5.55→8.00

### 시네마틱 엔딩

- **Ⅶ (ch250)** drawVictoryHeavenThird — 자색 sphere + 황금 균열(창조주 빛) + 회전 후광 + 옥좌 표식. 헤드라인 "천국 3층천 침범 완료!".
- **Ⅷ (ch300, 게임 최종)** drawVictoryArmageddon — 황금 sphere + 적금 광선 12방향(창조주의 손길) + 중앙 천상의 새우깡(큰 새우깡 + 빛나는 십자가). 헤드라인 "천상의 새우깡 — 창조주의 인정!". Sub: "창조주와 함께 악의 세력을 격퇴 — 천상의 새우깡을 받은 가족".

글로브 위 파티 배치: 가족 중앙 + 친구 5종 외곽 + 부모 pair earthR×0.55 + 조상 earthR×0.32. 모두 발이 globe 표면에 닿도록 foot offset 정확히 빼서 `c.y = surfaceY(dx) - foot_offset`.

### 영구 효과 (ch300 클리어 후)

- `progress.armageddonVictory = true` + `progress.eyesGlowPermanent = true`
- `getPigeonHungerState()` 가 항상 `'glow'` 반환 → 시작화면·인게임·시네마틱 모두 남편 비둘기 눈 광휘
- `progress.ownedSkins` 에 `'celestial_cracker'` 자동 추가 (price 0)

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
