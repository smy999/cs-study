# Data Structure

- [Array](#Array)
- [LinkedList](#LinkedList)
- [Hash Table](#HashTable)
- Stack     
- Queue
- Graph
- Tree
- 그래프(Graph)와 트리(Tree)의 차이점
- [Heap](#Heap)
- [Red-Black Tree](#Red-Black-Tree)
- B+ Tree
- [참고자료](#)

<br>

# Array

### 1. 개념

- 같은 type의 data를 연속된 메모리 공간에 순차적으로 저장한 선형 자로구조(sequence container)
- data를 하나의 변수에 grouping해서 관리하는 위한 방법으로, 반복문과 함께 사용하면 효율적인 처리가 가능하다.
- 배열의 크기는 고정, 선언 시 배열의 크기를 결정하고 이후 변경할 수 없다


### 2. 시간 복잡도

- 맨앞/중간에 삽입/삭제: O(n)
- 맨뒤에 삽입/삭제: O(1)
- 탐색: O(1)


### 3. 장단점

| 장점         | 단점         |
| ----------- | ----------- |
| index로 data에 빠르게 접근할 수 있다. | 배열 내의 데이터 이동이 어렵다. 중간에 삽입할 경우 삽입 위치 이후의 모든 원소를 한칸씩 뒤로 밀어야 한다. |
| 연속된 메모리 공간으로 관리가 편리하다. | 연속된 메모리 공간으로 중간 데이터가 삭제되는 메모리가 낭비되는 문제가 발생한다. |
|  | 크기 변경이 불가능하다. 이후 새로운 데이터를 추가할 수 없어 새로운 배열을  생성한 후 기존 값을 복사해야 한다. |


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


### 2. 구조

```
[    Head     ]--->[     Node    ]    [     Node    ]    [     Node    ]    [     Node    ]
                   [Data][Pointer]--->[Data][Pointer]--->[Data][Pointer]--->[Data][Pointer]--->[    Tail     ]
```
- Node: 데이터 저장 단위
- Data: 실제 data를 저장하는 곳
- Pointer(Link): 다음 node의 연결 정보를 저장하는 공간으로 다음 node의 주소값을 가진다.
- Head: LinkedList의 첫 node를 가리킨다.
- Tail: LinkedList의 마지막 node로 Null을 값을 가진다.


### 3. 시간 복잡도

- 맨 앞/뒤에서 삽입/삭제하는 경우: O(1)
- 중간에 삽입/삭제하는 경우: O(n) = 탐색 시간
- 탐색: O(n)


### 4. 장단점

| 장점         | 단점         |
| ----------- | ----------- |
| data의 삽입/삭제가 편리하다.(해당 부분의 연결을 끊고 새로운 노드에 연결한 후 다음 노드와 연결해준다.) | 특정 데이터를 검색할 때 index로 접근하지 않기 때문에 처음부터 끝까짓 순회하여 시간이 오래걸린다. |
| 논리적 순서를 갖는 특정으로 메로리를 효율적으로 사용할 수 있다. | Pointer를 저장하는 메모리 공간이 추가적으로 필요하다. |
| 동적으로 메모리를 할당하여 선언 시 크기를 정하지 않아도 된다. (크기 변경이 가능하다.) | 구현이 어렵다. |


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

### 6. 사용처
- 추가와 삭제가 많은 경우에는 Array보다는 LinkedList를 사용한다.
- 대용량 데이터 처리에 적합하다.
- 크기가 정해지지 않은 경우에 사용한다.


<br>


# HashTable

### 1. 개념

- Hash 함수를 사용하여 변환한 값을 index 삼아 key와 value(data) 쌍을 저장하는 자료구조이다.
- 각각의 key 값에 hash 함수를 적용하여 고유 index를 상성한 후, 이 index를 사용하여 값을 저장하고나 검색한다.
- 이때, 실제 값이 저장되는 곳을 bukets 혹은 slot이라고 한다.
- 기본연산으로 search, insert, delete가 있다.
- Hash 함수의 특성상 다른 문자열의 hasing 결과가 같을 수 있다. 이런 경우를 hash collision이라고 한다.


### 2. 구조
- Key: 길이가 일정하지 않은 Hash 함수의 입력값.
- Hash Function: key를 hast로 변경하는 역할. 일정하지 않은 길이를 가진 key를 일정하게 만들어 저장소를 효율적으로 관리할 수 있다. 하지만 다른 문자열의 hasing 결과가 같아서 발생하는 hash collision이 발생할 수 있어서 hash 함수를 만들 때 충돌을 최소화하는 방법을 찾아야한다.
- Hash: Hash Function의 결과값. 저장소(bucket과 slot)에서 value와 매칭되어 저장된다.
- Value: 최종적으로 저장되는 값. bucket과 slot에 저장되며, key-value 쌍으로 key에 매칭되어 기본 연산 접근이 가능하다.


### 3. 시간 복잡도

* 평균: O(1)
* 데이터가 충돌한 경우: O(n), 모든 저장소를 검색해야 한다.


### 4. 장단점

| 장점         | 단점         |
| ----------- | ----------- |
|  |  |
|  |  |
|  |  |

<br>

<hr>

저번주 내용 skipㅎ 나중에 할게요

<hr>


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


### 2. 충족 조건
* Shape Property: 완전이진트리를 유지해야 한다.
* Heap Property: 부모의 우선순위가 자식의 우선순위보다 높아야 한다.
* Node 개수: ```2^h-1 < n <= 2^(h+1)-1```를 지켜한다.


### 3. 종류
* Max Heap: 우선순위가 높을수록(Root에 가까워질수록) Node의 Value값이 더 크다.

  ![min heap](https://user-images.githubusercontent.com/33407191/126661525-2df5acd2-0c2b-485a-82c9-8ce7d676cb73.png)

* Min Heap: 우선순위가 높을수록(Root에 가까워질수록) Node의 Value값이 더 작다.

  ![max heap](https://user-images.githubusercontent.com/33407191/126661530-9cea0716-9881-4dba-8751-38808a4a831a.png)


### 4. 연산
* 삽입(Percolate-Up)
  1. 원소를 heap의 가장 마지막 node에 추가한다.
  2. 추가한 원소를 부모와 비교하며 순서가 heap 조건과 일치할 때까지 부모 node와 위치를 바꾼다.
* 삭제(Percolate-Down)
  1. heap의 root node를 삭제한다.
  2. 마지막 node를 root node로 이동한 후, 자식 node와 비교해가며 순서가 heap 조건과 일치할 때까지 자식 node와 위치를 바꾼다.
* heapify
  * Heap 성질을 만족하게 하는 연산으로, 위 삽입/삭제의 2번 단계에 해당한다. heap 성질을 만족하도록 만드는 연산이다.


### 5. 시간 복잡도
* 삽입/삭제 : O(1)
* 삽입/삭제 후 heapify하게 만드는 시간: O(logn)
* 총 시간 복잡도: O(1)\*O(logn)


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

<img src = "https://user-images.githubusercontent.com/33407191/126873131-ef2a7db1-381c-495e-a028-2d03b8e7e67d.png" width="600px">


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
  <img src = "https://user-images.githubusercontent.com/33407191/126873126-cf6b067a-ceed-45fc-a640-e17ab576eebe.png" width="500px">
  * B를 기준으로 *left rotation*
    1. B를 새로운 root로 지정한다.
    2. A를 B의 새로운 left childe로 지정한다.
    3. y를 A의 새로운 right child로 지정한다.
  * 해당 tree은 parent node가 존재하는 sub tree일 수 있다. 이때 A가 parent의 left child였다면 B를 parent의 left child로 설정한다. (A가 parent의 right child였을 때도 동일한 방법)

  사진



* Right Rotation
  <img src = "https://user-images.githubusercontent.com/33407191/126873128-b59499f3-1719-49e2-a7fc-204c3de3e778.png" width="500px">
  * A를 기준으로 *right rotation*
    1. A를 새로운 root로 지정한다.
    2. B를 A의 새로운 right childe로 지정한다.
    3. y를 B의 새로운 left child로 지정한다.
    4. 해당 tree은 parent node가 존재하는 sub tree일 수 있다. 이때 B가 parent의 left child였다면 A를 parent의 left child로 설정한다. (B가 parent의 right child였을 때도 동일한 방법)

  사진

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

HashTable
- https://velog.io/@cyranocoding/Hash-Hashing-Hash-Table%ED%95%B4%EC%8B%9C-%ED%95%B4%EC%8B%B1-%ED%95%B4%EC%8B%9C%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0%EC%9D%98-%EC%9D%B4%ED%95%B4-6ijyonph6o
- https://mangkyu.tistory.com/102

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
