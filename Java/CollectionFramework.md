## CollectionFramework
- 자바에서 컬렉션 프레임워크란 다수의 데이터를 쉽고 효과적으로 처리할 수 있는 표준화 된 방법을 제공하는 클래스의 집합을 의미한다. 즉, 데이터를 저장하는 자료 구조와 데이터를 처리하는 알고리즘을 구조화하여 클래스로 구현해 놓은 것이다.
- JDK 1.2부터 컬렉션 프레임워크가 등장하였다. 이전에는 Vector, Hashtable, Properties와 같은 컬렉션 클래스들을 서로 각자 다른 방식으로 처리해야 했다.
- 컬렉션 프레임워크에 속하는 인터페이스를 구현한 클래스를 컬렉션 클래스라고 한다.

## List
- List<E> : 순서가 있는 데이터의 집합으로, 데이터의 중복을 허용한다. 
- 구현 클래스 : Vector, ArrayList, LinkedList, Stack, Queue
<ul>
  <li>ArrayList<E> 클래스 : 가장 많이 사용되는 컬렉션 클래스 중 하나. JDK 1.2부터 제공된 ArrayList 클래스는 내부적으로 배열을 이용하여 요소를 저장한다. 배열을 이용하기 때문에 인덱스를 이용해 배열 요소에 빠르게 접근할 수 있다. 하지만 배열은 크기를 변경할 수 없는 인스턴스이므로, 크기를 늘리기 위해서 새로운 배열을 생성하고 기존의 요소들을 옮겨야 하는 복잡한 과정을 거쳐야 한다. 이 과정은 자동이지만, 요소의 추가 및 삭제 작업에 걸리는 시간이 매우 길어지는 단점을 가진다.</li>
  <li>LinkedList<E> : LinkedList 클래스는 ArrayList 클래스가 배열을 이용하여 요소를 저장함으로써 발생하는 단점을 극복하기 위해 고안. JDK 1.2부터 등장했으며 클래스 내부적으로 연결 리스트를 이용하여 요소를 저장한다.</li>
  <li>Vector<E> : Vector 클래스는 JDK 1.0부터 사용해 온 ArrayList 클래스와 같은 동작을 수행하는 클래스. 현재에는 기존 코드와의 호환성을 위해서만 남아있으므로, Vector 클래스보다는 ArrayList 클래스를 사용하는 것이 좋다.</li>
  <li>Stack<E> : List 컬렉션 클래스의 Vector 클래스를 상속받아, 전형적인 스택 메모리 구조의 클래스를 제공.</li>
  <li>Queue<E> : 클래스로 구현된 스택과는 달리 자바에서 큐 메모리 구조는 별도의 인터페이스 형태로 제공. 하위 인터페이스로 Deqie<E>, BlockingDeque<E>,BlockingQueue<E>,TransferQueue<E> 등이 있다.</li>
</ul>

## Set
- 요소의 저장 순서를 유지하지 않는다. 같은 요소의 중복 저장을 허용하지 않는다.
- 대표적인 Set 컬렉션 클래스 : HashSet<E>, TreeSet<E>
<ul>
  <li>HashSet<E> 클래스 : HashSet 클래스는 Set 컬렉션 클래스에서 가장 많이 사용되는 클래스 중 하나. JDK 1.2부터 제공되었으며 해시 알고리즘을 사용하여 검색 속도가 매우 빠르다. HashSet 클래스는 내부적으로 HashMap 인스턴스를 이용하여 요소를 저장한다. 만약 요소의 저장 순서를 유지하고 싶으면 JDK 1.4부터 제공하는 LinkedHashSet 클래스를 사용하면 된다. HashSet에 이미 존재하는 요소를 추가하려고 하면, 해당 요소를 저장하지 않고 false를 반환한다. -> HashSet에 이미 존재하는 요소인지를 파악하기 위해 다음과 같은 과정을 거친다. 
  <ol><li>해당 요소에서 hashCode() 메소드를 호출하여 반환된 해시값으로 검색할 범위를 결정한다.</li>
  <li>해당 범위 내의 요소들을 equals() 메소드로 비교한다.</li>
  </ol>
  - 따라서 HashSet에서 add() 메소드를 사용하여 중복 없이 새로운 요소를 추가하기 위해서는 hashCode()와 equals() 메소드를 상황에 맞게 오버라이딩해야 한다.</li>
  <li>TreeSet<E> 클래스 : TreeSet 클래스는 데이터가 정렬된 상태로 저장되는 이진 검색 트리(binary search tree)의 형태로 요소를 저장한다. 이진 검색 트리는 데이터를 추가하거나 제거하는 등의 기본 동작 시간이 매우 빠르다. JDK 1.2부터 제공되는 TreeSet클래스는 NavigableSet 인터페이스를 기존의 진 검색 트리의 성능을 향상시킨 레드-블랙 트리(Red-Black Tree)로 구현한다.</li>
