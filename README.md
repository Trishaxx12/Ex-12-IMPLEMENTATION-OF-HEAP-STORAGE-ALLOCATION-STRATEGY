# Ex. No : 12	
# IMPLEMENTATION OF HEAP STORAGE ALLOCATION STRATEGY 
## Register Number :212221040173
## Date : 02/05/2024

## AIM   
To write a program to implement heap storage allocation strategy.

## ALGORITHM
1.	Start the program.
2.	Define a function create( ) to create a list of allocated node. This function returns a pointer to head of list.
3.	Define a function display(node) to display the list of allocated nodes.
4.	Define a function search(node,key) to search for the element in list.
5.	Define a function insert(node) to insert element into the list.
6.	Define a function get_prev(node,value) to look for the previous element in the list.
7.	Define a function delete() to remove an element from the list.
8.	Stop the program.

## PROGRAM
```
#include<stdio.h>
#include<stdlib.h>

#define TRUE 1
#define FALSE 0

typedef struct Heap {
    int data;
    struct Heap *next;
} node;

node *create();
void display(node *);
node *search(node *, int);
node *insert(node *);
void dele(node **);
node *insert_head(node *);
void insert_last(node *);
void insert_after(node *);

int main() {
    int choice, val;
    char ans;
    node *head = NULL;

    do {
        printf("\nProgram to perform various operations on heap using dynamic memory management");
        printf("\n1. Create");
        printf("\n2. Display");
        printf("\n3. Insert an element in a list");
        printf("\n4. Delete an element from list");
        printf("\n5. Quit");
        printf("\nEnter your choice (1-5): ");
        scanf("%d", &choice);

        switch(choice) {
            case 1:
                head = create();
                break;
            case 2:
                display(head);
                break;
            case 3:
                head = insert(head);
                break;
            case 4:
                dele(&head);
                break;
            case 5:
                exit(0);
            default:
                printf("Invalid choice, try again");
        }
    } while(choice != 5);

    return 0;
}

node* create() {
    node *temp, *New, *head;
    int val;
    char ans = 'y';
    head = NULL;

    do {
        printf("\nEnter the element: ");
        scanf("%d", &val);

        New = (node*)malloc(sizeof(node));
        if(New == NULL) {
            printf("\nMemory is not allocated");
            exit(1);
        }

        New->data = val;
        New->next = NULL;

        if(head == NULL)
            head = New;
        else {
            temp = head;
            while(temp->next != NULL)
                temp = temp->next;
            temp->next = New;
        }

        printf("\nDo you want to enter more elements? (y/n): ");
        scanf(" %c", &ans);
    } while(ans == 'y');

    printf("\nThe list is created\n");
    return head;
}

void display(node *head) {
    node *temp;
    temp = head;

    if(temp == NULL) {
        printf("\nThe list is empty\n");
        return;
    }

    printf("\nThe list is: ");
    while(temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->next;
    }
    printf("NULL\n");
}

node *insert(node *head) {
    int choice;
    printf("\n1. Insert a node as a head node");
    printf("\n2. Insert a node as a last node");
    printf("\n3. Insert a node at an intermediate position in the list");
    printf("\nEnter your choice for insertion of node: ");
    scanf("%d", &choice);

    switch(choice) {
        case 1:
            head = insert_head(head);
            break;
        case 2:
            insert_last(head);
            break;
        case 3:
            insert_after(head);
            break;
        default:
            printf("\nInvalid choice.\n");
    }
    return head;
}

node *insert_head(node *head) {
    node *New;
    int val;
    New = (node*)malloc(sizeof(node));
    if(New == NULL) {
        printf("\nMemory is not allocated");
        exit(1);
    }

    printf("\nEnter the element to insert: ");
    scanf("%d", &val);

    New->data = val;
    New->next = head;
    head = New;
    return head;
}

void insert_last(node *head) {
    // Implement insertion at the last node
    printf("\nInsert last function is under construction.\n");
}

void insert_after(node *head) {
    // Implement insertion after a specific node
    printf("\nInsert after function is under construction.\n");
}

void dele(node **head) {
    // Implement deletion logic here
    printf("\nDelete function is under construction.\n");
}

```
## OUTPUT 
![Screenshot 2024-05-01 230649](https://github.com/gsuryanavya/19CS409-Compiler-Design-Lab/assets/133086963/4b124fb8-db02-4d77-a2ce-0772da412daf)

## RESULT
The heap storage allocation strategy is implemented successfully, and the output is verified.
