# python3 2022.8.18关于类、类属性、实例属性的区分，__init__、__str__
记住一句话：类是模板，而实例则是根据类创建的对象。
以圆为例，任何圆具有统一的圆周率pi，实例圆具有单独的、特有的周长r。
根据相似特征抽象出圆类，每个圆的半径可以不同，那么半径可以作为圆的《实例属性》；而每个圆的圆周率pi是相同的，那么圆周率pi就可以作为《类属性》，这样就定义出了一个圆类。
# 一、Python类的定义与实例的创建
在Python中，类通过 class 关键字定义，类名通用习惯为首字母大写，Python3中类基本都会继承于object类，语法格式如下，我们创建一个Circle圆类:

    class Circle(object):  # 创建Circle类，Circle为类名
      pass  # 此处可添加属性和方法
注意：我们定义的类都会继承于object类，当然也可以不继承object类；两者区别不大，但没有继承于object类使用多继承时可能会出现问题。

有了Circle类的定义，就可以创建出具体的circle1、circle2等实例，circle1和circle2是个实际的圆。创建实例使用 类名+()，类似函数调用的形式创建。

如下我们创建两个Circle类的实例：

    circle1= Circle()
    circle2= Circle()
# 二、Python类中的实例属性与类属性（重）
类的属性是用来表明这个类是什么的。

类的属性分为实例属性与类属性两种。

  实例属性用于区分不同的实例；
  类属性是每个实例的共有属性。
区别：实例属性每个实例都各自拥有，相互独立；而类属性有且只有一份，是共有的属性。
  class Circle():
    pi = 3.14  #类属性pi，不可更改

    def __init__(self, r):  #方法第一个参数一定是self
        self.r = r   #半径r是实例属性，必须用self

    # def zc(self):   #周长
    #     c=self.pi*self.r

    def __str__(self):
        return "元的半径是:{},类属性pi值是：{}，实例属性是：{}".format(self.r, Circle.pi,self.pi)
        #如果用self.pi就是实例属性，Circle.pi就是类属性
        
  面试喜欢问的问题：创建类时，类方法中的self是什么？
  self 代表类的实例，是通过类创建的实例 (注意，在定义类时这个实例我们还没有创建，它表示的我们使用类时创建的那个实例)
        
实例化此圆类：

  from yuan import Circle

if __name__ == '__main__':
    Circle1 = Circle(2)
    Circle2 = Circle(3)
    Circle1.pi = Circle2.pi = 3.1415926   #此处修改实例化后类属性其实并未成功，py使用同名的pi实例属性覆盖了类属性pi。实例属性优先级高。
    print(Circle1)
    print(Circle2)

输出结果：
  
    元的半径是:2,类属性pi值是：3.14，实例属性是：3.1415926
    元的半径是:3,类属性pi值是：3.14，实例属性是：3.1415926
    
  仔细观察我们通过类创建的实例修改的类属性后，通过其他实例访问类属性他的值还是没有改变。其实是通过实例修改类属性是给实例创建了一个与类属性同名的实例属性而已，实例属性访问优先级比类属性高，所以我们访问时优先访问实例属性，它将屏蔽掉对类属性的访问。
  
原文：https://zhuanlan.zhihu.com/p/30024792













### 常见的魔法函数
## __ init__()
所有类的超类object，有一个默认包含pass的__ init __()实现，这个函数会在对象初始化的时候调用，我们可以选择实现，也可以选择不实现，一般建议是实现的，不实现对象属性就不会被初始化。

__init__() 方法可以包含多个参数，但必须包含一个名为 self 的参数，且必须作为第一个参数。也就是说，类的构造方法最少也要有一个 self 参数，仅包含 self 参数的 __init__() 构造方法，又称为类的默认构造方法。例如，仍以 TheFirstDemo 类为例，添加构造方法的代码如下所示：

         class TheFirstDemo:
        '''这是一个学习Python定义的第一个类'''

        # 构造方法
        def __init__(self):
                print("调用构造方法")

        # 下面定义了一个类属性
        add = 'http://c.biancheng.net'

        # 下面定义了一个say方法
        def say(self, content):
                print(content)


         if __name__ == "__main__":
                result = TheFirstDemo()
输出结果：

         调用构造方法
在创建 result 这个对象时，隐式调用了我们手动创建的 __init__() 构造方法。

