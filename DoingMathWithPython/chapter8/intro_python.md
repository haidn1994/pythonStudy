# 파이썬 주제 소개

이 부록의 목적은 두 가지다. 앞의 장에서 상세히 소개하지 못한 몇 가지 파이썬 주제에 대해 빠르게 소개하고  
더 좋은 파이썬 프로그램을 작성할 수 있는 주제를 소개한다.  

## if\_\_name\_\_ == '\_\_main\_\_':

이 책 전반에 걸쳐 다음 코드 블록을 이용한다. 블록 내에 정의한 func()는 함수다.  

```{.py}
if\_\_name\_\_ == '\_\_main\_\_':
	# Do something
	func()
```
이러한 코드 블록은 프로그램이 자체적으로 실행될(임포트 된 것이 아니게) 때만 블록 내 명령이 실행되도록 해준다.  
'백문이 불여일타' 간단한 데모를 살펴보고 factorial.py를 호출하는 다음 프로그램을 살펴보자.  

```{.py}
# Find the factorial of a number
def fact(n):
	p = 1
	for i in range(1, n + 1)
		p = p*i
	return p

print(__name__) # (1)

if __name__ == '__main__':
	n = int(input('Enter an integer to find the factorial of: '))
	f = fact(n)
	print('Factorial of {0} : {1}'.format(n, f))
```
위 프로그램은 정수의 팩토리얼을 계산하는 함수 fact()를 정의하고 있다.  
이 프로그램을 실행하면 \_\_name\_\_은 자동으로 \_\_main\_\_으로 설정되므로 (1)에서 print명령에 해당하는  
\_\_main\_\_을 출력한다.  다음으로 정수를 입력하면 정수의 책토리얼을 계산한 다음 이를 출력한다.  


이제 또 다른 프로그램에서 팩초리얼을 계산할 필요가 있다고 하자. 함수를 다시 작성하는 대신 이를 임포트해  
해당 함수를 재사용한다.
```{.py}
from factorial import fact
if __name__ == '__main__':
	print('Factorial of 5: {0}'.format(fact(5)))
```

두 프로그램은 동일한 디렉토리에 있어야 함을 주의하자. 이 프로그램을 실행하면 다음과 같은 결과를 얻게 된다.  


```{.py}
# factorial
# Factorial of 5: 120
```
요약하면 프로그램에서 if\_\_name\_\_ == '\_\_main\_\_': 을 사용하는 것은 좋은 관행이다.  
이렇게 작성된 프로그램 코드는 자체실행모드(standalone)에서는 실행이 된다. 하지만 또 다른 프로그램에 임포트하면  
해당 프로그램 코드는 실행되지 않는다.  

## 리스트 컴프리헨션
 
정수 리스트를 가지며 원 리스트의 요소 제곱으로 이루어진 신규 리스트를 생성한다고 하자.  
이미 우리가 알고 있는 방법은 다음과 같다.  

```{.py}
x = [1, 2, 3, 4]
x_square = []
for n in x:
	x_square.append(n**2)
print(x_square)
# [1, 4, 9, 16]
```

하지만 리스트 컴프리헨션을 사용하면 좀 더 효율적으로 사용할 수 있다.  
(내가 생각하기에 리스트 컴프리헨션은 안쪽에 흐름 제어문을 적절하게 넣으면 필터링해서 넘겨주는 구문인 것 같다.
 또한 이 녀석의 특징은 흐름 제어문임에도 불구하고 :을 붙이지 않아도 내부적으로 알아서 처리하는 듯 싶다.)  

```{.py}
x_square = [n**2 for n in x]
print(x_square)
```
이렇게 해도 이전 코드와 완전히 동일한 결과를 얻을 수 있다.  


또 다른 예제로 포물선 운동을 하는 물체의 궤적을 그리기 위해 74p의 '포물선 그리기'에서 작성한 프로그램을 살펴보자.  
이 프로그램은 각 시간에 x와 y좌표를 계산하기 위한 다음 코드 블록을 갖는다.  
```{.py}
# 시간간격 계산
intervals = frange(0, t_flight, 0.001)

# x와 y좌표리스트
x = []
y = []
for t in intervals:
	x.append(u*math.cos(theta)*t)
	y.append(u*math.sin(theta)*t - 0.5*g*t*t)
```

리스트 컴프리헨션을 이용하면 다음과 같은 코드 블록을 재작성 할 수 있다.  

```{.py}
# 시간간격 계산
intervals = frange(0, t_flight, 0.001)

# x와 y좌표리스트
x = [u*math.cos(theta)*t for t in intervals]
y = [u*math.sin(theta)*t - 0.5*g*t*t for t in intervals]
```

공백 리스트를 만들고 for루프를 작성하여 리스트에 추가할 필요가 없어졌으므로 코드는 더 간결해졌다.  
리스트 컴프리헨션은 명령 하나로 이러한 문제를 해결해 준다.  
어떤 리스트 아이템을 수식에서 계산할지를 선택하기 위해 리스트 컴프리헨션에 조건을 추가할 수 있다.  
다시 한번 첫번째 예제를 살펴보자.  

```{.py}
x = [1, 2, 3, 4]
x_square = [n**2 for n in x if n%2 == 0]
print(x_square)
# [4, 16]
```

이 리스트 컴프리헨션에서 if조건을 이용해 파이썬이 x의 짝수 리스트 아이템만을 대상으로 수식 n\*\*2를 계산한다.  

