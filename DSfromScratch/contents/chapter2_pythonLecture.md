# 파이썬 속성 강좌

## The Zen of Python

파이썬 인터프리터를 실행하고 import this를 입력하면 바로 출력되는데, 그 중에서 가장 많은 논란이 이는 부분은 다음과 같다.  
> 무엇을 하든 그것을 할 수 있는 하나의, 가급적이면 단 하나의 당연한 방법이 존재해야 한다.


이렇게 '당연한' 방식으로 쓰여진 코드를 일반적으로 '파이썬스럽다(Pythonic)'고 한다.  
이 책은 파이썬에 관한 책은 아니지만 앞으로 파이썬 스러운 코드와 그렇지 않은 코드를 비교할 것이고,  
대부분의 경우 파이썬스러운 해법을 더 선호할 것이다.  

### 들여쓰기
많은 프로그래밍 언어는 코드의 단락을 구분하는 데 중괄호(curly braces, {})를 사용한다.  
하지만 파이썬은 들여쓰기를 사용한다. 보통 클래스, 함수 선언 뒤쪽에 붙은 :이나 흐름 제어문 뒤쪽에 붙은 :부터 들여쓰기를 구분한다.  


이 덕분에 파이썬의 가독성은 아주 높아졌지만, 코드 형태에 상당히 조심해야 한다.  
공백문자는 소괄호와 대괄호 안에서는 무시되기 때문에 긴 계산을 하거나 코드의 가독성을 높이는 데 유용하게 쓸 수 있다.  
자주 사용하지는 않지만, 역슬래시(backslash)를 사용하면 코드가 다음 줄로 이어지는 것을 명시할 수 있다.  


들여쓰기를 사용함으로써 생기는 한 가지 문제는 코드를 복사해서 파이썬 셸에 붙여넣을 때 어려움을 겪을 수 있다는 것이다.  
한편 IPython에는 %pasteㄹ라는 특별한 명령이 있어서 공백문자뿐만 아니라 클립보드에 있는 무엇이든 제대로 붙여넣을 수 있다.  
이것 하나만으로도 IPython을 쓸 이유는 충분하다.  

### 모듈
파이썬에 기본적으로 포함된 몇몇 기능과 각자 다운 받은 제3자 패키지(3rd party packages)에 포함된 기능들은  
파이썬을 실행시킬 때 함께 실행되지 않는다. 이 기능을 사용하기 위해서는 모듈을 불러오는 import를 사용해야 한다.  
또한 as키워드를 사용해서 코드에서 사용할 모듈의 별칭을 사용할 수 있다.  
그리고 모듈 하나에서 몇몇 특정 기능만 필요하다면, 전체 모듈을 불러오지 않고 해당기능만 명시해서 불러올 수 있다.  


가장 안좋은 습관 중 하나는 모듈의 기능들을 통째로 불러와서 기존의 변수들을 덮어쓰는 것이다.  
```{.py}
match = 10
from re import * # 윽! re에도 match라는 함수가 존재한다.
print match
```
그러나 아직은 우리에게 이런 습관이 없을 테니 크게 걱정하지 않아도 된다.  


### 함수

일반적인 기명 함수를 정의하는 방법은 다들 알고 있을테니 넘어간다. 대신 간단한 람다함수를 정의하는 법을 알려주겠다.  

```{.py}
y = apply_to_one(lambda x: x + 4) # 5
```
대부분의 사람들은 그냥 def를 사용하라고 얘기하겠지만, 변수에 람다 함수를 할당할 수도 있다.  
하지만 변수에 람다함수를 할당하는 것은 이방법은 특별한 이유가 없으면 피하는 것이 좋다.  
콜백 같은 것을 사용할 것이 아니면 별로 이득이 없기 때문이다.  


함수의 인자에는 기본값을 할당할 수 있는데, 기본값 외의 값을 전달하고 싶을 때는 직접 명시해주면 된다.  

```{.py}
def my_print(message="my default message"):
	print message

my_print("hello") # "hello"를 출력
my_print() # "my default message"를 출력
```
가끔식 인자의 이름을 명시해주면 편리하다.  
반드시 선언한 순서에 맞추지 않아도 알아서 처리해주기 때문이다.  

### 문자열

파이썬은 몇몇 특수문자를 인코딩할 때 역슬래시를 사용한다.  

