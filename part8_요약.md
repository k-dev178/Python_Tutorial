# Part 8. 요약

> 전체 내용 압축 정리. 시험 직전 한 번 훑어보기 좋게.

---

## 8.1 각 단원 한눈에

### Part 1. 입출력과 변수
- 출력: `print(...)`
- 입력: `n = int(input())` ← 항상 형변환
- 자료형: `int`, `float`, `str`, `bool`

### Part 2. 연산자
- 산술: `+ - * / // % **`
- 비교: `== != > < >= <=`
- 논리: `and`, `or`, `not`

### Part 3. 반복문
- `for i in range(1, n+1):`
- `while 조건:`
- 누적 패턴 4가지: 합 · 카운트 · 최대 · 최소

### Part 4. 조건문
- `if / elif / else`
- 들여쓰기로 블록 구분

### Part 5. 리스트와 문자열
- 인덱싱 `[i]` (0부터)
- 슬라이싱 `[a:b]` (b 미포함)
- 한 줄 입력: `nums = list(map(int, input().split()))`

### Part 6. 함수와 딕셔너리
- `def f(x): return ...`
- `d = {"key": value}`, `d["key"]`

### Part 7. 풀이 5단계
문제 읽기 → 입출력 확인 → `input()` → 로직 구현 → `print()`

---

## 8.2 7대 유형 템플릿

### 유형 1. 입력 → 계산 → 출력

```python
n = int(input())
print(n * 2)
```

(입력 `7`)
```
14
```

### 유형 2. 조건 분기 (if/elif/else)

```python
n = int(input())
if n % 2 == 0:
    print("짝수")
else:
    print("홀수")
```

(입력 `8`)
```
짝수
```

### 유형 3. 누적합 (1~N 합)

```python
n = int(input())
total = 0
for i in range(1, n+1):
    total += i
print(total)
```

(입력 `5`)
```
15
```

### 유형 4. 카운트 (개수 세기)

```python
count = 0
for i in range(1, 101):
    if i % 7 == 0:
        count += 1
print(count)
```

```
14
```

### 유형 5. 최댓값/최솟값 찾기

```python
nums = [3, 7, 1, 9, 4]
max_val = nums[0]
for x in nums:
    if x > max_val:
        max_val = x
print(max_val)
```

```
9
```

### 유형 6. 리스트 + 반복문 + 조건

```python
nums = list(map(int, input().split()))
for x in nums:
    if x > 5:
        print(x)
```

(입력 `3 7 1 9 4`)
```
7
9
```

### 유형 7. 문자열 다루기

```python
s = input()
print(len(s))
print(s[::-1])
print(s.count("a"))
print(s.split())
```

(입력 `apple banana cherry`)
```
19
yrrehc ananab elppa
3
['apple', 'banana', 'cherry']
```

---

## 8.3 자주 빠지는 함정 10선 ⚠️

| # | 함정 | 올바른 예 |
|---|---|---|
| 1 | `input()` 결과는 **문자열** | `n = int(input())` |
| 2 | `=` (대입) vs `==` (비교) | `if x == 5:` |
| 3 | `range(1, 10)`은 10 미포함 | 1~10 원하면 `range(1, 11)` |
| 4 | 인덱스는 **0부터** | `nums[0]`이 첫 번째 |
| 5 | 누적 변수는 반복 **밖에서** 초기화 | `total = 0`을 for 위에 |
| 6 | `True`, `False`는 **대문자** 시작 | `True`, 아닌 `true` |
| 7 | 들여쓰기 깊이가 구조를 결정 | 같은 블록은 같은 깊이 |
| 8 | `/` (실수 나누기) vs `//` (몫) | 정수 나누기는 `//` |
| 9 | while에서 변수 갱신 빠지면 무한루프 | `i += 1` 잊지 말기 |
| 10 | 문자열은 변경 불가 | `s[0] = "a"`는 에러 |
