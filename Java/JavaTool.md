## JAR 
- JAR(JAVA Archive, 자바 아카이브)는 여러개의 자바 클래스 파일과 클래스들이 이용하는 관련 리소스(텍스트 그림 등) 및 메타데이터를 하나의 파일로 모아서 자바 플랫폼에 응용 소프트웨어나 라이브러리를 배포하기 위한 소프트웨어 패키지 파일 포맷이다.
- JAR 파일은 실제로 ZIP 파일 포맷으로 이루어진 압축파일로서, 파일확장자는 .jar이다. JDK에 포함된 jar명령어를 이용해서 JAR파일을 만들거나 압축을 풀 수 있다. 
- JAR 파일은 자라 런타임이 효율적으로 애플리케이션을 배치(디플로이)할 수 있는 수단으로 설계되었다. JAR파일은 한 차례의 요청으로 애플리케이션 전체를 다운로드 할 수 있게 해준다.
- 압축 해제 명령어 : ex) jar -xf foo.jar
- 실행 명령어 : ex) java -jar foo.jar

## Jconsole
- Jconsole이란 jvm상의 Thread, heap, Memory 및 Vm 정보를 모니터링 하기 위한 툴이다. JDK 1.5에서 제공하며 JMX를 기반으로 동작한다. Jconsole은 JVM의 광범위한 Java Management Extension(JMX) 사용 툴로 자바 플랫폼에서 수행되는 어플리케이션의 퍼포먼스 및 자원 사용에 대한 정보를 제공한다.
- JMX(Java Management eXtension) : 응용 프로그램(소프트웨어),객체,장치(프린터 등) 및 서비스 지향 네트워크 등을 감시 관리를 위한 도구를 제공하는 자바 API이다. 응용프로그램/객체/장치,서비스 지향 네트워크는 MBean(Managed Bean)이라는 객체로 표현된다. 

## JPS
- JPS : Java Virtual Machine Process Status Tool. 대상 시스템에서 HotSpot JVM(Java Virtual Machine)의 목록을 보여준다. 유닉스의 ps -ef | grep java와 유사한 기능.
- 사용 형식 : jps [option] [hostid]
- Options : 
<ul>
  <li>-q : 로컬 VM id 목록만 표시, 클래스명/JAR 파일명/메인 메소드 전달된 인수등 출력 억제</li>
  <li>-m : 메인 메소드의 args 표시</li>
  <li>-l : 전체 패키지명 표시</li>
  <li>-v : jvm 파라미터 표시</li>
  <li>-V : Flag 파일을 통해 JVM에 전달된 인수를 표시 (-XX:Flags=<filename> argument)</li>
  <li>Joption : jps에 의해 호출된 자바 런처(실행)로 옵션을 전달, -J-Xms48m 이렇게 하면 VM에 초기 48Mb로 시작메모리를 설정한다.</li>
</ul>

- Host Identifier : [protocol:][[//]hostname][:port][/servername]

## Keytool
- 키와 인증서를 관리하는 유틸로서, 개인키 공개키 및 자신이 권한을 부여한 인증서를 관리할 수 있게 하며, 자료의 보장과 전자서명에 의한 인증을 관리할 수 있게 한다. 여기서 생성된 키와 인증서는 keystore라는 곳에 저장을 하게 되며 파일로 구현되며, 비밀번호를 이용하여 키나 인증서를 보호한다.
- 사용 방법 :
<ul>
  <li>개인키 생성 : keytool -genkey -keyalg RSA -keystore private</li>
  <li>공개키 추출 : keytool -export -file filee -keystore privateServer -> privateServer라는 것에서 file이라는 이름으로 추출한다.</li>
  <li>공개키를 publicServer라는 파일에 저장 : keytool -import -keystore publicServer -file key</li>
</ul>

## Jmap
- Jmap은 현재 수행중인 자바 어플리케이션의 메모리맵을 보여주는 툴. 이 툴을 사용하여 heap 메모리를 덤프떠서 볼 수 있다.
- 사용방법
<ul>
  <li>jmap [option] <pid></li>
  <li>jmap [option] <executable <core></li>
  <li>jmap [option] [server_id@]<remote server IP or hostname></li>
</ul>
- 옵션
<ul>
  <li>-dump : JVM Heap을 덤프(binary 형식)</li>
  <li>-finalizerinfo : finalize를 기다리는 객체 정보</li>
  <li>-heap : JVM Heap 정보</li>
  <li>-hito : Heap histogram 정보</li>
  <li>-permstat : PermGen 정보</li>
</ul>

## Jstack
- 실행중인 JVM 프로세스에서 쓰레드 덤프를 뜰 수 있게 해주는 툴.

## Jhat
- Jmap으로 생성된 바이너리 heap 덤프 파일을 분석하여 보여주는 툴.

## Jstat
- HostSpot JVM에 있는 모니터링 도구. GC 수행정보, 클래스로더 수행 정보, Jusi-in-Time 컴파일러 수행 정보 등도 jstat으로 알 수 있다.
