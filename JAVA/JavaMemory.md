
# JAVA 의 Stack 과 Heap

![JAVA Memory](../image/javamemorystackheap.jpg)

## Stack

- __Heap 영역에 생성된 Object 타입의 데이터의 참조값이 할당__ 된다.  
- 원시타입의 데이터가 값과 함께 할당된다.  
- __지역변수들은 scope 에 따른 visibility__ 를 가진다.  
- 각 __Thread 는 자신만의 Stack__ 을 가진다.  

  Stack에는 Heap 영역에서 생성된 Object타입의 데이터들에 대한 참조를 위한 값들이 할당된다. 또한, 원시타입(primitive types) - byte, short, int, long, double, float, boolean, char 타입의 데이터들이 할당된다. 이때 원시타입의 데이터들에 대해서는 참조값을 저장하는 것이 아니라 실제 값을 Stack 에 직접 저장하게 된다.
  
  Stack 영역에 있는 변수들은 visibility를 가진다. 변수의 scope에 대한 개념이다. 전역변수가 아닌 지역변수가 foo() 라는 함수내에서 Stack 에 할당 된 경우, 해당 지역변수는 다른 함수에서 접근할 수 없다. 예시로, foo()라는 함수에서bar() 함수를 호출하고 bar() 함수의 종료되는 중괄호 `}`가 실행된 경우(함수가 종료된 경우), bar() 함수 내부에서 선언한 모든 지역변수들은 stack에서 pop 되어 사라진다.
  
  Stack 메모리는 Thread 하나당 하나씩 할당된다. 즉, 쓰레드 하나가 새롭게 생성되는 순간 해당 쓰레드를 위한 Stack도 함께 생성되며, 각 쓰레드에서 다른 쓰레드의 Stack 영역에는 접근할 수 없다.
  
__Stack 실행 코드__

```java
  public class Main{
    public static void main(String[] args) {
      int argument = 4;
      argument = someOperation(argument);
    }
    
    private static int someOperation(int param){
      int tmp = param * 3;
      int result = tmp / 2;
      return result;
    }
  }
```
  argument 에 4 라는 값을 최초로 할당했고, 이 argument 변수를 함수에 넘겨주고 결과값을 또 다시 argument에 할당하는 코드이다.  
  `int arguemnt = 4;` 에 의해 argument라는 변수 명으로 공간이 할당되고, argument 변수의 타입은 원시타입이므로 이 공간에는 실제 4라는 값이 할당된다.
![MemoryStack](../image/javamemory_1.png)

  `someOperation()` 함수가 호출될때 인자로argument 변수를 넘겨주며 scope가 `someOperation()` 함수로 이동한다. scope가 바뀌면서 기존의 argument 라는 값은 scope에서 벗어나므로 사용할 수 없다. 이때 인자로 넘겨받은 값은 파라미터인 param 에 복사되어 전달하는데, param 또한 원시타입이므로 stack에 할당된 공간이 값에 할당된다.
![MemoryStack](../image/javamemory_2.png)

```java
  int tmp = param * 3;
  int result = tmp / 2;
```
![MemoryStack](../image/javamemory_3.png)

  다음으로, 닫는괄호 `}` 가 실행되어 `someOperation()` 함수 호출이 종료되면 호출함수 scope 에서 사용되었던 모든 지역변수들은 stack에서 pop 된다. 함수가 종료되어 지역변수들이 모두 pop 되고, 함수를 호출했던 시점으로 돌아가면 스택의 상태는 아래와 같이 변한다.
![MemoryStack](../image/javamemory_4.png)
  argument 변수는 4로 초기화 되었지만, 함수의 실행결과인 6이 기존 argument 변수에 재할당 된다. 물론 함수호출에서 사용되었던 지역변수들이 모두 pop되기 전에 재할당 작업이 일어날 것이다.

## Heap

  - Heap 영역에는 주로 긴 생명주기를 가지는 데이터들이 저장 된다. (대부분의 오브젝트는 크기가 크고, 서로 다른 코드블럭에서 공유되는 경우가 많다.)  
  - 애플리케이션의 모든 메모리 중 Stack 에 있는 데이터를 제외한 부분이라고 보면 된다.  
  - __모든 Object 타입(Integer, String, ArrayList, ...)은 Heap 영역에 생성__ 된다.  
  - __몇개의 스레드가 존재하든 상관없이 단 하나의 Heap 영역만 존재__ 한다.  
  - Heap 영역에 있는 오브젝트들을 가리키는 레퍼런스 변수가 Stack에 올라가게 된다.  
  
  
  [좀더 공부 필요]
  - 참조  
  https://yaboong.github.io/java/2018/05/26/java-memory-management/
