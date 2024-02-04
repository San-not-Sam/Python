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

# Copy 함수

### Function이란?

**수학적인 의미의 함수와 개념은 비슷하지만 역할이 다르다.**

* input이 들어와서 output이 정해진 규칙에 따라 나온다는 개념은 같지만, 프로그램에서의 하나의 함수는 **하나의 기능**을 나타낸다.
* 정확하게 함수는 특정 기능을 구현한 **코드 묶음**이다.
* def 함수이름(param1, param2, ... ): return
* 함수를 쓰는 이유는 **재사용성** 때문이다.

> 함수를 사용하는 가장 중요한 이유는 재사용성 때문이다. Reusability라고 하며, _**똑같은 구조의 코드가 반복되는 것을 피하기 위해 사용**_된다. 똑같은 구조의 코드는 보통 한 가지의 기능 단위로 묶이게 되며, 이 기능 단위를 코드로 묶어서 함수로 만든다.

### Python Function Definition

```python
# Function Definition
def add(a, b):
    # 입력받은 a, b를 더한 값을 돌려주는 함수.
    result = a + b
    return result

# Function Call
add(3, 5)
```

```
8
```

* 정확한 용어 구분은 중요하지만, 보통은 parameter라고 총칭한다. 크게 중요하진 않다.

**기억해야 할 것은, input --- (Function) ----> output 의 구조이며, 이 때 어떤 input parameter가 들어가서, 어떤 output parameter가 나오는지 주목해야한다.**

**연습삼아, 사칙연산을 모두 함수로 만들어보자.**

```python
def sub(a, b):
  return a - b

def mul(a, b):
  return a * b

def div(a, b):
  if b == 0:
    print("Do not divided by zero.")
    return
  return a / b

n1, n2 = 2, 0
print(sub(n1, n2))
print(mul(n1, n2))
print(div(n1, n2))
```

```
2
0
Do not divided by zero.
None
```

#### 함수 정의의 다양한 형태를 연습해보자!

**1. 가장 흔하게 사용되는 경우 -> 함수 parameter와 return이 모두 존재하는 경우.**

```python
def set_name(name):
  name = name.upper()
  print(f"Set name as {name}.")
  return name

name = set_name("Kim")
```

```
Set name as KIM.





'KIM'
```

**2. 함수 parameter는 없고 return이 존재하는 경우.**

```python
def save_file():
  save_flag = False
  with open("a.txt") as f:
    f.write(data)
    save_flag = True

  return save_flag
```

**3. 함수 parameter는 있는데 return이 없는 경우.**

```python
def save_file(file_path):
  with open(file_path) as f:
    f.write(data)
```

**4. 함수 parameter도 없고 return도 없는 경우.**

```python
def say_hi():
  print("Hi!")

say_hi()
```

```
Hi!
```

**Q. 만약에 함수의 입력 parameter의 개수를 모를땐 어떻게 해야할까?**

```python
def add_many(*args): # *(asterisk)를 앞에 붙이는 것으로 여러개의 parameter를 받아서 tuple로 변환하여 준다.   
  total = 0
  for arg in args:
    total += arg

  return total

print(add_many(1, 2, 3))
print(add_many(1, 2, 3, 4, 5))
print(add_many(1, 2, 3, 4, 5, 6, 7, 8, 9, 10))

def feed_forward(**kwargs): # kwargs -> dict
  pass
```

```
6
15
55
```

**Q. 만약에 parameter가 너무 많아서 몇 개만 입력 parameter로 넣고 싶을 땐 어떻게 해야할까?**

> 아래는 scikit-learn 라이브러리에 있는 logistic regression 모델의 **init** 함수 코드이다.

> parameter가 너무 많아서, 다 외울수도 없다. 이럴 땐 default parameter를 지정해놓고, 필요한 parameter만 입력받는다.

\-- 이렇게 정의되는 함수의 parameter를 **keyword parameter** 라고 한다.

![linear\_regression](https://drive.google.com/uc?id=1zSGj9LN7ArY19vgtsiiDawfxSQY8uUxD)

**Q. 코드를 작성할 때, 언제 이 부분은 함수로 구현해야겠다 라고 판단할 수 있을까?**

_**A. 똑같은 코드가 2번 이상 반복될 때.**_

#### 파라미터에 대해 조금 더 알아봅시다!

* 함수에서 사용되는 변수들에게는 효력 범위와 수명이 있습니다.

Q. 만약에 함수의 파라미터 변수 이름과, 함수를 호출하는 argument의 이름이 같은 경우에 어떻게 될까?

```python
# 효력 범위 : scope
# 수명 : lifetime

# global variable
a = 10
name = "Kim"

def change_name(name): # code block
  #global name # make local variable to global.
  print("2. ", name)

  name = "Lee"
  #id(name)

  return name

print("1. " , name)
name2 = change_name()
print("3. ", name) # "Lee"가 아니고 "Kim" -> "Kim"이 아니고 "Lee"
print("4. ", name2)
```

```
1.  Kim
2.  Kim
3.  Lee
4.  Lee
```

#### Lambda 함수를 사용해보자!

> Lambda Expression

* 굉장히 간단한 함수가 있는 경우, 한 줄짜리 함수로 간편하게 사용할 수 있다.
* 이런 함수를 Lambda 함수라고 하며, lambda 함수와 반복문을 통해 함수의 정의없이 다양한 프로그래밍이 가능하다.

```python
def add(a, b):
    return a+b

# lambda 함수로 바꾸면?
f = lambda a, b : a + b
print(f(3, 5))
print(add(3, 5))
```

```
8
8
```

Q. 아래 리스트의 원소들을 원소들의 길이에 따라 정렬하고 싶은 경우엔 어떻게 해야할까?

```python
def get_length(s):
  return len(s)

strings = ['yoon', 'kim', 'jessica', 'jeong']
strings.sort(key=lambda s : len(s)) # alphatical order -> 글자 길이에 따른 정렬.
strings
```

```
['kim', 'yoon', 'jeong', 'jessica']
```

#### 파이썬에 이미 정의되어 있는 함수들을 사용해보자!

```python
import math
# 수학 계산을 해봅시다.
number = 3.14
# 절대값, 올림, 내림
print(abs(number))
print(math.ceil(number))
print(math.floor(number))
# sin, cos
print(math.sin(number))
print(math.cos(number))
```

```
3.14
4
3
0.0015926529164868282
-0.9999987317275395
```

```python
# 복권 숫자를 만들어봅시다.
import random

random.randint(1, 45)
random.choices(list(range(1, 46)), k=6)
```

```
[15, 5, 23, 1, 13, 1]
```

```python
# 다양한 사전들을 써봅시다.
import collections
from collections import defaultdict

#D = collections.defaultdict(int)
D = defaultdict(int)
D
#collections.OrderedDict() -> python 3.9 이상부터 default가 됨.
```

```
defaultdict(int, {})
```
