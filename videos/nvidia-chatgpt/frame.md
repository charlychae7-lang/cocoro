---
version: alpha
name: GTC Keynote — Frame (NVIDIA-inspired, video layer)
description: >
  ChatGPT의 등장과 NVIDIA 주가 폭발을 다루는 모션 그래픽용 프레임 디자인 시스템.
  NVIDIA 브랜드 아이덴티티(NVIDIA Green #76B900 + 순수 블랙 + 화이트)와 GTC 키노트 영상의
  분위기(깊은 블랙 무대, 네온 그린 라이트, 와이어프레임·파티클 필드, 거대한 숫자)를 기준으로 한다.
  비공식 팬/해설 영상용 — 공식 로고·서체는 NVIDIA 브랜드 가이드라인에 따라 별도 확보 필요.
unit: the frame — 1920×1080 primary; 9:16 and 1:1 documented
principle: black stage · one green light · numbers are the hero

colors:
  # — brand core —
  nvidia-green: "#76B900"        # 유일한 브랜드 컬러. 빛(light)으로 사용
  green-bright: "#9AE000"        # 글로우 하이라이트, 숫자 상승 피크
  green-deep: "#3F6B00"          # 그림자 쪽 그린, 그리드/와이어프레임 저휘도
  green-glow: "rgba(118,185,0,0.35)"   # 블룸/헤일로
  # — stage —
  black: "#000000"               # 기본 무대
  carbon: "#0B0D0A"              # 패널/카드 (살짝 그린 기운의 블랙)
  graphite: "#1A1C18"            # 2단계 서피스
  line: "#2A2D26"                # 1px 헤어라인
  # — text —
  white: "#FFFFFF"
  gray-100: "#E6E8E3"
  gray-400: "#9A9E94"            # 보조 텍스트
  gray-600: "#5B5F55"            # 힌트/축 라벨
  # — semantic (데이터 전용, 최소 사용) —
  down-red: "#E5484D"            # 하락/경쟁 비교 시에만
  chatgpt-teal: "#10A37F"        # ChatGPT 언급 시 보조 태그 한정 (면적 5% 이하)

typography:
  # NVIDIA Sans(NVIDIA-EMEA)는 사내 전용 서체 → 공개 대체: Barlow(헤드라인) / Inter(본문)
  display:   { fontFamily: "Barlow", cqw: 14.0, weight: 800, lineHeight: 0.9, tracking: "-0.02em" }
  h1:        { fontFamily: "Barlow", cqw: 7.0,  weight: 800, lineHeight: 0.95, tracking: "-0.01em" }
  h2:        { fontFamily: "Barlow", cqw: 4.2,  weight: 700, lineHeight: 1.05 }
  stat-value:{ fontFamily: "Barlow", cqw: 18.0, weight: 800, lineHeight: 0.9, tracking: "-0.03em", tabularNums: true }
  lead:      { fontFamily: "Inter",  cqw: 1.7,  weight: 400, lineHeight: 1.5 }
  body:      { fontFamily: "Inter",  cqw: 1.3,  weight: 400, lineHeight: 1.55 }
  label:     { fontFamily: "JetBrains Mono", cqw: 0.78, weight: 500, tracking: "0.16em", upper: true }
  date-tag:  { fontFamily: "JetBrains Mono", cqw: 1.1,  weight: 500, tracking: "0.12em", upper: true }

spacing:
  pad-x: "6cqw"
  pad-y: "5cqw"
  gap-lg: "4cqw"
  gap-md: "2cqw"
  gap-sm: "1cqw"

components:
  stage:
    ground: "{colors.black}"
    description: "기본 배경. 순수 블랙 + 중앙 하단에서 올라오는 {colors.green-glow} 라디얼 빛. 그라디언트는 이 빛 하나뿐."
  green-light:
    description: "그린은 '색'이 아니라 '빛'이다. 발광 라인, 글로우, 하이라이트 바로만 쓰고 면(面) 채우기는 CTA/강조 한 곳만."
  hairline:
    stroke: "1px solid {colors.line}"
    description: "구조는 1px 헤어라인과 모서리 브래킷(┌ ┐)으로. 그림자·라운드 없음(라운드 0~4px)."
  corner-brackets:
    color: "{colors.nvidia-green}"
    description: "프레임/카드 네 모서리 L자 브래킷 — GTC 스타일 'HUD' 느낌의 시그니처."
  kicker:
    typography: "{typography.label}"
    color: "{colors.nvidia-green}"
    description: "챕터 상단 아이브로우. 예: '01 / NOV 30, 2022'."
  stat-hero:
    typography: "{typography.stat-value}"
    color: "{colors.white}"
    accent: "{colors.nvidia-green}"
    description: "화면당 숫자 1개가 주인공. 카운트업 후 그린 글로우 펄스."
  chart-line:
    stroke: "{colors.nvidia-green} 3–4px, 하단 영역은 green→transparent 그라디언트"
    grid: "{colors.line} 1px, 축 라벨 {typography.label} {colors.gray-600}"
    description: "주가 차트는 라인 드로우 + 선두 점(헤드)에 글로우. 이벤트 지점에 수직 마커 + 라벨 카드."
  event-marker:
    shape: "수직 1px 라인 + 원형 노드 + 라벨 카드(carbon 서피스, 그린 브래킷)"
    description: "ChatGPT 출시, GPU 수요 급증, 실적 발표 등 타임라인 이벤트."
  wireframe-field:
    description: "저휘도({colors.green-deep}) 3D 와이어프레임 격자/지형/뉴럴 네트워크. 배경 깊이감용, 텍스트 뒤에서 천천히 이동."
  particle-stream:
    description: "그린 입자가 칩(GPU) 방향으로 수렴 — '데이터가 컴퓨팅으로 흘러든다'의 은유."
---

# GTC Keynote — Frame (NVIDIA-inspired)

## Overview

**주제:** ChatGPT의 등장 → AI 연산 수요 폭발 → NVIDIA 주가 급등. 서사는 "하나의 앱이
산업 전체의 연산 수요를 열었다"이다.

**룩:** GTC 키노트 무대 — 깊은 블랙 위에 **NVIDIA 그린이 빛으로** 존재한다. 거대한 숫자,
발광하는 라인 차트, 와이어프레임과 파티클이 깔린 공간감, 모서리 브래킷 HUD. 차분한 설명이
아니라 **무대 조명이 켜지는 순간**처럼 연출한다.

**핵심 원칙**

- **블랙 무대** — 배경은 `#000` 계열만. 흰 배경 프레임 금지.
- **그린은 빛** — `#76B900`이 유일한 강조색. 한 프레임에 그린이 화면의 15%를 넘지 않게(글로우 제외).
- **숫자가 주인공** — 한 프레임에 히어로 숫자/문장 1개, 3~6배 크기로 지배.
- **구조는 선** — 카드는 헤어라인 + 코너 브래킷. 그림자·둥근 모서리 지양.
- **하락/경쟁 색(적색)·ChatGPT 틸**은 데이터 구분이 꼭 필요할 때만, 소면적으로.

## The Frame

- **Primary:** 1920×1080 (16:9), 타입은 `cqw` 단위(`px ÷ 1920 × 100`). 모든 프레임 그라운드에 `container-type: size`.
- **Vertical 1080×1920 / Square 1080×1080:** 동일 토큰, `pad`를 6cqw 유지, 히어로 숫자를 한 줄 → 두 줄로 스택.
- **Safe area:** 좌우 6cqw, 상하 5cqw. 자막/라벨은 하단 8cqw 이내 금지(플랫폼 UI 겹침).
- **Frame Craft Bar**
  - *Squint:* 눈을 가늘게 떴을 때 숫자/문장 1개 + 그린 빛 1곳만 보여야 함.
  - *Silence:* 선언 프레임은 50% 이상 비어 있음(블랙이 여백).
  - *Reference:* GTC 키노트 오프닝 시퀀스, NVIDIA 제품 티저. 실패 모습 = 파란 계열 IT 컨설팅 슬라이드, 다색 대시보드.

## Colors

| 역할 | 토큰 | 사용 |
|---|---|---|
| 무대 | `#000000` / `#0B0D0A` | 배경 / 카드 |
| 브랜드 빛 | `#76B900` | 라인, 글로우, 키커, 브래킷, 강조 숫자 |
| 피크 | `#9AE000` | 차트 선두 점, 신고가 순간 |
| 저휘도 그린 | `#3F6B00` | 와이어프레임, 그리드 |
| 텍스트 | `#FFFFFF` / `#9A9E94` / `#5B5F55` | 주 / 보조 / 힌트 |
| 데이터 예외 | `#E5484D`, `#10A37F` | 하락·ChatGPT 태그 (극소량) |

글로우 규칙: `box-shadow/filter: drop-shadow(0 0 24px rgba(118,185,0,.45))` 계열 1단 + 2단(넓고 약한) 이중 블룸.

## Typography

- **Barlow 800** (헤드라인·숫자) — NVIDIA Sans의 각진 DIN풍 인상에 가장 가까운 공개 서체. 대문자 대신 **Title/Sentence case + 강한 굵기**.
- **Inter 400** (본문·캡션), **JetBrains Mono 500 대문자** (키커·날짜·축·수치 라벨).
- 한글 병기 시: **Pretendard** (헤드라인 800 / 본문 400)로 동일 굵기 매핑. 한 프레임 내 서체 3종 초과 금지.
- 숫자는 항상 `tabular-nums`, 카운트업 중 자릿수 흔들림 방지.

## Motion System (모션 그래픽 핵심)

**무드:** 빠르고 정밀한 "기계식" 모션 + 마지막에 빛이 번지는 "블룸". 바운스·탄성 없음.

| 요소 | 모션 | 이징 / 시간 |
|---|---|---|
| 오프닝 | 블랙 → 하단 그린 빛 점등 → 와이어프레임 격자 슬로우 드리프트 | `power3.out`, 0.8–1.2s |
| 타이틀 | 마스크 리빌(아래→위) + 글자 단위 스태거 30ms, 직후 그린 스캔라인 1회 통과 | `expo.out`, 0.6s |
| 히어로 숫자 | 카운트업(감속 곡선) → 도달 시 글로우 펄스 + 미세 카메라 푸시인 | `power4.out`, 1.2–1.8s |
| 주가 차트 | 라인 드로우(SVG stroke) + 선두 점 글로우 + 영역 그라디언트 페이드 | `none`(선형) 구간 + 급등 구간만 가속 |
| 이벤트 마커 | 수직 라인 성장 → 노드 팝 → 라벨 카드 코너 브래킷 트레이스 | `power2.out`, 0.5s |
| 파티클 | 그린 입자가 GPU/칩 아이콘으로 수렴 | 유기적 곡선, 2–3s 루프 |
| 전환 | 하드컷 + 그린 라인 와이프 / 줌스루(칩 내부로 진입) | 0.4–0.6s, 비트에 동기 |
| 엔딩 | 모든 요소 암전 → 단일 그린 라인/로고 점등 | `power3.inOut` |

**규칙:** 한 샷 한 모션 아이디어 · 카메라는 느린 푸시인(100→108%)만 · 글리치는 급락/위기 장면에서 0.2초 이내로만.

## 스토리 구조 제안 (60–90초, 6 챕터)

1. **PROLOGUE** — 블랙, 점등. "2022. 11. 30" 날짜 태그.
2. **THE SPARK** — ChatGPT 출시, 사용자 수 급증 카운트업 (수치는 반드시 출처 확인 후 기입).
3. **THE DEMAND** — 파티클이 GPU로 수렴, "학습과 추론은 GPU 위에서 돈다".
4. **THE CHART** — NVDA 주가 라인 드로우, 이벤트 마커 3~4개.
5. **THE NUMBER** — 시가총액/상승률 히어로 숫자 1개 (거대 스탯 프레임).
6. **EPILOGUE** — "새로운 연산의 시대" 한 문장 + 암전.

## Do / Don't

- ✅ 블랙 + 그린 빛 + 흰 숫자 / 코너 브래킷 / 와이어프레임 / 선형 차트
- ✅ 모든 수치에 `SOURCE` 라벨(작은 모노 캡션) 부착
- ❌ 파란·보라 AI 그라디언트, 다색 파이차트, 둥근 카드+그림자, 이모지
- ❌ 투자 권유로 읽히는 문구 ("지금 사야", 목표가). 서사는 '현상 설명'에 한정
- ❌ 공식 로고/서체를 허락 없이 변형 (사용 시 NVIDIA 브랜드 가이드 준수, 클리어스페이스·색 변경 금지)

## 확인이 필요한 항목

- 사용할 정확한 수치(ChatGPT 사용자 수, NVDA 주가·시총 구간)와 기준일 — 출시 시점에 최신 데이터로 검증
- 로고 사용 여부(공식 에셋 확보 vs. 텍스트 워드마크만 사용)
- 영상 길이·비율(16:9 vs 9:16)과 한글/영문 자막 여부
