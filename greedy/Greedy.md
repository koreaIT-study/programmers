# Greedy
그리디 알고리즘은 동적 프로그래밍 사용 시 지나치게 많은 일을 한다든 것에서 착안하여 고안된 알고리즘이다.

동적 프로그래밍을 대체하는 것은 아니고 같이 쓰이며 서로 보완하는 개념이다.

그리디 알고리즘은 탐욕 알고리즘 또는 욕심쟁이 알고리즘이라고도 불리는데요. 미래를 생각하지 않고 각 단계에서 가장 최선의 선택을 하는 기법.

각 단계에서 최선의 선택을 한 것이 전체적으로 최선이길 바라는 알고리즘.

<img width="775" alt="스크린샷 2022-07-24 오후 4 13 10" src="https://user-images.githubusercontent.com/82895809/180636602-92d59045-70f5-4c66-a128-f7cdf23d3f67.png">

물론 모든 경우에서 그리디 알고리즘이 통하지는 않는다.

## 탐욕 알고리즘 문제를 해결하는 방법
1. 선택 절차(Selection Procedure): 현재 상태에서의 최적의 해답을 선택한다.
2. 적절성 검사(Feasibility Check): 선택된 해가 문제의 조건을 만족하는지 검사한다.
3. 해답 검사(Solution Check): 원래의 문제가 해결되었는지 검사하고, 해결되지 않았다면 선택 절차로 돌아가 위의 과정을 반복한다.

### 탐욕 알고리즘을 적용하려면 문제가 다음 2가지 조건을 성립하여야 한다.
* 탐욕 알고리즘이 잘 작동하는 문제는 대부분 탐욕스런 선택 조건(Greedy Choice Property)과 최적 부분 구조 조건(Optimal Substructure)이라는 두 가지 조건이 만족된다.
* 탐욕스런 선택 조건은 앞의 선택이 이후의 선택에 영향을 주지 않는다는 것이며, 최적 부분 구조 조건은 문제에 대한 최적해가 부분문제에 대해서도 역시 최적해라는 것이다.

1. 탐욕적 선택 속성(Greedy Choice Property) : 앞의 선택이 이후의 선택에 영향을 주지 않는다.
2. 최적 부분 구조(Optimal Substructure) : 문제에 대한 최종 해결 방법은 부분 문제에 대한 최적 문제 해결 방법으로 구성된다.

* 이러한 조건이 성립하지 않는 경우에는 탐욕 알고리즘은 최적해를 구하지 못한다.
* 하지만, 이러한 경우에도 탐욕 알고맂므은 근사 알고리즘으로 사용이 가능할 수 있으며, 대부분의 경우 계산 속도가 빠르기 때문에 실용적으로 사용할 수 있다.
* 이 경우 역시 어느 정도까지 최적해에 가까운 해를 구할 수 있는지를 보장하려면 엄밀한 증명이 필요하다.
* 어떤 특별한 구조가 있는 문제에 대해서는 탐욕 알고맂므이 언제나 최적해를 찾아낼 수 있다.
* 이 구조를 매트로이드라 한다.
* 매트로이드는 모든 문제에서 나타나는 것은 아니나, 여러 곳에서 발견되기 때문에 탐욕 알고리즘의 활용도를 높여준다.

> 탐욕 알고리즘은 항상 최적의 결과를 도출하는 것은 아니지만, 
> 어느 정도 최적에 근사한 값을 빠르게 도출할 수 있는 장점이 있다. 
> 이 장점으로 인해 탐욕 알고리즘은 근사 알고리즘으로 사용할 수 있다.

> 탐욕 알고리즘을 적용해도 언제나 최적해를 구할 수 있는 문제(매트로이드)가 있고, 
> 이러한 문제에 탐욕 알고리즘을 사용해서 빠른 계산 속도로 답을 구할 수 있다. 
> 그래서 실용적으로 사용할 수 있다.

## 근사 알고리즘(Approximation Algorithm)
* 근사 알고리즘은 어떤 최적화 문제에 대한 해의 근삿값을 구하는 알고리즘을 의미한다.
* 이 알고리즘은 가장 최적화되는 답을 구할 수는 없지만, 비교적 빠른 시간에 계산이 가능하며 어느 정도 보장된 근사핼르 계산할 수 있다.

## 그리디 알고리즘 문제
가장 일반적인 문제의 예는 거스름돈 문제가 있다.

