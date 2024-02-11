---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# iteration Stement (While, For)

## 1. `while` statement

* 조건을 만족할 때 까지 반복한다.

### \[실습  1]&#x20;

* 구구단 2단 만들기&#x20;

```python
number = 0
while number < 10:
  print("2 x %d = %d" % (number, 2*number))
  number = number + 1 
```

```
2 x 1 = 2
2 x 2 = 4
2 x 3 = 6
2 x 4 = 8
2 x 5 = 10
2 x 6 = 12
2 x 7 = 14
2 x 8 = 16
2 x 9 = 18
```

### \[실습  2]&#x20;

* 실제로 커피 자판기는 커피 재고가 소진되었을 때 종료된다. 커피가 다 떨어질 때까지 반복되는 커피 자판기 프로그램을 설계하자.&#x20;

```python
# 자판기의 커피 수량
coffee = 5

# 커피가 남아있는 동안 작동!
while coffee > 0:

    # 실제로는 자판기를 통해서 넣은 금액.
    money = int(input("금액을 입력해주세요 : "))
    
    if money == 300:
        # 실제로 이 파트는 자판기에서 커피를 뽑는 명령으로 대체된다.
        print("Coffee")

        # 이제 커피를 하나씩 줄인다.
        coffee = coffee - 1

    elif money < 300:
        # 실제로 이 파트는 돈을 반환한다.
        print("%d원을 돌려줍니다." % money)
        
     
    else: # or elif money > 300:

        # 커피를 뽑아주고
        print("Coffee")
        # 이제 커피를 하나씩 줄인다.
        coffee = coffee - 1
        # 거스름돈을 돌려준다.
        print("%d원을 돌려줍니다." % (money-300))
        
    # 커피가 다 떨어진 경우 알려야한다.
print("커피가 모두 소진되었으니, 관리자에게 문의해주세요.")
```

```
금액을 입력해주세요 : 500
Coffee
200원을 돌려줍니다.
금액을 입력해주세요 : 300
Coffee
금액을 입력해주세요 : 150
150원을 돌려줍니다.
금액을 입력해주세요 : 1000
Coffee
700원을 돌려줍니다.
금액을 입력해주세요 : 700
Coffee
400원을 돌려줍니다.
금액을 입력해주세요 : 400
Coffee
100원을 돌려줍니다.
커피가 모두 소진되었으니, 관리자에게 문의해주세요.
```

## 2. <mark style="color:red;">`for`</mark> statement

