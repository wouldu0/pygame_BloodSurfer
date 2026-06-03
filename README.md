# 🩸 블러드 서퍼 (Blood Surfer)

## 🎬 시연 영상

[![블러드 서퍼 시연 영상](https://img.youtube.com/vi/USC7DWskQYw/0.jpg)](https://youtube.com/shorts/USC7DWskQYw?feature=share)

> **파이썬 기반 혈관 관리 액션 게임**  
> 혈류 속을 서핑하며 좋은 습관을 섭취하고 나쁜 습관을 파괴해 혈관을 정화하라!

---

## 📖 게임 소개

**블러드 서퍼**는 심혈관 질환 예방을 주제로 한 건강 기능성 게임입니다.  
플레이어는 혈관 속 캐릭터를 조종하여 60초 동안 혈관 청정도를 유지하고, 나쁜 생활습관 아이템을 피하면서 건강한 음식을 섭취해 혈관을 정화합니다.

- 오염된 혈관이 점차 깨끗해지는 과정을 시각적으로 연출
- 유해 요소가 신체에 미치는 영향을 직관적으로 체험
- 건강한 습관에 대한 동기부여를 제공하는 교육적 게임

---

## 🎮 조작법

| 키 | 동작 |
|---|---|
| `←` / `→` 방향키 | 캐릭터 이동 |
| `SPACE` | 일시정지 / 튜토리얼 확인 |
| `R` | 언제든지 초기화 및 재시작 |
| `ESC` | 게임 종료 |

---

## 🏆 승리 조건

- **60초** 동안 생존하면서 최종 혈관 청정도 **50% 이상** → ✅ MISSION COMPLETE!
- 혈관 청정도가 **0%** 가 되면 → ❌ HEART FAILURE...

---

## 🍎 아이템 설명

### 굿 아이템
| 아이템 | 효과 | 청정도 | 필살 게이지 |
|---|---|---|---|
| 브로콜리 | 혈관 염증 제거, 탄성 유지 | +8 | +12 |
| 블루베리 | 혈관 노화 방지, 혈압 감소 | +6 | +22 |
| 아보카도 | 혈압 감소, 혈관 탄성 유지 | +5 | +18 |
| 토마토 | 혈관 내벽 보호, 혈전 억제 | +4 | +16 |
| 아몬드 | 콜레스테롤 감소, 비타민 E | +3 | +28 |

### 배드 아이템
| 아이템 | 패널티 |
|---|---|
| 정크푸드 | 혈관 청정도 -10, 지방 장애물 증가 |
| 담배 | 혈관 청정도 -10, 2초간 시야 연기로 차단 |
| 술 | 혈관 청정도 -10, 좌우 방향 반전 |
| 스트레스 | 혈관 청정도 -10, 1초간 움직임 정지 |

### 필살기 아이템 (게이지 100% 도달 시 등장)
| 아이템 | 효과 |
|---|---|
| 덤벨 / 런닝머신 | 엑서사이즈 모드 발동, 청정도 +25, 5초간 배드 아이템 무효화 |
| 캡슐 | 청정도 +15, 5초간 굿 아이템 자석 효과 |

---

## ⚡ 특수 이벤트: 회식 파도

**30초 경과 시** 피할 수 없는 회식 파도가 밀려옵니다.  
정크푸드, 담배, 술이 동시에 대량 쏟아지며 BGM이 변경됩니다. 사전에 청정도와 필살기를 비축해두세요!

---

## 🛠 개발 환경 및 의존성

- **언어**: Python 3.x
- **핵심 라이브러리**: Pygame 3.1.1
- **표준 모듈**: `random`, `math`, `time`, `os`

### 설치

```bash
pip install pygame
```

### 실행

```bash
python pygame_ing.py
```

---

## 📁 프로젝트 구조

```
blood-surfer/
├── pygame_ing.py       # 메인 실행 파일
└── assets/             # 모든 리소스 파일
    ├── character.png
    ├── character_1.png
    ├── 3d_d_character.png
    ├── 3d_dm_character.png
    ├── 3d_stressed.png
    ├── b_character.png
    ├── wall.png
    ├── title.png
    ├── main.png
    ├── story1.png ~ story5.png
    ├── tutorial.png
    ├── pause.png
    ├── ending_win.png
    ├── ending_fail.png
    ├── 1.png / 2.png / 3.png / start.png
    ├── fat_small.png / fat_small1.png
    ├── 3d_junkfood.png / 3d_cigarette.png
    ├── 3d_alcohol.png / 3d_stress.png
    ├── 3d_broccoli.png / 3d_blueberry.png
    ├── 3d_avocado.png / 3d_tomato.png / 3d_almond.png
    ├── 3d_dumbbell.png / 3d_pill.png / 3d_treadmill.png
    ├── bgm.wav
    ├── tutorial.wav
    ├── cpr.wav / heartbeat.wav / hylight.wav
    ├── hit.wav / good.wav / bad.wav
    ├── powerup.wav / win.wav / lose.wav
    └── DungGeunMo.ttf  # 없으면 맑은고딕으로 자동 대체
```

> ⚠️ `assets/` 폴더 내 리소스 파일(이미지, 사운드)은 `.gitignore`에 의해 저장소에 포함되지 않습니다.  
> 별도로 전달받아 `assets/` 폴더에 배치해주세요.

---

## 🧩 주요 기술 구현

### 2D 환경에서의 3D 원근감 표현
- **원근 투영(Perspective Projection)** 공식 `pf = 150 / (z + 1)` 으로 깊이감 구현
- z값(거리)에 따라 오브젝트 크기와 위치가 동적으로 변화
- Depth Sorting으로 먼 객체 먼저 렌더링해 자연스러운 입체감 연출

### 실시간 난이도 조절
- 혈관 청정도가 낮아질수록 지방 장애물 수 자동 증가 (최대 55개)
- 시간 경과에 따른 스크롤 속도 및 아이템 생성 주기 조절

### 렌더링 최적화
- **이미지 아틀라스(Atlas)** 방식으로 스케일/회전 연산 캐싱
- 지방 장애물 및 아이템 이미지 사전 빌드로 프레임 드랍 방지

---

## 📄 라이선스

본 프로젝트는 교육 목적으로 제작되었습니다.
