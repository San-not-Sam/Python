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

# Pandas Method

## 1. Pandas DataFrame and Operations

```python
# pandas 라이브러리를 불러옵니다. pd를 약칭으로 사용합니다.
import pandas as pd
import numpy as np
```

* DataFrame은 2차원 테이블이고, 테이블의 한 줄(행/열)을 Series라고 합니다.
* Series의 모임이 곧, DataFrame이 됩니다.

```python
# s는 1, 3, 5, np.nan, 6, 8을 원소로 가지는 pandas.Series
pd.Series([1, 3, 5, np.nan, 6, 8])
```

```
0    1.0
1    3.0
2    5.0
3    NaN
4    6.0
5    8.0
dtype: float64
```

```python
# 12x4 행렬에 1부터 48까지의 숫자를 원소를 가지고, index는 0부터 시작하고, coulmns은 순서대로 X1, X2, X3, X4로 하는 DataFrame 생성
df = pd.DataFrame(data=np.arange(1, 49).reshape(12, 4),
                  index=np.arange(12),
                  columns=["X1", "X2", "X3", "X4"])

df
```

|    | X1 | X2 | X3 | X4 |
| -- | -- | -- | -- | -- |
| 0  | 1  | 2  | 3  | 4  |
| 1  | 5  | 6  | 7  | 8  |
| 2  | 9  | 10 | 11 | 12 |
| 3  | 13 | 14 | 15 | 16 |
| 4  | 17 | 18 | 19 | 20 |
| 5  | 21 | 22 | 23 | 24 |
| 6  | 25 | 26 | 27 | 28 |
| 7  | 29 | 30 | 31 | 32 |
| 8  | 33 | 34 | 35 | 36 |
| 9  | 37 | 38 | 39 | 40 |
| 10 | 41 | 42 | 43 | 44 |
| 11 | 45 | 46 | 47 | 48 |

\<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24" width="24px">

```
  <script>
    const buttonEl =
      document.querySelector('#df-f340ca3a-f13c-4cf4-ac22-ee642be0d438 button.colab-df-convert');
    buttonEl.style.display =
      google.colab.kernel.accessAllowed ? 'block' : 'none';

    async function convertToInteractive(key) {
      const element = document.querySelector('#df-f340ca3a-f13c-4cf4-ac22-ee642be0d438');
      const dataTable =
        await google.colab.kernel.invokeFunction('convertToInteractive',
                                                 [key], {});
      if (!dataTable) return;

      const docLinkHtml = 'Like what you see? Visit the ' +
        '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
        + ' to learn more about interactive tables.';
      element.innerHTML = '';
      dataTable['output_type'] = 'display_data';
      await google.colab.output.renderOutput(dataTable, element);
      const docLink = document.createElement('div');
      docLink.innerHTML = docLinkHtml;
      element.appendChild(docLink);
    }
  </script>
</div>
```

```python
# dataframe index
df.index
```

```
Int64Index([0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11], dtype='int64')
```

```python
# dataframe columns
df.columns
```

```
Index(['X1', 'X2', 'X3', 'X4'], dtype='object')
```

```python
# dataframe values
df.values
```

```
array([[ 1,  2,  3,  4],
       [ 5,  6,  7,  8],
       [ 9, 10, 11, 12],
       [13, 14, 15, 16],
       [17, 18, 19, 20],
       [21, 22, 23, 24],
       [25, 26, 27, 28],
       [29, 30, 31, 32],
       [33, 34, 35, 36],
       [37, 38, 39, 40],
       [41, 42, 43, 44],
       [45, 46, 47, 48]])
```

```python
# 특정 column을 가져오기
df["X2"] # dictionary like
```

```
0      2
1      6
2     10
3     14
4     18
5     22
6     26
7     30
8     34
9     38
10    42
11    46
Name: X2, dtype: int64
```

```python
# X1 column에 2 더하기
#df["X1"] = df["X1"] + 2
df["X1"] + 2
```

```
0      3
1      7
2     11
3     15
4     19
5     23
6     27
7     31
8     35
9     39
10    43
11    47
Name: X1, dtype: int64
```

## 2. Dataframe 기초 method&#x20;

```python
# dataframe의 맨 위 다섯줄을 보여주는 head() --> 5줄 display
#df.head()
df.tail()
```

|    | X1 | X2 | X3 | X4 |
| -- | -- | -- | -- | -- |
| 7  | 29 | 30 | 31 | 32 |
| 8  | 33 | 34 | 35 | 36 |
| 9  | 37 | 38 | 39 | 40 |
| 10 | 41 | 42 | 43 | 44 |
| 11 | 45 | 46 | 47 | 48 |

\<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24" width="24px">

```
  <script>
    const buttonEl =
      document.querySelector('#df-66cf8ef2-bdd2-44fb-85e7-30313b41b8e3 button.colab-df-convert');
    buttonEl.style.display =
      google.colab.kernel.accessAllowed ? 'block' : 'none';

    async function convertToInteractive(key) {
      const element = document.querySelector('#df-66cf8ef2-bdd2-44fb-85e7-30313b41b8e3');
      const dataTable =
        await google.colab.kernel.invokeFunction('convertToInteractive',
                                                 [key], {});
      if (!dataTable) return;

      const docLinkHtml = 'Like what you see? Visit the ' +
        '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
        + ' to learn more about interactive tables.';
      element.innerHTML = '';
      dataTable['output_type'] = 'display_data';
      await google.colab.output.renderOutput(dataTable, element);
      const docLink = document.createElement('div');
      docLink.innerHTML = docLinkHtml;
      element.appendChild(docLink);
    }
  </script>
</div>
```

