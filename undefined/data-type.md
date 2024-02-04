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

# Data Type

## 변수(Variable)이란?

* 변수는 메모리에 데이터를 저장하기 위한 공간을 가리키는 말이며, 컴퓨터와 프로그래밍 언어 사용자간의 약속이다.

> a : 컴퓨터와 사용자가 인식하는 특정 데이터를 저장하고 있는 공간이고, 공간의 이름을 a라고 한다.

* 변수는 일종의 닉네임으로, 실제 물리적인 메모리 주소공간을 가리킨다.

> 사용자는 변수의 이름으로 데이터를 인식하고, 컴퓨터는 변수의 주소로 데이터를 인식합니다.

* 변수에 데이터를 저장할 때는 =를 사용한다. 이 때 =를 assignment operator라고 부른다.

> a = 10 (a라는 공간에, 10이라는 데이터를 할당해주세요.)

(OPTIONAL) a = 10을 예로 들었을 때, =을 기준으로 왼쪽을 lvalue라고 하며 실제 메모리 주소를 의미하고, =을 기준으로 오른쪽을 rvalue고 하며 실제 데이터(또는 값)을 의미한다.

```python
# 변수 a에 10이라는 정수 데이터를 할당(assign)한다.
a = 10
```

```python
# a라는 변수가 실제 메모리에서 저장되어 있는 위치.(메모리 주소)
id(a)
```

```
  File "<ipython-input-5-34dfda666408>", line 3
    10 = a
          ^
SyntaxError: can't assign to literal
```

## Q. 왜 data type은 여러가지 일까?

* 다음 질문에 대해 생각해보자.

> Q1. 컴퓨터는 정수와 실수를 어떻게 인식할까? (어떻게 구분할까)

> Q2. 100개의 숫자를 한꺼번에 다루고 싶을 때 어떻게 해야할까?

> Q3. 컴퓨터는 문자를 어떻게 인식할까?

> Q4. 많은 데이터를 빠르게 찾아야 할때는 어떻게 저장할까?

* 위 질문에 대한 대답을 data type을 배우면서 생각해봅시다.
*



## 1. 숫자 데이터 (Numeric Data Types)

* 숫자형 데이터란, 정수/실수/복소수/2진수/8진수/16진수를 포함하며 가장 많이 사용하는 데이터 타입중에 하나다.
* 파이썬은 숫자의 표현 범위가 무한대이다.
* 숫자 데이터는 우리가 알고 있는 대부분의 연산을 그대로 지원한다. 사칙연산, 나머지 구하기, 몫 구하기, 거듭제곱 등

### 1) 정수형 (Integer)

```python
1+1
```

```
2
```

```python
# a에 10, b에 5를 할당하고, a와 b를 더한 결과를 출력합니다.
a = 10
b = 5
a + b
```

```
15
```

```python
a - b
```

```
5
```

```python
type(b)
```

```
int
```

### 2) 실수형 (Floating point)

```python
c = 3.14
c
```

```
3.14
```

```python
c + 3.14
```

```
6.28
```

```python
# d에 4를 할당하고 c에서 d를 뺀 값을 출력합니다.
d = 4
c - d # -0.86
```

```
-0.8599999999999999
```

```python
# 1.34 x 10^6을 의미한다.
e = 1.34E6; e2 = 1.34e-3 # 1.34 x 10^(-3)
e, e2
```

```
(1340000.0, 0.00134)
```



### 3) 연산하기&#x20;

**(1) 사칙연산**

```python
# a에 10, b에 3을 할당하고 a와 b의 사칙연산 결과를 출력합니다. 이번에는 출력할때 print 함수를 사용합니다.
a = 10
b = 3
print(a + b)
print(a - b)
print(a * b)
print(a / b)
```

```
13
7
30
3.3333333333333335
```

```python
# a에 10.3, b에 -1.6을 할당하고 사칙연산 결과를 출력합니다.
a = 10.3
b = -1.6
```

**(2) 특수연산**

```python
c = 5
d = 2
print(c ** d) # c를 d번 곱한 것. c^d
print(c // d) # c를 d로 나눈 몫.
print(c % d)  # c를 d로 나눈 나머지.
```

