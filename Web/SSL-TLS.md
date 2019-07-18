## SSL-TLS
- TLS(Transport Layer Security)는 인터넷 상에서 통신할 때 주고받는 데이터를 보호하기 위한 표준화된 암호 프로토콜이다. 
- TLS는 넷스케이프사에 의해 개발된 SSL(Secure Socket Layer) 3.0 버전을 기반으로 하며, 현재는 2008년 발표된 TLSS 1.2가 최종 버전이다.
- TLS는 전송 계층(Transport Layer)의 암호화 방식이기 때문에 HTTP뿐만 아니라 FTP, XMPP등 응용 계층(Application Layer)프로토콜의 종류에 상관없이 사용할 수 있다는 장점이 있으며 기본적으로 인증(Authentication), 암호화(Encryption), 무결성(Integrity)을 지원한다.

## TLS HandShake
 <ol><li>클라이언트와 서버는 메시지로 기본적인 정보를 송수신</li>
 <li>서버는 서버가 사용하는 SSL/TLS 인증서를 전달</li>
 <li>클라이언트는 암호화 통신에 사용할 대칭키를 생성하고 서버에 전달. 이 과정을 키 교환ㄴ(Key Exchange)라고 하며 디피-헬만 키 교환(DIffe-Hellman key exchange) 또는 RSA를 많이 사용</li>
 <li>클라이언트는 암호화 통신에 사용 가능한 암호 알고맂즘과 해시 알고리즘 목록을 서버에 전달</li>
 <li>서버도 알고리즘 목록을 교환 후 핸드셰이크가 종료되며 이제 클라이언트와 서버는 암호화 통신에 필요한 대칭키를 서로 보유</li></ol>
- 이 과정이 끝나면 SSL 세션이 구축되며 실제 암호화 통신을 시작할 수 있다.
- openssl 명령어로 현재 tls의 정보를 볼 수 있다. ex) openssl s_client -connect google.com:443

## HMAC
- 메세지를 두 peer간 통신을 할 때 메세지의 내용이 손상될 수 있다. 메세지의 손상 여부를 파악하기 위해 사용하는 기술이 MAC(Message Authentication Code)이다. TLS에서는 HMAC(Hash MAC)이라는 방법을 사용한다. 만약 A라는 메세지의 내용을 보낸다고 가정하고, 송신 peer는 A를 수신 peer와 합의한 Hash 함수를 이용해서 Hash 값을 만들고 메세지 A에 Hash를 덧붙인 A'를 보낸다. 이를 수신 측 peer에서는 A와 Hash값을 분리하고 A의 Hash 값을 구한 뒤 받은 값과 비교해, 제대로 메세지가 도착했는지 검증한다.

## 

## 참고
- https://soul0.tistory.com/510
- https://b.luavis.kr/server/tls-101
