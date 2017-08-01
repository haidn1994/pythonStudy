# 유용한 파이썬 모듈

7장에서 배웠듯이 파이썬 모듈은 함수와 클래스, 변수들의 조합이다.  
파이썬은 함수와 클래스를 더 쉽게 사용하기 위해 모듈을 사용한다.  
모듈을 프로그램에 임포트하면 거기에 담긴 모든 것을 사용할 수 있다.  
예를 들어 4장에서 turtle모듈을 임포트 했을 때 우리는 캔버스를 나타내는 객체를 생성하는 데 사용되는 Pen 클래스에 접근할 수 있었다.  

* import turtle
* t = turtle.Pen()

파이썬은 여러 가지 작업들을 위한 모듈들을 많이 가지고 있다. 이번 장에서는 가장 유용한 것들 몇 가지와 그들이 가지고 있는 함수들을 살펴볼 것이다. 

## COPY 모듈을 사용해서 복사본을 만든다.

copy 모듈은 객체의 복사본을 생성하는 함수들을 가지고 있다. 대게 프로그램을 만들 때 새로운 객체를 생성하지만,   
가끔은 복사본을 생성하고 새로운 객체를 생성하기 위해 그 복사본을 사용하는 것이 유용하다.  


예를 들어서 다음과 같은 클래스가 있다고 하자.
```{.py}
class Animal:
	def __init__(self, species, number_of_legs, color):
		self.species = species
		self.number_of_legs = number_of_legs
		self.color = color

# 그리고 새로운 객체를 하나 생성해 보자.

harry = Animal('hipogriff, 6, 'pink')
```

만약 히포그리프 무리를 만들고 싶다면 어떻게 해야 할까?  
앞의 코드를 여러번 반복해서 생성할 수도 있겠지만, 다음과 같이 copy모듈에 있는 copy를 사용할 수도 있다.  

```{.py}
import copy
harry = Animal('hipogriff', 6, 'pink')
harriet = copy.copy(harry)

print(harry.species)
# 출력: hippogriff
print(harriet.species)
# 출력: hippogriff
```

이 예제에서는 객체를 생성하고 harry라는 변수에 담은 다음, 그 객체의 복사본을 생성하여 harriet이라고 한다.  
이 두개의 객체들은 완전히 다른 객체다. 이렇게 하면 약간의 타이핑을 줄여준다.  
하지만 객체가 매우 복잡해서 생성자도 매우 복잡하면, 타이핑도 줄여주고 복사할 수 있다는 것 자체가 훨씬 더 유용할 것이다.  


Animal 객체들의 리스트를 생성하고 copy할 수도 있다.
하지만 여기서 부터 주의해야 할 점이 하나 있다.(이건 비단 리스트에만 해당하는 사항이 아니다.)
만약 원본 리스트인 my\_animals에 있는 Animal객체 중의 하나의 종을 변경하면 어떻게 될까?
파이썬은 more\_animals에 있는 것도 변경한다.
```{.py}
harry = Animal('hipogriff', 6, 'pink')
carrie = Animal('chimera', 4, 'green')
billy = Annimal('bogill', 0, 'purple')
my_animals = [harry, carrie, billy]
more_animals = copy.copy(my_animals)
```


하지만 주의해야 할 점이 하나 있다. copy.copy는 사실상 **얕은 복사**(shallow copy)를 만든 것이기 때문이다.  
이 말은 여러분이 복사했던 객체들 안에 있는 객체들을 복사하지 않았음을(그렇다! 인스턴스가 새로 만들어진게 아니다!)  
의미한다. 여기서는 메인 list객체를 복사했지만, 리스트 안의 각각의 객체들을 복사한 것은 아니다.  

```{.py}
my_animals[0].species = 'ghoul'
print(my_animals[0].species)
print(more_animals[0].species)
```

copy모듈에 있는 다른 함수인 deepcopy는 복사된 객체 안에 있는 모든 객체의 복사본을 실제로 생성한다.  
그 결과 원본 Animal객체들 중 하나를 변경하면 새로운 리스트에 있는 객체들에는 영향을 미치지 않는다.  
다음 예제를 살펴보자.

```{.py}
more_animals = copy.deepcopy(my_animals)
my_animals[0].species = 'wyrm'

print(my_animals[0].species)
# 출력: wyrm
print(more_animals[0].species)
# 출력: ghoul
```

## KEYWORD 모듈로 키워드 추적하기

## RANDOM 모듈로 랜덤 숫자 얻기

### 난수를 뽑기 위해 RANDINT 사용하기

### 리스트에서 항목을 무작위로 뽑기 위해 CHOICE사용하기

### 리스트를 섞기 위해 SHUFFLE 사용하기

## SYS 모듈로 쉘 컨드롤 하기

sys 모듈은 파이썬 쉘 자체를 컨트롤할 때 사용할 수 있는 시스템 함수들을 가지고 있다.  
여기서는 exit함수, stdin과 stdout객체, version변수를 어떻게 사용하는지 살펴볼 것이다.  

### EXIT 함수로 쉘 종료하기

exit함수는 파이썬 쉘이나 콘솔을 멈추는 방법이다. 
다음의 코드를 입력하면 정말로 종료하고 싶은지를 묻는 다이얼로그가 나타날 것이다. Yes를 클릭하면 쉘이 종료된다.
(이건 python IDLE를 사용하고 있을 때 나타나는 것이고, 아니면 안 나타난다.)  

* import sys
* sys.exit()

### STDIN 객체로 읽기

### STDOUT 객체로 쓰기

### 내가 쓰는 파이썬 버전은?

## TIME 모듈로 시간 작업하기

파이썬의 time 모듈은 시간을 표시하는 함수들을 가지고 있다.  
주의해야 할 점은 사람이 보는 시계와 많이 다른 모습과 목적을 가진다는 점이다.  

### ASCTIME으로 날짜 변환하기

### LOCALTIME으로 날짜와 시간 얻기

### SLEEP으로 잠깐 쉬기

## 정보를 저장하기 위해 PICKLE모듈을 사용하기

## 복습

## 프로그래밍 퍼즐

### 1번 문제 답
### 2번 문제 답

