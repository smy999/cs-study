# Data Structure

- [Array](#Array)
- [LinkedList](#LinkedList)
- [HashTable](#HashTable)
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


#### 2. 구조

```
[     Node    ]    [     Node    ]    [     Node    ]    [     Node    ]
[Data][Pointer]--->[Data][Pointer]--->[Data][Pointer]--->[Data][Pointer]
[    Head     ]                                          [    Tail     ] 
```
- Node: 데이터 저장 단위
- Data: 실제 data를 저장하는 곳
- Pointer(Link): 다음 node의 연결 정보를 저장하는 공간으로 다음 node의 주소값을 가진다.
- Head: LinkedList의 첫 node
- Tail: LinkedList의 마지막 node


#### 3. 시간 복잡도
- 


#### 4. 장단점

| 장점         | 단점         |
| ----------- | ----------- |
| index로 data에 빠르게 접근할 수 있다. | 배열 내의 데이터 이동이 어렵다. 중간에 삽입할 경우 삽입 위치 이후의 모든 원소를 한칸씩 뒤로 밀어야 한다. |
| 삽 | 연속된 메모리 공간으로 중간 데이터가 삭제되는 메모리가 낭비되는 문제가 발생한다. |
| 사전에 data 공간을 할당하지 않아도 된다.(배열과 다르게 선언 시 크기가 정해지지 않는다.) | 크기 변경이 불가능하다. 이후 새로운 데이터를 추가할 수 없어 새로운 배열을  생성한 후 기존 값을 복사해야 한다. |


#### 5. 사용법(Java)
```

```


<br>


## HashTable


<br>



## 참고자료

Array
- https://velog.io/@choiiis/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-%EB%B0%B0%EC%97%B4Array%EA%B3%BC-%EB%A6%AC%EC%8A%A4%ED%8A%B8List
- https://opentutorials.org/module/1335/8677
 
LinkedList
- https://opentutorials.org/module/1335/8821
