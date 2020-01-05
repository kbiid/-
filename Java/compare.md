## Interface Comparable
- 정의 
<ul>
  <li>정렬 수행 시 기본적으로 적용되는 정렬 기준이 되는 메서드를 정의하는 인터페이스</li>
  <li>package: java.lang.Comparable : Java에서 제공되는 정렬이 가능한 클래스들은 모두 Comparable 인터페이스를 구현하고 있으며, 정렬 시에 이에 맞게
  정렬이 수행된다. ex) Integer,Double클래스 : 오름차순 정렬. String 클래스 : 사전순 정렬</li>
</ul>

- 구현 방법
<ul>
  <li>정렬할 객체에 Comparable interface를 implements 후, compareTo() 메서드를 오버라이드하여 구현한다.</li>
  <li>compareTo() 메서드 작성법 
    <ol>
      <li>현재 객체 < 파라미터로 넘어온 객체 : 음수 리턴</li>
      <li>현재 객체 == 파라미터로 넘어온 객체 : 0 리턴</li>
      <li>현재 객체 > 파라미터로 넘어온 객체 : 양수 리턴</li>
      <li>음수 또는 0이면 객체의 자리가 그대로 유지되며, 양수인 경우에는 두 객체의 자리가 바뀐다.</li>
    </ol>
  </li>
</ul>

- 사용 방법 : Arrays.sort(array), Collections.sort(list)

## Arrays.sort()와 Collections.sort()의 차이
- Arrays.sort()
<ul>
  <li>배열 정렬의 경우</li>
  <li>Object Array : 새로 정의한 클래스에 대한 배열 *Primitive Array에서는 Dual Pivot QuickSort(Quick Sort + Insertion Sort)를 사용</li>
  <li>Primirie Array : 기본 자료형에 대한 배열</li>
</ul>

- Collections.sort() : List Collection 정렬의 경우. ex) ArrayList, LinkedList, Vector 등 * 내부적으로 Arrays.sort()를 사용

## Interface Comparator
- 정의 
<ul>
  <li>정렬 가능한 클래스(Comparable 인터페이스를 구현한 클래스)들의 기본 정렬 기준과 다르게 정렬 하고 싶을 때 사용하는 인터페이스</li>
  <li>package : java.util.Comparator : 주로 익명 클래스로 사용된다. 기본적인 정렬 방법인 오름차순 정렬을 내림차순으로 정렬할 때 많이 사용한다.</li>
</ul>

- 구현 방법
<ul>
  <li>Comparator interface를 implements 후 compare() 메서드를 오버라이드한 myComparator class를 작성한다.</li>
  <li>compare() 메서드 작성법
    <ol>
      <li>첫 번째 파라미터로 넘어온 객체 < 두 번째 파라미터로 넘어온 객체 : 음수 리턴</li>
      <li>첫 번째 파라미터로 넘어온 객체 == 두 번째 파라미터로 넘어온 객체 : 0 리턴</li>
      <li>첫 번째 파라미터로 넘어온 객체 > 두 번째 파라미터로 넘어온 객체 : 양수 리턴</li>
    </ol>
  </li>
  <li>음수 또는 0이면 객체의 자리가 그대로 유지되며, 양수인 경우에는 두 객체의 자리가 변경된다.
    <ul>
      <li>즉, Integer.compare(x,y)(오름차순 정렬)와 동일한 개념이다. -> return (x < y) ? -1 : ((x==y) ? 0 : 1);</li>
      <li>내림차순 정렬의 경우 두 파라미터의 위치를 바꿔준다. -> Integer.compare(y,x)(내림차순 정렬)</li>
    </ul>
  </li>
</ul>

- 사용 방법
<ul>
  <li>Arrays.sort(array, myComparator)</li>
  <li>Collections.sort(list,myComparator)</li>
  <li>Arrays.sort(), Collections.sort() 메서드는 두 번째 인자로 Comparator interface를 받을 수 있다.</li>
</ul>

- 두 번째 인자로 Comparator interface를 받는 경우 : 우선 순위 큐(PriorityQueue) 생성자의 두 번째 인자로 Comparator interface를 받을 수 있다.
<ul>
  <li>PriorityQueue(int initialCapacity, Comparator<? super E> comparator) </li>
  <li>지정된 Comparator의 정렬 방법에 따라 우선 순위를 할당한다.</li>
</ul>

출처 : https://gmlwjd9405.github.io/2018/09/06/java-comparable-and-comparator.html