### 거스름돈 문제
> 당신은 음식점의 계산을 도와주는 점원입니다. 
> 카운터에는 거스름돈으로 사용할 500원, 100원, 50원, 10원 동전이 무한개 존재합니다. 
> 손님에게 거슬러 줘야 할 돈이 N원일 때 거슬러주어야 할 동전의 최소 개수를 구하라. 
> 단, 거슬러 줘야 할 돈 N은 항상 10의 배수이다.

이 문제에서 우리가 생각할 수 있는 것은 **'가장 큰 단위의 돈부터 생각하자'** 이다. 

만약 2240원이라는 돈을 거슬러 줘야 한다고 가정하면 이 돈을 거슬러 줄 수 있는 방법은 많다.

```java

    public int solution(int money) {
        int answer = 0;
        int[] change = { 500, 100, 50, 10 };
        int remain = money;
        for (int i : change) {
            answer += remain / i;
            remain = remain % i;
        }
        return answer;
    }
```

그리디 알고리즘을 사용해 답을 찾게 된다면, 그 답이 정당한지 생각해봐야한다.

거스름돈 문제는 가지고 있는 동전 중 '큰 단위'의 동전이 항상 '작은 단위'의 배수이므로 (500 = 100 * 5, 100 = 50 * 2, 50 = 10 * 5) 작은 단위 동전을 조합해 다른 해가 나올 수 없기 때문에 사용할 수 있다.

### 활동 선택 문제
이 문제는 시간표 짜기, 회의실 시간 분배 문제와 비슷한 문제 유형에 해당한다.

활동 선택 문제란, 한 강의실에서 여러개의 수업을 하려고 할 때 한번에 가장 많은 수업을 할 수 있는 경우를 고르는 것이다. (수업 시작 시간, 수업 종료 시간)

* 조건으로는 시작 시간과 끝나는 시간이 같은 경우, 그것도 하나의 수업으로 친다. (3 3, 5 5...)
* 또 수업이 끝나고 바로 다른 수업을 시작할 수 있다. (1 3, 3 5, 5 7)

<img width="774" alt="스크린샷 2022-07-24 오후 5 00 34" src="https://user-images.githubusercontent.com/82895809/180637965-b3ceabf6-cdd1-423f-8804-5df08d3e9fe9.png">

<img width="770" alt="스크린샷 2022-07-24 오후 5 00 43" src="https://user-images.githubusercontent.com/82895809/180637970-68ec7f43-4da6-4e35-b4c4-00a782ca9800.png">

Si는 시작시간, Fi는 종료시간이다. 

수업들은 하나의 강의실에세 진행해야 하므로 2개의 수업이 중복해서 실행 될 수 없다.

이 때 가장 많은 수업을 할 수 있는 경우를 찾아야한다.
(가장 많은 수업을 고르는 것이지 가장 많은 시간을 할 수 있는 경우를 고르는 것이 아니다.)

* 최적해를 구하기 위해서는 가장 빨리 끝나는 수업을 골라야 한다.

결과적으로 보면 a1, a3, a6, a8이나 A1, A3, A7, A9 등을 고르면 정답입니다. 

문제는 이것을 컴퓨터에게 어떻게 고르도록 시키느냐다.

이 문제는 동적 프로그래밍을 통해서도 풀 수 있다. 

하나의 예를 들어 G18을 A1이 종료된 후부터, A8이 시작하기 전 활동들의 집합이라고 보면, 

G18 = {A3, A5, A6, A7} 

이 중에서 최적의 조합(활동들이 겹치지 않고 개수는 최대)을 B18이라고 하면, 

하나의 예로 B18 = {A3, A6}라고 할 수 있다. {A3, A7}도 가능하다.

B18에서 A6를 골랐다고 치면, A6를 고르면 이제 문제는 두 개로 쪼개진다. 

G16과 G68에서 각각 최적인 B16와 B18을 찾는 거다.

이제 B16과 B18의 개수와 A6 1개를 더하면 최적 활동의 개수를 알 수 있다.

이를 식으로 나타내면 C[i,j] = max(C[i,k] + C[k,j] + 1)이 된다. 

C는 집합 Gij의 최적 개수를 나타낸다. 

max는 B18에서 A6 말고 다른 것을 골랐을 때의 경우도 모두 생각해서 그 중 최적을 찾는 거다.

이렇게 동적 프로그래밍으로 할 수도 있지만,(동적 프로그래밍 설명은 다음에....) 

문제는 이렇게 하면 모든 C들을 구해야한다는 것이다.

하지만 우리는 그리디 알고리즘으로 더 효율적으로 풀 수 있다.

직관적으로 생각하면, 최적의 해를 구하기 위해서는 첫 번째 활동이 최대한 일찍 끝나면 된다. 

