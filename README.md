# -
第一个仓库，如何创建链表
#include <stdio.h>
#include <stdlib.h>
struct Node//定义一个数据类型
{
	int data;
	struct Node* pNext;//该数据类型中有一个整型数据和指向下一个同类型的指针
};
struct Node* create_list(void);
void traverse_list(struct Node* pHead);
int main()
{
	struct Node* pHead;//pHead用来存放链表头结点的地址
	pHead = create_list();//创建一个非循环单链表，并将头指针赋给pHead
	traverse_list(pHead);//对链表进行输出
	return 0;
}
struct Node* create_list(void)
{
	int len;//用来存放有效节点的个数
	int i;
	int val;//用来临时存放用户输入的结点的值
	struct Node* pHead = (struct Node*)malloc(sizeof(struct Node));
	if (NULL == pHead)
	{
		printf("分配失败，程序终止！\n");
		exit(-1);
	}
	struct Node* pTail = pHead;
	pTail->pNext = NULL;
	printf("请输入您需要生成的链表节点的个数：len=");
	scanf_s("%d", &len);
	for (i = 0; i < len; ++i)
	{
		printf("请输入第%d个节点的值：", i + 1);
		scanf_s("%d", &val);
		struct Node* pNew = (struct Node*)malloc(sizeof(struct Node));
		if (NULL == pNew)
		{
			printf("分配失败，程序终止！\n");
			exit(-1);//终止程序
		}
		pNew->data = val;
		pTail->pNext = pNew;
		pNew->pNext = NULL;
		pTail = pNew;
	}
	return pHead;
}
	
	void traverse_list(struct Node* pHead)
	{
		struct Node* p = pHead->pNext;
		while (NULL != p)
		{
			printf("%d\n", p->data);
			p = p->pNext;
		}
	}