</ul>

## Map
- Map 인터페이스는 Collection 인터페이스와는 다른 저장 방식을 가진다. Map 인터페이스를 구현한 Map 컬렉션 클래스들은 키와 값을 하나의 쌍으로 저정하는 방식(key-value방식)을 사용.
- 요소의 저장 순서를 유지하지 않는다. 키는 중복을 허용하지 않지만, 값의 중복은 허용한다.
- 대표적인 Map 컬렉션 클래스 : HashMap<K,V> , Hashtable<K,V> , TreeMap<K,V>
<ul>
  <li>HashMap<K,V> 클래스 : HashMap 클래스는 Map 컬렉션 클래스에서 가장 많이 사용되는 클래스 중 한나. JDK 1.2부터 제공된 HashMap 클래스는 해시 알고리즘을 사용하여 검색 속도가 매우 빠르다.</li>
  <li>Hashtable<K,V> 클래스 : Hashtable<K,V> 클래스는 HashMap 클래스와 같은 동작을 하는 클래스. 현재에는 기존 코드와의 호환성을 위해서만 남아있으므로, Hashtable보다는 HashMap 클래스를 사용하는 것이 좋다.</li>
  <li>TreeMap<K,V> 클레스 : 키와 값을 한 쌍으로 하는 데이터를 이진 검색 트리의 형태로 저장한다. 이진 검색 트리는 데이터를 추가하거나 제거하는 등의 기본 동작 시간이 매우 빠르다. JDK 1.2부터 제공된 TreeMap 클래스는 NavigableMap 인터페이스를 기존의 이진 검색 트리의 성능을 향상시킨 레드-블렉 트리로 구현한다.</li>
</ul>
- SynchronizedMap과 CouncurrentHashMap
<ul>
  <li>Hashtable은 데이터 변경 메서드가 모두 동기화 메서드로 선언되어 있다. 메서드 호출 전에 쓰레드간 동기화 락을 걸기 때문에 멀티 쓰레드 환경에서도 데이터의 무결성을 보장한다. 반면, HashMap은 동기화를 지원하지 않는다. 즉, 여러 쓰레드에서 동시에 HashMap을 접근하게 되면 데이터 무결성이 손상될 수 있다.</li>
  <li>HashTable은 데이터 무결성을 지키기 위한 동기화 때문에 속도가 느리다. 동기화 락 작업은 매우 느린 동작이다. 상대적으로 동기화 처리를 하지 않는 HashMap은 Hashtable에 비해 매우 빠른 처리 속도를 가진다. 그렇기 때문에 데이터 무결성의 우려가 없는 단일쓰레드에서는 HashMap을 사용하는 것이 효율적이다.</li>
  <li>HashMap을 사용하면서 동기화를 해결하기 위해 나온 개념이 SynchronizedMap. 어떤 Map 인터페이스(동기화를 지원하지 않는 Map이라도)를 사용하더라도 SynchonizedMap으로 랩핑하여 주면 해당 Map 객체는 동기화 맵이 된다. -> this.infos = Collections.synchronizedMap<new HashMap<Long,String>());</li>
  <li>JAVA 1.5부터는 ConcurrentUtil이라는 인터페이스를 기본ㄴ으로 제공. JAVA 1.5부터는 멀티 쓰레드 환경에서는 ConcurrentHashMap 클래스를 사용.ConcurrentHashMap은 SynchronizedMap으로 감싸진 HashMap이나 HashTable보다 더 빠른 속도를 보이면서도 쓰레드 간의 동기화를 보장. ConcurrentHashMap은 동기화 시, Map 전체에 동기화 락을 걸지 않고, Map을 여러 조각으로 쪼개어 부분부분 락을 거는 형태로 구현되어 있기 때문.</li>
</ul>

## 참고
- https://ooz.co.kr/71
