### 关于python的pdb调试
#### <font color=gray size=5> 介绍</font> 
当我们运行程序的时候，不同的语言可以通过相应输出来调试程序。比如：php用ehco或者var_dump()；js中用console.log()；python中可以用print()或者log的方式。当对于相对复杂的程序时，需要引入一种可以进行单步调试以及方便查看变量的方式排查问题，python中的pdb就是用来解决这个问题的。因为本地环境无法测试，所以在测试环境下进行，用pdb调试。本地项目也可以采用编译器（pycharm）调试模式。
#### <font color=gray size=5>常用命令了解</font>

命令|  用途
---|---
break/b | 设置断点
continue/c | 继续执行程序或者跳到下个断点
list/l | 查看当前行的代码段
step/s | 进入函数
return/r | 执行代码直到从当前函数返回
exit/q | 中止并退出
next/n | 执行下一行
p/！ | 打印变量的值，例如p a
help/h | 帮助
#### <font color=gray size=5>项目中使用</font>
先说一点废话，平常也没地儿叨叨自己的工作hhhhh。</br>
刚进入一个项目组，整个项目架构很大，类似于OpenStack，但都是完全自己开发的。尤其对我之前没有做过python项目的新手来说看起来很困难。上班第二天大哥带我熟悉了一遍代码，啥也没记住基本上。后来我就自己慢慢看，发现连入口都找不到。（哭）因为它没有页面展示，客户端是命令行输入命令，服务端是在region同样是命令行显示。有些函数调用有六七层。不过这样可能过段时间对shell更熟练，一定会这样的。</br>
过了两天接手了一个任务，需要优化一个guest请求。开始时候，一整天都在print，跳到一个函数就输出很多东西，然后慢慢看。自己也感觉到效率很低，但没有办法。。。</br>
然后又过了一天，带着问题一个小哥哥，他给我演示了一遍pdb调试。</br>
整个过程下来，两个字，舒爽。</br>
所以自己也想总结一下。</br>
首先，在自己想要调试的代码地方引入pdb代码片段：
```python
import pdb
pdb.set_trace()
```
![image](https://github.com/HaleyMaa/python-study/blob/master/1.png?raw=true)
如图，我在这个地方加了断点。
然后我在客户端去执行group_server_list请求时，在region中就会看到就会调用到这个函数，并进入调试模式。
![image](https://github.com/HaleyMaa/python-study/blob/master/2.png?raw=true)

执行w命令就可以看到调用栈情况:

![image](https://github.com/HaleyMaa/python-study/blob/master/3.png?raw=true)

查看命令执行，依次得到相应结果和变化。
鉴于代码不让上传git，所以具体细节不在描述。
