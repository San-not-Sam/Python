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

# Copy If 조건문

\##If statement (조건문)

* 프로그램에서 가장 중요한 조건 판단이다.
* 모든 프로그램은 조건을 판단하여 다음 진행 과정을 결정한다.
* 파이썬은 if, elif, else 구문을 이용하여 조건을 사용할 수 있다.

> 간단한 예시를 생각해보자. **자판기에 들어갈 프로그램을 만들어야 한다.** 자판기에 입력된 돈이 300원이면 커피를 주고, 300원보다 적은 경우엔 돈을 그냥 돌려주고, 300원보다 많은 경우에는 커피와 함께 거스름돈을 주어야 한다. 이를 어떻게 구현할 수 있을까?

* 파이썬에서 if문을 사용하는 방법

```python
a = 7
# a가 5인데, a가 5와 같으면, True를 출력하고 싶다.
if a == 5:
  print("True")
```

> 조건문을 사용하기 위해선, 비교연산과 논리연산을 알아야 한다.

```python
# 같다, 다르다, 크다, 작다, 크거나 같다, 작거나 같다
a == b
a != b
a > b
a < b
a >= b
a <= b
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
```

> 비교연산과 논리연산의 공통점은 결과가 참(True) 또는 거짓(False)라는 것이다.

### 자판기를 만들어보자.

> _REMIND_

> **자판기에 들어갈 프로그램을 만들어야 한다.** 자판기에 입력된 돈이 300원이면 커피를 주고, 300원보다 적은 경우엔 돈을 그냥 돌려주고, 300원보다 많은 경우에는 커피와 함께 거스름돈을 주어야 한다. 이를 어떻게 구현할 수 있을까?

```python
money = 300
# 돈이 300원인데, 돈이 300원이랑 같으면 coffee를 준다.
if money == 300:
  print("Coffee")
```

```
Coffee
```

```python
money = 200
# 돈이 200원 있다. 그러면 어떻게 해야할까?
if money < 300:
  print("거스름돈 %d원을 돌려줍니다." % money)
```

```
거스름돈 200원을 돌려줍니다.
```

```python
money = 1000
# 돈이 1000원이 있는 경우에는?
if money > 300:
  print("Coffee")
  print("거스름돈 %d원을 돌려줍니다." % (money-300))
```

```
Coffee
거스름돈 700원을 돌려줍니다.
```

### 자판기 코드 다시 생각해보기

> if문에는 if가 아닌 경우에 해당하는 조건을 체크할 수 있는 elif(else if) 구문이 있다.

> 모든 if, elif 조건에 체크되지 않는 나머지 경우를 처리하는 else 구문도 있다.

**이를 자판기 예제에 다시 적용해보자.**

```python
money = 100
# 돈이 300원인데, 돈이 300원이랑 같으면 coffee를 준다.
if money == 300:
  print("Coffee")
elif money < 300:
  print("거스름돈 %d원을 돌려줍니다." % money)
else: # 나머지 케이스 == money > 300
  print("Coffee")
  print("거스름돈 %d원을 돌려줍니다." % (money-300))
```

```
거스름돈 100원을 돌려줍니다.
```

### if-elif-else 말고 nested 구조를 이용해 작성해보자.

```python
# nested if
money = 300
if money == 300:
  print("Coffee")
else:
  if money < 300:
    print("거스름돈 %d원을 돌려줍니다." % money)
  else:
    print("Coffee")
    print("거스름돈 %d원을 돌려줍니다." % (money-300))
```

```
Coffee
```
