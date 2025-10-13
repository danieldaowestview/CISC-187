# Activity 6: Stacks and Queues

## Code
Task
Using Figure 17 as a model, in the book Data Structures in C++, illustrate the result of each operation in the sequence PUSH(S,4), PUSH(S,1), PUSH(S,3), POP(S), PUSH(S,8), and POP(S) on an initially empty stack S
```
S = []
S = [4]
S = [1, 4]
S = [3, 1, 4]
S = [1, 4]
S = [8, 1, 4]
S = [1, 4]
```
Using Figure 18 as a model, in the book Data Structures in C++, illustrate the result of each operation in the sequence ENQUEUE(Q,4), ENQUEUE(Q,1), ENQUEUE(Q,3), DEQUEUE(Q), ENQUEUE(Q,8), and DEQUEUE(Q) on an initially empty queue Q
Q = []
Q = [4]
Q = [4, 1]
Q = [4, 1, 3]
S = [1, 3]
S = [1, 3, 8]
S = [3, 8]
Rewrite ENQUEUE and DEQUEUE to detect underflow and overflow of a queue. (see Listings 4 & 5 in the book). Code is not required. 1 pt
Listing Pseudocode of QUEUE-EMPTY(Q)
```
if Q.top == 0
  return TRUE
else return FALSE
```
Listing 4 Pseudocode of ENQUEUE(Q,x)
```
Q[Q.tail] = x
**if (Q.tail + 1 == Q.head) or (Q.tail == Q.length and Q.head == 1)
    error "overflow"**
if Q.tail == Q.length
    Q.tail = 1
else Q.tail = Q.tail + 1
```
Listing 5 Pseudocode of DEQUEUE(Q)
```
x = Q[Q.head]
**if Q.head == Q.tail
  error "underflow"**
if Q.head == Q.length
    Q.head = 1
else Q.head = Q.head + 1
return x
```
A stack allows insertion and deletion of elements at only end, and a queue allows insertion at one end and deletion at the other end, a deque (double-ended queue) allows insertion and deletion at both ends. Write four 
O(1)-time procedures to insert elements into and delete elements from both ends of a deque implemented by an array.

Insert at Front
```
if deque is full
    error "overflow"
front = (front - 1 + n) mod n
Deque[front] = x
```
Insert at Rear
```
if deque is full
    error "overflow"
Deque[rear] = x
rear = (rear + 1) mod n
```
Delete from Front
```
if deque is empty
    error "underflow"
x = Deque[front]
front = (front + 1) mod n
```

Delete from Rear
```
if deque is empty
    error "underflow"
rear = (rear - 1 + n) mod n
x = Deque[rear]
```