```
25
2
1
```

**Q. 어떤 연도를 N이라고 할 때, N이 윤년인지 아닌지 알아보는 방법은 무엇일까?**

_A. 윤년 규칙. N이 4의 배수이면서, 100의 배수가 아니거나 400의 배수면 윤년이다._

```python
N % 4
N % 100
N % 400
```

## 2. 문자열(String)

* 문자열 데이터란, 문자(character)의 나열을 의미한다. e.g. "Hello world"

> string ; Character Sequence

* 파이썬에 다룰 수 있는 문자열의 크기도 제한이 없다.
* 파이썬에선 '와 " 두 가지의 기호를 통해 문자열을 나타낸다. 즉 ' 부터 ' 까지 또는 " 부터 " 까지 하나의 문자열이다. e.g. 'Hello', "World"
* 컴퓨터는 문자(character)를 encoding하여 숫자로 표현한다. 알려진 예로 ASCII, utf-8, cp949가 있다.

> 컴퓨터는 문자를 숫자로 인식한다. e.g. ASCII 코드로 변환하면 A->65, a->97

* 현재 전세계적으로 웹에서 사용되는 국제 표준은 UTF-8(Universal code character set Transformation Format - 8-bit)이다.

**(OPTIONAL)** UTF-8에선 a는 1바이트로, '가'는 3바이트로 인식한다. 이를 가변 인코딩 방식이라고 하며, 영어보다 한글이 더 많은 데이터를 필요로 한다.

### 1) 만드는 여러 방법

```python
s = 'Hello World'
s
```

```
'Hello World'
```

```python
s1 = """kim yong dam
is
smart."""
s1
```

```
'kim yong dam\nis\nsmart.'
```

```python
s2 ="""To Be Great is
To Be Misunderstood.
- Ralph Waldo Emerson
"""
print(s2) # 그냥 s2만 쓰면 어떻게 될까?
s2
```

```
To Be Great is
To Be Misunderstood.
- Ralph Waldo Emerson






'To Be Great is\nTo Be Misunderstood.\n- Ralph Waldo Emerson\n'
```

```python
# 왜 파이썬은 ""와 ''를 모두 제공할까요?
# 아래 s3와 s4를 문자열로 만들어서 출력해봅시다. 
s3 = "I'm a boy."
s4 = 'She said, "Go away!"'
print(s3)
print(s4)
```

```
I'm a boy.
She said, "Go away!"
```

### 2) 특수 문자 표현 (escape code)&#x20;

```python
# \n -> new line
print("Hello\n\n\n\n\nWorld")
```

```
Hello




World
```

```python
# \t -> tab
print("Hello\t\t\t\t\t\tWorld")
```

```
Hello						World
```

### 3) 연산하기

> 문자열의 사칙연산은 어떻게 정의될까? 숫자에선 당연했지만, 문자열의 더하기, 곱하기는 어떻게 정의되는지 잘 생각해보자.

```python
s = "Hello"
s1 = "World"
# Q. 가운데 빈 칸을 넣고 싶을 땐 어떻게 해야할까?
s + ' ' + s1 # string concatenation
```

```
'Hello World'
```

```python
s2 = "Hello"
s2 * 10
```

```
'HelloHelloHelloHelloHelloHelloHelloHelloHelloHello'
```

```python
s3 = "Enjoy your life."
len(s3)
# 문자열의 길이를 출력하는 함수 len() 을 통해 s3의 문자 갯수(문자열 길이)를 알아보자.
```

```
16
```

### 4) Formatting

* 문자열을 출력할 때(print 함수를 이용하여) 특정 format을 지정하고 싶은 경우에는 어떻게 해야할까?

e.g. OOO님의 주민등록번호는 XXXXXXX-XXXXXXX입니다.

* 문자열 포맷에는 크게 3가지가 있다. (기호에 맞게 사용하면 됩니다)

"사과는 4개있다."

1. print format 사용

> print("%s는 %d개 있다." % ("사과", 4))

2. str.format 함수 사용

> print("{}는 {}개 있다.".format("사과", 4))

3. f-string (\*\*)

> apple = "사과", count = 4

> print(f"{apple}는 {count}개 있다.")

