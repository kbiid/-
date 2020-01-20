<h2>Nginx란</h2>

 - Nginx란 러시아의 한 개발자가 apache의 C10K 문제(한 시스템에 동시접속자 수가 1만명이 넘어갈 때 효율적인 방안)를 해결하기 위해 Event-Driven 구조로 만든 웹 서버 SW이다.
- 우리가 개발한 응용 프로그램이 OSI 7 Layer 중 application Level에서 동작하고 그 아래 Level에서 Nginx같은 웹 서버가 HTTP 통신을 제공하게 된다.
- Nginx는 가벼움과 높은 성능을 목표로 한다. 웹 서버, 리버스 프로시 및 메일 프로식 기능을 가진다.
- Nginx는 기본적으로 두 가지 버전이 존재한다. stable버전과 mainline버전이다. stable 안정 버전이므로 사용이 권장되나 mainline도 불안정한 것은 아니다.

<h2>Apache vs Nginx</h2>

<h3>Apache</h3>

- Client가 HTTP 요청을 보낼 때, Apache는 MPM(Multi-Process Module)을 사용하여 처리한다. MPM에는 크게 두 가지 방식이 있다.
<ol>
  <li>PreFork 방식(다중 프로세스 처리) : Client 요청에 대해 default 갯수만큼 apache 자식 프로세스를 생성하여 처리하고, 요청이 많을 경우 Process를 생성하여 처리하는 방식이다. Apache 설치 시, default로 설정되어 있다.</li>
  <li>Worker 방식(멀티 프로세스 - 스레드 방식) : Prefork와 같이 Default Apache 자식 프로세스를 생성하고 요청이 많아지면 각 프로셋의 스레드를 생성해 처리하는 구조이다. 두 방식의 특징은 우리가 흔히 알고 있는 프로세스와 쓰레드 사용의 장/단점과 동일하다.</li>
</ol>

- Apache는 접속마다 Process 또는 Thread를 생성하는 구조이다. 동시 접속 요청이 10,000개라면 그 만큼 Process or Thread 생성 비용이 들 것이고 대용량 요청을 처리할 수 있는 웹서버로서의 한계를 드러내게 된다.

<h3>Nginx</h3>

- Nginx는 Event-Driven 방식으로 동작한다. 한 개 또는 고정된 프로세스만 생성하고, 그 프로세스 내부에서 비동기 방식으로 효율적으로 작업들을 처리한다. 따라서 동시 접속 요청이 많아도 Process 또는 Thread 생성 비용이 존재하지 않는다.

- Event-Driven 방식에선 작업을 하다 I/O, socket read/write 등 CPU가 관여하지 않는 작업이 시작되면 기다리지 않고 바로 다른 작업을 진행한다. 진행중인 I/O 등의 작업들이 끝나면 아까 했던 작업을 다시 진행하면 된다는 이벤트가 발생하고 그 작업을 처리하게 된다.

<h2>참고 사이트</h2>

- https://medium.com/sjk5766/%EB%84%8C-%EB%AD%90%EB%8B%88-nginx-9a8cae25e964
- https://blog.asamaru.net/2015/11/27/installing-nginx-on-centos-6-dot-5-slash-7/
