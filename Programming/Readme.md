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

## SOLID
- S : SRP(Single Responsibility Principle) 단일 책임 원칙. 모든 클래스는 단 하나의 책임을 가진다. 즉, 클래스를 수정할 이유가 오직 하나여야한다는 뜻이다. 이는 각 클래스의 응집도(Cohension)을 높이기 위함이다.
- O : OCP(Open Closed Principle) 개방-폐쇄 원칙. 확장에 대해서는 개방 되어 있어야 하지만, 수정에 대해서는 폐쇄 되어야 한다. 기능을 확장했을 때, 기존 클래스의 변경을 최소화하는 것이다.
- L : LSP(Liskov Substitusion Principle) 리스코프 치환 법칙. 자식 클래스는 언제나 자신의 부모 클래스를 교체할 수 있다는 원칙이다. 즉, 부모 클래스가 들어갈 자리에 자식 클래스를 넣어도 계획대로 잘 작동해야 한다는 원칙. 업캐스팅을 해도 아무런 문제가 야 한다는 것이다. 
- I : ISP(Interface Segregaion Principle) 인터페이스 분리 원칙. 클라이언트가 자신이 이용하지 않는 메서드에 의존하지 않아야 한다는 원칙. 자신이 사용하지 않는 기능(인터페이스)에는 영향을 받지 말아야 한다는 의미이다. 각 메소드의 변경에 따른 클래스의 변경을 최소화하자는데 있다.
- D : DIP(Depndency Inversion Principle) 의존성 역전 법칙 : 상위클래스는 하위클래스에 의존해서는 안된다는 법칙. 
- https://wkdtjsgur100.github.io/solid-principle/

## PMO, PM, PL
- PMO(Project Management Office) : 사업 주관기관의 입장에서 운영되며, 프로젝트를 성공적으로 수행하기 위해 프로젝트 전체 추진단계 및 전 분야를 총괄 관리하는 사업관리 전문조직.
- PM(Project Manager) : 프로젝트의 모든 책임을 지는 사람. PM은 조직의 외부와 조직을 매개해주는 역할. 외적으로는 대표하여 협상이나 회의를 하며 내적으로는 스케쥴, 리소스 조달, 품질에 대한 지휘를 한다.
- PL(Project Leader) : PM이 외부로의 대표자라면, PL은 내부에서의 인솔자. 업무의 분담, 작업지시, 리소스 배분, 문제 해결방안의 도출 등의 역할을 기대받는다. 

## batch, daemon 
- daemon : 데몬은 사용자가 직접적으로 제어하지 않고, 백그라운드에서 돌면서 여러 작업을 하는 프로그램을 말한다. 시스템 로그를 남기는 syslogd처럼 보통 데몬을 뜻하는 'd'를 이름 끝에 달고 있으며, 일반적으로 프로세스로 실행된다. 데몬은 대개 부모 프로세스를 갖지 않으며, 즉 PPID가 1이다. 따라서 프로세스 트리에서 init 바로 아래에 위치한다. 데몬이 되는 방법은 일반적으로 자식 프로세스를 fork하여 생성하고 자식을 분기한 자신을 죽이면서 init이 고아가 된 자식 프로세스를 자기 밑으로 데려가도록 하는 방식이다. 이러한 방법을 'fork off and die'라 부르기도 한다. 시스템은 시동할 때 데몬을 시작하는 경우가 많으며, 이런 데몬들은 네트워크 요청, 하드웨어 동작, 여타 프로그램에 반응하는 기능을 담당하게 된다. 그 밖에도 몇몇 리눅스에 있는 devfsd처럼 하드웨어 설정이나, cron처럼 주기적인 작업을 실행하는 등 기타 다양한 목적으로 사용된다.
- batch : batch processing(일괄 처리)란 컴퓨터 프로그램 흐름에 따라 순차적으로 자료를 처리하는 방식을 뜻한다. 초기의 일괄처리 방식은 사용자와 상호작용하는 것이 불가능했지만, 운영 체제가 발전함에 따라 프로그램 입출력을 통해 상호작용하는 것이 가능해졌다. 개별적으로 어떤 요청이 있을 때마다 실시간으로 통신하는 것이 아닌 한꺼번에 일괄적으로 대량 건을 처리하는 것이다. 배치는 보통 정해진 특정한 시간에 실행된다.
