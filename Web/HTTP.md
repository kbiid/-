## HTTP, HTTPS
- HTTP는 HyperText Transfer Protocol로 WWW상에서 정보를 주고 받는 프로토콜이다. 클라이언트인 웹브라우저가 서버에 HTTP를 통해 웹페이지나 이미지 정보를 요청하면 서버는 이 요청에 응답하여 요구하는 정보를 제공하게 된다. 결국, HTTP는 웹브라우저(Client)와 서버(Server)간의 웹페이지같은 자원을 주고 받을 때 쓰는 통신 규약이다. 
- HTTPS는 인터넷 상에서 정보를 암호화하는 SSL(Secure Sockey Layer) 프로토콜을 이용하여 웹브라우저(클라이언트)와 서버가 데이터를 주고 받는 통신 규약이다. HTTPS는 HTTP 메세지(text)를 암호화하는 것이다. HTTPS의 S가 Secure Socket, 보안 통신망을 말한다. HTTPS의 암호화 원리의 핵심은 공개키 암호화 방식이다.

## HTTP 메소드
<ul>
  <li>GET : 요청받은 URI의 정보를 검색하여 응답한다.</li>
  <li>HEAD : GET방식과 동일하지만, 응답에는 BODY가 없고 응답코드와 HEAD만 응답한다.</li>
  <li>POST : 요청된 자원을 생성(CREATE)한다. 새로 작성된 리소스인 경우 HTTP헤더 항목 LOcation : URI주소를 포함하여 응답.</li>
  <li>PUT : 요청된 자원을 수정(UPDATE)한다. 내용 갱신을 위주로 Location : URI를 보내지 않아도 된다. 클라이언트측은 요청된 URI를 그대로 사용하는 것으로 간주함.</li>
  <li>PATCH : PUT과 유사하게 요청된 자원을 수정(UPDATE)할 때 사용한다. PUT의 경우 자원 전체를 갱신하는 의미지만, PATCH는 해당자원의 일부를 교체하는 의미로 사용.</li>
  <li>DELETE : 요청된 자원을 삭제할 것을 요청함. (안정성 문제로 대부분의 서버에서 비활성)</li>
  <li>CONNECT : 동적으로 터널 모드를 교환, 프락시 기능을 요청시 사용</li>
  <li>TRACE : 원격지 서버에 루프백 메시지 호출하기 위해 테스트용으로 사용</li>
  <li>OPTIONS : 웹서버에서 지원되는 메소드의 종류를 확인할 경우 사용</li>
</ul>

## HTTP POST와 PUT의 차이
- POST는 보통 INSERT의 개념이고 PUT은 UPDATE의 개념이다. 동일한 자원을 여러번 POST하면 서버자원에는 변화가 생기지만, 여러번 PUT하는 경우는 변화가 생기지 않는다.
- POST의 경우 클라이언트가 리소스의 위치를 지정하지 않는 경우 사용된다. 따라서, 요청이 여러번 수행되는 경우 매번 새로운 자원이 생성된다. 멱등하지 않는다라고도 말한다.
- PUT의 경우는 클라이언트가 명확하게 리소스의 위치를 지정한다. 아무리 많이 수행되더라도 리소스의 위치가 지정되어 새로운 자원이 생성되지 않으며 동일한 리소스를 수정하기 때문에 여러분 요청하더라도 동일하다.

## PUT과 PATCH의 차이
- PUT이 해당 자원의 전체를 교체하는 의미를 지니는 대신, PATCH는 일부를 변경한다는 의미를 지닌다. PUT은 전체자원을 업데이트하기 때문에 동일 자원에 대해서 동일하게 PUT을 처리하는 경우 멱등하게 처리된다. 반면 PATCH로 처리되는 경우 자원의 일부가 변경되기 때문에 멱등성을 보장할 수 없다.

## HTTP의 멱등성
- 멱등(idempotent)의 의미는 같은 작업을 계속 반복해도 같은 결과가 나오는 경우를 의미한다. 동일한 자원에 대한 GET 요청이라면 클라이언트에 반환되는 모든 응답은 동일해야 한다. 특정 자원에 대한 DELETE의 경우도 자원은 더 이상 이용할 수 없어야 하며, DELETE 요청을 다시 호출한 경우도 자원은 여전히 사용할 수 없는 상태여야 한다.

