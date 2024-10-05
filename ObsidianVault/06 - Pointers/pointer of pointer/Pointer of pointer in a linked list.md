in a linked list to avoid the the need to assign the new header pointer every time as in the example below.
```c
typedef struct Node
{
	int data;
	struct Node *next;
}

st_node *insert_node(st_node *list, st_node *new_node)
{
	if(list == NULL)
	{
		list = new_node;
		return (head);
	}
	new_node->next = list;
	list = new_node;
	return (list);
}

int main(void)
{
	st_node *list = NULL;
	list = insert_node(list, new_node0); //new_node in this example does'n exist
	list = insert_node(list, new_node1);
	list = insert_node(list, new_node2);
	list = insert_node(list, new_node3);
}
```

we can use a pointer of a pointer to allow us to change the head pointer of a linked list, as in the example below:

```c
typedef struct Node
{
	int data;
	struct Node *next;
}
//recive a pointer to head pointer of a linked list
void insert_node(st_node **list, st_node *new_node)
{
	if(*list == NULL)
	{
		*list = new_node;
		return;
	}
	new_node->next = *head;
	*head = new_node;
	return;
}

int main(void)
{
	st_node *list = NULL;
	list = insert_node(list, new_node0); //new_node in this example does'n exist
	list = insert_node(list, new_node1);
	list = insert_node(list, new_node2);
	list = insert_node(list, new_node3);
}
```

in the above case we receive a pointer to a pointer that's the header pointer to the linked list

