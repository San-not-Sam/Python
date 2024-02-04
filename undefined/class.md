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

# Copy Class

* Python은 OOP 패러다임으로 구현된 언어입니다.
* Python에서 Class를 직접 구현하면서 개념을 익혀봅시다.

```python
# Notebook 이라는 사물을 클래스로 정의합니다.
class Notebook():
  def __init__(self, manufacturer, model, cpu_type, ram_size, ssd_size):
    self.manufacturer = manufacturer
    self.model = model
    self.cpu_type = cpu_type
    self.ram_size = ram_size
    self.ssd_size = ssd_size
```

```python
# 클래스의 생성자(constructor)를 불러와봅니다.
notebook = Notebook("Apple", "M1 Max", "M1 Max", 64, 2048)
notebook.model
```

```
'M1 Max'
```

* Notebook이라는 개념을 클래스로 구현하였습니다.
* Notebook에서 필요한 여러가지 기능을 함수(class method)로 구현합니다.

```python
# 클래스 내부의 함수를 구현합니다.
# 해당 노트북의 운영체제가 UNIX 계열 운영체제인지 아닌지 확인하는 Class Method를 구현합니다.

class Notebook:
  
  def __init__(self, manufacturer, model, cpu_type, ram_size, ssd_size, os):
    self.manufacturer = manufacturer
    self.model = model
    self.cpu_type = cpu_type
    self.ram_size = ram_size
    self.ssd_size = ssd_size
    self.os = os

  ## TO-DO ##
  def is_UNIX(self):
    UNIX = ["macOS", "Ubuntu", "iOS", "Android"]
    if self.os in UNIX:
      return True
    else:
      return False

nb = Notebook("Apple", "M1 Max", "M1 Max", 64, 2048, "macOS")
nb2 = Notebook("LG", "Gram 17", "Intel i7", 16, 512, "Windows")

#nb.is_UNIX()
nb2.is_UNIX()
```

```
False
```

```python
# 해당 노트북의 모델을 출력해주는 Class Method를 구현합니다.
class Notebook:
  
  def __init__(self, manufacturer, model, cpu_type, ram_size, ssd_size, os):
    self.manufacturer = manufacturer
    self.model = model
    self.cpu_type = cpu_type
    self.ram_size = ram_size
    self.ssd_size = ssd_size
    self.os = os

  ## TO-DO ##
  def is_UNIX(self):
    UNIX = ["macOS", "Ubuntu", "iOS", "Android"]
    if self.os in UNIX:
      return True
    else:
      return False

  def print_model(self):
    print(f"This Notebook is {self.model} model.")

nb = Notebook("Apple", "M1 Max", "M1 Max", 64, 2048, "macOS")
nb2 = Notebook("LG", "Gram 17", "Intel i7", 16, 512, "Windows")
nb.print_model()
nb2.print_model()
```

```
This Notebook is M1 Max model.
This Notebook is Gram 17 model.
```

## 클래스 상속 (Class inheritence)

* Notebook들은 제조사마다 다른 모델이 있습니다.
* 해당 모델들은 Notebook이지만, 모델마다 다른 특징을 가지고 있습니다.
* 노트북의 개념을 그대로 이어받아, 모델마다 다른 개념을 Class로 구현해봅시다.

```python
# notebook class를 상속받아서 새로운 MacBook class를 정의
class MacBook(Notebook):
  def __init__(self, model, release_date, display_size, cpu_type, ram_size, ssd_size, os):
    self.model = model
    self.release_date = release_date
    self.display_size = display_size
    self.cpu_type = cpu_type
    self.ram_size = ram_size
    self.ssd_size = ssd_size
    self.os = os

macbook = MacBook("Macbook Pro", "2020", "13", "Intel i5", 16, 1024, "macOS")
macbook.print_model() # print_model <- Notebook 클래스에서 상속받은 Class method.
```

```
This Notebook is Macbook Pro model.
```

```python
# notebook class를 상속받아서 새로운 Dell_Laptop class를 정의
class Dell_Laptop(Notebook):
  def __init__(self, model, series, display_size, cpu_type, ram_size, ssd_size, os="Windows 11"):
    self.model = model
    self.series = series
    self.display_size = display_size
    self.cpu_type = cpu_type
    self.ram_size = ram_size
    self.ssd_size = ssd_size
    self.os = os

dell = Dell_Laptop("XPS", 9500, 15, "Intel i7", 16, 2048, "Windows 10")
dell.print_model()
```

```
This Notebook is XPS model.
```

## Method Overriding

```python
# 각 모델마다 다르게 정보를 출력해주는 is_UNIX 함수를 재정의합니다.
# notebook class를 상속받아서 새로운 MacBook class를 정의
class MacBook(Notebook):
  def __init__(self, model, release_date, display_size, cpu_type, ram_size, ssd_size, os):
    self.model = model
    self.release_date = release_date
    self.display_size = display_size
    self.cpu_type = cpu_type
    self.ram_size = ram_size
    self.ssd_size = ssd_size
    self.os = os

  def is_UNIX(self):
    UNIX = ["Ubuntu", "iOS", "Android", "Mojave", "Catelina", "Sierra" ,"High Sierra", "Montrery"]
    if self.os in UNIX:
      return True
    else:
      return False

# notebook class를 상속받아서 새로운 Dell_Laptop class를 정의
class Dell_Laptop(Notebook):
  def __init__(self, model, series, display_size, cpu_type, ram_size, ssd_size, os="Windows 11"):
    self.model = model
    self.series = series
    self.display_size = display_size
    self.cpu_type = cpu_type
    self.ram_size = ram_size
    self.ssd_size = ssd_size
    self.os = os

  def print_model(self):
    print(f"This notebook is {self.model} {self.series} {self.display_size} model.")


macbook = MacBook("Macbook Pro", "2020", "13", "Intel i5", 16, 1024, "Mojave")
print(macbook.is_UNIX())

dell = Dell_Laptop("XPS", 9500, 15, "Intel i7", 16, 2048, "Mojave")
#dell.print_model()
print(dell.is_UNIX())
```

```
True
False
```
