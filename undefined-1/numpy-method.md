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

# Numpy method

### Numpy

#### 1. Numpy Array and Operation

* numpy의 기본적인 사용법에 대해서 배워봅니다.
* numpy에서 numpy.array를 만드는 여러가지 방법과 지원하는 연산자에 대해서 공부합니다.

#### 1.1. Numpy Array creation

```python
# numpy 라이브러리를 불러옵니다.
import numpy as np
```

```python
# 파이썬 리스트 선언
data = [1, 2, 3, 4, 5]
data
```

```
[1, 2, 3, 4, 5]
```

```python
# 파이썬 2차원 리스트(행렬) 선언
data2 = [[1, 2], [3, 4]]
data2
```

```
[[1, 2], [3, 4]]
```

```python
# 파이썬 list를 numpy array로 변환합니다.
arr = np.array(data)
# numpy array를 만드는 방식의 대부분은 파이썬 리스트를 np.array로 변환하는 방식입니다.
arr = np.array([1, 2, 3, 4, 5])
arr
```

```
array([1, 2, 3, 4, 5])
```

```python
# 2차원 리스트를 np.array로 만듭니다.
arr2 = np.array(data2) # data2라는 리스트를 numpy array로 만들어라.
arr2 # 2차원 numpy array -> 행렬!
```

```
array([[1, 2],
       [3, 4]])
```

```python
# 0부터 9까지 숫자를 자동으로 생성한 array
np.array(list(range(10)))
np.arange(10)
```

```
array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
```

```python
# 10부터 99까지 숫자를 자동으로 생성한 array
np.arange(10, 100)
```

```
array([10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26,
       27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43,
       44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60,
       61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77,
       78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94,
       95, 96, 97, 98, 99])
```

```python
arr.shape # (5, ) != (5, 1)
arr2.shape # (2, 2)
```

```
(2, 2)
```

#### 1.2. Reshaping array

```python
# 3 x 3 행렬을 만들어봅시다. 
# if, 6 x 6 ?
x = np.array([[1, 2, 3],
              [4, 5, 6],
              [7, 8, 9]])
x
```

```
array([[1, 2, 3],
       [4, 5, 6],
       [7, 8, 9]])
```

```python
# reshape을 이용하여 만들어봅시다.
np.arange(1, 10).reshape(3, 3) # (9, ) -> (3, 3)
```

```
array([[1, 2, 3],
       [4, 5, 6],
       [7, 8, 9]])
```

```python
# row vector를 column vector로
np.arange(6).reshape(6, 1)
```

```
array([[0],
       [1],
       [2],
       [3],
       [4],
       [5]])
```

```python
# 펼치기
x.reshape(-1, )
```

```
array([1, 2, 3, 4, 5, 6, 7, 8, 9])
```

#### 1.3. Concatenation of arrays

```python
arr1 = np.array([[1, 2, 3]])
arr2 = np.array([[4, 5, 6]])
# arr1 + arr2 = ?
# L = [1, 2, 3]
# L2 = [4, 5, 6]
# L + L2
# arr1와 arr2를 합칩니다
np.concatenate([arr1, arr2], axis=0)
```

```
array([[1, 2, 3],
       [4, 5, 6]])
```

```python
# stacking vertically
np.vstack([arr1, arr2])
```

```
array([[1, 2, 3],
       [4, 5, 6]])
```

```python
# stacking horizontally
np.hstack([arr1, arr2])
```

```
array([1, 2, 3, 4, 5, 6])
```

### 1.4. Array Arithmetic (like vector) --> Universal Function

```python
# v1 = (1, 2, 3), v2 = (4, 5, 6) 벡터 2개 생성하기.
v1 = np.array([1, 2, 3])
v2 = np.array([4, 5, 6])
```

```python
# 리스트로 더하기 연산해보기
L = [1, 2, 3]
L2 = [4, 5, 6]
L + L2
```

```
[1, 2, 3, 4, 5, 6]
```

```python
#  vector addition
v1 + v2
```

```
array([5, 7, 9])
```

```python
#  vector subtraction
v1 - v2
```

```
array([-3, -3, -3])
```

```python
# (not vector operation) elementwise multiplication
v1 * v2
```

```
array([ 4, 10, 18])
```

```python
# (not vector operation) elementwise division
v1 / v2
```

