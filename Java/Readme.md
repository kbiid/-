## Java 버전별 특징

# Java8
- 람다 표현식(lambda expression) : 함수형 프로그래밍
- 스트림 API(stream API) : 데이터의 추상화
- java.time 패키지 : Joda-Time을 이용한 새로운 날짜와 시간 API
- 나즈혼(Nashorn) : 자바스크립트의 새로운 엔진

- 출처 : http://tcpschool.com/java/java_intro_java8

# Java9
- Java Jigsaw : 유연한 런타임 이미지를 만들 수 있도록 Java 플랫폼을 묘듈화 하기 위한 것.
- 출처 : https://greatkim91.tistory.com/197
- 이외의 특징들 : https://medium.com/@goinhacker/java-9%EC%9D%98-%EB%B3%80%ED%99%94%EC%99%80-%ED%8A%B9%EC%A7%95-%EB%8C%80%EC%B6%A9-%EC%A0%95%EB%A6%AC-fca77cee88f2

# Java10
- Local-Variable Type Inference : 로컬변수 선언을 var를 이용하여 선언 가능
- 출처 : https://itstory.tk/entry/Java-10-%EC%8B%A0%EA%B7%9C-%EA%B8%B0%EB%8A%A5%ED%8A%B9%EC%A7%95-%EC%A0%95%EB%A6%AC

## 오라클 JDK vs Open JDK
- 폐쇄적인 상업코드 기반의 Oracle JDK. 오픈 소스 기반의 Open JDK
- Oracle JDK는 Open JDK에 없는 재산권이 걸린 플러그인 제공. 해당 플러그인은 Oracle이 재산권 보유.
- Oracle JDK만 존재하는 대표적 기능 -> 글꼴 라이브러리, Java Web Start
- https://jsonobject.tistory.com/395

## 얕은 복사 vs 깊은 복사
- Shallow copy : 배열이나 객체를 복사할 때 단순히 참조만 복사하는 것으로써 원본이 변경되면 복사본도 같이 변경됨.
- Deep copy : 데이터만 복사하고 주소는 달라서 값을 변경해도 영향을 주지 않는다.

## 1부터 100까지 더하는 방식?
- 반복문
- 재귀함수
- intstream : IntStream.rangeClosed(1, 99).sum()
