---
description: 函数：可在任意位置复用的对象，可储存一串代码，是一组可执行任务的语句。
---

# Functions

<pre class="language-python" data-title="定义函数" data-overflow="wrap"><code class="lang-python">""" 
函数名可包含字母、数字、下划线，不可由数字开头。 
可添加参数的说明和函数的说明，只用于说明实际无输入限制。
def fun(a:int，b:bool,c:str='hh一二'): 
    """
    函数说明
    函数说明
    """
    xxxxx dec 
fun1(a,b,c): 
    xxxxx 
""" 
def fun(a): # 定义形参 a 
    b = a*5 print(b) 
    fun("a") # 指定实参 a 输出 aaaaa
    
<strong># 若已定义形参的默认值，不传参时默认值生效
</strong># 使用形参的名字确定参数的值叫关键字参数

def fun2(a=1,b=2):
    print(a*b) 
fun2() # 输出 2 fun2(2,3) 
# 位置参数：按位置顺序确定参数的值，输出 6 
fun2(5) # 只传第一个位置参数，输出 10 
fun2(,7) # 报错，第一个位置参数不能为空 
fun2(b=5,a=7) # 关键字参数：使用参数的名字确定参数的值,输出 35 
fun2(b=7) # 输出 7 ​
# 实参可以是任意类型，但不代表一定可以运行成功。
</code></pre>

<pre class="language-python" data-title="不定长参数" data-overflow="wrap"><code class="lang-python"><strong># *可以写在任意参数前方
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

return后面的代码都不执行

break用来退出当前循环

continue用来跳过单次循环

#### 作用域scope

变量生效的区域，Python 中分为程序运行时生效的全局作用域与仅在函数执行时生效的函数作用域，函数作用域内的变量为局部变量，其他为全局变量。函数有嵌套时从最下层的函数一层层向上找变量。

#### 命名空间namespace

同来存储变量的字典，分为全局命名空间和函数命名空间，生效范围同作用域。

#### 全局空间globals

如果没有定义任何命名空间，所有的类与函数的定义都是在全局空间。

{% code title="递归" overflow="wrap" %}
```
# 求幂
def power(n,i):
    if i == 1:
        return n
    return n * power(n,i-1)
print(power(2,5))

# 回文
a = "abcba"
b = "aisdbcjk"
c = "abdcba"
def palindrome(s):
    if len(s) <2:
        return True
    elif s[0] != s[-1]:
        return False
    return palindrome(s[1:-1])
print(palindrome(a))
print(palindrome(b))
print(palindrome(c))
```
{% endcode %}

