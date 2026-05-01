# Part 6. 함수와 딕셔너리

> **기본형 한 가지씩만 외워두면 충분.**

---

## 6.1 함수가 왜 필요한가

같은 코드를 여러 번 쓸 때, 이름을 붙여 한 덩어리로 관리.

**함수 없이**

```python
print("=" * 20)
print("결과")
print("=" * 20)

print("=" * 20)
print("끝")
print("=" * 20)
```

```
====================
결과
====================
====================
끝
====================
```

**함수로**

```python
def line():
    print("=" * 20)

line()
print("결과")
line()
line()
print("끝")
line()
```

```
====================
결과
====================
====================
끝
====================
```

> 결과는 같지만, 코드를 바꾸고 싶을 때 한 곳만 수정하면 된다.

---

## 6.2 def — 함수 정의

### 가장 단순한 형태 (입력 X, 출력 X)

```python
def hello():
    print("안녕하세요")

hello()
hello()
```

```
안녕하세요
안녕하세요
```

### 매개변수 (입력) 받기

```python
def hello(name):
    print("안녕,", name)

hello("민수")
hello("영희")
```

```
안녕, 민수
안녕, 영희
```

### return — 결과 돌려주기

```python
def add(a, b):
    return a + b

result = add(3, 5)
print(result)
print(add(10, 20))
```

```
8
30
```

---

## 6.3 함수의 4가지 형태

| 입력 | 출력 | 예시 |
|---|---|---|
| 없음 | 없음 | `def line(): print("=" * 20)` |
| 있음 | 없음 | `def hello(name): print("안녕", name)` |
| 없음 | 있음 | `def get_pi(): return 3.14` |
| 있음 | 있음 | `def add(a, b): return a + b` ← 가장 많이 씀 |

---

## 6.4 변수의 범위 (scope)

함수 안에서 만든 변수는 함수 밖에서 못 본다.

```python
def f():
    x = 10

f()
print(x)
```

```
NameError: name 'x' is not defined
```

함수 밖 변수는 함수 안에서 **읽기**는 가능.

```python
y = 100

def g():
    print(y)

g()
```

```
100
```

---

## 6.5 패턴 (함수)

### 패턴 1. 함수로 짝홀 판별

```python
def is_even(n):
    if n % 2 == 0:
        return True
    else:
        return False

print(is_even(10))
print(is_even(7))
```

```
True
False
```

### 패턴 2. 함수로 합 계산

```python
def sum_to(n):
    total = 0
    for i in range(1, n+1):
        total += i
    return total

print(sum_to(10))
print(sum_to(100))
```

```
55
5050
```

### 패턴 3. 함수로 최댓값 찾기

```python
def find_max(nums):
    max_val = nums[0]
    for x in nums:
        if x > max_val:
            max_val = x
    return max_val

print(find_max([3, 7, 1, 9, 4]))
```

```
9
```

---

## 6.6 딕셔너리 — 이름표로 값 찾기

리스트는 **위치(인덱스)**로 찾고, 딕셔너리는 **이름(키)**으로 찾는다.

```python
score = {"국어": 90, "영어": 85, "수학": 95}

print(score["국어"])
print(score["수학"])
```

```
90
95
```

### 추가/변경

```python
score = {"국어": 90, "영어": 85, "수학": 95}
score["과학"] = 88
score["국어"] = 100
print(score)
```

```
{'국어': 100, '영어': 85, '수학': 95, '과학': 88}
```

### 삭제

```python
score = {"국어": 90, "영어": 85, "수학": 95}
del score["영어"]
print(score)
```

```
{'국어': 90, '수학': 95}
```

### 키 존재 여부

```python
score = {"국어": 90, "영어": 85, "수학": 95}
if "국어" in score:
    print("있음")
```

```
있음
```

### 모든 키/값 순회

```python
score = {"국어": 90, "영어": 85, "수학": 95}

for k in score:
    print(k, score[k])
```

```
국어 90
영어 85
수학 95
```

```python
score = {"국어": 90, "영어": 85, "수학": 95}

for k, v in score.items():
    print(k, v)
```

```
국어 90
영어 85
수학 95
```

---

## 6.7 패턴 (딕셔너리)

### 패턴: 빈도 세기

```python
s = "banana"
count = {}

for ch in s:
    if ch in count:
        count[ch] += 1
    else:
        count[ch] = 1

print(count)
```

```
{'b': 1, 'a': 3, 'n': 2}
```

### 패턴: 점수 평균

```python
score = {"국어": 90, "영어": 85, "수학": 95}
total = 0
for k in score:
    total += score[k]
print(total / len(score))
```

```
90.0
```

---

## 6.8 자주 빠지는 함정 ⚠️

1. **함수 정의 끝 콜론(`:`)** 누락 → SyntaxError
2. **return은 한 번 만나면 함수 종료** (그 뒤 코드는 실행 X)
3. **return 없는 함수는 None 반환** → `print(f())`가 `None` 출력
4. **딕셔너리 키는 따옴표 필수** (`score["국어"]`, `score[국어]`는 에러)
5. **존재하지 않는 키 접근 시 KeyError** → `in`으로 먼저 확인

---

## 6.9 연습문제 4

**1) 두 정수를 받아 합을 반환하는 함수 `add`를 정의하고 사용**

**2) 정수 N을 받아 N의 약수 개수를 반환하는 함수**

**3) 학생 이름과 점수가 든 딕셔너리에서 평균 점수 출력**
```python
students = {"민수": 80, "영희": 95, "철수": 70}
```

**4) 문자열을 받아 알파벳 빈도를 딕셔너리로 반환하는 함수**

---

## 해설

**1)**
```python
def add(a, b):
    return a + b

print(add(3, 5))
print(add(100, 200))
```

```
8
300
```

**2)**
```python
def count_divisors(n):
    count = 0
    for i in range(1, n+1):
        if n % i == 0:
            count += 1
    return count

print(count_divisors(12))
```

```
6
```

> 12의 약수: 1, 2, 3, 4, 6, 12 → 6개

**3)**
```python
students = {"민수": 80, "영희": 95, "철수": 70}
total = 0
for name in students:
    total += students[name]
print(total / len(students))
```

```
81.66666666666667
```

**4)**
```python
def freq(s):
    result = {}
    for ch in s:
        if ch in result:
            result[ch] += 1
        else:
            result[ch] = 1
    return result

print(freq("hello"))
```

```
{'h': 1, 'e': 1, 'l': 2, 'o': 1}
```