```python
# 10줄
df.head(10)
```

|   | X1 | X2 | X3 | X4 |
| - | -- | -- | -- | -- |
| 0 | 1  | 2  | 3  | 4  |
| 1 | 5  | 6  | 7  | 8  |
| 2 | 9  | 10 | 11 | 12 |
| 3 | 13 | 14 | 15 | 16 |
| 4 | 17 | 18 | 19 | 20 |
| 5 | 21 | 22 | 23 | 24 |
| 6 | 25 | 26 | 27 | 28 |
| 7 | 29 | 30 | 31 | 32 |
| 8 | 33 | 34 | 35 | 36 |
| 9 | 37 | 38 | 39 | 40 |

\<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24" width="24px">

```
  <script>
    const buttonEl =
      document.querySelector('#df-53470bf3-728b-41ef-8257-52da544510e1 button.colab-df-convert');
    buttonEl.style.display =
      google.colab.kernel.accessAllowed ? 'block' : 'none';

    async function convertToInteractive(key) {
      const element = document.querySelector('#df-53470bf3-728b-41ef-8257-52da544510e1');
      const dataTable =
        await google.colab.kernel.invokeFunction('convertToInteractive',
                                                 [key], {});
      if (!dataTable) return;

      const docLinkHtml = 'Like what you see? Visit the ' +
        '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
        + ' to learn more about interactive tables.';
      element.innerHTML = '';
      dataTable['output_type'] = 'display_data';
      await google.colab.output.renderOutput(dataTable, element);
      const docLink = document.createElement('div');
      docLink.innerHTML = docLinkHtml;
      element.appendChild(docLink);
    }
  </script>
</div>
```

```python
# dataframe에 대한 전체적인 요약정보를 보여줍니다. index, columns, null/not-null/dtype/memory usage가 표시됩니다.
df.info()
```

```
<class 'pandas.core.frame.DataFrame'>
Int64Index: 12 entries, 0 to 11
Data columns (total 4 columns):
 #   Column  Non-Null Count  Dtype
---  ------  --------------  -----
 0   X1      12 non-null     int64
 1   X2      12 non-null     int64
 2   X3      12 non-null     int64
 3   X4      12 non-null     int64
dtypes: int64(4)
memory usage: 480.0 bytes
```

```python
# dataframe에 대한 전체적인 통계정보를 보여줍니다.
df.describe()
```

|       | X1        | X2        | X3        | X4        |
| ----- | --------- | --------- | --------- | --------- |
| count | 12.000000 | 12.000000 | 12.000000 | 12.000000 |
| mean  | 23.000000 | 24.000000 | 25.000000 | 26.000000 |
| std   | 14.422205 | 14.422205 | 14.422205 | 14.422205 |
| min   | 1.000000  | 2.000000  | 3.000000  | 4.000000  |
| 25%   | 12.000000 | 13.000000 | 14.000000 | 15.000000 |
| 50%   | 23.000000 | 24.000000 | 25.000000 | 26.000000 |
| 75%   | 34.000000 | 35.000000 | 36.000000 | 37.000000 |
| max   | 45.000000 | 46.000000 | 47.000000 | 48.000000 |

\<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24" width="24px">

```
  <script>
    const buttonEl =
      document.querySelector('#df-d30d50ec-8487-4e5f-8aed-2b6a111d3880 button.colab-df-convert');
    buttonEl.style.display =
      google.colab.kernel.accessAllowed ? 'block' : 'none';

    async function convertToInteractive(key) {
      const element = document.querySelector('#df-d30d50ec-8487-4e5f-8aed-2b6a111d3880');
      const dataTable =
        await google.colab.kernel.invokeFunction('convertToInteractive',
                                                 [key], {});
      if (!dataTable) return;

      const docLinkHtml = 'Like what you see? Visit the ' +
        '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
        + ' to learn more about interactive tables.';
      element.innerHTML = '';
      dataTable['output_type'] = 'display_data';
      await google.colab.output.renderOutput(dataTable, element);
      const docLink = document.createElement('div');
      docLink.innerHTML = docLinkHtml;
      element.appendChild(docLink);
    }
  </script>
</div>
```

```python
# X2 column를 기준으로 내림차순 정렬
df.sort_values(by="X2", ascending=False)
```

|    | X1 | X2 | X3 | X4 |
| -- | -- | -- | -- | -- |
| 11 | 45 | 46 | 47 | 48 |
| 10 | 41 | 42 | 43 | 44 |
| 9  | 37 | 38 | 39 | 40 |
| 8  | 33 | 34 | 35 | 36 |
| 7  | 29 | 30 | 31 | 32 |
| 6  | 25 | 26 | 27 | 28 |
| 5  | 21 | 22 | 23 | 24 |
| 4  | 17 | 18 | 19 | 20 |
| 3  | 13 | 14 | 15 | 16 |
| 2  | 9  | 10 | 11 | 12 |
| 1  | 5  | 6  | 7  | 8  |
| 0  | 1  | 2  | 3  | 4  |

\<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24" width="24px">

```
  <script>
    const buttonEl =
      document.querySelector('#df-c5688e73-0e8f-44d4-99cc-d4ba502c7885 button.colab-df-convert');
    buttonEl.style.display =
      google.colab.kernel.accessAllowed ? 'block' : 'none';

    async function convertToInteractive(key) {
      const element = document.querySelector('#df-c5688e73-0e8f-44d4-99cc-d4ba502c7885');
      const dataTable =
        await google.colab.kernel.invokeFunction('convertToInteractive',
                                                 [key], {});
      if (!dataTable) return;

      const docLinkHtml = 'Like what you see? Visit the ' +
        '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
        + ' to learn more about interactive tables.';
      element.innerHTML = '';
      dataTable['output_type'] = 'display_data';
      await google.colab.output.renderOutput(dataTable, element);
      const docLink = document.createElement('div');
      docLink.innerHTML = docLinkHtml;
      element.appendChild(docLink);
    }
  </script>
</div>
```

