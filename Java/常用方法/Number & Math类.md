# Number & Math类常用方法

## Number类常用方法

Java 的 `Number` 是一个抽象类，`Integer`、`Long`、`Double` 等都是它的子类。以下是一些常用的方法：

### 1. xxxValue() 方法

将 Number 对象转换为xxx数据类型的值并返回。

```java
Integer x = 5;
System.out.println(x.byteValue());   // 5
System.out.println(x.shortValue());  // 5
System.out.println(x.intValue());    // 5
System.out.println(x.longValue());   // 5
System.out.println(x.floatValue());  // 5.0
System.out.println(x.doubleValue()); // 5.0
```

### 2. compareTo() 方法

比较两个Number对象的大小。

```java
Integer x = 5;
System.out.println(x.compareTo(3));  // 1  (x > 3)
System.out.println(x.compareTo(5));  // 0  (x == 5)
System.out.println(x.compareTo(8));  // -1 (x < 8)
```

### 3. equals() 方法

判断Number对象是否与参数相等。

```java
Integer x = 5;
Integer y = 5;
Integer z = 6;
System.out.println(x.equals(y));  // true
System.out.println(x.equals(z));  // false
```

### 4. valueOf() 方法

返回一个原生数据类型或String参数构造的Number对象。

```java
Integer x = Integer.valueOf(9);
Double y = Double.valueOf(5.0);
Float z = Float.valueOf("80");    // String参数
```

### 5. toString() 方法

以字符串形式返回值。

```java
Integer x = 5;
System.out.println(x.toString());  // "5"
```

### 6. parseInt() / parseFloat() 等方法

将字符串解析为相应的基本类型。

```java
int i = Integer.parseInt("123");
float f = Float.parseFloat("123.45");
```

## Math 类常用方法

`Math` 类包含执行基本数字运算的方法，如初等指数、对数、平方根和三角函数等。

### 1. 绝对值

```java
System.out.println(Math.abs(-10.4));  // 10.4
System.out.println(Math.abs(10.4));   // 10.4
```

### 2. 向上取整和向下取整

```java
System.out.println(Math.ceil(10.1));   // 11.0
System.out.println(Math.floor(10.7));  // 10.0
```

### 3. 四舍五入

```java
System.out.println(Math.round(10.4));  // 10
System.out.println(Math.round(10.5));  // 11
```

### 4. 最大值和最小值

```java
System.out.println(Math.max(12, 15));  // 15
System.out.println(Math.min(12, 15));  // 12
```

### 5. 幂运算

```java
System.out.println(Math.pow(2, 3));  // 8.0
```

### 6. 平方根

```java
System.out.println(Math.sqrt(16));  // 4.0
```

### 7. 随机数

```java
System.out.println(Math.random());  // 返回0.0到1.0之间的随机数
```

### 8. 三角函数

```java
System.out.println(Math.sin(Math.PI / 2));  // 1.0
System.out.println(Math.cos(Math.PI));      // -1.0
System.out.println(Math.tan(Math.PI / 4));  // 1.0
```

### 9. 自然对数

```java
System.out.println(Math.log(Math.E));  // 1.0
```

### 10. 常量

```java
System.out.println(Math.PI);   // 3.141592653589793
System.out.println(Math.E  );    // 2.718281828459045
```
