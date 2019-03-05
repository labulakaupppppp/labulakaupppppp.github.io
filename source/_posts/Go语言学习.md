---
title: Go语言学习
date: 2019-03-02 10:58:52
tags: GO
---
GO语言学习，从0开始！
<!-- more-->
### GO安装
#### 下载地址
[GO官网](https://golang.org/dl/)
Windows/macOS/Linux三个版本按需下载。要是链接打不来，ShadowSocks了解一下。
****
### Hello World
先用记事本试一下：
```
package main

import "fmt"

func main(){
	fmt.Println("Hello world!")
}
```
在test.go所在目录下执行
```
go run test.go
```
你的世界你看见！
在上段代码中：
1. 第一行先声明包信息package：每一个源文件非注释第一行都需要指明该文件属于哪个包。每一个GO程序都需要一个名为main的包。
2. import 引入fmt包（fmt包包含了类似于print和scanf的格式化I/O）
3. func main表示函数的开始，每个可执行函数必须含有main函数，在没有init函数的情况下，需要先执行main函数。
4. 注释跟Java一样，//单行注释；/* ....*/多行注释。
5. fmt.Println可以输出引号内的内容，并在后面加一个回车。不加回车为Print。括号内可以填写变量名，以输出变量。
6. 标识符以大写字母开头可以被外部包中的代码使用被称为导出，类似于public；标识符以小写字母开头，对包外不可见，在包内可见切可用类似于protected。
***
### GO 语言基础
#### GO标记
GO标记包括**关键字**，**标识符**，**常量**，**字符串**。

#### 行分割符
GO中每行代表一个语句，如需要写在一行需要在中间加一个";",但不建议这样做。
#### 注释
```
//这是单行注释
/* 这
是
多行注释
*/
```

#### 标识符
标识符可以命名变量、类型等程序实体。
规则包括：
* 由字母或数字组成a-z，A-Z，0-9
* 可包含下划线_
* 第一个字符不能是数字可以使字母或者下划线
标识符举例：ym_001；_temp;ks123;等
无效字符举例：1aab;for(关键字);a-c(运算符不可作为标识符)

#### 关键字
GO中包含25个关键字
| 关键字 | ha | ha | ha | ha |
| ------ | ------- | ------ | ------ | ------ |
| break | default | func | interface | select |
| case | defer | go | map | struct |
| chan | else | goto | package | switch |
| const | fallthrough | if | range | type |
| continue | for | import | return | var |
> 关键字 [defer](https://studygolang.com/articles/16859) 用于注册延迟调用。这些调用直到 ret 前才被执行，通常用于释放资源或错误处理。
> 在Go语言中,[channel](https://studygolang.com/articles/05075)即指通道类型。有时也用它来直接指代可以传递某种类型的值的通道。
> fallthrough：在switch中一个case后面加入fallthrough可以强制执行后面的case

Go语言还有36个预定义标识符
| 预定义标识符 | 1 | 2 | 3 | 4 | 5 |
|---- | ---- | ---- | ---- | ---- | ---- | 
| append | bool | byte | cap | close | complex | complex64 | cmplex 128  |uint 16|
| copy | false | float32 | float64 | imag | int | int8 | int16 | int32 |
| int32 | int64 | iota | len | make | new | nil | panic |uint64 |
| print | println | real | recover |string | true | uint | uint8 | uintptr |

#### Go语言的空格
GO语言中加入空格可增加可读性，如下：
```
num=a+b;
num = a + b;
```
*****
### Go语言的数据类型
数据类型用于声明函数与变量；Go语言中包括类型如下：
* 布尔型：true false。例如 var b bool = true
* 数字类型：
    1. 整型 int
    2. 浮点型 float32 float64
    3. 复数
* 字符串类型（字节使用UTF-8编码表示Unicode文本）
* 派生类型
    1. 指针类型（Pointer)
    2. 数组类型
    3. 结构化类型（struct）
    4. Channel类型
    5. 函数类型
    6. 切片类型
    7. 接口类型（interface）
    8. Map类型
    
#### 数字类型
整型
1. uint8 无符号8位整型（0-255）
2. uint16 无符号16位整型（0-65535）
3. uint32 无符号32位整型（0-4294967295）
4. uint64 无符号64位整型（0-18446744073709551615；2de64次方减一）
5. int8 有符号（-128~127）
6. int16 有符号 16 位整型 (-32768 到 32767)
7. int32 有符号 32 位整型 (-2147483648 到 2147483647)
8. int64  有符号 64 位整型 (-9223372036854775808 到 9223372036854775807)

浮点型：
1. float32  IEEE-754 32位浮点型数
2. float64 IEEE-754 64位浮点型数
3. complex64 32 位实数和虚数
4. complex128 64 位实数和虚数

其他数字类型：
1. byte 类似于uint8
2. rune 类似 int32
3. uint 32 或 64 位
4. int 与 uint 一样大小
5. uintptr 无符号整型，用于存放一个指针
***** 

### Go语言变量
Go中声明变量一般形式如下：
```
var indentifier type
```

#### 变量声明
* 指定变量类型，声明后若不赋值，使用默认值
    ```
    var v_name v_type
    v_name = value
    //var a int =10
    ```
* 根据值制动判断变量类型
    ```
    var v_name = value
    //var b = 10
    ```
* 省略var ：=左侧使用未声明过的变量（这种类型只能在函数体内使用）。
    ```
    v_name ：= value
    //c := 10
    ```
    在相同的代码块中不可以多次使用:=，因为:=左侧变量字在第一次使用的时候就被初始化了。
在一段代码块中声明了某局部变量，就需要在相同代码块中使用它，否则会出现a declared and not used的错误。
但是全局变量允许声明后不使用；

#### 多变量声明
多变量与单变量类似，也是三种方式
    ```
    //方式一
    var vname1, vname2, vname3 type
    vname1,vname2,vname3 = v1, v2, v3
    //方式二
    var name1, name2, name3 = v1,v2,v3
    //方式三
    vvname1, vvname2, vvname3 := v1,v2,v3
    ```
此外可以看出，多变量允许在一行进行赋值

#### 值类型与引用类型
所有像 int、float、bool 和 string 这些基本类型都属于值类型，使用这些类型的变量直接指向存在内存中的值，
当使用等号 = 将一个变量的值赋值给另一个变量时，如：j = i，实际上是在内存中将 i 的值进行了拷贝，
你可以通过 &i 来获取变量 i 的内存地址，例如：0xf840000040（每次的地址都可能不一样）。值类型的变量的值存储在栈中。
 内存地址会根据机器的不同而有所不同，甚至相同的程序在不同的机器上执行后也会有不同的内存地址。因为每台机器可能有不同的存储器布局，并且位置分配也可能不同。
更复杂的数据通常会需要使用多个字，这些数据一般使用引用类型保存。
一个引用类型的变量 r1 存储的是 r1 的值所在的内存地址（数字），或内存地址中第一个字所在的位置。 
这个内存地址为称之为指针，这个指针实际上也被存在另外的某一个字中。
同一个引用类型的指针指向的多个字可以是在连续的内存地址中（内存布局是连续的），这也是计算效率最高的一种存储形式；也可以将这些字分散存放在内存中，每个字都指示了下一个字所在的内存地址。
当使用赋值语句 r2 = r1 时，只有引用（地址）被复制。
如果 r1 的值被改变了，那么这个值的所有引用都会指向被修改后的内容，在这个例子中，r2 也会受到影响。 

#### 简短形式，使用 := 赋值操作符
我们知道可以在变量的初始化时省略变量的类型而由系统自动推断，声明语句写上 var 关键字其实是显得有些多余了，因此我们可以将它们简写为 a := 50 或 b := false。
a 和 b 的类型（int 和 bool）将由编译器自动推断。
这是使用变量的首选形式，但是它只能被用在函数体内，而不可以用于全局变量的声明与赋值。使用操作符 := 可以高效地创建一个新的变量，称之为初始化声明。
使用:= 也可以实现并行赋值，即使变量类型不同，如：
```
a, b, c := 1, 2, "abc"
```
其中 a，b为int型，而c为字符型。
空白标识符 _ 也被用于抛弃值，如值 5 在：_, b = 5, 7 中被抛弃。
_ 实际上是一个只写变量，你不能得到它的值。这样做是因为 Go 语言中你必须使用所有被声明的变量，但有时你并不需要使用从一个函数得到的所有返回值。
并行赋值也被用于当一个函数返回多个返回值时，比如这里的 val 和错误 err 是通过调用 Func1 函数同时得到：val, err = Func1(var1)。 
*****
### 常量
常量是一个简单值的标识符，在程序运行时，不会被修改的量。
常量中的数据类型只可以是布尔型、数字型（整数型、浮点型和复数）和字符串型。
常量的定义格式：
```
const identifier [type] = value
//显式类型定义： 
    const b string = "abc"
//隐式类型定义： 
    const b = "abc"
//多个相同类型的声明可以简写为：
    const c_name1, c_name2 = value1, value2
```
常量还可以用作枚举：
```
const (
    Unknown = 0
    Female = 1
    Male = 2
)
```
数字 0、1 和 2 分别代表未知性别、女性和男性。

常量可以用len(), cap(), unsafe.Sizeof()函数计算表达式的值。常量表达式中，函数必须是内置函数，否则编译不过：
```
package main

import "unsafe"
const (
    a = "abc"
    b = len(a)
    c = unsafe.Sizeof(a)
)

func main(){
    println(a, b, c)
}
//运行结果：abc 3 16
//字符串类型在 go 里是个结构, 包含指向底层数组的指针和长度,这两部分每部分都是 8 个字节，所以字符串类型大小为 16 个字节(不管字符串多长都是16）。
```
#### iota
iota，特殊常量，可以认为是一个可以被编译器修改的常量。（iota 表示从 0 开始自动加 1）
iota 在 const关键字出现时将被重置为 0(const 内部的第一行之前)，const 中每新增一行常量声明将使 iota 计数一次(iota 可理解为 const 语句块中的行索引)。
iota 可以被用作枚举值：
```
const (
    a = iota
    b = iota
    c = iota
)
```
第一个 iota 等于 0，每当 iota 在新的一行被使用时，它的值都会自动加 1；所以 a=0, b=1, c=2 可以简写为如下形式：
```
const (
    a = iota
    b
    c
)
```
iota 用法
```
package main

import "fmt"

func main() {
    const (
            a = iota   //0
            b          //1
            c          //2
            d = "ha"   //独立值，iota += 1
            e          //"ha"   iota += 1
            f = 100    //iota +=1
            g          //100  iota +=1
            h = iota   //7,恢复计数
            i          //8
    )
    fmt.Println(a,b,c,d,e,f,g,h,i)
}
```
以上实例运行结果为：

0 1 2 ha ha 100 100 7 8
再看个有趣的的 iota 实例：
```
package main

import "fmt"
const (
    i=1<<iota  //i=1<<0
    j=3<<iota  //j=3<<1
    k          //k=3<<2
    l          //l=3<<3
)

func main() {
    fmt.Println("i=",i) //i=1：左移 0 位,不变仍为 1;
    fmt.Println("j=",j) //j=3：左移 1 位,变为二进制 110, 即 6;
    fmt.Println("k=",k) //k=3：左移 2 位,变为二进制 1100, 即 12;
    fmt.Println("l=",l) //l=3：左移 3 位,变为二进制 11000,即 24。
}
```
以上实例运行结果为：
i= 1
j= 6
k= 12
l= 24

### 运算符
运算符用于在程序运行时执行数学或逻辑运算。

Go 语言内置的运算符有：
    * 算术运算符 + - * / % ++ --
    * 关系运算符 ==  != > < <= >= 
    * 逻辑运算符 &&(AND)  || (OR)  !(NOT)
    * 位运算符  &  |   ^(异或：不同为1，相同为0） <<(左移 乘以2的n次方）  >>(右移 除以2的n次方）
    * 赋值运算符 =  +=  -= *= /= %= <<= >>= &= ^= |=
    * 其他运算符 &(取地址符） *（指针变量）

指针变量 * 和地址值 & 的区别：指针变量保存的是一个地址值，会分配独立的内存来存储一个整型数字。当变量前面有 * 标识时，才等同于 & 的用法，否则会直接输出一个整型数字。
```
func main() {
   var a int = 4
   var ptr *int
   ptr = &a
   println("a的值为", a);    // 4
   println("*ptr为", *ptr);  // 4
   println("ptr为", ptr);    // 824633794744
}
```
*****
### 条件语句
* if
* if...else
* if嵌套语句
* switch （case fallthrough break）
* select:	select 语句类似于 switch 语句，但是select会随机执行一个可运行的case。如果没有case可运行，它将阻塞，直到有case可运行。
*****
### 循环语句
* for
* 循环嵌套
循环控制语句包括：break continue goto
```
goto label;
..
.
label: statement;
```
*****
### 函数
至少有一个main函数
#### 函数定义

```
func function_name( [parameter list] ) [return_types] {
   函数体
}
```
例如：
```
func max(num1, num2 int) int {
   /* 定义局部变量 */
   var result int

   if (num1 > num2) {
      result = num1
   } else {
      result = num2
   }
   return result 
}
```
#### 函数调用
当创建函数时，你定义了函数需要做什么，通过调用该函数来执行指定任务。
调用函数，向函数传递参数，并返回值
#### 函数有多个返回值
```
func swap(x, y string) (string, string) {
   return y, x
}
```
函数调用时，需两个变量保存函数返回值
```
a,b := swap("Tom","Jack")
```
#### 函数参数
函数若使用参数，该变量就是函数的形参，形参就像定义在函数体内的局部变量
调用函数，可以通过两种方式：
* 值传递：值传递是指在调用函数时将实际参数复制一份传递到函数中，这样在函数中如果对参数进行修改，将不会影响到实际参数。
* 引用传递 ：引用传递是指在调用函数时将实际参数的地址传递到函数中，那么在函数中对参数所进行的修改，将影响到实际参数。
Go语言默认值传递

#### 函数用法
* 函数作为值：函数定义后可作为值来使用
```
package main

import (
   "fmt"
   "math"
)

func main(){
   /* 声明函数变量 */
   getSquareRoot := func(x float64) float64 {
      return math.Sqrt(x)
   }

   /* 使用函数 */
   fmt.Println(getSquareRoot(9))

}
```
* 闭包：闭包是匿名函数，可在动态编程中使用
```
package main

import "fmt"

func getSequence() func() int {
   i:=0
   return func() int {
      i+=1
     return i  
   }
}

func main(){
   /* nextNumber 为一个函数，函数 i 为 0 */
   nextNumber := getSequence()  

   /* 调用 nextNumber 函数，i 变量自增 1 并返回 */
   fmt.Println(nextNumber())
   fmt.Println(nextNumber())
   fmt.Println(nextNumber())
   
   /* 创建新的函数 nextNumber1，并查看结果 */
   nextNumber1 := getSequence()  
   fmt.Println(nextNumber1())
   fmt.Println(nextNumber1())
}
```
以上代码执行结果为：
```
1
2
3
1
2
```
* 方法:方法就是一个包含了接受者的函数
*****
### Go语言变量作用域
作用域表示已经声明的标识符所代表的常量、类型、变量、函数或包在源代码中的作用范围。
Go语言中变量声明的三个位置为：
* 函数内定义的变量为**局部变量**
* 函数外定义的变量为**全局变量**
* 函数定义中的变量称为**形式参数**

#### 局部变量
函数内声明，作用域在函数体内，参数与返回值也是局部变量。
```
package main
import "fmt"
func main(){
//声明局部变量
var a, b, int
//初始化参数
a = 10
b = 20
fmt.Println("a = %d, b = %d",a, b)
}
```

#### 全局变量
在函数体外声明，可以在整个包内被使用，当包被导出后也可以被外部包使用。全局变量可以被任何函数使用。
```go
package main
import "fmt"
//声明全局变量
var g int
func main(){
//声明局部变量
var a, b, int
//初始化参数
a = 10
b = 20
g = a + b
fmt.Printf("结果： a = %d, b = %d and g = %d\n", a, b, g)
}
```
全局变量可以与局部变量有相同的名称，但是局部变量会被优先考虑。
```
package main
import "fmt"
//全局变量
var g int = 20
func main(){
		//局部变量
		var g int = 10
		fmt.Print("g = %d\n", g)
}
//上述代码的输出为 g = 10
```
#### 形式参数
形式参数会作为函数的局部变量来使用
```
package main
import "fmt"
//全局变量
var a int = 20
func main() {
   /* main 函数中声明局部变量 */
   var a int = 10
   var b int = 20
   var c int = 0

   fmt.Printf("main()函数中 a = %d\n",  a);
   c = sum( a, b);
   fmt.Printf("main()函数中 c = %d\n",  c);
}

/* 函数定义-两数相加 */
func sum(a, b int) int {
   fmt.Printf("sum() 函数中 a = %d\n",  a);
   fmt.Printf("sum() 函数中 b = %d\n",  b);

   return a + b;
}
```
#### 初始化局部变量与全局变量
| 数据类型 | 初始化默认值 |
| ----- | ----- |
| int | 0 |
| float32 | 0 |
| pointer | nil |
***** 
### 数组
Go语言提供了数组类型的数据结构
数组是具有相同唯一类型的一组已编号且长度固定的数据项序列，这种类型可以是任意的原始类型如*整型*、*字符串*、*自定义类型*。


| 名称 | 英文全称 | 缩写 | 名称 | 英文全称 | 缩写 |
| ----- | ----- | ----- | ----- | ----- | ----- |
| 丙氨酸 |	Alanine |	A/Ala |	亮氨酸	| Leucine | L/Leu |
| 精氨酸 | Arginine |	R/Arg | 赖氨酸 | Lysine |  	K/Lys | 
| 天冬酰胺 | Asparagine | N/Asn | 	蛋氨酸	 | Methionine | 	M/Met | 
| 天冬氨酸 | Aspartic acid | D/Asp	 | 苯丙氨酸	 | Phenylalanine	 | F/Phe | 
| 半胱氨酸 | Cysteine | C/Cys | 	脯氨酸 | 	Proline | 	P/Pro | 
| 谷氨酰胺 | Glutamine	 | Q/Gln	 | 丝氨酸	 | Serine	 | S/Ser | 
| 谷氨酸 | Glutamic acid | 	E/Glu | 	苏氨酸 | 	Threonine | 	T/Thr | 
| 甘氨酸 | Glycine	 | G/Gly	 | 色氨酸	 | Tryptophan | 	W/Trp | 
| 组氨酸 | Histidine | 	H/His	 | 酪氨酸 | 	Tyrosine | 	Y/Tyr | 
| 异亮氨酸 | Isoleucine	 | I/Ile | 	缬氨酸 | 	Valine | 	V/Val | 
