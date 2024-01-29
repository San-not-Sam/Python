# Page

## 파이썬 프로그래밍

​

### 9. 함수 <a href="#id-9" id="id-9"></a>

#### 1) 정의 <a href="#id-1" id="id-1"></a>

* 한 가지의 기능을 하는 코드 묶음으로, input을 받아서 처리하고 output을 돌려주는 코드.
* 함수(function)는 기능(function)을 의미합니다.
* 함수의 input을 = parameter(또는 = argument)라고 합니다.
* 함수는 input을 받아서 주어진 기능대로 처리한 뒤, output을 return합니다.
* 정의한 함수를 사용하는 것을 function call이라고 합니다.

#### 2) 특징 <a href="#id-2" id="id-2"></a>

def function1(a, b):something = ...\<statement>\<statement>......return somethingresult = function1(3, 5)

* 함수를 호출하면 정의한 code block내의 코드를 실행합니다.
* 함수의 input인 parameter에 어떤 값이 들어오고, 어떤 결과를 return할지 잘 정해야합니 다. (parameterization)
* 함수를 사용하면 코드를 구조화하기 쉽습니다!
* 기존 코드를 설계할 때부터 함수로 작성하는 경우도 있고, 우선 기능을 하는 코드를 만든 다음에 재구조화를 하는 경우도 있습니다.
* 이러한 작업을 Refactoring 이라고 합니다.
* 구조화된 코드는 코드의 재사용성(Reusability) 가 향상됩니다. → 코드의 생산성 향상!

​

* Key Points

1. 1.함수를 정의해서 사용할 때도, : 사용이 중요합니다.
2. 2.함수를 사용하는 이유는 코드의 재사용성을 높이기 위해서 사용합니다.
3. 3.함수들의 구조를 잘 짜면 유지보수하기 쉬운 좋은 코드를 만들 수 있습니다.

​

### 10. I/O  <a href="#id-10.-i-o" id="id-10.-i-o"></a>

1. 1.I/O : Input/Output의 약자로 컴퓨터가 데이터를 입력받고 출력하는 모든 작업을 의미합니다.

![](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FvnagCf7GnrTdHN7L0qZ8%2Fuploads%2FHfWbrpc4dVylE5x2qwhh%2Fimage.png?alt=media\&token=581307a7-693c-4fdc-a857-270a51eb7d8c)Source : https://en.wikiversity.org/wiki/Hardware#/media/File:Computer1.png

1. 1.프로그램 입장에서 들어오는 모든 데이터를 Input, 나가는 모든 데이터를 Output이라고 합니다
2. 2..메인 메모리 입장에서 생각하는 들어오고 나가는 모든 데이터에 대해서 I/O 처리라고 부릅니다. (단, CPU와의 소통은 제외)
3. 3.사용자로부터 키보드로 입력받는 것을 `stdin` 이라고 하며, 사용자에게 다시 결과를 모니터로보여주는 것을 `stdout` 이라고 합니다.

