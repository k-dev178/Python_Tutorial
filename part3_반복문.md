# Part 3. 반복문

> 반복문이 안 잡히면 모든 응용 문제가 막힌다.
> 핵심: **누적 패턴 4가지(합·카운트·최대·최소)**는 모두 한 뿌리에서 나온다.

---

## 3.1 반복문이 왜 필요한가

1부터 5까지 출력하고 싶다면?

```python
print(1)
print(2)
print(3)
print(4)
print(5)
```

```
1
2
3
4
5
```

만약 1부터 1000까지라면? → 사람이 1000줄을 칠 수 없다.
**반복문**은 같은 일을 컴퓨터에게 시키는 도구다.

```python
for i in range(1, 6):
    print(i)
```

```
1
2
3
4
5
```

---

## 3.2 for + range — 정해진 횟수만큼 반복

### range의 3가지 형태

```python
print(list(range(5)))
print(list(range(1, 6)))
print(list(range(1, 10, 2)))
print(list(range(10, 0, -1)))
```

```
[0, 1, 2, 3, 4]
[1, 2, 3, 4, 5]
[1, 3, 5, 7, 9]
[10, 9, 8, 7, 6, 5, 4, 3, 2, 1]
```

> **주의: `range(N)`은 0부터 시작해서 N-1까지** (N은 포함 X)

### 기본 형태

```python
for i in range(5):
    print(i)
```

```
0
1
2
3
4
```

```python
for i in range(1, 11):
    print(i)
```

```
1
2
3
4
5
6
7
8
9
10
```

### 들여쓰기는 반드시 일치

```python
for i in range(3):
    print(i)
print("끝")
```

```
0
1
2
끝
```

> `print(i)`는 for 안에 (3번 실행), `print("끝")`은 for 밖에 (1번 실행).

---

## 3.3 while — 조건이 만족되는 동안 반복

```python
i = 1
while i <= 5:
    print(i)
    i += 1
```

```
1
2
3
4
5
```

> ⚠️ `i += 1`을 빼먹으면 **무한루프**가 된다.

### 언제 for, 언제 while?
- **반복 횟수를 알 때** → `for`
- **언제 끝날지 모를 때(조건 만족 시 종료)** → `while`

---

## 3.4 break와 continue — 흐름 제어

### break — 반복 즉시 종료

```python
for i in range(10):
    if i == 5:
        break
    print(i)
```

```
0
1
2
3
4
```

### continue — 다음 반복으로 건너뛰기

```python
for i in range(10):
    if i % 2 == 0:
        continue
    print(i)
```

```
1
3
5
7
9
```

> 짝수면 `continue`로 건너뛰고, 홀수만 출력됨.

---

## 3.5 누적 패턴 4가지

**여러 형태로 변형되는 패턴. 뼈대를 외우자.**

### A. 합 (sum)

```python
total = 0
for i in range(1, 11):
    total = total + i
print(total)
```

```
55
```

### B. 카운트 (count)

```python
count = 0
for i in range(1, 101):
    if i % 7 == 0:
        count = count + 1
print(count)
```

```
14
```

> 1~100 중 7의 배수는 14개.

### C. 최댓값

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

### D. 최솟값

```python
nums = [3, 7, 1, 9, 4]
min_val = nums[0]
for x in nums:
    if x < min_val:
        min_val = x
print(min_val)
```

```
1
```

> **이 4가지는 본질이 같다**: 변수 하나를 만들어두고, 반복하면서 그 변수를 갱신한다.

---

## 3.6 패턴 6종

### 패턴 1. 1~N 합

```python
n = int(input())
total = 0
for i in range(1, n+1):
    total += i
print(total)
```

(입력 `10`)
```
55
```

### 패턴 2. 약수 구하기

```python
n = int(input())
for i in range(1, n+1):
    if n % i == 0:
        print(i)
```

(입력 `12`)
```
1
2
3
4
6
12
```

### 패턴 3. 구구단 (특정 단)

```python
n = int(input())
for i in range(1, 10):
    print(n, "x", i, "=", n*i)
```

(입력 `7`)
```
7 x 1 = 7
7 x 2 = 14
7 x 3 = 21
7 x 4 = 28
7 x 5 = 35
7 x 6 = 42
7 x 7 = 49
7 x 8 = 56
7 x 9 = 63
```

### 패턴 4. 별찍기 (직각삼각형)

```python
n = int(input())
for i in range(1, n+1):
    print("*" * i)
```

(입력 `4`)
```
*
**
***
****
```

### 패턴 5. 자릿수 합 (반복으로)

```python
n = int(input())
total = 0
while n > 0:
    total += n % 10
    n = n // 10
print(total)
```

