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

##

### # 변수(Variable)

* 메모리에 데이터를 저장하기 위한 공간이자,  실제 물리적인 메모리 주소 공간이다.&#x20;
* 사용자는 변수의 이름으로, 컴퓨터는 변수의 주소로 데이터를 인식한다.&#x20;

```python
# a라는 변수가 실제 메모리에서 저장되어 있는 위치(메모리 주소)
id(a)
```

* 데이터를 저장할 때에는 '=' (Assignment Operator)를 사용한다.&#x20;

```python
# 변수 a에 10이라는 정수 데이터를 할당(assign)한다.
a = 10
```

> lvalue (실제 메모리 주소) = rvalue(실제 데이터)

## 1. 숫자 데이터 (Numeric Data Types)

* <mark style="color:red;">정수,  실수</mark>, 복소수, 2진수, 8진수, 16진수를 포함한다.
* 파이썬에서 숫자의 표현 범위는 무한하다.
* 사칙연산(+, -, \*, /), 나머지 구하기(%), 몫 구하기(divmod), 거듭제곱(\*\*) 등 모두 가능하다.&#x20;

### 1) 정수형 (Integer)

```python
# 각각 a와 b에 10과5를 할당한 후 사칙 연산 
a = 6
b = 7
a + b
a - b
```

```
13
-1
```

```python
# 데이터 타입을 확인하는 함수
type(b)
```

```
int
```

### 2) 실수형 (Floating point)

<pre class="language-python"><code class="lang-python"><strong>c = 3.14
</strong>c
</code></pre>

```
3.14
```

```python
# 데이터 타입을 확인하는 함수
type(c)
```

```
float
```

### 3) 연산

**(1) 사칙연산**

```python
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
a = 10.3
b = -1.6
```

**(2) 특수연산**

```python
c = 5
d = 2
print(c ** d) # c를 d번 곱한 것(거듭제곱). c^d
print(c // d) # c를 d로 나눈 몫.
print(c % d)  # c를 d로 나눈 나머지.
```

```
25
2
1
```

## 2. 문자열(String) of 연속형 데이터

* 문자열 데이터 = 문자의 나열(Character Sequence)
* 파이썬에서 문자열의 크기에는 제한이 없다.
* 두 가지 기호로 나타낸다. **Single Quotation**(**' '**),  **Double Quotation**(**" "**)&#x20;
* 컴퓨터는 문자를 encoding하여 숫자로 표현한다. e.g. ASCII, utf-8, cp949
* 컴퓨터는 문자를 숫자로 인식한다. e.g.  A → 65, a -> 97 (ASCII 코드 변환시)
* 웹 국제 표준은 <mark style="color:red;">UTF-8</mark>(Universal code character set Transformation Format - 8-bit)
* UTF-8는 가변 인코딩 방식을 따르며, 이 때 'a'는 1바이트, '가'는 3바  이트로 인식된다. 즉, 영어보다 한 글이 더 많은 데이터를 필요로 한다.&#x20;

### 1) 만드는 여러 방법

```python
s = 'Hello World'
s
```

```
'Hello World'
```

```python
s1 = """Kim Sangcheol
is
clever."""
s1
```

```
'Kim sangcheol\nis\nclever.'
```

```python
s2 ="""To Be Great is
To Be Misunderstood.
- Ralph Waldo Emerson
"""
print(s2) # print문을 동원한 출력과 
s2        # 그렇지 않은 출력에는 출력값에 차이가 있음. 
```

```
To Be Great is
To Be Misunderstood.
- Ralph Waldo Emerson

'To Be Great is\nTo Be Misunderstood.\n- Ralph Waldo Emerson\n'
```

```python
# Single Quotation(' '),  Double Quotation(" ")이 모두 존재하는 이유 
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
# \n -> enter: 행 바꾸기(새로운 하나의 행)
print("Hello\n\n\nWorld")
```

```
Hello


World
```

```python
# \t -> tab: 행 늘리기(탭의 개수만큼 공백이 옆으로늘어남)
print("Hello\t\t\t\t\t\tWorld")
```

```
Hello						World
```

### 3) 연산

* '덧셈'과 '곱셈'만 지원되며, '곱셈' 및 '나눗셈' 등 기타 연산은 지원되지 않는다.&#x20;

```python
# 덧셈 
s = "Hello"
s1 = "World"
s + ' ' + s1 # string concatenation
```

```
'Hello World'
```

```python
# 곱셈 
s2 = "Hello"
s2 * 10
```

```
'HelloHelloHelloHelloHelloHelloHelloHelloHelloHello'
```

```python
# 문자열의 길이를 출력
s3 = "Enjoy your life."
len(s3) 
```