\# stdin/stdout examplea = input("숫자를 하나 입력하세요 : ") # input 함수는 뭐든 str로 받아옵니다.print(a)>>> 숫자를 하나 입력하세요 : 5>>> '5'프로그램은 메인 메모리 상에서 존재하기 때문에, 스토리지로부터 파일을 불러오는 것도 input이고, 프로그램의 결과를 스토리지에 저장하는 것도 output입니다.스토리지와 프로그램 사이의 I/O를 file I/O 라고 합니다.# filein/fileout examplewith open("data/a.txt", 'r') as f:data = f.readlines()파이썬에서는 with open() 함수를 통해서 텍스트 파일을 쉽게 불러올 수 있습니다. )‘r’, ‘w’, ‘a’ 등의 mode를 바꿔서 파일을 다른 옵션으로 열 수 있다. (read, write, append 순다른 타입의 파일을 열기 위해선 다른 라이브러리들이 필요합니다.e.g. csv, excel 파일을 열기 위해 pandas, csv, openpyxl 라이브러리를 사용할 수 있다.e.g. png, jpg 파일을 열기 위해 PIL, opencv 라이브러리를 사용할 수 있다.e.g. pk, pkl 파일을 열기 위해 pickle 라이브러리를 사용할 수 있다. (파일 타입이 binary라서, ‘rb’를 써야함)I/O가 데이터 처리를 할 때 가장 느린 파트이기 때문에 신경써줘야 합니다. (performance bottleneck)11. OOP정의Object-Oriented Programming의 약자로 객체(Object)를 기반으로 프로그 램을 만드는 방법론입니다.Source : https://velog.io/@gil0127/Object-Oriented-Programming-in-Javascript실제 세상을 표현하고 있는, 여러가지 개념들을 프로그램으로 옮겨서 구현할 수 있 기 위한 컨셉의 프로그래밍 패러다임(paradigm)입니다. → 개념의 추상화(abstraction)객체(object)라는 개념은 실제 사물 하나하나를 의미할 수 있고, 이러한 사물들이 공유하는 속성을 정의한 것을 클래스(Class)라고 합니다.기존 방식은 데이터(변수, variable)와 데이터를 처리하는 기능(함수, function)이 독립적이 었지만, OOP는 이를 하나의 개념(Class)로 묶어서 생각하기 때문에 그 객체가 처리되는 기능을 자연스럽게 정의할 수 있습니다.Class에는 Class를 기술하는 정보를 나타내는 변수인 Class variable 과 Class의 특징을 설명하는 기능인 Class method 를 포함합니다.추상적인 개념 Class를 실제로 사용하려면 하나 하나의 개별 사물로 만들어야 하는데, 이를 개별 사물인 객체(object)라고 합니다. → 개념의 구체화(instantiation)장점클래스 구조를 잘 설계하면 라이브러리 형태로 재사용이 쉬워진다. → 생산성 향상2. 일상 생활에 존재하는 개념을 그대로 프로그램에 구현 가능하다. → 자연적인 모델링3. 클래스의 상속의 개념 때문에, 프로그래밍 자체의 재사용성이 극대화된다. → 재사용성 증가4. OOP를 이용하여 개발을 하게되면, 다른 기능을 수정하더라도 클래스가 서로 다르게 구현 되어 있어 다른 기능에 끼치는 영향이 매우 적어질 수 있다. → 유지보수 용이성 증가1) Inheritance(상속)Source : https://masterdotnet.com/csharptutorial/csharpinheritance/클래스는 개념의 추상화이기 때문에, 해당 개념을 계승하는 하위 개념을 만들 수 있습니다.상위/하위 개념이 상대적으로 존재하며, 상속하는 클래스는 superclass , 상속받는 클래스는 subclass 라고 얘기합니다.subclass는 superclass의 모든 개념을 이어받기 때문에, class variable, class method 도 그대로 이어받습니다.2) polymorphism(다형성)Source : https://codegym.cc/groups/posts/polymorphism-in-java여러 하위 클래스가 같은 class method를 상속받게 되면, 그 기능을 다르게 구현할 수 있습 니다.예를 들어 Animal 이라는 Class에 Speak()이라는 method가 있다면, 이 기능은 다른 동물 을 표현하는 subclass들마다 다르게 구현될 수 있습니다. → Dog : “Woof” , Cat : “Meow” , Cow : “Moo”이렇게 하나의 기능을 나타내는 개념이 실제 구현해서 다양한 형태로 표현 가능한 것을 Polymorphism 이라고 합니다.이러한 다형성을 구현할 수 있는 기능을 Method Overriding 이라고 합니다.3) Abstraction(추상화)Abstraction(추상화)는 Class 내부에 구현된 Class variable이나 Class method를 직접 보지 않아도 개념상으로 사용할 수 있게 하는 개념입니다.기능에 대한 명세나 변수의 의미만 확실하게 알면, 내부 구현은 살펴보지 않아도 됩니다.4) Encapsulation(은닉화)Source : https://medium.com/javarevisited/why-should-encapsulation-to-be-used-e82a81f5c47cEncapsulation은 Class variable과 Class method까지 단일 개념으로 구성되어 있어, 사 용자가 개념 구현의 혼선을 막고 심플하게 사용할 수 있게 만드는 특징을 말합니다.Encapsulation이 잘되면 사용자는 Class의 내부 구현 코드를 보지 않아도 내부 데이터와 기능을 사용하는데 아무런 문제가 없습니다.우리가 사용해왔던 모든 함수들, Data type들의 내부 구현 코드를 보지 않아도 개념적으로 이해하고 사용할 수 있는 이유도 Encapsulation이 잘되기 때문입니다.e.g. List.append()를 예로 들 수 있습니다.12. ClassOOP에서 구현하려는 개념을 추상화한 코드 템플릿.Source: https://wikidocs.net/28Class를 이용해서 구현하려는 개념을 객체(object)의 형태로 찍어낼 수 있습니다.구현하려는 대상의 특성을 Class variable로, 대상이 수행해야 하는 일을 Class method로 구현해야 합니다.Constructor(생성자)를 통해서 객체를 찍어내는 틀을 정의할 수 있습니다.# Python Class exampleclass Human(superclass): # 상속을 받고 싶을 때, 상속받을 클래스 이름을 파라미터로 지정.def \_\_init\_\_(self, name, weight): # Constructorself.name = nameself.weight = weight...def gain\_weight(self, a, b):tmp\_weight = self.weight + a\<statement>...return tmp\_weight>>> object1 = Human("Kim", 70) # class\_name() : \_\_init\_\_ method call>>> object1.name>>> "Kim">>> object1.gain\_weight(5, 7)>>> 75생성자는 init() 함수를 이용하여 구현합니다.구현되는 객체는 self 라는 자체 변수를 가집니다.self는 말 그대로 객체 자기 자신을 지칭 합니다. self 변수를 통해서 모든 객체는 자기 자신을 구분할 수 있습니다.Class method도 self 변수를 이용하여 객체를 구분합니다.self는 Class variable이기 때문에 하나의 Class내에서 통용됩니다.Class도 역시 재사용성을 고려하여 디자인되어야 합니다.Class로 구현할 때 제일 중요한 포인트는 “어떤 특성과 어떤 기능을 구현할 것인가" 입니다.ML/DL Project 실무에서의 활용.Tensorflow/Keras templatehttps://github.com/Husseinjd/keras-tensorflow-templatePytorch templatehttps://github.com/victoresque/pytorch-template![](https://avatars.githubusercontent.com/u/157803039?v=4)Last modified 6h agoON THIS PAGE9. 함수1) 정의2) 특징10. I/O11. OOP1) Inheritance(상속)2) polymorphism(다형성)3) Abstraction(추상화)4) Encapsulation(은닉화)12. Class