(입력 `1234`)
```
10
```

> 1234 → 4 + 3 + 2 + 1 = 10

### 패턴 6. 0이 입력될 때까지 반복

```python
total = 0
while True:
    n = int(input())
    if n == 0:
        break
    total += n
print(total)
```

(입력 `5`, `3`, `7`, `0`)
```
15
```

---

## 3.7 중첩 반복 — 격자 사고

반복문 안에 반복문이 있는 구조. 표/격자/2차원 데이터에 사용.

### 구구단 전체

```python
for i in range(2, 10):
    for j in range(1, 10):
        print(i, "x", j, "=", i*j)
    print()
```

```
2 x 1 = 2
2 x 2 = 4
... (중간 생략)
2 x 9 = 18

3 x 1 = 3
...
9 x 8 = 72
9 x 9 = 81

```

### 별찍기 (사각형)

```python
n = 3
for i in range(n):
    for j in range(n):
        print("*", end="")
    print()
```

```
***
***
***
```

> `end=""`로 줄바꿈 없이 같은 줄에 `*`을 찍고, 안쪽 for가 끝나면 `print()`로 줄바꿈.

### 별찍기 (피라미드)

```python
n = 4
for i in range(1, n+1):
    print(" " * (n-i) + "*" * (2*i-1))
```

```
   *
  ***
 *****
*******
```

---

## 3.8 자주 빠지는 함정 ⚠️

1. **`range(1, 10)`은 10을 포함하지 않는다** → 1~10을 원하면 `range(1, 11)`
2. **while에서 변수 갱신을 빼먹으면 무한루프** (`i += 1` 잊지 말기)
3. **들여쓰기 깊이로 어디까지가 반복인지 결정됨** → 한 칸이라도 다르면 결과가 달라짐
4. **누적합 변수는 반복 시작 전에 초기화** (`total = 0`을 for 안에 넣으면 매번 0으로 리셋!)
5. **`break`는 자기 단계의 반복만 끝낸다** (중첩에서 안쪽 break는 바깥쪽까진 안 빠져나옴)

---

## 3.9 연습문제 10

**1) 1부터 100까지의 합 출력**

**2) 1부터 N까지 짝수만 더한 합 출력 (N 입력)**

**3) N의 모든 약수 출력 후, 약수의 개수도 출력**

**4) 1부터 100까지 중 3의 배수 또는 5의 배수의 합**

**5) 별찍기 직각삼각형 (N 입력)**

**6) 정수 5개 입력받아 최댓값 출력**

**7) 정수를 계속 입력받다가 음수가 나오면 종료, 합 출력**

**8) N 팩토리얼 (1×2×3×...×N) 계산**

**9) 1부터 시작해서 합이 처음으로 100을 넘는 수 찾기**

**10) 1234와 같은 4자리 수의 각 자릿수를 거꾸로 출력 (4 3 2 1)**

---

## 해설

**1)**
```python
total = 0
for i in range(1, 101):
    total += i
print(total)
```

```
5050
```

**2)**
```python
n = int(input())
total = 0
for i in range(1, n+1):
    if i % 2 == 0:
        total += i
print(total)
```

(입력 `10`)
```
30
```

**3)**
```python
n = int(input())
count = 0
for i in range(1, n+1):
    if n % i == 0:
        print(i)
        count += 1
print("개수:", count)
```

(입력 `12`)
```
1
2
3
4
6
12
개수: 6
```

**4)**
```python
total = 0
for i in range(1, 101):
    if i % 3 == 0 or i % 5 == 0:
        total += i
print(total)
```

```
2418
```

**5)**
```python
n = int(input())
for i in range(1, n+1):
    print("*" * i)
```

(입력 `3`)
```
*
**
***
```

**6)**
```python
max_val = int(input())
for _ in range(4):
    x = int(input())
    if x > max_val:
        max_val = x
print(max_val)
```

(입력 `5`, `12`, `8`, `3`, `20`)
```
20
```

**7)**
```python
total = 0
while True:
    n = int(input())
    if n < 0:
        break
    total += n
print(total)
```

(입력 `5`, `3`, `7`, `-1`)
```
15
```

**8)**
```python
n = int(input())
result = 1
for i in range(1, n+1):
    result *= i
print(result)
```

(입력 `5`)
```
120
```

**9)**
```python
total = 0
i = 0
while total <= 100:
    i += 1
    total += i
print(i)
```

```
14
```

> 1+2+3+...+14 = 105 (100을 처음 넘는 시점)

**10)**
```python
n = int(input())
while n > 0:
    print(n % 10, end=" ")
    n //= 10
```

(입력 `1234`)
```
4 3 2 1 
```
