# C++标准库 STL 与 泛型编程

Generic Programming（GP，泛型编程）：如何正确使用`template`来进行编程！

目标： 

* level 0：使用C++ 标准库
* level 1：认识C++ 标准库
* level 2：__良好__使用C++ 标准库
* level 3：扩充C++ 标准库

C++ 标准库（Standard Library）> 标准模版库（STL）

标准库以header files形式呈现：

* C++标准库的header files不带 .h 例如 `#include<vector>`
* 新式的header files不带`.h` 
* 旧式的header files带`.h` 例如`#include<stdio.h>`

`namespace`的用法

## STL 六大部件

* 容器（Containers）：存储数据的地方
* 分配器（Allocators）
* 算法（Algorithm）
* 迭代器（Iterators）：泛化的指针
* 适配器（Adapters）
* 仿函数（Functors）

![image-20200622222555830](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20200622222555830.png)

```cpp
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

using namespace std;

int main()
{
	int ia[6] = { 27, 210, 12, 47, 109, 83 };
	vector<int, allocator<int>> vi(ia, ia + 6);

	cout << count_if(vi.begin(), vi.end(),
		not1(bind2nd(less<int>(), 40)));
	return 0;
}
```



“前闭后开”区间

```cpp
Container<T> c;
...
Container<T>::iterator ite= c.begin();
for (; ite != c.end(); ++ite)
    ..

//改进
std::vector<double> vec;

```



容器

* Sequence Containers
  * Array：固定空间，提前分配
  * Vector：自动扩充元素
  * Deque：双队列，两端可进可出
  * List：双向链表
  * Forward-List：单向链表
* Associative Containers - 大量查找
  * Set/Multiset：红黑树，[key/value]
  * Map/Multimap：红黑树，[key, value]
* Unordered Containers (其实就是Associative Containers中的一种)
  * HashTable： Separate Chaining

使用容器array

```cpp
#include <array>
#include <iostream>
#include <ctime>
#include <cstdlib> //qsort, bsearch, NULL

namespace test1{
    void test_array{
        cout<<"\ntest_array()...... \n";
        
        array<long, ASIZE> c;
        
        clock_t timeStart = clock(); //
    }
}
```

