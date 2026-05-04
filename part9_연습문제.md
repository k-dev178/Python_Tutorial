# Part 9. 연습문제

> 학습한 내용을 시험 형식으로 점검. **시간을 재고 풀어볼 것.**

---

## 9.1 코드 작성형 연습문제 (5문제, 권장 시간 30분)

### 문제 1. 두 정수 합
두 정수를 입력받아 합을 출력하시오.

```
입력: 7 (엔터) 5 (엔터)
출력: 12
```

### 문제 2. 짝홀 판별
정수 N을 입력받아 짝수면 "짝수", 홀수면 "홀수"를 출력하시오.

```
입력: 8
출력: 짝수
```

### 문제 3. 1~N 짝수의 합
정수 N을 입력받아 1부터 N까지의 짝수만 더한 결과를 출력하시오.

```
입력: 10
출력: 30
```

### 문제 4. 학생 점수 평균과 등급
정수 5개를 입력받아 평균을 출력하고, 평균에 따라 등급을 출력하시오.
- 90 이상: A
- 80 이상: B
- 70 이상: C
- 60 이상: D
- 그 외: F

```
입력: 90 85 70 60 95
출력:
80.0
B
```

### 문제 5. 최고 점수와 학생 위치
정수 N과 N개의 점수를 입력받아 최고 점수와 그 점수를 받은 학생의 번호(1번부터)를 출력하시오.

```
입력:
5
70 90 85 95 80
출력:
95 4
```

---

## 9.2 코드 작성형 연습문제 — 해설

### 문제 1
```python
a = int(input())
b = int(input())
print(a + b)
```

(입력 `7`, `5`)
```
12
```

### 문제 2
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

### 문제 3
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

### 문제 4
```python
nums = list(map(int, input().split()))
avg = sum(nums) / len(nums)
print(avg)

if avg >= 90:
    print("A")
elif avg >= 80:
    print("B")
elif avg >= 70:
    print("C")
elif avg >= 60:
    print("D")
else:
    print("F")
```

(입력 `90 85 70 60 95`)
```
80.0
B
```

### 문제 5
```python
n = int(input())
nums = list(map(int, input().split()))

max_val = nums[0]
max_idx = 0
for i in range(n):
    if nums[i] > max_val:
        max_val = nums[i]
        max_idx = i

print(max_val, max_idx + 1)
```

(입력 `5`, `70 90 85 95 80`)
```
95 4
```

---

---

## 9.3 코드 분석형 연습문제 (20문항)

> 코드를 보고 출력을 예측하거나 빈칸을 채우거나 버그를 고치는 문제.
> 직접 풀어본 뒤 정답 확인.

### 유형 A. 코드 읽기 — 결과 예측 (8문제)

#### Q1
```python
print(7 // 2, 7 % 2)
```

**정답 (출력)**
```
3 1
```

#### Q2
```python
a = "10"
b = "20"
print(a + b)
```

**정답 (출력)**
```
1020
```
> 문자열 이어붙이기.

#### Q3
```python
n = 1234
print(n // 100 % 10)
```

**정답 (출력)**
```
2
```
> 백의 자리.

#### Q4
```python
total = 0
for i in range(1, 6):
    total += i
print(total)
```

**정답 (출력)**
```
15
```

#### Q5
```python
x = 5
if x > 10:
    print("A")
elif x > 3:
    print("B")
else:
    print("C")
```

**정답 (출력)**
```
B
```

#### Q6
```python
nums = [10, 20, 30, 40, 50]
print(nums[1:4])
```

**정답 (출력)**
```
[20, 30, 40]
```

#### Q7
```python
s = "hello"
print(s[::-1])
```

**정답 (출력)**
```
olleh
```

#### Q8
```python
count = 0
for i in range(1, 21):
    if i % 3 == 0:
        count += 1
print(count)
```

**정답 (출력)**
```
6
```
> 3, 6, 9, 12, 15, 18 — 6개.

---

### 유형 B. 빈칸 채우기 (6문제)

#### Q9
1부터 N까지의 합을 구하는 코드:
```python
n = int(input())
total = 0
for i in range(1, ___):
    total += i
print(total)
```

**정답**: `n+1`

#### Q10
정수 5개의 평균을 구하는 코드:
```python
total = 0
for _ in range(5):
    n = int(input())
    total += n
print(total ___ 5)
```

**정답**: `/`

#### Q11
3의 배수만 출력하는 코드:
```python
for i in range(1, 31):
    if ___:
        print(i)
```

**정답**: `i % 3 == 0`

#### Q12
리스트의 최댓값을 찾는 코드:
```python
nums = [3, 7, 1, 9, 4]
max_val = nums[0]
for x in nums:
    if x ___ max_val:
        max_val = x
print(max_val)
```

**정답**: `>`

#### Q13
짝홀 판별 코드:
```python
n = int(input())
if ___ == 0:
    print("짝수")
else:
    print("홀수")
```

**정답**: `n % 2`

#### Q14
"hello"의 길이를 출력:
```python
s = "hello"
print(___)
```

**정답**: `len(s)`

---

### 유형 C. 디버깅 — 잘못된 부분 고치기 (6문제)

#### Q15
1부터 10까지의 합을 출력하려는 코드. 무엇이 잘못되었나?
```python
total = 0
for i in range(1, 10):
    total += i
print(total)
```

**정답**: `range(1, 10)`은 10을 포함하지 않음 → `range(1, 11)`로 수정. 결과 55.

#### Q16
무한루프가 발생하는 코드:
```python
i = 1
while i <= 5:
    print(i)
```

**정답**: `i += 1` 누락. while 안에 추가.

#### Q17
두 수의 합을 출력하려는 코드:
```python
a = input()
b = input()
print(a + b)
```

**정답**: `int(input())`로 형변환. 안 그러면 문자열 이어붙이기 됨.

#### Q18
1~10 합을 구하는데 결과가 항상 10:
```python
total = 0
for i in range(1, 11):
    total = 0
    total += i
print(total)
```

**정답**: for 안의 `total = 0`을 삭제 (매번 리셋되고 있음).

#### Q19
조건문 에러:
```python
x = 10
if x = 10:
    print("ten")
```

**정답**: `=` → `==`로 수정.

#### Q20
인덱스 에러:
```python
nums = [1, 2, 3]
print(nums[3])
```

**정답**: 인덱스는 0~2까지만. `nums[2]` 또는 `nums[-1]`로 수정.

---

## 9.4 채점 기준

### 코드 작성형 (50점)
- 문제 1: 5점
- 문제 2: 5점
- 문제 3: 10점
- 문제 4: 15점
- 문제 5: 15점

### 코드 분석형 (50점)
- Q1~Q8: 각 3점 (24점)
- Q9~Q14: 각 3점 (18점)
- Q15~Q20: 각 약 1.3점 (8점)

### 점수별 진단

| 점수 | 진단 | 권장 학습 |
|---|---|---|
| 90~100 | 시험 우수 통과 가능 | Part 7 풀이 전략 정독 후 시험 |
| 70~89 | 합격선 안정권 | 약한 부분 Part 1~6 복습 |
| 50~69 | 합격 가능, 보강 필요 | 7유형(Part 8)을 손으로 다시 적기 |
| 50 미만 | 기초 보강 필요 | Part 1~4 반복 + 누적 패턴 4가지 외우기 |