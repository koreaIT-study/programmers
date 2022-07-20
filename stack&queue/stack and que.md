# 스택(Stack) 이란

사전적 의미로는 '쌓다', '더미'라는 뜻이다. 스택을 흔히 후입선출(선출후입), LIFO 라고 부르는데 
쉽게 설명하자면 아래가 막힌 어떤 물체를 생각하시면 된다. 쓰레기통, 마트용 음료수 진열대 등 이러한 것이 스택 구조다. 
즉 한 쪽 끝에서만 자료(데이터)를 넣고 뺄 수 있는 형식의 자료 구조 입니다. 스택을 실제 개발환경에서 사용 하는 경우는 
인터넷 브라우저의 '뒤로가기', '앞으로가기' 버튼을 생각 하면 된다. 따라서 Stack은 데이터를 쌓는 형식으로 저장하는데 
따라서 조회, 추가, 삭제 모두 가장 위에 있는 즉 가장 최근의 값에서 이루어 진다. 스택 구조에서 가장 상단에 있는 데이터를 Top이라고 한다.

# 스택 선언방법

사용 방법은 Stack을 선언해서 사용하면 된다. 제네릭 부분에는 사용할 객체를 담으면 된다.

```java
import java.util.Stack;	//import 하기
Stack<String> stack = new Stack<>();	//String 형 Stack 선언
```

# 스택의 기본 함수

 먼저 Stack에 대해 설명을 했듯이, 들어오는 것만 값을 입력하고, 삭제는 값을 입력하지 않는다.
제일 마지막에 들어온 값이 제일 먼저 나가기 때문이다.

### Stack 추가 - push
```java
import java.util.stack;

public class Study_Stack {
  public static void main (String[] args) {
    Stack<Integer> stack = new Stack<>();
    
    stack.push(1);
    stack.push(10);
    stack.push(30);
    
    System.out.println(stack.toString());
  }
}
```
1, 10, 30 순서로 stack에 추가하였다.
System.out.println으로 출력할 때, stack에 순서대로 등록되어 [1, 10, 30]으로 출력된다.


### Stack 삭제 - pop
```java
import java.util.stack;

public class Study_Stack {
  public static void main (String[] args) {
    Stack<Integer> stack = new Stack<>();
    
    // 입력
    stack.push(1);
    stack.push(10);
    stack.push(30);
    
    // 삭제
    stack.pop();
    System.out.println(stack.toString());
  }
}
```
pop을 선언하면 제일 마지막에 등록된 30이 삭제된다.
이는 Stack의 구조대로 마지막 선언 값이 제일 먼저 사라진 것이다.
System.out.println으로 출력할 때, stack에 순서대로 등록되어 [1, 10]으로 출력된다.

### Stack 전체 삭제 - clear
```java
import java.util.stack;

public class Study_Stack {
  public static void main (String[] args) {
    Stack<Integer> stack = new Stack<>();
    
    // 입력
    stack.push(1);
    stack.push(10);
    stack.push(30);
    
    // 전체 삭제
    stack.clear();
    System.out.println(stack.toString());
  }
}
```
Stack의 값을 모두 지운다.
Stack의 값이 많을 경우, 한 번에 비우는 방법은 clear함수를 이용하면 된다

### Stack의 마지막 값 확인 - peek
```java
import java.util.stack;

public class Study_Stack {
  public static void main (String[] args) {
    Stack<Integer> stack = new Stack<>();
    
    // 입력
    stack.push(1);
    stack.push(10);
    stack.push(30);
    
    // 마지막 입력값 확인
    System.out.println(stack.peek());
  }
}
```
peek() 함수는 Stack의 가장 마지막 값을 확인할 수 있다.
또한 pop()으로 삭제하기 전 삭제 대상이 무엇인지 확인이 가능하다.

### Stack의 배열 길이 수 - size
```java
import java.util.stack;

public class Study_Stack {
  public static void main (String[] args) {
    Stack<Integer> stack = new Stack<>();
    
    // 입력
    stack.push(1);
    stack.push(10);
    stack.push(30);
    
    // stack 배열 길이의 수
    System.out.println(stack.size());
  }
}
```
size()함수는 stack에 쌓인 배열 갯수를 return해준다

### Stack이 비어있는지 확인 - isEmpty
```java
import java.util.stack;

public class Study_Stack {
  public static void main (String[] args) {
    Stack<Integer> stack = new Stack<>();
    
    // 입력
    stack.push(1);
    stack.push(10);
    stack.push(30);
    
   
    System.out.println(stack.isEmpty());  // false
    
    // stack 전체 삭재
    stack.clear();
    System.out.println(stack.isEmpty());  // true
    
  }
}
```
stack이 비어있다면 true를 리턴해주고, 있으면 false를 리턴해준다.

### Stack에 일치하는 값이 들어있는지 확인 - contains
```java
import java.util.stack;

public class Study_Stack {
  public static void main (String[] args) {
    Stack<Integer> stack = new Stack<>();
    
    // 입력
    stack.push(1);
    stack.push(10);
    stack.push(30);
    
   
    System.out.println(stack.contains(10);  // true
    
    System.out.println(stack.contains(11);  // false
    
  }
}
```
stack에 매개변수로 보낸 값이 있는지 없는지 확인한 후 값이 포함되어 있다면 true, 없다면 false를 return해준다
