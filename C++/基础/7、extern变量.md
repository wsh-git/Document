# 定义：

extern 变量类型 变量名

# 作用：

`extern`允许在不同文件间共享全局变量和函数；

当我们在一个源文件中定义了全局变量或函数时，可以通过`extern`关键字在其他文件中使用定义好的内容；

方便管理全局数据，支持跨文件使用相同的全局变量；

# 注意：

只对确实需要跨文件使用的全局变量内容使用`extern`；

全局变量过多会导致程序设计变得复杂，容易引入错误；

如果不慎使用，可能导致多个文件对全局变量的修改难以追踪，增加调试和维护的难道；

## 使用外部变量时的注意点

当多个文件中有重名的全局变量（c++编译器不允许多个cpp文件中定义同名全局变量，直接编译报错）

同一个作用域定义同名变量

# 举例：

> test.cpp

```c++
#include <iostream>

using namespace std;

int a = 1;
string b = "testcpp";
float c = 1.1;

void testFunc() {
    cout << "text func" << endl;
}

void testFunction(int a) {
    cout << a << endl;
}
```

> main.cpp

```c++
#include <iostream>

using namespace std;

// 外部变量
extern int a;
extern string b;
extern float c;

// 外部方法
extern void testFunc();
extern void testFunction(int a);

int main() {
    cout << a << endl;
    cout << b << endl;
    cout << c << endl;
    
    testFunc();
    testFunction(1);
}
```