```python
fruit = "파인애플"
count = 300
```

```python
# 1) print formatting
print("%s는 %d개있다." % (fruit, count))
```

```
파인애플는 300개있다.
```

```python
# 2) str.format
print("{}는 {}개있다.".format(fruit, count))
```

```
파인애플는 300개있다.
```

```python
# 3) f-string
print(f"{fruit}는 {count}개있다.")
```

```
파인애플는 300개있다.
```

**Q. 개인정보를 사용자로부터 입력받아, 주민등록등본을 출력해주는 키오스크(Kiosk)용 프로그램을 제작하려고 한다. 입력받은 이름을 name이라는 변수에, 주민번호 앞자리를 id라는 변수에 입력받았다면, 주민등록등본에 어떻게 출력해야 할까?**

### 5) 관련 함수들

(1) 대소문자 바꾸기 upper(), lower()

```python
s = "hi"
s.upper()
```

```
'HI'
```

```python
s = "Hi"
s.lower()
```

```
'hi'
```

(2) 문자 공백 지우기 strip()

```python
s = "         h        i     "
#s.strip()
s.replace(" ", "")
```

```
'hi'
```

(3) 문자열 삽입 join()

```python
"[".join("KimYongDam")
```

```
'K[i[m[Y[o[n[g[D[a[m'
```

(4) 문자열 나누기 split()

```python
s = "Life is too short."
s.split("too") # 괄호안에 아무것도 안쓰면 공백을 기준으로 잘라줍니다.
```

```
['Life is ', ' short.']
```

(5) 문자열 바꾸기 replace()

```python
s = "Life is too short."
# Life를 This pencil로 바꿔봅시다.
s.replace("Life", "This pencil")
```

```
'This pencil is too short.'
```

##

## 3. 연속형 데이터 (Sequential Data Types)&#x20;

**Q. 숫자 100개를 한번에 다루려고 한다. <=> 하나의 변수에 숫자 100개를 저장하고 싶다. 어떻게 해야할까?**

_A. 연속형 데이터 타입을 사용하자!_

* 연속형 데이터란, 하나의 변수가 하나의 데이터를 가지고 있던 숫자형 데이터와 달리, 여러개의 데이터를 하나의 변수에 가지고 있는 데이터 타입이다.
* 연속형 데이터 타입에는 리스트(List), 튜플(Tuple), 문자열(String)이 있다. (문자열을 문자들의 나열로 인식하기 때문에, 연속형 데이터이다.)
* 연속형 데이터의 크기 제한은 없다. 하지만, 사용하는 컴퓨터의 가용 메모리 용량을 인지하며 사용해야 한다.
* 각 연속형 데이터 타입마다 특징이 다르다. 그 특징을 파악하여 용도에 맞는 데이터 타입을 사용하는 것이 중요하다.

**(OPTIONAL)** 사전(dictionary) 타입은 associative array라고 불리며, 흔히 알고있는 Hash table 구조이다.

##

## 1) 리스트(List)

* 가장 많이 사용되는 연속형 데이터 타입이자, 굉장히 유연한 구조를 가지고 있어 대부분의 데이터를 편하게 다룰 수 있다.
* 파이썬에서 \[ 와 ]를 이용하여 표현한다. e.g. \[1, 2, 3]
* 리스트의 원소는 쉼표로 구분되며, 리스트의 원소는 아무 데이터 타입이나 가능하다. 리스트조차 가능하다.
* 리스트를 이용하면 파이썬에서 다루는 대부분의 데이터는 아무 무리없이 다룰 수 있다. 하지만 수정이 자유롭기 때문에 수정을 하면 안되는 경우에는 사용하면 안된다.

### (1) 만드는 법&#x20;

```python
# 정수 1, 2, 3을 원소로 가지는 리스트를 만듭니다.
L = [1, 2, 3]
L, type(L)
```

```
([1, 2, 3], list)
```

```python
L1 = [] # empty list
type(L1)
```

```
list
```

```python
L2 = list() # 빈 리스트를 만드는 같은 방법
type(L2)
```

```python
L3 = [1, "Hi", 3.14, [1, 2, 3]] # 리스트에는 다양한 타입의 원소를 다 포함할 수 있다. 심지어 리스트도.
L3
```

