# Activity 화면 전환시 Fragment의 commit에 관해

http://www.kmshack.kr/2013/08/fragment-%ED%8C%8C%ED%97%A4%EC%B9%98%EA%B8%B0-3-fragmentmanager-fragmenttransaction%EC%97%90-%EB%8C%80%ED%95%B4%EC%84%9C/

commit()은 Activity의 onSaveInstanceState() 하기전에 수행되어야 하며, 이를 어길시 java.lang.IllegalStateException: Can not perform this action after onSaveInstanceState 예외가 발생된다.

예를 들어 화면전환을 했다가 돌아 왔을때 Fragment갱신을 해야 하는 경우를 들어 보자.

Activity1에서 onActivityCreated() → commit() 후 다른 Activity2로 전환전 Activity1의 onSaveInstanceState()가 호출 된다.  그런뒤 Activity2를 띄우고 Activity2가 닫긴후 Activity1의 onRestart() → commit()을 하면 예외가 발생한다.

onSaveInstanceState()가 된이후에 commit()을 했기때문이다.

이렇게 화면갱신이 필요한 경우에는 commit()을 쓰지 말고 commitAllowingStateLoss()를 호출 해서 onSaveInstanceState()와 무관하게 commit를 할 수 있다.

 

또한 사용하다가 주의해야 할 점은..

commit은 바로 실행 되지 않고 메인쓰레드에 의해 스케쥴처리 되기때문에 Activity는 종료 되었는데, Fragment가 생성되면서 ApplicationContext에서 NullPointException이 발생 할 수 있다.
