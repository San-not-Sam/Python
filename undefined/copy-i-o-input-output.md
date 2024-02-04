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

# Copy I/O (Input/Output)

## 1. STDIN / STDOUT (Standard IN, Standard OUT)

* 파이썬은 input()을 통해서 stdin을 사용자로부터 입력받을 수 있다.
* 파이썬은 print()를 통해서 stdout을 사용자에게 출력할 수 있다.

```python
# a에 키보드로 입력받은 값을 할당하고 출력해본다.
a = input()
a, type(a)
```

```
10





('10', str)
```

* 파이썬에서는 stdin은 무조건 문자열 타입으로 들어온다. 이를 type casting을 통해서 다른 데이터 타입으로 바꾸어 사용해야 한다.

```python
# 입력받는 값을 숫자라고 가정한 경우.
n = int(input())
n, type(n)
```

```
10





(10, int)
```

```python
# 입력받는 값을 숫자라고 가정했는데 문자열이 들어오면 에러가 난다. 이 경우는 type casting이 실패한 경우이다.
#n = int(input())
n = int(input())
n + 2
```

```
10





12
```

* 입력이 문자열이기 때문에 fancy하게 input을 처리할 수 있는 방법이 있다.

### Q. 만약에 stdin으로 여러 개의 숫자가 들어오는 경우, 입력의 format을 알고 있다고 가정했을 때, 이를 효과적으로 처리할 수 있을까?

```python
# 이는 숫자를 2개로 가정한 경우
a, b = input().split(',') # ['3', '5']
a, b = int(a), int(b)
a + 2
```

```
3, 5





5
```

```python
# 이와 같은 표현을 list comprehension이라고 한다.
[x+2 for x in range(1, 4)]

L = []
for x in range(1,4):
  L.append(x+2)
L
```

```
[3, 4, 5]
```

```python
# for문을 사용한 코드
numbers = []
for num in input().split(','):
  numbers.append(int(num))
numbers
```

```
3,4,5,6,7,877,9,1,12,3,5,6





[3, 4, 5, 6, 7, 877, 9, 1, 12, 3, 5, 6]
```

```python
# 위의 코드는 아래와 같다. 위의 코드가 훨씬 간단한 것을 확인할 수 있다. 익숙해져서 list comprehension을 사용하도록 하자.
[int(num) for num in input("숫자 여러개를 입력하세요.(단 ','로 구분합니다.) ").split(",")]
```

```
숫자 여러개를 입력하세요.(단 ','로 구분합니다.) 1,2,3,4,5,6,7,8





[1, 2, 3, 4, 5, 6, 7, 8]
```

```python
from google.colab import drive
drive.mount('/content/drive')
```

```
Mounted at /content/drive
```

## 2. File I/O

* file I/O란 프로그램에서 파일을 저장하고 불러오는 모든 것들을 의미합니다.
* file에는 txt, png, json, xlsx 등 여러가지 종류가 있습니다.
* 그 중에서 가장 간단하게 사용할 수 있는 데이터는 txt 파일입니다.

> 텍스트 파일을 여는 방법에는 read(), readline(), readlines(), for문을 이용한 방법이 있다. 코드를 통해 각 방법의 차이를 알아보자.

```python
# f.read()를 통해 data 폴더안에 있는 test.txt를 read mode로 열어봅니다.
file_path = "/content/drive/MyDrive/Colab Notebooks/data/test.txt"

with open(file_path, 'r') as f:
  data = f.read()

data
```

```
'아\n휴\n아이구\n아이쿠\n아이고\n어\n나\n우리\n저희\n따라\n의해\n을\n를\n에\n의\n가\n으로\n로\n에게\n뿐이다\n의거하여\n근거하여\n입각하여\n기준으로\n예하면\n예를 들면\n예를 들자면'
```

```python
# f.readline()를 통해 data 폴더안에 있는 test.txt를 read mode로 열어봅니다.
with open(file_path, 'r') as f:
  data = f.readline()

data
```

```
'아\n'
```

```python
# f.readlines()를 통해 data 폴더안에 있는 test.txt를 read mode로 열어봅니다.
with open(file_path, 'r') as f:
  data = f.readlines()

data
```

