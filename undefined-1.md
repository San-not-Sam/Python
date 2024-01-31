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

# \[개념] 파이썬 라이브러리

## # Library

### 1) 정의&#x20;

* 패키지(package)라고도 하며, 사용자가 코드를 직접 작성해야 하는 수고를 덜어주고, 유용한 기능을 쉽게 사용할 수 있도록 돕는 함수(function)와 메서드(method)로 구성된 여러 모듈의 집합이다.

### 2) 특징&#x20;

* 명령어 중 `import` 로 불러올 수 있다.&#x20;
* 데이터 분석에 빈번하게 이용되는 라이브러리는 Colab에  내장되어 있다.&#x20;
* 내장되어 있지 않은 라이브러리는 `!pip install '라이브러리 이름'`으로 설치가 가능하다.
* **\[용어 정리]**  모듈(Module) -   파이썬 확장자(.py)로 구성되어 실행이 가능한 하나의 파일로, '함수(function)', '클래스(class)', '변수(variable)'로 구성된다.&#x20;

<figure><img src=".gitbook/assets/image.png" alt=""><figcaption><p><a href="https://medium.com/@learnbay/python-libraries-for-data-analysis-and-modeling-in-data-science-c5c994208385">https://medium.com/@learnbay/python-libraries-for-data-analysis-and-modeling-in-data-science-c5c994208385</a></p></figcaption></figure>

## 1-1. Numpy

### 1) 정의

* 동일한 타입의 데이터가 나열되어 있는 집합으로, 벡터 및 수치 연산에 최적화된 라이브러리이다(Numerical computing with Python).&#x20;
* 다차원 배열을 쉽고 빠르게 계산하는  파이썬의 대표 라이브러리이다.&#x20;
* 데이터 분석시, 주로  Pandas와 연계되어 사용된다.

<figure><img src=".gitbook/assets/image (19).png" alt="" width="563"><figcaption><p><a href="https://medium.com/byte-sized-code/common-placeholders-in-numpy-arrays-1c3673718f2f">https://medium.com/byte-sized-code/common-placeholders-in-numpy-arrays-1c3673718f2f</a></p></figcaption></figure>

### 2) 특징&#x20;

* 배열이 적재된 축(axis) 의 개수에 따라 다양한 차원을 표현할 수 있다. e.g. '1차원', '2차원', 3차원'&#x20;
* Numpy는 파이썬에서 지원되지 않는 ‘배열 자료형’에 대한 대안이다.
* '최적화된 C code로 구현되어 있어 뛰어난 성능을 보인다.&#x20;
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
* 데이터의 형태는 텍스트, 오디오, 이미지 등 가지각색 다양한 형태로 존재하는데, 이에 대한 해석은 컴퓨터의 연산 작업 구조상 형태와 관계없이 배열 단위의 형태로 이뤄진다. 넘파이는데이터 분석시 파이썬을 통해 모든 형태의 데이터를 분석하기 위해 사용된다.

## 1-2. Numpy Array&#x20;

### 1) 정의

numpy에서 사용되는 기본적인 자료구조로, C언어의 array 구조와 동일한 개념이다.&#x20;

<figure><img src=".gitbook/assets/image (1).png" alt=""><figcaption><p>Source : https://indianaiproduction.com/python-numpy-array/</p></figcaption></figure>

### 2) List와의 공통점&#x20;

1. indexing으로 원소를 접근할 수 있습니다.
2. 생성 후 assignment operator를 이용해서 원소의 update가 가능합니다.

### 3) List와의 차이점

1. 선언한 이후에 크기 변경이 불가능합니다.
2. **\[homogeneous array]** 모든 원소의 데이터 타입이 동일해야 합니다.&#x20;
3. 제공하는 데이터 타입이 다르다. 다중 리스트 구조와 달리, 넘파이 배열은 동일한 데이터 타입으로 구성된다.&#x20;

<figure><img src=".gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

