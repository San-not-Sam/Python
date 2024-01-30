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

# 데이터 분석 라이브러리

## 1. Numpy

### 1) 정의

Numerical computing with Python으로, 수치연산 및 벡터 연산에 최적화된 라이브러리이다.&#x20;

### 2) 특징&#x20;

* 최적화된 C code로 구현되어 있어 뛰어난능성을 보입니다.&#x20;
* **\[numerical stable]** 파이썬과 달리, 수치 연산의 안정성이 보장되어 있다.&#x20;
* N차원 실수값 연산에 최적화되어 있다. (=N개의 실수로 이루어진 벡터 연산에 최적화되어 있다.)

```
# numpy example
import numpy as np
arr = np.array([1, 2, 3])
print(np.linalg.norm(arr)) # print L2 norm of vector (1, 2, 3)
```

### 3) 사용  이유&#x20;

* 데이터가 벡터로 표현되는 만큼, 데이터 분석은 벡터 연산으로 볼 수 있다. 따라서, 벡터 연산을 잘 쓸 수 있어야 한다.&#x20;
* 파이썬은 실수값 연산에 오류가 있다면 원하는 결과를 얻지 못할만큼 수치 연산에 약하다. 많은 실수 연산이 요구되는 머신러닝에서 파이썬을성사용한다면 성능이 저하될 수 있다.&#x20;
* numpy는 벡터 연산을 빠르게 처리하는 데에 최적화되어 있으며, 파이썬 리스트로 구현할 때 보다 빠르다.

## 2. Numpy Array&#x20;

### 1) 정의

numpy에서 사용되는 기본적인 자료구조로, C언어의 array 구조와 동일한 개념이다.&#x20;

<figure><img src=".gitbook/assets/image.png" alt=""><figcaption><p>Source : https://indianaiproduction.com/python-numpy-array/</p></figcaption></figure>

### 2) List와의 공통점&#x20;

1. indexing으로 원소를 접근할 수 있습니다.
2. 생성 후 assignment operator를 이용해서 원소의 update가 가능합니다.

### 3) List와의 차이점

1. 선언한 이후에 크기 변경이 불가능합니다.
2. **\[homogeneous array]** 모든 원소의 데이터 타입이 동일해야 합니다.&#x20;
3. 제공하는 데이터 타입이 다르다.&#x20;

<figure><img src=".gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

4. 수치와 관련된 데이터 타입이 대부분입니다.
5. 원소의 크기(memory size)를 조절할 수 있으며, 크기에 따라 표현할 수 있는 수치 범위가 정해집니다.&#x20;

<table><thead><tr><th width="125"></th><th width="177"></th><th width="188"></th><th width="153"></th><th></th></tr></thead><tbody><tr><td>np.int8</td><td>수치 표현에 8 bits를 사용한다</td><td>00000000 ~ 11111111</td><td>2^8 (256개)</td><td>-128 ~ 127</td></tr><tr><td>np.float32</td><td>실수 표현에 32 bits를 사용한다</td><td>exponent, mantissa, sign</td><td>single precision</td><td></td></tr></tbody></table>



###

###



```
```