```
[1, 'Hi', 3.14, [1, 2, 3]]
```

```python
L4 = [[1, 2],
     [3, 4]] # 2x2 행렬 표현처럼 사용할 수 있다. 이를 2차원 리스트라고 한다.
L4 # 실제로는 2개의 리스트를 원소로 가지는 리스트이다.
```

```
[[1, 2], [3, 4]]
```

### (2) Indexing&#x20;

* 연속형 데이터들은 하나의 변수에 여러가지 데이터를 가지기 때문에 여러 데이터를 접근하는 방법이 필요하다.
* 이를 위해 indexing이라는 기법이 있다. 말그대로 index를 통해 접근(access)하는 방법이다.
* 리스트의 index는 맨 앞부터 0으로 시작하며, 1씩 증가하는 정수 index를 사용한다.

e.g. \[1, 2, 3]이면 첫번째 원소는 index가 0이고, 두번째 원소는 index가 1이다.

* 파이썬에서는 음수 index도 제공하는데, 이는 뒤쪽부터 접근할 수 있는 방법이다.

e.g. \[1, 2, 3]이면 뒤에서 첫번째(맨 마지막)원소는 index가 -1이고, 뒤에서 두번째 원소는 index가 -2이다.

* index를 통해 접근하는 방법은 해당 변수이름에 \[]를 사용하며, \[]안에 index를 넣어서 접근할 수 있다.

e.g L = \[1, 2, 3]이면 L\[0]은 1이고, L\[2]는 L\[-1]이며 3이다.

```python
L = [1, 2, 3, 4, 5]
L
```

```
[1, 2, 3, 4, 5]
```

```python
# L의 첫번째 원소
L[0]
```

```
1
```

```python
# L의 5번째 원소
L[4]
```

```
5
```

```python
# L에 없는 index는?
L[13]
```

```
---------------------------------------------------------------------------

IndexError                                Traceback (most recent call last)

<ipython-input-91-7c2e7b6419da> in <module>()
      1 # L에 없는 index는?
----> 2 L[13]


IndexError: list index out of range
```

```python
# L의 마지막 원소
L[-1]
```

```
5
```

```python
# indexing을 이용한 연산. L의 첫번째, 두번째 원소를 가져다가 더해봅니다.
L[0] + L[1]
```

```
3
```

```python
L2 = [1, [2, 3], 5]
L2
```

```
[1, [2, 3], 5]
```

```python
# L2에서 2에 접근하기 위해 indexing을 해보자.
L2[1][0]
```

```
2
```

### (3) Slicing&#x20;

**슬라이싱은 리스트에서 뿐만 아니라, 리스트와 비슷한 구조인 numpy array와 pandas series, dataframe에서도 많이 이용되니 꼭 알아두어야 한다.**

* 슬라이싱은 리스트의 일부분만 잘라낸다는 의미이다. (말그대로 슬라이싱)
* 리스트의 일부만 사용하고 싶을 때 쓰는 기법이며, indexing을 범위로 하는 느낌이다.
* 리스트의 index와 :를 사용하여 슬라이싱을 할 수 있다.

e.g. L = \[1, 2, 3, 4] L\[0:2]는 \[1, 2]이다.

```python
L = [1, 2, 3, 4, 5]
L
```

```
[1, 2, 3, 4, 5]
```

```python
# L의 첫번째부터 index2 까지 자르기
L[0:2] # L[0] L[1]
```

```
[1, 2]
```

```python
# L의 두번째부터 index4 까지 자르기
L[1:4] # L[1] L[2] L[3] L[4]
```

```
[2, 3, 4, 5]
```

```python
# 시작 index를 생략하면, 자동으로 index는 0이 된다. (맨 처음)
L[:4]
```

```
[1, 2, 3, 4]
```

```python
# 끝 index를 생략하면, 자동으로 index는(리스트의 길이)가 된다. (맨 마지막) Q. 왜 리스트의 길이일까?
L[2:len(L)] # L[2] L[3] L[len(L)-1] ## len(L) 5
```

```
[3, 4]
```

> **TIP!** 문자열도 연속형 데이터 타입이기 때문에, indexing과 slicing이 다 된다. 하나의 문자열을 생성하여 연습해보자.