* <mark style="color:red;">지정 횟수(반복 대상의 크기)</mark>까지만 반복한다( ↔ <mark style="color:green;">while</mark>문 - <mark style="color:green;">조건이 만족</mark>할 때까지만 반복).
* 반복 가능한 객체(iterable object) 즉, [연속형 데이터 타입 변수](#user-content-fn-1)[^1]를 대상으로 수행한다.

### \[실습 3]

```python
L = [1, 2]
s = "Python"
t = (1, 0, -1)
for i in t:
  print(i)
```

```
1
0
-1
```

### \[실습 4]

```python
beverages = ['콜라', '사이다', '환타', '제로콜라', '제로사이다']
for coffee in coffees:
  print(coffee)
```

```
콜라
사이다
환타
제로콜라
제로사이다
```

### ★ range() 함수

* for문은 지정한 횟수만큼만 반복하기에, 횟수가 자동으로 생성되는 것이 중요하다.&#x20;
* range함수는 특정 범위의 숫자 값들을 자동으로 생성한다. e.g. range(1, 6) -> 1, 2, 3, 4, 5&#x20;

> **range(**<mark style="color:red;">**x**</mark>**, **<mark style="color:green;">**y**</mark>**)  :  "**<mark style="color:red;">**x <=**</mark>** 숫자의 범위 **<mark style="color:green;">**< y**</mark>**"** &#x20;

```python
for i in range(1, 4):
  print(i)
```

```
1
2
3
```

### \[실습 5]

* 5,000원이 있을 때, 마실 수 있는 음료수는?

```python
beverages = ['콜라', '사이다', '환타', '제로콜라', '제로사이다']
prices = [4100, 4600, 4600, 5100, 6000]

for i in range(6): # for i in range(0, 6)
  if prices[i] <= 5000:
    print(beverages[i])
```

```
콜라
사이다
환타
```

### \[실습 6]&#x20;

* 특별 행사로 모든 음료의 값에서 500원이 할인되었다. 5,000원이 있을 때, 마실 수 있는 음료수는?

```python
beverages = ['콜라', '사이다', '환타', '제로콜라', '제로사이다']
prices = [4100, 4600, 4600, 5100, 6000]

# index
for i in range(len(beverages)):
  if prices[i] - 500 <= 5000:
    print(beverages[i])

print()
# enumerate
for idx, price in enumerate(beverages):
  if price - 500 <= 5000:
    print(beverages[idx])

print()
# zip
for beverages, price in zip(beverages, prices):
  if price - 500 <= 5000:
    print(beverages)
```

```
```

### ★ break (반복 중지)

* 반복이 더 이상 필요 없어 **중지**하고자 할 때 사용

```python
# 자판기의 커피 수량
coffee = 5

# 일단 작동!
while True: # 영원히 반복. (infinite loop)

    if coffee == 0:
        break
    # 실제로는 자판기를 통해서 넣은 금액.
    money = int(input("금액을 입력하세요."))

    
    if money == 300:
        # 실제로 이 파트는 자판기에서 커피를 뽑는 명령으로 대체된다.
        print("Coffee")
        # 이제 커피를 하나씩 줄인다.
        coffee = coffee - 1

    elif money < 300:
        # 실제로 이 파트는 돈을 반환한다.
        print("%d원을 반환합니다." % money)
     
    else: # or elif money > 300:
        print("Coffee")
        # 커피를 뽑아주고
        coffee = coffee - 1
        # 이제 커피를 하나씩 줄인다.
        print("%d원을 반환합니다." % (money-300))
        # 거스름돈을 돌려준다.
        
        
    # 커피가 다 떨어진 경우 알려야한다.
print("커피가 모두 소진되었으니, 관리자에게 문의해주세요.")
```

```
금액을 입력하세요.500
Coffee
200원을 반환합니다.
금액을 입력하세요.300
Coffee
금액을 입력하세요.500
Coffee
200원을 반환합니다.
금액을 입력하세요.700
Coffee
400원을 반환합니다.
금액을 입력하세요.1000
Coffee
700원을 반환합니다.
커피가 모두 소진되었으니, 관리자에게 문의해주세요.
```

### ★ continue (반복 건너뛰기)

* 특정 조건에만 반복을 건너 뛰고(skip) 싶을 때 사용&#x20;

```python
# 자판기의 커피 수량
coffee = 5
# 거스름돈 보관
change = 0

# 일단 작동!
while coffee > 0:

    # 실제로는 자판기를 통해서 넣은 금액.
    money = int(input("금액을 입력해주세요 : ")) # 150
    # 잔고와 합쳐서 체크.
    money = money + change

    
    if money == 300:
        # 실제로 이 파트는 자판기에서 커피를 뽑는 명령으로 대체된다.
        print("Coffee")
        # 이제 커피를 하나씩 줄인다.
        coffee = coffee - 1

    elif money < 300:
        # 돈을 더 받자.
        print("돈이 모자랍니다. 추가로 금액을 입력해주세요.")
        change = money # 잔고를 저장.
        continue # 정산을 하지 않고, skip.
        
    else: # or elif money > 300:
        print("Coffee")
        # 커피를 뽑아주고
        coffee = coffee - 1
        # 이제 커피를 하나씩 줄인다.
        print("%d원을 반환합니다." % (money-300))
        # 거스름돈을 돌려준다.

    # 정산
    change = 0
        
    # 커피가 다 떨어진 경우 알려야한다.
print("커피가 모두 소진되었으니, 관리자에게 문의해주세요.")
```

```
금액을 입력해주세요 : 300
Coffee
금액을 입력해주세요 : 500
Coffee
200원을 반환합니다.
금액을 입력해주세요 : 150
돈이 모자랍니다. 추가로 금액을 입력해주세요.
금액을 입력해주세요 : 200
Coffee
50원을 반환합니다.
금액을 입력해주세요 : 1500
Coffee
1200원을 반환합니다.
금액을 입력해주세요 : 100
돈이 모자랍니다. 추가로 금액을 입력해주세요.
금액을 입력해주세요 : 200
Coffee
커피가 모두 소진되었으니, 관리자에게 문의해주세요.
```

### \[실습 7]&#x20;

```python
for dan in range(2, 10):
  print("-" * 10)
  for number in range(1, 10):
    print("%d x %d = %d" % (dan, number, dan*number))
```

```
----------
2 x 1 = 2
2 x 2 = 4
2 x 3 = 6
2 x 4 = 8
2 x 5 = 10
2 x 6 = 12
2 x 7 = 14
2 x 8 = 16
2 x 9 = 18
----------
3 x 1 = 3
3 x 2 = 6
3 x 3 = 9
3 x 4 = 12
3 x 5 = 15
3 x 6 = 18
3 x 7 = 21
3 x 8 = 24
3 x 9 = 27
----------
4 x 1 = 4
4 x 2 = 8
4 x 3 = 12
4 x 4 = 16
4 x 5 = 20
4 x 6 = 24
4 x 7 = 28
4 x 8 = 32
4 x 9 = 36
----------
5 x 1 = 5
5 x 2 = 10
5 x 3 = 15
5 x 4 = 20
5 x 5 = 25
5 x 6 = 30
5 x 7 = 35
5 x 8 = 40
5 x 9 = 45
----------
6 x 1 = 6
6 x 2 = 12
6 x 3 = 18
6 x 4 = 24
6 x 5 = 30
6 x 6 = 36
6 x 7 = 42
6 x 8 = 48
6 x 9 = 54
----------
7 x 1 = 7
7 x 2 = 14
7 x 3 = 21
7 x 4 = 28
7 x 5 = 35
7 x 6 = 42
7 x 7 = 49
7 x 8 = 56
7 x 9 = 63
----------
8 x 1 = 8
8 x 2 = 16
8 x 3 = 24
8 x 4 = 32
8 x 5 = 40
8 x 6 = 48
8 x 7 = 56
8 x 8 = 64
8 x 9 = 72
----------
9 x 1 = 9
9 x 2 = 18
9 x 3 = 27
9 x 4 = 36
9 x 5 = 45
9 x 6 = 54
9 x 7 = 63
9 x 8 = 72
9 x 9 = 81
```

[^1]: 리스트, 튜플, 문자열