## 3.  Fancy Indexing !

* 데이터를 filtering <=> Search !
* 전체 데이터에서 원하는 일부의 데이터를 찾아오는 방법 !

```python
# pandas dataframe은 column 이름을 이용하여 기본적인 Indexing이 가능합니다.
# X1 column을 indexing
#df["X1"]
df.X1
```

```
0      1
1      5
2      9
3     13
4     17
5     21
6     25
7     29
8     33
9     37
10    41
11    45
Name: X1, dtype: int64
```

```python
# dataframe에서 slicing을 이용하면 row 단위로 잘려나옵니다.
# 앞에서 3줄을 slicing 합니다.
df[:3]
```

|   | X1 | X2 | X3 | X4 |
| - | -- | -- | -- | -- |
| 0 | 1  | 2  | 3  | 4  |
| 1 | 5  | 6  | 7  | 8  |
| 2 | 9  | 10 | 11 | 12 |

\<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24" width="24px">

```
  <script>
    const buttonEl =
      document.querySelector('#df-c7981670-136c-423d-bd86-fdf9841a3153 button.colab-df-convert');
    buttonEl.style.display =
      google.colab.kernel.accessAllowed ? 'block' : 'none';

    async function convertToInteractive(key) {
      const element = document.querySelector('#df-c7981670-136c-423d-bd86-fdf9841a3153');
      const dataTable =
        await google.colab.kernel.invokeFunction('convertToInteractive',
                                                 [key], {});
      if (!dataTable) return;

      const docLinkHtml = 'Like what you see? Visit the ' +
        '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
        + ' to learn more about interactive tables.';
      element.innerHTML = '';
      dataTable['output_type'] = 'display_data';
      await google.colab.output.renderOutput(dataTable, element);
      const docLink = document.createElement('div');
      docLink.innerHTML = docLinkHtml;
      element.appendChild(docLink);
    }
  </script>
</div>
```

```python
# df에서 index value를 기준으로 indexing도 가능합니다. (여전히 row 단위)
#df.index[0]
df.loc[0]
```

```
X1    1
X2    2
X3    3
X4    4
Name: 0, dtype: int64
```

```python
# df.loc는 특정값을 기준으로 indexing합니다. (key - value)
df.loc[7]
```

```
X1    29
X2    30
X3    31
X4    32
Name: 7, dtype: int64
```

```python
df
```

|    | X1 | X2 | X3 | X4 |
| -- | -- | -- | -- | -- |
| 0  | 1  | 2  | 3  | 4  |
| 1  | 5  | 6  | 7  | 8  |
| 2  | 9  | 10 | 11 | 12 |
| 3  | 13 | 14 | 15 | 16 |
| 4  | 17 | 18 | 19 | 20 |
| 5  | 21 | 22 | 23 | 24 |
| 6  | 25 | 26 | 27 | 28 |
| 7  | 29 | 30 | 31 | 32 |
| 8  | 33 | 34 | 35 | 36 |
| 9  | 37 | 38 | 39 | 40 |
| 10 | 41 | 42 | 43 | 44 |
| 11 | 45 | 46 | 47 | 48 |

\<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24" width="24px">

```
  <script>
    const buttonEl =
      document.querySelector('#df-104383f0-68e5-46db-afff-c7ff2dec29a2 button.colab-df-convert');
    buttonEl.style.display =
      google.colab.kernel.accessAllowed ? 'block' : 'none';

    async function convertToInteractive(key) {
      const element = document.querySelector('#df-104383f0-68e5-46db-afff-c7ff2dec29a2');
      const dataTable =
        await google.colab.kernel.invokeFunction('convertToInteractive',
                                                 [key], {});
      if (!dataTable) return;

      const docLinkHtml = 'Like what you see? Visit the ' +
        '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
        + ' to learn more about interactive tables.';
      element.innerHTML = '';
      dataTable['output_type'] = 'display_data';
      await google.colab.output.renderOutput(dataTable, element);
      const docLink = document.createElement('div');
      docLink.innerHTML = docLinkHtml;
      element.appendChild(docLink);
    }
  </script>
</div>
```

```python
# df.loc에 2차원 indexing도 가능합니다.
#df.loc[9, "X4"]
#df.loc[3:5, "X2":"X4"]
df.loc[[0, 1, 4, 6, 10], ["X1", "X3"]]
```

|    | X1 | X3 |
| -- | -- | -- |
| 0  | 1  | 3  |
| 1  | 5  | 7  |
| 4  | 17 | 19 |
| 6  | 25 | 27 |
| 10 | 41 | 43 |

\<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24" width="24px">

```
  <script>
    const buttonEl =
      document.querySelector('#df-1ea9189f-183c-48d5-a59c-0fafbb3d6905 button.colab-df-convert');
    buttonEl.style.display =
      google.colab.kernel.accessAllowed ? 'block' : 'none';

    async function convertToInteractive(key) {
      const element = document.querySelector('#df-1ea9189f-183c-48d5-a59c-0fafbb3d6905');
      const dataTable =
        await google.colab.kernel.invokeFunction('convertToInteractive',
                                                 [key], {});
      if (!dataTable) return;

      const docLinkHtml = 'Like what you see? Visit the ' +
        '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
        + ' to learn more about interactive tables.';
      element.innerHTML = '';
      dataTable['output_type'] = 'display_data';
      await google.colab.output.renderOutput(dataTable, element);
      const docLink = document.createElement('div');
      docLink.innerHTML = docLinkHtml;
      element.appendChild(docLink);
    }
  </script>
</div>
```