### (4) 연산하기

> 문자열때와 마찬가지로, 리스트도 더하기, 곱하기 연산이 존재한다. 어떤 의미일지 생각해보자.

#### &#x20;① 더하기

```python
L = [1, 2, 3]
L2 = [4, 5]
L + L2 # list concatenation
```

```
[1, 2, 3, 4, 5]
```

#### &#x20; ② 곱하기

```python
L * 3 # L + L + L
```

```
[1, 2, 3, 1, 2, 3, 1, 2, 3]
```

#### ③ 수정하기

```python
L2[0] = 144
L[2] = 7
```

```python
print(L[1])
print(L2[1])
L[1] + L2[1] # 값이 바뀐게 적용이 됩니다.
```

```
2
5





7
```

### (5) 관련 함수

#### ①원소 추가하기 append() (\*\*\*)

```python
# 빈 리스트 L을 만들어서 3, 2, 1 순서대로 원소를 추가해봅니다.
L = []
L.append(3)
L.append(2)
L.append(1)
L
```

```
[3, 2, 1]
```

#### ② 원소 정렬하기 sort()

```python
# sort()를 이용해 L을 "오름차순" 정렬합니다.
L = [4, 3, 16]
#L.sort(reverse=True) # reverse=True를 쓰면, "내림차순" 정렬이 됩니다.
L
```

```
[4, 3, 16]
```

#### ③ 뒤집기(정렬 X) reverse()

```python
#L.reverse() # reverse()와 같은 결과를 내는 신박한 방법도 있습니다. L[::-1]
L.reverse()
L
```

```
[16, 3, 4]
```

#### ④ 원소 제거하기 pop()&#x20;

```python
L.pop()
```

```
---------------------------------------------------------------------------

IndexError                                Traceback (most recent call last)

<ipython-input-148-a522295e58ee> in <module>()
----> 1 L.pop()


IndexError: pop from empty list
```

```python
L
```

```
[]
```

## 2) 튜플(Tuple)

* tuple은 list과 거의 같다.

> indexing, slicing 모두 동일하게 사용 가능하다. 원소들도 자유롭게 사용 가능하다.

* 거의 같은데, 다른 점이 딱 2가지 있다.

**(1) 리스트는 \[]를 사용하고, 튜플은 ()을 사용한다.**

**(2) 리스트는 생성 후에 변경이 가능하고(mutable) 튜플은 생성 후에 변경이 불가능하다.(immutable)**

> Mutable : 생성된 이후에 변경(assignment)이 자유롭게 가능한 data type. e.g. List, dict, set

> immutable : 생성된 이후에 변경이 불가능한 data type e.g. int, float, string, tuple, frozenset

> 1. 성능적인 이슈 -> 변경되지는 않는 그 자체로 장점이 생김.

> 2. 프로그래밍적인 이슈 -> 데이터 수정 자체를 하지 않는 경우 실수를 방지할 수 있다.

```python
# 1, 2를 원소로 가지는 tuple을 생성해 봅니다.
t = (1, 2)
t, type(t)
```

```
((1, 2), tuple)
```

```python
t1 = ()
t1, type(t1)
```

```
((), tuple)
```

```python
t2 = ('a', 'b', ('a', 'b'))
t2
```

```
('a', 'b', ('a', 'b'))
```

```python
t3 = (1, "a", (3, 3.14), ["yongdam", 3])
t3
```

```
(1, 'a', (3, 3.14), ['yongdam', 3])
```

```python
t[0]
```

```
1
```

```python
t[-1]
```

```
2
```

```python
t[0] = 3 # 튜플의 원소를 변경해보자.
```

```
---------------------------------------------------------------------------

TypeError                                 Traceback (most recent call last)

<ipython-input-156-3618893200c3> in <module>()
----> 1 t[0] = 3 # 튜플의 원소를 변경해보자.


TypeError: 'tuple' object does not support item assignment
```

```python
t
```

```
(1, 2)
```

```python
# 그럼 tuple의 더하기, 곱하기는 어떻게 될까?
t = (1, 2)
t2 = (3, 4)
t + t2
```

```
(1, 2, 3, 4)
```

