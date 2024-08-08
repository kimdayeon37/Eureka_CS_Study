# 자료구조
![Untitled](https://github.com/user-attachments/assets/4eb647b4-3df5-4800-9663-dc58ad59611b)


# 우선순위 큐(Priority Queue)

Priority Queue: 요소들이 우선 순위에 따라 정렬되는 자료구조

- 기본적인 Queue: FIFO 방식
- 우선순위 Queue: 각 요소들이 특정 기준에 따라 우선순위를 갖고, 이 우선순위가 가장 높은 데이터가 먼저 나오게 된다. Queue 인터페이스를 상속받기 때문에 Queue 인터페이스에서 정의된 메서드들도 사용할 수 있다.

> Priority Queue 메소드
> 
- Insert: 우선순위 큐에 새로운 요소 추가
- Extract-Max: 우선순위가 가장 높은(낮은) 요소를 제거하고 반환
- Peek:  우선순위가 가장 높은(낮은) 요소 반환

> 데이터가 N개일 때, 구현 방식에 따른 시간 복잡도 비교
> 

| 구현방식 | 삽입 시간 | 삭제 시간 |
| --- | --- | --- |
| 리스트 | O(1) | O(N) |
| 힙(heap) | O(logN) | O(logN) |

## 힙(heap)의 특징

- 힙은 완전 이진 트리 자료구조의 일종
    - 완전 이진 트리는 배열을 사용해서 구현 가능하다
- 최댓값과 최솟값을 찾는 연산을 빠르게 하기 위해 만들어진 자료구조
- 힙에서는 항상 루트 노드를 제거
- 최소 힙(Min heap)
    - 루트 노드가 가장 작은 값을 가진다.
    - 따라서 값이 작은 데이터가 우선적으로 제거된다. → 오름차순
    - 최소 힙 구성 함수: Min-Heapify()
        - 상향식 - 부모 노드로 거슬러 올라가며 부모보다 자신의 값이 더 작은 경우에 위치를 교체한다.
        - 하향식 - 부모 노드에서 자식노드로 내려가며 자신의 값이 더 큰 경우에 위치를 교체한다.
- 최대 힙(Max heap)
    - 루트 노드가 가장 큰 값을 가진다.
    - 따라서 값이 큰 데이터가 우선적으로 제거된다. → 내림차순

<aside>
💡 최소힙에서 가장 작은 값을 찾는(Peek) 시간 복잡도: O(1)
최소힙에서 가장 작은 값을 빼는(Extract-Max) 시간 복잡도: O(logN)

</aside>

> 최소 힙에 새로운 원소가 삽입될 때
> 
<img width="802" alt="Untitled" src="https://github.com/user-attachments/assets/1a741ce9-667a-405c-b091-fa0a3df578d0">


- 원소가 삽입 되었을 때 최악의 경우 root node까지 올라간다.
- 트리의 깊이는 logN이기 때문에 O(logN)의 시간 복잡도를 유지할 수가 있다.

> 힙에서 원소가 삭제될 때
> 

<img width="580" alt="image" src="https://github.com/user-attachments/assets/3149bf59-3e37-4d3a-8e5d-9de8551ab82f">

- 원소가 제거 되었을 때 최악의 경우 leaf node까지 내려간다.
- 트리의 깊이는 logN이기 때문에 O(logN)의 시간 복잡도를 유지할 수가 있다.

⇒ 즉, 힙에서 원소를 꺼낼 때, 원소를 넣을 때 모두 O(logN)의 시간 복잡도를 만족한다.

### Heapify 과정

1. 단순 삽입 방식 - 단순히 N개의 데이터를 힙에 넣었다가 모두 꺼내는 작업은 정렬과 동일하다. (힙 정렬)
    - 각 요소를 삽입할 때마다 O(logN)의 시간이 걸리며, N개의 요소를 삽입하므로 전체 시간복잡도는 O(NlogN)
2. Bottom-Up 방식 - 배열의 마지막 요소에서 첫번째 요소로 거꾸로 올라가면서 각 요소에 대해 Heapify 호출하는 방식
    - 시간복잡도: O(N)
    
    > 시간복잡도 증명
    > 
    <img width="472" alt="Untitled" src="https://github.com/user-attachments/assets/a07da3f6-ec9d-46d5-aa44-e0ab93a6d240">

    
    N(노드의 수)=6
    
    - 각 h값마다 있는 노드의 수: [N/2^h]
    - h에 있는 노드 하나를 처리할 때 최대 시간복잡도: h
    - 각 층을 처리할 때 시간복잡도: h*[N/2^h]
    - 층은 1부터 logN까지

   <img width="482" alt="Untitled" src="https://github.com/user-attachments/assets/964f6f8a-a40b-4a5c-b7fd-87a8f683ba0d">
