---
description: 基础知识
---

# Basic

## 基础**语法**

#### **标识符**

可理解为"名字"。

* 可由英文字母、下划线、中文汉字以及其他语言文字开头。
* 由文字、数字、下划线组成。
* 区分大小写。
* 不可使用保留字。

建议使用英文字母、数字、下划线的组合。

{% code title="保留字" overflow="wrap" %}
```python
import keyword
print(keyword.kwlist)
"""
输出：
['False', 'None', 'True', '__peg_parser__', 'and', 'as', 'assert', 'async', 'await', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
"""
```
{% endcode %}

#### **注释**

有 3 种注释方式，注释掉的代码不会被执行。

{% code title="注释方式" overflow="wrap" %}
```python
# 要注释的内容1，只支持单行

"""
要注释的内容2，支持多行
要注释的内容2，支持多行
"""

'''
要注释的内容3，支持多行
要注释的内容3，支持多行
'''
```
{% endcode %}

#### **缩进**

同一代码块内需使用相同个数的空格或 tab 进行缩进，否则运行会报错。

<pre class="language-python" data-title="缩进" data-overflow="wrap" data-line-numbers><code class="lang-python"># 3~5 行使用相同缩进，8~9 行使用相同缩进
def un(a,b):
<strong>          n1 = a-b
</strong><strong>          n2 = b-a
</strong><strong>          print(str(n1),"\n",str(n2))
</strong><strong>
</strong><strong>def n(a,b):
</strong><strong> n = a + b
</strong><strong> print(n)
</strong><strong>
</strong><strong>fun(1,2)
</strong>n(1,2)
</code></pre>

#### **输出与输入**

{% code title="input() & print" overflow="wrap" %}
```python
UserKeyword = input("Input A Word: ") # 输入关键字
print(UserKeyword) # 输出关键字，结尾默认换行
print("Done",end = "") # 输出文字，结尾处不加换行
print("Finish")
```
{% endcode %}

## 数据类型

数据类型可根据 value 是否可变区分为可变对象（list、dict、set）与不可变对象（number、str、tuple）

#### **变量与对象的区分**

对象是一个由 id、type、value 组成的数据结构。可以说 Python 中一切皆是对象，而变量是用来引用对象的。改变量时只会影响当前变量，改对象时会影响所有指向该对象的变量。

{% code title="更改变量的值" overflow="wrap" %}
```python
a = [1,2,3] 
b = a 
b = [1,2]
print(a) 
print(b) 

"""
输出：
[1, 2, 3]
[1, 2 ]
"""
```
{% endcode %}

{% code title="更改对象的值" overflow="wrap" %}
```python
a = [1,2,3] 
b = a 
b[0] = 5
print(a) 
print(b) 

"""
输出：
[5, 2, 3]
[5, 2, 3]
"""
```
{% endcode %}

#### Number-数字 <a href="#bcvdj" id="bcvdj"></a>

数字为不可变对象。int、float、bool、complex 均属于数字。bool 有 True 和 False，在字符串、列表、元组中不为零或非空均视为 True，反之则为 False。

{% code overflow="wrap" %}
```python
a = True
b = False
print(id(1)) # 输出 2086197881136
print(id(0)) # 输出 2086197881104
print(id(True)) # 输出 140731585263720
print(id(False)) # 输出 140731585263752
print(id(a)) # 输出 140731585263720
print(id(b)) # 输出 140731585263752
print(id(True+False)) # 输出 2086197881136
```
{% endcode %}

#### String-"字符串" <a href="#avwlo" id="avwlo"></a>

字符串为不可变对象。需要用一对单/双/三引号包起来，文案中还有引号时需使用反斜杠进行转义。支持索引截取。

{% code overflow="wrap" %}
```python
print('''"t'fjj"''') # 输出 "t'fjj"
print("a")  # 输出 a
print('b')  # 输出 b
print('\'s')  # 转义，输出 's
print(r'\'s') # 引号前加 r 表示不转义，输出 \'s
print("123"[1:]) # 支持索引截取，输出 23
```
{% endcode %}

#### List-\[列表] <a href="#jeose" id="jeose"></a>

列表为可变对象。可存储任意对象，可有重复元素，元素可以是不同类型。支持索引截取。

{% code overflow="wrap" %}
```python
a = [1,2,3,4,5]
b = a
b[0] = 5 #
print(a) # 输出 [5, 2, 3, 4, 5]
print(a[0:5:2]) # 输出 [5, 3, 5]
print(a[0::3]) # 输出 [5, 4]
```
{% endcode %}

#### Tuple-(元祖) <a href="#mo5xv" id="mo5xv"></a>

