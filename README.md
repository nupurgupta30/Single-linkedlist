# Single-linkedlist
#include<stdio.h>
#include<stdlib.h>

struct node
{int data;
struct node *next;
}*head = NULL;
void newLL()
{struct node *t = NULL;
struct node *p = NULL;
t = (struct node*)malloc(sizeof(struct node));
scanf("%d",&(t->data));
t->next=NULL;
if(head == NULL)
head = t;
else
{p = head;
while(p->next!= NULL)
p=p->next;
p->next= t;
}
}
void display()
{struct node *q = head;
if(head == NULL)
printf("Empty List");
else{
printf("\nHEAD->");
while(q!= NULL)
{printf("%d->",q->data);
q=q->next;
}
printf("NULL\n");
}
}
void addbeg()
{struct node *newNode = (struct node*) malloc (sizeof(struct node));
printf("Enter data :");
scanf("%d",&newNode->data);
newNode->next = head;
head = newNode;
printf("Done");
}
void addend()
{struct node *newNode;
newNode = (struct node*) malloc(sizeof(struct node));
printf("Enter data :");
scanf("%d",&newNode->data);
newNode->next = NULL;
struct node *temp = head;
if(head == NULL)
head = newNode;
else
{while(temp->next != NULL)
temp = temp->next;
temp->next = newNode;
}
printf("Done");
}
void addpos()
{int pos;
struct node *newNode;
struct node *temp = head;
newNode = (struct node*) malloc(sizeof(struct node));
printf("Enter Position :");
scanf("%d",&pos);
printf("Enter data :");
scanf("%d",&newNode->data);
for(int i=2; i < pos; i++)
{if(temp->next != NULL)
temp = temp->next;
}
newNode->next = temp->next;
temp->next = newNode;
printf("Done");
}
void delbeg()
{if(head == NULL)
printf("Empty List");
else
{ head=head->next;
printf("Done"); }
}
void delend()
{struct node* temp = head;
if(temp == NULL)
printf("Empty list");
else if(head->next==NULL)
{head =NULL;
printf("Done");
}
else
{while(temp->next->next!=NULL)
temp = temp->next;
temp->next = NULL;
printf("Done");
}
}
void delpos()
{if(head == NULL)
printf("Empty list");
else
{int pos;
printf("Enter Position :");
scanf("%d",&pos);
if(pos==1)
head = head->next;
else{
struct node *temp = head;
for(int i=2; i< pos; i++)
{
if(temp->next!=NULL)
temp = temp->next;
}
temp->next = temp->next->next;
}
printf("Done");
}
}
int main()
{int c,size,i,x=1;
printf("New List :-\n");
printf("\tEnter initial size of new list :");
scanf("%d",&size);
for(i=0;i<size;i++)
{printf("Enter Data %d:",i+1);
newLL();
}
printf("\t\tLinked List Created!!");
do
{printf("\n-----------------------------------------------------------\n");
printf("1.New Node(First)   \t2.New Node(Last)     \t3.New Node(AtPosition)\n");
printf("4.Delete Node(First)\t5.Delete Node(Last)  \t6.Delete Node(AtPosition)\n");
printf("7.Display           \t9.exit");
printf("\n\t\tEnter Choice :");
scanf("%d",&c);
printf("\n-----------------------------------------------------------\n");
switch(c)
{case 1: {addbeg(); break; }
case 2: {addend(); break; }
case 3: {addpos(); break; }
case 4: {delbeg(); break; }
case 5: {delend(); break; }
case 6: {delpos(); break; }
case 7: {display(); break; }
case 8: {x=0;break;exit(0);    }
default:{printf("\n\n\t\tError!!!!!"); break;}
}
}while(x);
return 0;
}

