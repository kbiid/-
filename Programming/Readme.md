## IaaS, PaaS, SaaS, BaaS
- Iaas(Infrastructure as a Service)는 서버를 운영하기 위한 서버 자원, IP, Network, Storage, 전력 등등 인프라를 구축하기 필요한 것들을
가상의 환경에서 쉽고 편하게 이용할 수 있도록 서비스 형태로 제공. H/W 확장성이 좋고 탄력적이면 빠른 제공이 가능한 가상화 기술 사용.
PaaS,SaaS의 기반이 되는 기술
- PaaS(Platform as a Service)는 서비스를 개발할 수 있는 안## IaaS, PaaS, SaaS, BaaS
- Iaas(Infrastructure as a Service)는 서버를 운영하기 위한 서버 자원, IP, Network, Storage, 전력 등등 인프라를 구축하기 필요한 것들을
가상의 환경에서 쉽고 편하게 이용할 수 있도록 서비스 형태로 제공. H/W 확장성이 좋고 탄력적이면 빠른 제공이 가능한 가상화 기술 사용.
PaaS,SaaS의 기반이 되는 기술
- PaaS(Platform as a Service)는 서비스를 개발할 수 있는 안정적인 환경과 그 환경을 이용하는 응용 프로그램을 개발할 수 있는
API까지 제공하는 형태
- SaaS(Software as a Service)는 Cloud환경에서 동작하는 응용프로그램을 서비스 형태로 제공하는 것
- http://www.hostway.co.kr/support/faq/iaas-paas-saas%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80%EC%9A%94
- BaaS(Backend as a Service)는 모바일 백엔드 서비스를 의미한다. 서버와 통신하는 백엔드를 서비스 형태로 개발자에게 제공해 서버기술을 몰라도 그 환경에 연결되는 모바일 앱을 만들 수 있도록 지원해주는 퍼블릭 클라우드의 일종이다.
- http://i-bada.blogspot.com/2015/10/backend-as-service-baas.html

## CI/CD
- CI/CD는 애플리케이션 개발 단계를 자동화하여 애플리케이션을 보다 짧은 주기로 고객에게 제공하는 방법. 지속적인 통합, 지속적인 서비스 제공,
지속적인 배포.
- CI(Continuous Integration)
- CD는 (Continuous Delivery) or (Continuous Deployment)
- https://www.redhat.com/ko/topics/devops/what-is-ci-cd

## XML vs JSON vs YAML
- XML은 데이터를 표현하기 위해 많이 사용되어 온 방식으로 HTML과 흡사한 구조를 가지고 있음. 고유한 문법이 있으며 소프트웨어 및 하드웨어에 대하여 독립적으로 데이터를 처리할 수 있음. 특징은 꺽쇠(<>). 트리 계층 구조를 가지고 있다.
- JSON도 데이터를 처리하기 위한 방식. REST API 사용시 가장 많이 사용되며, 주석을 사용할 수 없다.
- YAML은 JSON과 비슷하게 사람이 읽기 쉬운 형태의 데이터 표현. 주석을 사용 가능하며 개행, 공백으로 블록을 인식. 태그를 사용하지 않으며 공백 위주로 데이터를 구분하므로 한 줄로 작성할 수 없다. 한글과 같은 유니코드를 그대로 사용할 수 있다는 장점이 있음.
- https://ndb796.tistory.com/251

## 아키텍트 용어 
- 아키텍트 : 아키텍쳐를 설계 하는 사람을 의미한다.

- Enterprise Architect (EA) : Business Architecture를 포함하여 전체 아키텍쳐의 설계에 대한 책임을 갖고 있다. 비즈니스의 이해를 바탕으로 전체 시스템에 대한 큰 그림을 설계하며, 장기적인 IT전략 수립을 담당한다. SA,TA,AA,DA,BA에 대한 통제권한을 가지고 팀을 운영하기도 한다.

