# constexpr函数可以在编译时计算，也可以在运行时求值

> [!constexpr函数何时在编译时求值？]
> 如果在需要常量表达式的地方使用返回值，则有资格在编译时计算的constexpr函数将仅在编译时求值。否则，不能保证编译时计算。
> 
> 因此，constexpr函数最好被认为是“可以在常量表达式中使用”，而不是“将在编译时求值”。
> 
> [[Constexpr函数在编译时和运行时的区别]]

# consteval函数

C++20引入了关键字consteval，用于指示函数必须在编译时求值，否则将导致编译错误。这种函数称为即时函数（immediate functions）。

```C++
#include <iostream>

consteval int greater(int x, int y) // function 现在是 consteval
{
    return (x > y ? x : y);
}

int main()
{
    constexpr int g { greater(5, 6) };              // ok: 在编译时求值
    std::cout << g << '\n';

    std::cout << greater(5, 6) << " is greater!\n"; // ok: 在编译时求值

    int x{ 5 }; // not constexpr
    std::cout << greater(x, 6) << " is greater!\n"; // error: consteval 函数必须在编译时求值

    return 0;
}
```

# constexpr/consteval函数隐式内联

因为constexpr函数可以在编译时求值，所以编译器必须能够在调用该函数的所有点上看到constexpl函数的完整定义。前向声明是不够的，即使实际的函数定义稍后出现在同一编译单元中。

这意味着在多个文件中调用的constexpr函数需要将其定义包含在对应的文件中——这通常会违反单定义规则。为了避免这样的问题，constexpr函数是隐式内联的，这使得它们不受单定义规则的约束。

因此，constexpr函数**通常在头文件中定义**，因此它们可以被 `#include` 在任何需要完整定义的.cpp文件中。

出于相同的原因，consteval函数也隐式内联。

# constexpr函数可以调用非常量表达式函数

[[测试constexpr函数]]时，使用常量上下文。因为constexpr函数可能可以在非常量上下文可以编译，但是在常量上下文中不行。