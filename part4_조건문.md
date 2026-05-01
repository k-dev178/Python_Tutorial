# Part 4. 조건문

> "**컴퓨터에게 결정을 위임하는 도구**". 반복문과 결합하면 응용 폭이 매우 넓다.

---

## 4.1 조건문이 필요한 이유

```python
score = 85
print("합격")
```

```
합격
```

이건 의미가 없다. 점수가 30이든 100이든 무조건 "합격"만 찍는다. **점수에 따라 다르게 출력**하고 싶다.

```python
score = 85
if score >= 60:
    print("합격")
else:
    print("불합격")
```

```
합격
```

이게 조건문이다. **상황을 보고 다르게 행동하라**고 시키는 것.

---

## 4.2 if / else / elif

### if 만 — 조건이 참일 때만 실행

```python
score = 90
if score >= 60:
    print("합격")
```

```
합격
```

### if + else — 양자택일

```python
n = 7
if n % 2 == 0:
    print("짝수")
else:
    print("홀수")
```

```
홀수
```

### if + elif + else — 다중 분기

```python
score = 85
if score >= 90:
    print("A")
elif score >= 80:
    print("B")
elif score >= 70:
    print("C")
else:
    print("F")
```

```
B
```

> **중요**: `elif`는 **위 조건이 거짓일 때만** 검사된다. 위에서부터 차례로 확인.

---

## 4.3 들여쓰기 — 파이썬의 문법

다른 언어는 `{ }`로 묶지만, 파이썬은 **들여쓰기로 구조를 표현**한다.

```python
x = 5
if x > 0:
    print("양수")
    print("크다")
print("끝")
```

```
양수
크다
끝
```

> `print("양수")`, `print("크다")`는 if에 속함 (들여쓰기 됨).
> `print("끝")`은 if 밖이라 항상 실행됨.

**규칙**
- 들여쓰기는 **공백 4칸 또는 Tab** (둘 중 하나로 통일)
- 같은 블록은 **같은 깊이**여야 함
- 섞으면 **IndentationError**

---

## 4.4 비교/논리 연산자 (복습)

| 비교 | 의미 |
|---|---|
| `==` | 같다 |
| `!=` | 다르다 |
| `>`, `<` | 크다, 작다 |
| `>=`, `<=` | 크거나 같다, 작거나 같다 |

| 논리 | 의미 |
|---|---|
| `and` | 둘 다 참이어야 참 |
| `or` | 하나라도 참이면 참 |
| `not` | 반대로 |

### 활용 예시

```python
age = 17

if age >= 13 and age <= 19:
    print("청소년")

if age < 13 or age > 19:
    print("청소년 아님")
```

```
청소년
```

> 두 번째 if는 조건이 거짓이라 아무것도 출력되지 않음.

---

## 4.5 중첩 조건문

```python
score = 85
attendance = 90

if score >= 60:
    if attendance >= 80:
        print("최종 합격")
    else:
        print("출석 부족")
else:
    print("점수 미달")
```

```
최종 합격
```

**같은 일을 `and`로도 쓸 수 있다**

```python
score = 85
attendance = 90

if score >= 60 and attendance >= 80:
    print("최종 합격")
elif score >= 60:
    print("출석 부족")
else:
    print("점수 미달")
```

```
최종 합격
```

> 일반적으로 `and`로 쓰는 게 더 읽기 쉽다. 중첩은 깊어질수록 가독성이 떨어진다.

---

## 4.6 패턴 5종

### 패턴 1. 짝홀 판별

```python
n = int(input())
if n % 2 == 0:
    print("짝수")
else:
    print("홀수")
```

(입력 `7`)
```
홀수
```

### 패턴 2. 양수/음수/0

```python
n = int(input())
if n > 0:
    print("양수")
elif n < 0:
    print("음수")
else:
    print("0")
```

(입력 `-3`)
```
음수
```

### 패턴 3. 점수 → 등급

```python
score = int(input())
if score >= 90:
    print("A")
elif score >= 80:
    print("B")
elif score >= 70:
    print("C")
elif score >= 60:
    print("D")
else:
    print("F")
```

(입력 `85`)
```
B
```

### 패턴 4. 윤년 판별

```python
year = int(input())
if year % 4 == 0 and year % 100 != 0:
    print("윤년")
elif year % 400 == 0:
    print("윤년")
else:
    print("평년")
```

(입력 `2024`)
```
윤년
```

> 한 줄로 줄이면: `if (year % 4 == 0 and year % 100 != 0) or year % 400 == 0:`

### 패턴 5. BMI 판정

```python
weight = float(input())
height = float(input())
bmi = weight / (height * height)

if bmi < 18.5:
    print("저체중")
elif bmi < 23:
    print("정상")
elif bmi < 25:
    print("과체중")
else:
    print("비만")
```

