## Redirect vs Forward
- forward : forward 방식은 다음 이동한 URL로 요청정보를 그대로 전달한다. 사용자가 최초로 요청한 요청정보는 다음 URL에서도 유효하다.
  <ul>
    <li>web container 차원에서의 페이지 이동, 실제로 웹 브라우저는 다른 페이지로 이동했는지 알 수 없다.</li>
    <li>웹 브라우저에는 최초 호출한 URL만 표시되고, 이동한 페이지의 URL정보는 볼 수 없다.</li>
    <li>동일한 web container에 있는 페이지로만 이동이 가능하다.</li>
    <li>현재 실행중인 페이지와 forward에 의해 호출될 페이지는 request, response 객체를 공유한다.</li>
  </ul>
- redirect : 최초 요청을 받은 URL1에서 클라이언트에 redirect할 URL2를 리턴하고, 클라이언트에게 새로운 요청을 생성하여 URL2에 다시 요청을 보낸다. 따라서 처음 보냈던 최초의 요청정보는 더 이상 유효하지 않게 된다.
  <ul>
    <li>web container는 redirect 명령이 들어오면 웹 브라우저에게 다른 페이지로 이동하라는 명령을 내린다.</li>
    <li>웹 브라우저는 URL을 지시된 주소로 바꾸고 그 주소로 이동한다.</li>
    <li>다른 web container에 있는 주소로 이동이 가능하다.</li>
    <li>새로운 페이지에서는 request, response 객체가 새롭게 생성된다.</li>
  </ul>
- URL의 변화 여부(redirect -> 변화 O, forward -> 변화 X)
- 객체의 사용 여부(redirect -> 재사용 X, forward -> 재사용 O)
- 시스템(session, DB)에 변화가 생기는 요청(로그인, 회원가입, 글쓰기)의 경우 redirect방식으로 응답하는 것이 바람직하며, 시스템에 변화가 생기지 않는 단순조회(리스트보기, 검색)의 경우 forward 방식으로 응답하는 것이 바람직하다.
