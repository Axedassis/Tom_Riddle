==Root-Left-Right==

The steps to implement `preorder Traversal - DFS - Binary Tree` is 
visited the `root` node of binary trees, then the `left subtree` at last the `right subtree` as the gif in below.

![[preordercom-gif-maker.gif]]

The algorithm to implement the Preorder Traversal of Binary Tree
is:

1. if ==root== is ==NULL== then return
2. Process root (verify, print or do something)
3. Preorder (root -> left)
4. Preorder (root -> right)

a visual representation of this is:

```md
Input :…….A  
…………../ …….\  
………..B ………..C  
……../……\  
……D……..E  
Output : ABDEC
```

---
### Program to implement Preorder Traversal

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct Node
{
	int data;
	struct Node *left;
	struct Node *right;
} st_node;

st_node *create_Node(int value)
{
	st_node *new_node = (st_node *)malloc(sizeof(st_node));
	if(new_node == NULL)
	{
		printf("Unable to allocated memory");
		exit (EXIT_FAILURE);
	}
	new_node->data = value;
	new_node->left = new_node->right = NULL;
	return (new_node);
}

void DFS_print_preorder(st_node *root)
{
	if(root != NULL)
	{
		printf("%d\n", root->data);
		DFS_print_preorder(root->left);
		DFS_print_preorder(root->right);
	}
	return ;
}

int main(void)
{
	st_node *root = create_Node(1);
	root->right = create_Node(3);
	root->right->right = create_Node(6);
	root->left = create_Node(2);
	root->left->right = create_Node(5);
	root->left->left = create_Node(4);

	DFS_print_preorder(root);
	return (0);
}
```