```python
# dataframe에 조건식을 적용해주면 조건에 만족하는지 여부를 알려주는 "mask"가 생깁니다.
# Q. df에서 X3 column에 있는 원소들중에 3의 배수만 출력해주세요!
#df[df["X3"] > 20] # mask
df[df["X3"] % 3 == 0]
```

|   | X1 | X2 | X3 | X4 |
| - | -- | -- | -- | -- |
| 0 | 1  | 2  | 3  | 4  |
| 3 | 13 | 14 | 15 | 16 |
| 6 | 25 | 26 | 27 | 28 |
| 9 | 37 | 38 | 39 | 40 |

\<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24" width="24px">

```
  <script>
    const buttonEl =
      document.querySelector('#df-606abda6-ecc1-4b33-a220-42bf91c558a7 button.colab-df-convert');
    buttonEl.style.display =
      google.colab.kernel.accessAllowed ? 'block' : 'none';

    async function convertToInteractive(key) {
      const element = document.querySelector('#df-606abda6-ecc1-4b33-a220-42bf91c558a7');
      const dataTable =
        await google.colab.kernel.invokeFunction('convertToInteractive',
                                                 [key], {});
      if (!dataTable) return;

      const docLinkHtml = 'Like what you see? Visit the ' +
        '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
        + ' to learn more about interactive tables.';
      element.innerHTML = '';
      dataTable['output_type'] = 'display_data';
      await google.colab.output.renderOutput(dataTable, element);
      const docLink = document.createElement('div');
      docLink.innerHTML = docLinkHtml;
      element.appendChild(docLink);
    }
  </script>
</div>
```

```python
df
```

|    | X1 | X2 | X3 | X4 |
| -- | -- | -- | -- | -- |
| 0  | 1  | 2  | 3  | 4  |
| 1  | 5  | 6  | 7  | 8  |
| 2  | 9  | 10 | 11 | 12 |
| 3  | 13 | 14 | 15 | 16 |
| 4  | 17 | 18 | 19 | 20 |
| 5  | 21 | 22 | 23 | 24 |
| 6  | 25 | 26 | 27 | 28 |
| 7  | 29 | 30 | 31 | 32 |
| 8  | 33 | 34 | 35 | 36 |
| 9  | 37 | 38 | 39 | 40 |
| 10 | 41 | 42 | 43 | 44 |
| 11 | 45 | 46 | 47 | 48 |

\<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24" width="24px">

```
  <script>
    const buttonEl =
      document.querySelector('#df-f996fc4c-4910-424e-82b3-f44bb0da990c button.colab-df-convert');
    buttonEl.style.display =
      google.colab.kernel.accessAllowed ? 'block' : 'none';

    async function convertToInteractive(key) {
      const element = document.querySelector('#df-f996fc4c-4910-424e-82b3-f44bb0da990c');
      const dataTable =
        await google.colab.kernel.invokeFunction('convertToInteractive',
                                                 [key], {});
      if (!dataTable) return;

      const docLinkHtml = 'Like what you see? Visit the ' +
        '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
        + ' to learn more about interactive tables.';
      element.innerHTML = '';
      dataTable['output_type'] = 'display_data';
      await google.colab.output.renderOutput(dataTable, element);
      const docLink = document.createElement('div');
      docLink.innerHTML = docLinkHtml;
      element.appendChild(docLink);
    }
  </script>
</div>
```

```python
# 2차원 리스트 indexing과 같은 원리가 되었습니다.
# integer-location based indexing
df.iloc[5]
```

```
X1    21
X2    22
X3    23
X4    24
Name: 5, dtype: int64
```

```python
# iloc로 2차원 indexing을 하게되면, row 기준으로 index 3,4를 가져오고 column 기준으로 0, 1을 가져옵니다.
df.iloc[[3, 4], [0, 1]]
```

|   | X1 | X2 |
| - | -- | -- |
| 3 | 13 | 14 |
| 4 | 17 | 18 |

\<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24" width="24px">

```
  <script>
    const buttonEl =
      document.querySelector('#df-de6f2569-c858-4ac4-b6b8-bfb264267132 button.colab-df-convert');
    buttonEl.style.display =
      google.colab.kernel.accessAllowed ? 'block' : 'none';

    async function convertToInteractive(key) {
      const element = document.querySelector('#df-de6f2569-c858-4ac4-b6b8-bfb264267132');
      const dataTable =
        await google.colab.kernel.invokeFunction('convertToInteractive',
                                                 [key], {});
      if (!dataTable) return;

      const docLinkHtml = 'Like what you see? Visit the ' +
        '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
        + ' to learn more about interactive tables.';
      element.innerHTML = '';
      dataTable['output_type'] = 'display_data';
      await google.colab.output.renderOutput(dataTable, element);
      const docLink = document.createElement('div');
      docLink.innerHTML = docLinkHtml;
      element.appendChild(docLink);
    }
  </script>
</div>
```

```python
# Q. 2차원 indexing에 뒤에가 : 면 어떤 의미일까요?
df.loc[3:10, :]
df.loc[:, "X1":"X2"]
df.iloc[:, 0:1]
df.iloc[0:3, 0:2]
```

