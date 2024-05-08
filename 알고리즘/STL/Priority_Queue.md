
#### 우선순위 큐?
설정된 우선순위에 따라 가장 Top을 유지하고 먼저 Pop이 되는 큐
내부적으로 Heap의 자료구조를 갖는다.

1. empty : priorityqueue가 비어있는지 확인한다.
2. size : priorityqueue의 크기를 확인한다.
3. top : priorityqueue 내부의 제일 우선순위의 값을 보여준다.
4. push : priorityqueue에 값을 삽입한다.
5. emplace : priorityqueue에 구조를 삽입한다.
6. pop : priorityqueue에서 제일 우선순위의 값을 제거한다.
7. swap : 두개의 priorityqueue를 swap한다.(내부를 서로 바꾼다.)

```c++
priority_queue<자료형, 구현체, 비교연산자> pq;

#example
priority_queue <int, vector<int>, greater<int> > pq;
-> int 자료형이 작은값이 우선되게 선언
```
