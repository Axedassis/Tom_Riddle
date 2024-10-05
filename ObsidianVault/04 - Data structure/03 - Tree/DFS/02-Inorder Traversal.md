
(eu tinha criado a porcaria do arquivo inteiro mas ele só sumiu)
ent fica com o importante e o link k k https://www.geeksforgeeks.org/inorder-traversal-of-binary-tree/)

==left - root - right==

![[inorder.gif]]

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

void DFS_print_inorder(st_node *root)
{
	if(root == NULL)
		return;

	DFS_print_inorder(root->left);
	printf("%d\n", root->data);
	DFS_print_inorder(root->right);
}

int main(void)
{
	st_node *root = create_Node(1);
	root->right = create_Node(3);
	root->right->right = create_Node(6);
	root->left = create_Node(2);
	root->left->right = create_Node(5);
	root->left->left = create_Node(4);

	DFS_print_inorder(root);
	return (0);
}