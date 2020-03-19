# 第三章：函数
---
## 习题 3-1
* 编写一个名为right_justify的函数，函数接受一个名为``'s'``的字符串作为形参， 并在打印足够多的前导空格（leading space）之后打印这个字符串，使得字符串的最后一个字母位于显示屏的第70列。  
    ```python
    >>> right_justify('monty')
    ```
   >提示：使用字符串拼接（string concatenation）和重复。另外，Python提供了一个名叫len的内建函数，可以返回一个字符串的长度，因此`len('allen')`的值是5。

    函数对象是一个可以赋值给变量的值，也可以作为实参传递。例如， `do_twice`函数接受函数对象作为实参，并调用这个函数对象两次：  

    ```python
    def do_twice(f):
    f()
    f()
    ```

    下面这个示例使用`do_twice`来调用名为`print_spam`的函数两次。

    ```python
    def print_spam():
    print('spam')

    do_twice(print_spam)
    ```
    1. 将这个示例写入脚本，并测试。
    2. 修改`do_twice`，使其接受两个实参，一个是函数对象，另一个是值。 然后调用这一函数对象两次，将那个值传递给函数对象作为实参。
    3. 从本章前面一些的示例中，将 `print_twice` 函数的定义复制到脚本中。
    4. 使用修改过的`do_twice`，调用`print_twice`两次，将`'spam'`传递给它作为实参。
    5. 定义一个名为`do_four`的新函数，其接受一个函数对象和一个值作为实参。 调用这个函数对象四次，将那个值作为形参传递给它。 函数体中应该只有两条语句，而不是四条。
    >注意：这一习题只能使用我们目前学过的语句和特性来完成。
## 习题 3-2  

  1. 编写一个能画出如下网格（grid）的函数：
        ```
            + - - - - + - - - - +
            |         |         |
            |         |         |
            |         |         |
            |         |         |
            + - - - - + - - - - +
            |         |         |
            |         |         |
            |         |         |
            |         |         |
            + - - - - + - - - - +
        ```    
        >提示：你可以使用一个用逗号分隔的值序列，在一行中打印出多个值：
        ```python
            print('+', '-')
        ```
        这两个语句的输出结果是 `'+ -'`。

        一个没有传入实参的 `print` 语句会结束当前行，跳到下一行。  

  2. 编写一个能够画出四行四列的类似网格的函数。
---
## 参考答案

### 习题3-1
[本部分直接采用原书代码，翻译：dlnb526](http://greenteapress.com/thinkpython2/code/do_four.py)
```python
def do_twice(func, arg):
    """运行一个函数两次

    func: 传入的函数
    arg: 传入的参数
    """
    func(arg)
    func(arg)


def print_twice(arg):
    """打印参数两次.

    arg: 任何可打印的东西
    """
    print(arg)
    print(arg)


def do_four(func, arg):
    """运行代码四次.

    func: 传入的函数
    arg: 传入函数的参数
    """
    do_twice(func, arg)
    do_twice(func, arg)


do_twice(print, 'spam')
print('')

do_four(print, 'spam')
```
### 习题3-2
[本部分直接采用原书代码，翻译：dlnb526](http://greenteapress.com/thinkpython2/code/grid.py)
```python
# 这是最直接的
# 绘制2*2格子的方式

def do_twice(f):
    f()
    f()

def do_four(f):
    do_twice(f)
    do_twice(f)

def print_beam():
    print('+ - - - -', end=' ')

def print_post():
    print('|        ', end=' ')

def print_beams():
    do_twice(print_beam)
    print('+')

def print_posts():
    do_twice(print_post)
    print('|')

def print_row():
    print_beams()
    do_four(print_posts)

def print_grid():
    do_twice(print_row)
    print_beams()

print_grid()
    

# 这是绘制4*4格子
# 不那么直接的方式

def one_four_one(f, g, h):
    f()
    do_four(g)
    h()

def print_plus():
    print('+', end=' ')

def print_dash():
    print('-', end=' ')

def print_bar():
    print('|', end=' ')

def print_space():
    print(' ', end=' ')

def print_end():
    print()

def nothing():
    "do nothing"

def print1beam():
    one_four_one(nothing, print_dash, print_plus)

def print1post():
    one_four_one(nothing, print_space, print_bar)

def print4beams():
    one_four_one(print_plus, print1beam, print_end)

def print4posts():
    one_four_one(print_bar, print1post, print_end)

def print_row():
    one_four_one(nothing, print4posts, print4beams)

def print_grid():
    one_four_one(print4beams, print_row, nothing)

print_grid()

comment = """

在绘制完4*4格子后，我发现有许多具有相同结构的函数：
他们会完成一件事，完成另外一件事情四次，
再完成另一件事情一次。

因此我写了one_four_one函数，取三个函数作为其参数；这个函数
回调第一个函数一次，然后利用do_four 函数回调第二个函数四次，
最后回调第三个函数。

然后我利用one_four_one重写了print1beam, print1post, 
print4beams, print4posts,print_row 和 print_grid 函数

编程是一个探索性的过程。 编写程序的草稿通常可以使您深入了解问题，
这可能会使您重写代码，反映解决方案的结构。
--- 艾伦
"""

print(comment)
```
---
> Github:https://github.com/dlnb/Think_Python_exercise  
> 关于我：
>> 博客园：https://www.cnblogs.com/dlnb526/  
>>   
>> FishC:https://fishc.com.cn/space-uid-783916.html
 