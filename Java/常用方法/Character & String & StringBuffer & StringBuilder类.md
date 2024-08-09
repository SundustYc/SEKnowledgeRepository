# Character & String & StringBuffer & StringBuilder类常用方法

![关系图](关系图.png)

## Character

|方法|简介|
|-|-|
|``isLetter()``|是否是一个字母|
|``isDigit()``|是否是一个数字字符|
|``isWhitespace()``|是否是一个空白字符|
|``isUpperCase()``|是否是大写字母|
|``isLowerCase()``|是否是小写字母|
|``toUpperCase()``|指定字母的大写形式|
|``toLowerCase()``|指定字母的小写形式|
|``toString()``|返回字符的字符串形式，其长度为1|

## String

|**方法**|**简介**|
|-|-|
|``char charAt(int index)``|返回指定索引处的 char 值|
|``int compareTo(Object o)``|把这个字符串和另一个对象比较|
|``int compareTo(String anotherString)``|按字典顺序比较两个字符串|
|``int compareToIgnoreCase(String str)``|按字典顺序比较两个字符串，不考虑大小写|
|``String concat(String str)``|将指定字符串连接到此字符串的结尾|
|``boolean contentEquals(StringBuffer sb)``|当且仅当字符串与指定的StringBuffer有相同顺序的字符时候返回真|
|``static String copyValueOf(char[] data)``</br>``static String copyValueOf(char[] data, int offset, int count)``|返回指定数组中表示该字符序列的 String|
|``boolean endsWith(String suffix)``|测试此字符串是否以指定的后缀结束|
|``boolean equals(Object anObject)``|将此字符串与指定的对象比较|
|``boolean equalsIgnoreCase(String anotherString)``|将此 String 与另一个 String 比较，不考虑大小写|
|``byte[] getBytes()``</br>``byte[] getBytes(String charsetName)``|使用平台的默认字符集将此 String 编码为 byte 序列，并将结果存储到一个新的 byte 数组中|
|``void getChars(int srcBegin, int srcEnd, char[] dst, int dstBegin)``|将字符从此字符串复制到目标字符数组|
|``int hashCode()``|返回此字符串的哈希码|
|``int indexOf(int ch)``</br>``int indexOf(int ch, int fromIndex)``</br>``int indexOf(String str)``</br>``int indexOf(String str, int fromIndex)``|返回指定字符/子字符串在此字符串中第一次出现处的索引，从指定的索引开始搜索|
|``String intern()``|返回字符串对象的规范化表示形式|
|``int lastIndexOf(int ch)``</br>``int lastIndexOf(int ch, int fromIndex)``</br>``int lastIndexOf(String str)``</br>``int lastIndexOf(String str, int fromIndex)``|返回指定字符/字符串在此字符串中最后一次出现处的索引，从指定的索引处开始进行反向搜索|
|``int length()``|返回此字符串的长度|
|``boolean matches(String regex)``|告知此字符串是否匹配给定的正则表达式|
|``boolean regionMatches(boolean ignoreCase, int toffset, String other, int ooffset, int len)``</br>``boolean regionMatches(int toffset, String other, int ooffset, int len)``|测试两个字符串区域是否相等|
|``String replace(char oldChar, char newChar)``|返回一个新的字符串，它是通过用 newChar 替换此字符串中出现的所有 oldChar 得到的|
|``String replaceAll(String regex, String replacement)``|使用给定的 replacement 替换此字符串所有匹配给定的正则表达式的子字符串|
|``String replaceFirst(String regex, String replacement)``|使用给定的 replacement 替换此字符串匹配给定的正则表达式的第一个子字符串|
|``String[] split(String regex)``|根据给定正则表达式的匹配拆分此字符串|
|``boolean startsWith(String prefix)``</br>``boolean startsWith(String prefix, int toffset)``|测试此字符串从指定索引开始的子字符串是否以指定的前缀开始|
|``CharSequence subSequence(int beginIndex, int endIndex)``|返回一个新的字符序列，它是此序列的一个子序列|
|``String substring(int beginIndex)``</br>``String substring(int beginIndex, int endIndex)``|返回一个新的字符串，它是此字符串的一个子字符串|
|``char[] toCharArray()``|将此字符串转换为一个新的字符数组|
|``String toLowerCase()``</br>``String toUpperCase()``|使用默认语言环境的规则将此 String 中的所有字符都转换为小/大写|
|``String toLowerCase(Locale locale)``</br>``String toUpperCase(Locale locale)``|使用给定 Locale 的规则将此 String 中的所有字符都转换为小/大写|
|``String toString()``|返回此对象本身|
|``String trim()``|返回字符串的副本，忽略前导空白和尾部空白|
|``static String valueOf(primitive data type x)``|返回给定data type类型x参数的字符串表示形式|
|``contains(CharSequence chars)``|判断是否包含指定的字符序列|
|``isEmpty()``|判断字符串是否为空|

## StringBuffer

|**方法**|**简介**|
|-|-|
|``public StringBuffer append(String s)``|将指定的字符串追加到此字符序列|
|``public StringBuffer reverse()``|将此字符序列用其反转形式取代|
|``public delete(int start, int end)``|移除此序列的子字符串中的字符|
|``public insert(int offset, int i)``|将 int 参数的字符串表示形式插入此序列中|
|``insert(int offset, String str)``|将 str 参数的字符串插入此序列中|
|``replace(int start, int end, String str)``|使用给定 String 中的字符替换此序列的子字符串中的字符|
|``int capacity()``|返回当前容量|
|``char charAt(int index)``|返回此序列中指定索引处的 char 值|
|``void ensureCapacity(int minimumCapacity)``|确保容量至少等于指定的最小值|
|``void getChars(int srcBegin, int srcEnd, char[] dst, int dstBegin)``|将字符从此序列复制到目标字符数组 dst|
|``int indexOf(String str)``</br>``int indexOf(String str, int fromIndex)``|从指定的索引处开始，返回第一次出现的指定子字符串在该字符串中的索引|
|``int lastIndexOf(String str)``</br>``int lastIndexOf(String str, int fromIndex)``|从索引处逆向搜索字符串，返回指定子字符串最后（早）出现的位置|
|``int length()``|返回长度（字符数）|
|``void setCharAt(int index, char ch)``|将给定索引处的字符设置为 ch|
|``void setLength(int newLength)``|设置字符序列的长度|
|``CharSequence subSequence(int start, int end)``|返回一个新的字符序列，该字符序列是此序列的子序列|
|``String substring(int start)``</br>``String substring(int start, int end)``|返回一个新的 String，它包含此序列当前所包含的字符子序列|
|``String toString()``|返回此序列中数据的字符串表示形式|
