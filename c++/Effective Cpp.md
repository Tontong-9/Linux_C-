# Effective CPP

- [Effective CPP](#effective-cpp)
  - [让自己习惯 CPP](#让自己习惯-cpp)
    - [条款 01：将 C++ 看作一个语言联邦](# 条款 01：将 C++ 看作一个语言联邦)
    - [条款 02：尽量以 const, enum, inline 替换 #define](# 条款 02：尽量以 const, enum, inline 替换 #define)
    - [条款 03：尽可能使用 const](# 条款-03尽可能使用-const)
    - [条款 04：确定对象被使用前已先被初始化](# 条款-04确定对象被使用前已先被初始化)
  - [构造/析构/赋值运算](#构造析构赋值运算)
    - [条款 05：了解 C++ 默默编写并调用了那些函数](#条款-05了解-c-默默编写并调用了那些函数)
    - [条款 06：若不想使用编译器自动生成的函数，就该明确拒绝](#条款-06若不想使用编译器自动生成的函数就该明确拒绝)
    - [条款 07：为多态基类声明 virtual 析构函数](#条款-07为多态基类声明-virtual-析构函数)
    - [条款 08：别让异常逃离析构函数](#条款-08别让异常逃离析构函数)
    - [条款 09：绝不再构造和析构过程中调用 virtual 函数](#条款-09绝不再构造和析构过程中调用-virtual-函数)
    - [条款 10：令 operator= 返回一个 reference to * this](#条款-10令-operator-返回一个-reference-to--this)
    - [条款 11：在 operator= 中处理 “自我赋值”](#条款-11在-operator-中处理-自我赋值)
    - [条款 12：复制对象时勿忘其每一个部分](#条款-12复制对象时勿忘其每一个部分)
  - [资源管理](#资源管理)
    - [条款 13：以对象管理资源](#条款-13以对象管理资源)
    - [条款 14：在资源管理类中小心 copying 行为](#条款-14在资源管理类中小心-copying-行为)
    - [条款 15：在资源管理类中提供对原始资源的访问](#条款-15在资源管理类中提供对原始资源的访问)
    - [条款 16：成对使用 new 和 delete 时采用相同形式](#条款-16成对使用-new-和-delete-时采用相同形式)
    - [条款 17：以独立语句将 newed 对象置入智能指针](#条款-17以独立语句将-newed-对象置入智能指针)
  - [设计与声明](#设计与声明)
    - [条款 18：让接口容易被正确使用，不易被误用](#条款-18让接口容易被正确使用不易被误用)
    - [条款 19：设计 class 犹如设计 type](#条款-19设计-class-犹如设计-type)
    - [条款 20：宁以 pass-by-reference-to-const 替换 pass-by-value](#条款-20宁以-pass-by-reference-to-const-替换-pass-by-value)
    - [条款 21：必须返回对象时，别妄想返回其 reference](#条款-21必须返回对象时别妄想返回其-reference)
    - [条款 22：将成员变量声明为 private](#条款-22将成员变量声明为-private)
    - [条款 23：宁以 non-member、non-friend 替换 member 函数](#条款-23宁以-non-membernon-friend-替换-member-函数)
    - [条款 24：若所有参数皆需要类型转换，请为此采用 non-member 函数](#条款-24若所有参数皆需要类型转换请为此采用-non-member-函数)
    - [条款 25：考虑写出一个不抛出异常的 swap 函数](#条款-25考虑写出一个不抛出异常的-swap-函数)
  - [实现 Implementations](#实现-implementations)
    - [条款 26：尽可能延后变量定义式的出现时间](#条款-26尽可能延后变量定义式的出现时间)
    - [条款 27：尽量少做转型动作](#条款-27尽量少做转型动作)
    - [条款 28：避免返回 handles 指向对象内部成分](#条款-28避免返回-handles-指向对象内部成分)
    - [条款 29：为“异常安全”而努力是值得的](#条款-29为异常安全而努力是值得的)
    - [条款 30：透彻了解 inlining 的里里外外](#条款-30透彻了解-inlining-的里里外外)
    - [条款 31：将文件间的编译依存关系降至最低](#条款-31将文件间的编译依存关系降至最低)
  - [继承于面向对象设计](#继承于面向对象设计)
    - [条款 32：确定你的 public 继承塑模出 is-a 关系](#条款-32确定你的-public-继承塑模出-is-a-关系)
    - [条款 33：避免遮掩继承而来的名称](#条款-33避免遮掩继承而来的名称)
    - [条款 34：区分接口继承和实现继承](#条款-34区分接口继承和实现继承)
    - [条款 35：考虑 virtual 函数以外的其他选择](#条款-35考虑-virtual-函数以外的其他选择)
    - [条款 36：绝不重新定义继承而来的 non-virtual 函数](#条款-36绝不重新定义继承而来的-non-virtual-函数)
    - [条款 37：绝不重新定义继承而来的缺省参数值](#条款-37绝不重新定义继承而来的缺省参数值)
    - [条款 38：通过复合塑模出 has-a 或“根据某物实现出”](#条款-38通过复合塑模出-has-a-或根据某物实现出)
    - [条款 39：明智而审慎地使用 private 继承](#条款-39明智而审慎地使用-private-继承)
    - [条款 40：明智而审慎地使用多重继承](#条款-40明智而审慎地使用多重继承)
  - [模板于泛型编程](#模板于泛型编程)
    - [条款 41：了解隐式接口和编译器多态](#条款-41了解隐式接口和编译器多态)
    - [条款 42：了解 typename 的双重含义](#条款-42了解-typename-的双重含义)




## 让自己习惯 CPP

### 条款 01：将 C++ 看作一个语言联邦

- 如今的 C++ 已经是一个多重泛型编程语言，支持多种编程形式：
   1. 过程形式；
   2. 面向对象形式；
   3. 函数形式；
   4. 泛型形式；
   5. 元编程形式。

- 主要包含的次语言有:
  1. C：可以说 C++ 以 C 为基础；
  2. Object-Oriented C++：C with Class 形式；
  3. Template C++：即 C++ 泛型编程形式；
  4. STL：即基于 Template C++ 提供的功能库，使用其必须遵循一些它的规章制度。

### 条款 02：尽量以 const, enum, inline 替换 #define

- 即尽量通过使用编译器的编译阶段替代预处理器：
  1. 首先比起预处理器的盲目替换，常量可以产生更少量的代码。
  2. 编译器可以针对相应代码进行类型检查，而 #define 不会。
  3. 无法使用 #define 创建一个类的专属常量，因为它兼容 C 编程类型并不重视作用域。

- 对于**单纯常量**，最好以 const 或 enum 替代。
- 形似**函数的宏**（macros），最好改用 inline 替代。

```cpp
template<typename T>                               // because we don't

inline void callWithMax(const T& a, const T& b)    // know what T is, we
{                                                  // pass by reference-to-

  f(a > b ? a : b);                                // const — see Item 20

}
```

### 条款 03：尽可能使用 const

- 使用 const 带来的优势：
  - const 可以协助你确保一些常量不会被修改；
  - const 在修饰对象上有很多的选择；

    ```cpp
    // 关键字 const 出现在 * 左边则修饰指针指向的数据为常量；出现在 * 右边则修饰指针本身为常量
    char greeting[] = "Hello";
    char *p = greeting;                 // non-const pointer,
                                        // non-const data
    const char *p = greeting;           // non-const pointer,
                                        // const data
    char * const p = greeting;          // const pointer,
                                        // non-const data
    const char * const p = greeting;    // const pointer,
                                        // const data
    ```

  - 支持对迭代器进行 const 修饰；

    ```cpp
    std::vector<int> vec;
    ...
    const std::vector<int>::iterator iter = vec.begin();    // iter acts like a T* const
    *iter = 10;                                 // OK, changes what iter points to
    ++iter;                                    // error! iter is const
    
    std::vector<int>::const_iterator cIter = vec.begin();  //cIter acts like a const T*
    *cIter = 10;                               // error! *cIter is const
    ++cIter;                                  // fine, changes cIter
    ```

  - const 可以修饰返回值防止调用者使用错误；

    ```cpp
    if (a * b = c) ...                       // oops, meant to do a comparison!
    ```

  - const 修饰成员函数方便调用者知道哪个接口可以处理 const 与取得 cosnt 对象；
    - 注意：两个成员函数是可以根据常量性的不同进行重载的，书中的例子可以很好的体现：
    - 注意：如果成员函数修饰为 const 的话，返回值也应该为 const ，因为我们无法保证使用者是否会修改。

      ```cpp
      class TextBlock {
      public:
      
      ...
          // 针对 const obj 与 non-const obj 都有进行处理的成员函数
          const char& operator[](std::size_t position) const   // operator[] for
          { return text[position]; }                           // const objects
          char& operator[](std::size_t position)               // operator[] for
          { return text[position]; }                           // non-const objects
      
      private:
          std::string text;
      };
      ```

      - 在 cosnt 和 non-const 成员函数中避免重复，以上述的例子中针对 const obj 和 non-const obj 各实现一份的方法可能会导致部分代码重复需要注意，可以令 non-const 方法调用其 const 的兄弟方法通过一个转型动作实现，虽说转型是一个糟糕的主意，但是针对这种情况需要考量：

        ```cpp
        class TextBlock {
        
        public:
        
        ...
        
        const char& operator[](std::size_t position) const     // same as before
        {
            ...
            ...
            ...
            return text[position];
        }
        
        char& operator[](std::size_t position)         // now just calls const op[]
        {
            return
            const_cast<char&>(                         // cast away const on
                                                        // op[]'s return type;
                static_cast<const TextBlock&>(*this)     // add const to *this's type;
                [position]                            // call const version of op[]
            );
        
        }
        ...
        
        };
        ```

### 条款 04：确定对象被使用前已先被初始化

- 对于无任何成员的内置类型，需要手动完成其初始化。而针对内置类型以外的，需要确保构造函数完成对成员的初始化。

  - C 类型的数组一般不会保证内容初始化，但是 C++ 的容器类型则会保证这一点。
- 赋值与初始化区别，如下例子 C++ 的类成员初始化实在构造函数调用之前完成调用相应成员的默认构造函数，而例子中属于**赋值**，在构造调用之前还对这些成员进行过默认初始化。注意 numTimesConsulted 成员是内置类型，不保证会在初始化时默认获得初值（除非显式初始化），为了避免没有默认构造的内置类型引入错误最好对所有类成员进行显示初始化：

    ```cpp
    class PhoneNumber {
        ...
    };
    
    class ABEntry { // ABEntry = "Address Book Entry"
    
    public:
        ABEntry(const std::string& name, const std::string& address,
    
            const std::list<PhoneNumber>& phones);
    
    private:
        std::string theName;
    
        std::string theAddress;
    
        std::list<PhoneNumber> thePhones;
    
        int numTimesConsulted;
    };
    //赋值
    ABEntry::ABEntry(const std::string& name, const std::string& address,
    
        const std::list<PhoneNumber>& phones)
    
    {
    
        theName = name; // these are all assignments,
    
        theAddress = address; // not initializations
    
        thePhones = phones;
    
        numTimesConsulted = 0;
    }
    //初始化
    ABEntry::ABEntry(const std::string& name, const std::string& address,
                     const std::list<PhoneNumber>& phones)
    : theName(name),
    theAddress(address),                  // these are now all initializations
    thePhones(phones),
    numTimesConsulted(0)
    {}                                      // the ctor body is now empty
    ```

- 当一个类存在多个构造函数，同时也包含多个成员需要进行初始化，这时多份成员初始化代码就会重复。这种情况就可以省略掉初始化与赋值初始化一样效果的成员，将其放入类函数内供所有构造函数调用。
- 针对初始化列表注意与类成员初始化顺序要保持一致，否则编译器会报告一个警告。
- 全局静态对象 non-local static 会在程序结束时自动销毁，析构会在 main() 函数执行完成后被调用。但是这种全局静态对象存在一个问题，即两个不同的编译单元的静态对象之间存有依赖关系我们无法确定这两个静态对象的初始化顺序，C++ 对其没有定义。可以使用单例模式消除这种隐患，将其封装到一个全局静态的接口中，返回这个静态对象指针，这个方法可以确保其初始化。

  - 这种静态全局变量在多线程环境下的初始化会很麻烦，应该在单线程启动过程中调用一次先将其初始化避免此问题。

## 构造/析构/赋值运算

### 条款 05：了解 C++ 默默编写并调用了那些函数

- 编译器会自动生成：
  - 默认构造函数；
  - 默认析构函数（默认生成非虚析构，除非基类声明了虚析构）；
  - 拷贝构造函数；
  - 重载"="号构造函数。

  ```c++
  class Exampple{
      public:
      	Example()=default;//编译器生成的默认构造函数
      	Example(const Example &example)=default;// 编译器生成的拷贝构造函数
      	Example(const Example&) = delete;//C++11 引入了删除的函数（= delete），可以显式阻止编译器生成默认的特殊成员函数。
      	Example(Example&& other) = default;  // 编译器生成的移动构造函数 (C++11)
      	Example& operator=(const Example& other) = default;  // 编译器生成的拷贝赋值运算符
      	Example& operator=(Example&& other) = default;  // 编译器生成的移动赋值运算符 (C++11)
       	~Example() = default;  // 编译器生成的析构函数
  };
  
  ```

- 当手动实现了一个构造函数后就不必担心编译器画蛇添足般在添加一个无实参的构造啦。

- 默认提供的拷贝构造函数（"="构造同）仅仅对类成员进行简单拷贝，对于指针类型不会进行内存的深拷贝，因此最好使用容器类型。
  - 当内含引用成员的类发成拷贝构造时，需要手动实现 copy 构造对相应引用成员处理，否则编译器会拒绝对其进行编译。
  - 如果基类中拷贝构造函数是私有的派生类无法提供默认的拷贝构造了。

- 深拷贝vs.浅拷贝

  - 使用容器类型来避免深拷贝问题

    为了避免手动管理内存以及避免浅拷贝带来的问题，推荐使用标准库提供的容器类（如 `std::vector`、`std::unique_ptr` 等）。这些容器类在拷贝和赋值时会自动进行深拷贝或者转移操作：

    ```cpp
    
    #include <vector>
    #include <memory>
    
    class Example {
    public:
        std::vector<int> data;  // 使用容器进行深拷贝管理
        std::unique_ptr<int> ptr; // 使用智能指针来管理资源
    };
    ```

    以上代码中，`std::vector` 会自动进行深拷贝，`std::unique_ptr` 则会通过移动语义来避免拷贝。

  - 拷贝构造函数与引用成员

    当一个类包含引用成员时，编译器会生成的默认拷贝构造函数无法直接复制引用成员，因为引用必须在初始化时绑定到某个对象或值，一旦绑定就无法更改。需要手动实现拷贝构造函数

    如果类包含引用成员，编译器无法生成默认拷贝构造函数，我们需要手动实现：

    ```cpp
    
    class Example {
    public:
        int& ref; // 引用成员
    
        // 手动实现拷贝构造函数
        Example(int& r) : ref(r) {}
    
        Example(const Example& other) : ref(other.ref) {}
    };
    ```

    在手动实现的拷贝构造函数中，`ref` 成员必须在初始化列表中进行初始化，而不能在构造函数体内赋值。

  - 基类的私有拷贝构造函数与派生类

    如果基类的拷贝构造函数被声明为私有或被删除（`= delete`），派生类将无法使用默认的拷贝构造函数。这是因为派生类的默认拷贝构造函数会尝试调用基类的拷贝构造函数，而如果基类的拷贝构造函数是私有的或被删除，编译器无法访问或调用它。

    解决方法

    - **显式声明派生类的拷贝构造函数**：在派生类中显式定义自己的拷贝构造函数，并调用基类的公有拷贝构造函数（如果存在）或者自行处理基类成员。

    ```cpp
    
    class Base {
    private:
        Base(const Base&); // 私有拷贝构造函数
    };
    
    class Derived : public Base {
    public:
        // 显式声明派生类的拷贝构造函数
        Derived(const Derived& other) : Base(other) {
            // 其他拷贝操作
        }
    };
    ```

    - **删除派生类的拷贝构造函数**：如果类不应该被复制，显式删除拷贝构造函数。

    ```cpp
    class Derived : public Base {
    public:
        Derived(const Derived&) = delete;  // 显式删除拷贝构造函数
    };
    ```

    这种方法防止了对派生类对象的拷贝，也确保了类的设计符合其使用意图。

    总结

    1. **默认拷贝构造函数**会对类成员进行**浅拷贝**，不适合指针成员的情况，因此推荐使用容器类型或智能指针来管理资源。
    2. 当类包含**引用成员**时，编译器不会生成默认拷贝构造函数，程序员需要手动实现。
    3. 如果基类的拷贝构造函数是**私有的**或被**删除**，派生类必须显式提供拷贝构造函数或删除拷贝构造函数。

  ```c++
  
  ```

  

### 条款 06：若不想使用编译器自动生成的函数，就该明确拒绝

- 拒绝生成默认的方法可以先将其手动声明为私有并且不去实现，这样当使用者企图拷贝时编译器会发生警告，通过友员或者其他成员函数中调用连接器会提醒你。
  - 还可以将拷贝构造函数放入基类中且声明为私有，可以将链接器期间的错误提升到编译期。

    ```cpp
    class Uncopyable {
    
    protected: // allow construction
        Uncopyable() { } // and destruction of
        ~Uncopyable() { } // derived objects...
    
    private:
        Uncopyable(const Uncopyable&); // ...but prevent copying
    
        Uncopyable& operator=(const Uncopyable&);
    };
    
    class HomeForSale : private Uncopyable { // class no longer
    
        ... // declares copy ctor or
    
    }; // copy assign. operator
    ```

- 为驳回编译器自动提供的技能，可将相应的成员函数声明为 private 并且不予实现。或者使用基类的做法。

- C++11 引入了删除的函数（= delete），可以显式阻止编译器生成默认的特殊成员函数。

  ```c++
  Example(const Example& example)=default;
  Example(const Example&) = delete;//C++11 引入了删除的函数（= delete），可以显式阻止编译器生成默认的特殊成员函数。
  ```

  

### 条款 07：为多态基类声明 virtual 析构函数

- C++ 明确支出，当派生类对象经由一个基类指针被删除，而且该基类还带着一个 non-virtual 析构函数，结果时未定义的。一般都是派生类多余基类部分没有释放造成内存泄漏。[虚析构原理](https://www.cnblogs.com/xylc/p/3586892.html)
  - 因此可以断定任何函数只要带有 virtual 那么就应该有一个 virtual 的析构函数。

- 没有明确的继承要求使用 virtual 就不要使用，虚表扩张会浪费内存空间。

### 条款 08：别让异常逃离析构函数

- C++ 并不鼓励在析构中抛出异常，会造成析构不完全引发内存泄漏。
  - 而当一个析构函数中多次抛出异常，则会进入不明确的地方。

- 在析构中避免异常抛出的两种办法：
  1. 在析构中捕获可能抛出的异常，并且终止程序运行；
  2. 在析构中捕获可能抛出的异常，进行记录（吞掉）。

- 上述两种避免析构中异常的方法，都存在各自的优势和问题，最好的方式则是如果某个操作可能在失败时抛出异常，而又存在某种需要必须处理该异常，那么这个异常必须来自析构函数以外的地方。举个例子：当析构中需要关闭某些可能抛出异常的资源，那么应该将关闭的操作交由客户或者上级逻辑，不应再本层级的析构中完成。

### 条款 09：绝不再构造和析构过程中调用 virtual 函数

- 基类会在派生类之前构造完成，所以在构造中调用 virtual 函数将会是**基类的对应实现**，而不是你所期待的派生类的扩展。
  - 可以理解为对象在派生类构造执行之前不会成为一个派生类。

- 返过来，当析构时也是派生类先析构，一旦派生类析构开始执行，对象内的成员变量便呈现为未定义。

- 总的来说析构、构造中调用 virtual 函数最大的问题时容易调用错误的实现，隐藏问题不易被察觉。

### 条款 10：令 operator= 返回一个 reference to * this

- 主要是为了实现连锁赋值形式：

```cpp
int x, y, z;
x = y = z = 15;                        // chain of assignments
x = (y = (z = 15));
```

- 具体实现：

```cpp
class Widget {

public:
  ...
    Widget& operator+=(const Widget& rhs   // the convention applies to
    {                                      // +=, -=, *=, etc.
        ...
        return *this;
    }
    Widget& operator=(int rhs)            // it applies even if the
    {                                     // operator's parameter type
        ... // is unconventional
        return *this;
    }
   ...
};
```

### 条款 11：在 operator= 中处理 “自我赋值”

- 自我赋值看起来有些蠢，但是在复杂的逻辑中总会遇到这种情况。
- 如果不注意会编写出一些不安全的复制函数，如下例，想要避免也很简单进行一个判断比对即可。

```cpp
Widget& Widget::operator=(const Widget& rhs) // unsafe impl. of operator=
{
    delete pb; // stop using current bitmap

    pb = new Bitmap(*rhs.pb); // start using a copy of rhs's bitmap

    return *this; // see Item 10
}
```

- 但是异常是我们不得不需要考虑的事情，如果 new Bitmap 过程中导致异常，Widget 最终都会持有一个指针指向一块被删除的 Bitmap，对此无能为力只能浪费时间去调试。而解决办法也很简单：

```cpp
Widget& Widget::operator=(const Widget& rhs)
{
    Bitmap* pOrig = pb; // remember original pb

    pb = new Bitmap(*rhs.pb); // make pb point to a copy of *pb

    delete pOrig; // delete the original pb

    return *this;
}
```

- 其实可以看出想要保证异常安全时，对于自我复制的判断是自然成立的，因此大多数时候都是考虑通过精心安排的语句保证异常安全即可。

### 条款 12：复制对象时勿忘其每一个部分

- 条款 5 介绍了编译器自动实现的 copy 方法，会对被拷贝对象的所有成员变量都进行一份拷贝。但是当你自己实现一个拷贝方法后，编译器便放手不管了，及时有遗漏没有拷贝的成员也不再会报错提醒你，**因此当你一个 class 添加一个成员变量，必须同时修改 copy 函数才行**。

- 继承是个需要特殊注意滴，因为派生类中都是包含一份基类成员的副本，因此 copy 记得不要忘记它们，可以调用基类的复制方法来进行复制。

```cpp
PriorityCustomer::PriorityCustomer(const PriorityCustomer& rhs)
    : Customer(rhs), // invoke base class copy ctor
    priority(rhs.priority)
{
    logCall("PriorityCustomer copy constructor");
}

PriorityCustomer& PriorityCustomer::operator=(const PriorityCustomer& rhs)
{
    logCall("PriorityCustomer copy assignment operator");
    Customer::operator=(rhs); // assign base class parts 复制基类成员
    priority = rhs.priority;
    return *this;
}
```

- 不要用 copy assignment 操作符调用 copy 构造方法，反过来一样，应该将两者可复用的地方抽离放入第三个方法内，供两个 copy 调用。



## 资源管理

### 条款 13：以对象管理资源

- 可以利用 C++ 的机制去协助释放资源：即将资源放入对象内，通过 C++ 的析构函数自动调用的机制确保资源释放。这也是智能指针的核心思想，他有两个关键的想法：
  - 获得资源后立刻放入管理对象内；
  - 管理对象运用析构函数确保资源被释放。
- 由于 auto_ptr 被销毁时会自动删除它所指向的内存，所以注意不要让多个 auto_ptr 指向同一块内存造成内存多次释放。当前现代 C++ 的替代方式即 unique_ptr，特点是它无法进行复制等操作，只可以通过 move 进行所有权迁移，避免了多个指针指向同一个内存的问题。
  - 由于智能指针的特性 STL 容器最好不保存智能指针。
- shared_ptr 的复制行为是预期内的，因此它可以作用域 STL 容器，但是需要注意**定制析构**、出错定位比较复杂。
- [关于智能指针介绍文档](https://www.cnblogs.com/WindSun/p/11444429.html)

### 条款 14：在资源管理类中小心 copying 行为

- 如条款 13 介绍的 RAII 资源管理方法，可能遇到情一种情况便是“当一个 RAII 对象被复制，会发生什么？”
  - 禁止复制：许多情况下对 RAII 进行复制是不合理的，应该如 条款 6 种介绍的方法禁止复制。
  - 对底层资源使用引用计数：shared_ptr 智能指针就是这么实现的。
  - 复制底层资源：复制 RAII 管理的资源，进行”深度拷贝“。
  - 转移底层资源所有权：unique_ptr 指针 move 语义一样。

### 条款 15：在资源管理类中提供对原始资源的访问

- 使用 RAII 对象来进行资源管理很棒，但是使用许多的 API 依旧会逼迫你操作原始资源，一般有两个方式可以通过 RAII 对象操作原始数据：
  - 一般标准智能指针提供 get 成员函数，显示的返回智能指针内部的原始指针（复件）。
  - 智能指针一般重载了指针操作符(operator-> 和 operator*)，隐式的转换为底部原始指针。
- 通常使用显示的转换 get 方法是比较通用的，因为这样可以避免“非故意的类型转换”情况。保证接口正确使用不要增加默认与隐式的规则。

### 条款 16：成对使用 new 和 delete 时采用相同形式

- new 与 delete 要成对使用相信不必多说，但是 delete 最大的问题在于：即将被删除的内存之内究竟存有多少对象？这个问题的答案决定了有多少个析构函数必须被调用起来。这就是需要 new 和 delete 数组时需要增加 `[]` 的原因，数组使用的内存通常还包括数组大小的记录。

### 条款 17：以独立语句将 newed 对象置入智能指针

- shared_ptr 构造函数需要一个原始指针，但该构造函数是 explicit 构造，禁止隐式转化导致编译不通过。

```cpp
int priority();

void processWidget(std::tr1::shared_ptr<Widget> pw, int priority);

processWidget(new Widget, priority()); // 这边编译会报错

//只能使用这种强转来通过编译
processWidget(std::tr1::shared_ptr<Widget>(new Widget), priority());
```

- 上例种还存在一个问题，传入智能指针的方式由于 C++ 编译器在对函数调用时，是先创建参数相关代码，其执行的顺序是不确定的：
  - 可能的调用：
    - 调用 priority；
    - 执行 new Widget；
    - 调用 shared_ptr 构造。
  - 还可能：
    - 执行 new Widget；
    - 调用 priority；
    - 调用 shared_ptr 构造。
- 而第二种当 priority 调用失败后就会导致先 new 出来的 widget 被泄漏了。因此基于以上两个问题最好以独立语句将 newed 对象置入智能指针。

```cpp
std::tr1::shared_ptr<Widget> pw(new Widget);  // store newed object
                                              // in a smart pointer in a
                                              // standalone statement

processWidget(pw, priority());                // this call won't leak
```

## 设计与声明

### 条款 18：让接口容易被正确使用，不易被误用

- 提供的接口不应出现可能导致误用的歧义，即使用者能成功通过编译便正确的使用了功能接口。
  - 如书中提供的 Date 类的设计模式。使用结构封装数据对每种类型数据在结构中进行校验判断，防止误用。
- 提供出的 types 应与内置的 types 行为一致。避免无端与内置类型不兼容，真正的理由是为了提供行为一致的接口，使得接口更加容易使用。
  - 就像 a 与 b 都是 ints ，但是 a * b 却不能想 int 一样合法，这就造成使用上的困难。
- 不要给提供的接口强加规则，任何接口如果需要使用者必须记得做某些事情这样总会引起错误使用，不能假设使用者会记得。
  - 就像条款 13 种提供的 createInvestment 方法，将其返回值强制为智能指针，避免使用这误用造成资源泄露。`std::tr1::shared_ptr<Investment> createInvestment();`
- "阻止误用"，包括建立新类型、限制类型上的操作、限制对象值范围以及消除使用者资源管理的责任。
- shared_ptr 支持定制型删除器，防范 DLL 问题。

### 条款 19：设计 class 犹如设计 type

- 设计一个好的 class 就像一个内置 type 一样有自然的语法，直观的语义，以及一或多个高效实现。
- 设计一个 class 要问问自己以下问题：
  1. 新 type 的对象应该如何被创建和销毁？
  2. 对象的初始化和对象的赋值该有什么样的差别？
  3. 新 type 的对象如果 pass by value ，意味着什么？
     - copy 构造函数用来定义一个 type 的 pass by value 如何实现。
  4. 什么是新 type 的“合法值”？
  5. 你的新 type 需要配合某个继承图系么？
  6. 你的新 type 需要什么样的转换？
  7. 什么样的操作符和函数对此新 type 是否合理？
  8. 什么样的标准函数应该驳回？
  9. 谁该取用新 type 的成员？
  10. 什么是新 type 的“未声明接口”？
  11. 你的新 type 有多么一般化？
  12. 你真的需要一个新 type 吗？

### 条款 20：宁以 pass-by-reference-to-const 替换 pass-by-value

- pass-by-value 更多的浪费资源，包括多次的构造析构，保存中间局部变量的内存等等。
- 使用 pass-by-reference 如不会修改引用变量，则使用 const 限定其为常引用。
- 以 pass-by-reference 可以避免对象切割问题，使用 pass-by-value 将派生类值传递给父类会调用父类的 copy 构造函数，造成派生类部分数据丢失。
- 内置类型、STL 的迭代器和函数对象使用 pass-by-value 更加合适。
- 除开内置类型不一定所有的小型 types 都是 pass-by-value 的合格选择，例如 STL 容器，其实现仅比指针多一点，但是其 copy 构造调用的消耗却很昂贵，因为复制这种指针和需要复制那些指针指向的数据即”深拷贝“。及时其他小型对象不会有这种 copy 构造函数，但是也存在效率上的问题。
  - 还有一个理由是小型 types 其大小容易有所变化，这就可能在以后影响效率。

### 条款 21：必须返回对象时，别妄想返回其 reference

- 首先考虑好返回引用对象的声明周期，不要返回一个局部的对象。
- 考虑好了不要返回一个局部的对象，自然而然会想着在堆上分配内存创建一个对象来返回引用，虽然没有什么大错误，但是这是一个坏主意。不仅仅堆上创建对象所要承担的构造消耗，更因该考虑下谁该 delete 到这个对象呢？本着不要强加逻辑给使用者原则，更应该返回一个智能指针。
- 考虑下列代码，如果重载实现了 `*` 操作符，并且返回了一个堆上的对象引用 `operator*(operator*(x, y), z)` 这一步中进行了两次 new 操作，而使用者却没有办法 delete 掉中间隐藏的哪个对象。

```cpp
const Rational& operator*(const Rational& lhs,   // warning! more bad
                          const Rational& rhs)   // code!
{
  Rational *result = new Rational(lhs.n * rhs.n, lhs.d * rhs.d);
  return *result;
}

Rational w, x, y, z;
w = x * y * z;                     // same as operator*(operator*(x, y), z)
```

- 返回 static 的引用会造成严重的多线程问题，以及书中的判断比对问题。

### 条款 22：将成员变量声明为 private

- 将成员变量声明为 private，可以通过提供对外方法来控制访问权限、范围等等。
- protected 并不比 public 更具有封装性。

### 条款 23：宁以 non-member、non-friend 替换 member 函数

- 在编写 class 方法时，大多数直觉便是将操作成员的方法都放到一个类中，但是有时对于需要调用几个方法来完成某个功能时。非成员方法将这几个方法绑定会比成员方法更好。
- 封装的优势：
  - 某些东西被封装，可以看见它的人就越少，我们也就存在更大的空间去修改它。
  - 封装使我们能够改变事物而只影响有限的用户。
  - 越多的函数可访问，哪个数据的封装性就越低。
- 非成员非友员的封装优势便是它不会增加“能够访问 class 内 private 成分"的范围。
- 同样非成员方法也可以使另一个 class 中的成员方法，即只要不会影响能够访问 class 内 private 成分的范围即可。
- 当使用非成员非友员方法来进行功能类的方法调用时有两点可以优化注意：
  - 可以将一个多功能类拆分成多个子功能类，并且去除之间编译依赖。
  - 将所有创建的便利方法函数放在多个头文件但是同一个命名空间内，便于扩展。

### 条款 24：若所有参数皆需要类型转换，请为此采用 non-member 函数

- 当重载实现了类的 operator* 成员方法，会发现不支持交换定律的问题。

```cpp
class Rational {

public:

  Rational(int numerator = 0,        // ctor is deliberately not explicit;
           int denominator = 1);     // allows implicit int-to-Rational
                                     // conversions
  int numerator() const;             // accessors for numerator and
  int denominator() const;           // denominator — see Item 22
  const Rational operator*(const Rational& rhs) const;
private:
  ...
};


result = oneHalf * 2;                             // fine
result = 2 * oneHalf;                             // error!
//------------------------------
result = oneHalf.operator*(2);                    // fine
result = 2.operator*(oneHalf);                    // error!
```

- 首先看成功的 `oneHalf * 2` 主要是因为发生了隐式转换，通过传入的证数构造了一个新对象。如果 Rational 构造标识了 explicit 那么 `oneHalf * 2` 也不会成功了。
- 想要解决 `2 * oneHalf` 失败的问题，可以使用全局覆写 operator* 的方法。

```cpp
const Rational operator*(const Rational& lhs,     // now a non-member
                         const Rational& rhs)     // function
```

### 条款 25：考虑写出一个不抛出异常的 swap 函数

- 默认提供的 swap 函数十分平淡，仅仅是通过一个 tmp 中间变量保存交换 A 与 B。
- pimpl 手法，即以指针指向一个对象，内含真正的数据，仅仅交换指针即可。但是默认的 swap 往往调用默认的类 operator= 重载方法效率比较低需要我们重载一个针对目标对象 swap 函数方法。

```cpp
class WidgetImpl { // class for Widget data;

public: // details are unimportant
private:
    int a,
        b,
        c; // possibly lots of data —

    std::vector<double> v; // expensive to copy!
};

class Widget { // class using the pimpl idiom

public:
    Widget(const Widget& rhs);

    Widget& operator=(const Widget& rhs) // to copy a Widget, copy its
    {   // WidgetImpl object. For
        // details on implementing
        *pImpl = *(rhs.pImpl); // operator= in general,
        // see Items 10, 11, and 12.
    }

private:
    WidgetImpl* pImpl; // ptr to object with this

}; // Widget's data

// 通常我们不能够改变 std 命名空间内的任何东西，但可以为标准 templates 制造特化版本。

class Widget { // same as above, except for the

public: // addition of the swap mem func
    void swap(Widget& other)
    {
        using std::swap; // the need for this declaration
        // is explained later in this Item
        swap(pImpl, other.pImpl); // to swap Widgets, swap their
    } // pImpl pointers
};

namespace std {
template <> // revised specialization of
void swap<Widget>(Widget& a, // std::swap
                  Widget& b)
{
    a.swap(b); // to swap Widgets, call their
} // swap member function
}
```

## 实现 Implementations

### 条款 26：尽可能延后变量定义式的出现时间

- 只在需要的地方声明变量，防止无用的构造与析构。
- 条款 4 介绍的通过 default 构造一个对象后赋予其初值，比在构造时指定初值效率要差。因此尽可能在声明变量时指定初始值，跳过无意义的 default 构造。
- 对于循环中使用的局部变量定义应该放在循环外还是循环内：
  - 如果对象变量的一个赋值操作成本小于一组构造+析构成本那么就定义在循环外，反之放入循环内。

### 条款 27：尽量少做转型动作

- c++ 提供了 4 种新式的转型：
  - `const_cast<T>(expression)`：用来将对象的常量性移除。
  - `dynamic_cast<T>(expression)`：安全向下转型。
  - `reinterpret_cast<T>(expression)`：用来处理无关类型之间的转换。具体实现于与编译器有关，不具备移植性。
  - `static_cast<T>(expression)`：强迫隐式转换，类似 c 中的强转。
- 目前旧式转型依然合法，但是新式的转型更具有优势：
  - 新式转型可以很容易在代码中辨识出来，便于搜索和阅读。
  - 各转型动作的目标越细化，编译器就越可能帮助诊断错误运用。
- 函数型转型: `doSomeWork(const YourClass&);` 原型存在以下使用 `doSomeWork(YourClass(15)) == doSomeWork(static_cast<YourClass>(15))`，这两种情况是等效的。
- 有时当我们持有一个函数指针时，不要妄想通过知道对象内存布局来进行偏移实现某些操作，这对于不同编译器不同平台时不可移植的。
- 下边这种操作时错误的，它仅仅时作用在了强转产生的一个针对 this 指针父类资源的副本上。

```cpp
class Window { // base class

public:
    virtual void onResize() {... } // base onResize impl
    ...
};

class SpecialWindow : public Window { // derived class

public:
    virtual void onResize()
    {                                           // derived onResize impl;

        static_cast<Window>(*this).onResize();  // cast *this to Window,
                                                // then call its onResize;
                                                // this doesn't work!
        ...                                     // do SpecialWindow-
    }                                           // specific stuff
    ...
};
```

- dynamic_cast 转换慎用，**大部分的实现效率低下**（通过对 class 名称进行比对）。一般使用的情况都是在你想要将一个退化为基类的派生类指针，转换为派生类。

### 条款 28：避免返回 handles 指向对象内部成分

- 通常我们认为对象”内部“就是指它的成员变量，不对外公开的数据、使用的函数，因此当返回 handle 指向了这部分则会导致类的封装遭到破坏。
- 类方法返回`引用的方式`向外暴露对象内部成员时：
  - 首先会导致类成员的封装性降低，类成员的封装性最多只等于这个类方法的访问级别。
  - 并且当返回非 const 的引用，并且这个引用对象指向类成员时，调用者就可以直接修改掉对象类成员，而不用通过任何方法，导致封装被破坏。解决这个的问题则是将返回的类型限定为 const，避免使用者修改的危险。`相当于有限的放松了类成员的读权限`。
- 当返回指针、迭代器与引用存在的问题是一致的，破坏了类的封装性。
- 除了破坏类的封装性问题，返回 handle 指向类内部成分还存在更严重的问题即，空悬(dangling)。因此当使用指向类内部的 handle 时，必须注意对象的生命周期。

### 条款 29：为“异常安全”而努力是值得的

- 异常安全性即当有异常抛出时，函数会保证：
  - 不泄露任何资源；
  - 不允许数据被破坏：即已经被修改的成员或者状态当异常发生后，需要保证恢复到调用之前的状态。
- 异常安全函数提供以下三个保证之一：
  - 基本承诺：如果异常抛出，程序内的任何事物仍然保持在有效的状态下。但是当调用失败后无法确保当前函数处于哪种状态。
  - 强烈保证：如果异常抛出，程序的状态不会改变，即如果函数调用成功就是完全成功，失败就会回退到调用前的状态。
  - 不抛掷异常：承诺不抛出异常，能供完成承诺的功能。
- 实现强烈保证的异常安全：
  - 将堆内存资源、锁资源等等，通过智能指针以及资源管理类进行管理。
  - `不要为了标识某件事情发生而改变对象状态，除非那件事情真的发生了`。
    - 只有当已经具体事情执行完成后才进行修改标志事情的内部状态（计数器、标志位等等）相应操作。
- copy and swap 策略：对打算修改的对象进行拷贝，在其副本上进行修改，当所有操作成功后，再将修改的副本与元对象在一个不抛出异常的操作中进行置换（swap）。

```cpp
struct PMImpl {                         // PMImpl = "PrettyMenu

    std::tr1::shared_ptr<Image> bgImage; // Impl."; see below for

    int imageChanges;                   // why it's a struct  p132解释
};

class PrettyMenu {

    ····

private:
    Mutex mutex;

    std::tr1::shared_ptr<PMImpl> pImpl;
};

void PrettyMenu::changeBackground(std::istream& imgSrc)
{

    using std::swap;                        // see Item 25

    Lock ml(&mutex);                        // acquire the mutex

    std::tr1::shared_ptr<PMImpl>            // copy obj. data

        pNew(new PMImpl(*pImpl));

    pNew->bgImage.reset(new Image(imgSrc)); // modify the copy

    ++pNew->imageChanges;

    swap(pImpl, pNew);                      // swap the new

                                            // data into place

}                                           // release the mutex
```

- copy and swap 虽然对于对象状态的回退是个好办法，但是它并不能保证整个函数，尤其当函数内部调用了其他函数方法，那么就变成了木桶效应，整个函数的异常安全级别由最低的那个函数决定。
- 保证异常安全对于效率上的影响也是需要考虑的，有时刻意的提供强烈保证的异常安全导致的效率与复杂度对于其他人也是灾难的，因此效率、复杂度与将要提供的安全等级之间需要寻求平衡。

### 条款 30：透彻了解 inlining 的里里外外

- inline 函数不仅仅时免去了调用关系，还开放了编译器对代码的最优化能力。
- inline 函数的代价：目标码变大、降低 cache 命中率影响效率。
  - 但是换个角度说，如果 inline 函数的本体很小，那么编译器优化后的代码可能比针对函数调用所产生的代码更小，这就是向好的方向前进了。因此 inline 函数要尽量短小精悍。
- inline 函数通常置于头文件中由于 Inlining 大多发生在 C++ 程序的编译期，在进行替换时需要了解函数实现。Templates 通常置于头文件中也是相同原因，它一旦被使用编译器为了具现它需要了解其具体实现。
- 大部分编译器会拒绝复杂的函数（例如带有循环或递归）的函数 inlining，并且对于所有的虚函数都不会 inlining，这是因为虚函数是当运行期才决定调用哪个，而 inline 则是编译期进行替换因此编译器不知道该替换那个函数。因此一个表面上看似 inline 的函数是否真的 inlining，取决于你使用的编译器以及编译环境。
- 调用方式也会影响是否以 inlining 的方式调用：

```cpp
inline void f() {...}      // assume compilers are willing to inline calls to f
void (*pf)() = f;          // pf points to f

...

f();                      // this call will be inlined, because it's a "normal" call
pf();                     // this call probably won't be, because it's through
                          // a function pointer
```

- 构造函数与析构函数往往是 inlining 的糟糕候选人，即使是空的构造函数背后也有着很多工作大多由编译器实现，由编译器于编译期间产生并安插到你的程序中的代码，有时就放在你的构造和析构函数内。而这部分实现中可能会调用 base class 或者其他成员变量的构造，而这些调用均会影响编译器是否对此空白构造函数 inlining。
- 程序库中必须考虑 inline 函数所带来的耦合，一旦某个 inline 函数进行了修改，则所有用到这个函数的关联库都必须重新编译。

### 条款 31：将文件间的编译依存关系降至最低

- include 包括的头文件造成文件间的依赖关系。

- 使用前置声明注意的问题：

  - 不该声明标准程序库（类似 std::string 是一个模板实现 typedef 成为 string）。
  - 前置声明 class 编译器无法获取到对象的大小。

- 针对前置声明获取不到 class 大小的问题：

  - 可以将类分割为两部分，一个只提供接口，另一个负责具体实现该接口，这种设计就是 pimple idiom 也被成为 Handle class：

  ```cpp
    #include <string>                      // standard library components
                                           // shouldn't be forward-declared
    #include <memory>                      // for tr1::shared_ptr; see below
  
    class PersonImpl;                      // forward decl of Person impl. class
    class Date;                            // forward decls of classes used in
    class Address;                         // Person interface
  
    class Person {
    public:
        Person(const std::string& name, const Date& birthday,
                const Address& addr);
  
        std::string name() const;
  
        std::string birthDate() const;
  
        std::string address() const;
    ...
    private:                                     // ptr to implementation;
  
        std::tr1::shared_ptr<PersonImpl> pImpl;  // see Item 13 for info on
  
    };                                            // std::tr1::shared_ptr
  ```

  - 这种分离关键在于以 “声明的依存性” 替换 “定义的依存性”，这便是编译依存性最小化本质：现实中让头文件尽可能自我满足，如果做不到，则让它于其他文件内的声明式（非定义式）相依。
    - 如果使用 **引用** 或者 **指针** 可以完成任务，就不要使用 object 定义式。
    - 尽量以 class 声明式替换 class 定义式。
    - 为声明式和定义式提供不同的头文件。

- 另一种 Handle class 的方法是令目标类成为一个 抽象基类，描述出接口通过派生具体实现，这种实现称为 Interface class。

  - 而使用时需要以抽象基类的指针或者引用来编写应用程序，这就需要一个构建方法工厂、组件等等用来得到 Handle。

- Handle classes 和 Interface classes 解除了接口和实现之间的耦合关系，从而降低了文件间的编译依赖性。但同样的它也存在的一些缺点：

  - 在 Handle classes 身上，成员函数通过 implementation pointer 取得对象数据，为每一次的访问增加了一层间接层，而每一个对象消耗的内存数量必须增加 implementation pointer，并且 implementation pointer 需要初始化，指向一个动态分配得来的 implementation object，所以必须承受动态内存分配于释放带来的消耗以及 bad_alloc 的异常可能。
  - 置于 Interface classes，由于每个函数都是 virtual，所以你必须为每次函数调用付出一个间接跳跃，此外还要承受 vptr（条款 7）等虚函数所带来的成本。
  - 不论 Handle classes 和 Interface classes 都不能充分利用 inline 函数，因为 inline 的具体实现都需要放入头文件内，而这两种方式均为了隐藏具体实现而努力。

## 继承于面向对象设计

### 条款 32：确定你的 public 继承塑模出 is-a 关系

- public 继承中：基类体现出一般化，派生类体现出特殊化。
- 语言于事实上的差异可能令继承关系显得不伦不类，就像企鹅于鸟的关系。但是具体的实现还是要看功能，假如你只考虑鸟喙、爪子等等，那么就不用担心企鹅与鸟的基类是否要由 fly 啦。
- public 继承意味着 is-a 。适用于 base classes 上的每一件事情一定适用于 derived classes 身上，因为每一个 derived class 对象也都是一个 base class 对象。

### 条款 33：避免遮掩继承而来的名称

- 众所周知😄 C++ 作用域就近原则，内层遮掩外层。而在继承关系中，派生类的成员函数内指向基类中的成员时，编译器可以找到相应的成员，这是由于派生类作用域被嵌套在基类的作用域内，

![scope]()

```cpp
class Base {
private:

  int x;

public:

  virtual void mf1() = 0;

  virtual void mf2();

  void mf3();
  ...
};

class Derived: public Base {
public:

  virtual void mf1();

  void mf4();
  ...
};

```

- 而当我们重载了基类的方法后，mf3 注意仅仅重载了无参数版本：

```cpp
class Base {

private:

  int x;

public:

  virtual void mf1() = 0;

  virtual void mf1(int);

  virtual void mf2();

  void mf3();

  void mf3(double);

  ...

};

class Derived: public Base {

public:

  virtual void mf1();

  void mf3();

  void mf4();

  ...

};
```

- 而这时进行调用，这就体现出了从名称查找的观点。这和本条款一开始展示的道理相同，当时函数 someFunc 内的 double x 遮掩了 global 作用域内的 int x，如今 Derived 内的函数 mf3 遮掩了一个名为 mf3 但类型不同的 Base 函数：

```cpp
Derived d;

int x;

...

d.mf1();                   // fine, calls Derived::mf1

d.mf1(x);                  // error! Derived::mf1 hides Base::mf1  可以看到派生类遮掩了基类的其他多态方法

d.mf2();                   // fine, calls Base::mf2

d.mf3();                   // fine, calls Derived::mf3

d.mf3(x);                  // error! Derived::mf3 hides Base::mf3 非虚的也是一样
```

- 那么该如何使用基类的其他不同参数的同名方法呢，这就可以使用 using 来在派生类中探查到基类内指定名称的方法。

```cpp
class Derived: public Base {

public:

  using Base::mf1;       // make all things in Base named mf1 and mf3

  using Base::mf3;       // visible (and public) in Derived's scope


  virtual void mf1();

  void mf3();

  void mf4();

  ...

};
```

- 而如果派生类是通过 private 继承基类时，并且仅仅想要继承 mf1 哪个无参数的版本，这时 using 就不能用了，因为它会导致所有 mf1 的函数在派生类作用域可见，这时就要用到一个转交函数：

```cpp
class Base {

public:

  virtual void mf1() = 0;

  virtual void mf1(int);

  ...                                    // as before

};

class Derived: private Base {

public:

  virtual void mf1()                   // forwarding function; implicitly

  { Base::mf1(); }                     // inline (see Item 30)
  ...

};

...

Derived d;

int x;

d.mf1();                               // fine, calls Derived::mf1

d.mf1(x);                              // error! Base::mf1() is hidden
```

### 条款 34：区分接口继承和实现继承

- 派生类所继承的内容包括：函数接口继承与函数实现继承，可能存在的继承情况：

  - 派生类只继承接口的声明。
  - 同时继承接口与实现，但对某个接口实现还要可以 override。
  - 继承接口与实现不允许 override。

- 抽象基类总是对 public 继承的派生类起到影响：

  - 声明一个 pure virtual 函数的目的是为了让派生类只继承函数接口。但是我们还可以对纯虚函数提供具体实现定义，调用的唯一途径是明确指出其 class 名称。
    - 成员函数的接口总是会被继承，所有抽象基类的接口在 public 继承的情况下遵循 is-a 关系，其接口应该对所有派生类有效。
  - 声明一个 impure virtual 非纯虚函数的目的是让派生类继承该函数的接口和缺省实现。
    - 但是允许 impure virtual 函数同时指定函数声明和函数缺省行为，可能导致新增派生类时忘记新增 override 该函数造成错误，而这种错误只有在运行期间才会被发现。
  - 因此我们需要切断 virtual 函数接口和其缺省实现之间的联系，除非明确要求继承基类的默认实现。

  ```cpp
    class Airplane {
    public:
  
    virtual void fly(const Airport& destination) = 0;
    ...
    protected: //因为它时 Airplane 以及 derived classes 的实现细目
  
        void defaultFly(const Airport& destination);
  
    };
  
    void Airplane::defaultFly(const Airport& destination)
    {
  
        //default code for flying an airplane to the given destination
  
    }
  
    // 若想使用缺省实现，可以在 fly 函数中对 defaultFly 做一个 inline 调用
    class ModelA: public Airplane {
    public:
  
    virtual void fly(const Airport& destination)
        { defaultFly(destination); }
  
        ...
    };
  
    class ModelB: public Airplane {
    public:
  
        virtual void fly(const Airport& destination)
        { defaultFly(destination); }
  
        ...
    };
  ```

  - 上述的方法存在一个问题便是由于分别提供接口与缺省实现，可能由于过度雷同的命数名称引起命名空间污染，因此我们可以利用 pure virtual 函数必须在 derived classes 中重新声明，但是纯虚函数也可以拥有自己的实现特性。
    - 如果合并 fly 和 defaultFly，就丧失了“让两个函数享有不同保护级别”的机会。

  ```cpp
    class Airplane {
  
    public:
        virtual void fly(const Airport& destination) = 0;
  
        ...
    };
  
    void Airplane::fly(const Airport& destination) // an implementation of
    { // a pure virtual function
  
        default code for flying an airplane to the given destination
  
    }
  
    class ModelA : public Airplane {
  
    public:
        virtual void fly(const Airport& destination)
        {
            Airplane::fly(destination);
        }
  
        ...
    };
  
    class ModelB : public Airplane {
  
    public:
        virtual void fly(const Airport& destination)
        {
            Airplane::fly(destination);
        }
  
        ...
    };
  
    class ModelC : public Airplane {
  
    public:
        virtual void fly(const Airport& destination);
  
        ...
    };
  
    void ModelC::fly(const Airport& destination)
    {
  
        code for flying a ModelC airplane to the given destination
  
    }
  ```

- 声明 non-virtual 函数的目的时为了令 derived classes 继承函数的接口及一份强制性实现。

### 条款 35：考虑 virtual 函数以外的其他选择

- 籍由 Non-Virtual Interface 手法实现 Template Method 模式：

  - 及通过一个 public 非虚接口隐藏掉虚接口具体的调用实例，并且可以灵活的按要求调用相关虚接口，这种方法称为 NVI (Non-Virtual Interface)。

  ```cpp
    class GameCharacter {
  
    public:
        int healthValue() const // derived classes do not redefine
        { // this — see Item 36
  
            ...; // do "before" stuff — see below
  
            int retVal = doHealthValue(); // do the real work
  
            ...; // do "after" stuff — see below
  
            return retVal;
        }
  
        ...;
  
    private:
        virtual int doHealthValue() const // derived classes may redefine this
        {
  
            ...; // default algorithm for calculating
  
        } // character's health
    };
  ```

  - NVI 手法优势便是派生类有权重写 virtual 的 doHealthValue 方法具体的实现，但是基类的 healthValue 对外方法接口保留了调用的方法一致性。

- 籍由 Function Pointers 实现 Strategy 模式

  - Function Pointers 手法便是以传入函数指针的特性来实现 virtual 派生类各自实现的多样性。以 NVI 中的例子便是 doHealthValue 接口用外部传入的计算方法函数指针代替。

  ```cpp
    class GameCharacter; // forward declaration
  
    // function for the default health calculation algorithm
  
    int defaultHealthCalc(const GameCharacter& gc);
  
    class GameCharacter {
  
    public:
        typedef int (*HealthCalcFunc)(const GameCharacter&);
  
        explicit GameCharacter(HealthCalcFunc hcf = defaultHealthCalc)
            : healthFunc(hcf)
  
        {
        }
  
        int healthValue() const
  
        {
            return healthFunc(*this);
        }
  
        ...
  
    private :
        HealthCalcFunc healthFunc;
    };
  ```

  - 与 NVI 相比的特点：
    - 同一人物类型之间可以有着不同的 `健康计算函数`；
    - 某一只任务的 `健康计算函数` 可以在运行期变更；
  - 存在的问题：
    - 如果需要获取目标任务的 non-public 接口提供的数据，便存在无法获取的问题；
    - 一般解决上边的问题首先想到的便是`弱化 class 封装`使用 friends 友员，这便是使用时需要权衡的。

- 籍由 tr1::function 完成 Strategy 模式

  - 上述的两种方法 NVI 与 function ptr 对于模板来似都存在死板的局限性。使用 tr1::function 可以持有任何可调用物（函数指针、函数对象、或成员函数指针），只要其签名式兼容于需求端。

  ```cpp
    class GameCharacter;                                 // as before
    int defaultHealthCalc(const GameCharacter& gc);      // as before
  
    class GameCharacter {
    public:
  
    // HealthCalcFunc is any callable entity that can be called with
    // anything compatible with a GameCharacter and that returns anything
    // compatible with an int; see below for details
    // 这里的函数签名便是 返回一个 int 接受一个 const GameCharacter 的引用签名
    typedef std::tr1::function<int (const GameCharacter&)> HealthCalcFunc;
  
    explicit GameCharacter(HealthCalcFunc hcf = defaultHealthCalc)
    : healthFunc(hcf)
    {}
  
    int healthValue() const
    { return healthFunc(*this);   }
  
    ...
  
    private:
        HealthCalcFunc healthFunc;
    };
  ```

```
EvilBadGuy ebg1(calcHealth);                        // character using a
                                                    // health calculation
                                                    // function
```

```
  - tr1::function 可以兼容符合函数签名的各种函数指针:

  ```cpp
    short calcHealth(const GameCharacter&); // health calculation
                                            // function; note
                                            // non-int return type

    struct HealthCalculator {                       // class for health
        int operator()(const GameCharacter&) const  // calculation function
        {
            ...
        }                                           // objects
    };

    class GameLevel {
    public:
        float health(const GameCharacter&) const;   // health calculation
        ...                                         // mem function; note
    };                                              // non-int return type

    class EvilBadGuy : public GameCharacter {       // as before
        ...
    };

    class EyeCandyCharacter : public GameCharacter {    // another character
        ...                                             // type; assume same
    };                                                  // constructor as

    // EvilBadGuy
    EvilBadGuy ebg1(calcHealth);    // character using a
                                    // health calculation
                                    // function

    EyeCandyCharacter ecc1(HealthCalculator()); // character using a
                                                // health calculation
                                                // function object
    GameLevel currentLevel;
    ...

    EvilBadGuy ebg2(                        // character using a
        std::tr1::bind(&GameLevel::health,  // health calculation
                        currentLevel,       // member function;
                        _1)                 // see below for details
    );
```

- 在使用 GameLevel class 的成员函数 health 时，由于他是成员函数会有一个隐藏的参数就是 this，因此需要转换，这就是 std::tr1::bind 的作用了。

- 古典 Strategy 模式

  - 使用一个计算类方法，通过派生实现不同的计算方法，统一传入需要的地方。

  ```cpp
    class GameCharacter;                            // forward declaration
    class HealthCalcFunc {
    public:
        ...
        virtual int calc(const GameCharacter& gc) const
        { ... }
        ...
    };
  
    HealthCalcFunc defaultHealthCalc;
  
    class GameCharacter {
    public:
        explicit GameCharacter(HealthCalcFunc *phcf = &defaultHealthCalc)
        : pHealthCalc(phcf)
        {}
  
        int healthValue() const
        { return pHealthCalc->calc(*this);}
  
        ...
    private:
        HealthCalcFunc *pHealthCalc;
    };
  ```

### 条款 36：绝不重新定义继承而来的 non-virtual 函数

```cpp
class B {
public:
    void mf();
    ...
};

class D : public B {
    ...
};

// Even without knowing anything about B, D, or mf, given an object x of type D,
D x; // x is an object of type D

// you would probably be quite surprised if this,
B* pB = &x; // get pointer to x
pB->mf(); // call mf through pointer

//behaved differently from this :

D* pD = &x; // get pointer to x
pD->mf(); // call mf through pointer

```

- 注意派生类 D 中覆写了基类 B 中的同名 mf 方法，导致的问题便是同一个派生类指针，转为基类后调用的同名方法变为了基类中的 mf 方法，造成这种两面行为是由于 non-virtual 函数如 B::mf 和 D::mf 都是静态绑定的，通过什么类型调用就是其类型所定义的版本。另一方面 virtual 函数时动态绑定，所以即使转成了基类类型，最终通过虚函数表还是会调用到原始指针类型所定义的方法上。
- 另一个问题便是 D 的行为于 B 出现了分歧，不再符合了 public 继承的 is-a 原则：
  - 适用于 B 对象的每一件事情，都适用于 D，因为每一个 D 对象都是一个 B 对象；
  - B 的 derived classes 一定会继承 mf 的接口和实现，因为 mf 时 B 的一个 non-virtual 函数。

### 条款 37：绝不重新定义继承而来的缺省参数值

- 由于默认参数静态绑定，因此在派生类中重复指定默认参数时无效的，最终依旧会使用基类中的指定默认参数。
- 这么做的原因便是效率，如果想要类似 virtual 接口一样动态绑定便会扩大虚表。
- 如果想要给 virtual 接口加上默认参数，可以使用 NVI 手法来增加。

### 条款 38：通过复合塑模出 has-a 或“根据某物实现出”

- 复合（composition）是类型之间的一种关系，当某种类型的对象内含其他类型的对象，便是这种关系。“public” 继承标识者 is-a 关系，而复合便是 has-a 或者 is-implemented-in-terms-of （根据某物实现出）。在应用域（application domain），复合意味着 has-a （有一个）。在实现域（implementation domain），复合意味着 is-implemented-in-terms-of （根据某物实现出）。

### 条款 39：明智而审慎地使用 private 继承

- private 继承与 public 继承存在许多差异：
  - 不会自动将 derived class 转化为 base class。
  - 继承来的成员、方法，权限均为 private。
- private 意味着 is-implemented-in-terms-of （根据某物实现出）。派生类与父类之间的关系并不大。Private 继承在软件 “设计”层面上没有意义，其意义只及于软件实现层面。与**复合**在实现域一样，我们需要知道尽可能使用复合，必要时才使用 **private 继承**。
  - 当实现某些功能时需要一些其他类辅助，但是这两个类之间并非 is-a 的关系，这时便可以使用 private 继承。
- 还可以考虑如书中 p189 展示的 复合 + public 继承的方式来避免 private 继承，至于避免 private 继承的好处：
  - 可以防止 derived class 重新定义某些接口，如果通过 private 继承其无法防止派生类去重新定义 virtual 函数，但是如果通过 private 复合成员，其派生类无法取用便没有办法在重新定义了。
  - 不使用编译的依赖程度可以降低。
- 和复合不同，private 继承可以用来实现 empty base 最优化。这对致力于“对象尺寸最小化”的程序库开发者来说可能会很有用。

### 条款 40：明智而审慎地使用多重继承

- 多重继承比单一继承更加复杂，它可能导致新的歧义性，以及对 virtual 继承的需要。
- virtual 继承会增加大小、速度、初始化复杂度等等成本，如果 virtual base classes 不带任何数据，将是最具实用价值的情况。
- 多重继承的确有政党用途。例如涉及 public 继承某个 interface class 和 private 继承某个协助实现的 class 的两项组合。

## 模板于泛型编程

### 条款 41：了解隐式接口和编译器多态

- 显式的接口于运行期多态是 C++ 面向对象典型的使用方式，但是在 Templates 及泛型编程种，隐式接口和编译器多态更加典型且重要。
  - 隐式接口的优势便是具体接口需要支持的类型取决于其操作，凡是涉及到模板参数 `Template<typename T>` 模板接口的使用时，就有可能造成模板具现化，且这种具现行为发生在编译期，以不同的模板参数 T 可以具现出不同的接口，这就是编译期多态。
  - 显式接口通常由函数的签名式构成，多态则是通过 virtual 函数发生于运行期。而 template 参数而言，接口是隐式的，奠基于有效表达式。多态则是通过 template 具现化和函数重载解析发生于编译期。

### 条款 42：了解 typename 的双重含义

```cpp
template<class T> class Widget;
template<typename T> class Widget;
```

- 上述两种 template 声明式中，class 于 typename 并没有什么不同。然而 C++ 并不总是把 class 和 typename 视为等价。
- 从属名称：template 内出现的名称如果相依于某个 template 参数，称之为从属名称（dependent names）。