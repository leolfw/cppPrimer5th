# cppPrimer5th
C++ Primer 第五版答案，个人学习记录使用，欢迎讨论。
## 第二章
### 练习2.1
short、int、long和long long的区别是尺寸的不同，在C++中规定了其最小值，分别是16位、16位、32位和64位。  
其中，long long是在C++11中新定义的。  
无符号型可以表示正数、负数和0，无符号类型仅能表示大于等于0的值。  
float是单精度，一般16位，7个有效位；double是双精度，一般32位，16个有效位。
### 练习2.2
利率是浮点的，而且数据不大，选用float；  
本金一般是整形的，而且可能超过int的表示范围，所以采用long long；  
付款是本金和利率计算得到的结果，浮点型，采用double；
### 练习2.3
结果如下：
```cpp
32
4294967264
32
-32
0
0
```
其中记住，当不同类型的数值一起运算时，向窄兼容性的数据类型转换，结果也是窄数据类型。  
如，int + unsigned int = unsigned int
### 练习2.4
```cpp
#include <iostream>

int main(){
	unsigned u = 10, u2 = 42;
	std::cout << u2 - u << std::endl;
	std::cout << u - u2 << std::endl;

	int i = 10, i2 = 42;
	std::cout << i2 - i << std::endl;
	std::cout << i - i2 << std::endl;
	std::cout << i - u << std::endl;
	std::cout << u - i << std::endl;
	return 0;
}
```
![2.4 程序运行结果](https://github.com/leolfw/cppPrimer5th/blob/master/images/2_4.png)
### 练习2.5
1. 
'a' 字符字面值
L'a' 宽字符型字面值，类型是wchar_t
"a" 字符串字面值
L"a" 宽字符字符串型字面值，类型是wchar_t
2. 
10 int
10u unsigned int
10L long int 
10uL unsigned long int
012 八进制的12，十进制的10
0xc 十六进制的‘c’，十进制的12
3. 
3.14 double
3.14f float
3.14L long double
4. 
10 int
10u unsigned int
10.=10.0 double
10e-2 10^-2，即0.01
### 练习2.6
```cpp
int month = 9, day = 7;
int month = 09, day = 07;
```
采用字面值对int类型进行初始化，其中'09'和‘07’表示八进制数值。  
'09'编译不成功，八进制中没有数字9。  
'07'和‘7’表示相同数值。
### 练习2.7
1.  "Who goes with F\145rgus?\012"
F\145为八进制的泛化的转义序列，ASC编码的101，即e；  
\012为换行符。  
一般的转义序列有11个，分别是：
\n \v \\ \r \t \b \? \f \a \" \'
其他的使用泛化转义序列，\x+数字表示十六进制，\+数字表示八进制，在Latin-1字符集下，\12就是换行符。
2. 3.14e1L
3.14*10^1 long double
3. 1024L
long int
4. 3.14L
long double
### 练习2.8
```cpp
#include <iostream>
using namespace std;

int main(){
	cout << "\62\115\n";
	return 0;
}
```
![2.8.1 程序运行结果](https://github.com/leolfw/cppPrimer5th/blob/master/images/2_8_1.png)
#include <iostream>
using namespace std;

int main(){
	cout << "\62\t\115\n";
	return 0;
}
![2.8.2 程序运行结果](https://github.com/leolfw/cppPrimer5th/blob/master/images/2_8_2.png)
### 练习2.9
1. std::cin >> int input_value;
输入运算符的右边必须为对象，不能是初始化语句。
2. int i = {3.14};
正确，列表初始化，C++11才有的。
3. double salary = wage = 9999.99;
错误，双重初始化了。
4. int i = 3.14;
正确，会自动进行类型转换。
### 练习2.10
globar_str 空串
global_int 0
local_int 未定义
local_str 空串
函数内的基本类型，在未定义情况下是不确定的；函数外的为0；
字符串未定义就是空串。
### 练习2.11
1. extern int ix = 1024;
定义
2. int iy;
定义
3. extern int iz;
声明
### 练习2.12
1. int double = 3.14;
错误。关键字不能作变量名。
2. int _;
不一定。定义在函数体内时，正确；函数体外时，错误。
3. int catch-22；
错误。只能由字母数字和下划线组成。
4. int 1_or_2 = 1;
错误。不能以数字开头。
5. double Double = 3.14;
正确。
### 练习2.13
```cpp
#include <iostream>
int i = 42;

int main(){
	int i = 100;
	int j = i;
	return 0;
}
```
局部变量覆盖了全局变量，所以i = 100; j = 100;
### 练习 2.14
```cpp
#include <iostream>
int i = 100, sum = 0;

int main(){
	for (int i = 0; i != 10; ++i){
		sum += i;
	}
	std::cout << i << " " << sum << std::endl;
	return 0;
}
```
100 45
局部变量和全局变量的作用域不同。
### 练习2.15
1. int ival = 1.01;
合法。
2. int &rval1 = 1.01;
不合法。引用初始化必须是对象，不能是字面值。
3. int &rval2 = ival;
合法。
4. int &rval3;
不合法。引用必须初始化。
### 练习2.16
```cpp
int i = 0, &r1 = i; 
double d = 0, &r2 = d;
```
1. r2 = 3.14149;
合法。d = 3.14159
2. r2 = r1;
不合法。因为引用本身不是一个对象，所以不能定义引用的引用。
3. i = r2;
合法。将double d的值赋予int i。
4. r1 = d;
合法。将int i的值赋予double i。
### 练习2.17
10 10
### 练习2.18
