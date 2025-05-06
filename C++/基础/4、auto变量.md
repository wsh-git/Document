# 定义：

变量名前面有关键字`auto`的变量；

# 作用：

让编译器自动推断变量的类型；减少手动定义类型的麻烦，提高代码的简洁性；代码可读性受到影响，必须在声明时进行初始化，否则编辑器无法推断类型；

# 注意：

在初学阶段，不太建议频繁使用`auto`，因为不太有利于查看逻辑；

# 举例：

```c++
#include <iostream>

using namespace std;

int main() {
    int a = 1;
    auto b = false; // b 就是boolean类型
}
```
