### 顺序表

##### 存储结构

```C
//静态分配
#define MaxSize 50
typedef struct
{
    ElemType data[MaxSize];
    int length;
}SqList;
```

```C
//动态分配
#define InitSize 100
typedef struct
{
    ElemType *data;
    int MaxSize, length;
}SeqList;
```

```C
//动态分配语句
L.data = (ElemType*)malloc(sizeof(ElemType)*InitSize);
L.data = new ElemType[InitSize];
```

##### 基本操作

```C
//插入
bool ListInsert(SqList &L, int i, ElemType e){
    if (i<1 || i>L.length+1)
        return false;
    if (L.length>=MaxSize)
        return false;
    for (int j=L.length; j>=i; j--)
        L.data[j] = L.data[j-1];
    L.data[i-1] =e;
    L.length++;
    return true;
}
```

```C
//删除
bool ListDelete(SqList &L, int i, ElemType &e){
    if (i < 1 || i > L.length)
        return false;
    e = L.data[i=1];
    for (int j = i; j < L.length; j++)
        L.data[j-1] = L.data[j];
    L.length--;
    return true;
}
```

```C
//按值查找
int LocateElem(SqList L, ElemType e){
    int i;
    for ( i = 0; i < L.length; i++)
        if (L.data[i]==e)
            return i + 1;
        return 0; 
}
```

### 单链表

##### 存储结构

```C
typedef struct LNode
{
    ElemType data;
    struct LNode *next;
} LNode, *LinkList;
```

##### 基本操作

```C
//头插法建立单链表
LinkList Link_HeadInsert(LinkList &L)
{
    LNode *s;
    int x;
    L = (LinkList)malloc(sizeof(LNode));
    L->next = NULL;
    scanf("%d", &x);
    while (x != 9999)
    {
        s = (LinkList)malloc(sizeof(LNode));
        s->data = x;
        s->next = L->next;
        L->next = s;
        scanf("%d", &x);
    }
    return L;
}
```

```C
//尾插法建立单链表
LinkList List_TailInsert(LinkList &L)
{
    int x;
    L = (LinkList)malloc(sizeof(LNode));
    LNode *s, *r = L;
    scanf("%d", &x);
    while (x != 9999)
    {
        s = (LinkList)malloc(sizeof(LNode));
        s->data = x;
        r->next = s;
        r = s;
        scanf("%d", &x);
    }
    r->next = NULL;
    return L;
}
```

```C
//按序号查找
LNode *GetElem(LinkList L, int i)
{
    int j = 1;
    LNode *p = L -> next;
    if (i == 0)
        return L;
    if (i < 1)
        return NULL;
    for (p && j < i)
    {
        p = p -> next;
        j++；
    }
    return p;
}
```

```C
//按值查找表结点
LNode *LocateElem(LinkList L, ElemType e)
{
    LNode *p = L -> next;
    while (p != NULL && p -> data != e)
        p = p -> next;
    return p;
}
```

```C
//将值为e的结点插入到第i个位置
LinkList InsertElem(LinkList &L, int i, ElemType e)
{
    s = (LinkList)malloc(sizeof(LNode));
    s -> data = e;
    LNode *p = GetElem(L, i-1);
    s -> next = p -> next;
    p -> next = s;
    return L;
}
```

```C
//删除第i个结点
LinkList List_Delete(LinkList &L, int i)
{
    LNode *p, *q;
    if (i == 0)
        return L;
    if (i < 1)
        return NULL;
    p = GetElem(L, i-1);
    q = p -> next;
    p -> next = q -> next;
    free(q);
    return L;
}
```

```C
//删除结点*p
LinkList LNode_Delete(LinkList &L, p)
{
    LNode *q = p -> next;
    p -> data = p -> next -> data;
    p -> next = q -> next;
    free(q);
    return L;
}
```

