## 编程知识点

#### vector

.size(): 长度

.front(): 得到首元素的引用

.back(): 得到最后一个元素的引用



#### pair

pair<T1, T2> p1;            //创建一个空的pair对象（使用默认构造），它的两个元素分别是T1和T2类型，采用值初始化。

pair<T1, T2> p1(v1, v2);    //创建一个pair对象，它的两个元素分别是T1和T2类型，其中first成员初始化为v1，second成员初始化为v2。

make_pair(v1, v2);          // 以v1和v2的值创建一个新的pair对象，其元素类型分别是v1和v2的类型。

p1 < p2;                    // 两个pair对象间的小于运算，其定义遵循字典次序：如 p1.first < p2.first 或者 !(p2.first < p1.first) && (p1.second < p2.second) 则返回true。

p1 == p2；                  // 如果两个对象的first和second依次相等，则这两个对象相等；该运算使用元素的==操作符。

p1.first;                   // 返回对象p1中名为first的公有数据成员

p1.second;                 // 返回对象p1中名为second的公有数据成员



#### queue

- front()：返回 queue 中第一个元素的引用。如果 queue 是常量，就返回一个常引用；如果 queue 为空，返回值是未定义的。
- back()：返回 queue 中最后一个元素的引用。如果 queue 是常量，就返回一个常引用；如果 queue 为空，返回值是未定义的。
- push(const T& obj)：在 queue 的尾部添加一个元素的副本。这是通过调用底层容器的成员函数 push_back() 来完成的。
- push(T&& obj)：以移动的方式在 queue 的尾部添加元素。这是通过调用底层容器的具有右值引用参数的成员函数 push_back() 来完成的。
- pop()：删除 queue 中的第一个元素。
- size()：返回 queue 中元素的个数。
- empty()：如果 queue 中没有元素的话，返回 true。
- emplace()：用传给 emplace() 的参数调用 T 的构造函数，在 queue 的尾部生成对象。
- swap(queue<T> &other_q)：将当前 queue 中的元素和参数 queue 中的元素交换。它们需要包含相同类型的元素。也可以调用全局函数模板 swap() 来完成同样的操作。



#### string

.c_str(): 转换为char*

.length()、.size()：获取长度

.compare(const string& str)：字符串比较

.substr(int pos, int n)



#### unordered_set

```c++
std::unordered_set<std::string> uset{ "http://c.biancheng.net/c/",
                                     "http://c.biancheng.net/java/",
                                   "http://c.biancheng.net/linux/"};
```

begin()

end()

cbegin()

cend()

empty()

size()

find(key)

count(key)

emplace()

insert()

erase()

clear()



## 选择题知识点

1. sizeof（数组指针）和sizeof(指针）的区别

2. 派生类的构造函数的成员初始化列表中，不能包含**基类的子对象初始化**。

   *（派生类能够调用基类的构造函数。但是类的成员初始化都由自己的构造函数来完成，而不要其他派生体系中的类来干涉。你可以通过调用基类构造函数来给基类成员初始化，但是不能直接对基类成员初始化。）*

3. 引用和指针：

   1. 引用创建时必须初始化，指针可以在任何时候初始化
   2. 引用必须指向对象，不能为NULL，指针可能为NULL

4. 构造函数可以被重载，因为构造函数可以有多个且可以带参数。

   析构函数不可以被重载，因为析构函数只能有一个，且不能带参数。



## 面试知识点

#### static

1. 静态变量：全局 or 局部
2. 静态函数 *头文件中最好别用，cpp中应该用。因为头文件中的函数应当是给多个cpp共用的，而cpp中的函数应当是给本文件用的*
3. 类的静态成员（变量/函数）：类的多个对象共享

#### 四种类型转换

1. const_cast

2. static_cast

3. dynamic_cast

4. reinterpret_cast

   *为什么不使用C的强制转换？*

   *C的强制转换表面上看起来功能强大什么都能转，但是转化不够明确，不能进行错误检查，容易出错。*

#### 引用和指针

1. 本质：指针保存一个地址，有自己的空间；而引用只是一个别名
2. sizeof、初始化、const、能否指向其他对象、多级指针、++、动态分配内存

#### 常量

1. 常量定义必须初始化

2. 对于局部对象，常量存放在栈区，对于全局对象，常量存放在全局/静态存储区。对于字面值常量，常量存放在常量存储区。

3. 定义为const的对象的所有数据成员的值都不能被修改。凡出现调用非const的成员函数，将出现编译错误。但构造函数除外。

4. 问题：c++：void display( ) const 中的const是什么意思？
   简答：
   意思是除了表明了mutable的成员变量以外
   该类的其他的成员变量在这个函数内一律不能修改。

   详细：
   加const表明，该函数只能是只读的，不能修改私有变量的值。加强安全性。
   给隐含的this指针加const，表示这个this指向的东西是const的，也就是说这个函数中无法改动数据成员了。const是一种保证，告诉你这个成员不会改变对象的状态。在设计类的时候，一个原则就是对于不改变数据成员的成员函数都要在后面加 const。

   除此之外，在类的成员函数后面加 const 还有什么好处呢？那就是常量（即 const）对象可以调用 const 成员函数，而不能调用非const修饰的函数。

5. const int * 表示，指向常量int 类型的指针，即指向的这块内存的内容，不可以修改。（但指针本身可以修改）

   ```c++
   const int* c_PtrA  =  new int(10);
   int * ptrB= new int(10);
   
   c_PtrA = ptrB; // 没问题
   ptrB = c_PtrA; // 编译报错 不能从 const int* 转换程 int* (const int* 已经限制此地址内容，不可修改。这时，却让 int * 指针指向这块地址，而使用 int * 指针，表示此地址内容可修改。发生冲突)
   
   // 下面这种情况不会报错，但可能造成程序崩溃
   ptrB = (int*)c_PtrA;
   // ....
   *ptrB = 20; // 此处修改了b和a共同指向的地址的内容，程序崩溃
   ```

   

#### 类型转换

1. 对于只存在单个参数的构造函数的对象构造来说，函数调用可以直接使用该参数传入，编译器会自动调用其构造函数生成临时对象。



#### 编译

1. 预处理
2. 编译
3. 汇编
4. 链接



### 面试题

1. 模板成员函数可以是虚函数吗？