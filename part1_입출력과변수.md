# Part 1. 입출력과 변수

> `print`, `input`, 변수, 자료형, 연산자. 이 한 묶음이 안 잡히면 그 다음이 다 무너진다.

---

## 1.1 print — 출력의 기본

```python
print("안녕하세요")
print(10)
print(3 + 5)
print("점수:", 90)
print("가", "나", "다")
```

```
안녕하세요
10
8
점수: 90
가 나 다
```

> 콤마(`,`)로 여러 값을 출력하면 자동으로 한 칸씩 띄어진다.

**여러 줄 출력**

```python
print("첫째 줄")
print("둘째 줄")
```

```
첫째 줄
둘째 줄
```

**🌟 [고급] 한 줄로 이어 출력 (sep, end)**

```python
print("a", "b", "c", sep="-")
print("끝", end="!")
```

```
a-b-c
끝!
```

---

## 1.2 변수 — 데이터에 이름 붙이기

```python
name = "민수"
age = 17
pi = 3.14
is_student = True

print(name, age)
print(pi, is_student)
```

```
민수 17
3.14 True
```

**규칙**
- 영문/숫자/언더스코어(`_`)만 사용
- 숫자로 시작 불가 (`1score` ✗, `score1` ✓)
- 공백 사용 불가 (`my score` ✗, `my_score` ✓)
- 대소문자 구별 (`Age`와 `age`는 다른 변수)

**값 바꾸기**

```python
x = 10
x = 20      # 덮어쓰기
x = x + 5   # x에 5 더한 값을 다시 x에
print(x)
```

```
25
```

---

## 1.3 자료형 — 데이터의 종류

| 자료형 | 예시 | 설명 |
|---|---|---|
| `int` (정수) | `10`, `-3`, `0` | 소수점 없는 수 |
| `float` (실수) | `3.14`, `0.5` | 소수점 있는 수 |
| `str` (문자열) | `"안녕"`, `'hi'` | 따옴표로 감싼 글자 |
| `bool` (불리언) | `True`, `False` | 참/거짓 (대문자 시작!) |

**자료형 확인 — `type()`**

```python
print(type(10))
print(type(3.14))
print(type("hi"))
print(type(True))
```

```
<class 'int'>
<class 'float'>
<class 'str'>
<class 'bool'>
```

**같은 모양이라도 자료형이 다르면 결과가 다르다**

```python
print(1 + 1)
print("1" + "1")
print("a" * 3)
```

```
2
11
aaa
```

---

## 1.4 input — 사용자에게 값 받기

**핵심 사실: `input()`은 항상 문자열을 반환한다.** (키보드는 글자만 친다)

```python
name = input("이름을 입력하세요: ")
print("안녕,", name)
```

(사용자가 `민수` 입력)
```
이름을 입력하세요: 민수
안녕, 민수
```

**숫자가 필요하면 반드시 형변환**

```python
age = input("나이: ")        # "17" (문자열)
age = int(age)              # 17 (정수)

# 한 줄로 줄여 쓰기 <- 보통 이걸 더 많이 씀
age = int(input("나이: "))
```

---

## 1.5 형변환 — 자료형 바꾸기

| 함수 | 역할 |
|---|---|
| `int(x)` | 정수로 변환 |
| `float(x)` | 실수로 변환 |
| `str(x)` | 문자열로 변환 |

```python
n = int("100")
f = float("3.14")
s = str(42)
print(n, f, s)
```

```
100 3.14 42
```

**문자열과 숫자를 함께 출력하려면 `str()` 또는 콤마 사용**

```python
score = 90
print("점수: " + str(score))
print("점수:", score)
```

```
점수: 90
점수: 90
```

**흔한 함정**

```python
a = input()
b = input()
print(a + b)
```

(사용자가 `5`, `3` 입력)
```
53
```

> 문자열끼리 이어붙이기가 됐다.

의도대로 하려면:

```python
a = int(input())
b = int(input())
print(a + b)
```

(사용자가 `5`, `3` 입력)
```
8
```

---

## 1.6 자주 빠지는 함정 ⚠️

1. **input의 결과는 문자열** → 숫자 연산 시 `int()` 빼먹지 말기
2. **`=`는 대입, `==`는 비교** — 절대 헷갈리지 말 것
3. **`/`는 항상 실수**, 정수 나눗셈은 `//`
4. **`True`, `False`는 대문자 시작** (`true`는 에러)
5. **변수명은 대소문자 구별** (`Score`와 `score`는 다른 변수)
6. **문자열과 숫자는 `+`로 못 합침** → `str()` 또는 콤마 사용

---

## 1.7 패턴

### 패턴 A. 입력 → 계산 → 출력

```python
n = int(input())
print(n * 2)
```

(입력 `7`)
```
14
```

### 패턴 B. 두 수 받아서 사칙연산

```python
a = int(input())
b = int(input())
print(a + b)
print(a - b)
print(a * b)
print(a / b)
```

(입력 `10`, `3`)
```
13
7
30
3.3333333333333335
```

### 패턴 C. 자릿수 분리

```python
n = int(input())
print(n // 1000)
print(n // 100 % 10)
print(n // 10 % 10)
print(n % 10)
```

(입력 `1234`)
```
1
2
3
4
```

### 패턴 D. 단위 변환 (예: 초 → 시:분:초)

```python
total = int(input())
h = total // 3600
m = total % 3600 // 60
s = total % 60
print(h, m, s)
```

(입력 `7384`)
```
2 3 4
```

> 7384초 = 2시간 3분 4초

---

## 1.8 연습문제

**1) 두 정수를 입력받아 합·차·곱·몫·나머지 출력**

**2) 원의 반지름을 입력받아 넓이 출력 (π = 3.14)**

**3) 4자리 정수를 입력받아 각 자릿수의 합 출력 (예: 1234 → 10)**

**4) 섭씨 온도를 입력받아 화씨로 변환 (F = C × 9/5 + 32)**

**5) 이름과 나이를 입력받아 "○○님은 ○○살입니다" 출력**

---

## 해설

**1)**
```python
a = int(input())
b = int(input())
print(a + b)
print(a - b)
print(a * b)
print(a // b)
print(a % b)
```

(입력 `10`, `3`)
```
13
7
30
3
1
```

**2)**
```python
r = float(input())
print(3.14 * r * r)
```

(입력 `5`)
```
78.5
```

**3)**
```python
n = int(input())
total = n // 1000 + n // 100 % 10 + n // 10 % 10 + n % 10
print(total)
```

(입력 `1234`)
```
10
```

**4)**
```python
c = float(input())
f = c * 9 / 5 + 32
print(f)
```

(입력 `25`)
```
77.0
```

**5)**
```python
name = input()
age = int(input())
print(name + "님은 " + str(age) + "살입니다")
```

(입력 `민수`, `17`)
```
민수님은 17살입니다
```
