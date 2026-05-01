# Part 5. 리스트와 문자열

> 데이터를 **묶어서** 다루는 방법. 반복문과 결합하면 사실상 모든 응용 문제를 풀 수 있다.

---

## 5.1 리스트 — 여러 값을 하나로 묶기

```python
nums = [10, 20, 30, 40, 50]
fruits = ["사과", "바나나", "포도"]
mixed = [1, "두", 3.0, True]
empty = []

print(nums)
print(fruits)
print(mixed)
print(empty)
```

```
[10, 20, 30, 40, 50]
['사과', '바나나', '포도']
[1, '두', 3.0, True]
[]
```

> 자료형을 섞어도 됨. 빈 리스트는 `[]`.

---

## 5.2 인덱싱 — 위치로 값 꺼내기

**인덱스는 0부터 시작한다.**

```python
nums = [10, 20, 30, 40, 50]
#       0   1   2   3   4

print(nums[0])
print(nums[2])
print(nums[-1])
print(nums[-2])
```

```
10
30
50
40
```

> 음수 인덱스는 뒤에서부터. `-1`이 마지막 값.

**값 변경**

```python
nums = [10, 20, 30, 40, 50]
nums[0] = 100
print(nums)
```

```
[100, 20, 30, 40, 50]
```

---

## 5.3 슬라이싱 — 부분 리스트 꺼내기

`리스트[시작:끝]` — **끝은 포함 안 됨**

```python
nums = [10, 20, 30, 40, 50]

print(nums[1:4])
print(nums[:3])
print(nums[2:])
print(nums[:])
print(nums[::2])
print(nums[::-1])
```

```
[20, 30, 40]
[10, 20, 30]
[30, 40, 50]
[10, 20, 30, 40, 50]
[10, 30, 50]
[50, 40, 30, 20, 10]
```

---

## 5.4 리스트 메서드

| 메서드 | 역할 | 예시 |
|---|---|---|
| `append(x)` | 끝에 추가 | `nums.append(60)` |
| `insert(i, x)` | 위치에 삽입 | `nums.insert(0, 5)` |
| `remove(x)` | 값 제거 (첫 번째) | `nums.remove(20)` |
| `pop()` | 마지막 값 제거+반환 | `last = nums.pop()` |
| `sort()` | 오름차순 정렬 | `nums.sort()` |
| `sort(reverse=True)` | 내림차순 | `nums.sort(reverse=True)` |
| `reverse()` | 순서 뒤집기 | `nums.reverse()` |
| `len(리스트)` | 개수 | `len(nums)` |
| `sum(리스트)` | 합 | `sum(nums)` |
| `max(리스트)` | 최댓값 | `max(nums)` |
| `min(리스트)` | 최솟값 | `min(nums)` |
| `값 in 리스트` | 포함 여부 | `30 in nums` |

```python
nums = [3, 1, 4, 1, 5]
nums.append(9)
print(nums)

nums.sort()
print(nums)

print(len(nums))
print(sum(nums))
print(max(nums))
print(4 in nums)
```

```
[3, 1, 4, 1, 5, 9]
[1, 1, 3, 4, 5, 9]
6
23
9
True
```

---

## 5.5 리스트와 반복문 — 핵심

### 모든 원소 출력

```python
nums = [10, 20, 30]
for x in nums:
    print(x)
```

```
10
20
30
```

### 인덱스와 함께 출력

```python
nums = [10, 20, 30]
for i in range(len(nums)):
    print(i, nums[i])
```

```
0 10
1 20
2 30
```

### 리스트의 합 직접 계산

```python
nums = [10, 20, 30, 40]
total = 0
for x in nums:
    total += x
print(total)
```

```
100
```

### 조건에 맞는 원소만 처리

```python
nums = [3, 7, 2, 9, 4]
for x in nums:
    if x > 5:
        print(x)
```

```
7
9
```

---

## 5.6 리스트 입력 받기

### N개의 정수를 입력받아 리스트로

```python
n = int(input())
nums = []
for _ in range(n):
    x = int(input())
    nums.append(x)

print(nums)
print(sum(nums))
```

(입력 `3`, `10`, `20`, `30`)
```
[10, 20, 30]
60
```

### 한 줄에 공백으로 구분된 값 받기

```python
nums = list(map(int, input().split()))
print(nums)
```

(입력 `10 20 30`)
```
[10, 20, 30]
```

> **흔한 한 줄짜리 트릭. 외워둘 것.**

---

## 5.7 문자열 — 사실 리스트와 비슷하다

```python
s = "hello"
#    01234

print(s[0])
print(s[-1])
print(s[1:4])
print(len(s))
print("e" in s)
```

```
h
o
ell
5
True
```

> ⚠️ **문자열은 변경 불가** — `s[0] = "H"`는 에러. 새 문자열을 만들어야 함.

---

## 5.8 문자열 메서드

