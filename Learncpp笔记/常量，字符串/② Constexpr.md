# constexpr关键字

**constexpr**（“常量表达式”的缩写）变量只能是编译时常量。如果constexpr变量的初始化值不是常量表达式，编译器将报错。

```

```C++
#include <iostream>

int five()
{
    return 5;
}

int main()
{
    constexpr double gravity { 9.8 }; // ok: 9.8 是常量表达式
    constexpr int sum { 4 + 5 };      // ok: 4 + 5 是常量表达式
    constexpr int something { sum };  // ok: sum 是常量表达式

    std::cout << "Enter your age: ";
    int age{};
    std::cin >> age;

    constexpr int myAge { age };      // 编译报错: age 不是常量表达式
    constexpr int f { five() };       // 编译报错: five() 返回值不是常量表达式

    return 0;
}
```

# [[常量折叠（constant folding）]]


 