```
16
```

### 4) Formatting

* **특정한 형태**로 문자열을 출력하고자 할 때 사용&#x20;

(1) print format

> print("%s는 %d개 있다." % ("string", decimal))

```python
fruit = "자몽"
count = 700
```

```python
# 1) print formatting
print("%s는 %d개있다." % (fruit, count)) 
# %s - 문자열 출력, %d - 정수 출력, %f - 실수 출력
```

```
자몽은 700개있다.
```

(2) str.format&#x20;

> print("{}는 {}개 있다.".format("문자열  데이터", decimal))

```python
# 2) str.format
print("{}는 {}개있다.".format(fruit, count))
```

```
자몽은 700개있다.
```

(3) f-string(\*\*)&#x20;

> print(f"{문자열  데이터}는 {count}개 있다.")

```python
# 3) f-string
print(f"{fruit}는 {count}개있다.")
```

```
자몽은 700개있다.
```

### 5) 관련 함수들

(1) 대/소문자로 바꾸기 upper() / lower()

```python
s = "hi"
print(s.upper())
s = "Hi"
print(s.lower())
```

```
'HI'
'hi'
```

(2) 문자 공백 지우기 strip()

```python
s = "         h        i     "
s.strip()             # 문자열 밖의 공백만 제거 
# s.replace(" ", "")  # 문자열 안팎의 모든 공백 제거 
```

```
'hi'
```

(3) 문자열 삽입 join()

```python
"[".join("KimSangcheol")
"-".join("abcd")
```

```
'K[i[m[S[a[n[g[c[h[e[o[l'
'a-b-c-d'
```

(4) 문자열 나누기 split()

```python
s = "Life is too short."
s.split("too") # 괄호 안을 채우지 않으면 공백을 기준으로 나눔.   
```

```
['Life is ', ' short.']
```

(5) 문자열 바꾸기 replace()

```python
s = "My hair is too short."
s.replace("My hair", "This pen")
s.replace(" ", "") # 공백을 제거, strip의 대안
```

```
'This pencil is too short.'
```



## 3. 연속형 데이터 (Sequential Data Types)&#x20;

* **\[정의]** 복수의 데이터를 하나의 변수에 포함하는 데이터 타입이다.&#x20;
* **\[필요성]** 하나의 변수에 하나가 아닌 여러 개의 데이터를 저장할 때 사용한다. \
  ( ↔ **숫자형 데이터** : 한개의 변수가 한 개의 데이터만을 가짐.)
* **\[종류]** 리스트(List), 튜플(Tuple), 문자열(String)
* **\[주의 사항]**&#x20;
  1. 크기 제한은 없지만 컴퓨터의 가용 메모리 용량을 감안하여 사용해야 한다.&#x20;
  2. 종류마다 특징이 다르므로, 용도에 맞게 사용해야 한다.&#x20;

## 1) <mark style="color:red;">리스트\[</mark>List<mark style="color:red;">]</mark>

* 리스트 내 원소는 어떤 데이터 타입도 가능하며, 쉼표(,)로 구분된다.&#x20;
* 수정이 자유롭기 때문에, 수정 허용이 불가한 경우에는 사용이 적절치 않다.&#x20;

### (1) 만드는 법&#x20;

```python
# 정수 1, 2, 3을 원소로 가지는 리스트 생성 
L = [1, 2, 3]
L, type(L)
```

```
([1, 2, 3], list)
```

```python
# 빈 (empty) 리스트 생성하는 2가지 방법 
L1 = [] 
type(L1) 
L2 = list()
type(L2)
```

```
list
list  
```

<pre class="language-python"><code class="lang-python"># 숫자형, 문자열, 소수, <a data-footnote-ref href="#user-content-fn-1">리스트</a>를 원소로 가지는 리스트 생성 
L3 = [1, "Hi", 3.14, [1, 2, 3]] 
L3
</code></pre>

```
[1, 'Hi', 3.14, [1, 2, 3]]
```

```python
# N차원 리스트(행렬) 생성 
L4 = [[1, 2],
     [3, 4]] # 2x2 행렬처럼 사용할 수 있으며, 이를 2차원 리스트라고 한다. 
L4           # 2개의 리스트를 원소로 가지는 리스트이다.
```

```
[[1, 2], [3, 4]]
```

### (2) Indexing (찾아내기)

