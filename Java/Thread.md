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

## Thread Pool
- Thread Pool이란 쉽게 말해서 스레드를 미리 만들어 두는 것이다. thread가 비록 fork()에 비해서 생성과 소멸시에 훨씬 적은 비용을 소모하지만 꽤 많은 시간과 비용을 소비하는 작업이다. Thread Pooling은 이러한 반복적인 thread의 생성/소멸에 의한 비효율적인 측면을 없애고자 하는 목적으로 만들어진 프로그래밍 기법이다.
- 동작 원리 : 자바에서는 스레드풀을 생성하고 사용할 수 있도록 java.util.concurrent Package에서 ExecutorService 인터페이스와 Executors클래스를 제공하고 있다. Executors의 다양한 정적 메서드를 통해 ExecutorService 구현객체를 만들어서 사용할 수 있으며, 그것이 바로 스레드 풀이다.
- 장점
 <ul>
 <li>스레드를 생성/수거하는데 드는 비용이 들지 않는다.</li>
 <li>스레드가 생성될 때 os가 메모리 공간을 확보해주고 메모리를 스레드에게 할당해준다.</li>
 <li>스레드 풀을 미리 만들어 두기 때문에 처음에 생성하는 비용은 들지만 이전의 스레드를 재사용할 수 있으므로 시스템 자원을 줄일 수 있고, 작업을 요청시 이미 스레드가 대기중인 상태이기 때문에 작업을 실행하는데 딜레이가 발생하지 않는다.</li>
 <li>서비스 적인 측면으로 바라볼 때, 특히 대규모 프로젝트에서 다수의 사용자의 요청을 수용하고, 빠르게 처리하고 대응하기 위해 스레드풀을 사용한다.</li>
 </ul>
- 단점
 <ul>
 <li>thread pool에 thread를 너무 많이 생성해 두었다가 사용하지 않으면 메모리 낭비가 발생한다.</li>
 </ul>
 
## ExecutorService, Executor
- Executor : Java 5부터 제공되는 인터페이스(concurrency api)로서  구현체로 쓰레드 풀, 큐 등을 다양하게 제공하고 있다.
- ExecutorService : 병렬작업 시 여러개의 작업을 효율적으로 처리하기 위해 제공되는 JAVA의 라이브러리이다. 통상적으로 작업을 분리하고 수행하는 작업을 구현하려고 하면, 각기 다른 Thread를 생성해서 작업을 하고, 처리가 완료되면 해당 Thread를 제거하는 작업을 진행해야 한다. 이러한 일련의 작업을 쉽게 할 수 있도록 도와준다.
 <ul>
 <li>CachedThreadPool : thread를 캐싱하는 thread pool(여기서 캐싱의 의미는 일정시간동안 thread를 검사한다는 뜻. 60초 동안 작업이 없으면 pool에서 제거한다.)</li>
 <li>FixedThreadPool : 고정된 개수를 가진 thread pool</li>
 <li>SingleThreadExecutor : 한 개의 thread로 작업을 처리하는 thread pool</li>
 </ul>

## Callable, Runnable
- Callable은 다른 쓰레드에 의해서 실행되어질 수 있는 클래스의 객체를 위한 interface라는 점에서 Runnable과 비슷한 인터페이스이다.
- Callable이 Generic으로 받은 Return 타입으로, return을 하는데 반해서, Runnable은 return값이 없다. Callable이 Exception을 낼 수 있는데 반해, Runnable은 그럴 수 없다.
- Callable이 Runnable의 확장형 개념. Runnable은 1.0, Callable는 1.5에서 생겨남. Runnable은 놔두고 기능을 확장하기 위해서 Callable이 만들어졌다.

## Multi Process, Multi Thread
- 동시에 두 가지 이상의 루틴을 실행할 수 있는 역할을 하는 것은 동일하다.
- Multi Process
 <ul>
 <li>부모-자식 관계라고 해도 자신만의 메모리 영역을 가지게 된다.</li>
 <li>환경변수와 프로세스 핸들 테이블이 상속 가능할 뿐 결국 독립적인 관계이다.</li>
 <li>fork를 통해 프로세스를 복사한다.</li>
 <li>유닉스 계열에서 ps 명령어로 현재 수행되고 있는 프로세스를 확인할 수 있다.</li>
 <li>프로세스 간의 통신을 하려면 IPC(Inter Process Comuunication; 세마포어, 큐, 공유메모리)를 통해야 한다.</li>
 </ul>
- Multi Thread
 <ul>
 <li>하나의 프로세스가 다수 개의 작업을 각각 스레드를 이용하여 동시에 작동 시킬 수 있다.</li>
 <li>다음과 같은 공유 메모리를 가진다 :  Code 영역, Data 영역, Heap 영역</li>
 </ul>
 * 참고 : https://you9010.tistory.com/136
 
- Multi Thread는 Multi Process에 비해 상당한 이점을 가진다.
 <ol>
 <li>컨텍스트 스위칭(Context Switching) 시에 공유 메모리 만큼의 시간(자원) 손실이 줄어든다.</li>
 <li>Stack을 제외한 모든 메모리를 공유하기 때문에 global(전역), static(정적) 변수 그리고 new, malloc에 의한 모든 자료를 공유할 수가 있다.(이는 프로세스간 통신(ex.pipe)과 같이 복잡한 과정을 거치지 않고 보다 효율적인 일처리가 가능하다는 것을 뜻한다.)
 </li>
 </ol>
 -> 서로 별개의 프로그램이라면 독립적인 프로세스를 구성해야 하지만  서로 관련된 기능들은 멀티 스레드로 구현하는 것이 이득이다.

- 여러 개의 스레드가 동일한 데이터 공간을 공유하면서 이들을 수정한다는 점에서 문제가 생긴다. 멀티 프로세스의 방식의 프로그램에서 하나의 프로세스가 자신의 데이터 공간을 망가뜨린다면 해당 프로세스의 중단을 낳게 될 것이다. 하지만 멀티 스레드 방식의 프로그램에서는 하나의 스레드가 자신이 사용하던 데이터 공간을 망가뜨린다면 그 결과는 하나의 데이터 공간을 공유하는 모든 스레드를 작동불능 상태로 만들어 버릴 것이다.
