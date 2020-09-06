<h2>TLS란?</h2>
- 전송 계층 보안(Transport Layer Security, TLS, 과거 명칭 : 보안 소켓 레이어/Secure Sockets Layer, SSL)은 컴퓨터 네트워크에 통신 보안을 제공하기 위해 설계된 암호 규약이다.
- TLS는 SSL이 표준화 되면서 바뀐 이름이다. 이 규약은 인터넷 같이 TCP/IP 네트워크를 사용하는 통신에 적용되며, 통신 과정에서 전송계층 종단간 보안과 데이터 무결성을 확보해준다.
- SSL은 POODLE, DROWN 등의 취약점이 발견되어 현재 사용되지 않는다.
- TLS를 사용해 암호화된 연결을 하는 HTTP를 HTTPS(Secure)라고 하며, 웹사이트 주소는 HTTPS로 시작한다. 
- TLS는 다양한 종류의 보안 통신을 하기 위한 프로토콜이며, HTTPS는 TLS 위에 HTTP 프로토콜을 얹어 보안된 HTTP 통신을 하는 프로토콜이다.

<h2>설명</h2>
- TLS는 클라이언트/서버 응용 프로그램이 네트워크로 통신을 하는 과정에서 도청, 간섭, 위조를 방지하기 위해서 설계되었다. 그리고 암호화를 해서 최종단의 인증, 통신 기밀성을 유지시켜준다.
- 3단계 기본 절차
 <ol>
 <li>지원 가능한 알고리즘 서로 교환</li>
 <li>키 교환, 인증</li>
 <li>대칭키 암호로 암호화하고 메시지 인증</li>
 </ol>
 
 <h2>참고사이트</h2>
 - https://ko.wikipedia.org/wiki/%EC%A0%84%EC%86%A1_%EA%B3%84%EC%B8%B5_%EB%B3%B4%EC%95%88
 - https://brownbears.tistory.com/402