不仅如此，在 __init__() 构造方法中，除了 self 参数外，还可以自定义一些参数，参数之间使用逗号“,”进行分割。例如，下面的代码在创建 __init__() 方法时，额外指定了 2 个参数：

    class CLanguage:
        '''这是一个学习Python定义的一个类'''
        def __init__(self,name,add):
            print(name,"的网址为:",add)

    #创建 add 对象，并传递参数给构造函数
    add = CLanguage("C语言中文网","http://c.biancheng.net")
输出结果：

    C语言中文网 的网址为: http://c.biancheng.net
可以看到，虽然构造方法中有 self、name、add 3 个参数，但实际需要传参的仅有 name 和 add，也就是说，self 不需要手动传递参数。

## __ str__()
直接打印对象的实现方法，__ str__是被print函数调用的。打印一个实例化对象时，打印的其实时一个对象的地址。而通过__str__()函数就可以帮助我们打印对象中具体的属性值，或者你想得到的东西。

在Python中调用print()打印实例化对象时会调用__str__()。如果__str__()中有返回值，就会打印其中的返回值。

    class Cat:
        """定义一个猫类"""
 
        def __init__(self, new_name= "汤姆", new_age= 20):
            """在创建完对象之后 会自动调用, 它完成对象的初始化的功能"""
            self.name = new_name
            self.age = new_age  # 它是一个对象中的属性,在对象中存储,即只要这个对象还存在,那么这个变量就可以使用
            # num = 100  # 它是一个局部变量,当这个函数执行完之后,这个变量的空间就没有了,因此其他方法不能使用这个变量
 
        def __str__(self):
            """返回一个对象的描述信息"""
            # print(num)
            return "名字是:%s , 年龄是:%d" % (self.name, self.age)

    #创建了一个对象
    tom = Cat("汤姆", 30)
    print(tom)
输出结果：

    名字是:汤姆 , 年龄是:30
总结：当使用print输出对象的时候，只要自己定义了__str__(self)方法，那么就会打印从在这个方法中return的数据。__str__方法需要返回一个字符串，当做这个对象的描写。



原文：https://www.zhihu.com/question/46973549#:~:text=%E8%BF%99%E9%87%8C%E7%9A%84%20__init__%20%E6%96%B9%E6%B3%95%E6%98%AF%E4%B8%80%E4%B8%AA%E7%89%B9%E6%AE%8A%E7%9A%84%E6%96%B9%E6%B3%95%EF%BC%88init%E6%98%AF%E5%8D%95%E8%AF%8D%E5%88%9D%E5%A7%8B%E5%8C%96initialization%E7%9A%84%E7%9C%81%E7%95%A5%E5%BD%A2%E5%BC%8F%EF%BC%89%EF%BC%8C%E5%9C%A8%E4%BD%BF%E7%94%A8%E7%B1%BB%E5%88%9B%E5%BB%BA%E5%AF%B9%E8%B1%A1%E4%B9%8B%E5%90%8E%E8%A2%AB%E6%89%A7%E8%A1%8C%EF%BC%8C%E7%94%A8%E4%BA%8E%E7%BB%99%E6%96%B0%E5%88%9B%E5%BB%BA%E7%9A%84%E5%AF%B9%E8%B1%A1%E5%88%9D%E5%A7%8B%E5%8C%96%E5%B1%9E%E6%80%A7%E7%94%A8%E3%80%82.%20%E5%88%9D%E5%A7%8B%E5%8C%96%E5%B1%9E%E6%80%A7%E7%9A%84%E8%AF%AD%E5%8F%A5%E5%B0%B1%E6%98%AF%20self.name%20%3D%20name%20%E8%BF%99%E7%A7%8D%E4%BA%86%EF%BC%8C%E8%BF%99%E4%B8%80%E5%8F%A5%E4%B8%8D%E5%A4%AA%E5%A5%BD%E7%90%86%E8%A7%A3%EF%BC%8C%E6%88%91%E4%BB%AC%E6%8A%8A%E5%AE%83%E6%94%B9%E7%BC%96%E4%B8%80%E4%B8%8B%E5%B0%B1%E5%A5%BD%E7%90%86%E8%A7%A3%E4%BA%86%EF%BC%9A.,%20self.name%20%3D%20n%20%20self.age%20%3D%20a.
