# Data Structure

- [Array](#Array)
- [LinkedList](#LinkedList)
- [Hash Table](#Hash Table)
- Stack     
- Queue
- Graph
- Tree
- 그래프(Graph)와 트리(Tree)의 차이점
- 참고자료

<br>

## Array

#### 1. 개념

- 같은 type의 data를 연속된 메모리 공간에 순차적으로 저장한 선형 자로구조(sequence container)
- data를 하나의 변수에 grouping해서 관리하는 위한 방법으로, 반복문과 함께 사용하면 효율적인 처리가 가능하다.
- 배열의 크기는 고정, 선언 시 배열의 크기를 결정하고 이후 변경할 수 없다


#### 2. 시간 복잡도

- 맨앞/중간에 삽입/삭제: O(n)
- 맨뒤에 삽입/삭제: O(1)
- 탐색: O(1)


#### 3. 장단점

| 장점         | 단점         |
| ----------- | ----------- |
| index로 data에 빠르게 접근할 수 있다. | 배열 내의 데이터 이동이 어렵다. 중간에 삽입할 경우 삽입 위치 이후의 모든 원소를 한칸씩 뒤로 밀어야 한다. |
| 연속된 메모리 공간으로 관리가 편리하다. | 연속된 메모리 공간으로 중간 데이터가 삭제되는 메모리가 낭비되는 문제가 발생한다. |
|  | 크기 변경이 불가능하다. 이후 새로운 데이터를 추가할 수 없어 새로운 배열을  생성한 후 기존 값을 복사해야 한다. |


#### 4. 사용법(Java)
```
// 선언과 함께 초기화
int[] arr = {1, 2, 3, 4};

// 선언 후 값 넣기
int[] arr2 = new int[4];
for(int i = 0; i < arr2.length(); i++) {
  arr2[i] = sc.nextInt();
}
```


#### 5. 사용처

- 배열은 데이터의 개수가 확실하게 정해졌을 때, 추가적인 삽입/삭제가 빈번하지 않을 때, 검색을 할 때(index를 사용하여 빠른 검색이 가능) 사용하는 것이 좋다.


<br>


## LinkedList

#### 1.  개념

- 서로 다른 곳에 저장된 데이터를 연결한 list 구조
- 배열과는 달리 연속된 메모리를 필요로하지 않고, 빈 공간을 찾아 연결한 후 사용한다. (Array는 물리적으로 연속된 메모리에 저장, list는 논리적인 순서)
- 자료구조 tree에 근간이 되는 자료구조이다.
- 동적으로 메모리를 할당한다.
- 하나의 link에 4byte를 차지하며, double LinkedList는 8byte를 차지한다.


#### 2. 구조

```
[    Head     ]--->[     Node    ]    [     Node    ]    [     Node    ]    [     Node    ]
                   [Data][Pointer]--->[Data][Pointer]--->[Data][Pointer]--->[Data][Pointer]--->[    Tail     ]
```
- Node: 데이터 저장 단위
- Data: 실제 data를 저장하는 곳
- Pointer(Link): 다음 node의 연결 정보를 저장하는 공간으로 다음 node의 주소값을 가진다.
- Head: LinkedList의 첫 node를 가리킨다.
- Tail: LinkedList의 마지막 node로 Null을 값을 가진다.


#### 3. 시간 복잡도

- 맨 앞/뒤에서 삽입/삭제하는 경우: O(1)
- 중간에 삽입/삭제하는 경우: O(n) = 탐색 시간
- 탐색: O(n)


#### 4. 장단점

| 장점         | 단점         |
| ----------- | ----------- |
| data의 삽입/삭제가 편리하다.(해당 부분의 연결을 끊고 새로운 노드에 연결한 후 다음 노드와 연결해준다.) | 특정 데이터를 검색할 때 index로 접근하지 않기 때문에 처음부터 끝까짓 순회하여 시간이 오래걸린다. |
| 논리적 순서를 갖는 특정으로 메로리를 효율적으로 사용할 수 있다. | Pointer를 저장하는 메모리 공간이 추가적으로 필요하다. |
| 동적으로 메모리를 할당하여 선언 시 크기를 정하지 않아도 된다. (크기 변경이 가능하다.) | 구현이 어렵다. |


#### 5. 사용법(Java)
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

#### 6. 사용처
- 추가와 삭제가 많은 경우에는 Array보다는 LinkedList를 사용한다.
- 대용량 데이터 처리에 적합하다.
- 크기가 정해지지 않은 경우에 사용한다.


<br>


## Hash Table

#### 1. 개념

- Hash 함수를 사용하여 변환한 값을 index 삼아 key와 value(data) 쌍을 저장하는 자료구조이다.
- 각각의 key 값에 hash 함수를 적용하여 고유 index를 상성한 후, 이 index를 사용하여 값을 저장하고나 검색한다.
- 이때, 실제 값이 저장되는 곳을 bukets 혹은 slot이라고 한다.
- 기본연산으로 search, insert, delete가 있다.
- Hash 함수의 특성상 다른 문자열의 hasing 결과가 같을 수 있다. 이런 경우를 hash collision이라고 한다.


#### 2. 구조
- Key: 길이가 일정하지 않은 Hash 함수의 입력값.
- Hash Function: key를 hast로 변경하는 역할. 일정하지 않은 길이를 가진 key를 일정하게 만들어 저장소를 효율적으로 관리할 수 있다. 하지만 다른 문자열의 hasing 결과가 같아서 발생하는 hash collision이 발생할 수 있어서 hash 함수를 만들 때 충돌을 최소화하는 방법을 찾아야한다.
- Hash: Hash Function의 결과값. 저장소(bucket과 slot)에서 value와 매칭되어 저장된다.
- Value: 최종적으로 저장되는 값. bucket과 slot에 저장되며, key-value 쌍으로 key에 매칭되어 기본 연산 접근이 가능하다.


#### 3. 시간 복잡도

* 평균
    * O(1), key 값을 hash화 해서 고유 index를 생성한 경우
* 데이터가 충돌한 경우: O(n), 연결 리스트를 모두 검색해야 한다.


#### 4. 장단점

| 장점         | 단점         |
| ----------- | ----------- |
|  |  |
|  |  |
|  |  |


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