- Solution Architect (SA) : SA는 특정 솔루션에 대한 Architecture를 설계한다. SA가 하는 업무와 EA와 겹치는 부분이 있을 수도 있지만, EA가 전체 구조에 대한 설계라면 SA는 특정 분야에 대한 세부설계를 담당한다고 할 수 있다. 특정 영역에 대해서 전문적인 지식이 필요하다.

- Technical Architect (TA) - Infra Architet : 프로젝트에서 필요로 되어지는 Hardware 및 네트워크의 아키텍쳐를 설계한다. 

- Application Architect (AA) : 특정 어플리케이션의 구축에 대한 표준 가이드 및 아키텍쳐 구조를 담당한다. SA는 각각의 독립적인 Application 간의 종속성이 발생하는 것에 대한 설계를 진행하며, AA는 독립적인 Application의 세부 설계를 담당하게 된다.

- Data Architect (DA) : 전체 데이터에 대한 구조적 설계를 담당한다.

- Business Architect (BA) : EA는 좀 더 기술적 측면에 집중하고 BA는 비즈니스적 측면을 고려할 수 있도록 역할을 분담한다.

- Global Architect (GA) : 일반적인 프로젝트 팀 구조에서는 잘 존재하지 않는 역할이다. EA는 비즈니스를 포함한 외부 대응이나 큰 그림에 신경 쓰고, GA는 기술 위주의 아키텍쳐 설계에 집중한다.

- Quality Assurance (QA) : 주로 프로그램이나 문서의 검수를 한다. 로직이나 내용보다는 룰(규정) 지켰는지 확인.
게임업계에서는 게임이 일정 수준의 품질을 가질 수 있도록 제품 출시 이전에 각종 테스트 및 검수 작업을 하는 업무를 말한다.

- Quality Control (QC) : 품질관리를 뜻한다. 품질관리란 기업 경영상 제일 유리하다고 생각되는 품질을 보장하고 이것을 가장 경제적 제품으로서 생산하는 방법을 말한다. 또한 품질에 대한 요구 사항을 만족 시키기 위해 사용되는 운영상의 기법 및 활동을 말한다.

정적인 환경과 그 환경을 이용하는 응용 프로그램을 개발할 수 있는
API까지 제공하는 형태
- SaaS(Software as a Service)는 Cloud환경에서 동작하는 응용프로그램을 서비스 형태로 제공하는 것
- http://www.hostway.co.kr/support/faq/iaas-paas-saas%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80%EC%9A%94

## CI/CD
- CI/CD는 애플리케이션 개발 단계를 자동화하여 애플리케이션을 보다 짧은 주기로 고객에게 제공하는 방법. 지속적인 통합, 지속적인 서비스 제공,
지속적인 배포.
- CI(Continuous Integration)
- CD는 (Continuous Delivery) or (Continuous Deployment)
- https://www.redhat.com/ko/topics/devops/what-is-ci-cd

## XML vs JSON vs YAML
- XML은 데이터를 표현하기 위해 많이 사용되어 온 방식으로 HTML과 흡사한 구조를 가지고 있음. 고유한 문법이 있으며 소프트웨어 및 하드웨어에 대하여 독립적으로 데이터를 처리할 수 있음. 특징은 꺽쇠(<>). 트리 계층 구조를 가지고 있다.
- JSON도 데이터를 처리하기 위한 방식. REST API 사용시 가장 많이 사용되며, 주석을 사용할 수 없다.
- YAML은 JSON과 비슷하게 사람이 읽기 쉬운 형태의 데이터 표현. 주석을 사용 가능하며 개행, 공백으로 블록을 인식. 태그를 사용하지 않으며 공백 위주로 데이터를 구분하므로 한 줄로 작성할 수 없다. 한글과 같은 유니코드를 그대로 사용할 수 있다는 장점이 있음.
- https://ndb796.tistory.com/251
