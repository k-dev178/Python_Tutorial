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
