`Binary Tree` is out first non-linear data structure, each node has at most two children and which children are referred as the `left child` and `right child`.

![[Pasted image 20240929182014.png]]


The **topmost node** in a binary tree is called ==root==, and the bottom-most nodes area called ==leaves==

---
### Representation of Binary Tree

each node in a Binary Tree has three parts:
- Data
- Pointer to left child
- Pointer to right child
![[Pasted image 20240929182642.png]]

The basic Syntax to create a binary tree node is:

```c
typedef struct Node
{
	int data;
	struct Node* left;
	struct Node* right;
} st_node;

st_node new_Node(int value)
{
	st_node *new_node  = (st_node *)malloc(sizeof(st_node));
	new_node->data = value;
	new_node->left = new_node->right = NULL;
	return (new_node);
}

```

Assign this node into a binary data structure like this
![[Pasted image 20240929183242.png]]
is gonna be something like this:
```c
int main(void)
{
st_node *first_element = new_Node(2);
st_node *second_element = new_Node(3);
st_node *third_element = new_Node(4);
st_node *four_element = new_Node(5);

first_element->left = second_element;
first_element->right = third_element;
second_element->left = four_element;

return (0);
}
```

---
### Terminologies in Binary Tree
- Nodes
- Root
- Leaf Nodes
- Parent Nodes
- Child Nodes
- Depth of a Node
	-The number of edges from a specific node to the root node. The depth of the root node is zero.
- Height of a Binary 
	-The number of nodes from the deepest leaf node to the root node.

Subtrees = is a parent with 2 child
Siblings = is 2 parent in the same level

![[Pasted image 20240929184107.png]]

---
### Properties

- The maximum number of nodes possible at level L is 2^L
	L = 0 -> 1, L = 1 -> 2, L = 2 -> 4, ...

- The maximum number of node in binary tree of height H is 2^(h+1) - 1
	H = 3 -> 2^(2+1) - 1 =  7 Nodes

---

### Types of Binary Tree

==On the basis of Numbers of Children==
	-[[01 - Full Binary Tree]]
	-[[02 - Degenerate Binary Tree]]

---

### Operations on Binary Tree
Traversal in Binary Tree involves visiting all the nodes of the binary tree. Traversal algorithms can be classified broadly into two categories ==DFS== and ==BFS==

#### DFS(Depth-First Search)
DFS explorer as far down a branch as possible before backtracking, it is implemented using `recursion`

the main Traversal methods in DFS is:

[[01-Preorder Traversal]] Visits the `node` first, then `left subtree`, then `right subtree`.

[[02-Inorder Traversal]] Visits `left subtree`, then the `node`, then the `right subtree`.

[[03-Postorder Traversal]] - Visits `left subtree`, then `right subtree`, then the `node`.

**RESUME**
```c
// In-order DFS: Left, Root, Right
void inOrderDFS(struct Node *node){
    if (node == NULL) return;
    inOrderDFS(node->left);
    printf("%d ", node->data);
    inOrderDFS(node->right);
}

// Pre-order DFS: Root, Left, Right
void preOrderDFS(struct Node *node){
    if (node == NULL) return;
    printf("%d ", node->data);
    preOrderDFS(node->left);
    preOrderDFS(node->right);
}

// Post-order DFS: Left, Right, Root
void postOrderDFS(struct Node *node){
    if (node == NULL) return;
    postOrderDFS(node->left);
    postOrderDFS(node->right);
    printf("%d ", node->data);
}
```

#### BFS(Breadth-First Search)

BFS explores all nodes at the present ==depth== before moving on to nodes at the next depth level. It is typically implemented using a ==queue==. BFS in a binary tree is commonly referred to as ==Level Order Traversal==.



