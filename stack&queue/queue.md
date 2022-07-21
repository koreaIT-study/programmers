# 큐(Queue)란
Queue는 사전적으로 "줄을 서다"라는 의미이다. 줄을 서서 기다린다는 것처럼 먼저 들어오면 데이터가 먼저 나가는 형식이다
일명 FIFO(FirstInFirstOut) 방식
반대로 Stack은 LIFO방식이라 두 개가 많이 비교된다

![image](https://user-images.githubusercontent.com/93892965/180133888-119010a3-98b9-4c6c-80d2-205236aeef42.png)


# 큐 선언방법
사용 방법은 Queue를 선언해서 사용하면 된다. 제네릭 부분에서는 사용할 객체를 담으면 된다.
```java
  import java.util.Queue;	//import 하기
  Queue<String> queue = new LinkedList<String>();  //String 형 Queue 선언
  Queue<String> queue1 = new LinkedList<Integer>(); // Integer타입으로 선언
  Queue<String> queue2 = new LinkedList<>(); // new부분 타입 생략 가능
  Queue<String> queue3 = new LinkedList<String>(Arrays.asList('a', 'b', 'c')); // 선언과 동시에 초기값 세팅
```
자바에서는 Queue를 선언할 때 LinkedList로 생성을 해줘야 한다.
때문에 LinkedList를 사용하기 때문에 Queue와 LinkedList를 모두 import해줘야 한다.

# 큐의 기본 함수

### Queue 추가 - add
```java
  import java.util.LinkedList;
import java.util.Queue;

public class Study_Queue {
	public static void main(String[] args)  {
		Queue<String> queue = new LinkedList<String>();
		
		// 값 추가
		queue.add("Hello");
		queue.add("World");
		
		System.out.print(queue); // 결과 출력
	}
}
```
Queue의 값을 추가하는 방법은 add() 메서드로 add(Object)로 값을 추가한다.
데이터가 뒤에서부터 차례대로 들어오기 때문에 출력값은 [Hello, World]로 출력된다. 

### Queue 삭제 - poll, remove
```java
import java.util.LinkedList;
import java.util.Queue;

public class Study_Queue {
	public static void main(String[] args)  {
		Queue<String> que = new LinkedList<String>();
		
		// 값 추가
		que.add("Hello");
		que.add("World");
		que.add("Im");
		que.add("Seong");
		que.add("Hun");
		
		System.out.println(que); // 결과 출력 -> [Hello, World, Im, Seong, Hun]
		
		que.poll(); // 맨 앞의 값 삭제

		System.out.println(que); // 결과 출력 -> [World, Im, Seong, Hun]
		
		que.remove(); // 맨 앞의 값 삭제

		System.out.println(que); // 결과 출력 -> [Im, Seong, Hun]

		que.remove("Seong"); // 해당하는 값 삭제

		System.out.println(que); // 결과 출력 -> [Im, Hun]

		que.clear(); // Index의 값 삭제

		System.out.println(que); // 결과 출력 -> []
	}
}
```
Queue의 값을 삭제하는 방법은 여러 가지가 있다. 기본적으로 poll()과 remove() 메서드를 사용한다
poll()에서는 대기열이 비어있다면 null을 반환하고 remove()에서는 대기열이 비어있으면 NoSuchElement 에러를 리턴한다

remove(Object)를 하게 되면 Object에 해당하는 값을 삭제한다. 대신 Object가 두개라면 더 앞에 있는 값을 삭제한다

clear() 함수는 Queue의 값을 모두 삭제하고 초기화한다.


### Queue의 크기 구하기 - size
```java
import java.util.LinkedList;
import java.util.Queue;

public class Study_Queue {
	public static void main(String[] args)  {
		Queue<String> que = new LinkedList<String>();
		
		// 값 추가
		que.add("Hello");
		que.add("World");
		que.add("Im");
		que.add("Seong");
		que.add("Hun");
		
		System.out.println(que.size()); // 결과 출력 -> 5
  }
}
```
size()함수는 해당 Queue의 데이터의 갯수를 int로 리턴해준다

### Queue의 값 출력하기 - peek
```java
import java.util.LinkedList;
import java.util.Queue;

public class Study_Queue {
	public static void main(String[] args)  {
		Queue<String> que = new LinkedList<String>();
		
		// 값 추가
		que.add("Hello");
		que.add("World");
		que.add("Im");
		que.add("Seong");
		que.add("Hun");
		
		System.out.println(que.peek()); // 결과 출력 -> Hello
    
    		/* Iterator 클래스를 사용하여 값 출력 */
		Iterator iter = que.iterator();
		while(iter.hasNext())
			System.out.print(iter.next() + " ");  // 결과 출력 -> Hello World Im Seong Hun
  }
}
```
Queue에서의 peek은 Stack과 다르게 맨 처음 넣은 값을 반환한다. (선입선출)
또한 모든 값을 출력하고 싶다면 Iterator 클래스를 사용하여 출력해야 한다.
