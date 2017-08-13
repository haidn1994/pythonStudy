# pyqt

GUI를 위한 pyqt를 배워보자. 여기서는 pyqt5를 기준으로 배워보도록 한다.  

## 가장 간단한 예제

가장 간단한 예제로 simple.py를 만들어볼 것이다.  

```{.py}
#!/usr/bin/python3
# -*- coding: utf-8 -*-

import sys
from PyQt5.QtWidgets import QApplication, QWidget

if __name__ == '__main__':

	# 모든 PyQt5 애플리케이션은 애플리케이션 객체를 생성해야 한다.
	# sys.argv 매개변수는 커맨드라인의 인수 목록이다. 
	app = QApplication(sys.argv)

	# QWidget 위젯은 PyQt5의 모든 사용자 인터페이스 객체의 기본 클래스이다.
	# 또한 기본 생성자를 제공하는데 기본 생성자에는 부모 객체가 없다. 
	# 부모 객체가 없는 위젯을 창(window)이라고 부른다.
	w = QWidget()

	# resize()는 위젯의 크기를 조절한다. 단위는 px이며, 각각 너비(width)와 높이(height)를 조정한다.
	w.resize(250, 150)

	# move()는 위젯을 화면상의 위치로 이동시킨다.
	w.move(300, 300)

	# setWindowTitle은 윈도우의 제목을 결정하는 메소드다.
	w.setWindowTitle('Simple')

	# show()는 위젯을 화면에 표시한다. 위젯은 "먼저 메모리에 만들어지고" 나중에 화면에 표시된다.
	w.show()

	# 마지막으로 응용 프로그램의 메인 루프를 입력한다.
	# 이 시점부터 이벤트 처리가 시작된다. 
	# 메인 루프는 윈도우 시스템으로부터 이벤트를 받아서 어플리케이션 위젯으로 보낸다.
	# 메인 루프는 exit()를 호출하거나 메인 위젯이 파괴되면 끝난다.
	# sys.exit()는 확실한 종료를 보장한다. 응용 프로그램이 어떻게 종료되었는지 시스템 환경에 알려준다.
	sys.exit(app.exec())
```

자세한 설명은 주석에 달려있으니 참고하라

## 아이콘 예제

여기서 말하는 아이콘이란 제목 표시줄의 왼쪽 상단 모서리에 표기되는 작은 이미지를 뜻한다.  
다음 예제에서 pyqt5로 어떻게 다루는 보여줄 것이다. 또한 새로운 방법을 소개한다.  


일부 환경에서는 제목 표시 줄에 아이콘이 표시되지 않지만 가능하게 해야 한다.  
아이콘이 표시되지 않는다면 튜토리얼 필자의 [stackoverflow답변](https://stackoverflow.com/questions/44080247/pyqt5-does-now-show-icons/45439678#45439678)을 참고하도록 한다.  

```{.py}

import sys
from PyQt5.QtWidgets import QApplication, QWidget
from PyQt5.QtGui import QIcon

class Example(QWidget):

	def __init__(self):
		super().__init__()

		self.initUI()
	
	def initUI(self):
		self.setGeometry(300, 300, 300, 220)
		self.setWindowTitle('Icon')
		self.setWindowIcon(QIcon('web.png'))

		self.show()

if __name__ == '__main__':

	app = QApplication(sys.argv)
	ex = Example()
	sys.exit(app.exac_())

```

사실 기능적으로 위의 예제와 크게 다르지 않다. 아이콘을 추가하는 로직과 setGeometry()를 사용했다는 것만 빼면,  
하지만 이 코드는 객체지향적으로 코딩되었고, setGeometry()는 위에서 소개한 move()와 resize()를 한데 합쳐놓은 메소드다.  
그리고 아이콘을 추가하는 메서드를 굉장히 직관적인 편이니 설명은 생략한다. 하지만 제대로 동작하지 않는다면 튜토리얼 저자의 stackoverflow답변을 참고하라.  


## tooltip 보여주기

pyqt5에서는 어떤 위젯에도 풍선 도움말을 붙일 수 있다.  

```{.py}
import sys
from PyQt5.QtWidgets import(QWidget, QToolTip, QPushButton, QApplication)
from PyQt5. QtGui import QFont

class Example(QWidget)
	def __init__(self)
		super().__init__()
		
		self.initUI()

	def initUI(self):
		QToolTip.setFont(QFont('SanSerif', 10)

		self.setToolTip('This is a <b>QWidget</b> widget')

		btn = QPushButton('Button', self)
		btn.setToolTip('This is a <b>QPushButton</b> widget')
		btn.resize(btn.sizeHint())
		btn.move(50, 50)

		self.setGeometry(300, 300, 200, 200)
		self.setWindowTitle('Tooltips')
		self.show()

if __name__ == '__main__':
	app = QApplication(sys.argv)
	ex = Example()
	sys.exit(app.exec_())
```