元组为不可变对象。可存储任意对象，可有重复元素，元素可以是不同类型。支持索引截取。

```
tuple_1 = 1,2,3,4
tuple_1[0] = 2
# 执行后显示 TypeError: 'tuple' object does not support item assignment
```

```
# 方法1，单个元素时必须加逗号
tuple_1 = 10,

# 方法2
tuple_2 = 10,20,30

# 方法3
tuple_3 = (10,20,30)
```

```
tuple_1 = 1,2,3,4
a,b,c,d = tuple_1
print(a) # 输出 1
print(b) # 输出 2
print(c) # 输出 3
print(d) # 输出 4
a,b = b,a
print(a) # 输出 2
print(b) # 输出 1
print(tuple) # 输出 (1, 2, 3, 4)
print(tuple[1]) # 输出 2

"""
1.解包时变量的数量需与元素个数一致
2.可在其中一个变量前加*号获取剩余所有元素
3.解包时只能存在一个*号
"""
a,*b,c = tuple_1
print(b) # 输出 [2, 3]
a,b,*c = tuple_1
print(c) # 输出 [3, 4]
```

#### Dict-{字典} <a href="#y8rbn" id="y8rbn"></a>

可变对象，字典属于新的结构，称为映射，是类似列表的储存对象的容器。其中的每一个对象均有一个键(key)与一个值(value)，每一个键值对都是一个项(item)。

```
"""
1.键必须是不可变对象，若出现相同的键会使用最后一次出现的值。
2.值可以是任意对象，也可以是字典 
"""
# 写法1
{key:value,key:value}
# 写法2:
{
key:value,
key:value,
key:value
}
```

```
"""
以下方法输出结果都是 {'name': 'Lilei', 'age': 22}
"""
# 方法1(键必须加引号)
d = {}
d["name"] = "Lilei"
d["age"] = 22
print(d) # 

# 方法2(键可以不加引号)
d = dict(name = "Lilei",age = 22)
print(d) 

# 方法3(将有双值子序列的序列装换为字典)
# - 双值子序列：每个子序列里只有2个值的序列  
d = dict([("name","Lilei"),("age",18)])
print(d) 

# 方法4（和方法1一样）
d =  {"name": "Lilei", "age": 22}
```

```
d = dict([("name","Lilei"),("age",18)])

# 查询字典长度，即键值对个数，输出结果是 2
print(len(d)) 

# 查询字典内是否有指定键
print("name" in d)   # 输出 True
print("name" not in d) # 输出 False

# 获取指定键的值，键的名字必须是实际存在的
print(d["name"]) # 输出 Lilei

# 获取字典中指定键的值
print(d.get("name"))  # 输出 Lilei
print(d.get("name","没有指定键时显示这一句提示"))  # 输出 Lilei
print(d.get("none","没有指定键时显示这一句提示")) # 输出 没有指定键时显示这一句提示
```

```
d =  {"name": "Lilei", "age": 22}
# 键已存在时替换值
d["name"] = "Hanmeimei" 

# 添加新的键值对
d["gender"] = "female"
print(d) # 输出 {'gender': 'female', 'age': 22, 'name': 'Hanmeimei'}

# 字典中不存在指定键时添加新的键值对，若已存在则不做修改
d.setdefault("name","11")
d.setdefault("nation","xxx")
r = d.setdefault("age","None")
print(d) # 输出 {'gender': 'female', 'age': 22, 'name': 'Hanmeimei', 'nation': 'xxx'}
print(r) # 输出 22

# 更新字典
d1 = {"name":"Lilei"}
d2 = {"name":"Hanmeimei","age":22}
d1.update(d2) # 将 d2 加入至 d1，有重复的键时使用 d2 的值
print(d1) # 输出 {'age': 22, 'name': 'Hanmeimei'}
print(d2) # 输出 {'age': 22, 'name': 'Hanmeimei'}
```

```
d =  {"name": "Lilei", "age": 22, "gender":"male"}

# 使用 del d["键"] 删除键值对，删除不存在的键时会抛出异常
del d["name"]
print(d) # 输出 {'age': 22, 'gender': 'male'}

# 使用 popitem 删除最后一个项，若字典为空时会抛出异常
d1 = d.popitem()
print(d) # 输出 {'age': 22}
print(d1) # 输出元组 ('gender', 'male')

# 使用 pop 删除指定项，删除不存在的键时会抛出异常
# 若设置了默认值不会报错
d = {"a":"aaa","b":"bbb","c":"ccc"}
d1 = d.pop("b")
d2 = d.pop("d","默认值")
print(d)  # 输出 {'a': 'aaa', 'c': 'ccc'}
print(d1) # 输出 bbb
print(d2) # 输出 默认值
d3 = d.pop("d") # 抛出异常，找不到键 "d"

# 删除字典的所有项
d =  {"name": "Lilei", "age": 22, "gender":"male"}
d1 = d.clear()
print(d1) # 输出 None
print(d) # 输出 {}
```