|   | X1 | X2 |
| - | -- | -- |
| 0 | 1  | 2  |
| 1 | 5  | 6  |
| 2 | 9  | 10 |

\<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24" width="24px">

```
  <script>
    const buttonEl =
      document.querySelector('#df-10005027-76d9-4ab0-86f3-c0518588a0f3 button.colab-df-convert');
    buttonEl.style.display =
      google.colab.kernel.accessAllowed ? 'block' : 'none';

    async function convertToInteractive(key) {
      const element = document.querySelector('#df-10005027-76d9-4ab0-86f3-c0518588a0f3');
      const dataTable =
        await google.colab.kernel.invokeFunction('convertToInteractive',
                                                 [key], {});
      if (!dataTable) return;

      const docLinkHtml = 'Like what you see? Visit the ' +
        '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
        + ' to learn more about interactive tables.';
      element.innerHTML = '';
      dataTable['output_type'] = 'display_data';
      await google.colab.output.renderOutput(dataTable, element);
      const docLink = document.createElement('div');
      docLink.innerHTML = docLinkHtml;
      element.appendChild(docLink);
    }
  </script>
</div>
```

## 4. 여러 DataFrame 합치기

```python
df1 = pd.DataFrame({'A': ['A0', 'A1', 'A2', 'A3'], 
                    'B': ['B0', 'B1', 'B2', 'B3'],
                    'C': ['C0', 'C1', 'C2', 'C3'],
                    'D': ['D0', 'D1', 'D2', 'D3']},
                   index=[0, 1, 2, 3])

df2 = pd.DataFrame({'A': ['A0', 'A1', 'A2', 'A3'],
                    'B': ['B4', 'B5', 'B6', 'B7'],
                    'C': ['C4', 'C5', 'C6', 'C7'],
                    'D': ['D4', 'D5', 'D6', 'D7']},
                   index=[0, 1, 2, 3])

df3 = pd.DataFrame({'A': ['A8', 'A9', 'A10', 'A11'],
                    'B': ['B8', 'B9', 'B10', 'B11'],
                    'C': ['C8', 'C9', 'C10', 'C11'],
                    'D': ['D8', 'D9', 'D10', 'D11']},
                   index=[0, 1, 2, 3])
```

```python
df1
```

|   | A  | B  | C  | D  |
| - | -- | -- | -- | -- |
| 0 | A0 | B0 | C0 | D0 |
| 1 | A1 | B1 | C1 | D1 |
| 2 | A2 | B2 | C2 | D2 |
| 3 | A3 | B3 | C3 | D3 |

\<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24" width="24px">

```
  <script>
    const buttonEl =
      document.querySelector('#df-ad0a3ccf-a3a8-4c47-9a13-bbea84e4f74b button.colab-df-convert');
    buttonEl.style.display =
      google.colab.kernel.accessAllowed ? 'block' : 'none';

    async function convertToInteractive(key) {
      const element = document.querySelector('#df-ad0a3ccf-a3a8-4c47-9a13-bbea84e4f74b');
      const dataTable =
        await google.colab.kernel.invokeFunction('convertToInteractive',
                                                 [key], {});
      if (!dataTable) return;

      const docLinkHtml = 'Like what you see? Visit the ' +
        '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
        + ' to learn more about interactive tables.';
      element.innerHTML = '';
      dataTable['output_type'] = 'display_data';
      await google.colab.output.renderOutput(dataTable, element);
      const docLink = document.createElement('div');
      docLink.innerHTML = docLinkHtml;
      element.appendChild(docLink);
    }
  </script>
</div>
```

```python
df2
```

|   | A  | B  | C  | D  |
| - | -- | -- | -- | -- |
| 0 | A0 | B4 | C4 | D4 |
| 1 | A1 | B5 | C5 | D5 |
| 2 | A2 | B6 | C6 | D6 |
| 3 | A3 | B7 | C7 | D7 |

\<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24" width="24px">

```
  <script>
    const buttonEl =
      document.querySelector('#df-e69f9242-bd72-4cda-9987-20da6249654e button.colab-df-convert');
    buttonEl.style.display =
      google.colab.kernel.accessAllowed ? 'block' : 'none';

    async function convertToInteractive(key) {
      const element = document.querySelector('#df-e69f9242-bd72-4cda-9987-20da6249654e');
      const dataTable =
        await google.colab.kernel.invokeFunction('convertToInteractive',
                                                 [key], {});
      if (!dataTable) return;

      const docLinkHtml = 'Like what you see? Visit the ' +
        '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
        + ' to learn more about interactive tables.';
      element.innerHTML = '';
      dataTable['output_type'] = 'display_data';
      await google.colab.output.renderOutput(dataTable, element);
      const docLink = document.createElement('div');
      docLink.innerHTML = docLinkHtml;
      element.appendChild(docLink);
    }
  </script>
</div>
```

```python
df3
```

|   | A   | B   | C   | D   |
| - | --- | --- | --- | --- |
| 0 | A8  | B8  | C8  | D8  |
| 1 | A9  | B9  | C9  | D9  |
| 2 | A10 | B10 | C10 | D10 |
| 3 | A11 | B11 | C11 | D11 |

\<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24" width="24px">

