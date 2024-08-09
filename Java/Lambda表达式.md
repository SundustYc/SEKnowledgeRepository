# Lambda表达式

Java中的Lambda表达式使用了一种称为方法引用或方法句柄的方法。在运行时，Lambda表达式被转换为一个invokedynamic指令，这个指令会指向一个由Java虚拟机生成的内部类。这种机制减少了生成匿名类的开销，提高了运行效率。

语法糖

## 语法

(parameters) -> expression

(parameters) -> { statements; }

- **parameters**：指代传递给Lambda表达式的参数。
- **->**：Lambda操作符，分隔参数和Lambda主体。
- **expression** 或 **statements**：Lambda主体，包含执行的逻辑，可以是一个简单表达式或一个代码块。

Lambda表达式只能用于函数式接口（Functional Interface）。函数式接口是仅包含一个抽象方法的接口。Java 8引入了@FunctionalInterface注解，用于标注函数式接口。

### 常用的函数式接口

- java.util.function.Predicate<T>：用于判断条件。
- java.util.function.Consumer<T>：用于执行操作。
- java.util.function.Function<T, R>：用于转换操作。
- java.util.function.Supplier<T>：用于提供对象。

#### Predicate

```java
public class PredicateExample {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("Charlie", "Alice", "Bob", "David");

        // 定义一个Predicate
        Predicate<String> predicate = name -> name.startsWith("A");

        // 过滤以"A"开头的名字
        names.stream()
             .filter(predicate)
             .forEach(System.out::println);
    }
}
```

#### Consumer

```java
public class ConsumerExample {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("Charlie", "Alice", "Bob", "David");

        // 定义一个Consumer
        Consumer<String> consumer = name -> System.out.println("Hello, " + name);

        // 对每个名字执行操作
        names.forEach(consumer);
    }
}
```

#### function

```java
public class FunctionExample {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("Charlie", "Alice", "Bob", "David");

        // 定义一个Function
        Function<String, Integer> function = s -> s.length();
        // 方法引用 Function<String, Integer> function = String::length;
        // 将每个名字转换为其长度
        List<Integer> nameLengths = names.stream()
                                         .map(function)
                                         .collect(Collectors.toList());

        nameLengths.forEach(System.out::println);
    }
}
```

## 示例

### 实现函数式接口

```java
@FunctionalInterface
interface MyFunctionalInterface {
    void myMethod();
}

public class LambdaExample {
    public static void main(String[] args) {
        MyFunctionalInterface myFunc = () -> System.out.println("Hello, Lambda!");
        myFunc.myMethod();
    }
}
```

### 排序集合

```java
import java.util.Arrays;
import java.util.List;

public class LambdaSortExample {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("Charlie", "Alice", "Bob");
        // 使用Lambda表达式按字母顺序排序
        names.sort((a, b) -> a.compareTo(b));
        System.out.println("按字母顺序排序:");
        names.forEach(System.out::println);
        // 使用方法引用简化Lambda表达式
        names.sort(String::compareTo);
        System.out.println("按字母顺序排序（使用方法引用）:");
        names.forEach(System.out::println);
    }
}
```

### 过滤和映射

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class LambdaStreamExample {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("Charlie", "Alice", "Bob", "David");

        // 过滤名字长度大于3的名字
        List<String> filteredNames = names.stream()
                                          .filter(name -> name.length() > 3)
                                          .collect(Collectors.toList());

        System.out.println("过滤名字长度大于3的名字:");
        filteredNames.forEach(System.out::println);

        // 将所有名字转换为大写
        List<String> upperCaseNames = names.stream()
                                           .map(name -> name.toUpperCase())
                                           .collect(Collectors.toList());
        System.out.println("将所有名字转换为大写:");
        upperCaseNames.forEach(System.out::println);
    }
}
```
