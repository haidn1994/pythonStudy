# 데이터 시각화

데이터 과학자가 갖춰야 할 기본 기술 중 하나는 데이터 시각화다.  
시각화를 만드는 것은 아주 쉽지만, 좋은 시각화를 만드는 것은 상당히 어렵다.  
데이터 시각화에는 두 가지 목적이 있다.  

* 데이터 탐색(exploration)
* 데이터 전달(communication)

이 장에서는 데이터를 탐색하는 방법을 배우고, 이 책에서 살펴볼 시각화를 만드는 데 필요한 기술들을 익힐 것이다.  

## matplotlib

matplotlib은 다소 오래되었지만 간단한 막대 그래프, 선 그래프, 또는 산점도를 그릴 떄는 나쁘지 않다.  
그 중에서는 우리는 특히 matplotlib.pyplot모듈을 사용할 것이다.  
pyplot은 시각화를 단계별로 간편하게 만들 수 있는 구조로 되어 있으며, 
시각화가 완성되면 savefig()를 통해 그래프를 저장하거나, show()를 사용해서 화면에 띄울 수 있다.  
예를 들어, 다음 코드를 한번 작성해 보자.

```{.py}
from matplotlib import pyplot as plt

years = [1950, 1960, 1970, 1980, 1990, 2000, 2010]
gdp = [300.2, 543.3, 1075.9, 2886.2, 5987.7, 10290.7, 15002.4]

# x축에는 연도, y축에는 GDP가 있는 선 그래프를 만들자.
plt.plot(years , gdp, color = 'green', marker = 'o', linestyle = 'solid')

# 제목을 더하자
plt.title("Nominal GDP")

# y축에 레이블을 추가하자
plt.ylabel("Billions of $")
plt.show()
```

아주 복잡한 수준의 그래프를 그리는 것보다는 무엇이 있는지 감을 잡을 수 있도록 몇몇 예시를 통해서 가볍게 다뤄보자.  

## 막대 그래프

막대 그래프(bar charts)는 이산적인 항목들에 대한 변화를 보여 줄 떄 사용하면 좋다.  
예를 들어 다음 코드는 여러 영화가 아카데미 시상식에서 상을 각각 몇 개 받았는지를 보여준다.  

```{.py}
movies = ["Annie Hall", "Ben-Hur", "Casablanca", "Gandhi", "West Side Story"]
num_oscars = [5, 11, 3, 8, 10]

# 막대 너비의 기본값이 0.8이므로
# 막대가 가운데로 올 수 있도록 왼쪽 좌표에 0.1씩 더해 주자
xs = [i + 0.1 for i, in enumerate(movies)]

# 왼편으로부터 x축의 위치가 xs이고 높이가 num_oscars인 막대를 그리자
plt.bar(xs, num_oscars)
plt.ylabel("# of Academy Awards")
plt.title("My Favorite Movies")

# 막대의 가운데에 오도록 영화 제목 레이블을 달자.
plt.xticks([i + 0.1 for i, in enumerate(movies)], movies)
plt.show()
```

## 선 그래프

앞에서 이미 살펴본 바와 같이 plt.plot()을 이용하면 선 그래프(line charts)를 그릴 수 있다.  
이 그래프는 다음 코드와 같이 어떤 경향을 보여줄 때 유용하다.

## 산점도

산점도(scatterplots)는 두 변수 간의 연관관계를 보여 주고 싶을 때 적합한 형태의 그래프다.  
예를 들어, 다음 코드는 각 사용자의 친구 수와 그들이 매일 사이트에서 체류하는 시간 사이의 연관성을 보여주는 산점도를 그린다.  

