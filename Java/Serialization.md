## Serialization
- 직렬화란? : 자바 시스템 내부에서 사용되는 Obejct 또는 Data를 외부의 자바 시스템에서도 사용할 수 있도록 byte 형태로 데이터를 변환하는 기술. JVM의 메모리에 상주(힙 또는 스택)되어 있는 객체 데이터를 바이트 형태로 변환하는 기술
- 역직렬화(Deserialization) : byte로 변환된 Data를 원래대로 Obejct나 Data로 변환하는 기술을 역직렬화라고 부른다. 직렬화된 바이트 형태의 데이터를 객체로 변환해서 JVM으로 상주시키는 형태.

## 직렬화 조건
- 자바 기본(primitive) 타입과 java.io.Serializable 인터페이스를 상속받은 객체는 직렬화 할 수 있는 기본 조건을 가진다.
- 자바 직렬화는 java.io.ObjectOutputStream 객체를 이용한다.