4. 수치와 관련된 데이터 타입이 대부분입니다.
5. 원소의 크기(memory size)를 조절할 수 있으며, 크기에 따라 표현할 수 있는 수치 범위가 정해집니다.&#x20;

<table><thead><tr><th width="125"></th><th width="177"></th><th width="188"></th><th width="153"></th><th></th></tr></thead><tbody><tr><td>np.int8</td><td>수치 표현에 8 bits를 사용한다</td><td>00000000 ~ 11111111</td><td>2^8 (256개)</td><td>-128 ~ 127</td></tr><tr><td>np.float32</td><td>실수 표현에 32 bits를 사용한다</td><td>exponent, mantissa, sign</td><td>single precision</td><td></td></tr></tbody></table>

### <mark style="color:orange;">4) 배열 데이터 슬라이싱과 정렬</mark>&#x20;

1. 배열 생성하기&#x20;
2. 슬라이싱
3. Fancy 인덱싱
4. Boolean 인덱싱
5. 유용한 Numpy 함수&#x20;
6. 배열 차원 변환&#x20;
7. 정렬

### 5) 행렬(matrix) 연산과 성능&#x20;

1. 정의
2. 기본 연산
   1. 덧셈 & 뺄셈
   2. 곱셈 & 나눗셈&#x20;
3. 행렬 집계 함수
   1. 합계
   2. 최대
   3. 최소
   4. 평균
   5. <mark style="color:orange;">표준편차</mark>
4. <mark style="color:orange;">Broadcasting 연산</mark>
5.



## 2-1. Pandas

### 1) 정의

* 정형 데이터 분석에 최적화된 라이브러리&#x20;

### 2) 특징&#x20;

* 정형 데이터를 효율적으로 표현하는 DataFrame 형태로 모든 데이터를 표현한다.&#x20;
* Numpy와 마찬가지로, 벡터 연산에 최적화되어있다.&#x20;
* 표 형태의 데이터(행렬) 조작에 특화되어 있다.&#x20;
* 대용량 데이터 셋을 이용한 여러 통계 처리 기능을 제공한다.
* 엑셀의 거의 모든 기능과 SQL과 같은 DB문도 구현한다(호환).&#x20;

```
# pandas example
import pandas as pd
df = pd.DataFrame(np.random.randn(5, 3))
df.head()
```

### 3) 사용하는 이유

* 대부분의 정제된 데이터들은 테이블 형태로 표현된다. Pandas는이런 테이블 형태의 데이터를 분석하기에 최적의 라이브러리입니다.&#x20;
* Numpy처럼 정형화된 데이터 연산에 최적화되어 있기에,  성능이 매우 뛰어나다.  &#x20;
* 다양한 정형 데이터를 통합 관리할 수 있다. json, html, csv, xlsx, hdf5, sql, ... 모 두 DataFrame으로 통일해서 표현될 수 있다.&#x20;
* 엑셀에서 제공하는 거의 모든 연산 기능을 제공할 정도로,  편의성이 좋다.

### 4) 활용

* 엑셀 전처리작업
* SQL  DB 작업
* 웹 크롤링&#x20;
* 시각화&#x20;

## 2-2. Pandas DF (DataFrame)

### 1) 정의

* pandas 라이브러리가 사용하는 기본 자료구조

<figure><img src=".gitbook/assets/image (15).png" alt=""><figcaption><p>Source : https://www.geeksforgeeks.org/creating-a-pandas-dataframe/</p></figcaption></figure>

### 2) 특징

* 기본적으로2차원 테이블 구조이지만, 1차원 구조로된  series 있다. (1 row, 1 column)&#x20;
* \[**indexing**] row, column으로 모든 원소를 구분한다. &#x20;
* index, columns, values라는 객체 변수를 가지고 있다.&#x20;
* Relational DB와 완전히 호환됩니다.&#x20;
* 하나의 column을 기준으로 모든 원소의 data type이 동일하다(모든 numpy array가 가지는 data type과 동일).
* numpy array를 상위 호환하는 개념으로서, 내부 구현체로 numpy array를 사용하기에universal function을 사용할 수 있다.&#x20;