```
  <script>
    const buttonEl =
      document.querySelector('#df-d0ca26d9-c280-4e36-8aa6-b894829a2a72 button.colab-df-convert');
    buttonEl.style.display =
      google.colab.kernel.accessAllowed ? 'block' : 'none';

    async function convertToInteractive(key) {
      const element = document.querySelector('#df-d0ca26d9-c280-4e36-8aa6-b894829a2a72');
      const dataTable =
        await google.colab.kernel.invokeFunction('convertToInteractive',
                                                 [key], {});
      if (!dataTable) return;

      const docLinkHtml = 'Like what you see? Visit the ' +
        '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
        + ' to learn more about interactive tables.';
      element.innerHTML = '';
      dataTable['output_type'] = 'display_data';
      await google.colab.output.renderOutput(dataTable, element);
      const docLink = document.createElement('div');
      docLink.innerHTML = docLinkHtml;
      element.appendChild(docLink);
    }
  </script>
</div>
```

```python
# SQL과 같이 join operation을 사용할 수 있다.
pd.merge(df1, df2, on="A", how="outer")
```

|   | A  | B\_x | C\_x | D\_x | B\_y | C\_y | D\_y |
| - | -- | ---- | ---- | ---- | ---- | ---- | ---- |
| 0 | A0 | B0   | C0   | D0   | NaN  | NaN  | NaN  |
| 1 | A1 | B1   | C1   | D1   | NaN  | NaN  | NaN  |
| 2 | A2 | B2   | C2   | D2   | NaN  | NaN  | NaN  |
| 3 | A3 | B3   | C3   | D3   | NaN  | NaN  | NaN  |
| 4 | A4 | NaN  | NaN  | NaN  | B4   | C4   | D4   |
| 5 | A5 | NaN  | NaN  | NaN  | B5   | C5   | D5   |
| 6 | A6 | NaN  | NaN  | NaN  | B6   | C6   | D6   |
| 7 | A7 | NaN  | NaN  | NaN  | B7   | C7   | D7   |

\<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24" width="24px">

```
  <script>
    const buttonEl =
      document.querySelector('#df-d7740735-36ce-482f-b937-ad47c05330e8 button.colab-df-convert');
    buttonEl.style.display =
      google.colab.kernel.accessAllowed ? 'block' : 'none';

    async function convertToInteractive(key) {
      const element = document.querySelector('#df-d7740735-36ce-482f-b937-ad47c05330e8');
      const dataTable =
        await google.colab.kernel.invokeFunction('convertToInteractive',
                                                 [key], {});
      if (!dataTable) return;

      const docLinkHtml = 'Like what you see? Visit the ' +
        '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
        + ' to learn more about interactive tables.';
      element.innerHTML = '';
      dataTable['output_type'] = 'display_data';
      await google.colab.output.renderOutput(dataTable, element);
      const docLink = document.createElement('div');
      docLink.innerHTML = docLinkHtml;
      element.appendChild(docLink);
    }
  </script>
</div>
```

```python
# left join
#pd.merge(df2, df3, on="A", how="left")
pd.merge(df1, df2, on="A", how="left")
```

|   | A  | B\_x | C\_x | D\_x | B\_y | C\_y | D\_y |
| - | -- | ---- | ---- | ---- | ---- | ---- | ---- |
| 0 | A0 | B0   | C0   | D0   | B4   | C4   | D4   |
| 1 | A1 | B1   | C1   | D1   | B5   | C5   | D5   |
| 2 | A2 | B2   | C2   | D2   | B6   | C6   | D6   |
| 3 | A3 | B3   | C3   | D3   | B7   | C7   | D7   |

\<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24" width="24px">

```
  <script>
    const buttonEl =
      document.querySelector('#df-99af5234-d5f7-476f-9aa7-08d456e4c5e8 button.colab-df-convert');
    buttonEl.style.display =
      google.colab.kernel.accessAllowed ? 'block' : 'none';

    async function convertToInteractive(key) {
      const element = document.querySelector('#df-99af5234-d5f7-476f-9aa7-08d456e4c5e8');
      const dataTable =
        await google.colab.kernel.invokeFunction('convertToInteractive',
                                                 [key], {});
      if (!dataTable) return;

      const docLinkHtml = 'Like what you see? Visit the ' +
        '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
        + ' to learn more about interactive tables.';
      element.innerHTML = '';
      dataTable['output_type'] = 'display_data';
      await google.colab.output.renderOutput(dataTable, element);
      const docLink = document.createElement('div');
      docLink.innerHTML = docLinkHtml;
      element.appendChild(docLink);
    }
  </script>
</div>
```

```python
# 그냥 합치기 (concatenation)
pd.concat([df1, df2, df3], axis=0).reset_index(drop=True)
```

|    | A   | B   | C   | D   |
| -- | --- | --- | --- | --- |
| 0  | A0  | B0  | C0  | D0  |
| 1  | A1  | B1  | C1  | D1  |
| 2  | A2  | B2  | C2  | D2  |
| 3  | A3  | B3  | C3  | D3  |
| 4  | A0  | B4  | C4  | D4  |
| 5  | A1  | B5  | C5  | D5  |
| 6  | A2  | B6  | C6  | D6  |
| 7  | A3  | B7  | C7  | D7  |
| 8  | A8  | B8  | C8  | D8  |
| 9  | A9  | B9  | C9  | D9  |
| 10 | A10 | B10 | C10 | D10 |
| 11 | A11 | B11 | C11 | D11 |

\<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24" width="24px">

```
  <script>
    const buttonEl =
      document.querySelector('#df-c915fd95-aaa7-4c4c-9379-3e71636d10a2 button.colab-df-convert');
    buttonEl.style.display =
      google.colab.kernel.accessAllowed ? 'block' : 'none';

    async function convertToInteractive(key) {
      const element = document.querySelector('#df-c915fd95-aaa7-4c4c-9379-3e71636d10a2');
      const dataTable =
        await google.colab.kernel.invokeFunction('convertToInteractive',
                                                 [key], {});
      if (!dataTable) return;

      const docLinkHtml = 'Like what you see? Visit the ' +
        '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
        + ' to learn more about interactive tables.';
      element.innerHTML = '';
      dataTable['output_type'] = 'display_data';
      await google.colab.output.renderOutput(dataTable, element);
      const docLink = document.createElement('div');
      docLink.innerHTML = docLinkHtml;
      element.appendChild(docLink);
    }
  </script>
</div>
```

