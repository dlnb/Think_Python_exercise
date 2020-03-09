# 第二章：变量、表达式和语句
## 习题 2-1
  >和上一章一样，我还是要建议大家在学习新特性之后，在交互模式下充分试验，故意犯一些错误，看看到底会出什么问题。

* 我们已经知道 n = 42 是合法的。那么 42 = n 呢？  
* x = y = 1 又合法吗？  
* 在某些编程语言中，每个语句都是以分号 ； 结束的。如果你在一个Python语句后也以分号结尾，会发生什么？  
* 如果在语句最后带上句号呢？  
* 在数学记法中，你可以将 x 和 y 像这样相乘：xy。如果你在Python中也这么写的话，会发生什么？  

## 习题2—2
  >继续练习将Python解释器当做计算器使用：
1. 半径为r的球体积是 $\frac{4}{3}\pi r^3$。 半径为5的球体积是多少？

2. 假设一本书的零售价是$24.95，但书店有40%的折扣。运费则是第一本$3，以后每本75美分。 购买60本的总价是多少？

3. 如果我上午6:52离开家， 以放松跑（easy pace）的速度跑1英里（每英里8:15，即每英里耗时8分15秒），再以 节奏跑（tempo）的速度跑3英里（每英里7:12，即每英里耗时7分12秒)，之后又以放松跑的速度跑1英里，我什么时候回到家吃早饭？
   >译者注：配速（pace）是在马拉松运动的训练中常使用的一个概念，配速是速度的一种，是每公里所需要的时间。配速=时间/距离。Tempo run一般被翻译成「节奏跑」或「乳酸门槛跑」，是指以比10K或5K比赛速度稍慢（每公里大约慢10-15秒）的速度进行训练，或者以平时15K-半程的配速来跑。参考：https://www.zhihu.com/question/22237002

___
## 答案
 [by dlnb526]
### 习题2—1
```
我们已经知道 n = 42 是合法的。那么 42 = n 呢？  
```
* 不可以反向赋值，不然会报错哦！`SyntaxError: can't assign to literal`
```
x = y = 1 又合法吗？
```
* 当然合法！ 

```
在某些编程语言中，每个语句都是以分号 ； 结束的。如果你在一个Python语句后也以分号结尾，会发生什么？ 
```
 * 在编译时不会报错
  
```
如果在语句最后带上句号呢？
```
* 那就肯定报错啦！`SyntaxError: invalid syntax`
  
```
在数学记法中，你可以将 x 和 y 像这样相乘：xy。如果你在Python中也这么写的话，会发生什么？ 
```
* 他会将"xy"整体看作是一个变量！

### 习题2—2

1. 参考代码：
     ```python
    import math
    r = 5
    V = 4/3*math.pi*math.pow(r,3)
    print(V)
   ```
2. 参考代码：
    ```python
    price = 24.95
    discount = 0.4
    first_ex = 3
    ex = 0.75
    num = 60
    Total  = num*price*(1-discount) + (num-1)*ex + ex
    print(Total)
    ```
3. 参考代码：
   ```python
    easytime = 8*60 + 15
    tempotime = 7*60 + 12
    totaltime = easytime*2 + tempotime*3

    min_time = totaltime//60
    sec_time = totaltime - min_time*60

    print(min_time," ",sec_time)
    ```
    得到结果我们可以看出跑步一共用了38分6秒。
    后面如果想要方便的计算时间可以引入time模块，略。

---
> Github:https://github.com/dlnb/Think_Python_exercise  
> 关于我：
>> 博客园：https://www.cnblogs.com/dlnb526/  
>>   
>> FishC:https://fishc.com.cn/space-uid-783916.html