| 메서드 | 역할 | 예시 |
|---|---|---|
| `upper()` | 대문자로 | `"hi".upper()` → `"HI"` |
| `lower()` | 소문자로 | `"HI".lower()` → `"hi"` |
| `replace(a, b)` | a를 b로 교체 | `"hello".replace("l", "L")` → `"heLLo"` |
| `split(s)` | s로 자르기 → 리스트 | `"a,b,c".split(",")` → `["a","b","c"]` |
| `join(리스트)` | 리스트를 합치기 | `"-".join(["a","b"])` → `"a-b"` |
| `strip()` | 양쪽 공백 제거 | `"  hi  ".strip()` → `"hi"` |
| `count(x)` | 등장 횟수 | `"banana".count("a")` → `3` |
| `find(x)` | 위치 (없으면 -1) | `"hello".find("l")` → `2` |

```python
s = "Hello World"
print(s.upper())
print(s.lower())
print(s.replace("l", "L"))
print(s.split())
print(s.count("o"))
print(len(s))
```

```
HELLO WORLD
hello world
HeLLo WorLd
['Hello', 'World']
2
11
```

---

## 5.9 문자열 반복문

```python
s = "hello"
for ch in s:
    print(ch)
```

```
h
e
l
l
o
```

**모음 개수 세기**

```python
s = input()
count = 0
for ch in s:
    if ch in "aeiouAEIOU":
        count += 1
print(count)
```

(입력 `Hello World`)
```
3
```

---

## 5.10 패턴 5종

### 패턴 1. 리스트 합·평균

```python
nums = list(map(int, input().split()))
print(sum(nums))
print(sum(nums) / len(nums))
```

(입력 `10 20 30 40 50`)
```
150
30.0
```

### 패턴 2. 리스트에서 특정 값 카운트

```python
nums = [1, 2, 3, 2, 1, 2]
target = 2
count = 0
for x in nums:
    if x == target:
        count += 1
print(count)
```

```
3
```

> 또는 `print(nums.count(2))` 한 줄로도 가능.

### 패턴 3. 최댓값의 위치(인덱스) 찾기

```python
nums = [3, 7, 1, 9, 4]
max_idx = 0
for i in range(len(nums)):
    if nums[i] > nums[max_idx]:
        max_idx = i
print(max_idx)
```

```
3
```

### 패턴 4. 문자열 뒤집기

```python
s = input()
print(s[::-1])
```

(입력 `hello`)
```
olleh
```

### 패턴 5. 단어 개수 세기

```python
s = input()
words = s.split()
print(len(words))
```

(입력 `Hello World Python`)
```
3
```

---

## 5.11 자주 빠지는 함정 ⚠️

1. **인덱스는 0부터** → `nums[1]`은 두 번째 값
2. **슬라이싱은 끝 포함 안 됨** → `nums[0:3]`은 0,1,2번 인덱스
3. **`len(리스트)`는 함수, `nums.len()`은 에러**
4. **빈 리스트는 `[]`** (괄호 종류 주의)
5. **문자열은 변경 불가** → `s[0] = "x"`는 에러
6. **`split()`은 공백 기준이 기본**, 다른 구분자는 `split(",")`
7. **`map(int, ...)`을 안 쓰면 문자열 리스트가 됨**

---

## 5.12 연습문제 8

**1) 정수 5개를 한 줄에 입력받아 합과 평균 출력**

**2) 리스트 `[5, 3, 8, 1, 9, 2, 7]`에서 5보다 큰 값만 출력**

**3) 문자열을 입력받아 길이와 첫 글자, 마지막 글자 출력**

**4) 문자열에서 "a"의 개수 세기**

**5) 리스트의 최댓값과 그 위치(인덱스) 출력**

**6) 문자열을 입력받아 거꾸로 출력 (예: "hello" → "olleh")**

**7) 정수 N개 입력 후, 리스트를 정렬해서 출력**

**8) 문장을 입력받아 단어 개수와 가장 긴 단어 출력**

---

## 해설

**1)**
```python
nums = list(map(int, input().split()))
print(sum(nums))
print(sum(nums) / len(nums))
```

(입력 `1 2 3 4 5`)
```
15
3.0
```

**2)**
```python
nums = [5, 3, 8, 1, 9, 2, 7]
for x in nums:
    if x > 5:
        print(x)
```

```
8
9
7
```

**3)**
```python
s = input()
print(len(s))
print(s[0])
print(s[-1])
```

(입력 `python`)
```
6
p
n
```

**4)**
```python
s = input()
print(s.count("a"))
```

(입력 `banana`)
```
3
```

**5)**
```python
nums = [3, 7, 1, 9, 4]
max_val = nums[0]
max_idx = 0
for i in range(len(nums)):
    if nums[i] > max_val:
        max_val = nums[i]
        max_idx = i
print(max_val, max_idx)
```

```
9 3
```

**6)**
```python
s = input()
print(s[::-1])
```

(입력 `hello`)
```
olleh
```

**7)**
```python
n = int(input())
nums = []
for _ in range(n):
    nums.append(int(input()))
nums.sort()
print(nums)
```

(입력 `4`, `5`, `2`, `8`, `1`)
```
[1, 2, 5, 8]
```

**8)**
```python
s = input()
words = s.split()
print(len(words))

longest = words[0]
for w in words:
    if len(w) > len(longest):
        longest = w
print(longest)
```

(입력 `Hello Python World`)
```
3
Python
```