```python
t2 * 3
```

```
(3, 4, 3, 4, 3, 4)
```

```python
len(t2 * 3)
```

```
6
```

## 3) 집합(Set)

* 집합 자료형은 정말 말그대로 수학에서 배우는 집합 그 자체이다.
* 수학에서는 집합을 {}로 표시했지만, 파이썬에서는 안타까운 이유로 {}를 사용하긴 하는데 그냥 사용할 수는 없다. 왜냐면 사전(Dictionary) 자료형도 {}를 사용하기 때문이다. 이에 대해서는 뒤에 자세히 배운다.
* 공집합을 생성할 때는 _반드시_ set()으로 생성해야 한다. {}로 생성하면 빈 사전이 생성된다.

e.g. {1, 2, 3} : 집합, {'a':1, 'b':2} : 사전

* 집합의 연산자인 교집합, 합집합, 차집합을 모두 지원한다.
* 집합의 특징이 2가지 있는데, 이 특징이 리스트와의 차이점이라 사용한다. 첫번째 특징이 집합 자료형을 사용하는 주된 이유이다.

(1) 집합은 원소의 중복을 허용하지 않는다. 즉, **원소의 종류**를 나타내기 좋다.

(2) 집합은 원소의 순서가 존재하지 않는다. 즉, 원소의 index가 없다.

```python
# 1, 2, 3을 원소로 가지는 집합을 만들어 봅시다.
s = {1, 2, 3}
s, type(s)
```

```
({1, 2, 3}, set)
```

```python
#s1 = {}
s1 = set() # 공집합 생성
s1, type(s1)
```

```
(set(), set)
```

```python
s[1] # 2가 나올것 같지만... ## indexing이 안됨.
```

```
---------------------------------------------------------------------------

TypeError                                 Traceback (most recent call last)

<ipython-input-165-119c3881ee56> in <module>()
----> 1 s[1] # 2가 나올것 같지만...


TypeError: 'set' object is not subscriptable
```

### (1) 연산하기

```python
s1 = {1, 2, 3, 4, 5}
s2 = {3, 4, 5, 6, 7}
```

#### ① 교집합&#x20;

```python
# s1과 s2의 교집합
s1 & s2 # 교집합의 연산 기호 &
```

```
{3, 4, 5}
```

```python
s1.intersection(s2) # s1과 s2의 자리를 바꿔서 당연히 같다.
s2.intersection(s1)
```

```
{3, 4, 5}
```

#### ② 교집합

```python
# s1과 s2의 합집합
s1 | s2
```

```
{1, 2, 3, 4, 5, 6, 7}
```

```python
s1 + s2 # 많이 혼동한다.
```

```
---------------------------------------------------------------------------

TypeError                                 Traceback (most recent call last)

<ipython-input-171-11f65b4bbb0e> in <module>()
----> 1 s1 + s2 # 많이 혼동한다.


TypeError: unsupported operand type(s) for +: 'set' and 'set'
```

```python
s1.union(s2)
s2.union(s1)
```

```
{1, 2, 3, 4, 5, 6, 7}
```

#### ③ 차집합

```python
# s1과 s2의 차집합
s1 - s2
```

```
{1, 2}
```

```python
s2 - s1 # 당연히 다르다.
```

```
{6, 7}
```

### (2) 원소의 uniqueness를 활용하는 경우.

```python
# 리스트 L에 있는 서로 다른 원소의 개수는?
L = [1, 1, 2, 2, 2, 3, 3, 3, 3, 4, 4, 4, 4, 4, 5, 6, 1, 1, 5]
len(set(L)) # type conversion
```

```
6
```

### (3) 관련 함수

#### ① 원소 하나 추가 add()

```python
s = set()
s.add(2)
s
```

```
{2}
```

#### ② 집합에 여러 원소 추가하기 update()

```python
s = {1, 2, 3}
s.update({4, 5}) # sequence 가능.
s
```

```
{1, 2, 3, 4, 5}
```

#### ③ 집합에서 원소 제거하기 remove()

```python
s.remove(13)
s
```

```
---------------------------------------------------------------------------

KeyError                                  Traceback (most recent call last)

<ipython-input-186-fa9d9cb9134f> in <module>()
----> 1 s.remove(13)
      2 s


KeyError: 13
```