```{.py}
tab_string = "\t" # 탭(tab)을 의미하는 문자열
len(tab_string)   # 1
```
만약 역슬래시를 역슬래시로 보이는 문자로 사용하고 싶다면(특히 윈도우 디렉터리 이름이나 정규표현식에서 사용하고 싶을 때)  
문자열 앞에 r을 붙여 raw string(가공되지 않은 문자열)이라고 명시하면 된다.  

```{.py}
tab_string = "\t" # 탭(tab)을 의미하는 문자열
len(tab_string)   # 2
```
### 예외 처리

코드가 뭔가 잘못되었을 때 파이썬은 예외(Exception)가 발생했음을 알려준다.  
예외를 제대로 처리해 주지 않으면 프로그램이 죽는데, 이를 방지하기 위해 사용할 수 있는 것이 try와 except이다.  

```{.py}
try:
	print 0/0
except ZeroDivisionError:
	print "cannot divide by zero"
```

많은 프로그래밍 언어에서 예외 처리는 나쁜 것이라고 받아들여지지만,  
파이썬에서는 코드를 깔끔하게 작성하기 위해서라면 얼마든지 사용되며 앞으로 우리도 사용할 것이다.  

### list

list는 익히 잘 알고있을 파이썬의 내장 자료구조로 생각한다.  
여기서 중요하게 짚고 넘어갈 것은 바로 list comprehension이다.  

```{.py}
# [0, 1, 2, ..., 9] 형태의 리스트
x = range(10)

# 결과는 9, list의 마지막 항목을 가장 파이썬스럽게 불러오는 방법
nine = x[-1]
# 결과는 8, 뒤에서 두 번째 항목을 가장 파이썬스럽게 불러오는 방법
eight = x[-2]
# x는 이제 [-1, 1, 2, 3, ..., 9]
x[0] = -1
```

또한 대괄호를 사용해서 list를 나눌 수도 있다.  
참고로 (시작 인덱스, 없으면 0부터):(끝 인덱스, 없으면 맨 마지막 인덱스도 포함하여 이터레이팅 + 참고로 끝 인덱스는 포함 X)이다.  

```{.py}
# [-1, 1, 2]
first_three = x[:3]
# [3, 4, ..., 9]
three_to_end = x[3:]
# [1, 2, 3, 4]
one_to_four = x[1:5]
# [1, 2, 3, ..., 8]
without_first_and_last = x[1:-1]
# [1, 2, 3, 4, 5, ..., 9]
copy_of_x = x[:]
```

파이썬에서 제공하는 in 연산자를 사용하면 list안에서 항목의 존재 여부를 확인할 수 있다.  
이 방법은 list의 항목을 하나씩 모두 확인해 보기 떄문에 list의 크기가 작을 때만 사용하도록 하자.

```{.py}
```

list를 연결시키는 방법은 매우 간단하다. + 연산자를 사용하거나, extend()를 사용하면 된다.

```{.py}
```
또는 list에 항목을 하나씩 추가하는 방법을 많이 사용한다.  
만약 list안에 몇 개의 항목이 존재하는지 알고 있다면 손쉽게 list를 풀 수(unpack)도 있다.  
하지만 양쪽 항목의 개수가 다르다면 ValueError가 발생한다. 보통 버릴 항목은 밑줄로 표시한다.  

```{.py}
# append()
x = [1, 2, 3]
x.append(0)
y = x[-1] # 결과는 0
z = len(x)# 결과는 4

# unpack
# 이제 x는 1, y는 2
x, y = [1, 2]
# 이제 y == 2이고 첫 번째 항목은 신경 쓰지 않는다.
_, y = [1, 2]
```

### tuple
tuple은 변경할 수 없는 list이다. list에서 수정을 제외한 모든 기능을 tuple에 적용할 수 있다.  
참고로 함수에서 여러값을 반환할 때 tuple을 사용하면 편리하다.  
그리고 tuple과 list는 다중 할당(multiple assginment)을 지원한다.

```{.py}
# tuple의 활용
def sum_and_product(x, y)
	return (x + y), (x*y)
sp = sum_add_product(2, 3) # 결과는 5, 6
s, p = sum_add_product(5, 10) # s는 15, p는 50

# 다중 할당 활용
x, y = 1, 2
x, y = y, x
```

### dict

### defaultdict

### Counter

### set

### 흐름 제어

### True와 False

다른 곳에도 적어놓았지만, True와 False는 bool타입이다. 그런데 bool타입은 int타입을 상속하고 있다는 점을 기억하라.


## 기본기에서 한 걸음 나아가기

### 정렬

### List Comprehension

### Generator와 iterator

### 난수 생성