* \[정의] Index를 통해 여러 데이터에 접근하는 방법
* \[특징]&#x20;
  1. \[양수; positive indexing (**->**) ] 원소의 순서는 맨 왼쪽부터 '0'에서 시작한다. e.g. (0, 1, 2, 3, ...)
  2. \[음수; negative indexing (**<-**) ] 원소의 순서는 맨 오른쪽부터 '-1'에서 시작한다. e.g. (..., -3, -2, -1)
  3. 대괄호 '\[ ]' 안에 index를 넣어 접근할 수 있다. e.g. L = \[7, 8, 9]에서 L\[0] -> 7, L\[1] -> 8, L\[-1] -> 9&#x20;

```python
L = [1, 2, 3, 4, 5]
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
L[5]
```

```
IndexError: list index out of range
```

```python
# L의 마지막 원소
L[-1] # L[4]와 같음
```

<pre><code><strong>5
</strong></code></pre>

```python
# indexing을 이용한 연산 
L[0] + L[1]
```

```
3
```

```python
L2 = [1, [2, 3], 4]
```

```python
# 리스트를 원소로 가지는 리스트에서 특정 원소에 접근 
L2[1]
L2[1][0] # 두 번째 원소의 첫 번째 원소에 접근 
L2[1][1] # 두 번째 원소의 두 번째 원소에 접근 
```

```
[2, 3]
2 
3
```

### (3) Slicing (잘라내기)

* 범위 단위의 indexing으로,  리스트의 일부만 사용하고자 할 때 쓰는 기법이다.&#x20;
* **index**와 **:(세미콜론)**를 사용하여 실행한다.&#x20;
* numpy array, pandas series, dataframe에서도 빈번하게 이용된다.&#x20;

> L\[m:n] - **m번째 원소**부터 **n-1번째 원소**까지

```python
L = [1, 2, 3, 4, 5]
```

```python
L[0:2] # 슬라이싱(0번째 원소 ~ 1번째 원소)
L[1:4] # 슬라이싱(1번째 원소 ~ 3번째 원소)
L[1:5] # 슬라이싱(1번째 원소 ~ 4번째 원소)
```

```
[1, 2]
[2, 3, 4]
[2, 3, 4, 5]
```

```python
L[:4] # 시작 index를 생략하면, 첫 번째 원소부터 시작한다.
L[0:4]
```

```
[1, 2, 3, 4]
[1, 2, 3, 4]
```

```python
L[2:]       # 끝 index를 생략하면, 마지막 원소까지포함한다.   
L[2:5]
L[2:6]      # 끝 index값이 원소 범위를 초과해도 마지막 원소까지만 포함한다. 
L[2:100]
L[2:len(L)] # 원소의 개수가 5개이므로, L[2:5]와 같음. → L[2], L[3], L[4]
```

```
[3, 4, 5]
[3, 4, 5]
[3, 4, 5]
[3, 4, 5]
[3, 4, 5]
```

### (4) 연산하기

