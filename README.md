#include<stdio.h>
#include<conio.h>
#include<malloc.h>
#include<process.h>
struct singly
{
int data;
struct singly *next;
} ;
struct singly *start=NULL;
void create(int);
void traverse();
void ins_first(int);
void del_first();
void main()
{
int ch;
int arr[10]={12,33,44,11,56,78,90,19,20,66};
int i=-1;
while(1)
	{
	clrscr();
	printf("Press 1 for creation\n");
	printf("Press 2 for traverseing\n");
	printf("Press 3 for ins_first\n");
	printf("Press 4 for del_first\n");
	printf("Press 5 for exit\n");
	printf("Select your option\n");
	scanf("%d",&ch);
	if(ch==1)
		{
		create(arr[++i]);
		}
	else if(ch==2)
		{
		traverse();
		getch();
		}
	else if(ch==3)
		{
		ins_first(arr[++i]);
		}
	else if(ch==4)
		{
		del_first();
		}
	else if(ch==5)
		{
		exit(0);
		}

	}

}
void create(int n)
{
struct singly *tmp,*tmp1;
if(start==NULL)
	{
	tmp=(struct singly*)malloc(sizeof(struct singly));
	start=tmp;
	tmp->next=start;
	tmp->data=n;
	}
else
	{
	tmp=start;
	while(tmp->next!=start)
		{
		tmp=tmp->next;
		}
	tmp1=(struct singly*)malloc(sizeof(struct singly));
	tmp1->next=tmp->next;
	tmp->next=tmp1;
	tmp1->data=n;
	}
}
void traverse()
{
struct singly *tmp;
tmp=start;
while(tmp->next!=start)
	{
	 printf("%d\n",tmp->data);
	 tmp=tmp->next;
	}
printf("%d\n",tmp->data);
}
void ins_first(int n)
{
struct singly *tmp,*tmp1;
tmp=start;
while(tmp->next!=start)
	{
	tmp=tmp->next;
	}
tmp1=(struct singly*)malloc(sizeof(struct singly));
tmp1->next=start;
start=tmp1;
tmp->next=start;
tmp1->data=n;
}
void del_first()
{
struct singly *tmp,*tmp1;
tmp=start;
while(tmp->next!=start)
	{
	tmp=tmp->next;
	}
tmp1=start;
start=tmp1->next;
tmp->next=start;
free(tmp1);

}
