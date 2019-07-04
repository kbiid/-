## Servlet과 JSP의 개념
- Servlet : 웹 기반의 요청에 대한 동적인 처리가 가능한 Server Side에서 돌아가는 Java Program. Java 코드 안에 HTML 코드. 웹 개발을 위해 만든 표준.
- JSP(Java Server Pages) : Java 언어를 기반으로 하는 Server Side 스크립트 언어. HTML 코드 안에 Java 코드.  Servlet를 보완하고 기술을 확장한 스크립트 방식 표준. Servlet의 모든 기능 + 추가적인 기능.

## Servlet과 JSP의 차이
- Servlet
  <ul>
    <li>Java 코드 안에 HTML 코드 (하나의 클래스)</li>
    <li>data processing(Controller)에 좋다.</li>
    <li>DB와의 통신, Business LOgic 호출, 데이터를 읽고 확인하는 작업 등에 유용하다.</li>
    <li>Servlet이 수정된 경우 Java 코드를 컴파일(.class)한 후 동적인 페이지를 처리하기 때문에 전체 코드를 업데이트하고 다시 컴파일한 후 재배포하는 작업이 필요하다.(생산성 저하)</li>
  </ul>
- JSP
  <ul>
    <li>HTML 코드 안에 Java 코드</li>
    <li>presentation(View)에 좋다.</li>
    <li>요청 결과를 나타내는 HTML 작성하는데 유용하다.</li>
    <li>JSP가 수정된 경우 재배포할 필요가 없어 WAS가 알아서 처리한다.(쉬운 배포)</li>
  </ul>
  
  ## Servlet과 JSP의 관계
  - JSP만을 이용하는 모델
    <ul>
      <li>JSP가 사용자의 요청을 받아 Java Bean(DTO,DAO)을 호출하여 적절한 동적인 페이지를 생성한다.</li>
      <li>동작 과정
        <ul>
          <li>JSP로 작성된 프로그램은 내부적으로 WAS에서 Servlet 파일로 변환</li>
          <li>JSP 태그를 분해하고 추출하여 다시 순수한 HTML 웹 페이지로 변환</li>
          <li>클라이언트로 응답</li>
        </ul></li>
      <li>특징
        <ul>
          <li>개발 속도가 빠르다.</li>
          <li>배우기 쉽다.</li>
          <li>프레젠테이션 로직(View)과 비즈니스 로직(Controller)이 혼재한다.</li>
          <li>JSP 코드가 복잡해져 유지 보수가 어려워진다.</li>
        </ul></li>
    </ul>
- JSP와 Servlet을 모두 이용하는 모델(MVC Architecture)
  <ul>
    <li>JSP와 Servlet을 모두 사용하여 프레젠테이션 로직(View)과 비즈니스 로직(Controller)을 분리한다.</li>
    <li>View(보여지는 부분)는 HTML이 중심이 되는 JSP를 사용</li>
    <li>Controller(다른 자바 클래스에 데이터를 넘겨주는 부분)는 Java 코드가 중심이 되는 Servlet을 사용</li>
    <li>Model은 Java Beans로, DTO와 DAO를 통해 Mysql과 같은 Data Storage에 </li>
  </ul>
