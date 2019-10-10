:
import numpy as np
from scipy.optimize import leastsq
 
###采样点(Xi,Yi)###
Xi=np.array([8.19,2.72,6.39,8.71,4.7,2.66,3.78,11.3])
Yi=np.array([7.01,2.78,6.47,6.71,4.1,4.23,4.05,10.1])
 
###需要拟合的函数func及误差error###
def func(p,x):
    k,b=p
    return k*x+b
 
def error(p,x,y,s):
    print (s)
    return func(p,x)-y #x、y都是列表，故返回值也是个列表
 
###TEST
p0=[100,100]
#print( error(p0,Xi,Yi) )
 
###主函数从此开始###
s="Test the number of iteration" #试验最小二乘法函数leastsq得调用几次error函数才能找到使得均方误差之和最小的k、b
Para=leastsq(error,p0,args=(Xi,Yi,s)) #把error函数中除了p以外的参数打包到args中
k,b=Para[0]
print("k=",k,'\n',"b=",b)
 
###绘图，看拟合效果###
import matplotlib.pyplot as plt
plt.scatter(Xi,Yi,color="red",label="Sample Point",linewidth=3) #画样本点
x=np.linspace(0,10,1000)
y=k*x+b
plt.plot(x,y,color="orange",label="Fitting Line",linewidth=2) #画拟合直线
plt.legend()
plt.show()
:





 2 import numpy as np
 3 from scipy.optimize import leastsq
 4 
 5 ###采样点(Xi,Yi)###
 6 Xi=np.array([0,1,2,3,-1,-2,-3])
 7 Yi=np.array([-1.21,1.9,3.2,10.3,2.2,3.71,8.7])
 8 
 9 ###需要拟合的函数func及误差error###
10 def func(p,x):
11     a,b,c=p
12     return a*x**2+b*x+c
13 
14 def error(p,x,y,s):
15     print s
16     return func(p,x)-y #x、y都是列表，故返回值也是个列表
17 
18 #TEST
19 p0=[5,2,10]
20 #print( error(p0,Xi,Yi) )
21 
22 ###主函数从此开始###
23 s="Test the number of iteration" #试验最小二乘法函数leastsq得调用几次error函数才能找到使得均方误差之和最小的a~c
24 Para=leastsq(error,p0,args=(Xi,Yi,s)) #把error函数中除了p以外的参数打包到args中
25 a,b,c=Para[0]
26 print"a=",a,'\n',"b=",b,"c=",c
27 
28 ###绘图，看拟合效果###
29 import matplotlib.pyplot as plt
30 
31 plt.figure(figsize=(8,6))
32 plt.scatter(Xi,Yi,color="red",label="Sample Point",linewidth=3) #画样本点
33 x=np.linspace(-5,5,1000)
34 y=a*x**2+b*x+c
35 plt.plot(x,y,color="orange",label="Fitting Curve",linewidth=2) #画拟合曲线
36 plt.legend()
37 plt.show()

###正则表达式
**1.选择**
+ 竖线|代表选择，具有最低优先级，例如grey|gray


**2.数量限定**
某个字符后的数量限定符用来限定前面这个字符允许出现的个数。
+ 加号+ 代表前面的字符至少出现一次（1次或多次） 例如：goo+gle可表示google，gooogle，gooooole
+ 问号？ 代表前面的字符最多出现一次（0次或1次） 例如：cou？lor可匹配coulor，color
+ 星号* 代表前面的字符可以不出现，也可以出现1次或多次（0，1或多次）例如:0*42可匹配42，042，0042