```
array([0.25, 0.4 , 0.5 ])
```

```python
# dot product
v1 @ v2 # 1x4 + 2x5 + 3x6
```

```
32
```

#### 1.5. Broadcast and Universal Function

* 서로 크기가 다른 numpy array를 연산할 때, 자동으로 연산을 전파(broadcast)해주는 기능. 행렬곱 연산을 할 때 편리하다.

```python
arr1 = np.array([1, 2, 3])
```

```python
arr2 = np.array([[-1, -1, -1],
                 [1, 1, 1]])
arr2.shape
```

```
(2, 3)
```

```python
# 2개의 array를 더해보면?
arr1 + arr2
```

```
array([[0, 1, 2],
       [2, 3, 4]])
```

```python
# 2개의 array를 곱해보면? (**)
arr1 * arr2
```

```
array([[-1, -2, -3],
       [ 1,  2,  3]])
```

* Universal Function : broadcast 기능을 확장해서, numpy array의 모든 원소에 동일한 함수를 반복문으로 적용한 것과 같은 효과를 내는 기능.

```python
arr1.shape[0]
```

```
3
```

```python
# f = lambda x : 1/x
f = lambda x : 1/x

arr1 = np.array([1., 2., 3.])

for i in range(arr1.shape[0]):
  arr1[i] = f(arr1[i])
print(arr1)

arr1 = np.array([1., 2., 3.])
print(1 / arr1) # universal func
```

```
[1.         0.5        0.33333333]
[1.         0.5        0.33333333]
```

```python
# f = lambda x : x + 2
#arr1 = arr1 + 2
arr1 = arr1 * 3
arr1
```

```
array([3., 6., 9.])
```

#### 1.6. Indexing

* numpy array의 indexing은 python list의 indexing과 같다!

```python
arr1 = np.arange(10)
```

```python
# 첫번째 원소
arr1[0]
```

```
0
```

```python
# 마지막 원소
arr1[-1]
```

```
9
```

```python
# 앞에서부터 원소 3개 slicing
arr1[:3]
```

```
array([0, 1, 2])
```

```python
arr2 = np.array([[1, 2, 3, 4],
               [5, 6, 7, 8],
               [9, 10, 11, 12]])
arr2
```

```
array([[ 1,  2,  3,  4],
       [ 5,  6,  7,  8],
       [ 9, 10, 11, 12]])
```

```python
# arr2의 2th row, 3th column 원소 = 7
arr2[1][2]
arr2[1, 2] # numpy array indexing에서 추가된 것!
```

```
7
```

```python
# arr2의 세번째 column [3, 7, 11]
arr2[0, 2]
arr2[1, 2]
arr2[2, 2]
arr2[:, 2]
```

```
array([ 3,  7, 11])
```

```python
# arr2의 두번째 row
arr2[0:2, 0:2] # arr2[1]
```

```
array([[1, 2],
       [5, 6]])
```

### 2. Numpy Methods

* numpy에서 사용되는 여러가지 함수들을 사용해봅시다.

#### 2.1. Math Functions

```python
# 표준정규분포에서 random sampling을 한 원소를 가지는 5x3 행렬을 만든다.
mat1 = np.random.randn(5, 3)
mat1
```

```
array([[ 0.37765459, -0.59941902,  1.24265268],
       [ 0.41603669, -1.93383008, -2.16308527],
       [ 0.30965658,  0.45795307, -0.19412538],
       [ 1.408876  , -1.12170785, -0.24092229],
       [-0.96010355,  1.89510812,  0.51684981]])
```

```python
# mat1에 절대값 씌우기
np.abs(mat1)
```

```
array([[0.37765459, 0.59941902, 1.24265268],
       [0.41603669, 1.93383008, 2.16308527],
       [0.30965658, 0.45795307, 0.19412538],
       [1.408876  , 1.12170785, 0.24092229],
       [0.96010355, 1.89510812, 0.51684981]])
```

```python
# mat1 제곱하기
np.square(mat1)
```

```
array([[0.14262299, 0.35930316, 1.54418567],
       [0.17308652, 3.73969878, 4.67893791],
       [0.0958872 , 0.20972101, 0.03768466],
       [1.98493158, 1.2582285 , 0.05804355],
       [0.92179882, 3.59143477, 0.26713372]])
```

