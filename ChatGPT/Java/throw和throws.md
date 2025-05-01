**什么是 `throws`，为什么用它，怎么用它**。

---

## **一、`throws` 是干嘛的？**

`throws` 用于 **方法声明中**，表示这个方法 **可能会抛出异常**，它的作用是：

> **把异常“甩锅”给调用者，让调用者负责处理。**

---

## **二、语法格式**

```java
返回类型 方法名(参数列表) throws 异常类型1, 异常类型2, ... {
    // 方法体
}
```

---

## **三、举个例子你就懂了**

```java
public class Example {

    // 声明：这个方法可能会抛出 IOException
    public static void readFile(String filePath) throws IOException {
        FileReader reader = new FileReader(filePath);  // 可能抛出异常
        // 读取内容...
    }

    public static void main(String[] args) {
        try {
            readFile("example.txt");
        } catch (IOException e) {
            System.out.println("处理异常：" + e.getMessage());
        }
    }
}
```

### **说明：**

- `readFile()` 方法里可能会出问题（比如文件不存在）
    
- 它**不处理这个异常**，而是 **用 `throws IOException` 声明“我可能出问题”**
    
- 调用者 `main()` 负责捕获这个异常（`try-catch`）
    

---

## **四、`throw` 和 `throws` 的区别**

|关键字|用途|位置|
|---|---|---|
|`throw`|**实际抛出异常对象**|方法体内|
|`throws`|**声明可能抛出的异常类型**|方法签名部分|

### 示例：

```java
public void test() throws IOException {
    throw new IOException("出错了！");  // 真·抛出异常
}
```

---

## **五、受检异常 vs 非受检异常**

Java 中异常分两类：

|类型|是否必须用 `throws` 或 `try-catch`|常见类名|
|---|---|---|
|**受检异常**|是，必须处理！|IOException, SQLException|
|**非受检异常**|否，可选处理|NullPointerException, IllegalArgumentException|

---

## **六、多个异常一起抛**

```java
public void doSomething() throws IOException, SQLException {
    // 可能同时抛出多个异常
}
```

---

## **七、实际开发中用法场景**

- 调用可能抛异常的库（比如文件操作、数据库连接）
    
- 编写底层 API 时不想自己处理异常，交给上层调用者处理
    
- 分离职责，让异常处理更灵活（例如统一封装日志）
    

---

## **总结一句话：**

> `throws` 是用来**告诉别人“这个方法可能会出错”**，你调用我，就得小心处理，不然编译器就给你红。

---

