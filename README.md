# test_6_2
#include <stdio.h>
#include <stdlib.h>
//查找
typedef struct BSTNode{
	int key;
	struct BSTNode* lchild,*rchild;
}BSTNode,*BSTree;
//二叉排序树的插入(递归实现）
int BST_Insert(BSTree &T,int k){
	if(T == NULL){
		T=(BSTree)malloc(sizeof(BSTNode));
		T->key = k;
		T->lchild = T->rchild;
		return 1;
	}
	else if(k == T->key)
		return 0;
	else if(k > T->key)
		return BST_Insert(T->rchild,k);
	else
		return BST_Insert(T->rchild,k);
}
//构造
void Creat_BST(BSTree T,int str[],int n){
	T = NULL;//初始化
	int i;
	while(i < n){
		BST_Insert(T,str[i]);
		i++;
	}
}
//平衡二叉树
typedef struct AVLNode{
	int key;
	int balance;
	struct AVLNode* lchild,*rchild;
}AVLNode,*AVLTree;
//B树
struct Node{
	ElemType key[4];
	struct Node* child[5];
	int num;
};
//排序
//直接插入排序
void InsertSort(int A[],int n){
	int i,j,temp;
	for(i=1;i<n;i++)
		if(A[i-1] > A[i]){
			temp = A[i];
			for(j=i-1;j>=0 && A[j]>temp;--j)
				A[j+1] = A[j];
			A[j+1] = temp;
		}
}
//哨兵
void InsertSort(int A[],int n){
	int i,j;
	for(i=2;i<n;i++)
		if(A[i-1] > A[i]){
			A[0] = A[i];
			for(j=i-1;A[j]>A[0];--j)
				A[j+1] = A[j];
			A[j+1] = A[0];
		}
}
//折半插入排序
void InsertSort(int A[],int n){
	int i,j,low,high,mid;
	for(i=2;i<=n;i++){
		A[0] = A[i];
		low=1,high=i-1;
		while(low<=high){
			mid = (low + high)/2;
			if(A[mid] > A[0])
				high = mid - 1;
			else
				low = mid + 1;
		}
		for(j=i-1;j>high+1;--j)
			A[j+1] = A[j];
		A[high+1] = A[0];
	}
}
//希尔排序
void ShellSort(int A[],int n){
	int d,i,j;
	for(d=n/2;d>=1;d=d/2)
		for(i=d+1;i<=n;++i)
			if(A[i-1] > A[i]){
				A[0] = A[i];
				for(j=i-d;j>0 && A[0]<A[j];j-=d)
					A[j+d] = A[j];
				A[j+d] = A[0];
			}
}
