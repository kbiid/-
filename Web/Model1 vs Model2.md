<h2>Model1</h2>
- 구조 : 사용자 <-(요청, 응답)-> View + Model(실질적으로 보여지는 페이지 (JSP))
- 장점
<ul>
  <li>개발 기간이 단축(JSP 위주의 단순한 페이지의 흐름)</li>
  <li>팀원의 수준이 높지 않아도 된다. 즉, 초심자도 쉽게 배울 수 있다.</li>
  <li>중,소형 프로젝트에 적합</li>
</ul>
- 단점
<ul>
  <li>웹 어플리케이션이 복잡해질수록 유지보수가 어렵고 힘들다.</li>
  <li>디자이너(퍼블리셔)와 개발자간의 의사소통이 필요하며 중요하다.(비즈니스 로직과 뷰 사이의 구분이 미비하다.)</li>
</ul>

<h2>Model2</h2>
- GUI 개발 모델인 MVC를 웹 어플리케이션에 적용하여 구현한 방식
- Model
  <ul>
    <li>Business Login을 담당. Java Bean으로 구현</li>
    <li>Business Service(Manager) - Business Login의 일의 흐름을 관리</li>
    <li>DAO(Data Access Object) - Database와 연동하는 Business Logic을 처리</li>
  </ul>
- View : Client에게 응답을 처리한다. - JSP 또는 html로 구현
- Controller : 클라이언트의 요청을 받아 Model과 View사이에서 일의 흐름을 조정
- 구조 : Model + Controller + View
- 장점
  <ul>
    <li>비즈니스 로직과 뷰의 분리로 유지보수와 확장이 용이하다</li>
    <li>개발자와 디자이너(퍼블리셔)의 작업이 분리되어 분업이 편리하다</li>
  </ul>
 - 단점
  <ul>
    <li>구조 설계를 위한 시간이 많이 소요되므로 개발 기간이 증가한다</li>
    <li>개발자들이 구조에 대한 이해가 필요하기 때문에 팀원의 높은 수준이 요구된다</li>
  </ul>

<h2>참고 사이트</h2>
- https://coding-factory.tistory.com/69
- https://johnmarc.tistory.com/6