## 4) 사전(Dictionary)

**파이썬에서 리스트와 함께 굉장히 많이 사용되는 구조. 특히 이번 교육과정 중에 많이 사용되니 꼭 마스터하는 것을 추천한다.**

* 파이썬에서 제공하는 사전 자료형은 key - value 방법을 통해 저장한다.

| name    | code |
| ------- | ---- |
| "John"  | 0011 |
| "Maria" | 1234 |

* 이런 table concept을 의미하며, 정수 index가 아닌 key값을 통해서 value를 access한다.

> key-value 방식으로 저장을 하는 것으로 얻는 이점은?

> A. 순서가 아닌 의미가 있는 값을 통해서 데이터 접근이 가능하다.

* 같은 말로 Hash Table이라고 불리며 데이터 관리에서 굉장히 중요한 개념이다.
* 파이썬에서 사전 자료형은 {}을 이용하여 표현하는데, 집합과의 차이점을 두기 위해 원소에 _반드시_ :가 들어가야 한다.
* 사전을 표현할 때는 {key : value, key2 : value2, ... } 형태로 표현한다.

e.g. {'a' : 1', "b" : 3}

### (1) 만드는 방법

```python
D = {"major" : "CSE", "name" : "kimyongdam"}
D
```

```
{'major': 'CSE', 'name': 'kimyongdam'}
```

```python
# 위에 나온 테이블 예시를 사전으로 만들어봅니다.
D = {"John" : '0011', "Maria" : '1234'}
D
```

```
{'John': '0011', 'Maria': '1234'}
```

```python
# 사전 D에 key가 'a'이고 value가 3인 원소를 추가하자.
# 만약에 indexing하려는 key가 존재하지 않는 경우엔, assign을 하게되면 key-value pair가 추가됩니다.
# 아닌 경우에는 assign 하게되면 value가 업데이트 됩니다.
D['a'] = 5
D
```

```
{'John': '0011', 'Maria': '1234', 'a': 5}
```

```python
D["a"] # key값이 이미 존재하는 경우에는 key값을 통한 indexing이 되며, key값이 존재하지 않을 때는 assignment를 사용하여 원소를 추가한다.
```

```
5
```

```python
D2 = {'a' : 1 , 'a' : 2, 'b': 3} # 무엇이 문제일까?
D2 # key가 될 수 있는 data type은 int, float, str, tuple
```

```
{'a': 2, 'b': 3}
```

> **TIP** 사전을 만들 때 key는 중복이 있으면 절대 안된다.

> 사전에서 key가 될 수 있는 data type은 **immutable**이어야 한다.

### (2) 관련 함수&#x20;

#### ① 사전의 모든 key값들 보기 keys()

```python
D = {'name': 'kim', 'phone': '01012345679', 'birth': '1234'}
D.keys()
```

```
dict_keys(['name', 'phone', 'birth'])
```

#### ② 사전의 모든 value들 보기 values()

```python
D.values()
```

```
dict_values(['kim', '01012345679', '1234'])
```

#### ③ 사전의 모든 key, value 쌍 보기 items()

```python
D.items()
```

```
dict_items([('name', 'kim'), ('phone', '01012345679'), ('birth', '1234')])
```

#### ④ 사전의 원소 가져오기 get()

```python
# D['name']과 같다.
D.get("surname", "Lee") # get 함수를 사용하면, default값을 지정할 수 있다.
```

```
'Lee'
```

#### ??? Sequence에 해당 데이터가 존재하는지 확인하기 : `in` operator

* in이라는 operator는 모든 연속형 데이터 타입에 사용할 수 있다.
* 사전의 경우에는 key값을 대상으로 하고, 리스트, 튜플, 집합, 문자열에 대해서는 해당 원소가 존재하는지 찾아서 True / False 를 알려준다.

```python
"phone" in D
```

```
True
```

```python
"major" in D
```

```
False
```

```python
# 리스트, 튜플, 집합에서도 테스트
L = [1, 2, 3]
t = (4, 5, 7)
s = {1, 3.14, "kim"}
"kim" in s
```

```
True
```
