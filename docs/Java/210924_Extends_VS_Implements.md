# Extends vs Implements
- 이직 면접때, 받은 질문이다.<br>
  **"Java의 Extends와 Implements 상속의 차이에 대해 설명해주실 수 있나요?"**

- 나는 .net 개발자였기에 Java의 기초 문법인 이것조차 몰랐었다.<br>
  진짜 지금 생각해보면 대책없이 면접보러 갔었던거 같은데, 당시엔 <br>
  <b>'Java 문법 좀 모르면 어때~~ 객체 지향 개발을 해봤냐 안해봤냐가 중요하지, 문법은 금방 익히자나'</b><br>
  이런 생각을 가지고 있엇다.<br>
  하지만, 면접관분들이 저런 사실을 어떻게 알겠는가~~~ 기초 문법도 모르는데ㅎㅎ<br>
  그래서 부랴부랴 또 복기를 하면서 찾아보았고 그렇게 어렵지 않은 내용이었다.

#### extends
- 상속의 대표적인 형태
- 부모의 메소드를 그대로 사용할 수 있으며, 오바라이딩 할 필요 없이 부모에 구현되있는 것을 직접 사용 가능<br>
  (추상 클래스 상속시엔 추상메소드를 오바라이딩 해야함)
- class - class 또는 interface - interface 상속에 사용
- 다중 상속 불가능

#### implements
- 부모의 메소드를 반드시 오바라이딩 해야함<br>
  (인터페이스 상속시 사용하니깐 당연한 부분)
- 다중 상속 가능