## 3. Matplotlib & Seaborn

### 1) Matplotlib 정의와 특징&#x20;

* 합성어(**Mat**h + **Plot** + **Lib**rary)로, 파이썬 오픈소스 라이브러리 中 가장 널리 사용되는 표준시각화 라이브러리이다.&#x20;
* MATLAB의 기능들을 파이썬으로 가져오는 컨셉으로 시작되었다.&#x20;
* 각종 논문에서 figure를 그릴 때, 사용될 만큼 깔끔하게 그래프를 그려주는 것으로 유명하다.&#x20;
* 거의 모든 그래프 형태를 표현할 수 있으며, 세부 옵션 조정을 통해 커스터마이징이 가능하다.&#x20;
* Numpy 및 Pandas와의 연동성이 높다.&#x20;
* `figure` 라는 도화지에 여러 component를 얹어서 그래프를 완성하는 컨셉으로 구현된다.
* 구현하는 방법은 크게 `pyplot` 와 `OOP-style`가 있다. 신속하되 적당한 퀄리티의 그래프를 원하면 전자를, 디테일한 표현이 담긴 그래프를 원하면 후자를 추천한다.&#x20;

### 2) Matplotlib 데이터 타입에 따른 그래프 시각화

<table><thead><tr><th width="151">데이터 유형</th><th width="300">예시 데이터 </th><th width="193">그래프 종류 </th></tr></thead><tbody><tr><td>연속형 데이터</td><td><ul><li><p>연속형 데이터 간 </p><ul><li>상관관계</li><li>변화량</li></ul></li></ul></td><td><ul><li>산점도(Scatter)</li><li>밀도(Density) </li></ul></td></tr><tr><td>범주형 데이터</td><td><ul><li><p>항목 또는 그룹 간 </p><ul><li>비교, 비율, 순위형 자료</li></ul></li></ul></td><td><p></p><ul><li>박스(Box)</li><li>바(Bar)</li><li>파이(Pie)</li><li>히트맵(Heat map)</li></ul></td></tr><tr><td>시계열 데이터</td><td><ul><li><p> 시간 단위 데이터의 경향성, 흐름 </p><ul><li>e.g. 날짜, 요일 등</li></ul></li></ul></td><td><p></p><ul><li>라인(Line)</li><li>리본(Ribbon)</li><li>VEB 그래프</li></ul></td></tr></tbody></table>

<figure><img src=".gitbook/assets/image (16).png" alt="" width="563"><figcaption><p>Source: https://matplotlib.org/stable/tutorials/introductory/usage.html#sphx-glr-tutorials-introductory-usage- py</p></figcaption></figure>

### 3) Seaborn 정의와 특징

* Statistical Data Visualization library based on matplotlib
* Matplotlib을 더 편하게 사용할 수 있도록 만든 라이브러리이다.&#x20;
* Matplotlib이 MATLAB을 표방하여 디자인된 것과 달리, Seaborn은 Numpy, Pandas 같은 파이썬 라이브러리들을 편하게 시각화하는 것을 중점으로 디자인된 라이브러리입니다.&#x20;
* 특히, DataFrame을 직접적으로 지원하기 때문에 훨씬 편리하게 데이터를 시각화할 수 있다.&#x20;
* 그리고 Matplotlib 위에 만들어져서, Matplotlib에 있는 개념들을 확장해서 사용할 수 있다.&#x20;
* 다양한 기본 plot들이 있어서 통계 분석을 빠르게 수행할 수 있다. → **EDA**
* **통계 데이터 시각화에 최적화된 라이브러리로서, 매력적이고 유익한 통계 그래픽을 위한 높은 수준의 인터페이스를 자랑한다.**&#x20;
* 보통 Matplotlib와 함께 사용한다.&#x20;

### 4) Seaborn 장점&#x20;

