# Date & SimpleDateFormat & Calendar类常用方法

## Date

|方法|简介|
|-|-|
|``boolean after(Date date)``|若当调用此方法的Date对象在指定日期之后返回true,否则返回false|
|``boolean before(Date date)``|若当调用此方法的Date对象在指定日期之前返回true,否则返回false|
|``Object clone( )``|返回此对象的副本|
|``int compareTo(Date date)``|比较当调用此方法的Date对象和指定日期。两者相等时候返回0。调用对象在指定日期之前则返回负数。调用对象在指定日期之后则返回正数|
|``boolean equals(Object date)``|当调用此方法的Date对象和指定日期相等时候返回true,否则返回false|
|``long getTime( )``|返回自 1970 年 1 月 1 日 00:00:00 GMT 以来此 Date 对象表示的毫秒数|
|``int hashCode( )``|返回此对象的哈希码值|
|``void setTime(long time)``|用自1970年1月1日00:00:00 GMT以后time毫秒数设置时间和日期|
|``String toString( )``|把此 Date 对象转换为以下形式的 String： dow mon dd hh:mm:ss zzz yyyy 其中： dow 是一周中的某一天 (Sun, Mon, Tue, Wed, Thu, Fri, Sat)|

## SimpleDateFormat

```java
public class DateDemo {
   public static void main(String[] args) {
 
      Date dNow = new Date( );
      SimpleDateFormat ft = new SimpleDateFormat ("yyyy-MM-dd hh:mm:ss");
 
      System.out.println("当前时间为: " + ft.format(dNow));
   }
}
```

## Calendar & GregorianCalendar

Calendar类实现了公历日历，GregorianCalendar是Calendar类的一个具体实现。

Calendar 的getInstance（）方法返回一个默认用当前的语言环境和时区初始化的GregorianCalendar对象

## set

public final void set(int year,int month,int date)
public final void set(int field,int value)

```java
Calendar c = Calendar.getInstance();
c.set(2009, 6 - 1, 12); //2009年6月12日
c.set(Calendar.DATE,10);
c.set(Calendar.YEAR,2008);
/**
 * Calendar.YEAR 年份
 * Calendar.MONTH 月份
 * Calendar.DATE 日期
 * Calendar.DAY_OF_MONTH 日期，和上面的字段意义完全相同
 * Calendar.HOUR 12小时制的小时
 * Calendar.HOUR_OF_DAY 24小时制的小时
 * Calendar.MINUTE 分钟
 * Calendar.SECOND 秒
 * Calendar.DAY_OF_WEEK 星期几
 */

```

## add

public final void add(int field,int value)

```java
Calendar c = Calendar.getInstance();
c.add(Calendar.DATE, 10);
c.add(Calendar.DATE, -10);
```

## get

```java
Calendar c = Calendar.getInstance();
// 获得年份
int year = c.get(Calendar.YEAR);
// 获得月份
int month = c.get(Calendar.MONTH) + 1;
// 获得日期
int date = c.get(Calendar.DATE);
// 获得小时
int hour = c.get(Calendar.HOUR_OF_DAY);
// 获得分钟
int minute = c.get(Calendar.MINUTE);
// 获得秒
int second = c.get(Calendar.SECOND);
// 获得星期几（注意（这个与Date类是不同的）：1代表星期日、2代表星期1、3代表星期二，以此类推）
int day = c.get(Calendar.DAY_OF_WEEK);
```

## GregorianCalendar

| **构造函数/方法** | **简介** |
| ---------------- | -------- |
| `GregorianCalendar()` | 在具有默认语言环境的默认时区内使用当前时间构造一个默认的 GregorianCalendar。 |
| `GregorianCalendar(int year, int month, int date)` | 在具有默认语言环境的默认时区内构造一个带有给定日期设置的 GregorianCalendar。 |
| `GregorianCalendar(int year, int month, int date, int hour, int minute)` | 为具有默认语言环境的默认时区构造一个具有给定日期和时间设置的 GregorianCalendar。 |
| `GregorianCalendar(int year, int month, int date, int hour, int minute, int second)` | 为具有默认语言环境的默认时区构造一个具有给定日期和时间设置的 GregorianCalendar。 |
| `GregorianCalendar(Locale aLocale)` | 在具有给定语言环境的默认时区内构造一个基于当前时间的 GregorianCalendar。 |
| `GregorianCalendar(TimeZone zone)` | 在具有默认语言环境的给定时区内构造一个基于当前时间的 GregorianCalendar。 |
| `GregorianCalendar(TimeZone zone, Locale aLocale)` | 在具有给定语言环境的给定时区内构造一个基于当前时间的 GregorianCalendar。 |
| `void add(int field, int amount)` | 根据日历规则，将指定的（有符号的）时间量添加到给定的日历字段中。 |
| `protected void computeFields()` | 转换UTC毫秒值为时间域值。 |
| `protected void computeTime()` | 覆盖Calendar，转换时间域值为UTC毫秒值。 |
| `boolean equals(Object obj)` | 比较此GregorianCalendar与指定的Object。 |
| `int get(int field)` | 获取指定字段的时间值。 |
| `int getActualMaximum(int field)` | 返回当前日期，给定字段的最大值。 |
| `int getActualMinimum(int field)` | 返回当前日期，给定字段的最小值。 |
| `int getGreatestMinimum(int field)` | 返回此GregorianCalendar实例给定日历字段的最高的最小值。 |
| `Date getGregorianChange()` | 获得格里高利历的更改日期。 |
| `int getLeastMaximum(int field)` | 返回此GregorianCalendar实例给定日历字段的最低的最大值。 |
| `int getMaximum(int field)` | 返回此GregorianCalendar实例的给定日历字段的最大值。 |
| `Date getTime()` | 获取日历当前时间。 |
| `long getTimeInMillis()` | 获取用长整型表示的日历的当前时间。 |
| `TimeZone getTimeZone()` | 获取时区。 |
| `int getMinimum(int field)` | 返回给定字段的最小值。 |
| `int hashCode()` | 重写hashCode。 |
| `boolean isLeapYear(int year)` | 确定给定的年份是否为闰年。 |
| `void roll(int field, boolean up)` | 在给定的时间字段上添加或减去（上/下）单个时间单元，不更改更大的字段。 |
| `void set(int field, int value)` | 用给定的值设置时间字段。 |
| `void set(int year, int month, int date)` | 设置年、月、日的值。 |
| `void set(int year, int month, int date, int hour, int minute)` | 设置年、月、日、小时、分钟的值。 |
| `void set(int year, int month, int date, int hour, int minute, int second)` | 设置年、月、日、小时、分钟、秒的值。 |
| `void setGregorianChange(Date date)` | 设置GregorianCalendar的更改日期。 |
| `void setTime(Date date)` | 用给定的日期设置Calendar的当前时间。 |
| `void setTimeInMillis(long millis)` | 用给定的long型毫秒数设置Calendar的当前时间。 |
| `void setTimeZone(TimeZone value)` | 用给定时区值设置当前时区。 |
| `String toString()` | 返回代表日历的字符串。 |
