## 스프링이란?
- 자바 엔터프라이즈 개발을 편하게 해주는 오픈소스 경량급 애플리케이션 프레임워크
  <ul>
    <li>애플리케이션 프레임워크 : 일반적으로 라이브러리나 프레임워크는 특정 업무 분야나 한 가지 기술에 특화된 목표를 가지고 만들어진다. 하지만 스프링은 이와 다르게 '애플리케이션 프레임워크'라는 특징을 갖고 있다. 애플리케이션 프레임워크는 특정 계층이나, 기술, 업무 분야에 국한되지 않고 애플리케이션의 전 영역을 포괄하는 범용적인 프레임워크를 말한다. 애플리케이션 개발의 전 과정을 빠르고 편리하며 효율적으로 진행하는데 일차적인 목표를 두는 프레임워크이다.</li>
    <li>경량급 : EJB가 동작하기 우해서 고가의 느리고 무거운 자바 서버(WAS)가 필요한 것과는 달리, 스프링은 가장 단순한 서버환경인 톰캣(Tomcat)인 제티(Jetty)에서도 완벽하게 동작한다. 단순한 개발툴과 기본적인 개발환경으로도 엔터프라이즈 개발에서 필요로 하는 주요한 기능을 갖춘 애플리케이션을 개발하기에 충분하다. 스프링의 장점은 가볍고 단순한 환경에서도 복잡한 EJB와 고가의 WAS를 갖춰야만 가능했던 엔터프라이즈 개발의 고급 기술을 대부분 사용할 수 있다는 점이다. 만들어진 코드가 지원하는 기술수준은 비슷하더라도 그것을 훨씬 빠르고 간편하게 작성하게 해줌을써 생산성과 품질 면에서 유리하다는 것이 스프링의 특징이다.</li>
    <li>자바 엔터프라이즈 개발을 편하게 : 스프링은 애플리케이션 개발자들이 스프링이라는 프레임워크가 제공하는 기술이 아니라 자신이 작성하는 애플리케이션의 로직에 더 많은 관심과 시간을 쏟게 해준다. 초기에 스프링의 기본 설정과 적용 기술만 잘 선택하고 준비해두면, 이후로 애플리케이션 개발 중에는 스프링과 관련된 코드나 API에 대해 개발자가 신경 쓸 일이 없다. 엔터프라이즈 개발에서 필연적으로 요구되는 기술적인 요구를 충족하면서도 개발을 복잡하게 만들지 않는다는 점이 스프링의 뛰어난 면이다.</li>
    <li>오픈소스 : 스프링에 적용된 오픈소스 라이선스는 비교적 제약이 적고 사용이 매우 자유로운 편인 아파치 라이선스 버전 2.0(Apache)이다.</li></ul> 

## 스프링의 특징
<ul>
  <li>경량(Light-weighted) : 크기와 부하 측면에서 독립된 몇 개의 jar 파일로 구성되어 있기 때문에 설치가 용이하며 POJO를 사용한다.</li>
  <li>IoC 패턴 : 객체 사이의 의존관계를 코드로 구현하지 않고 Framework에 의해 주입받는다.(Dependency Injection)</li>
  <li>AOP(Aspect Of Control) : 핵심 로직 개발 시 Transaction 지원이나 Loggin, Security 등 시스템 적 관심사에 신경쓸 필요가 없다.</li>
  <li>Transaction 관리 : Java Object 들에 대한 트랜잭션을 지원하지만 결코 J2EE와 같은 환경에 얽매이지 않는다.</li>
  <li>Container : Application 객체의 Life cycle과 객체들 간 의존관계를 컨테이너 형태로 관리한다. Servlet Container와 Spring container의 차이점은 특정 WAS. 벤더에 종속적이지 않으면서 자유로운 확장이 가능하다는 것이다.</li>
  <li>Framework : 간단한 컴포넌트 만으로도 Application 구성이 가능하다. xml 설정 파일 상의 선언적인 구성도 가능하다.</li>
  <li>Integration : Container 구조 덕분에 다른 프레임워크들과 결합이 쉽다. 특히 IBATIS, Hibernate 등과의 결합은 공식과도 같다.</li>
</ul>

## 스프링의 핵심
<ul>
  <li>POJO : Plain Old Java Object.</li>
  <li>DI : Dependency Injection</li>
  <li>AOP</li>
  <li>PSA : Portable Service Abstractions</li>
</ul>

