# IF와 ELSE로 물어보자

이제 파이썬에서 흐름 제어문을 어떻게 다루는지에 대해서 알아보자.  
대표적으로 IF문이 있는데, 다음과 같이 작성할 수 있다.  

```{.py}
age = 13
if age > 20:
	print('You are too old!')
```
여기서 콜론 다음에는 블록이 있는 것이 보이는가?  
콜론 다음 줄은 블록 안에 있어야 하며, 질문에 대한 대답이 참이라면 명령이 실행될 것이다.  
이제 블록과 조건문을 어떻게 작성하는 알아보자.

## 블록은 프로그래밍 구문들을 모아둔 것

코드의 블록(block)은 프로그래밍 구문들의 집합이다.  
예를 들어, 위에 작성한 코드에 살을 좀 더 붙여보자.

```{.py}
age = 25
if age > 20:
	print('You are old!')
	print('Why are you here?')
	print('Why aren\'t you mowing a lawn or sorting papers?')
```

이 블록은 공백 4칸으로 구분된다. (참고로 파이썬에서는 탭보다는 공백 4개로 하는 것을 권장한다.)  
참고로 블록이 적절하게 구분되지 못한다면, 들여쓰기 에러가 날 것이다. 예를 하나 들어보자.  

```{.py}
If age > 20:
	print('You are old!')
	  print('Why are you here?')	
# 첫번째 줄은 4칸, 두번째 줄은 6칸 공백이 있다. 이 때, 들여쓰기 에러가 발생한다.
```
## IF문과 ELIF문

## 조건문 조합하기

코드를 더 짧고 간단하게 해주는 and와 or키워드를 사용하면 조건문을 조합할 수 있다.  
다음은 or를 사용하는 예제다. 

```{.py}
if age == 10 or age == 11 or age == 12 or age = 13:
	print('What is 13 + 49 + 84 + 155 + 97? A headache!')
else:
	printf('Huh?')
```

이 코드에서 첫번째 줄에 있는 조건들 중에서 어떤 것이든지 참이라면 (즉 age가 10이거나 11, 12, 또는 13이라면)  
다음 줄에 있는 print로 시작하는 코드 블록 실행될 것이다. 또한 이 코드는 and와 몇가지 비교 연산자로 줄일 수 있다.  

```{.py}
if age >= 10 and age <= 13:
	print('What is 13 + 49 + 84 + 155 + 97? A headache!')
else:
	print('Huh?')
```

## 아무런 값이 없는 변수 - NONE

## 문자열과 숫자의 차이점

## 복습

## 프로그래밍 퍼즐

### 1번 문제 답

> I'm rich!! But I might be later...

### 2번 문제 답

```{.py}
if twinkies < 10 or twinkies > 500
	print("Too few or too many")
```

### 3번 문제 답
```{.py}
if 100 <= money and money <= 500 or 1000 <= money and money <= 5000:
	print("correct!")
else:
	print(fail)
```

### 4번 문제 답
```{.py}
ninjas = 5
if ninjas < 10:
	print("I can\'t fight those ninjas!")
elif ninjas < 30:
	print("It\'ll be a struggle, but I can take '\em")
elif ninjas < 50:
	print("That's too many")
```