* 덧셈'과 '곱셈'만 지원되며, '곱셈' 및 '나눗셈' 등 기타 연산은 지원되지 않는다.&#x20;

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
L[2] = 200
L2[0] = 100
```

```
[1, 2, 200]
[100, 5]
```

```python
print(L[2])
print(L2[0])
print(L[2] + L2[0]) # 바뀐 값이 적용된다. 
```

```
200
100
300
```

### (5) 관련 함수

#### ①원소 순서대로추가하기 append()&#x20;

```python
L = []       # 빈 리스트 생성 후 
L.append(3)  # 3, 2, 1 '순서대로' 원소를 추가하기
L
L.append(2)
L
L.append(1)
L
```

```
[3]
[3, 2]
[3, 2, 1]
```

#### ② 원소 역순으로 제거하기 pop()&#x20;

```python
L.pop()
L
L.pop()
L
L.pop()
L
```

```
[3, 2]
[3]
[]
```

#### ③ 원소 정렬하기 sort()

```python
L = [5, 2, 17]
L.sort()             # 오름 차순 정렬(default)
L.sort(reverse=True) # 내림 차순 정렬 
```

```
[5, 2, 17]
[2, 5, 17]
[17, 5, 2]
```

#### ④  원소 순서 뒤집기 reverse()

```python
L.reverse() # L[::-1]와 같은 결과를 낸다. 
L
```

```
[17, 2, 5]
```

## 2) <mark style="color:purple;">튜플(</mark>Tuple<mark style="color:purple;">)</mark>

* list와 마찬가지로, indexing, slicing을 사용하며, 원소도 자유롭게 사용한다.&#x20;
* list와의 차이점은 다음 두 가지이다.&#x20;
  1. 원소를 감쌀때, <mark style="color:red;">리스트</mark>는 <mark style="color:red;">\[]</mark>을 <mark style="color:purple;">튜플</mark>은 <mark style="color:purple;">()</mark>을 사용한다.&#x20;
  2. 리스트는 생성 후 <mark style="color:red;">변경이 가능</mark>한 반면, 튜플은 생성 후 <mark style="color:purple;">변경이 불가</mark>하다.&#x20;
* 변경을 원할 경우, 리스트로 변환한다. 이러한 번거로움으로 튜플 관련 함수도 많지 않다.&#x20;

<table><thead><tr><th width="157">구분</th><th width="227">변경 가능 여부 </th><th>e.g.</th></tr></thead><tbody><tr><td>Mutable</td><td>생성후 assignment 가능</td><td> <mark style="color:red;"><strong>list</strong></mark>, <mark style="color:green;"><strong>dict</strong></mark>, <mark style="color:orange;"><strong>set</strong></mark></td></tr><tr><td>Immutable</td><td>생성후 assignment 불가능 </td><td>int, float, <strong>string</strong>, <mark style="color:purple;"><strong>tuple</strong></mark></td></tr></tbody></table>

### (1) 만드는 법

```python
t = (1, 2)
t, type(t)
```

```
((1, 2), tuple)
```

```python
# 빈(empty) 튜플 생성
t1 = ()
t1, type(t1)
```

```
((), tuple)
```

```python
# 튜플을 원소로 하는 튜플 생성
t2 = ('a', 'b', ('a', 'b'))
t2
```

```
('a', 'b', ('a', 'b'))
```

```python
# 숫자형, 문자형, 튜플, 리스트를 원소로 하는 튜플 생성 
t3 = (1, "a", (3, 3.14), ["San", 3])
t3 
```

```
(1, 'a', (3, 3.14), ['San', 3])
```

```python
t
t[0]
t[-1]
```

```
(1, 2)
1
2
```

```python
# ★ 튜플의 원소는 변경이 불가하다. 
t[0] = 3  
```

```
TypeError: 'tuple' object does not support item assignment
```

### (2) 연산하기&#x20;

* 덧셈'과 '곱셈'만 지원되며, '곱셈' 및 '나눗셈' 등 기타 연산은 지원되지 않는다.&#x20;

```python
# 덧셈 및 곱셈 
t = (1, 2)
t2 = (3, 4)
t + t2
t2 * 3
```

```
(1, 2, 3, 4)
(3, 4, 3, 4, 3, 4)
```

```python
len(t2 * 3)
```

```
6
```

## 3) <mark style="color:orange;">집합{</mark>Set<mark style="color:orange;">}</mark>

* **{}**를 입력하면 **빈 사전(empty dictionary)**이 생기므로, **공집합을(empty set)** 생성시 **set()**을 입력&#x20;
* 집합의 연산자인 '교집합(intersection)', '합집합(union)', '차집합(difference)'이 지원된다.
* \[특징]  &#x20;
  1. 원소의 중복을 불허한다(원소의 종류를 나타내기 좋다.) 집합 자료형을 사용하는 주된 이유이다.
  2. 집합은 원소의 순서가 존재하지 않는다(원소의 index가 없다.)&#x20;

```python
# 1, 2, 3을 원소로 가지는 집합 생성
s = {1, 2, 3}
s, type(s)
```

```
({1, 2, 3}, set)
```

```python
s1 = set() # 공집합 생성
s1, type(s1)
s2 = {}
s2m type(s2)
```

```
(set(), set)
({}, dict)
```

```python
# 집합은 원소간 순서가 없으므로, 인덱싱 불가; 
s[1] # 리스트나 튜플이라면 2가 나와야 하지만, 순서가 없는 집합에서는 Error
```

```
TypeError: 'set' object is not subscriptable
```

### (1) 연산하기

```python
s1 = {1, 2, 3, 4, 5}
s2 = {3, 4, 5, 6, 7}
```

#### ① 교집합 (&, intersection)

```python
s1 & s2 
s1.intersection(s2) 
s2.intersection(s1) # 공통 분모를 찾는 과정이므로, s1과 s2의 자리를 바꿔도 당연히 같다.
```

```
{3, 4, 5}
{3, 4, 5}
{3, 4, 5}
```

#### ② 합집합 (|, union)

```python
s1 | s2
s1.union(s2)
s2.union(s1) # 합치는 과정이므로 순서는 무관하다. 
```

```
{1, 2, 3, 4, 5, 6, 7}
{1, 2, 3, 4, 5, 6, 7}
{1, 2, 3, 4, 5, 6, 7}
```

```python
s1 + s2 # 이는 성립하지 않는다. 
```

```
TypeError: unsupported operand type(s) for +: 'set' and 'set'
```

#### ③ 차집합(-, difference)

```python
s1 - s2
s2 - s1 
```

```
{1, 2}
{6, 7}
```

### (2) 집합 특징 활용하기&#x20;

```python
# 리스트 L에 있는 서로 다른 원소의 개수는?
L = [1, 1, 2, 2, 2, 3, 3, 3, 3, 4, 4, 4, 4, 4, 5, 6, 1, 1, 5]
set(L) # 타입 변환. 중복도 순서도 허용하지 않는 set을 활용하여 깔끔하게 나타낼 수 있다! 
len(set(L)) 
```

```
{1, 2, 3, 4, 5, 6} 
6
```

### (3) 관련 함수

#### ① 원소 한 개 추가 - add()

```python
s = set()
s.add(2)
s
```

```
{2}
```

#### ② 원소 여러 개 추가 - update()

```python
s = {1, 2, 3}
s.update({4, 5}) # 리스트나 튜플 등의 연속형 데이터 타입도 원소로추가할 수 있다. 
s
```

```
{1, 2, 3, 4, 5}
```

#### ③ 집합에서 원소 제거하기 remove()

<pre class="language-python"><code class="lang-python"><strong>s.remove(3) # 집합에서 순서는 없다. 원소를 괄호()안에 입력하면 해당 원소를 삭제한다. 
</strong><strong>s.remove(13) # 집합 내에 존재하지 않는 원소를 제거하면 Error
</strong>s
</code></pre>

```
KeyError: 13
```

## 4) <mark style="color:green;">사전{</mark>Dictionary<mark style="color:green;">}</mark>

* 사전 자료형은 {}로 표현하는데,  **집합(set)**과 구분하기 위해 원소에 반드시 **콜론(:)**이 들어가야 한다.&#x20;
* {key1 : value1, key2 : value2, ... } 형태로 표현하며 Hash Table라고 부른다.&#x20;

| name    | code |
| ------- | ---- |
| "Nick"  | 0022 |
| "Chole" | 5678 |

* key값을 통해서 value에 접근한다.&#x20;

### (1) 만드는 법

```python
# 생성 
D = {"Nick" : '0022', "Chole" : '5678'}
D
```

```
{'Nick' : '0022', 'Chole' : '5678'}
```

```python
# 원소(key, key-value) 추가 
D['a'] = 5 # 사전 D에 key가 'a'이고 key-value가 5인 원소를 추가(assign)하여 업데이트
D

