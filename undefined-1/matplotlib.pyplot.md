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

# matplotlib.pyplot

## 1. 정의&#x20;

* 시각화 방법에서 가장 많이 사용되는 라이브러리로서, 파이썬에 다양한 그래프 작성방법을 제공한다.
* &#x20;seaborn, folium 등의 시각화 라이브러리들에 영향을 주었다.&#x20;
* figure()를 기본적으로 그래프 그리는 객체로 사용하고, plot(), scatter() 함수를 이용하여 원하는 그래프를 그립니다.

```python
# matplotlib은 이렇게 불러오는 것이 관행입니다.
import matplotlib.pyplot as plt
#import matplotlib as mpl

# 이제 안써도 됨
#%matplotlib inline
```

```python
# 도화지를 깔고
plt.figure()
# 해당 리스트를 기준으로 하는 선을 그립니다.
plt.plot([1, 2, 4, 8, 16])
#plt.plot([1, 2, 3, 4, 5], [1, 2, 4, 8, 16])
# 보여주기
plt.show()
```

```python
# sample data를 하나 만들어봅시다!
x = ["Americano", "Cafe Latte", "Vanilla Latte", "Cold Brew", "Flat White"]
y = [1463, 301, 866, 905, 274]
```

**도화지에 그림을 그려봅시다**

순서대로 하나씩 세팅해봅니다.

1. figure & figsize
2. barplot
3. grid
4. title
5. axis label
6. lineplot
7. set label
8. legend
9. set limit in axis

```python
# 막대 그래프 그리기
plt.figure(figsize=(8, 6))
#plt.grid(alpha=0.3, color="black", linewidth=0.5)
plt.title("Coffee Sales in March", fontsize=20, loc="left")
plt.xlabel("Menu", fontsize=8)
plt.ylabel("Sales", fontsize=8)
plt.bar(x, y, color="lightcoral", label="Sales")
plt.plot(sorted([100, 200, 400, 800, 1600], reverse=True), label="Average")
plt.legend(loc="best")
#plt.ylim(0, 2000)
plt.yticks([num for num in range(0, 2100, 500)])
plt.show()
```

**이번에는 scatterplot을 그려봅시다**

1. figure & figsize
2. scatterplot
3. set color
4. set marker

```python
# 이번에는 scatterplot을 그려봅니다.
import numpy as np

x = np.random.random(1000)
y = np.random.random(1000)

plt.figure(figsize=(6, 6))
plt.scatter(x, y, color="orange", marker="x", s=50, alpha=0.3)
plt.show()
```

```python
# subplot을 이용하여 여러 개의 plot을 한번에 그립니다.
# subplot()을 이용하여 여러개의 plot을 하나의 figure에 출력할 수 있다.

# plt.subplot(nrows, ncols, index)
# nrows와 ncols가 있다고 했을 때의 위치!
## 처음할 때 굉장히 헷갈립니다!! 2 x 2로 연습을 많이 해보세요 :)
plt.figure(figsize=(6, 8))
#plt.subplot(2, 1, 1)
#plt.subplot(2, 1, 2)
#plt.subplot(2, 2, 1)
#plt.subplot(2, 2, 2)
#plt.subplot(2, 2, 3)
#plt.subplot(2, 2, 4)

plt.subplot(1, 2, 1)
plt.plot([0.1, 0.3, 0.5])
plt.subplot(3, 2, 2)
plt.bar([1, 2, 3], [3, 2, 1])
plt.subplot(3, 2, 4)
plt.plot([4, 1, -3])
plt.subplot(3, 2, 6)
plt.scatter([1, 2, 3, 4, 5], [5, 3, 4, 2, 1])
plt.show()
```

```python
## 번외. DataFrame으로 바로 plotting 가능
import pandas as pd

df = pd.DataFrame({"Menu" : x, "Count" : y})
#df = pd.DataFrame(data=y, index=x, columns=["Count"])
#plt.figure()
df.plot(kind="bar", x="Menu", y="Count")
#plt.show()
#df.plot(kind="barh")
#df
```

```
<matplotlib.axes._subplots.AxesSubplot at 0x7f8655065450>
```