```python
# mat1의 제곱근 구하기
np.sqrt(mat1) # nan = not a number
```

```
/usr/local/lib/python3.7/dist-packages/ipykernel_launcher.py:2: RuntimeWarning: invalid value encountered in sqrt
  





array([[0.61453608,        nan, 1.11474332],
       [0.64500906,        nan,        nan],
       [0.55646795, 0.6767223 ,        nan],
       [1.18696082,        nan,        nan],
       [       nan, 1.37662926, 0.71892267]])
```

```python
# linear algebra functions
vec = np.array([1, 2, 2])

# 1. norm
np.linalg.norm(vec) # vector L2 norm

# 2. eigenvalue
mat = np.array([[1, 2],
               [3, 4]])
np.linalg.eig(mat)
```

```
(array([-0.37228132,  5.37228132]), array([[-0.82456484, -0.41597356],
        [ 0.56576746, -0.90937671]]))
```

#### 2.2. Aggregation functions

```python
mat2 = np.random.rand(3, 2)
mat2
```

```
array([[0.32924457, 0.33160349],
       [0.39390233, 0.46379498],
       [0.46548057, 0.21238474]])
```

```python
# Summation
np.sum(mat2)
np.sum(mat2, axis=1)
np.sum(mat2, axis=0)
```

```
array([1.18862747, 1.00778321])
```

```python
# mean
np.mean(mat2)
np.mean(mat2, axis=0)
np.mean(mat2, axis=1)
```

```
array([0.33042403, 0.42884866, 0.33893265])
```

```python
# std
np.std(mat2)
```

```
0.08791139928701974
```

```python
# min, max
#np.min(mat2, axis=0)
np.max(mat2, axis=1)
```

```
array([0.33160349, 0.46379498, 0.46548057])
```

```python
# 최소값이 있는 Index
np.argmin(mat2, axis=0)

```

```
array([1, 1, 0])
```

```python
# 최대값이 있는 Index
np.argmax(mat2, axis=1)
```

```
array([1, 1, 0])
```

```python
mat2
```

```
array([[0.32924457, 0.33160349],
       [0.39390233, 0.46379498],
       [0.46548057, 0.21238474]])
```

```python
# 그냥 정렬 (오름차순 정렬만 지원합니다)
np.sort(mat2, axis=0) # 차이 ?

# 만약에 내림차순을 하겠다?
#np.sort(mat2, axis=0)[::-1]
```

```
array([[0.32924457, 0.21238474],
       [0.39390233, 0.33160349],
       [0.46548057, 0.46379498]])
```

```python
# index를 정렬
np.argsort(mat2, axis=0)
```

```
array([[0, 2],
       [1, 0],
       [2, 1]])
```

### 3. Performance Check

* Universal Function 기능을 통해 반복문을 사용한 것보다 훨씬 빠른 성능을 냅니다.
* 직접 실험을 통해 그 차이를 확인해보겠습니다.

```python
def reverse_num(values):
    output = np.empty(len(values))
    
    for i in range(len(values)):
        output[i] = 1.0 / values[i]
    
    return output
```

```python
# 1부터 100까지 범위에서 1000000개를 랜덤으로 뽑아서 array를 만듭니다.
big_array = np.random.randint(1, 100, 1000000)
big_array
```

```
array([70, 36, 44,  3, 13, 79, 11, 71, 95, 28, 65, 96, 63, 69,  9, 40, 82,
       41, 91, 72, 55, 98, 88, 34,  5, 53, 28, 69, 64, 55, 91, 18, 72, 43,
       38, 18, 65, 62, 62, 41, 18, 24, 78, 14, 18, 80, 47, 79, 42, 74, 76,
        8, 92, 18, 36, 56, 83, 60, 18, 12, 79, 41, 68, 39, 85, 98, 64, 20,
       57, 93, 91, 41, 42, 96, 84, 83, 63,  9, 32, 52, 18, 85, 66,  3, 50,
       90, 86, 10, 45, 80, 93, 48, 28, 33, 32, 44, 71, 78, 42, 35])
```

```python
%timeit reverse_num(big_array)
```

```
1000 loops, best of 5: 230 µs per loop
```

```python
%timeit 1.0 / big_array
```

```
The slowest run took 32.45 times longer than the fastest. This could mean that an intermediate result is being cached.
1000000 loops, best of 5: 1.39 µs per loop
```