* 통계 지원 기능이 제공된다.&#x20;
* 다양한 색조의 팔레팅(various hues)이 지원된다.&#x20;
* Pandas 데이터 프레임과 호환성이 높다. &#x20;
* Matplotlib 그래프와 호환성이 높다.&#x20;

### 5) 비교 (Matplotlib vs. Seaborn)

<table><thead><tr><th width="111">특징</th><th width="345" align="center">Matplotlib</th><th align="center">Seaborn</th></tr></thead><tbody><tr><td>용도 </td><td align="center">Pandas 및 Numpy를 활용한 다양한 플롯팅 </td><td align="center">Matplotlib와 용도가 동일한 확장판 </td></tr><tr><td>문법</td><td align="center">커스터마이징에서 코드가 길어질 만큼 복잡</td><td align="center">학습과 이해가 용이할만큼 간단</td></tr><tr><td>다중 figure</td><td align="center">일일이 옵션을 설정해야 한다.</td><td align="center">자동 생성 기능이 있다.</td></tr><tr><td>유연성</td><td align="center">커스터마이징을 허용할 만큼 유연성이 높다.</td><td align="center">자체 제공 테마 外 유연성이 낮다. </td></tr></tbody></table>



### 6) 기본 plots

* Lineplot

{% embed url="https://seaborn.pydata.org/examples/errorband_lineplots.html" %}

* Boxplot

{% embed url="https://seaborn.pydata.org/examples/grouped_boxplot.html" %}

* Jointplot

{% embed url="https://seaborn.pydata.org/examples/joint_kde.html" %}

* Pairplot

{% embed url="https://seaborn.pydata.org/examples/scatterplot_matrix.html" %}

## 4. Folium

### 1) 정의와 특징

* 지도 시각화로 으뜸이 되는 패키지
* 점(dot)과 선(line) 등 여러 방식으로 지도 표현이 가능
* 시각화 결과를 html로 저장할 수 있기에, 타인과의 공유가 원활하다.
* Pandas와의 호환성이 높다.&#x20;
* 간단한 지리 정보 특징을 표현하기 위한 표준 지도인 JSON 포맷을 기본 자료형으로 사용한다.&#x20;

### 2) 대표적 기능

* Interactive 지도
* 시계열 지도 변화 분석
* 히트맵(Heatmap)&#x20;



## 5. 탐색적 데이터 분석 (EDA)&#x20;

### 1) 정의

* Exploratory Data Analysis의 준말로,  데이터에서 분석에 필요한 여러 통계량을 계산하고, 시각화로이를 확인하는 작업.

<figure><img src=".gitbook/assets/image (18).png" alt=""><figcaption><p>Chapter.03_탐색적_데이터_분석-01. 탐색적 데이터 분석이란</p></figcaption></figure>

### 2) RECAP

* EDA는 분석을 하면서 데이터에서 확인하고 싶은 정보들을 찾아가는 즉, 데이터와 친해지는 과정이다.&#x20;
* 뚜렷하게정해진 프로세스는 따로 없고, 전적으로분석가들의 직관과 분석 프로세스에 달려있다. &#x20;
* 어떤 데이터를 사용하느냐에 따라서도 천차만별로 달라진다. &#x20;
* Data Scientist로서의 역량은 나만의 EDA process를 구축하는 데에 있다.&#x20;

### 3) 고려 사항

* **\[분석의 목표]** 해당 데이터를 보고 어떤 인사이트를 이끌어내고 싶은가?
* **\[분석 방법론]** 데이터의 여러 특성을 어떻게 파악하는가?&#x20;
* **\[분석을 위 한 프로그래밍]** 지금까지 배운 오픈소스 라이브러리들로 EDA를 어떻게 수행하는가?&#x20;

### 3) Hands-on

{% embed url="https://www.kaggle.com/ihormuliar/starbucks-customer-data" %}

{% embed url="https://www.kaggle.com/c/kaggle-survey-2021/data" %}

{% embed url="https://www.data.go.kr/data/15083033/fileData.do" %}
