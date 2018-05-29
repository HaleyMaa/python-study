### 如何简单理解python中的if \_\_name\_\_ = '\_\_main\_\_'
- 摘要</br>
简单来说，当.py文件直接运行时，if \_\_name\_\_ = '\_\_main\_\_'以下的代码会被执行，当.py文件以模块的形式被导入时，if \_\_name\_\_ = '\_\_main\_\_'以下的代码不被执行。
- 程序入口</br>
对于很多编程语言来讲，程序都需要一个入口，比如C，C++，以及完全面向对象的编程语言Java，C#等。c,c++这些都需要一个main函数作为程序的入口，程序的运行会从main函数开始。</br>
python的程序是动态的逐行解释运行。从脚本的第一行开始运行，没有统一的入口。
-事实说明（用代码来说话）
现在有一个test.py的文件
```py
pi = 3.14


def main():
    print("pi:", pi)


main()
```
执行：
```
('pi:', 3.14)
```
然后再写一个计算圆的面积的代码test2.py，需要用到test.py中的pi值。导入进去
代码如下：
```py
from test import pi


def area(r):
    return pi*(r**2)


def main():
    print("area is :", area(2))


main()
```
此时代码执行结果为：
```
('pi:', 3.14)
('area is :', 12.56)
```
我们修改test.py的代码，加入
```
if __name__ = "__main__"
```
这时候代码变为
```py
pi = 3.14


def main():
    print("pi:", pi)


if __name__ == '__main__':
    main()
```
这时候再运行test2.py，结果为：
```
('area is :', 12.56)
```
- __name__表示当前模块的名字</br>

__name__是内置变量，可用于表示当前模块的名字。
由此我们可知：如果一个.py文件（模块）被直接运行时，则其没有包结构，其__name__值为__main__，即模块名为__main__。

所以，if __name__ == '__main__'的意思是：当.py文件被直接运行时，if __name__ == '__main__'之下的代码块将被运行；当.py文件以模块形式被导入时，if __name__ == '__main__'之下的代码块不被运行。