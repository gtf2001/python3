
# 异常

~~~markdown
异常是一个对象

1. 异常的目的
		提高程序的容错性
		容错性太高太低都不好
~~~

- 异常

~~~markdown
1. IndexError   访问数组的时候索引超出范围
2. TypeError    函数调用的时候参数传递类型错误
3. ValueError    输入的值错误 
4. KeyError		字典的 键 没有这个键
5. NameError	没有这个变量名
6. UnicodeError		编码错误
7. TimeoutError  链接超时
8. FileNotFoundError 文件找不到
9. SyntaxError    语法错误
10. AttributeError  属性错误
11. KeyboardInterupt 用户中断执行
~~~

- 常见的异常

~~~markdown
1. TypeError
2. ValueError
...
...
..
~~~

- 异常处理

~~~markdown
1. try-except
		try:
			可能出现异常的代码
		except 异常类型 as 变量:
			处理异常的代码
		
		异常类型：异常的类名
		变量：用于接收异常的具体信息
		流程：
			try结构中如果出现了异常，则执行except中的代码
			
		except中默认可以捕获所有异常
		try-except结构可以嵌套使用
2. try-except-finally
		try:
			可能出现的异常代码
		except 异常类型 as 变量:
			处理异常的代码
		finally:
			无论如何都会执行的代码
		
		finally：一般用于释放资源，或者无论如何都必须执行的代码（持久化）
3. 可以嵌套使用
~~~

## 自定义异常

- raise语句

~~~markdown
主动抛出一个异常
~~~

- 自定义异常

~~~markdown
1. 自己定义一个异常的类
2. 必须直接或者间接的继承一个BaseException
	BaseException是所有的异常的类的父类
3. raise 异常类() 表示创建异常类的实例对象
	括号可以省略，编译器会自动添加小括号，表示创建对象
~~~

~~~python
def func():
    print('start')
    l = [1,2,3,4,5]
    try:
        raise IAmHungry('我已经三天没吃饭了')
    except IAmHungry as reason:
        print(reason)
class IAmHungry(BaseException):
    pass
func()
~~~

- else语句

~~~markdown
1. if-else
	表示执行if判断为False的情况下的代码
2. for-else
	当循环正常结束时执行else，否则不执行
3. while-else
	当循环正常结束时执行else，否则不执行
4. try-except-else/try-except-else-fianlly
	当try中没有出现任何异常，则执行else，否则不执行
	finally必须在最后
~~~










































