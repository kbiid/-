<h2>DAO(Data Access Object)</h2>
- DB를 사용해 데이터를 조죄하거나 조작하는 기능을 담당한다. Domain logic(비즈니스 로직이나 DB와 관련없는 코드들)을 persistence mechanism과 분리하기 위해 사용한다.
- persistence layer : Database에 data를 CRUD하는 계층
- 이렇게 따로 분리하는 이유는 HTTP Request를 Web Application이 받게 되면 Thread를 생성하게 되는데 비즈니스 로직이 DB로부터 데이터를 얻어오기 위해 매번 Driver를 로드하고 Connection 객체를 생성하게 되면 엄청 많은 커넥션이 일어나므로 DAO를 하나 만들어 DB 전용 객체로만 쓰는 것이다. 
- 이 개념은 DBCP(Database Connection Pool)로부터 나왔다. WAS(Wep Application Server)가 실행되면 일정량의 DB Connection 객체를 Pool에다 저장해 두고, HTTP Request에 따라 필요할 때마다 Pool에서 Connection 객체를 가져다 쓰고 반환하는 것이다.

<h2>DTO(Data Transfer Object)</h2>
- VO(Value Object)라고도 표현한다. 계층간 데이터 교환을 위한 자바빈즈(Java Beans)이다.
- 이 객체는 데이터베이스의 레코드의 데이터를 매핑하기 위한 데이터 객체를 말한다. DTO는 보통 로직을 가지고 있지 않고, data와 그 data에 접근을 위한 getter,setter만 가지고 있다.
- DTO는 Database에서 Data를 얻어 Service나 Controller 등으로 보낼 때 사용하는 객체를 말한다.

참고사이트
- https://lazymankook.tistory.com/30
