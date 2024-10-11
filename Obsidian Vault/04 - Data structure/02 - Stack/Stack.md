Similar to [[Queue]] but that follows a particular order in which the operations are performed.
The order may be ***LIFO(Last In First Out)**** or ***FILO(First In Last Out)****. <- same thing

It behaves like a stack of plates, where the last plate added is the first one to be removed.
![[Pasted image 20240926233300.png]]

To implement the stack, it is required to maintain the ***pointer to the top of the stack*** , which is the last element to be inserted because ***we can access the elements only on the top of the stack.***

---
#### Basic operations
- Push -> Adds an element to the top of the stack
	Adds an item to the stack. If the stack is full, then it is said to be an ****Overflow condition.****

- Pop -> Remove the top element from the stack
	If the stack is empty, then it is said to be an ****Underflow conditio****

- Peek -> Returns the top element without removing it
	Returns the top element of the stack.

- isEmpty -> Checks if the stack is empty
	Returns true if the stack is empty, else false.

- isFull -> Checks if the stack is full(in case of fixed-size arrays).
	Returns true if the stack is full, else false.
	
---
#### Types of stack

**Fixed size Stack**
	a fixed size stack has a fixed size and cannot grow or shrink dynamically
		-> If the stack is full and an attempt is made to add an element to it, an ==overflow error ==occurs.
		->If the stack is empty and an attempt is made to remove an element from it, an ==underflow error ==occurs.

**Dynamic Size Stack**
	A dynamic size stack can grow or shrink dynamically.
		A dynamic size stack can grow or shrink dynamically. This type of stack is implemented using a ==linked list==, as it allows for easy resizing of the stack.

---
#### Synatax

In an array-based implementation, the push operation is implemented by incrementing the index of the top element and storing the new element at that index. The pop operation is implemented by returning the value stored at the top index and then decrementing the index of the top element.

In a linked list-based implementation, the push operation is implemented by creating a new node with the new element and setting the next pointer of the current top node to the new node. The pop operation is implemented by setting the next pointer of the current top node to the next node and returning the value of the current top node.