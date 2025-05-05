# 一、参数默认值

## 定义：

有参数默认值的参数，一般称为可选参数；

## 作用：

当调用函数时可以不传入参数，不传就会使用默认值作为参数的值；

## 注意：

1、声明时带有默认值就行了，定义不能带有默认值，否则报错（除非声明和定义一起完成）；

2、支持多参数默认值，每个参数都可以有默认值；

3、如果要混用可选参数，必须写在普通参数后面；

## 举例：

```c++
#include <iostream>

using namespace std;

// 声明
void speak01(string message = "this is message.");
void speak02(string name = "LILY", float age = 6, string message = "this is message.");
void speak03(string name, float age, string message = "this is message.");

// 使用
int main() {
    speak01();
    speak01("this is custom message.");
    
    speak02();
    speak02("lily");
    speak02("lily", 6);
    
    speak03("lily", 6);
    speak03("lily", 6, "this is custom message.");
}

// 定义
void speak01(string message) {
    cout << message << endl;
}

void speak02(string name, float age, string message) {
    cout << name << age << message << endl;
}

void speak03(string name, float age, string message) {
    cout << name << age << message << endl;
}
```



# 二、函数的重载

## 定义：

在同一作用域中（比如全局作用域，结构体、类中），函数名相同，参数的数量不同、参数的类型不同，参数的顺序不同；

## 作用：

用来处理不同参数的同一类型的逻辑处理；

## 注意：

在使用重载函数时，一定要记住先声明；

如果忘记了声明，可能调用的函数并不会是你想象中的那个函数（类型的强制转换），而是参数数量相同的另一个重载函数；

默认参数（可选参数）会影响重载，编译器会不清楚该选择哪个重载；

## 举例：

```c++
#include <iostream>

using namespace std;

// 声明
void test01(int a, int b);
void test01(float a, float b);

void test02(int a, int b, int c);
void test02(int a, int b, float c);
void test02(int a, float b, int b);

// 使用
int main() {
    test01(1, 3);
    test01(1.1, 1.3); // 如果不声明 void test01(float a, float b);会调用void test01(int a, int b);
}

// 定义
void test01(int a, int b) {
    
}

void test01(float a, float b) {
    
}

void test02(int a, int b, int c) {
    
}

void test02(int a, int b, float c) {
    
}

void test02(int a, float b, int b) {
    
}
```



# 三、内联函数

## 定义：

内联函数是一种特殊的函数，需要使用`inline`关键字对函数进行声明或定义；

关键字`inline`告诉编辑器，在调用函数的时候，将函数的代码直接插入到调用该函数的位置，而不是执行常规的函数调用的过程。

## 作用：

减少函数调用的开销，适用于小型的、频繁调用的函数；

### 调用函数的开销

函数使用的开销主要涉及到压栈、跳转、返回等操作，而内联函数通过将函数代码直接插入到调用点来避免这些开销；

## 注意：

1、递归函数不能内联；

2、大型函数不适合内联（比如函数中有循环或条件分支语句）；

3、内联函数的调用会带来代码膨胀（即增大可执行文件的体积）；

4、如果你的函数过于复杂或代码量较大，即使使用了内联关键字，编译器可能也会忽略它；

## 举例：

```c++
#include <iostream>

using namespace std;

// 声明
inline int add(int a, int b)
    
// 使用
int main() {
    int sum = add(1, 3);
}

// 定义
inline int add(int a, int b) {
    return a + b;
}
```



# 四、auto变量

## 定义：

变量名前面有关键字`auto`的变量；

## 作用：

让编译器自动推断变量的类型；减少手动定义类型的麻烦，提高代码的简洁性；代码可读性受到影响，必须在声明时进行初始化，否则编辑器无法推断类型；

## 注意：

在初学阶段，不太建议频繁使用`auto`，因为不太有利于查看逻辑；

## 举例：

```c++
#include <iostream>

using namespace std;

int main() {
    int a = 1;
    auto b = false; // b 就是boolean类型
}
```



# 五、static变量

## 定义：

static 变量类型 变量名；

## 作用：

static 修饰的变量会在程序的整个生命周期内存储，就算是在函数内部声明，也遵循这一规则；

可以用来声明静态局部变量、静态全局变量、静态类成员等；

声明一次，永久使用；

## 注意：

静态变量只初始化一次，且一直保留值，适合全局共享信息或缓存的场景，因此也会增加内存的消耗；

除非有需求，否则不要过多的使用静态变量；



### 静态全局变量和全局变量的区别

全局变量：可以在多个文件中访问，适合需要共享数据的情况；

静态全局变量：只能在定义它的文件中访问，适合只在单个源文件内部使用的数据；

## 举例：

```c++
#include <iostream>

using namespace std;

// 声明
static int aa = 1; // 全局静态变量，伴随整个程序的生命周期；
void test();

// 使用
int main() {
    test();
}

// 定义
void test() {
    // 静态局部变量只有在第一次调用的时候才会初始化，之后就一直存在了
    // 不会重复的去分配内存空间（不会重复声明）
    static int a = 1;
    // todo:
}

```



# 六、register变量

## 定义：

register 变量类型 变量名称

寄存器和内存是计算机中两种不同类型的数据存储方式；

寄存器：寄存器是cpu内部的一部分，用于存储正在被处理的数据和指令，是cpu中最快的存储单元，位于处理器的核心部分；

内存：是指计算机系统中用于存储数据和程序指令的区域；内存的存储位置位于cpu外部，但于cpu通过总线连接；内存一般指内存条、硬盘中虚拟内存中的存储空间；

## 作用：

`register`修饰的变量会变为寄存器变量，会将变量存储在cpu的寄存器中，而不是存储在内存中，这一可以有效的提高访问速度，当使用变量时将直接从寄存器中读写，适合循环中的计数器等高频访问的变量；

## 注意：

在大多数编程环境下，无法直接操作寄存器上的内容，相对于程序来说，寄存器是一个由硬件自动管理的存储区域；在大多数编程环境下，我们提到的内存通常指存储在内存条中的数据，而不是cpu内部的寄存器；

在现代c++开发中使用较少，因为现代编译器中会自动优化变量的存储位置，往往比我们收到使用`register`关键词更加有效，在较新版本的c++中已经被废弃了；

现代编译器通常已经非常优化，对寄存器的分配也比较智能，显示使用`register`可能不会带来明显的性能提升；

`register`修饰的变量是不能获取该变量的地址的，因为在寄存器中没有地址（寄存器变量无法使用取地址符 &）；

## 举例：

```c++
int main() {
    register int a = 1;
    for(register int i = 0; i < 10; i++) {
        
    }
}
```

