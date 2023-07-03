# C-p37-6-
C语言学习笔记  p37 指针详解(6)
#include<stdio.h>
#include<stdlib.h>
int Add(int x,int y)
{
    return x+y;
}
int main()
{
    //指针数组
    int* arr[10];
    //数组指针
    int* (*pa)[10]=&arr
    //函数指针
    int (*pAdd)(int ,int)=Add;
    int sum=(*pAdd)(1,2);
    printf("sum=%d\n",sum);
    //函数指针的数组
    int(*pArr[5])(int,int)
    //指向函数指针数组的指针
    int(*(*ppArr)[5])(int,int)=&pArr;
    return 0;
}

//回调函数
//通过函数指针来调用的函数
void bubble_sort(int arr[],int sz)
{
    int i=0;
    for(i=0;i<sz-1;i++)
    {
        //一趟冒泡排序
        int j=0;
        //趟数
        for(j=0;j<sz-1-i;j++)
        {
            if(arr[j]>arr[j+1])
            {
                int tmp=arr[i];
                arr[j]=arr[j+1];
                arr[j+1]=tmp;
            }
        }
    }
}

struct Stu
{
    char name[20];
    int age;
};

int main()
{
    int arr[10]={9,8,7,6,5,4,3,2,1};
    int sz=sizeof(arr)/sizeof(arr[0]);
    struct Stu s[3]={{"zhangsan",20},{"lisi",30},{"wamgwu",10}};//如果是结构体数组或浮点型就不能用这个冒泡排序
    float f[]={9.0,8.0,7.0,6.0,5.0,4.0};
    qsort(arr,sz,sizeof(arr[0]),cmp_int);
    bubble_sort(arr,sz);
    int i=0;
    for(i=0;i<sz;i++)
    {
        printf("%d",arr[i]);
    }
    return 0;
}
//因为不够泛用，所以有一个qsort库函数
//函数原型:
//void qsort(void* base,size_tnum,size_t width,int(_cdecl* compare)(const void* elem1,const void* elem2));
//void* base,目标数组起始地址    1注：void*类型指针不能进行解引用，因为类型不确定，所以访问字节数无法确定    2注：void*的类型不能进行+-整数的操作
//size_tnum,数组元素个数
//size_t width,第一个元素大小(单位是字节)
//int(_cdecl* compare)(const void* elem1,const void* elem2)，比较方法
int main()
{
    //比较两个整形值的
    return *(int*)e1 -*(int*)e2;
    //相减=0则相等，第一个>第二个返回正数，第一个<第二个返回负数
    return 0;
}

//浮点型打印
int cmp_f;oat(const void* e1,const void* e2)
{
    if(*(float*)e1==*(float*)e2)
        return 0;
    else if(*(float*)e1>*(float*)e2)
        return 1;
    else
        return -1;
}
void test2()
{
    float f[]={9.0,8.0,7.0,6.0,5.0,4.0};
    int sz=sizeof(f)/sizeof(f[0]);
    qsort(f,sz,sizeof(f[0]),cmp_float);
    int j=0;
    for(j-0;j<sz;j++)
    {
        printf("%f",f[j]);
    }
}
//将test2放入main函数内部就行了

//结构体类型的比较函数
int cmp_stu_by_age(const void*e1,const void* e2)
{
    return ((struct Stu*)e1->age-((struct Stu*)e2)->age;
}
//此例拿的年龄比
