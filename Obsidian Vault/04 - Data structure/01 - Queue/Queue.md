Similar to Stack(FILO) the queue follow the FIFO(first in first out), a good a analogy to think what's a queue as a line of people waiting to receive something in sequential order which starts from the beginning of the line

the main difference between stack and queue is the removing. in the **Stack** we remove the item most recently added, in a queue, we remove the item the **least** recently added.

![[Pasted image 20240922205253.png]]

---
the top of this data structure can called by **Front** or **Head**. and the final can be called by **Back/Tail/Rear**.

---
### Basic Operations
Enqueue() -> insert an element at the end of queue
Dequeue() -> remove an element at the initial of queue
isEmpty() -> verify if the queue is empty
isFull() -> verify if the queue is full
Front() -> return the element at front of queue (without removing it)
Rear() -> return the element at the end of queue (without removing it)
Size() -> return the total of element in a queu

---
### Types of queue
**Simple Queue** -> also know as `linear queue` 
**Circular Queue** -> is similar to linear queue except for the fact the last element is always connect to the first element.
**Priority** -> arrranges the elements in a queue based on some priority, as example the values.
**Dequeue** -> also know as `Double Ended Queue`, an element can be added or remove from both sides of queue.

---
### Advantages and Disadvantages

**Advantages** -> easy to implement and has fixed size.
	**Disadvantages** -> Fixed size can be a problem. and Resizing this queue can be another problem.

---
### Code

**Creating**
```c
typedef struct Queue{
	int front, rear, size; //some meadata to handle with the queue
	unsigned int capacity; 
	int *array;
} st_queue;

struct *createQueue(unsigned int capacity)
{
	st_queue *queue = (st_queue *)malloc(sizeof(st_queue));
	if(queue == NULL)
		return;
	queue->size = queue.front = 0;
	queue->rear = -1;
	queue->array = (int *)malloc(sizeof(int) * capacity);
	if(array == NULL)
		return;
	return (queue);
} 
```

Size != Capacity-> Size refers to the how many elements are in the queue similarly the capacity refers to how many elements the queue can comport.

! the `front` is typically initialized to 0 to signify the starting position of the queue, where elements will be dequeued (removed).

The `rear` is always initialized to -1 because it tracks the position of the most recently added element. On the first `enqueue`, the `rear` moves from -1 to 0, which is the initial index position in the queue

---

**Insert Values**
```c
void enqueu(st_queue *queue, int value)
{
	if(isFull(queue))
		return;
	queue.rear = (queue.rear + 1) % (queue.capacity); //circular queue
	/*
	capity = 5
	size = 4
	rear = 4
	append more 1 element to queue
	(4 + 1) % 5 = 0. the rear backs to the initial position
	
	(3 + 1) % 5 = 4 the rear still < 5, indicate that queue still had space
	*/
	queue.array[queue.rear] = value;
	queue.size = queue.size + 1;
}
```

the `isFull` function basically is a function that see if the `size` is equal to `capacity`

```c
int isFull(st_node *queue)
{
	return (queue->size == queue->capacity)
}
```
---
**Delete elements**
```c
int dequeue(st_queue *queue)
  if (isEmpty(queue))
        return INT_MIN; //bufferUnderFlow return the Minimun Size.
	int item = queue->array[queue->front];
	queue->front = (queue->front + 1) % queue->capacity
	queue->size = queue->size - 1;
	return (item);
```
!when we had a buffer underflow we had to return the `Minimum int`

!It is important to note that because we have an array with a fixed size, we cannot actually remove a value from it. Instead, what we do is increase our 'trackers', which would be the front and rear.