그래야 다른 활동들을 더 많이 선택할 수 있기 때문이다. 

위의 경우에서는 첫 선택으로 가장 빨리 끝나는 A1을 골라야한다. 

A1을 골랐다면 이제 A2와 A4는 고를 수 없다(A1이랑 겹침). 

그 다음 선택은 다음으로 일찍 끝나는 A3가 될 것이다. 

그 다음은 A6, 마지막은 A8이 되어 최종적으로 {A1, A3, A6, A8}이 된다.

``` javascript
var activity = [[1,1,3], [2,2,5], [3,4,7], [4,1,8], [5,5,9], [6,8,10], [7,9,11], [8,11,14], [9,13,16]];
function activitySelection(act) {
  var result = [];
  var sorted = act.sort(function(prev, cur) {
    return prev[2] - cur[2]; // 끝나는 시간 순으로 정렬
  });
  var last = 0;
  sorted.forEach(function(item) {
    if (last < item[1]) { // 조건 만족 시 결과 집합에 추가
      last = item[2];
      result.push(item);
    }
  });
  return result.map(function(r) {
    return r[0]; // map을 한 이유는 그냥 몇 번째 행동이 선택되었는지 보여주기 위함.
  });
}
activitySelection(activity); // [1, 3, 6, 8]

```

일단 끝나는 시간 순으로 정렬한 후, 반복문을 돌며 집합의 끝나는 시간이 다음 행동의 시작 시간보다 작은 경우 집합에 추가하면 된다.

출처 : https://www.zerocho.com/category/Algorithm/post/584ba5c9580277001862f188

위와 똑같은 다른 설명을 가져왔음.

<img width="476" alt="스크린샷 2022-07-24 오후 5 36 24" src="https://user-images.githubusercontent.com/82895809/180639208-254b3231-ccdf-436e-9cdd-71b9766777e1.png">

위에서 각 활동과 그것들의 시작 / 종료 시간이 설정되어 있는 것을 알 수 있다.

이 문제는 최대한 많은 활동을 해야 하므로 언제 시작하든 전체에서 가장 종료 시간이 빠른 것부터 선택해야 한다.

어차피 시작 시간은 종료 시간 이전이므로 고려하지 않는다.

따라서, 종료 시간을 기준으로 정렬한 뒤, 제일 먼저 끝나는 활동을 무조건 선택하고 끝났을 때, 바로 다음에 선택할 수 있는 활동을 찾아 수행하는 방식을 반복하여 해결할 수 있다.

<img width="727" alt="스크린샷 2022-07-24 오후 5 36 55" src="https://user-images.githubusercontent.com/82895809/180639234-5fd3e6d4-7a60-49d9-ba72-0479ebe80d89.png">

좌측 부터 수행 후 우측 그림과 같이 수행이 완료되어 최종 D - C - A - F 번째 활동을 선택하게 된다.

``` java
public class Main{
    public static void main(String[] args){
        // 활동 정보를 List에 저장하고 정렬한다.
        ArrayList<Action> list = new ArrayList<>();
        list.add(new Action("A", 7, 8));
        list.add(new Action("B", 5, 7));
        list.add(new Action("C", 3, 6));
        list.add(new Action("D", 1, 2));
        list.add(new Action("E", 6, 9));
        list.add(new Action("F", 10, 11));
        Collections.sort(list);
        
        // Greedy 알고리즘 수행 후, 결과 출력
        ArrayList<Action> ans = greedy(list);
        for(Action act : ans){
            System.out.print(act.name + ", ");
        }
    }

    // Greedy 알고리즘을 통해 선택된 활동들을 반환한다.
    private static ArrayList<Action> greedy(ArrayList<Action> list){
        int time = 0;
        ArrayList<Action> ans = new ArrayList<>();

        for(Action act : list){
            if(time <= act.startTime){
                time = act.endTime;
                ans.add(act);
            }
        }
        return ans;
    }
}

// 활동 정보를 가진 Class로 Comparable을 구현하여 종료 시간 기준 오름차순으로 정렬함.
class Action implements Comparable<Action>{
    String name;
    int startTime;
    int endTime;
    public Action(String name, int startTime, int endTime){
        this.name = name;
        this.startTime = startTime;
        this.endTime = endTime;
    }

    @Override
    public int compareTo(Action a) {
        return this.endTime - a.endTime;
    }

    @Override
    public String toString() {
        return this.name;
    }
}

// 결과
// D, C, A, F, 
```
출처 : https://hongjw1938.tistory.com/172

