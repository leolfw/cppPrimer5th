# cppPrimer5th
C++ Primer 第五版答案，个人学习记录使用，欢迎讨论。
## 第一章
### 练习1.1
```cpp
int main(){
	return 0;
} 
```
### 练习1.2
```cpp
int main(){ 
	return -1;
}
```
其中，返回值-1常常作为程序错误的标识。  
在VS2013系统中，编辑生产.exe程序后，只要在cmd窗口中，运行完.exe后，输入 echo %ERRORLEVEL%，就可以查看程序的返回值了。  
不同的程序返回值，有助于我们了解程序运行的不同结果。
### 练习1.3
```cpp
# include <iostream>
using namespace std;

int main(){
	cout << "Hello,World" << endl;
	return 0;
}
```
或者，利用作用域运算符（::）说明使用std标准库中的标准输出流<<。
```cpp
#include <iostream>

int main(){
	std::cout << "Hello,World" << std::endl;
	return 0;
}
```
### 练习1.4
```cpp
#include <iostream>
using namespace std;

int main(){
	cout << "Pls Enter two int nums:";
	int v1 = 0, v2 = 0;
	cin >> v1 >> v2;
	cout << "The sum of "<< v1 <<" and "<< v2 
		 << " is " << v1 + v2 <<endl;
	return 0;
}
```
### 练习1.5
```cpp
#include <iostream>
using namespace std;

int main(){
	cout << "Pls Enter two int nums:";
	int v1 = 0, v2 = 0;
	cin >> v1 >> v2;
	cout << "The sum of "<< v1 <<" and "<< v2 << " is " << v1 + v2 <<endl;
	return 0;
}
```
### 练习1.6
```cpp
std::cout << "The sum of " << v1;
		  << " and " <<v2;
		  << " is " << v1+v2 << std::endl;
```
程序不合法。因为输入运算符（<<）接受两个运算对象：左侧是ostream对象，右侧的运算对象是要打印的值。
### 练习1.7
不正确的嵌套注释的程序
```cpp
#include <iostream>
using namespace std;

int main(){
	/*
	/* This is a test*/
	*/
	cout << "Hello,World" << endl;
	return 0;
}
```
程序编译不通过，显示错误为 error C2059:syntax error:'/'。
### 练习1.8
- 第一个正确。输出：	/*
- 第二个正确。输出：	*/
- 第三个不正确。改为：
```cpp
cout <</*"*/"*/";  
```
输出：	*/
- 第四个正确。输出:/*

### 练习1.9
```cpp
#include <iostream>
using namespace std;

int main(){
	int i = 50, sum = 0;
	while (i <= 100){
		sum += i;
		i++;
	}
	cout << "The sum of 50 to 100 is " << sum << endl;
	return 0;
}
```
### 练习1.10
```cpp
#include <iostream>
using namespace std;

int main(){
	cout << "The nums between 10 to 0 are :" << endl;
	int i = 10;
	while (i >= 0){
		cout << i << endl;
		i--;
	}
	return 0;
}
```
### 练习1.11
```cpp
#include <iostream>
using namespace std;

int main(){

	cout << "Pls Enter 2 nums:";
	int v1 = 0, v2 = 0, i = 0;
	cin >> v1 >> v2;
	cout << "The nums between " << v1 << " and " << v2 << " are :" << endl;
	if (v1 < v2){
		i = v1;
		while (i <= v2){
			cout << i << endl;
			i++;
		}
	}
	else {
		i = v1;
		while (i >= v2){
			cout << i << endl;
			i--;
		}
	}
	return 0;
}
```
### 练习1.12
对[-100,100]之间整数进行相加，sum终值为0。
### 练习1.13  
#### 1.9
```cpp
#include  <iostream>
using namespace std;

int main(){
	int sum = 0;
	for (int i = 50; i <= 100; i++){
		sum += i;
	}
	cout << "The sum of 50 to 100 is " << sum << endl;
	return 0;
}
```
#### 1.10  
```cpp
#include  <iostream>
using namespace std;

int main(){
	cout << "The nums between 10 to 0 are :" << endl;
	for (int i = 10; i >= 0;i--){
		cout << i << endl;
	}
	return 0;
}
```
#### 1.11  
```cpp
#include <iostream>
using namespace std;

int main(){

	cout << "Pls Enter 2 nums:";
	int v1 = 0, v2 = 0, i = 0;
	cin >> v1 >> v2;
	cout << "The nums between " << v1 << " and " << v2 << " are :" << endl;
	if (v1 < v2){
		for (i = v1; i <= v2; i++){
			cout << i << endl;
		}
	}
	else {
		for (i = v1; i >= v2; i--){
			cout << i << endl;
		}
	}
	return 0;
}
```
### 练习1.14
for和while语句可以实现相同的功能。  
在for语句中，循环控制变量的初始化和修改都放在语句头部分，形式较为简洁，适用于循环次数已知的情况。  
在while语句中，循环控制变量的初始化在while之前，循环控制变量修改一般放在循环体中，形式上不如for简洁，适用于循环次数未知的情况。
#### 练习1.15
错误是无穷无尽的，遇到再分析吧。
### 练习1.16
```cpp
#include <iostream>
using namespace std;

int main(){
	cout << "Pls enter nums :" ;
	int i = 0, sum = 0;
	while (cin >> i){
		sum += i;
	}
	cout << "The sum is " << sum << endl;
	return 0;
}
```
其中，判断语句cin>>i表示遇到文件结束符EOF或者无效输入时就会为false。  
EOF在Windows中为Ctrl+Z；Unix和Mac OS中为Ctrl+D；
### 练习1.17
正常输出。
### 练习1.18
自己运行。
### 练习1.19
在1.11答案已经做了相同的处理。
### 练习1.20
```cpp
#include <iostream>
#include "Sales_item.h"
using namespace std;

int main(){
	cout << "The books' details:ISBN,nums of books,price" << endl;
	cout << "eg:101 4 8" << endl;
	cout << "Pls enter:" << endl;
	Sales_item item;
	while (cin >> item){
		cout << item << endl;
	}
	return 0;
}
```
### 练习1.21
```cpp
#include <iostream>
#include "Sales_item.h"
using namespace std;

int main(){
	cout << "The books' details:ISBN,nums of books,price" << endl;
	cout << "eg:101 4 8" << endl;
	cout << "Pls enter two books:" << endl;
	Sales_item item1,item2;
	cin >> item1 >> item2;
	cout << item1+item2 << endl;
	return 0;
}
```
### 练习1.22
```cpp
#include <iostream>
#include "Sales_item.h"
using namespace std;

int main(){
	cout << "The books' details:ISBN,nums of books,price" << endl;
	cout << "eg:101 4 8" << endl;
	cout << "Pls enter books of same ISBN:" << endl;
	Sales_item itemAll,item;
	cin >> itemAll;
	while (cin >> item){
		itemAll += item;
	}
	cout << itemAll << endl;
	return 0;
}
```
![1.22 程序运行结果](https://github.com/leolfw/cppPrimer5th/blob/master/images/1_22.PNG)
### 练习1.23
```cpp
#include <iostream>
#include "Sales_item.h"
using namespace std;

int main(){
	cout << "The books' details:ISBN,nums of books,price" << endl;
	cout << "eg:101 4 8" << endl;
	cout << "Pls enter books of same ISBN:" << endl;
	Sales_item curr_item,item;

	cin >> curr_item;
	int count = 1;

	while (cin >> item){
		if (item.isbn() == curr_item.isbn()){
			count++;
		}
		else{
			cout << curr_item.isbn() << " has " << count << " books" << endl;
			curr_item = item;
			count = 1;
		}
	}
	cout << curr_item.isbn() << " has " << count << " books" << endl;
	return 0;
}
```
### 练习1.24
![1.24 程序运行结果](https://github.com/leolfw/cppPrimer5th/blob/master/images/1_24.PNG)
### 练习1.25
按照书本的程序编译就可以了。