데이터 과학을 하다 보면 난수(random number)를 생성해야 할 때가 자주있다. 이때는 random모듈을 사용할 수 있다.  
이 때는 random모듈을 사용할 수 있다.  

```{.py}
import random

four_uniform_randoms = [random.random() for _ in range(4)]

# random.random()은 float타입의 
# 0과 1사이의 난수를 생성한다.
# 앞으로 가장 자주 사용할 함수이다.
```

만약 동일한 난수를 계속 사용하고 싶다면 random.seed를 통해 매번 고정된 난수를 생성하면 된다.  

```{.py}
# 여기서 궁금한게 하나 생겼다. print는 파이썬의 연산자인가?

random.seed(10) # seed를 10으로 설정
print random.random() # 0.57이 나왔다고 하자.
random.seed(10) # seed를 다시 10으로 설정해도 
print random.random() # 역시나 0.57이 출력된다.
```

인자가 1개 혹은 2개인 random.randrange 메서드를 사용하면 range()에 대항하는 구간 안에서 난수를 생성할 수 있다.  

```{.py}
random.randrange(10) # range(10) = [0, 1, 2, 3, ..., 9]에서 난수 생성
random.randrange(3, 6) # [3, 4, 5]에서 난수를 생성
```
random 모듈에는 가끔씩 사용하지만 유용한 여러 함수가 존재한다.  
random.shuffle은 list의 항목을 임의 순서로 재정렬해 준다.

```{.py}
up_to_ten = range(10)
random.shuffle(up_to_ten)
print up_to_ten

# 예를 들어 [2, 5, 1, 9, 7, 3, 8, 6, 4, 0] (결과는 제각각일 것이다.)
```

random.choice 메서드를 사용하면 list에서 임의의 항목을 하나 선택할 수 있다.  

```{.py}
my_best_friend = random.choice(["Alice", "bob", "Charlie"]) # 뭐가 되었든 셋중에 하나가 나올 것이다.
```

그리고 random.sample을 사용하면 list에서 중복이 허용되지 않는 임의의 표본 list를 만들 수 있다.  

```{.py}
lottery_numbers = range(60)
winning_numbers = random.sample(lottery_numbers, 6) # 예를 들어, [16, 36, 10, 6, 25, 9]
```

만약 중복이 허용되는 임의의 표본 list를 만들고 싶다면 random.choice 메서드를 여러 번 사용하면 된다.  

```{.py}
four_with_replacement = [random.choice(range(10))
						 for _ in range(4)]
# 예를 들어, [9, 4, 4, 2]
```
### 정규표현식

정규표현식(regular expressions), 또는 regex를 사용하면 문자열을 찾을 수 있다.  
정규표현식은 매우 유용하지만 책 한 권이 나올 정도로 상당히 복잡하다.  
여기서는 간략한 예시를 통해서 맛만 보자.  

```{.py}
import re

# 참고로 all과 any는 빌트인 함수로 컨테이너를 인수로 받는다.
# any는 iteration을 하면서 하나라도 참이면 True를 반환한다. 전부 거짓이면 False를 반환한다.
# 반대로 all은 iteration을 하면서 하나라도 참이 아니면 False를 반환하고 전부 참이면 True를 반환한다.

print all([ # 모두 True
		not re.match("a", "cat"), # 'cat'은 'a'로 시작하지 않기 때문에
		re.search("a", "cat"), # 'cat'안에는 'a'가 존재하기 때문에
		not re.search("c", "dog"), # 'dog'안에는 'c'가 존재하지 않기 때문에
		3 == len(re.split("[ab]", "carbs")), # a 혹은 b 기준으로 나누면 ['c', 'r', 's']가 생성되기 때문에
		"R-D-" == re.sub("[0-9]", "-", "R2D2") # 숫자를 "-"로 대체
]) # 따라서 True가 출력된다.
		


```

### 객체 지향 프로그래밍

### 함수형 도구

### enumerate
list를 반복하면 list의 항목과 인덱스가 모두 필요한 경우가 종종 있다.  

### zip과 argument unpacking
가끔씩 두 개 이상의 list를 서로 묶어 주고 싶을 때가 있다.  
zip은 여러 개의 list를 서로 상응하는 항목의 tuple로 구성된 list로 변환해 준다.  

### args와 kwargs
특정 함수 f를 입력하면 f의 결과를 두 배로 만들어주는 함수를 반환해 주는 고차 함수를 만들고 싶다고 해보자.  

```{.py}
```
```{.py}
```
```{.py}
```
```{.py}
```
```{.py}
```