(입력 `70`, `1.75`)
```
정상
```

> 70 / (1.75 × 1.75) ≈ 22.86 → 정상 범위.

---

## 4.7 반복문 + 조건문 조합

### 1~100 중 짝수만 출력

```python
for i in range(1, 101):
    if i % 2 == 0:
        print(i)
```

```
2
4
6
... (중간 생략)
98
100
```

### 1~100 중 3의 배수의 합

```python
total = 0
for i in range(1, 101):
    if i % 3 == 0:
        total += i
print(total)
```

```
1683
```

### 정수 5개 받아 양수 개수 세기

```python
count = 0
for _ in range(5):
    n = int(input())
    if n > 0:
        count += 1
print(count)
```

(입력 `1`, `-2`, `3`, `-4`, `5`)
```
3
```

---

## 4.8 코드 읽기 훈련

**다음 코드의 출력은?**

### Q1
```python
x = 10
if x > 5:
    if x > 15:
        print("A")
    else:
        print("B")
else:
    print("C")
```
<details><summary>정답</summary>B</details>

### Q2
```python
n = 7
if n % 2 == 0:
    print("짝")
elif n % 3 == 0:
    print("삼배")
elif n % 7 == 0:
    print("칠배")
else:
    print("기타")
```
<details><summary>정답</summary>칠배 (앞 조건 모두 거짓이라 elif 검사가 계속됨)</details>

### Q3
```python
a = 5
b = 10
if a > 3 and b < 5:
    print("A")
elif a > 3 or b < 5:
    print("B")
else:
    print("C")
```
<details><summary>정답</summary>B (and는 거짓, or에서 첫 조건 참)</details>

### Q4
```python
x = 0
if x:
    print("참")
else:
    print("거짓")
```
<details><summary>정답</summary>거짓 (0은 False로 취급)</details>

### Q5
```python
score = 85
grade = ""
if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
elif score >= 70:
    grade = "C"
print(grade)
```
<details><summary>정답</summary>B</details>

---

## 4.9 자주 빠지는 함정 ⚠️

1. **`=`(대입)와 `==`(비교) 혼동** → `if x = 5:`는 SyntaxError
2. **들여쓰기 불일치** → IndentationError
3. **`elif`는 위가 거짓일 때만 검사**됨 → 모든 if를 따로 쓰면 동작이 다름
4. **조건문 끝 콜론(`:`) 누락** → SyntaxError
5. **`and`, `or`, `not`은 소문자** (`AND`, `OR` ✗)
6. **0, 빈 문자열, 빈 리스트는 `False`로 취급됨**

---

## 4.10 연습문제 7

**1) 정수를 입력받아 양수/음수/0 판별**

**2) 점수를 입력받아 A/B/C/D/F 등급 출력**

**3) 두 정수 중 큰 수 출력**

**4) 세 정수 중 가장 큰 수 출력**

**5) 윤년 판별 프로그램**

**6) 1~100 중 4의 배수이면서 6의 배수가 아닌 수의 개수**

**7) 정수 N을 입력받아 N이 소수인지 판별 (1과 자기 자신만 약수)**

---

## 해설

**1)**
```python
n = int(input())
if n > 0:
    print("양수")
elif n < 0:
    print("음수")
else:
    print("0")
```

(입력 `0`)
```
0
```

**2)**
```python
s = int(input())
if s >= 90:
    print("A")
elif s >= 80:
    print("B")
elif s >= 70:
    print("C")
elif s >= 60:
    print("D")
else:
    print("F")
```

(입력 `75`)
```
C
```

**3)**
```python
a = int(input())
b = int(input())
if a > b:
    print(a)
else:
    print(b)
```

(입력 `7`, `12`)
```
12
```

**4)**
```python
a = int(input())
b = int(input())
c = int(input())
if a >= b and a >= c:
    print(a)
elif b >= c:
    print(b)
else:
    print(c)
```

(입력 `5`, `12`, `8`)
```
12
```

**5)**
```python
y = int(input())
if (y % 4 == 0 and y % 100 != 0) or y % 400 == 0:
    print("윤년")
else:
    print("평년")
```

(입력 `2000`)
```
윤년
```

**6)**
```python
count = 0
for i in range(1, 101):
    if i % 4 == 0 and i % 6 != 0:
        count += 1
print(count)
```

```
17
```

> 4의 배수 25개 중 6의 배수(12, 24, 36, 48, 60, 72, 84, 96) 8개를 빼면 17.

**7)**
```python
n = int(input())
is_prime = True
if n < 2:
    is_prime = False
else:
    for i in range(2, n):
        if n % i == 0:
            is_prime = False
            break

if is_prime:
    print("소수")
else:
    print("소수 아님")
```

(입력 `7`)
```
소수
```
