# AI 가계부 배틀 — 실습 시작점

> 영수증을 던지면 AI 둘이 내 지갑을 두고 싸운다 — PyCon Korea 2026 튜토리얼

**일시:** 2026년 8월 17일(월) 10:00–13:00 · 공간 1

**이 저장소에는 완성된 코드가 없습니다.** 오늘 여러분이 직접 채웁니다.

---

## 🚀 처음이신가요? 여기부터

**파이썬을 미리 설치하지 않으셔도 됩니다.** 아래 2번에서 설치할 `uv`라는 도구가
알아서 받아옵니다.

### 1. 터미널 열기

| | |
|---|---|
| **맥** | `Command` + `Space` → "터미널" 입력 → `Enter` |
| **윈도우** | 시작 메뉴에서 "PowerShell" 검색 → 실행 |
| **리눅스** | `Ctrl` + `Alt` + `T` |

### 2. uv 설치하기

**맥 / 리눅스**
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

**윈도우 (PowerShell)**
```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

설치가 끝나면 **터미널을 완전히 닫았다가 다시 열어 주세요.**

### 3. 이 저장소 내려받고 그 안으로 들어가기

```bash
git clone https://github.com/mindori/pycon2026-start.git
cd pycon2026-start
```

> `ls` 를 쳐서 `README.md` 와 `main.py` 가 보이면 제대로 들어온 것입니다.
> 이걸 안 하고 `uv sync` 를 치면 `No pyproject.toml found` 가 납니다.

### 4. 필요한 것 설치하기 — 파이썬 포함

```bash
uv sync
```

### 5. API 키 넣기 — 🔑 **키는 강사가 메일로 보내드립니다**

**발급받지 않으셔도 됩니다.** 실습용 Gemini API 키를 강사가 만들어 보내드리고,
비용도 강사가 부담합니다. 못 받으셨으면 **현장에서 메일 주소만 알려 주세요.**

**맥 · 리눅스**
```bash
cp .env.example .env
```

**윈도우 (PowerShell)**
```powershell
copy .env.example .env
```

만들어진 `.env` 를 편집기로 열어 받은 키를 붙여넣으세요. 앞뒤에 따옴표나 공백을
넣으면 안 됩니다.

### 6. 잘 됐는지 확인하기

```bash
uv run python check_env.py
```

✅ 가 다섯 개 나오면 준비 끝입니다.

---

## 📖 교재는 따로 있습니다

당일 진행은 **교재**를 보며 합니다. 코드 블록이 전부 거기 있습니다.

| 막 | 문서 | 시간 |
|---|---|---|
| 0막 | [환경 점검과 첫 호출](https://github.com/mindori/pycon2026/blob/main/docs/handbook/00-환경점검.md) | 20분 |
| 1막 | [본다 — 영수증을 데이터로](https://github.com/mindori/pycon2026/blob/main/docs/handbook/01-본다.md) | 30분 |
| 2막 | [정리한다 — 가계부 만들기](https://github.com/mindori/pycon2026/blob/main/docs/handbook/02-정리한다.md) | 10분 |
| 3막 | [토론한다 — 페르소나와 종료 조건](https://github.com/mindori/pycon2026/blob/main/docs/handbook/03-토론한다.md) | 25분 |
| 4막 | [판정관과 피날레](https://github.com/mindori/pycon2026/blob/main/docs/handbook/04-판정.md) | 15분 |

---

## 이 저장소에 무엇이 있고 무엇이 없나

**여러분이 채울 파일** — 지금은 안내문 한 줄만 들어 있습니다.

| 파일 | 언제 |
|---|---|
| `budget_battle/models.py` | 1막 · 3막 · 4막에서 나눠 씁니다 |
| `budget_battle/vision.py` | 1막 |
| `budget_battle/ledger.py` | 2막 |
| `budget_battle/personas.py` | 3막 |
| `budget_battle/debate.py` | 3막 |
| `budget_battle/judge.py` | 4막 |
| `main.py` | 막마다 통째로 갈아엎습니다 |

**미리 넣어둔 것** — 오늘 배울 내용이 아니라서 손대지 않습니다.

| 파일 | 왜 |
|---|---|
| `budget_battle/config.py` | 키 로딩·모델 ID·상수 |
| `budget_battle/client.py` | 재시도·백오프·캐시 폴백. 현장 와이파이가 흔들려도 진도가 멈추지 않게 하는 안전장치입니다 |
| `app.py` | 4막 피날레용 Streamlit 앱. 실행만 합니다 |
| `check_env.py` | 환경 진단 |
| `receipts/` | 샘플 영수증 7장 |
| `cache/` | AI 호출이 실패했을 때 쓰는 미리 뽑아둔 결과 |

---

## 🆘 완성본이 필요하시면

진도가 많이 밀렸거나, 집에 가서 답을 맞춰보고 싶으시면 **완성본 저장소**가 있습니다.

**https://github.com/mindori/pycon2026**

거기에는 모든 파일이 완성된 채로 들어 있고, 막별 스냅샷(`steps/`)과 교재도
함께 있습니다. **오늘 현장에서는 되도록 열지 마세요** — 직접 쳐보는 것이
오늘의 목적입니다.

---

## 준비물

- **노트북** (맥 / 윈도우 / 리눅스 무관)
- **API 키는 준비 안 하셔도 됩니다** — 강사가 메일로 보내드립니다
- **본인 영수증 3~5장** (선택)

> 💡 **품목이 찍힌 영수증**이 좋습니다. 편의점·카페·마트 영수증처럼 무엇을
> 샀는지 줄줄이 적힌 것이요. 카드 결제 전표(가맹점명과 승인금액만 있는 종이)만
> 있으면 AI가 "어디서 얼마"까지만 알 수 있어 토론이 심심해집니다.

---

## 자주 막히는 곳

| 증상 | 해결 |
|---|---|
| `No pyproject.toml found` | 폴더 밖입니다. `cd pycon2026-start` |
| `command not found: uv` | 터미널을 닫았다가 다시 열어 보세요 |
| `GOOGLE_API_KEY를 찾을 수 없습니다` | `.env` 를 만들고 강사가 보낸 키를 넣으셨는지 확인 (5번) |
| `ModuleNotFoundError: budget_battle` | 저장소 폴더 안에서 실행하고 계신지 확인하세요 |
| 실행이 멈춘 것 같아요 | 잠시 기다리세요. 코드가 알아서 재시도합니다 |

---

## 라이선스

[MIT License](LICENSE). 학습·실습 목적으로 자유롭게 활용하셔도 됩니다.
