# `std::cin`获取字符串输入

将`std::string`与`std::cin`一起使用可能会产生一些意外！考虑以下示例:

```C++
#include <iostream>
#include <string>

int main()
{
    std::cout << "Enter your full name: ";
    std::string name{};
    std::cin >> name; // 可能不一定按预期工作，因为std::cin读取到 空白字符，就会停止

    std::cout << "Enter your favorite color: ";
    std::string color{};
    std::cin >> color;

    std::cout << "Your name is " << name << " and your favorite color is " << color << '\n';

    return 0;
}
```
下面是此程序的示例运行结果:
```C++
Enter your full name: John Doe
Enter your favorite color: Your name is John and your favorite color is Doe
```
发生了什么事？结果是，当使用 操作符» 从`std::cin`中提取字符串时，操作符» 仅返回其遇到的第一个空格之前的字符。任何其他字符都留在`std::cin`中，等待下一次提取。

所以，当我们使用 操作符» 将输入提取到变量名中时，只提取了“John”，将“Doe”留在`std::cin`中。然后，当我们使用 操作符» 提取输入到color变量时，它提取了“Doe”，而不是等待我们输入。然后程序结束。

# 什么是`std::ws`？

`std::ws`输入操纵器告诉`std::cin`在提取之前忽略任何前导空格。前导空格是出现在字符串开头的任何空格字符（空格、制表符、换行符）。

# 初始化`std::string`的开销很大

每当初始化`std::string`时，都会生成用于初始化它的字符串的副本。复制字符串的成本很高，因此应注意将复制的数量降至最低。

当通过值将`std::string`传递给函数时，必须实例化`std::string`函数参数，并使用参数进行初始化。这将导致昂贵的拷贝。我们将在——`std::string_view`简介中讨论如何做（使用`std:∶string_view`）。