```
# 不想改动原对象时可使用 copy 复制一个对象，在原字典和被复制的字典中修改至都不会影响另一个
d =  {"name": "Lilei", "age": 22, "gender":"male"}
d1 = d
d2 = d.copy()
print(id(d)) # 输出 2903309356480
print(id(d1)) # 输出 2903309356480
print(id(d2)) # 输出 2903309362112
d2["name"] = "Hanmeimei"
print(d) # 输出 {'name': 'Lilei', 'age': 22, 'gender': 'male'}
print(d2) # 输出 {'name': 'Hanmeimei', 'age': 22, 'gender': 'male'}
d["gender"] = "female"
print(d) # 输出 {'name': 'Lilei', 'age': 22, 'gender': 'female'}
print(d2) # 输出 {'name': 'Hanmeimei', 'age': 22, 'gender': 'male'}

# 原字典中存在可变对象，此时 d 与 d1 的子字典是同一个 id，更改子字典的值时 d 与 d1 都会被影响
d =  {"a":{"name": "Lilei", "age": 22}, "gender":"male"}
d1 = d.copy()
d1["a"]["age"] = "11"
print(d) # 输出 {'a': {'name': 'Lilei', 'age': '11'}, 'gender': 'male'}
print(d1) # 同上
```

```
d = {"a":"aaa","b":"bbb"}

# keys 返回字典的所有键
print(d.keys()) # 输出 dict_keys(['a', 'b'])

# values 返回字典的所有值
print(d.values()) # 输出 dict_values(['aaa', 'bbb'])

# items 返回字典的所有项
print(d.items()) # 输出 dict_items([('a', 'aaa'), ('b', 'bbb')])

for i in d.keys():
    print(i,"=",d[i])
for o in d.values():
    print(o)
for c in d.items():
    print(c)
for a,b in d.items():
    print(a,"=",b)
```

#### Set{集合} <a href="#hiuwx" id="hiuwx"></a>

```
"""
1.与列表不同，集合只能存储不可变对象
2.集合内的对象有顺序，但其与插入顺序不一致
3.元素需唯一，相同的元素会被合并为一个
"""
# 方法1，此方法不支持创建空集合
s1 = {1,2,3}
s2 = {} # 这其实是一个字典
print(s1)

# 方法2，此方法可用於创建空集合
s3 = set()
print(s3)

d = {"a":"aac","b":"bbb"}
s4 = set(d) 
print(s4) # 将字典转换为集合时只保留字典的键

# 集合不支持索引 s[0]，但支持使用 in/not in 和 len 等进行查询

# 在集合中添加元素
s.add(1)

# 将 s1 的元素添加到 s
s.update(s1)

# 从集合中随机删除并返回元素
s.pop()

# 从集合中删除指定元素 a,a为集合中的一个元素
s.remove(a)

# 清空集合
s.clear（）

# copy 进行浅复制
```

```
s = {1,2,3,4,5}
s2 = {3,4,5,6,7}

# 交集运算，不影响元集合
result = s & s2
print(result) # 输出 {3, 4, 5}

# 并集运算
result=s | s2
print(result) # 输出 {1, 2, 3, 4, 5, 6, 7}

# 差集运算
result=s - s2
print(result) # 输出 {1, 2}

# 异或集，获取只在一个集合中出现的元素
result=s ^ s2
print(result) # 输出 {1, 2, 6, 7}

# 是否包子集，如果两个子集完全相同，他们也互为子集和超集的关系。
a={1,2,3}
b={1,2,3,4,5}

result = a <= b
print(result) # 输出 True

result1 = b <= a
print(result1) # 输出 False

a={1,2,3}
b={1,2,3}
result = a <= b # 输出 True

# 检查一个集合是不是另一个集合的真子集，若 B 集合中有 A 集合所有的元素，且 A 集合是 B 集 合的真子集，则 A 就 是 B 的真子集，B 就是 A 的超子集。

a={1,2,3}
b={1,2,3,4,5}
result = a < b
print(‘result=’，result)
输出结果为 result=TRUE

a={1,2,3}
b={1,2,3}
result = a < b
print(‘result=’，result)

输出结果为 result=FALSE

# >= 检查一个集合是否是另一个集合的超集

# > 检查一个集合是否是另一个集合的真超集
```

运算符\



\


\


\


\
