### auto 与 &

```c++

for(auto e:sequence)
将sequence中的每个元素都拷贝到对象e中

for(auto &e:sequence)
给sequence 中的每个对象都取了别名e

```

### 内存分配问题

//二:动态内存分配问题:c中 供程序使用的存储空间，有程序区，静态存储区，动态存储区。

//c++中，我们把内存进一步详细分为5个区域，

**//(1)栈:一般函数内的局部变量都会放在这里，由编译器自动分配和释放。**

**//(2)堆:程序员ma1loc/new分配，用free/delete来释放。忘记释放后，系统会回收。**

//(3)全局/静志存储区:放全局变量和静志变量static。 程序结束时系统释放。

//(4)常量存储区:I Love China :

//(5)程序代码区

```c
#define NULL 0

void* malloc(int NumBytes);
void free(void *FistBytes);
char *p = NULL;
p = (char *)malloc(5*sizeof(int));
strcpy(p,"hello world!");//不安全，数据会覆盖未知的堆位置
strcpy_s(p,"hello world!");//报错，所分配的堆空间不足
free(p);

```



```c++
#define NULL 0

void* malloc(int NumBytes);
void free(void *FistBytes);
char *p = NULL;
p = new int;//将开辟的一个2字节的int型地址返回给p
p = new int(4);//将开辟的一个2字节的int型地址返回给p,并且该地址的值为4
p = new int[5];//将开辟的五个2字节的int型地址返回给p
delete p;
delete p;
delete[] p;//结合free就知道了
```



### NULL 与 nullptr

```c++
#define nullptr (void*)
#define NULL   0  |   (void*)//避免指数与整数的混淆
typdid(NULL) // int
typdid(nullptr) //nullptr_t

```

**总结：对于指针的初始化，能用nullptr就用它。**



### 结构体 传参

```c++
//引用传参，效率高
void do(struct &tmp)
//结构体指针作为参数传参，效率高
void do(struct* tmp)
    tmp->name = "sd";
do(&mp);

```

