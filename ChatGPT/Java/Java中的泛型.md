

---

### 💡 Java 中的泛型为什么不能直接使用基本数据类型？

Java 的泛型（Generics）设计目标是为了**在编译时期进行类型检查**，并且**实现类型的安全性和代码的重用性**。

但有一个限制：  
➡ **泛型只能接受引用类型（Reference Types），不能接受基本数据类型（Primitive Types）**。

---

### ✅ 原因详解：

#### 1. **泛型是“语法糖”，在编译后会进行类型擦除（Type Erasure）**

Java 的泛型是通过类型擦除实现的。  
也就是说，编译器在编译时会把泛型中的类型参数“擦除”掉，替换为一个原始类型（通常是 `Object` 或者边界类型）。

例如：

```java
List<Integer> list = new ArrayList<>();
```

编译后大致会变成：

```java
List list = new ArrayList();
```

然后在使用的时候会自动插入强制类型转换。

但问题是：  
➡ Java 的基本数据类型（如 `int`, `double`）不是 `Object` 的子类，**不能直接替换为 Object 来使用**。

---

#### 2. **基本类型不是对象（Object）**

Java 的泛型系统只能处理引用类型，比如类和接口。  
而 `int`、`double`、`boolean` 等基本类型不是对象，不能当作泛型的类型参数。

---

### 🧩 解决方案：使用包装类（Wrapper Classes）

为了能在泛型中使用基本数据类型，Java 提供了包装类：

|基本类型|包装类|
|---|---|
|int|Integer|
|double|Double|
|char|Character|
|boolean|Boolean|
|...|...|

Java 5 开始还引入了 **自动装箱（Autoboxing）/拆箱（Unboxing）**：

```java
List<Integer> list = new ArrayList<>();
list.add(10);  // 自动装箱：int -> Integer
int x = list.get(0);  // 自动拆箱：Integer -> int
```

---

### ✅ 总结一句话：

> Java 的泛型只能接受引用类型，而基本数据类型不是对象，不能作为泛型参数，因此我们使用对应的包装类。借助自动装箱/拆箱机制，这种转换对开发者来说是无感的。

---

