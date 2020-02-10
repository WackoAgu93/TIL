

# String, StringBuffer, StringBuilder

  자바에서 String과 StringBuffer, StringBuilder이 차이점을 알아본다.  
  이들의 모든 공통점은 __String(문자열)을 저장하고 관리하는 클래스__ 들이다.
  
  - 차이점
  String과 StringBuffer, StringBuilder의 차이점은 String은 immutable(불변)하고 StringBuffer, StringBuilder는 mutable(가변)한다는 점이다.
  
  쉽게 말해서 String은 new 연산을 통해 생성되면 그 인스턴스의 메모리 공간은 절대 변하지 않는다.  
  그래서 + 연산이나 concat을 이용해서 문자열에 변화를 줘도 메로리 공간이 변하는 것이 아니라 새로운 String 객체를 new로 만들어서 새로운 메모리 공간을 만들어 낸다.  
  
  이렇게 새로운 문자열이 만들어지면 기존의 문자열은 가비지 콜렉터에의해 제거되어야 하는 단점(언제 제거 될지 모른다.)이 있다.  
  또한 이러한 문자열 연산이 많아질 때 계속해서 객체를 생성하는 오버헤드가 발생하므로 성능이 떨어질 수 밖에 없는 단점이 있다.
  
  대신 String 클래스의 객체는 불변하기 때문에 단순하게 읽어가는 조회연산에서 타 클래스보다 빠르게 읽을 수 있는 장점이 있다. 불변하기 때무에 멀티쓰레드 환경에서 동기화를 신경쓸 필요가 없다.  
  즉, String 클래스는 문자열 연산이 적고 조회가 많을 때 멀티쓰레드 환경에서 사용하면 좋다.
  
  
  [추가 보완 ]
