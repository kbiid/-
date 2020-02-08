<h2>배경</h2>

- Apache Struts는 2000년에 등장하여 많은 자바 기반의 웹 어플리케이션들을 개발하는데 도움을 주며 성장을 해왔고 2005년 JavaONE에서 Struts 프로젝트의 개발자와 비하이브의 개발자가 미팅을 통해 Struts Ti 제안 초안을 구성, 그리고 여러 웹 프레임워크의 좋은 아이디어들을 하나로 통합하는 것에 흥미를 가진 개발자들 간의 모임이 만들어지면서, 본격적으로 Struts2의 개발이 시작. Struts1의 보완과 웹워크의 장점을 결합한 형태이다.

<h2>의미</h2>

- 용어의 뜻으로는 "지주, 버팀목, 받침대". MVC 아키텍쳐를 채용하고 있는 자바 기반의 프레임 워크이다.

<h2>특징</h2>
  <ul>
    <li>완전히 새로운 프레임워크(Struts1 때와는 다른 웹워크 2의 MVC 아키텍쳐 채용)</li>
    <li>직관적인 개발 (POJO 기반 액션)</li>
    <li>신속한 리로딩( 변경된 환경 설정 파일의 내용을 컨테이너 재시작 없이 리로드)</li>
    <li>손쉬운 Ajax 구현 (Dojo 프레임워크 포함, Ajax 테마 지원 태그)</li>
    <li>다양한 표현식 언어 EL(Expression Language) 지원 (JSTL, OGNL)</li>
    <li>다양한 리절트 타입의 지원 및 프로파일링</li>
  </ul>
  
<h2>흐름</h2>
  <ol>
    <li>http://localhost...action 다시 말해 client로부터 request가 들어오면 strtuts의 생명주기 시작</li>
    <li>Struts2 상의 web.xml과 struts.xml에서 FilterDispatcher 통과 후 URL 필터링(Servlet container는 이 request를 표준 filter chain으로 전달하는데, FilterDispatch라는 Filter가 호출 됨)</li>
    <li>이 Filter는 ActionMapper를 참조해서 Action를 호출하지 안 할지 결정</li>
    <li>만약 ActionMapper가 호출해야 할 Action을 찾으면 FilterDispatcher는 ActionProxy에게 통제권을 넘겨줌</li>
    <li>ActionProxy는 Struts.xml과 같은 설정(Configuration) file을 읽어서 ActionInvocation class를 생성한 후에 통제권을 넘겨줌</li>
    <li>ActionInvocation은 필요할 경우 interceptor를 하나씩 호출한 후, 처음에 호출하기로 결정한 Action을 호출한다. 해당 class 파일로 이동해서 execute 실행 후 return 값 돌려줌.(Interceptor는 Logging, Validation, File upload, double-submit guard 등 struts에서 제공하는 특정 역할을 수행한다)</li>
    <li>이 Action의 결과값이 반환되면 ActionInvocation은 struts.xml에 정의된 결과 Page를 찾는다(Page는 결국 Response가 된다)</li>
    <li>Action 호출 전에 호출되었던 interceptor를 역순으로 하나씩 호출한 후, response를 Filter(대부분 FilterDispatcher)에게 넘겨준다</li>
    <li>이후 결과가 servlet Container에 넘겨지고 return 값에 따른 jsp(VIEW)를 Client에게 보여줌</li>
  </ol>

<h2>필터 디스패처</h2>

<h3>필터 디스패처란?</h3>

- 사용자의 요청을 최초로 처리하는 것. 서블릿 필터
- 필터 디스패처는 struts2의 컨트롤러이다
- 필터 디스패처는 액션을 실행하기 위한 환경을 구축한다
- 사용자에게 보낼 응답을 처리한다
- \WEB-INF\web.xml

``` 
<filter>
  <filter-name>struts</filter-name>
  <filter-class>org.apache.struts2.dispatcher.FilterDispatcher</filter-class>
</filter>

<filter-mapping>
  <filter-name>struts-cleanup</filter-name>
  <url-pattern>/*</url-pattern>
</filter-mapping>
```

<h2>Struts Interceptor</h2>

<h3>인터셉터란?</h3>

- 액션 실행주위로 실행될 수 있는 코드를 캡슐화한다
- 액션이 실행되기 전후에 요청이 다른 객체에 의해서 가로채어질 수 있다
- 이중서브밋 방지
- 타입변환
- 입력 파라미터의 값을 액션 클래스의 프로퍼티에 설정
- 유효성 검사
- 파일 업로드
- 출력페이지 준비

<h3>인터셉터 스택?</h3>

- 인터셉터는 하나의 액션이 실행되기 전과 후에 요청이 여러 인터셉터를 거치도록 설정할 수 있다. 이처럼 체인형식으로 형성된 여러 인터셉터의 무리를 인터셉터 스택이라 한다.
- 인터셉터는 정의된 순서대로 적용된다.
- 사용자만의 인터셉터 ㅡ


<h2>참고 사이트</h2>
- https://kimseunghyun76.tistory.com/295
- http://wiki.gurubee.net/pages/viewpage.action?pageId=1507889