#### Revision history

Today[![](https://avatars.githubusercontent.com/u/157803039?v=4)Create # \[연동 test\] 여기에 옮겨질까?2m ago on GitHub](https://app.gitbook.com/o/CNGVrK9H35CNfG7bwZDc/s/vnagCf7GnrTdHN7L0qZ8/\~/diff/\~/revisions/xgsbiFJvoejIpATBUSlR/)[![](https://avatars.githubusercontent.com/u/157803039?v=4)sck0784 merged 1 change from change request #13h ago](https://app.gitbook.com/o/CNGVrK9H35CNfG7bwZDc/s/vnagCf7GnrTdHN7L0qZ8/\~/diff/\~/revisions/FKoxsdIeZWFcWL9O4MQv/)[![](https://avatars.githubusercontent.com/u/157803039?v=4)sck0784 modified the page 파이썬 프로그래밍6h ago](https://app.gitbook.com/o/CNGVrK9H35CNfG7bwZDc/s/vnagCf7GnrTdHN7L0qZ8/\~/diff/\~/revisions/bp6or7tQvDnSePtIeQGZ/)[![](https://avatars.githubusercontent.com/u/157803039?v=4)sck0784 modified the page 파이썬 프로그래밍6h ago](https://app.gitbook.com/o/CNGVrK9H35CNfG7bwZDc/s/vnagCf7GnrTdHN7L0qZ8/\~/diff/\~/revisions/5aESeJnnElqegCKyXXJi/)[![](https://avatars.githubusercontent.com/u/157803039?v=4)sck0784 modified the page 파이썬 프로그래밍 and made 1 other change6h ago](https://app.gitbook.com/o/CNGVrK9H35CNfG7bwZDc/s/vnagCf7GnrTdHN7L0qZ8/\~/diff/\~/revisions/p5hqBG0P9DZcKWMAsJl9/)[![](https://avatars.githubusercontent.com/u/157803039?v=4)sck0784 modified the page 파이썬 프로그래밍6h ago](https://app.gitbook.com/o/CNGVrK9H35CNfG7bwZDc/s/vnagCf7GnrTdHN7L0qZ8/\~/diff/\~/revisions/UuBUOlcWFmh0ZBvzWHz6/)[![](https://avatars.githubusercontent.com/u/157803039?v=4)sck0784 modified the page 파이썬 프로그래밍 and made 1 other change6h ago](https://app.gitbook.com/o/CNGVrK9H35CNfG7bwZDc/s/vnagCf7GnrTdHN7L0qZ8/\~/diff/\~/revisions/IqFELpIC32LYD12Pb2lx/)[![](https://avatars.githubusercontent.com/u/157803039?v=4)sck0784 modified the page 파이썬 프로그래밍6h ago](https://app.gitbook.com/o/CNGVrK9H35CNfG7bwZDc/s/vnagCf7GnrTdHN7L0qZ8/\~/diff/\~/revisions/u69v3ozbx5gkhu4HPwhX/)[![](https://avatars.githubusercontent.com/u/157803039?v=4)sck0784 modified the page 파이썬 프로그래밍 and made 1 other change6h ago](https://app.gitbook.com/o/CNGVrK9H35CNfG7bwZDc/s/vnagCf7GnrTdHN7L0qZ8/\~/diff/\~/revisions/5j6RNsV5P6yvSN9BUSIO/)[![](https://avatars.githubusercontent.com/u/157803039?v=4)sck0784 modified the page 파이썬 프로그래밍7h ago](https://app.gitbook.com/o/CNGVrK9H35CNfG7bwZDc/s/vnagCf7GnrTdHN7L0qZ8/\~/diff/\~/revisions/hAZeGe8hP9qDxIjLSfAJ/)Load more\