![](https://raw.githubusercontent.com/nanfengchuiyeluo6/images/master/正则表达式.png)


###re模块
####compile函数
用于编译正则表达式，生成一个Pattern对象，使用形式如下：
```
1 re.compile(pattern[, flag])
```
其中，pattern是一个字符串形式的正则表达式，flag是一个可选参数，表示匹配模式，比如忽略大小写，多行模式等

###列表
&emsp; L[1:]:从第二个元素开始截取列表
&emsp; L[-2]:读取列表中倒数第二个元素
&emsp; L[1:5]:读取第2个元素到第5个元素
`如list2 = [1, 2, 3, 4, 5, 6, 7 ]`
`list2[1:5]:  [2, 3, 4, 5]`

###strip()
去掉文本开头和结尾的符号，如句子结尾有\n

###tile()
格式：tile（A,reps） 
* A：array_like 输入的array 
* reps：array_like A沿各个维度重复的次数
```
A=[1,2]
tile(A,2)
Out[10]: array([1, 2, 1, 2])

tile(A,(2,2))
Out[11]:
array([[1, 2, 1, 2],
       [1, 2, 1, 2]])

tile(A,(2,1))
Out[12]:
array([[1, 2],
       [1, 2]
```

###min(),max()
min(0)返回该矩阵中每一列的最小值

min(1)返回该矩阵中每一行的最小值

max(0)返回该矩阵中每一列的最大值

max(1)返回该矩阵中每一行的最大值

###python **表示幂
即把矩阵中的各元素值变成原来幂次，而不是矩阵相乘,且定义矩阵时使用array()函数来定义

###argsort()函数
将元素从小到大排列，返回排序后的各元素在原数组中的索引值

###get()函数
得到字典中对应键的值，若为get(i,0)则找键为i的值，若未找到则返回0

###字典中的item(),和iteritems()区别:
&emsp; 字典的items方法作用：是可以将字典中的所有项，以列表方式返回。因为字典是无序的，所以用items方法返回字典的所有项，也是没有顺序的。
&emsp; 字典的iteritems方法作用：与items方法相比作用大致相同，只是它的返回值不是列表，而是一个迭代器。

###sorted(iterable[,cmp[,key[,reverse]]])
参数解释：
1. iterable指定要排序的list或者iterable，不用多说；

2. cmp为函数，指定排序时进行比较的函数，可以指定一个函数或者lambda函数，如：
students为类对象的list，每个成员有三个域，用sorted进行比较时可以自己定cmp函数，例如这里要通过比较第三个数据成员来排序，代码可以这样写：
students = [('john', 'A', 15), ('jane', 'B', 12), ('dave', 'B', 10)]
sorted(students, key=lambda student : student[2])
1. key为函数，指定取待排序元素的哪一项进行排序，函数用上面的例子来说明，代码如下：
sorted(students, key=lambda student : student[2])
key指定的lambda函数功能是去元素student的第三个域（即：student[2]），因此sorted排序时，会以students所有元素的第三个域来进行排序。
有了上面的operator.itemgetter函数，也可以用该函数来实现，例如要通过student的第三个域排序，可以这么写：
sorted(students, key=operator.itemgetter(2))
sorted函数也可以进行多级排序，例如要根据第二个域和第三个域进行排序，可以这么写：
sorted(students, key=operator.itemgetter(1,2))
即先跟句第二个域排序，再根据第三个域排序。
1. reverse参数就不用多说了，是一个bool变量，表示升序还是降序排列，默认为false（升序排列），定义为True时将按降序排列。

###数组打印不全问题,有省略号
```
import numpy as np  
np.set_printoptions(threshold = 1e6)#设置打印数量的阈值
```

###改jupyter notebook默认路径
1. 打开C:/Users/你的账户/.jupyter/jupyter_notebook_config.py
2. 修改 #c.NotebookApp.notebook_dir = '' 为 c.NotebookApp.notebook_dir = '你想要默认打开的文件夹'，**并将#去掉**
3. 开始菜单找到 jupyter notebook 快捷键，右键->更多->打开文件所在位置，找打快捷方式在文件中的位置，右键->属性->目标，去掉最后的 %USERPROFILE%

###self代表类的实例

###广播原则
广播的原则：如果两个数组的后缘维度（trailing dimension，即从末尾开始算起的维度）的轴长度相符，或其中的一方的长度为1，则认为它们是广播兼容的。广播会在缺失和（或）长度为1的维度上进行。








###matplotlib.pyplot 的plt.add_subplot(331)
331表示把画布分成3行3列从左往右，从上往下第一块

###python切片
切片操作基本表达式：o[start_index:end_index:step]
&emsp; step:代表步长，正负均可，正代表从左到右，负代表从右到左，省略时默认为1，**切取方向非常重要**
&emsp; start_index：表示起始索引（包含该索引本身）；该参数省略时，表示从对象“端点”开始取值，至于是从“起点”还是从“终点”开始，则由step参数的正负决定，step为正从“起点”开始，为负从“终点”开始。
&emsp; end_index：表示终止索引（不包含该索引本身）；该参数省略时，表示一直取到数据“端点”，至于是到“起点”还是到“终点”，同样由step参数的正负决定，step为正时直到“终点”，为负时直到“起点”。

###str.format()
```
"{1} {0} {1}".format("hello", "world")  # 设置指定位置
'world hello world'
```

###shape和*shape的区别
shape打印是个保存形状的元组，*shape则把元祖中的元素取出为单个值
例子：
```
m1 = np.array([[2,3,4],[6,7,8],[10,11,12]])
print(m1.shape)
print(*m1.shape)
```
结果：
```
(3, 3)
 3 3
```

###pandas.DataFrame()
类似excel的二维表,同时DataFrame可以设置列名columns与行名index
例子：
```
type_dict = {'3': ['foo'], '4':['bar'],'5':['foobar'], '6':['foobarbar']}
df = pandas.DataFrame(type_dict)
print(df)
```
结果：
```
     3    4       5          6
0  foo  bar  foobar  foobarbar
```
**使用get_values()可得到所有值**
```
print(df.get_values())
[['foo' 'bar' 'foobar' 'foobarbar']]
```

###求标准差
&emsp; numpy.std() 求标准差的时候默认是除以 n 的，即是有偏的，np.std无偏样本标准差方式为加入参数 ddof = 1；
&emsp; pandas.std() 默认是除以n-1 的，即是无偏的，如果想和numpy.std() 一样有偏，需要加上参数ddof=0 ，即pandas.std(ddof=0)
&emsp; DataFrame的describe()中就包含有std()；





### enumerate()
用于将一个可遍历的数据对象(如列表、元组或字符串)组合为一个索引序列，同时列出数据和数据下标，一般用在 for 循环当中。
```
>>>seasons = ['Spring', 'Summer', 'Fall', 'Winter']
>>> list(enumerate(seasons))
[(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]
>>> list(enumerate(seasons, start=1))       # 下标从 1 开始
[(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]
```


###range相关用法
```
X =10*np.random.rand(5,3)
print(X)
y = np.array([0, 1, 2, 2, 1])
o = X[range(5),y]
print(o)
```
```
[[8.69085429 9.23003375 4.04620487]
 [3.25864454 8.83915961 4.53701494]
 [3.35682292 0.99775368 0.56795222]
 [7.66020735 2.89418004 0.03255102]
 [7.92240268 5.51456978 9.36346547]]
[8.69085429 8.83915961 0.56795222 0.03255102 5.51456978]
```
可以看到o输出的是一个一维数组，每行按y的标签输出

###python继承
```
class Person(object):
    def __init__(self, name, age):
        self.name = name
        self.age = age
        self.weight = 'weight'
    def talk(self):
        print("person is talking....")

class Chinese(Person):
    def __init__(self, name, age, language):  # 先继承，在重构
        Person.__init__(self, name, age)  #继承父类的构造方法，也可以写成：super(Chinese,self).__init__(name,age)
        self.language = language    # 定义类的本身属性 
    def walk(self):
        print('is walking...')
```

###字典in操作
用于判断键是否存在于字典中
```
dict = {'Name': 'Runoob', 'Age': 7}
 
# 检测键 Age 是否存在
if  'Age' in dict:
    print("键 Age 存在")
else :
    print("键 Age 不存在")

键 Age 存在
```

###将全为int的列表转为整数
`x = int(''.join([str(i) for i in a]))`