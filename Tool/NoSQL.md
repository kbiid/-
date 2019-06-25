## NoSQL
- NoSQL 데이터베이스는 전통적인 관계형 데이터베이스 보다 덜 제한적인 일관성 모델을 이용하는 데이터의 저장 및 검색을 위한 매커니즘을 제공한다. 이러한 접근에 대한 동기에는 디자인의 단순화, 수평적 확장성, 세세한 통제를 포함한다. NoSQL 데이터베이스는 단순 검색 및 추가 작업을 위한 매우 최적화된 키 값 저장 공간으로 레이턴시와 throughput(처리율)과 관련하여 상당한 성능 이익을 내는 것이 목적이다. NoSQL 데이터베이스는 빅데이터와 실시간 웹 어플리케이션의 상업적 이용에 널리 쓰인다. 또, NoSQL 시스템은 SQL 계열 쿼리 언어를 사용할 수 있다는 사실을 강조한다는 면에서 "Not only SQL"로 불리기도 한다.
- NoSQL은 초고용량 데이터 처리 등 성능에 특화된 목적을 위해, 비관계형 데이터 저장소에, 비구조적인 데이터를 저장하기 위한 분산 저장 시스템이라고 볼 수 있다.

## 관계형 DB와의 차이
- 관계형 모델을 사용하지 않으며 테이블간의 조인 기능이 없음
- 직접 프로그래밍을 하는 등의 비 SQL 인터페이스를 통한 데이터 액세스
- 대부분 여러 대의 데이터베이스 서버를 묶어서(클러스터링) 하나의 데이터베이스를 구성
- 관계형 데이터베이스에서는 지원하는 Data처리 완경설(Transaction ACID 지원) 미보장
- 데이터의 스키마와 속성들을 다양하게 수용 및 동적 정의(Schema-less)
- 데이터베이스의 중단 없는 서비스와 자동 복구 기능지원
- 다수가 Open Source로 제공
- 확장성,가용성,높은 성능

## NoSQL 종류
- Key Value DB : Key와 Value의 쌍으로 데이터가 저장되는 가장 단순한 형태의 솔루션으로 Amazon의 Dynamo Paper에서 유래되었다. Riak,Vodemort,Tokyo 등의 제품이 많이 알려져 있다.
- Wide Colummnar Store : Big Table DB라고도 하며, Google의 BigTable Paper에서 유래되었다. Key Value에서 발전된 형태의 Column Family 데이터 모델을 사용하고 있고, HBase, Cassandra, ScyllaDB 등이 이에 해당한다.
- Document DB : Lotus Notes에서 유래되었으며, JSON,XML과 같은 Collection 데이터 모델 구조를 채택하고 있다. MongoDB, CoughDB가 이 종류에 해당한다.
- Graph DB : Euler & Graph Theory에서 유래한 DB이다. Nodes, Relationship, Key-Value 데이터 모델을 채용하고 있다 .Neo4J, OreientDB 등의 제품이 있다.
