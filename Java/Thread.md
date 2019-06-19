## Thread
- Thread란? : 하나의 프로세스 내부에서 독립적으로 실행되는 하나의 작업 단위를 말하며, 세부적으로는 운영체제에 의해 관리되는 하나의 작업 혹은 태스크를 의미한다. 스레드와 태스크(혹은 작업)은 바꾸어 사용해도 무관하다.
 <ol>
 <li>JVM에 의해 하나의 프로세스가 발생하고 main() 안의 실행문들이 하나의 스레드입니다.</li>
 <li>main() 이외의 또 다른 스레드를 만들려면 Thread 클래스를 상속하거나 Runnable 인터페이스를 구현합니다.</li>
 <li>다중 스레드 작업 시에는 각 스레드끼리 정보를 주고받을 수 있어 처리 과정의 오류를 줄일 수 있다.</li>
 <li>프로세스끼리는 정보를 주고받을 수 없다.</li>
 </ol>
 
 - 멀티스레딩이란? : 여러 스레드를 동시에 실행시키는 응용프로그램을 작성하는 기법을 말한다.
  <ul>
  <li>장점 : 
  <ol><li>메모리 공유로 인한 시스템 자원 소모가 줄어 든다.</li>
  <li>동시에 두 가지 이상의 활동을 하는 것이 가능해진다.</li></ol></li>
  <li>단점 : 
  <ol><li>서로 자원을 소모하다가 충돌이 일어날 가능성이 존재한다.</li>
  <li>코딩이 난해해져 버그 생성확률이 높아진다.</li>
  </ol></li>
  </ul>
  
## Thread의 생성주기
- 그림 참고 : https://codedragon.tistory.com/3526
- Runnable 상태 : Thread가 실행되기 위한 준비 단계
- Running 상태 : 스케줄러에 의해 선택된 Thread가 실행되는 상태
- Blocked 상태 : Thread가 작업을 완수하지 못하고 잠시 작업을 멈추는 단계
<ol>
<li>Runnable (준비 상태) : Thread가 실행되기 위한 준비단계이다. CPU를 점유하고 있지 않으며 실행(Runnung 상태)을 하기 위해 대기하고 있는 상태이다.
코딩 상에서 start() 메소드를 호출하면 run() 메소드에 설정된 Thread가 Runnable 상태로 진입한다. "Ready" 상태라고도 한다.</li>
<li>Running (실행 상태) : CPU를 점유하여 실행하고 있는 상태이며 run() 메서드는 JVM만이 호출 가능하다. Runnable에 있는 여러 스레드 중 우선 순위를 가진 스레드가 결정되면 JVM이 자동으로 run() 메소드를 호출하여 스레드가 Running 상태로 진입한다.</li>
<li>Dead (종료 상태) : Running 상태에서 Thread가 모두 실행되고 난 후 완료 상태이다. "Done" 상태라고도 한다.</li>
<li>Blocked (지연 상태) : CPU의 점유권을 상실한 상태이다. 후에 특정 메소드를 실행시켜 Runnable로 전환한다. wait() 메소드에 의해 Blocked 상태가 된 스레드는 notify() 메소드가 호출되면 Runnable 상태로 간다. sleep(시간) 메소드에 의해 Blocked 상태가 된 Thread는 지정된 시간이 지나면 Runnable 상태로 간다.</li>
</ol>

## Thread클래스 상속과 Runnable 인터페이스 구현의 차이
- Thread 클래스를 상속받으면 다른 클래스를 상속받을 수 없기 때문에, Runnable 인터페이스를 구현하는 방법이 일반적이다.
- Runnable 인터페이스를 구현하는 방법은 재사용성(reusability)이 높고 코드의 일관성(consistency)을 유지할 수 있다는 장점이 있기 때문에 보다 객체지향적인 방법이다.
- 인스턴스 생성 방법의 차이
  <ul>
  <li>ThreadEx te = new ThreadEx(); te.start();</li>
  <li>Runnablelm r = new Runnablelm(); Thread t = new Thread(r,"first"); t.start();</li>
  </ul>
  -> 한 번 사용한 쓰레드는 재사용할 수 없다. 즉, 하나의 쓰레드는 start()가 한 번만 호출될 수 있다.
  
## start()와 run()에 대한 차이와 쓰레드가 실행되는 과정
- run()을 호출하는 것은 생성된 Thread를 실행시키는 것이 아니라 단순히 클래스에 속한 메서드 하나를 호출하는 것이다. 반면에 start()는 새로운 Thread가 작업을 실행하는데 필요한 호출스택(call stack)을 생성한 다음에 run()을 호출해서, 생성된 호출스택에 run()이 첫 번째로 저장되게 한다.
  <ol>
  <li>main메서드에서 Thread의 start메서드를 수행한다.</li>
  <li>start메서드는 Thread가 작업을 수행하는데 사용될 새로운 호출스택을 생성한다.</li>
  <li>생성된 호출스택에 run메서드를 호출해서 Thread가 작업을 수행하도록 한다.</li>
  <li>이제는 호출스택이 2개이기 때문에 스케줄러가 정한 순서에 의해서 번갈아 가면서 실행된다. </li>
  </ol>
- 한 Thread에서 예외가 발생해서 종료되어도 다른 Thread의 실행에는 영향을 미치지 않는다.
