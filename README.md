# 简介
	在进行算法描述之前进行了数据结构的知识的学习，大部分都是基础知识的学习与概念上的认知，没有涉及太多的程序，从这一部分开始，主要进行代码上的编写与调试！首先从简单的算法起步，逐步深入！
## 命名空间
命名空间是ANSIC++引入的可以由用户命名的作用域，用来处理程序中常见的同名冲突。
命名空间：实际上就是一个由程序设计者命名的内存区域，程序设计者可以根据需要指定一些有名字的空间域，把一些全局实体分别放在各个命名空间中，从而与其他全局实体分隔开来。 
        
```c++
        namespace ns1
        {
            int a；
            double b;
        }
```

namespace 是定义命名空间所必须写的关键字，ns1 是用户自己指定的命名空间的名字(可 以用任意的合法标识符，这里用ns1是因为ns是namespace的缩写，含义请楚)，在花括号内是声明块，在其中声明的实体称为命名空间成员(namespace member)。现在命名空间成员包括变量a和b，注意a和b仍然是全局变量，仅仅是把它们隐藏在指定的命名空间中而已。如果在程序中要使用变量a和b，必须加上命名空间名和作用域分辨符“::”，如ns1::a，ns1::b。这种用法称为命名空间限定(qualified)，这些名字(如ns1::a)称为被限定名 (qualified name)。C++中命名空间的作用类似于操作系统中的目录和文件的关系，由于文件很多，不便管理，而且容易重名，于是人们设立若干子目录，把文件分别放到不同的子目录中，不同子目录中的文件可以同名。调用文件时应指出文件路径。 

```c++
namespace Helper{
	int * generatearray(int n,int arrH,int arrL)
	{
		assert(arrH>=arrL);
		int * arr=new int[n];
		cout<<"address= "<<arr<<endl;
		srand((unsigned )time(NULL));
		for(int i=0;i!=n;++i)
		{
			arr[i]=rand()%(arrH-arrL+1)+arrL;

		}
		return arr;

	}

	template <typename T>
	void printArray(T arr[],int n) 
	{
		for(int i=0;i!=n;++i)
		{
			cout<<arr[i]<<" ";
		}
		cout<<endl;
	}
}

```
在这里我们创建了一个Helper的命名空间，其中有一个创建任意大小的数组的函数generatearray以及一个打印数组的函数printArray。我们在程序中使用的时候需要加上Helper::来限定命名空间，例如：Helper::generatearray,Helper::printArray。

## 选择排序
选择排序在很多书里都有介绍，这里不再进行描述，只是列出代码。
```c++
void selectSort(int arr[],int size)
{
	for(int i=0;i<size;i++)
	{
		int minIndex=i;
		for(int j=i+1;j<size;j++)
		{
			if(arr[j]<arr[minIndex])
				minIndex=j;
		}
		swap(arr[i],arr[minIndex]);
	}

}
```

