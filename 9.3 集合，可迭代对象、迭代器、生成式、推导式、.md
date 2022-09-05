# 集合



set

- 集合的特点

~~~markdown
1. 集合是无序的
2. 集合中的元素必须是可哈希的
		字典中的键是由set实现的
3. 是一个可迭代对象
4. 集合中的所有元素都是唯一的
	不可重复
5. 集合是可变类型
~~~

- 集合的创建

~~~markdown
1. 直接创建
	变量={元素1,元素2,......}
	d={1,2,3}
	无法手动创建空集合
2. 构造方法
	set()：空集合
	set(iterable)：通过可迭代对象来创建集合
~~~

- 集合的访问

~~~markdown
1. 访问一个元素
		不能访问一个元素
2. 访问多个元素
		无法访问多个元素
3. 访问所有元素
		遍历：将容器中的元素，不重复，不遗漏的访问一遍
		for循环
~~~

- 集合的修改

~~~markdown
1. update(set)
	通过一个集合，更新原有的集合
~~~

- 集合的添加

~~~markdown
1. add(value)
	向集合中添加一个元素
~~~

- 集合的删除

~~~markdown
1. remove(value)
	删除某个元素
	如果不存在，则报keyerror
2. pop()
	删除并且返回一个元素
	随机删除
	如果为空则报错：KeyError
3. discard()
	删除某个元素
	如果删除的元素不存在，不报错，并且什么都不做
~~~

- 补充

~~~markdown
去重
~~~

- 交集、并集、补集

~~~markdown
交集：intersection
差集：difference
并集：union
分离集：isdisjoint
对称差集：symmetric_difference
子集：issubset
父集：issuperset
~~~

- 不可变集合

~~~markdown
frozenset：不可变集合
~~~

- 特点

~~~markdown
1. 是一个不可变类型
2. 是一个可迭代对象
3. 是无序的
4. 没有下标的概念
~~~

- 可迭代对象

~~~markdown
list/tuple/str/range/dict/set/frozenset

可变类型：
list/dict/set

不可变类型：
tuple/str/frozenset
~~~

## 可迭代对象

- 容器

~~~markdown
Container
1. 可以存放多个数据
2. 可以存放多种数据
常见的容器：
	list、tuple、dict、set、frozenset、str

容器支持：
		成员关系
		in/not in
没有容器对象，抽象的概念
~~~

- 可迭代对象

~~~markdown
iterable
拥有迭代器的对象称之为可迭代对象
常见的可迭代对象：
	list、tuple、dict、set、frozenset、str
~~~

- 迭代器

~~~markdown
iterator
迭代器是一种特殊的可迭代对象
1. iter():返回一个对象的迭代器
	obj.__iter__()
	
2. next()：将迭代器中的游标向后挪一个单位，并且将划过的元素进行返回,迭代器是自己的迭代器
	obj.__next__()
	
	迭代器中的游标只能够向后移动
3. 只要是实现了__iter__()和__next__()的对象都是迭代器对象
~~~

- 生成器

~~~markdown
generator
生成器也是一种特殊的迭代器
1. 利用生成式创建生成器
		l = (i for i in range(10))
2. 通过yield来创建生成器
		l = ['胡承龙','许晋铭','段朝','孙林娜','王剑']

        def a():
            for i in l:
                yield i
3. 支持遍历
4. 生成器的迭代器是他自己
~~~

# 推导式

~~~markdown
1. 列表推导式
2. 字典推导式
3. 集合推导式

推导式：
	也称之为解析式
	利用逐步解析的方式，创建一个对象
	是python独有的特性
~~~

- 列表推导式

~~~markdown
语法
		变量=[元素 for i in 可迭代对象 if 布尔表达式]
		布尔判断：对数据进行筛选---可以省略
		for循环：给列表提供数据或者提供元素数量
		元素：最终列表中的元素
			固定的值
			变量
			表达式
			函数对象
			函数调用
~~~

- 字典推导式

~~~markdown
语法：
		变量={键:值 for i in 可迭代对象 if 布尔表达式}
~~~

~~~python
# d = {'许晋铭':i for i in range(10)}
# d = {k:v for k,v in [['许晋铭',250],['欢欢','鸡'],['辫儿','250']]}

d1 = dict(许晋铭=250,欢欢=290,辫儿=540)
d2 = {v:k for k,v in d1.items()}
print(d1)
print(d2)
~~~

- 集合推导式

~~~markdown
语法：
	变量={值 for i in 可迭代对象 if 布尔表达式}
	布尔运算：对数据进行筛选---可以省略
	for循环：给列表提供数据、提供元素的数量
	元素：最终列表中的元素
~~~



