# indexing하려는 key가 존재하지 않을 때, assign시 key-value pair가 추가됨.
```

```
{'Nick' : '0022', 'Chole' : '5678', 'a': 5}
```

```python
# 인덱싱하기 
D['a'] 
# key값이 존재하는 하는 경우, key값을 통해 indexing이 되며  
# key값이 존재하지 않을 경우, assignment를 사용하여 원소를 추가
```

```
5
```

```python
# 사전 생성시 중복은 허용되지 않는다. 중복되는 key와 key-value는 마지막에 쓴 값이 적용된다. 
D2 = {'a' : 1 , 'a' : 2, 'b': 3} # key가 될 수 있는 data type은 int, float, str, tuple
D2 
```

```
{'a': 2, 'b': 3}
```

### (2) 관련 함수&#x20;

#### ① 모든 key값 출력- keys()

```python
D = {'name': 'kim', 'phone': '01012345679', 'birth': '1234'}
D.keys()
```

```
dict_keys(['name', 'phone', 'birth'])
```

#### ② 모든 value 출력 - values()

```python
D.values()
```

```
dict_values(['kim', '01012345679', '1234'])
```

#### ③ 모든 key, value 쌍(pair) 출력  - items()

```python
D.items()
```

```
dict_items([('name', 'kim'), ('phone', '01012345679'), ('birth', '1234')])
```

#### ④ value 출력 - get()

```python
D.get("name")    
D.get("surname", "Lee") # key가 존재하지 않는 경우, default값을 지정할 수 있다.
```

```
'Kim'
'Lee'
```

### (3) `in` operator (모든 연속형 데이터에 적용)

* 특정 데이터의 존재 유무를 확인해준다.&#x20;
* **문자열, 리스트, 튜플, 집합**의 경우에는 '**원소**'를, **사전**의 경우에는 '**key값**'을 True/Fale로 출력한다.&#x20;

```python
# 문자열, 리스트, 튜플, 집합 
L = [1, 2, 3]
t = (4, 5, 7)
s = {1, 3.14, "kim"}
"kim" in L
"kim" in t
"kim" in s
```

```
False
False
True
```

```python
# 사전
"phone" in D
"major" in D
```

```
True
False
```

[^1]: 심지어 리스트조차 원소로 삼을 수 있다..!
