---
title: js常用方法整理
date: 2017-06-27 08:57:01
tags: [JavaScript]
---

# Array对象方法
## concat()
`连接两个或更多的数组，并返回结果,不改变现有数组`

```
arrayObject.concat(arrX,arrX,...,arrX)
//参数arrX,可为具体值或者数组对象
var arr = [1,2,3]
var arrX = [6,7,8]
arr.concat(4,arrX); //1,2,3,4,5,6,7,8
```

## join()
`将数组中的所有元素通过指定分隔符分隔后放入一个字符串中`

```
arrayObject.join(separator)
//参数separator，可选，未设置该参数默认使用逗号分隔符
var arr = ['A','B','C']
arr.join(); // A,B,C
```

## pop()
`删除并返回数组最后一个元素，**会改变原数组**`

```
arrObject.pop()
var arr = ['A','B','C']
arr.pop(); // C
```

## push()
`向数组末尾添加一个或多个元素，并返回新长度，**会改变原数组**`

```
arrayObject.push(el1,el2,...eln)
var arr = ['A','B','C']
arr.push('D'); //4
```

## shift()
`将数组中的第一个元素删除，并返回该值,**会改变原数组**`

```
arrayObject.shift();
var arr = ['A','B','C'];
arr.shift();// A
```

## unshift()
`向数组开头添加一个或多个元素，并返回新长度,**会改变原数组**`

```
arrayObject.unshift(el1,el2,...eln)
var arr = ['A','B','C']
arr.unshift('D'); //4
arr //['D','A','B','C']
```

## reverse()
`用于颠倒数组中元素的顺序，**会改变原数组**`

```
arrayObject.reverse();
var arr = ['A','B','C'];
arr.reverse();// ["C", "B", "A"]
```

## shift()
`将数组中的第一个元素删除，并返回该值,**会改变原数组**`

```
arrayObject.shift();
var arr = ['A','B','C'];
arr.shift();// A
```

## slice()
`从已有数组中返回指定元素，不会修改原数组`

```
arrayObject.slice(start,end)
// start:必填参数，设置起始选取位置，若为负数则从尾部计起，-1指最后一个元素
// end:可选参数，设置截取结束位置（结束处的数组下标），若未指定，则默认至数组结尾
[1,2,3,4,5,6,7,8,9].slice(1,-1); //[2,3,4,5,6,7,8]
```

## splice()
`数组中添加或删除元素，并返回被删除元素，**会修改原数组**`

```
arrayObject.splice(index,howmany,item1,...,itemN);
index:必填参数，整数，设置添加/删除位置，可使用负数（由右至左）
howmany:可选参数，需要删除的数量，若为0，则不删除，若未设置，则删除index后的所有元素
itemN:可选参数，向数组中添加的新元素
返回值：返回被删除元素的数组，若无，则返回空数组
```

## sort()
`对数组元素进行排序`
```
arrayObject.sort(sortby);
sortby:可选参数，设置排序规则，函数类型，未填参数默认字符编码顺序进行排序
```

## toString()
`返回一个字符串`

```
var arr = [1,2,'A'];
arr.toString();// "1,2,A"
```

## toLocaleString()
`数组中的元素使用各自的toLocaleString方法转成字符串`

# String方法

## charAt()
`从一个字符串中返回指定的字符`

```
str.charAt(index)
// index介于0~length-1，若未设置，则默认是0
```

## concat()
`将一个或者多个字符串与原字符串连接合并，返回新的字符串，多使用赋值操作代替concat（+，+=）`

## endsWith() ES6
`判断当前字符串是否是否以另外一个给定的字符串结尾，返回boolean指`

```
str.endsWith(serchString,position)
// searchString:需要匹配的字符串
// position:可选，匹配字符的结束位置，默认为str.length

var str = "Hello World,hello javascript."
str.endsWith("javascript."); //true
str.endsWith("hello"); //false
str.endsWith("hello",17); // true
```

## includes() ES6
`判断一个字符是否包含在另一个字符串中，返回boolean值`

```
str.includes(searchString,position)
// searchString:需要匹配的字符串
// position:可选，指定当前字符串开始匹配的索引，默认为0，负数无效
// 该方法区分大小写

var str = "Hello World,hello javascript."
str.includes("javascript"); //true
str.endsWith("HELLO"); //false
str.endsWith("Hello",1); //false
```

## indexOf() & lastIndexOf()
### indexOf()
`返回字符串中第一次出现指定值的索引，未找到返回-1`

```
str.indexOf(searchValue,fromIndex)
// searchValue:待查找的值
// fromIndex:可选，表示起始查找位置，默认为0
// 区分大小写
```
### lastIndexOf()
`返回字符串中最后一次指定值的索引，未找到返回-1`

```
str.lastIndexOf(searchValue,fromIndex)
// 参数同indexOf()
```

## match()
`当一个字符串与一个正则表达式匹配时，match()方法检索匹配项`

```
str.match(regexp);
// 返回array
```

## repeat() ES6
`构造并返回一个新字符串，该字符串包含被连接在一起的指定数量的字符串副本`

```
str.repeat(count);//count为0到正无穷之间的整数

'abc'.repeat(2); //abcabc
'abc'.repeat(1+1); //abcabc
'abc'.repeat(3.9); //abcabc
```
## replace() 
`由一个替换值替换一些或所有匹配的模式，模式为字符串或者正则表达式`

```
str.replace(regexp|substr, newSubStr|function)
```

## search()
`执行正则表达式和string对象之间的匹配`

```
str.search(regexp)
// 返回正则表达式再字符串中首次匹配项的索引，若无，返回-1
```

## slice() & substr() & substring()
`提取字符串的一部分,并返回一个新的字符串`

```
str.slice(start, end);
/***********************slice()说明******************************/
/*  start <= 新字符串 < end                                     
/*  start:以0为基数，若为负值，则length + start                  
/*  end:以0为基数，若为负值，则length + start,若省略则到字符串结尾
/***************************************************************/

str.substr(start, length);
/***********************substr()说明*****************************/
/*  start:以0为基数，若为负值,则从末尾开始字符索引                 
/*  length:截取长度，若忽略，则截取到字符串末尾                    
/************************************************************** */

str.substring(start, end);
/***********************substring()说明**************************/
/*  start <= 新字符串 < end                                     
/*  start = end 返回空字符串                                    
/*  未设置end，默认到字符串结尾                                  
/*  任一参数小于0或为NaN,被当作 0                                
/*  任一参数大于length，当作length                               
/*  start > end 自动调换顺序                              
/************************************************************** */
```

## toUpperCase() & toLowerCase() & toLocaleUpperCase() & toLocaleLowerCase()
`大小写转换`

## trim() & trimLeft() & trimRight()
`去除前后多余空格`