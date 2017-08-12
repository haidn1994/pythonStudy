# pyqt

GUI를 위한 pyqt를 배워보자. 여기서는 pyqt5를 기준으로 배워보도록 한다.  

# 가장 간단한 예제

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

