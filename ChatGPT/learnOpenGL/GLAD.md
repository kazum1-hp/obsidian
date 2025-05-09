

---


**OpenGL 是一个标准，它定义了函数该怎么“长什么样子”和“做什么”，但真正的实现是在你的显卡驱动里。**

---

## 🔧 为什么不能在编译时直接使用所有 OpenGL 函数？

当你写代码时，比如：

```cpp
glGenBuffers(1, &buffer);
```

你以为这个函数是“天然就有”的对吧？其实不是——它**不是像 `printf` 一样在标准库里早就编译好了的函数**，而是存在于**显卡驱动程序**中，是运行时动态加载的。

---

## 🔍 那怎么加载这些函数？

在 Windows 上，OpenGL 提供了一个函数：

```cpp
void* wglGetProcAddress(const char* name);
```

这个函数可以让你在运行时“向驱动请求”某个 OpenGL 函数，比如：

```cpp
GL_GENBUFFERS glGenBuffers = (GL_GENBUFFERS)wglGetProcAddress("glGenBuffers");
```

上面这一句的意思是：

> “嘿显卡驱动，给我 `glGenBuffers` 这个函数的地址吧，我想用。”

---

## 🙄 问题来了：太麻烦了！

你每调用一个函数就得：

1. 写 typedef 函数原型；
    
2. 用 `wglGetProcAddress` 取地址；
    
3. 自己定义函数指针；
    
4. 赋值；
    
5. 才能调用。
    

**几十个、几百个函数你受得了吗？**（你受得了我也不受得了😤）

---

## 🧰 所以怎么办？这时候，GLAD 出场！

GLAD 是一个 **OpenGL 加载库**，它自动帮你：

- 把所有 OpenGL 函数名、函数指针都声明好；
    
- 自动写好 `wglGetProcAddress` 调用；
    
- 在你程序初始化时，一次性加载全部需要的函数；
    
- 你就可以像普通函数一样直接用 `glGenBuffers()`，不用自己做类型转换和地址绑定了！
    

---

### 📦 简单说：

没有 GLAD 你就要这样用：

```cpp
typedef void (*GL_GENBUFFERS)(GLsizei, GLuint*);
GL_GENBUFFERS glGenBuffers = (GL_GENBUFFERS)wglGetProcAddress("glGenBuffers");
glGenBuffers(1, &buffer);
```

有了 GLAD，只要：

```cpp
#include <glad/glad.h>
glGenBuffers(1, &buffer); // 就这么用！
```

---

