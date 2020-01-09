<h2> 동일 출처 정책(Same-Origin Policy) </h2>

- 웹 애플리케이션 보안 모델에서 중요한 개념 중 하나.
- 자바스크립트(XMLHttpRequest)로 다른 웹페이지에 접근할 때는 같은 출처(same origin)의 페이지에만 접근이 가능하다. 같은 프로토콜, 호스트명, 포트가 같다는 것을 의미한다. 즉, 쉽게 말하면 웹페이지의 스크립트는 그 페이지와 같은 서버에 있는 주소로만 ajax 요청을 할 수 있다는 것이다.
- 초기에는 좋은 방법으로 여겨졌지만 요즘은 여러 도메인에 걸쳐서 구성되는 대규모 웹 프로젝트가 늘어나고, REST API 등을 이용한 외부 호출이 많아지는 상황에서는 거추장 스러운 기술이 되기도 하다.
- 그래서 만들어진 추가 정책이 CORS(Cross-Origin Resoure Sharing)이다. 서버에서 외부 요청을 허용할 경우 ajax 요청이 가능해지는 방식이다.
- 서버의 도움 없이 동일 출처 정책을 회피하여 외부 서버로 요청을 날릴 수 있는 방법

  <ol>
    <li> 웹 브라우저 실행 시 외부 요청을 허용하는 옵션을 사용. ex) 크롬 : --disable-web-security 옵션을 추가하여 크롬 실행</li>
    <li> 외부 요청을 가능하게 해주는 플러그인 설치</li>
    <li> JSONP 방식으로 요청.</li>
  </ol>

<h2> CORS(Cross-Origin Resource Sharing) </h2>

- 웹 브라우저에서 외부 도메인 서버와 통신하기 위한 방식을 표준화한 스펙. 서버와 클라이언트가 정해진 헤더를 통해 서로 요청이나 응답에 반응할지 결정하는 방식으로 교차 출처 자원 공유라는 이름으로 표준화가 되었다.
- 특정 HTTP header들을 사용하여 브라우저에게 어떤 도메인(origin)에 있는 리소스에 대한 접근 권한이 다른 도메인에도 있다는 것을 알려주는 방법이다.
- 다른 도메인에서의 요청에 대한 응답은 올바른 CORS header들을 포함해야 한다.
- CORS 에러는 보안 상의 이유로 자바스크립트 코드에서 무엇이 잘못됬는지 접근할 수 없다. 상세 정보를 파악하기 위해서는 브라우저 콘솔을 봐야한다.

<h3> CORS 작동 방식 </h3>
- preflight request(사전 요청) : 요청하려는 URL이 외부 도메인일 경우 웹 브라우저는 preflight요청을 먼저 날리게 된다. preflight 요청은 실제로 요청하려는 경로와 같은ㄴ URL에 대해 OPTIONS 메서드로 요청을 미리 날려보고 요청을 할 수 있는 권한이 있는지 확인한다. 

<h3> 인증된 요청과 응답 </h3>
- 요청을 보내는 측 : 기본적으로 브라우저는 XMLHttpRequest 이나 Fetch를 이용한 cross-domain Reuqest에서 HTTP 쿠키와 HTTP Authentication 정보를 전송하지 않음. withCredentials 옵션을 true로 설정하여야 HTTP 쿠키와 HTTP Authentication 정보를 전송 가능
- 응답을 보내는 측 : 인증된 요청에 응답하는 경우, 서버는 도메인을 특정해야만 하며, 와일드 카드를 사용할 수 없음. 응답 헤더인 Access-Control-Allow-Origin가 특정 도메인을 명시하고 있어야함.

<h3> 서버에서 CORS 요청 핸들링하기 </h3>

  <ol>
    <li>모든 외부 도메인에서 모든 요청을 허용할 경우 처리 : 모든 요청의 응답에 아래 header를 추가. <br>
      <strong>Access-Control-Allow-Origin: *</strong> <br>
      <strong>Access-Control-Allow-Methods: GET,POST,PUT,DELETE,OPTIONS <br> </strong>
      <strong>Access-Control-Max-Age: 3600 <br> </strong>
      <strong>Access-Control-Allow-Headers: Origin, Accept, X-Requested-With, Content-Type, Access-Control-Request-Method, Access-Control-Request-Headers, Authorization</strong>
    </li>
  </ol>
  
  - 웹 브라우저의 스크립트 엔진에서 preflight 요청 응답으로 Access-Control-Allow-Origin header에 "*" 값이 있으면 모든 도메인에서의 요청을 허용하는 것으로 판단한다. 

<h3> 문제 해결 </h3>
- Cross 도메인에 요청을 보낼 때, HTTP Request 코드에 withCredentials : true 프로퍼티를 추가하여 쿠키정보가 함께 요청되도록 함.
- 서버 측에서 응답을 보낼 때,Spring Beadn 설정이나 Controller 단에서 @CrossOrigin 추가.

<h2> 참고사이트 </h2>
- https://brunch.co.kr/@adrenalinee31/1
- https://blog.jungbin.kim/notes/2019-04-27-web-cross-origin-resource-sharing/
