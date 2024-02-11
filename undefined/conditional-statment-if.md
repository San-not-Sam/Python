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

# Conditional Statment (If)

## 1. 비교/논리 연산

```python
a == b # 같다
a != b # 다르다
a > b # 크다
a < b # 작다
a >= b # 크거나 같다
a <= b # 작거나 같다
```

```python
# A and B
# A = a > 5
# B = b < 6
A and B
# A or B
A or B
# not A
not A

비교연산과 논리연산의 공통점은 결과가 참(True) 또는 거짓(False)라는 것이다.
```

**\[해결할 문제]** &#x20;

> 커피 자판기를 구동할 프로그램을 만들어야 한다. 200원을 투입하면 커피를 내려주고, 200원 이상의 금액을 투입할 경우 거스름돈과 함께 커피를 내려주고, 200원 이하의 금액을 투입하면 투입액을 모두 돌려 주는 프로그램을 코드로 어떻게 구현할 수 있을까?&#x20;

## \[실습 1] if문

```python
money = 200
if money == 200:
  print("Coffee")
```

```
Coffee
```

```python
money = 100
if money < 200:
  print("거스름돈 %d원을 돌려줍니다." % money)
```

```
거스름돈 200원을 돌려줍니다.
```

```python
money = 1000
if money > 200:
  print("Coffee")
  print("거스름돈 %d원을 돌려줍니다." % (money-200))
```

```
Coffee
거스름돈 800원을 돌려줍니다.
```

## \[실습 2] if-elif-else문

* elif 조건에 체크되지 않는 나머지 경우를 처리할 때 사용한다.&#x20;

```python
money = 100
# 돈이 300원인데, 돈이 300원이랑 같으면 coffee를 준다.
if money == 200:
  print("Coffee")
elif money < 200:
  print("거스름돈 %d원을 돌려줍니다." % money)
else: # 나머지 케이스 == money > 200
  print("Coffee")
  print("거스름돈 %d원을 돌려줍니다." % (money-100))
```

```
거스름돈 100원을 돌려줍니다.
```

## \[실습 3] nested 구조

```python
# nested if
money = 300
if money == 200:
  print("Coffee")
else:
  if money < 200:
    print("거스름돈 %d원을 돌려줍니다." % money)
  else:
    print("Coffee")
    print("거스름돈 %d원을 돌려줍니다." % (money-300))
```

```
Coffee
```