```
['아\n',
 '휴\n',
 '아이구\n',
 '아이쿠\n',
 '아이고\n',
 '어\n',
 '나\n',
 '우리\n',
 '저희\n',
 '따라\n',
 '의해\n',
 '을\n',
 '를\n',
 '에\n',
 '의\n',
 '가\n',
 '으로\n',
 '로\n',
 '에게\n',
 '뿐이다\n',
 '의거하여\n',
 '근거하여\n',
 '입각하여\n',
 '기준으로\n',
 '예하면\n',
 '예를 들면\n',
 '예를 들자면']
```

```python
# for문을 통해 data 폴더안에 있는 test.txt를 read mode로 열어서 출력해봅니다.
L = []
with open(file_path, 'r') as f:
  for line in f:
    L.append(line)

L
```

```
['아\n',
 '휴\n',
 '아이구\n',
 '아이쿠\n',
 '아이고\n',
 '어\n',
 '나\n',
 '우리\n',
 '저희\n',
 '따라\n',
 '의해\n',
 '을\n',
 '를\n',
 '에\n',
 '의\n',
 '가\n',
 '으로\n',
 '로\n',
 '에게\n',
 '뿐이다\n',
 '의거하여\n',
 '근거하여\n',
 '입각하여\n',
 '기준으로\n',
 '예하면\n',
 '예를 들면\n',
 '예를 들자면']
```

### Q. test.txt를 열어서 한글자짜리를 다 지우고 다시 저장하고 싶다. 어떻게 해야할까?

```python
output = []
# test.txt를 read mode로 열고 할 일이 끝나면 자동으로 닫는다.
with open(file_path, 'r') as f:
  data = f.readlines()

print(data)

# 한글자 이상인 텍스트만 output list에 저장한다.
for word in data:
  word = word.strip()
  if len(word) > 1:
    output.append(word)

print(output)
# result.txt로 output list에 있는 내용을 저장하기 위해 write mode로 열었다.

## google에 "디렉토리 구조" 검색!
with open("/content/drive/MyDrive/Colab Notebooks/data/result.txt", 'w') as f:
  # f.write()
  for word in output:
    print(word, file=f)
```

```
['아\n', '휴\n', '아이구\n', '아이쿠\n', '아이고\n', '어\n', '나\n', '우리\n', '저희\n', '따라\n', '의해\n', '을\n', '를\n', '에\n', '의\n', '가\n', '으로\n', '로\n', '에게\n', '뿐이다\n', '의거하여\n', '근거하여\n', '입각하여\n', '기준으로\n', '예하면\n', '예를 들면\n', '예를 들자면']
['아이구', '아이쿠', '아이고', '우리', '저희', '따라', '의해', '으로', '에게', '뿐이다', '의거하여', '근거하여', '입각하여', '기준으로', '예하면', '예를 들면', '예를 들자면']
```

```python
# 제대로 데이터가 저장되어 있는지, 불러와서 확인한다.
L = []
with open("/content/drive/MyDrive/Colab Notebooks/data/result.txt", 'r') as f:
  for line in f:
    L.append(line)

L
```

```
['아이구\n',
 '아이쿠\n',
 '아이고\n',
 '우리\n',
 '저희\n',
 '따라\n',
 '의해\n',
 '으로\n',
 '에게\n',
 '뿐이다\n',
 '의거하여\n',
 '근거하여\n',
 '입각하여\n',
 '기준으로\n',
 '예하면\n',
 '예를 들면\n',
 '예를 들자면\n']
```

## (OPTIONAL) pickle 라이브러리를 통해서 파이썬 object 자체를 저장하기

```python
output
```

```
['아이구',
 '아이쿠',
 '아이고',
 '우리',
 '저희',
 '따라',
 '의해',
 '으로',
 '에게',
 '뿐이다',
 '의거하여',
 '근거하여',
 '입각하여',
 '기준으로',
 '예하면',
 '예를 들면',
 '예를 들자면']
```

```python
# 리스트 자체를 저장할 순 없나?
import pickle

with open("result.pk", 'wb') as f:
  pickle.dump(output, f)
```

```python
with open("result.pk", 'rb') as f:
  output2 = pickle.load(f)

output2
```

```
['아이구',
 '아이쿠',
 '아이고',
 '우리',
 '저희',
 '따라',
 '의해',
 '으로',
 '에게',
 '뿐이다',
 '의거하여',
 '근거하여',
 '입각하여',
 '기준으로',
 '예하면',
 '예를 들면',
 '예를 들자면']
```
