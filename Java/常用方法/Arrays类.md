# Arrays类常用方法

## public static int binarySearch(Object[] a, Object key)

用二分查找算法在给定数组中搜索给定值的对象(Byte,Int,double等)。数组在调用前必须排序好的。如果查找值包含在数组中，则返回搜索键的索引；否则返回 (-(插入点) - 1)。

## public static boolean equals(long[] a, long[] a2)

如果两个指定的 long 型数组彼此相等，则返回 true。如果两个数组包含相同数量的元素，并且两个数组中的所有相应元素对都是相等的，则认为这两个数组是相等的。换句话说，如果两个数组以相同顺序包含相同的元素，则两个数组是相等的。同样的方法适用于所有的其他基本数据类型（Byte，short，Int等）。

## public static void fill(int[] a, int val)

将指定的 int 值分配给指定 int 型数组指定范围中的每个元素。同样的方法适用于所有的其他基本数据类型（Byte，short，Int等）。

## public static void sort(Object[] a)

对指定对象数组根据其元素的自然顺序进行升序排列。同样的方法适用于所有的其他基本数据类型（Byte，short，Int等）。

## public static <T> void sort(T[] a, Comparator<? super T> c)

比较器版本

```java
import java.util.Arrays;
import java.util.Comparator;

class Person {
    String name;
    int age;

    Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @Override
    public String toString() {
        return name + ": " + age;
    }
}

public class CustomSortExample {
    public static void main(String[] args) {
        Person[] people = {
            new Person("Alice", 30),
            new Person("Bob", 25),
            new Person("Charlie", 35)
        };

        // 按年龄升序排序
        Arrays.sort(people, new Comparator<Person>() {
            @Override
            public int compare(Person p1, Person p2) {
                return Integer.compare(p1.age, p2.age);
            }
        });
        /** 
         * 传入一个匿名内部类实现 Comparator 接口
         * new Comparator<Person>() {
         *      @Override
         *      public int compare(Person p1, Person p2) {
         *          eturn Integer.compare(p1.age, p2.age);
         *      }
         *  }
         */
        System.out.println("按年龄升序排序:");
        for (Person person : people) {
            System.out.println(person);
        }
   }
}

// 也可采用Lambda表达式的形式来实现匿名内部类
Arrays.sort(people, (p1, p2) -> Integer.compare(p1.age, p2.age));
```
