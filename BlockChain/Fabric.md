## Hyperledger란?
- 리눅스 재단의 Hyperledger 프로젝트는 기업에서 적용이 가능한 표준적인 블록체인의 기술을 구현하는 목적으로 만들어진 블록체인 컨소시엄이다. Hyperledger 프로젝트는 Blockchain Explorer, Fabric, Iroha, Sawtooth Lack 등 여러 하위 프로젝트가 존재하고 있다.

## Hyperledger Fabric 이란?
- Hyperledger 프로젝트의 창립 멤버 중 한 명인 IBM이 44,000 줄의 블록체인 코드를 Hyperledger Fabric에 기부하면서 프로젝트화가 진행되었다. Fabric은 Hyperledger 프로젝트의 핵심 프로젝트로 블록체인의 런타임을 구현하는 프로젝트로 블록체인을 이용한 기반 기술에 대한 내용이 포함되어 있다. Hyperledger Fabric은 모듈형 아키텍처 기반의 블록체인 애플리케이션 또는 솔루션 개발을 위한 근간으로 고안된 비즈니스 블록체인 프레임워크로서 리눅스 재단이 주도하고 있다. Hyperledger Fabric은 합의, 멤버십 서비스 등 구성요소의 플러그 앤 플레이를 지원한다.
- 비트코인과 이더리움과의 차이 : https://cyberx.tistory.com/187
- 비트코인과 이더리움을 사용할 때에는 암호화 화폐를 지불하여 사용해야 하는 반면에 Fabric의 경우 이러한 지불을 해야 하는 형식이 없다. 또한 네트워크의 경우 Fabric은 인증서와 채널 등을 이용하여 같은 네트워크 상에 존재하더라도 인증된 그리고 허가된 사용자에 한해 같은 데이터를 보고 사용할 수 있도록 되어있다. Fabric의 경우 Chaincode라는 Smartcontract의 역할을 하는 것이 존재하며 이 Chaincode의 경우 Go언어를 통해 구현할 수 있다.
- 특징
  <ol>
    <li>허가형 네트워크 : 집단으로 정의된 멤버십과 접근 권한을 비즈니스 네트워크에 제공한다.</li>
    <li>거래의 기밀유지 : 비즈니스의 유연성과 보안성을 제공하여 정확한 암호화 키를 가지고 있는 당사자들에게만 거래가 보이도록 한다.</li>
    <li>암호화 화폐 불필요 : 거래를 확인하기 위해 채굴인나 값비싼 컴퓨팅을 요구하지 않는다.</li>
    <li>설정가능 : 스마트 계약을 활용하여 네트워크 상의 비즈니스 프로세스를 자동화 한다.</li>
  </ol>
  
  ## Hyperledger 구조
  - 크게 Membership, Blockchain, Transaction, Cahincode로 이루어져 있다.
    <ol>
      <li>Membership : Fabric은 참여 권한이 있는 유저들만이 사용 참여할 수 있는 폐쇄형 구조이다. 그래서 유저들이 Fabric 즉 원장(Ledger)에 데이터를 기록,수정,삭제 등의 처리를 하기 위해서 인증서를 필요로 하며 인증서를 발급 받기 위한 기능이 필요하다. 이 인증서를 등록 및 발급 관리 해주는 작업을 하는 것이 Membership이다. 이렇게 생성된 인증서를 통해 트랜잭션을 인정하고 Peer는 이 인증 사용하여 트랜잭션의 결과를 인증한다.</li>
      <li>Blockchain : Blockchain은 프라이빗 블록체인의 기본 구성요소로 블록체인에 저장하기 위한 데이털르 관리하는 분산원장 데이터베이스며, 이를 관리 및 처리하기 위한 기능으로 구성되어 있다. 블록체인 서비스는 HTTP/2 표준을 기반으로 P2P 프로토콜을 통해서 분산원장을 관리한다. 데이터 구조는 해시 알고리즘을 통해 World state를 복제하는 등 관리 하는데 가장 효율적으로 관리할 수 있도록 최적화되어 있다. 필요에 따라 다른 합의 알고리즘 플러그인(PBFT, Raft, PoW, PoS)을 연결하고 구성할 수 있다.</li>
      <li>Transaction : 프라이빗 블록체인에서 서비스나 처리에서 생성되는 트랜잭션을 관리하는 기능이다. 거래에서는 트랜잭션을 처리하는 부분을 기초로 구성되어 있다. 보증 피어 기능이라는 'Endorssement Validation'과 트랜잭션을 배치 처리하고 블록을 생성해 프라이빗 블록체인망에 참여하고 있는 모든 노드들에 분기 및 정렬 역할을 하는 오더링(Odering) 서비스가 있다.</li>
      <li>Chaincode : Chaincode는 Fabric에서 말하는 스마트 컨트랙트를 말하는 것으로 프라이빗 블록체인에서 중요한 기능이다. Chaincode는 기업 및 컨소시엄으로 구성된 서비스에 맞게 블록체인을 활용할 수 있도록 로직을 구현, 변경할 수 있으며 로직을 개발할 수 있도록 'Go', 'Node.js', 자바와 같은 언어로 개발을 할 수 있도록 지원ㄴ하고 있다. Chaincode는 수신 된 트랜잭션에 대한 응답으로 메소드가 호출되는 방식으로 되어있다. 즉 트랜잭션이 생성되어 전송될 때마다 Chaincode 내에 정의되어 있는 메소드가 실행되는 구조로 되어있다.</li>
    </ol>

## Fabric v1.0구조
- https://cyberx.tistory.com/187
<ol>
  <li> MSP(Membership Service Provider)에 해당 Application이 Fabric을 사용할 수 있도록 인증서 등록을 하는 작업을 진행한다.</li>
  <li> Fabric을 이용 시 Application이 블록체인에 트랜잭션 수행을 위한 Proposal을 한다.</li>
  <li> Proposal은 Peer에서 수행된다. Endorser들은 Poroposal을 받은 뒤 내부 처리를 통해 서명을 한 뒤 Proposal response를 Application에게 보낸다.</li>
  <li> 서명된 proposal response를 받은 Application은 트랜잭션을 수행한다.</li>
  <li> Peer에 있는 체인코드를 통해 필요한 처리를 진행한다.</li>
  <li> 처리를 진행 후 트랜잭션은 모든 채널에 대해서 Orderer가 받아서 트랜잭션의 순서대로 정렬을 한다.</li>
  <li> 이렇게 정렬 및 처리가 된 내용을 다시 Peer들에게 일괄적으로 전송을 하게 된다.</li>
</ol>
- 위 흐름에서 Endorser는 보증된 트랜잭션을 처리하도록 하는 역할을 하게 되며, 오더링 서비스는 합의 알고리즘을 수행한다. Fabric에서는 채널이라는 것이 있는데 채널은 실제 Chaincode가 디플로이 되고 트랜잭션이 실행되는 구간을 말한다. 채널이 생성될 때 해당하는 Peer를 지정할 수 있다. 채널이라는 개념을 통해 비즈니스적인 확장성을 제공해 줄 수 있으리라고 판단된다.
