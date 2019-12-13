1. 인코딩(확장자로 쓰이기도 한다)
<ul>
  <li>.der : Distinguished Encoding Representation(DER). 바이너리 DER 형식으로 인코딩된 인증서, 텍스트 편집기에서 열었는데 읽어들일 수 없다면 이 인코딩일 확률이 높다.</li>
  <li>.pem : X.0 v3 파일의 한 형태
    <ul>
      <li>PEM(Privacy Enhanced Mail)은 Base64인코딩된 ASCII text file이다.</li>
      <li>원래는 secure email에 사용되는 인코딩 포맷이었는데 email쪽에서는 잘 쓰이지 않고 인증서 또는 키 값을 저장하는데 많이 사용된다.</li>
      <li>-----BEGIN XXX-----, -----END XXX----- 로 묶여있는 text file을 보면 이 형식으로 인코딩 되어있다고 생각하면 된다. (담고있는 내용이 무엇인지에 따라 XXX위치에 CERTIFICATE, RSA PRIVATE KEY 등의 키워드가 들어있다.)</li>
      <li>인증서(Certificate = public key), 비밀키(private key). 인증서 발급 요청을 위해 생성하는 CSR(Certificate Signing Request)등을 저장하는데 사용된다.</li>
    </ul>
  </li>
</ul>

2. 확장자
<ul>
  <li>.crt, .cer 인증서를 나타내는 확장자인 cer과 crt는 거의 동일하다고 생각하면 된다.(cer은 Microsoft 제품군에서 많이 사용되고, crt는 unix, linux 계열에서 많이 사용된다.). 확장자인 cer과 crt만 가지고는 파일을 열어보기 전에 인코딩이 어떻게 되어있는지 판단하긴 힘들다.</li>
  <li>.key : 개인 또는 공개 PKCS#8 키를 의미</li>
  <li>.p12 : PKCS#12 형식으로 하나 또는 그 이상의 certificate(public)과 그에 대응하는 private key를 포함하고 있는 key store 파일이며 패스워드로 암호화 되어있다. 열어서 내용을 확인하려면 패스워드가 필요하다.</li>
  <li>.pfx : PKCS#12는 Microsoft의 PFX파일을 계승하여 만들어진 포맷이라 pfx와 p12를 구분없이 동일하게 사용하기도 한다.</li>
</ul>

3. 표준 비교 PKCS#8, PKCS#12, X.509
<ul>
  <li>PKCS #8은 Public-Key Cryptography Standards(PKCS) 표준 중의 일부로 private key를 저장하는 문법에 관한 표준이다. PKCS #8 private keys는 일반적으로 PEM 형식으로 인코딩된다.</li>
  <li>PKCS #12는 하나의 파일에 여러 암호화 관련 엔티티들을 합쳐서 보관하는 방식에 관한 표준이다.</li>
  <li>X.509는 public key infrastructure(PKI)에 대한 ITU-T의 표준(RFC 5280)으로 공개키(public key) 인증서의 format, revocation list(더 이상 유효하지 않은 인증서들에 대한 정보 배포), certification path(chain) validation 알고리즘 등을 정의한다. 보통 X.509 인증서라 하면 RFC 5280에 따라서 인코딩되거나 서명된 디지털 문서를 말한다.</li>
  <li>참고 : PEM 방식으로 인코딩된 pkcs8 형식(format) 비밀키(private key)를 암호화되지 않은 DER 인코딩으로 변경하는 명령어.
  'openssl pkcs8 -topk8 -inform PEM -outform DER -in private.key -out private.der'</li>
</ul>

4. 암호화/복호화 PKCS#1Padding, PKCS#5Padding, PKCS#7Padding의 차이점  

(1) PKCS5Padding,PKCS7Padding

대칭키 알고리즘(ex:AES)을 사용할 때 암호화 하려는 데이터의 길이가 긴 경우 ECB(Electronic Codebook),CBC(Cipher Block Chain)등의 block cipher방식을 사용해서 데이터를 암호화 하게 된다.  
블록단위로 잘라서 암호화/복호화가 진행되기 때문에 정해진 마지막 블록의 사이즈와 실제 데이터의 크기가 맞지 않는 경우가 생길 수 있다.  
이때 마지막 블록의 빈 공간을 채워넣는(padding) 방식을 말한다.  
예를 들어, 데이터가 17바이트인데 block size가 8바이트라면 총 3개의 블록이 필요하고 마지막 블록은 7바이트가 남기 때문에 이 부분을 특정 값으로 채워넣어서 암호화를 진행한다. PKCS5Padding과 PKCS7Padding 둘 다 빈 공간에 값을 채워넣는 규칙은 다음과 같다.
        <ul>
          <li>마지막 블록에 1바이트가 남는다면 '01'을 채워넣고 (01은 1바이트를 16진수 표기한 값)</li>
          <li>마지막 블록에 2바이트가 남는다면 '02 02'를 채워넣음</li>
          <li>마지막 블록에 3바이트가 남는다면 '03 03 03'를 채워넣음</li>
        </ul>
대신 PKCS5Padding과 PKCS7Padding의 경우 block size의 제약 조건이 다르다.  
- PKCS5Padding의 경우 block size 8바이트로 고정
- PKCS7Padding의 경우 block size 최대 255바이트까지 지원

(2) PKCS1Padding  
PKCS1Padding는 앞서말한 PKCS5Padding/PKCS7Padding과는 방식도 다르고 사용자도 다르다.  
PKCS1Padding는 보통 RSA 알고리즘과 같이 사용되며 PKCS#1 v1.5에 명시된 padding 방법을 사용한다.
<ul>
  <li>Encryption Block 구성 = 00 || Block Type || Padding || 00 || Data</li>
  <li>최소 11바이트의 패딩이 추가된다. (오버헤드가 크다) 잉 중 8바이트는 1~255사이의 랜덤 값으로 채워진다.</li>
  <li>이런 랜덤 특성 때문에 동일한 데이터를 암호화 해도 매번 다른 결과가 나온다.</li>
  <li>RSA의 특성상 보통 content 전체를 암호화하는데 사용되지 않고, content를 암호화 하는데 사용한 content key(private key)를 암호화 하기 위한 수단으로 사용되기 때문에 메세지의 크기가 늘어나는 패딩 오버헤드는 크게 문제되지 않는다.</li>
</ul>

(3) Crypto Library in Java  
Java에서 제공하는 Crypto 라이브러리의 경우 Cipher.getInstance("algoritm/mode/padding") 형식의 스트링으로 암호화 알고리즘, 모드, 패딩방식을 결정할 수 있다. 참고로 데이터의 길이가 길어서 (블럭의 갯수가 하나 이상인 경우) ECB는 보안성이 취약하니 CBC를 꼭 사용해야 한다. (각 블럭의 데이터가 섞이지 않은 상태로 동일한 암호화를 적용하면 데이터에 패턴이 나타나게 됨)

예시)
<ul>
  <li>"RSA/ECB/PKCS1Padding" (참고: 이 방식은 1개의 블록만 암호화 할 수 있도록 구현되어있기 때문에 실제로는 ECB라고 부를 수 없다.)</li>
  <li>"AES/ECB/PKCS5Padding"</li>
  <li>"AES/CBC/PKCS5Padding"</li>
  <li>"AES/ECB/PKCS7Padding"</li>
  <li>"AES/CBC/PKCS7Padding"</li>
</ul>

5. 참고 사이트
- https://www.letmecompile.com/certificate-file-format-extensions-comparison/
