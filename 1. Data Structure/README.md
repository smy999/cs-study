# Data Structure

- [Array](#Array)
- [LinkedList](#LinkedList)
- [Hash Table](#HashTable)
- [Stack](#Stack)    
- [Queue](#Queue)
- [Graph](#Graph)
- [Tree](#Tree)
- [Graph vs Tree](#Graph-vs-Tree)
- [Heap](#Heap)
- [Red-Black Tree](#RedBlack-Tree)
- [B+ Tree](#B+Tree)
- [참고자료](#)

<br>

# Array

### 1. 개념

- 같은 type의 data를 연속된 메모리 공간에 순차적으로 저장한 선형 자로구조(sequence container)
- data를 하나의 변수에 grouping해서 관리하는 위한 방법으로, 반복문과 함께 사용하면 효율적인 처리가 가능하다.
- 배열의 크기는 고정, 선언 시 배열의 크기를 결정하고 이후 변경할 수 없다.


### 2. 시간 복잡도

- 맨앞/중간에 삽입/삭제: O(n)
- 맨뒤에 삽입/삭제: O(1)
- 탐색: O(1)


### 3. 장단점

| 장점                                    | 단점                                                         |
| --------------------------------------- | ------------------------------------------------------------ |
| index로 data에 빠르게 접근할 수 있다.   | 배열 내의 데이터 이동이 어렵다. 중간에 삽입할 경우 삽입 위치 이후의 모든 원소를 한칸씩 뒤로 밀어야 한다. |
| 연속된 메모리 공간으로 관리가 편리하다. | 연속된 메모리 공간으로 중간 데이터가 삭제되는 메모리가 낭비되는 문제가 발생한다. |
|                                         | 크기 변경이 불가능하다. 이후 새로운 데이터를 추가할 수 없어 새로운 배열을  생성한 후 기존 값을 복사해야 한다. |


### 4. 사용법(Java)

```
// 선언과 함께 초기화
int[] arr = {1, 2, 3, 4};

// 선언 후 값 넣기
int[] arr2 = new int[4];
for(int i = 0; i < arr2.length(); i++) {
  arr2[i] = sc.nextInt();
}
```


### 5. 사용처

- 배열은 데이터의 개수가 확실하게 정해졌을 때, 추가적인 삽입/삭제가 빈번하지 않을 때, 검색을 할 때(index를 사용하여 빠른 검색이 가능) 사용하는 것이 좋다.


<br>


# LinkedList

### 1.  개념

- 서로 다른 곳에 저장된 데이터를 연결한 list 구조
- 배열과는 달리 연속된 메모리를 필요로하지 않고, 빈 공간을 찾아 연결한 후 사용한다. (Array는 물리적으로 연속된 메모리에 저장, list는 논리적인 순서)
- 자료구조 tree에 근간이 되는 자료구조이다.
- 동적으로 메모리를 할당한다.
- 하나의 link에 4byte를 차지하며, double LinkedList는 8byte를 차지한다.



<br>




### 2. 구조

```
[    Head     ]--->[Data][Pointer]--->[Data][Pointer]--->[    Tail     ]
```

![datastructure_linkedlist](https://user-images.githubusercontent.com/33407191/133926712-258dd244-89b7-4a11-b3c1-ff1a84a285a7.png)

- Node: 데이터 저장 단위
- Data: 실제 data를 저장하는 곳
- Pointer(Link): 다음 node의 연결 정보를 저장하는 공간으로 다음 node의 주소값을 가진다.
- Head: LinkedList의 첫 node를 가리킨다.
- Tail: LinkedList의 마지막 node로 Null을 값을 가진다.



<br>



### 4. 종류

![datastructure_linkedlist_type](https://user-images.githubusercontent.com/33407191/147643600-816f469e-c01c-42f7-bc98-0bd09d6bda29.png)

| 구분                                   | 내용                                                         |
| -------------------------------------- | ------------------------------------------------------------ |
| 단일 연결 리스트(Singly Linked List)   | - 각 노드가 다음 노드에 대해서만 참조하는 가장 단순한 형태의 연결 리스트<br>- 일반적인 큐를 구현 시 사용<br>- Head 노드를 잃어버려 참조하지 못하는 경우 데이터 전체를 사용 못하게 되는 단점이 있다.<br>- FAT 파일 시스템이 단일 연결 리스트로 파일 청크(동적 메모리로 할당되는 영역)를 연결한다. |
| 이중 연결 리스트(Doubly Linked List)   | - 각 노드가 이전 노드, 다음 노드에 대해서 참조하는 형태의 연결 리스트<br>- 삭제가 간편하며 단일 연결 리스트에 비해 데이터 손상에 강하지만, 관리할 참조가 2개이기 때문에 삽입이나 정렬의 경우 작업량이 더 많아진다. |
| 원형 연결 리스트(Circular Linked List) | - 연결 리스트에서 마지막 요소가 첫번째 요소를 참조한다.<br>- 스트림 버퍼의 구현에 많이 사용된다. |



<br>




### 3. 시간 복잡도

- 맨 앞/뒤에서 삽입/삭제하는 경우: O(1)
- 중간에 삽입/삭제하는 경우: O(n) = 탐색 시간
- 탐색: O(n)



<br>




### 4. 장단점

| 장점                                                         | 단점                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| data의 삽입/삭제가 편리하다.(해당 부분의 연결을 끊고 새로운 노드에 연결한 후 다음 노드와 연결해준다.) | 특정 데이터를 검색할 때 index로 접근하지 않기 때문에 처음부터 끝까 순회하여 시간이 오래걸린다. |
| 논리적 순서를 갖는 특정으로 메로리를 효율적으로 사용할 수 있다. | Pointer를 저장하는 메모리 공간이 추가적으로 필요하다.        |
| 동적으로 메모리를 할당하여 선언 시 크기를 정하지 않아도 된다. (크기 변경이 가능하다.) | 구현이 어렵다.                                               |

<br>

### 5. 사용법(Java)

```
// 선언
LinkedList list = new LinkedList();           // 타입이 없는 선언
LinkedList<Type> list = new LinkedList<>();   // 타입이 있는 선언

// add
list.addFirtst();
list.addLast();
list.add()
list.add(index, data)

// remove
list.removeFirst();
list.removeLast();
list.remove();        // 명시하지 않으면 0번째 삭제
list.remove(index);
list.clear();

// 크기 구하기
list.size();

// 출력
for(type i : list) Systme.out.print(i);   // for문 사용
Iterator<Type> iter = list.iterator();    // Iterator 사용
while(iter.haNext()) System.out.print(iter.next());

// 검색
list.contains();    // return: boolean
list.indexOf();     // return: index, -1
```



<br>



### 6. 사용처

- 추가와 삭제가 많은 경우에는 Array보다는 LinkedList를 사용한다.
- 대용량 데이터 처리에 적합하다.
- 크기가 정해지지 않은 경우에 사용한다.



<br>

<br>




# HashTable

### 1. 개념

- Hash 함수를 사용하여 변환한 값을 index 삼아 key와 value(data) 쌍을 저장하는 자료구조이다.
- 각각의 key 값에 hash 함수를 적용하여 고유 index를 상성한 후, 이 index를 사용하여 값을 저장하고나 검색한다.
- 이때, 실제 값이 저장되는 곳을 bukets 혹은 slot이라고 한다.
- 기본연산으로 search, insert, delete가 있다.
- Hash 함수의 특성상 다른 문자열의 hasing 결과가 같을 수 있다. 이런 경우를 hash collision이라고 한다.



### 2. 구조

![datastructure_hashtable](https://user-images.githubusercontent.com/33407191/148777138-b9cabcbd-d94c-4fde-88d1-e0197fbc9e25.png)

| 구분                    | 내용                                                         |
| ----------------------- | ------------------------------------------------------------ |
| Key                     | 길이가 일정하지 않은 Hash 함수의 입력값(= 매핑전 원래 데이터 값)공간 복잡도가 커진다. |
| Hash                    | 데이터를 다루는 기법                                         |
| Hash Function           | key를 hash value로 변경하는 역할. 일정하지 않은 길이를 가진 key를 고정된 길이의 데이터로 매핑하여 저장해 저장소를 효율적으로 관리할 수 있다. 하지만 다른 문자열의 hasing 결과가 같아서 나는 문제인 hash collision이 발생할 수 있다. 따라서 hash function를 만들 때 충돌을 최소화하는 방법을 찾아야 한다.해시 함수 의존도가 크며, 해시 함수로 인해 추가 연산이 필요하다. |
| Hash Value(= Hash Code) | 해시 함수에 의해 반환된 데이터의 고유 숫자 값(= 변환된 Key 값) |
| Value                   | 최종적으로 저장되는 값. bucket과 slot에 저장되며, key-value 쌍으로 key에 매칭되어 기본 연산 접근이 가능하다. |




### 3. 시간 복잡도

- 평균: O(1)

  (Hash Table의 index는 데이터의 고유한 위치이기 때문에 삽입 삭제 시 다른 데이터를 채울 필요가 업다.(= 데이터 이동이 없다.))

- 데이터가 충돌한 경우: O(n), 모든 저장소를 검색해야 한다.




### 4. 장단점

| 장점                                                         | 단점                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 적은 자원으로 많은 데이터 관리 가능<br>(HDD 저장소나 클라우드에 존재하는 수많든 데이터를 유한한 Hash 값으로 매핑하여 작은 크기의 메모리로 프로세스 관리가 가능) | 충돌에 주의해야 한다.                                        |
| Index를 사용하여 검색/삽입/삭제가 빠르다.                    | 공간 복잡도가 커진다.                                        |
| Key를 hashing 하는 과정에서 보안성이 올라간다.               | 순서가 있는 배열에는 맞지 않는다.                            |
| 중복을 제거에 유리하다.                                      | 해시 함수 의존도가 크며, 해시 함수로 인해 추가 연산이 필요하다. |





### 5. Hash Collision(해시 충돌)

![datastructure_hashtable_collision](https://user-images.githubusercontent.com/33407191/148777159-9c4f8394-a2b2-4b07-8ad1-321c4d35add5.png)

Hash Function의 서로 다른 입력값의 결과가 같을 때 즉, 결과 값이 중복될 때 hash collision이라고 한다.

Hash Collision을 해결하는 방법은 크게 2가지가 있다.

1. 분리 연결법(Seperate Chaining)
2. 개방 주소법(Open Addressing)



#### 5-1. 분리 연결법(Separate Chaining)

![datastructure_hashtable_seperatechaining](https://user-images.githubusercontent.com/33407191/148777200-5b07203f-0721-4332-9482-eff269f43c87.png)

분리 연결법은 동일한 버킷의 데이터에 대해 자료구조를 활용해 메모리를 추가하여 다음 데이터의 주소를 저장하는 것이다.

Linked List 혹은 Tree(Red-Black Tree)를 사용하는 방법으로 데이터가 6개 이하라면 Linked List를, 8개 이상이면 Tree를 사용한다.

위 그림처럼 인덱스에서 충돌이 일어났을 때 인덱스가 가리키는 linked list에 node를 삽입한다.

분리 연결법은 Linked List 구조이기 떄문에 추가할 수 있는 데이터의 제약이 적다.

해당 방법은 JDK 내부(Java8의 Hash테이블은 Self-Balancing Binary Search Tree 자료구조를 사용해 Chaining 방식을 구현)에서도 사용한다.



#### 5-2. **개방 주소법(Open Addressing)**

![datastructure_hashtable_openaddressing](https://user-images.githubusercontent.com/33407191/148777226-f54b6663-6910-4abc-8563-ebe02785af70.png)

개방 주소법은 분리 연결법과 다르게 비어있는 해시 테이블의 공간을 활용한다. 개방 주소법을 활용하는 대표적인 방법에는 3가지가 존재한다.

1. Linear Probing: 현재의 버킷 index로부터 고정폭 만큼씩 이동하여 차례대로 검색해 비어 있는 버킷에 데이터를 저장한다.

2. Quadratic Probing: 해시의 저장순서 폭을 제곱으로 저장하는 방식이다. 예를 들어 처음 충돌이 발생한 경우에는 1만큼 이동하고 그 다음 계속 충돌이 발생하면 2^2, 3^2 칸씩 옮기는 방식이다.

3. Double Hashing Probing: 해시된 값을 한번 더 해싱하여 해시의 규칙성을 없애버리는 방식이다. 해시된 값을 한번 더 해싱하여 새로운 주소를 할당하기 때문에 다른 방법들보다 많은 연산을 하게 된다.



리사이징(Resizing)?

Open Addressing은 고정 크기의 배열을 사용한다. 따라서 데이터를 더 넣기 위해서는 배열을 확장해야한다. 이것을 리사이징이라고 한다.

확장시 평균 2배로 확장하며, 전체 버켓의 75%가 저장되면 확장한다. 배열의 특성상 확장된 크기의 배열을 만든 후, 기존 배열을 복사한다.



### 6. **HashTable vs HashMap**

| 구분                     | HashTable   | HashMap                     |
| ------------------------ | ----------- | --------------------------- |
| 동기화 여부(thread-safe) | O           | X                           |
| Key의 null 값 허용 여부  | X           | O                           |
| Return type              | Enumeration | Fail-Fast(or safe)-Iterator |

(Thread-Safe? 여러 스레트가 하나의 자원을 사용하려할 때, 사용하려는 스레드 하나를 제외한 나머지 스레드들이 자원을 사용하지 못하는 것.)





<br>

<br>



# Stack



### 1.  개념

Stack? 쌓아 올리다.

데이터를 책처럼 차곡차곡 쌓아올리는 형태의 자료구조로,

한 방향에서만 자료를 넣고 뺄 수 있는 LIFO(Last In First Out, 후입선출) 방식의 자료구조이다.

- LIFO
- 같은 구조와 크기의 자료를 정해진 방향으로만 쌓는다.
- 가장 위에 있는 자료(= 가장 최신의 자료)를 top이라고 하며, top을 통해서만 stack에 접근이 가능하다.
- 비어있는 stack에서 원소를 뺄 때 stack underflow라는 오류가, stack에 원소를 넣을 때 stack overflow라는 오류가 발생한다.



<br>



### 2. 연산

<img width="879" alt="datastructure_stack" src="https://user-images.githubusercontent.com/33407191/148966433-def026c5-0b0e-401e-afb2-0bcfd4d9f2e2.png">

* push(item): item 하나를 stack의 가장 윗부분에 추가한다.
* pop(): stack에서 가장 위에 있는 항목을 제거한다.
* peek(): stack의 가장 위에 있는 항목을 반환한다.
* isEmpty(): stack이 비어 있을 때 true를 반환한다.



<br>



### 3. 시간 복잡도

| 연산   | 평균 | 최악 |
| ------ | ---- | ---- |
| Access | O(n) | O(n) |
| Search | O(n) | O(n) |
| Push   | O(1) | O(1) |
| Pop    | O(1) | O(1) |



<br>



### 4. 장단점

| 장점                            | 단점                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| 단순한 구조로 인해 구현이 쉽다. | 데이터 최대 개수를 미리 정해야 한다.                         |
| 데이터 저장/읽기 속도가 빠르다. | 저장 공간의 낭비가 발생할 수 있다.(미리 최대 개수만큼의 저장 공간을 확보해야 한다.) |



<br>



### 5. 사용처

* 재귀 알고리즘
* 실행 취소(Undo)
* Backtracking
* 웹 브라우저 뒤로 가기
* 구문 분석
* 후위(postfix) 표기법 연산
* 문자열 역순 출력
* 수식의 괄호 검사







<br>

<br>



# Queue

![datastructure_queue](https://user-images.githubusercontent.com/33407191/149959687-fba775d2-c521-4e18-a40e-b7d3abeeb3f1.png)


### 1.  개념

Queue? 줄, 줄을 서서 기다리다

한쪽에서 데이터가 추가되고 다른 한쪽에서는 데이터가 삭제되는 FIFO(First In First Out) 구조



<br>



### 2. 연산



* Enqueue: 맨 뒤에 요소 추가
* Dequeue: 맨 앞쪽의 요소 삭제
* peek: front에 위치한 데이터 읽기
* front: 맨 앞의 위치
* rear: 맨 뒤의 위치



<br>



### 3. 시간 복잡도

- 탐색: O(n)
- 삽입/삭제: O(1)



<br>



### 4. 종류

#### 4-1) **Linear Queue**(또는 Linked Queue, 선형큐)

![datastructure_linear](https://user-images.githubusercontent.com/33407191/149959864-e2b266a4-7a6b-419a-8c04-5a4eaf668c52.png)

- 선형 배열 또는 연결리스트를 사용하여 규현된 Queue
- 데이터 삽입을 위해서 계속해서 요소를 이동시켜야 한다.
- 삽입/삭제 연산이 계속되면 front와 rear는 증가한다. 따라서 front 앞쪽에 저장 공간이 있더라도 삽입할 수 없는 문제가 발생한다.



#### 4-2) **Circular Queue**(선형큐)

(시작 자료는 원형큐가 복잡하여 그리기를 포기했다. 대신 [https://velog.io/@nnnyeong/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-%EC%8A%A4%ED%83%9D-Stack-%ED%81%90-Queue-%EB%8D%B1-Deque](https://velog.io/@nnnyeong/자료구조-스택-Stack-큐-Queue-덱-Deque)를 참고하자.)

- 위 선형큐의 저장 공간의 낭비 문제를 해결하지만 제한된 크기로 문제가 된다.
- front는 맨 첫번째 요소 바로 앞을 가리키며, rear는 마지막 요소를 가리킨다.
- empty 상태: front == rear
- full 상태: front == (rear+1) % MAX_QUEUE_SIZE
- empty, full 상태를 구분하기 위하여 하나의 공간을 비운다.



<br>



### 5. 장단점

|                    | 장점             | 단점        |
| ------------------ | ---------------- | ----------- |
| **Linear Queue**   | 확장 가능한 크기 | 느린 속도   |
| **Circular Queue** | 빠른 속도        | 제한된 크기 |



<br>



### 6. 사용처

* 프린트 인쇄 대기열
* 콜센터 대기시간
* 프로세스 관리
* BFS 알고리즘 구현



<br>

<br>





# Graph



### 1. 개념

Graph? 정점과 간선으로 이루어진 자료구조

정점과 그 정점을 연결하는 간선을 하나로 모아놓은 구조로, 정점 간의 관계를 표현

정점마다 간선이 있을 수도, 없을 수도 있다.

Graph는 여러 개의 고립된 부분 그래프(Isolated Subgraphs)로 구성될 수 있다.



<br>



### 2. 구조

<img src = "https://user-images.githubusercontent.com/33407191/150109730-1f3a9131-94f7-41cf-8de1-dccffe8e4189.png" height="300px">

- 정점(vertice) : 노드(node)라고도 하며 정점에는 데이터가 저장 (A, B, C, D)
- 간선(edge): 링크(arcs)라고도 하며 정점 간의 관계를 나타냄
- 인접 정점(adjacent vertex) : 간선에 의해 연결된 정점 (A, B는 인접 정점)
- 단순 경로(simple-path): 경로 중 반복되는 정점이 없는 것, 같은 간선을 자나가지 않는 경로
- 차수(degree): 무방향 그래프에서 하나의 정점에 인접한 정점의 수 (A의 차수는 3)
- 진출 차수(out-degree) : 방향 그래프에서 사용되는 용어로 한 정점에서 외부로 향하는 간선의 수
- 진입 차수(in-degree) : 방향 그래프에서 사용되는 용어로 외부 정점에서 들어오는 간선의 수



<br>



### 3. 종류

<img src = "https://user-images.githubusercontent.com/33407191/150109084-cb3c8597-8358-4264-8ca1-bef64b7b2d17.png" height="300px">

- 무방향 그래프: 두 정점을 연결하는 간선에 방향이 없다.

- 방향 그래프: 두 정점을 연결하는 간선에 방향이 있다.

<img src = "https://user-images.githubusercontent.com/33407191/150109397-c9dc7d3a-3eae-43d7-bc44-484e6020cc2e.png" height="300px">

- 연결 그래프: 무방향 그래프에서 모든 정점에 대해서 항상 경로가 존재한다.

- 비연결 그래프: 무방향 그래프에서 특정 정점 사이에 경로가 존재하지 않는다.

<img src = "https://user-images.githubusercontent.com/33407191/150109420-a509527d-64d0-4b53-b649-6dc4b7422cb3.png" height="300px">

- 순환 그래프: 시작 정점과 도착 정점이 동일한 그래프

- 비순환 그래프: 순환 그래프를 제외한 그래프로 사이클이 존재하지 않는다.

<img src = "https://user-images.githubusercontent.com/33407191/150109438-2672a0bc-7950-4ae2-b657-dd84d95b0349.png" height="300px">

- 완전 그래프: 그래프의 모든 정점이 서로 연결되어 있다.

<img src = "https://user-images.githubusercontent.com/33407191/150109455-a296a192-bc0e-47d9-8c75-116da14c456c.png" height="300px">

- 가중치 그래프: 간선에 가중치가 할당된 그래프



<br>



### 4. 구현

#### **1) Adjacency Matrix(인접 행렬)**

- 그래프에 간선이 많은 밀집 그래프(Dense Graph)
- 정점 간에 연결이 되어있으면 1, 아니면 0



#### **2) Adjacency List(인접 리스트)**

- 가장 일반적인 그래프 표현 구조
- 그래프 내 적은 숫자의 간선을 가지는 희소 그래프(Sparse Graph)의 경우
- 정점 간에 연결이 되어있으면 해당 정점의 인덱스에 해당 정점 삽입



<br>



### 5. 장단점

| 구분                 | 장점                                                         | 단점                                                         |
| -------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **Adjacency Matrix** | \- 2차원 배열 안에 모든 정점들의 간선 정보를 담아 배열의 위치를 확인하면 두 점에 대한 연결 정보 조회에 O(1)의 시간 복잡도를 가진다.<br>\- 구현이 간단한다. | \- 모든 정점에 대한 간선 정보를 대입해 O(n^2)의 시간 복잡도를 가진다.<br>\- 필요 이상의 공간이 낭비된다. |
| **Adjacency List**   | \- 정점들의 연결 정보를 탐색할 때 O(n)의 시간 복잡도를 가진다.<br>\- 필요한 만큼의 공간만 사용하여 공간의 낭비가 적다. | \- 특정 두 점이 연결되었는지 확인할 때 인접 행렬에 비해 시간이 오래 걸린다.<br>\- 구현이 어렵다. |



<br>



### 6. 탐색

탐색? 그래프의 존재하는 모든 정점을 한 번씩 방분하는 것.



#### **1) 깊이 우선 탐색(DFS)**

- 최대한 깊게 탐색

- 임의의 정점에서 시작해서 다음 분기로 넘어가기 전에 해당 분기를 완벽히 탐색한다.

- 다이상 갈 곳이 없다면 이전 정점으로 돌아가는 방법

- 재귀 호출이나 스택을 사용하여 구현

- 모든 정점을 방문할 때 사용



#### **2) 너비 우선 탐색(BFS)**

- 최대한 넓게 탐색

- 임의의 정점에서 시작해서 인접한 노드를 먼저 탐색한다.

- 시적 정점에서 인접한 모든 정점을 방문한 후 다시 인접 정점에 인접한 정점을 방문하는 방법

- 큐를 사용하여 구현

- 두 정점 사이의 최단 경로 혹은 임의의 경로를 찾을 때 사용







<br>

<br>


# Tree

### **1. 개념**

나뭇가지처럼 연결된 비선형 계층적 자료구조

Graph의 한 종류로, 정점과 간선을 이용하여 데이터를 표현한다.

서로 다른 두 정점을 연결하는 길이 하나뿐인 그래프를 트리라고 한다.



<br>



### **2. 특징**

- 정점(Node) 들과 노드들을 연결하는 간선(Edge)들로 구성되어 있다. (N 개의 Node, N-1개의 Edge)
- 하나의 루트(Root) 노드를 가진다.
- 루트 노드는 0개 이상의 자식 노드를 가진다. (루트 노드를 제외한 모든 노드는 단 하나의 부모 노드를 가진다.)
- 자식 노드 또한 0개 이상의 자식 노드를 갖는다.
- 비선형 자료구조로 계층적 관계를 표현한다.
- Graph의 한 종류다. (Cycle이 없는 하나의 연결 그래프: Connected Graph, 방향성이 있는 비순환 그래프: Directed Acycle Graph)
- 트리는 데이터의 저장보다는 저장된 데이터를 효과적으로 탐색하기 위해 사용한다.



<br>



### 3. 구조

![datastructure_tree](https://user-images.githubusercontent.com/33407191/151926061-3968f4e8-db48-4afd-923c-ae7b79e1f107.png)

- Root Node: 부모가 없는 노드, 트리는 하나의 루트 노드만을 가진다.
- Leaf Node: 자식이 없는 노드, ‘말단 노드’ 또는 ‘잎 노드’라고도 부른다.
- Internal Node: 단말 노드가 아닌 노드
- Edge: 노드를 연결하는 선 (link, branch라고도 부름)
- Sibling: 같은 부모를 가지는 노드
- 노드의 크기(size): 자신을 포함한 모든 자손 노드의 개수
- 노드의 깊이(depth): 루트에서 어떤 노드에 도달하기 위해 거쳐야 하는 간선의 수
- Level: 트리의 특정 깊이를 가지는 노드의 집합
- Degree: 하위 트리 개수 / 간선 수 (degree) = 각 노드가 지닌 가지의 수
- 트리의 차수(degree of tree): 트리의 최대 차수
- 트리의 높이(height): 루트 노드에서 가장 깊숙이 있는 노드의 깊이



<br>



### 4. 종류

| **Binary Tree**<br>**(이진 트리)**                  | 각 노드가 최대 두 개의 자식을 갖는 트리각 노드는 자식이 없거나 한 개 이거나 두 개만을 갖는다.<br>2개의 자식 노드 중 왼쪽 노드를 Left Node, 오른쪽 노드를 Right Node라고 한다. |
| --------------------------------------------------- | ------------------------------------------------------------ |
| **Binary Search Tree**<br>**(BST, 이진 탐색 트리)** | 노드에 저장된 키(key)는 유일하다.<br>왼쪽 자식 노드의 키 < 부모의 키 < 오른쪽 자식 노드의 키<br>왼쪽과 오른쪽 서브 트리도 이진 탐색 트리이다.효율적인 탐색을 위한 고안됨 |
| **Balanced Tree**<br>**(B-Tree, 균형 트리)**        | 모든 노드의 왼쪽과 오른쪽 하위 트리의 높이가 최대 1만큼 차이가 날 수 있는 트리다. |
| **Full Binary Tree**<br>**(전 이진 트리)**          | 모든 노드가 0개 또는 2개의 자식 노드를 갖는 트리             |
| **Complete Binary Tree**<br>**(완전 이진 트리)**    | 마지막 레벨을 제외하고 모든 레벨이 완전히 채워져 있다.<br>마지막 레벨은 노드가 왼쪽에서 오른쪽으로 채워져야 한다.<br>완전 이진 트리는 배열을 사용해 효율적으로 표현 가능 |
| **Perfect Binary Tree**<br>**(포화 이진 트리)**     | 포화 이진 트리는 모든 레벨이 노드로 꽉 차 있는 트리전 이진 트리의 성질도 만족해야 한다.<br>즉 모든 노드가 0개 혹은 2개의 자식 노드를 갖는다.모든 말단 노드가 동일한 깊이 또는 레벨을 갖는다.<br>트리의 노드 개수가 2^(높이)-1 개다. |
| **Skewed Binary Tree**<br>**(편향 이진 트리)**      | 하나의 차수로만 이루어져 있는 경우<br>배열(리스트)와 같은 선형 구조이므로 Leaf Node 탐색 시 모두 데이터를 전부 탐색해야 한다는 단점이 있다. (보완 : 균형 트리) |



<br>



### 5. 순회

https://code-lab1.tistory.com/9 → 해당 포스팅에서 시작 자료와 함께 이해하기 쉽게 설명되어 있다. (그래프 그리기가 너무 벅차서... ㅎ)



#### **1) 전위 순회**

탐색 순서: Root - Left subtree - Right subtree

더 이상 왼쪽 서브 트리가 없을 때까지 들어간 후에 방문한다. 그 후 부모 노드를 방문하고, 오른쪽 서브 트리로 들어가서 다시 오른쪽 서브 트리의 왼쪽 서브 트리가 없을 때까지 들어간 후에 방문한다.



#### **2) 중위 순회**

탐색 순서: Left subtree - Root - Right subtree

일단 부모 노드를 먼저 방문한 후 왼쪽, 오른쪽 노드를 방문하고 하위 노드로 들어간다.



#### **3) 후위 순회**

탐색 순서: Left subtree - Right subtree - Root

더 이상 왼쪽 서브 트리가 없을 때까지 들어간 후에 방문한다. 그 후 오른쪽 서브 트리로 들어가서 다시 오른쪽 서브 트리의 왼쪽 서브 트리가 없을 때까지 들어간 후에 방문한다. 부모 노드는 왼쪽, 오른쪽 하위 노드가 모두 방문된 후에 방문한다.



<br>



### 6. 구현

행렬, 리스트로 구현할 수 있다.

#### **1) 인접 배열**

\- 1차원: 자신의 부모 배열만 저장

\- 2차원: 이진 트리의 경우, A[cur][left], A[cur][right] 와 같이 자신의 양쪽 노드를 저장



#### **2) 인접 리스트**

\- 가중치 O: Node와 가중치 정보를 저장하는 class 사용 + ArrayList[] 사용

\- 가중치 X: 단순 ArrayList



<br>



### 7. 사용처

계층 적 데이터 저장: 데이터를 계층 구조로 저장하는 데 사용(파일 및 폴더)

효율적인 검색 속도: 효율적인 삽입, 삭제 및 검색을 위해 트리 사용

힙(Heap): 트리로 된 자료 구조

데이터 베이스 인덱싱: 데이터베이스 인덱싱을 구현하는 데 트리를 사용 (B-Tree, B+Tree, AVL-Tree..)

Trie: 사전을 저장하는 데 사용되는 종류의 트리



<br>

<br>



#  Graph vs Tree



| 구분            | Graph                                                        | Tree                                                         |
| --------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 설명            | Node와 그 node를 연결하는 edge를 하나로 모아놓은 구조        | Graph의 한 종류로 DAG(Directed Acycle Graph: 방향성이 있는 비순환 Graph)의 한 종류 |
| 방향성          | Directed / Undirected                                        | Directed only                                                |
| Cycle           | Cycle 가능 / 자체 간선(self-loop) 가능<br>Cycle / Acycle     | Cycle 불가능 / 자체 간선 불가능<br>Acycle only               |
| Root            | Root 개념이 없다.                                            | 1개의 Root만 존재                                            |
| Parent-Child    | X                                                            | O                                                            |
| Model           | 네트워크 모델                                                | 계층 모델                                                    |
| 순회(Traversal) | DFS, BFS                                                     | DFS, BFS 안의 Pre & In & Post                                |
| Edge            | Graph의 종류에 따라 간선의 수가 다르다.<br>Edge가 존재하지 않을 수 있다. | Node가 N 개인 Tree는 항상 N-1개의 간선을 가진다.             |
| 경로(Path)      | -                                                            | 임의의 두 Node 간의 경로는 유일하다.                         |
| 예시            | 지도, 지하철 노선, 도로, 선수과목                            | 이진 트리, 이진 탐색 트리, 균형 트리, 이진 힙 등             |



<br>

<br>




# Heap

또는 Binary Heap

### 1.  개념

* tree 기반 자료구조로 heap 속성을 만족하는 완전한 트리
* heap 속성?
  * 큰 값은 상위, 작은 값은 하위에 위치하는 구조(혹은 반대)로, 부모 노드의 값이 자식 노드의 값보다 항상 크(작)다. 
  * 이와 같은 구조로 우선순위를 같는 heap을 최대힙(max heap)과 최소힙(min heap)라고 한다.
  * root(최상위 부모)의 우선순위가 가장 높다.
* 여러 개의 값들 중에서 최댓값이나 최솟값을 빠르게 찾도록 고안된 자료구조
* heap은 일종의 반정렬 상태(느슨한 정렬 상태)를 유지한다.
* 반정렬 상태?
  * 부모 자식간의 관계만 정의되어 있고, 형제, 사촌 간의 우선순위는 정해진 것이 없다.
* heap은 중복된 값을 허용한다.(이진 탐색 트리는 중복 값 미허용)
* 완전이진트리(Complete Tree)?
  * degree가 2인 binary tree
  * terminal node들의 위는 full tree(모든 terminal node의 level이 동일한 tree)이다.
  * terminal node들은 왼쪽부터 채워진다.
* Binary Heap은 Priority Queue(우선순위큐)를 구현하기 가장 좋은 구조이다.

<br>

### 2. 충족 조건

* Shape Property: 완전이진트리를 유지해야 한다.
* Heap Property: 부모의 우선순위가 자식의 우선순위보다 높아야 한다.
* Node 개수: ```2^h-1 < n <= 2^(h+1)-1```를 지켜한다.

<br>

### 3. 종류

* Max Heap: 우선순위가 높을수록(Root에 가까워질수록) Node의 Value값이 더 크다.

  ![min heap](https://user-images.githubusercontent.com/33407191/126661525-2df5acd2-0c2b-485a-82c9-8ce7d676cb73.png)

* Min Heap: 우선순위가 높을수록(Root에 가까워질수록) Node의 Value값이 더 작다.

  ![max heap](https://user-images.githubusercontent.com/33407191/126661530-9cea0716-9881-4dba-8751-38808a4a831a.png)

<br>

### 4. 연산

* 삽입(Percolate-Up)
  1. 원소를 heap의 가장 마지막 node에 추가한다.
  2. 추가한 원소를 부모와 비교하며 순서가 heap 조건과 일치할 때까지 부모 node와 위치를 바꾼다.
* 삭제(Percolate-Down)
  1. heap의 root node를 삭제한다.
  2. 마지막 node를 root node로 이동한 후, 자식 node와 비교해가며 순서가 heap 조건과 일치할 때까지 자식 node와 위치를 바꾼다.
* heapify
  * Heap 성질을 만족하게 하는 연산으로, 위 삽입/삭제의 2번 단계에 해당한다. heap 성질을 만족하도록 만드는 연산이다.

<br>

### 5. 시간 복잡도

* 삽입/삭제 : O(1)
* 삽입/삭제 후 heapify하게 만드는 시간: O(logn)
* 총 시간 복잡도: O(1)\*O(logn)

<br>

### 6. 구현

일반적으로 배열로 구현한다.

<br>

### 7. 사용처

우선순위 큐는 배열, 연결 리스트, 힙으로 구현이 가능하다. 이 중에서 힙으로 구현하는 것이 가장 효율적이다.

<br>
<br>


# Red-Black-Tree

### 1. 개념

* Red-Black Tree는 이진탐색트리(BST: Binary Search Tree)의 일종으로, 기본적인 아이디어를 유지하고 Tree의 밸런스가 무너지지 않게 하면서 최악의 경우에도 O(logn)의 시간복잡도를 갖게 하기 위한 자료구조
* 이진탐색트리는 최악의 경우 tree의 높이만큼의 탐색시간이 걸린다.(계속해서 왼쪽 또는 오른쪽 node로 연결될 때: O(h)의 시간복잡도)
* Red-Black Tree는 위와 같이 편향된 tree가 나오지 않도록 "조건"을 걸어 균형잡힌 tree로 만들어 준다. 따라서 red-black tree의 높이는 logn에 가까워지고, O(logn)의 시간복잡도를 가진다.
* 자식노드가 존재하지 않을 경우 NIL node라고 부르는 특수한 node가 있다고 가정한다. 따라서 모든 leaf node는 NIL 노드이다.



<br>



### 2. 정의(조건)

| 정의                                                         | 표현                                   |
| ------------------------------------------------------------ | -------------------------------------- |
| 각 node는 red 혹은 black이다.                                |                                        |
| root nodes는 black이다.                                      | Root Property                          |
| 모든 leaf node(= leaf node)는 black이다.                     | External Property                      |
| red node의 자식 node들은 전부 black이다.<br>(= red node는 연속되어 위치하지 않는다.) | Internal Property<br>(= No Double Red) |
| 모든 node에 대해서 해당 node에서부터 자손인 leaf node에 이르는 모든 경로에는 동일한 개수의 black node가 존재한다.<br>(= 단순 node의 수는 다를 수 있다.) | Depth Property                         |



<br>



### 3. 높이

<img src = "https://user-images.githubusercontent.com/33407191/126875429-35b61e28-bdf4-40fc-bc6c-c52c0ef41135.png" width="500px">


* 특정 node x의 height h(x)는 자신으로부터 NIL 노드까지의 가장 긴 경로에 포함된 간선의 개수이다.
* 특정 node x의 black-height bh(x)는 x로부터 NIL 노드까지의 경로상의 black node의 개수이다. 이때, 자신이 black node라면 bh(x)에 포함하지 않는다. 따라서, NIL의 bh는 0이다.
* Red-Black Tree의 높이는 O(logn)이다.
  * height가 h인 node의 black-height는 ```bh >= (h/2)```이다. (red-node는 연속될 수 없으므로 black-node의 수가 높이의 절반 이상이다.)
  * node x를 root로하는 임의의 sub tree는 적어도 ```2bh(x)-1```개의 internal node(내부노드)를 포함한다.
  * ```n >= 2bh-1 >= 2h/2-1``` 이므로, 여기서 bh와 h는 각각 root의 balck-height와 height이며, 정의에서 설명하는 5가지 조건을 만족하는 Red-Black Tree라면 자동으로 높이는 O(logn)이 된다.

<br>



### 4. Rotation

* Rotation은 Red-Black Tree를 재정렬하는 방법 중 하나인 Restructuring 과정에서 사용된다.

* Left Rotation

<img src = "https://user-images.githubusercontent.com/33407191/126873126-cf6b067a-ceed-45fc-a640-e17ab576eebe.png" width="400px">

  * B를 기준으로 *left rotation*
    1. B를 새로운 root로 지정한다.
    2. A를 B의 새로운 left childe로 지정한다.
    3. y를 A의 새로운 right child로 지정한다.
  * 해당 tree은 parent node가 존재하는 sub tree일 수 있다. 이때 A가 parent의 left child였다면 B를 parent의 left child로 설정한다. (A가 parent의 right child였을 때도 동일한 방법)


* Right Rotation

<img src = "https://user-images.githubusercontent.com/33407191/126873128-b59499f3-1719-49e2-a7fc-204c3de3e778.png" width="400px">

  * A를 기준으로 *right rotation*
    1. A를 새로운 root로 지정한다.
    2. B를 A의 새로운 right childe로 지정한다.
    3. y를 B의 새로운 left child로 지정한다.
    4. 해당 tree은 parent node가 존재하는 sub tree일 수 있다. 이때 B가 parent의 left child였다면 A를 parent의 left child로 설정한다. (B가 parent의 right child였을 때도 동일한 방법)



* 시간 복잡도
  * Rotation의 시간 복잡도는 O(1)이다.



<br>



### 5. 재정렬



Red-Black Tree를 만들어보자. node를 추가하다가 Double Red가 생긴다면?
해결방법에는 2가지(restructuring, recoloring)가 있다.

2가지 해결방법 중 어떤 방법을 적용할 것인지는 uncle node의 color에 따라 결정된다.

<img src = "https://user-images.githubusercontent.com/33407191/126873123-0070bf95-0109-41b3-8717-82e7c84fc26d.png" width="600px">

  * Restructuring: uncle이 black일 때
    1. 자식(child), 부모(parent), 부모의 부모(grand parent) 3개의 node를 정렬한다.
    2. 중앙값을 parent node로 지정하고 나머지 두값을 child로 지정한다. 이때 rotation이 사용된다.
    3. Parent node를 black으로, child node를 red로 지정한다. 
  * Recoloring: uncle이 red일 때
    1. Parent node를 black으로 변경한다.
    2. Grand parent node를 red로 지정한다.
    3. 이 과정을 위로 올라가면 반복해준다.
    4. Grand parent node가 root이면 다시 black으로 변경한다.



<br>



### 4. 시간복잡도

* Restructuring: O(1)
* Recoloring: O(logn)
* Search: Red-Black Tree의 search 알고리즘은 이진탐색트리(BST)와 같다.
* Insert: O(logn)
* Delete: O(logn)



<br>
<br>

# B+Tree

### 1. 개념

* B+ Tree는 key에 의해서 식별되는 record의 효율적인 삽입, 삭제, 검색을 통해 정렬된 데이터를 표현하기 위한 tree 자료구조이다.
* B tree는 모든 node에 record pointer를 가지지만, B+ Tree는 leaf node에서만 record pointer를 가진다.
  * 모든 record들은 tree의 가장 하위인 leaf node에 정렬되어있다. 그래서 leaf node를 data node라고 하기도 한다.
  * leaf node가 아닌 index node(inner block)에는 key 정보가 저장되어 있다.
* B+ Tree의 Inner Node는 Data(record)가 없기 때문에 B-Tree의 Inner Node에 비하여 용량작다.
  * 하나의 Disk Block에 더 많은 Inner Node를 배치 할 수 있게 되어, Key 탐색시 B-Tree에 비하여 상대적으로 적은 Disk Block만 읽어도 된다. 
  * 때문에 B+ Tree는 Key 탐색시 B-Tree보다 좀더 나은 성능을 보여준다.
* M차 B+ Tree의 특징
  * node는 최대 *M*개 부터 *M*/2개 까지의 자식을 가질 수 있다.
  * node에는 최대 *M*−1개 부터 [*M*/2]−1개의 키가 포함될 수 있다.
  * 노드의 키가 *x*개라면 자식의 수는 *x*+1개다.
  * 최소차수는 자식수의 하한값을 의미하며, 최소차수가 *t*라면 *M*=2*t*−1을 만족한다. (최소차수 *t*가 2라면 3차 B+ tree이며, key의 하한은 1개다.)

<br>



### 2. 구조

| 구분                        | 내용                                                         |
| --------------------------- | ------------------------------------------------------------ |
| Index Node<br>(=Inner Node) | Data node(=leaf node)를 제외한 node들<br>Index node의 key는 자신의 right sub tree의 data node의 첫번째에 위치한다. |
| Data Node<br>(=Leaf Node)   | Linkedlist로 구성되며, data node 하나의 크기는 index node와 같지 않아도 된다.<br>LinkedList 구조를 따라서 모든 Data Node는 왼쪽에서 오른쪽으로 연결되어있다. |



<br>



### 3. 연산

* Insert
  * Overflow가 발생하면 split된다.
  * 노드의 분열이 일어나면 중간 key 값이 부모 노드로 올라갈 뿐 아니라 새로 분열된 노드에도 포함되어야 한다.
  * 새 노드는 leaf 노드끼리의 linked list에도 삽입되어야 한다.
* Delete
  * 재배치와 합병이 필요하지 않을 때는 leaf 노드에서만 삭제된다.
  * Index 부분은 다른 key 값을 찾는데 사용될 수 있기 때문에 leaf node의 값이 삭제되어도 삭제하지 않는다.

* 재배치할 경우 index 부분의 node의 key 값은 변하지만 tree 구조는 변하지 않는다.
* 합병을 할 경우 index 부분에서도 key 값을 삭제한다.



<br>



### 4. 사용처

* RDB(Relational Database): table indexing을 위해 사용
* File System: block indexing을 위해 사용



<br>
<br>



## 참고자료

Array

- https://velog.io/@choiiis/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-%EB%B0%B0%EC%97%B4Array%EA%B3%BC-%EB%A6%AC%EC%8A%A4%ED%8A%B8List
- https://opentutorials.org/module/1335/8677

LinkedList

- https://opentutorials.org/module/1335/8821
- https://velog.io/@riceintheramen/Linked-list
- https://sycho-lego.tistory.com/17
- https://velog.io/@choiiis/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-%EB%B0%B0%EC%97%B4Array%EA%B3%BC-%EB%A6%AC%EC%8A%A4%ED%8A%B8List
- https://coding-factory.tistory.com/552
- https://freestrokes.tistory.com/84

HashTable

- https://velog.io/@cyranocoding/Hash-Hashing-Hash-Table%ED%95%B4%EC%8B%9C-%ED%95%B4%EC%8B%B1-%ED%95%B4%EC%8B%9C%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0%EC%9D%98-%EC%9D%B4%ED%95%B4-6ijyonph6o
- https://mangkyu.tistory.com/102
- https://hee96-story.tistory.com/48

Stack

- https://gmlwjd9405.github.io/2018/08/03/data-structure-stack.html
- https://monsieursongsong.tistory.com/4
- https://yoongrammer.tistory.com/45
- https://devuna.tistory.com/22
- https://goodgid.github.io/Data-Structure-Pros-And-Cons/
- https://onnons.tistory.com/293

Queue

- https://monsieursongsong.tistory.com/5
- https://devuna.tistory.com/22
- [https://velog.io/@nnnyeong/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-%EC%8A%A4%ED%83%9D-Stack-%ED%81%90-Queue-%EB%8D%B1-Deque](https://velog.io/@nnnyeong/자료구조-스택-Stack-큐-Queue-덱-Deque)
- https://minosaekki.tistory.com/11
- https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=rlaauddlf200&logNo=30140551855

Graph

- https://coding-factory.tistory.com/610
- https://suyeon96.tistory.com/32

- https://hongcoding.tistory.com/78

- https://gmlwjd9405.github.io/2018/08/13/data-structure-graph.html

Tree

- https://gmlwjd9405.github.io/2018/08/12/data-structure-tree.html
- https://yoongrammer.tistory.com/68
- https://monsieursongsong.tistory.com/6
- [https://velog.io/@kimdukbae/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-%ED%8A%B8%EB%A6%AC-Tree](https://velog.io/@kimdukbae/자료구조-트리-Tree)
- https://code-lab1.tistory.com/8
- https://code-lab1.tistory.com/9

Graph vs Tree

- https://gmlwjd9405.github.io/2018/08/12/data-structure-tree.html

Heap

- https://gmlwjd9405.github.io/2018/05/10/data-structure-heap.html
- https://kayuse88.github.io/binary-heap/
- https://blog.naver.com/kaoara/221949258742
- https://soniacomp.medium.com/%EA%B8%B0%EC%88%A0%EB%A9%B4%EC%A0%91-%EC%9D%B4%EC%A7%84%ED%83%90%EC%83%89%ED%8A%B8%EB%A6%AC-%ED%9E%99-2e7812d088fa
- 사진 출처: https://medium.com/@konduruharish/binary-heap-minheap-and-max-heap-in-typescript-and-c-be3cebee263e
- https://ratsgo.github.io/data%20structure&algorithm/2017/09/27/heapsort/

Red-Black Tree

- https://ratsgo.github.io/data%20structure&algorithm/2017/10/28/rbtree/
- https://github.com/namjunemy/TIL/blob/master/Algorithm/red_black_tree_01.md
- https://zeddios.tistory.com/237

* Rotation: https://ratsgo.github.io/data%20structure&algorithm/2017/10/27/avltree/
* 재정렬: https://junboom.tistory.com/18
* 시간복잡도: https://ferrante.tistory.com/46

B+ Tree

* https://ssup2.github.io/theory_analysis/B_Tree_B+_Tree/
* https://ju-hy.tistory.com/106
* https://ko.wikipedia.org/wiki/B%2B_%ED%8A%B8%EB%A6%AC
* https://wangin9.tistory.com/entry/B-tree-B-tree
* 삽입삭제 정리짱: https://velog.io/@emplam27/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-%EA%B7%B8%EB%A6%BC%EC%9C%BC%EB%A1%9C-%EC%95%8C%EC%95%84%EB%B3%B4%EB%8A%94-B-Plus-Tree