## 5. DataFrame으로 데이터 불러오기

Source : https://www.kaggle.com/c/titanic/data

```python
from google.colab import drive
drive.mount('/content/drive')
```

```
Mounted at /content/drive
```

```python
# train.csv 파일 불러오기
titanic = pd.read_csv("/content/drive/MyDrive/Colab Notebooks/data/titanic/train.csv")
titanic
```

|     | PassengerId | Survived | Pclass | Name                                              | Sex    | Age  | SibSp | Parch | Ticket           | Fare    | Cabin | Embarked |
| --- | ----------- | -------- | ------ | ------------------------------------------------- | ------ | ---- | ----- | ----- | ---------------- | ------- | ----- | -------- |
| 0   | 1           | 0        | 3      | Braund, Mr. Owen Harris                           | male   | 22.0 | 1     | 0     | A/5 21171        | 7.2500  | NaN   | S        |
| 1   | 2           | 1        | 1      | Cumings, Mrs. John Bradley (Florence Briggs Th... | female | 38.0 | 1     | 0     | PC 17599         | 71.2833 | C85   | C        |
| 2   | 3           | 1        | 3      | Heikkinen, Miss. Laina                            | female | 26.0 | 0     | 0     | STON/O2. 3101282 | 7.9250  | NaN   | S        |
| 3   | 4           | 1        | 1      | Futrelle, Mrs. Jacques Heath (Lily May Peel)      | female | 35.0 | 1     | 0     | 113803           | 53.1000 | C123  | S        |
| 4   | 5           | 0        | 3      | Allen, Mr. William Henry                          | male   | 35.0 | 0     | 0     | 373450           | 8.0500  | NaN   | S        |
| ... | ...         | ...      | ...    | ...                                               | ...    | ...  | ...   | ...   | ...              | ...     | ...   | ...      |
| 886 | 887         | 0        | 2      | Montvila, Rev. Juozas                             | male   | 27.0 | 0     | 0     | 211536           | 13.0000 | NaN   | S        |
| 887 | 888         | 1        | 1      | Graham, Miss. Margaret Edith                      | female | 19.0 | 0     | 0     | 112053           | 30.0000 | B42   | S        |
| 888 | 889         | 0        | 3      | Johnston, Miss. Catherine Helen "Carrie"          | female | NaN  | 1     | 2     | W./C. 6607       | 23.4500 | NaN   | S        |
| 889 | 890         | 1        | 1      | Behr, Mr. Karl Howell                             | male   | 26.0 | 0     | 0     | 111369           | 30.0000 | C148  | C        |
| 890 | 891         | 0        | 3      | Dooley, Mr. Patrick                               | male   | 32.0 | 0     | 0     | 370376           | 7.7500  | NaN   | Q        |

891 rows × 12 columns

\<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24" width="24px">

```
  <script>
    const buttonEl =
      document.querySelector('#df-8b370f61-8e1b-421a-a6ef-65be06fe9fec button.colab-df-convert');
    buttonEl.style.display =
      google.colab.kernel.accessAllowed ? 'block' : 'none';

    async function convertToInteractive(key) {
      const element = document.querySelector('#df-8b370f61-8e1b-421a-a6ef-65be06fe9fec');
      const dataTable =
        await google.colab.kernel.invokeFunction('convertToInteractive',
                                                 [key], {});
      if (!dataTable) return;

      const docLinkHtml = 'Like what you see? Visit the ' +
        '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
        + ' to learn more about interactive tables.';
      element.innerHTML = '';
      dataTable['output_type'] = 'display_data';
      await google.colab.output.renderOutput(dataTable, element);
      const docLink = document.createElement('div');
      docLink.innerHTML = docLinkHtml;
      element.appendChild(docLink);
    }
  </script>
</div>
```

```python
titanic.info()
```

```
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 891 entries, 0 to 890
Data columns (total 12 columns):
 #   Column       Non-Null Count  Dtype  
---  ------       --------------  -----  
 0   PassengerId  891 non-null    int64  
 1   Survived     891 non-null    int64  
 2   Pclass       891 non-null    int64  
 3   Name         891 non-null    object 
 4   Sex          891 non-null    object 
 5   Age          714 non-null    float64
 6   SibSp        891 non-null    int64  
 7   Parch        891 non-null    int64  
 8   Ticket       891 non-null    object 
 9   Fare         891 non-null    float64
 10  Cabin        204 non-null    object 
 11  Embarked     889 non-null    object 
dtypes: float64(2), int64(5), object(5)
memory usage: 83.7+ KB
```

```python
titanic.describe()
```

|       | PassengerId | Survived   | Pclass     | Age        | SibSp      | Parch      | Fare       |
| ----- | ----------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- |
| count | 891.000000  | 891.000000 | 891.000000 | 714.000000 | 891.000000 | 891.000000 | 891.000000 |
| mean  | 446.000000  | 0.383838   | 2.308642   | 29.699118  | 0.523008   | 0.381594   | 32.204208  |
| std   | 257.353842  | 0.486592   | 0.836071   | 14.526497  | 1.102743   | 0.806057   | 49.693429  |
| min   | 1.000000    | 0.000000   | 1.000000   | 0.420000   | 0.000000   | 0.000000   | 0.000000   |
| 25%   | 223.500000  | 0.000000   | 2.000000   | 20.125000  | 0.000000   | 0.000000   | 7.910400   |
| 50%   | 446.000000  | 0.000000   | 3.000000   | 28.000000  | 0.000000   | 0.000000   | 14.454200  |
| 75%   | 668.500000  | 1.000000   | 3.000000   | 38.000000  | 1.000000   | 0.000000   | 31.000000  |
| max   | 891.000000  | 1.000000   | 3.000000   | 80.000000  | 8.000000   | 6.000000   | 512.329200 |

\<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24" width="24px">

```
  <script>
    const buttonEl =
      document.querySelector('#df-d3f859ec-3ff7-4ce3-a056-273f539d813a button.colab-df-convert');
    buttonEl.style.display =
      google.colab.kernel.accessAllowed ? 'block' : 'none';

    async function convertToInteractive(key) {
      const element = document.querySelector('#df-d3f859ec-3ff7-4ce3-a056-273f539d813a');
      const dataTable =
        await google.colab.kernel.invokeFunction('convertToInteractive',
                                                 [key], {});
      if (!dataTable) return;

      const docLinkHtml = 'Like what you see? Visit the ' +
        '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
        + ' to learn more about interactive tables.';
      element.innerHTML = '';
      dataTable['output_type'] = 'display_data';
      await google.colab.output.renderOutput(dataTable, element);
      const docLink = document.createElement('div');
      docLink.innerHTML = docLinkHtml;
      element.appendChild(docLink);
    }
  </script>
</div>
```

```python
#titanic["Pclass"].value_counts()
#titanic[titanic.Age.isnull()]
# titanic.loc[0:100, "Name"]
# titanic.loc[0:100, "PassengerId":"Age"]
# titanic.iloc[100:200, :3]
#titanic[titanic.Age > 30]["Fare"]
titanic.loc[titanic.Age > 30, "Fare"].mean()
```

```
42.35290983606555
```

## 6. Pivot Table을 이용하여 데이터 살펴보기

* pivot table이란 기존 테이블 구조를 특정 column을 기준으로 재구조화한 테이블을 말합니다.
* 특정 column을 기준으로 pivot하기 때문에, 어떤 column에 어떤 연산을 하느냐에 따라서 만들어지는 결과가 바뀝니다.
* 주로 어떤 column을 기준으로 데이터를 해석하고 싶을 때 사용합니다.

```python
# 성별을 기준으로 생존률 파악 --> Mean vs Sum
pd.pivot_table(data=titanic, index=["Sex"], values=["Survived"], aggfunc=["sum", "mean", "count"])
```

|        | sum      | mean     | count    |
| ------ | -------- | -------- | -------- |
|        | Survived | Survived | Survived |
| Sex    |          |          |          |
| female | 233      | 0.742038 | 314      |
| male   | 109      | 0.188908 | 577      |

\<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24" width="24px">

```
  <script>
    const buttonEl =
      document.querySelector('#df-48395dbc-6b4d-4d1e-b8e2-f8ca4f1e83bb button.colab-df-convert');
    buttonEl.style.display =
      google.colab.kernel.accessAllowed ? 'block' : 'none';

    async function convertToInteractive(key) {
      const element = document.querySelector('#df-48395dbc-6b4d-4d1e-b8e2-f8ca4f1e83bb');
      const dataTable =
        await google.colab.kernel.invokeFunction('convertToInteractive',
                                                 [key], {});
      if (!dataTable) return;

      const docLinkHtml = 'Like what you see? Visit the ' +
        '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
        + ' to learn more about interactive tables.';
      element.innerHTML = '';
      dataTable['output_type'] = 'display_data';
      await google.colab.output.renderOutput(dataTable, element);
      const docLink = document.createElement('div');
      docLink.innerHTML = docLinkHtml;
      element.appendChild(docLink);
    }
  </script>
</div>
```

```python
# 사회 계급을 기준으로 생존률 파악
pd.pivot_table(data=titanic, index=["Pclass", "Sex"], values=["Survived"], aggfunc=["mean", "count"])
```

|        |          | mean     | count    |
| ------ | -------- | -------- | -------- |
|        |          | Survived | Survived |
| Pclass | Sex      |          |          |
| 1      | female   | 0.968085 | 94       |
| male   | 0.368852 | 122      |          |
| 2      | female   | 0.921053 | 76       |
| male   | 0.157407 | 108      |          |
| 3      | female   | 0.500000 | 144      |
| male   | 0.135447 | 347      |          |

\<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24" width="24px">

```
  <script>
    const buttonEl =
      document.querySelector('#df-e3f54c07-fab1-4727-9d38-0082ecddd78f button.colab-df-convert');
    buttonEl.style.display =
      google.colab.kernel.accessAllowed ? 'block' : 'none';

    async function convertToInteractive(key) {
      const element = document.querySelector('#df-e3f54c07-fab1-4727-9d38-0082ecddd78f');
      const dataTable =
        await google.colab.kernel.invokeFunction('convertToInteractive',
                                                 [key], {});
      if (!dataTable) return;

      const docLinkHtml = 'Like what you see? Visit the ' +
        '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
        + ' to learn more about interactive tables.';
      element.innerHTML = '';
      dataTable['output_type'] = 'display_data';
      await google.colab.output.renderOutput(dataTable, element);
      const docLink = document.createElement('div');
      docLink.innerHTML = docLinkHtml;
      element.appendChild(docLink);
    }
  </script>
</div>
```