## HTTP 통신 방식
- 2가지 특징
  <ol>
  <li> HTTP의 요청(request)과 응답(response) 방식 : 요청을 하고 응답을 받는 구조</li>
  <li> statless 
    <ul><li>각 HTTP 통신은 독립적이며 그 전에 처리된 HTTP 통신에 대해 전혀 알지 못함</li>
      <li>상태를 저장할 필요가 없으므로 HTTP 통신 간의 진행이나 연결 상태의 처리, 저장을 구현 및 관리하지 않아도 됨</li>
      <li>요청에 대해 독립적으로 응답만 보내줌</li>
      <li>단점 : stateless라 HTTP 요청시 필요한 모든 데이터를 매번 포함시켜 보내야 함
        <ul><li>어떤 요청시 사용자가 로그인 되어야 한다고 가정할 때, 해당 사용자 로그인 여부를 포함해 HTTP 요청을 날려야 함</li>
          <li>이런 점을 해결하기 위해 쿠키(cookie)나 세션(session)등을 사용해 필요한 진행 과정이나 데이터 저장</li>
          <li>쿠키 : 웹사이트에서 보내온 정보를 저장할 수 있도록 하는 작은 파일로 웹 브라우저(클라이언트)에 저장</li>
          <li>세션 : 쿠키와 마찬가지로 HTTP 통신상에 필요한 데이터를 저장하는데, 웹 서버에 데이터 저장</li></ul></li></ul>
  </li></ol>

## Request
- 메세지 구조
  <ul><li>요청 라인 : GET / HTTP/1.1
  <ul><li>요청 메소드 : GET,POST,PUT,DELETE</li>
    <li>요청 URL</li>
    <li>HTTP 버전</li></ul></li>
  <li>요청 헤더 : 키-값 방식으로 들어감
    <ul><li>Accept : 클라이언트가 받을 수 있는 컨텐츠</li>
      <li>Cookie : 쿠키</li>
      <li>Contetnt-Type : 메세지 바디 종류</li>
      <li>Content-Length : 메세지 바디 길이</li>
      <li>If-Modified-Since : 특정 날짜 이후에 변경됬을 때만</li></ul></li>
  <li>요청 바디(엔티티)</li></ul>
- Content-Type과 Body
  <ol><li>form 형태 : URLEncoded 방식
  <ul><li>application/x-www-form-urlencoded</li>
    <li>메세지 바디 : 쿼리 문자열</li></ul></li>
  <li>json 형태 : application/json</li>
  <li>멀티파트 형태 : 이진파일 넘길 때 사용, 하나의 메세지 바디에 파트를 나눠서 작성
    <ul><li>boundary는 파트 구분자</li>
      <li>multipart/form-data : boundary=frontier</li></ul></li></ol>
      
## Response
- 메세지 구조
  <ul><li>응답 라인 : 버전, 상태 코드, 상태 메세지 : HTTP/1.1 200 OK</li>
  <li>응답 헤더
    <ul><li>Content-Type : 바디 데이터의 타입</li>
      <li>Content-Length : 바디 데이터 크기</li>
      <li>Set-Cookie : 쿠키 설정</li>
      <li>ETag : 엔티티 태그</li></ul></li>
  <li>응답 바디 : HTML, JSON, Octet Stream 등이 있다</li></ul>
- 상태 코드 : https://ko.wikipedia.org/wiki/HTTP_%EC%83%81%ED%83%9C_%EC%BD%94%EB%93%9C
- Content-Type과 Body
  <ul><li>text/plain, text/html</li>
    <li>application/xml, application/json</li>
    <li>image/png, image/jpg</li>
    <li>audio/mp3, vieo/mp4</li></ul>

## HTTP 1.0 1.1 차이
- https://jaweb.tistory.com/entry/HTTP-HTTP-10-%EA%B3%BC-11-%EC%9D%98-%EC%B0%A8%EC%9D%B4-HTTP10-VS-HTTP11

## HTTP1 HTTP2 차이
- 

## 참고
- https://sjh836.tistory.com/81
- https://zzsza.github.io/development/2019/03/01/http-structure/