## POJO
- 진정한 POJO란 객체지향적인 원리에 충실하면서, 환경과 기술에 종속되지 않고 필요에 따라 재활용될 수 있는 방식으로 설계된 오브젝트를 말한다. 그런 POJO에 애플리케이션의 핵심 로직과 기능을 담아 설계하고 개발하는 방법을 POJO프로그래밍이라고 할 수 있다.
- POJO의 조건
  <ul><li>특정 규약(Contract)에 종속되지 않는다 : POJO는 자바 언어와 꼭 필요한 API 외에는 종속되지 않아야 한다. 따라서 EJB2와 같이 특정 규약을 따라 비즈니스 컴포넌트를 만들어야 하는 경우는 POJO가 아니다. 특정 규약을 따르는 경우 특정 클래스를 상속하도록 요구한다. 그럴 경우 자바의 단일 상속 제한 때문에 해당 클래스에 객체지향적인 설계 기법을 적용하기가 어려워지는 문제가 생긴다. 또 규약이 적용된 환경에 종속적이라 다른 환경으로 이전이 힘들다. 규약에 종속되지 않아야 하고, 객체지향 설계의 자유로운 적용이 가능한 오브젝트여야만 POJO라고 할 수 있다.</li>
  <li>특정 환경에 종속되지 않는다 : 순수한 애플리케이션 로직을 담고 있는 오브젝트 코드가 특정 환경에 종속되게 만들거나 애노테이션이나 엘리먼트 값에 특정 기술과 환경에 종속적인 정보를 담고 있다면 POJO라고 할 수 없다.</li></ul>
- POJO의 장점
  <ul>
  <li>특정한 기술과 환경에 종속되지 않는 오브젝트는 코드가 깔끔해진다.</li>
  <li>매우 유연한 방식으로 원하는 레벨에서 코드를 빠르고 명확하게 테스트할 수 있다.</li>
  <li>객체지향적인 설계를 자유롭게 적용할 수 있다.</li>
  </ul>
## 버전별 특징
<ul>
  <li>Spring 3.0 : Spring 3.0부터 Java5가 지원된다. 기존에 유지하던 하위호환성에 Generic이나 가변인자(varargs) 등과 같은 개선사항이 추가된다.
    <ul><li>전체 프레임워크를 하나의 spring.jar 파일로 제공하던 부분을 여러개의 jar 파일로 나누어 제공한다.</li>
      <li>SPEL(Spring Expression Language)가 도입되었다.</li>
      <li>Rest API에 대한 지원이 추가되었다.</li>
      <li>OXM(Object Xml Mapping) 기능이 추가되어 설정을 Xml형태로 할 수 있게 지원한다.</li>
      <li>Java annotation을 이용해서 DI의 지원이 가능하다.</li></ul></li>
  <li>Spring 4.0 : Java 8의 특징들을 적용할 수 있게 지원한다.
    <ul><li>Starter Pack이 생겨서 초보 개발자들에게 큰 진입장벽인 POM 설정을 도와준다.</li>
    <li>기존에 사용하지 않지만 호환성을 위해 남겨져있던 Deprecated Package들이 제거되었으며 Hibernate 3.6이상, EhCache 2.1 이상, Groovy 1.8이상, Joda-Time 2.0 이상 등 새로운 Dependency 들에 대해 지원한다.</li>
    <li>Java6, Java7, Jva8의 고유 기능들에 대해 지원한다. 람다식, Optional, Callback Interface 등의 기능을 Spring framework 레벨에서 사용할 수 있다.</li>
    <li>Java EE 6, 7에 대해 고려되어 있다. JPA 2.0과 Servlet 3.0에 대한 지원이 포함되어 있다는 뜻이다.</li>
    <li>Groovy를 이용한 Bean 설정이 가능하다. GroovyBeanDefinitionReader 문서를 참조할 것.</li>
    <li>Core 컨테이너들의 기능 지원이 확대되어있다. 먼저 Repository 들이 좀 더 쉽게 Inject될 수 있으며, 각종 Metadata Annotation들을 이용한 Custom Annotation 작성이 가능하다. @Lazy를 이용한 Lazy Injection이나 @Order을 통한 Interface, @Profile을 통한 프로필 버전 관리가 쉬워졌다.</li>
    <li>Web을 개발하기 위한 도구들이 생겼다. @RestController 같은 것들이 그것이다.</li>
    <li>Web Socket이나 STOMP등의 프로토콜을 같이 지원한다.</li>
    <li>테스트 환경이 개선되었다. Framework 레벨에서 Mock을 위한 ServletContext를 별도로 지원한다.</li></ul></li>
  <li>Spring5.0 : JDK 8+,9 등에 대해서 지원하며 Java8을 표준으로 사용한다.
  <ul><li>코어로직에 있어서 JDK 8의 특징들이 강화되었다.</li>
    <li>HTTP 메시지 코덱의 XML과 JSON 지원에 대한 구현이 Encoder와 Decoder의 사용을 통해 추상화 되었다.</li>
    <li>웹에 대한 지원이 향상되었다. 특히 Protobuf3.0지원이 적용되었다.</li>
    <li>https://atin.tistory.com/626</li></ul></li>
</ul>

## Annotation
- https://gmlwjd9405.github.io/2018/12/02/spring-annotation-types.html

## 참고
- https://12bme.tistory.com/157
