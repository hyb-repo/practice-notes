---
description: 函数：可在任意位置复用的对象，可储存一串代码，是一组可执行任务的语句。
---

# Page 2. Functions

{% code title="" overflow="wrap" %}
```python
""" 
函数名可包含字母、数字、下划线，不可由数字开头。 
def fun(): 
    xxxxx dec 
fun1(a,b,c): 
    xxxxx 
""" 
def fun(a): # 定义形参 a 
    b = a*5 print(b) 
    fun("a") # 指定实参 a 输出 aaaaa
若已定义形参的默认值，不传参时默认值生效
使用形参的名字确定参数的值叫关键字参数
def fun2(a=1,b=2):
    print(a*b) 
fun2() # 输出 2 fun2(2,3) 
# 位置参数：按位置顺序确定参数的值，输出 6 
fun2(5) # 只传第一个位置参数，输出 10 
fun2(,7) # 报错，第一个位置参数不能为空 
fun2(b=5,a=7) # 关键字参数：使用参数的名字确定参数的值,输出 35 
fun2(b=7) # 输出 7 ​
# 实参可以是任意类型，但不代表一定可以运行成功。
```
{% endcode %}

<pre class="language-python" data-title="" data-overflow="wrap"><code class="lang-python"><strong># *可以写在任意参数前方
</strong># 一个函数只能有一个有*的参数
​def fun(a, b, *c): 
    print(a) 
    print(b) 
    print(c) 
fun(1,2,3,4,5) 
""" 
输出： 
1 
2 
(3, 4, 5) # 3,4,5 会被保存到一个元组中 
""" ​
# 求不定个数数字之和的函数
def fun(*a): 
    n = 0 
    for i in a: 
    n += i 
    print(n) 
fun(1,2,3,4,5) ​
# *之后的所有参数必须以关键字传参
def fun(*a,b): 
    print(a) 
fun(1,2,3,4,5,b=0) # 不传 b=0 时会报错 ​
# * 形参只可接收位置参数（按顺序传参）
# ** 可以接收关键字参数，必须写在最后一个

</code></pre>

##

##
