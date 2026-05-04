# Part 0. 파이썬 설치

> 코드를 실행하려면 컴퓨터에 **파이썬**이 깔려 있어야 한다.
---

# 윈도우 설치

## 다운로드

- [https://www.python.org/downloads](https://www.python.org/downloads)
- 노란색 **Download Python 3.x.x** 버튼 클릭

운영체제는 자동 감지된다.

## 실행 및 설치

다운로드한 `python-3.x.x.exe` 실행.

> **가장 중요한 한 가지**
> 설치 첫 화면 아래쪽 **"Add python.exe to PATH"** 체크박스를 **반드시** 체크할 것.

체크 안 하면 나중에 cmd에서 파이썬을 못 찾는다.
체크 후 **Install Now** 클릭 → 1~2분 대기 → **Close**.

## 설치 확인

- **시작 → cmd** 검색해서 명령 프롬프트 열기
- 다음 입력:
  ```
  python --version
  ```
- `Python 3.x.x` 같이 버전이 뜨면 성공.

---

# 맥 설치

맥 사용시 homebrew를 사용하자.

> \> homebrew란?
> macOS 및 Linux 환경에서 터미널 명령어를 통해 소프트웨어를 손쉽게 설치, 업데이트, 삭제할 수 있게 해주는 오픈소스 패키지 관리자

## Homebrew 설치

* terminal/iterm2에서 다음 명령어 복붙
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
<br>
* 자세한 내용은 아래에서
[https://brew.sh/](https://brew.sh/)

### 명령어

터미널에서:
```
brew install python
```

업데이트는 `brew upgrade python`.

## 설치 확인

- terminal/iterm2 에서 다음과 같이 입력:
  ```
  python3 --version
  ```
- `Python 3.x.x` 같이 버전이 뜨면 성공.

> Mac은 보통 `python`이 아니라 `python3`로 입력해야 한다.

---

## 설치 안 될 때

| 증상 | 원인 / 해결 |
|---|---|
| `python은 내부 또는 외부 명령이 아닙니다` (Windows) | "Add to PATH" 체크 안 함 → 재설치하면서 체크 |
| `command not found: python` (Mac) | `python3`로 입력 (Mac은 python3가 표준) |
| 설치 중 권한 오류 | 관리자 권한으로 실행 / 비밀번호 입력 |
| `brew: command not found` (Mac) | Homebrew 미설치 → [brew.sh](https://brew.sh) 안내대로 설치 후 재시도 |

---

# IDLE로 코드 실행하기

**IDLE**은 파이썬 설치하면 같이 깔리는 기본 코드 편집기.
처음에는 IDLE 하나로 충분하다.

## IDLE 열기

- **윈도우**: 시작 메뉴에서 `IDLE` 검색 → `IDLE (Python 3.x)` 클릭
- **맥**: Spotlight(⌘+Space)에서 `IDLE` 검색 → 실행

열면 `>>>` 가 보이는 창이 뜬다. 이게 **Shell(셸) 창**.

## 방법 1. Shell에 바로 입력 (간단 테스트용)

`>>>` 옆에 코드를 한 줄씩 입력하고 엔터.

```
>>> print("hello")
hello
>>> 1 + 2
3
```

한 줄짜리 확인할 때 편하다. 단, 창을 닫으면 코드는 사라짐.

## 방법 2. 파일로 저장해서 실행 (실제 과제용)

1. IDLE Shell 창에서 메뉴 **File → New File** (또는 `Ctrl+N` / `⌘+N`)
2. 새 창이 뜨면 코드 작성:
   ```python
   print("hello")
   print(1 + 2)
   ```
3. **File → Save** (또는 `Ctrl+S` / `⌘+S`) → 파일명 `test.py`로 저장
4. **Run → Run Module** 또는 **F5** 키
5. Shell 창에 결과 출력:
   ```
   hello
   3
   ```

> 실제 시험·과제는 **방법 2**로 작성한다. `.py` 파일로 저장해야 코드를 다시 열고 수정할 수 있음.

## 주의사항

- **저장 안 하고 F5**: 저장하라는 창 뜸 → 저장하면 그대로 실행됨
- **확장자 빼먹기**: 꼭 `.py`로 저장. 다른 확장자면 파이썬으로 인식 안 됨
- **에러 메시지가 빨간 글씨로 뜸**: 당황하지 말고 마지막 줄 읽기. `SyntaxError`, `NameError` 같은 단어가 어떤 종류 에러인지 알려준다.
