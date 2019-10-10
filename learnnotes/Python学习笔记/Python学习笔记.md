:
import numpy as np
from scipy.optimize import leastsq
 
###������(Xi,Yi)###
Xi=np.array([8.19,2.72,6.39,8.71,4.7,2.66,3.78,11.3])
Yi=np.array([7.01,2.78,6.47,6.71,4.1,4.23,4.05,10.1])
 
###��Ҫ��ϵĺ���func�����error###
def func(p,x):
    k,b=p
    return k*x+b
 
def error(p,x,y,s):
    print (s)
    return func(p,x)-y #x��y�����б��ʷ���ֵҲ�Ǹ��б�
 
###TEST
p0=[100,100]
#print( error(p0,Xi,Yi) )
 
###�������Ӵ˿�ʼ###
s="Test the number of iteration" #������С���˷�����leastsq�õ��ü���error���������ҵ�ʹ�þ������֮����С��k��b
Para=leastsq(error,p0,args=(Xi,Yi,s)) #��error�����г���p����Ĳ��������args��
k,b=Para[0]
print("k=",k,'\n',"b=",b)
 
###��ͼ�������Ч��###
import matplotlib.pyplot as plt
plt.scatter(Xi,Yi,color="red",label="Sample Point",linewidth=3) #��������
x=np.linspace(0,10,1000)
y=k*x+b
plt.plot(x,y,color="orange",label="Fitting Line",linewidth=2) #�����ֱ��
plt.legend()
plt.show()
:





 2 import numpy as np
 3 from scipy.optimize import leastsq
 4 
 5 ###������(Xi,Yi)###
 6 Xi=np.array([0,1,2,3,-1,-2,-3])
 7 Yi=np.array([-1.21,1.9,3.2,10.3,2.2,3.71,8.7])
 8 
 9 ###��Ҫ��ϵĺ���func�����error###
10 def func(p,x):
11     a,b,c=p
12     return a*x**2+b*x+c
13 
14 def error(p,x,y,s):
15     print s
16     return func(p,x)-y #x��y�����б��ʷ���ֵҲ�Ǹ��б�
17 
18 #TEST
19 p0=[5,2,10]
20 #print( error(p0,Xi,Yi) )
21 
22 ###�������Ӵ˿�ʼ###
23 s="Test the number of iteration" #������С���˷�����leastsq�õ��ü���error���������ҵ�ʹ�þ������֮����С��a~c
24 Para=leastsq(error,p0,args=(Xi,Yi,s)) #��error�����г���p����Ĳ��������args��
25 a,b,c=Para[0]
26 print"a=",a,'\n',"b=",b,"c=",c
27 
28 ###��ͼ�������Ч��###
29 import matplotlib.pyplot as plt
30 
31 plt.figure(figsize=(8,6))
32 plt.scatter(Xi,Yi,color="red",label="Sample Point",linewidth=3) #��������
33 x=np.linspace(-5,5,1000)
34 y=a*x**2+b*x+c
35 plt.plot(x,y,color="orange",label="Fitting Curve",linewidth=2) #���������
36 plt.legend()
37 plt.show()

###������ʽ
**1.ѡ��**
+ ����|����ѡ�񣬾���������ȼ�������grey|gray


**2.�����޶�**
ĳ���ַ���������޶��������޶�ǰ������ַ�������ֵĸ�����
+ �Ӻ�+ ����ǰ����ַ����ٳ���һ�Σ�1�λ��Σ� ���磺goo+gle�ɱ�ʾgoogle��gooogle��gooooole
+ �ʺţ� ����ǰ����ַ�������һ�Σ�0�λ�1�Σ� ���磺cou��lor��ƥ��coulor��color
+ �Ǻ�* ����ǰ����ַ����Բ����֣�Ҳ���Գ���1�λ��Σ�0��1���Σ�����:0*42��ƥ��42��042��0042

![](https://raw.githubusercontent.com/nanfengchuiyeluo6/images/master/������ʽ.png)


###reģ��
####compile����
���ڱ���������ʽ������һ��Pattern����ʹ����ʽ���£�
```
1 re.compile(pattern[, flag])
```
���У�pattern��һ���ַ�����ʽ��������ʽ��flag��һ����ѡ��������ʾƥ��ģʽ��������Դ�Сд������ģʽ��

###�б�
&emsp; L[1:]:�ӵڶ���Ԫ�ؿ�ʼ��ȡ�б�
&emsp; L[-2]:��ȡ�б��е����ڶ���Ԫ��
&emsp; L[1:5]:��ȡ��2��Ԫ�ص���5��Ԫ��
`��list2 = [1, 2, 3, 4, 5, 6, 7 ]`
`list2[1:5]:  [2, 3, 4, 5]`

###strip()
ȥ���ı���ͷ�ͽ�β�ķ��ţ�����ӽ�β��\n

###tile()
��ʽ��tile��A,reps�� 
* A��array_like �����array 
* reps��array_like A�ظ���ά���ظ��Ĵ���
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
min(0)���ظþ�����ÿһ�е���Сֵ

min(1)���ظþ�����ÿһ�е���Сֵ

max(0)���ظþ�����ÿһ�е����ֵ

max(1)���ظþ�����ÿһ�е����ֵ

###python **��ʾ��
���Ѿ����еĸ�Ԫ��ֵ���ԭ���ݴΣ������Ǿ������,�Ҷ������ʱʹ��array()����������

###argsort()����
��Ԫ�ش�С�������У����������ĸ�Ԫ����ԭ�����е�����ֵ

###get()����
�õ��ֵ��ж�Ӧ����ֵ����Ϊget(i,0)���Ҽ�Ϊi��ֵ����δ�ҵ��򷵻�0

###�ֵ��е�item(),��iteritems()����:
&emsp; �ֵ��items�������ã��ǿ��Խ��ֵ��е���������б�ʽ���ء���Ϊ�ֵ�������ģ�������items���������ֵ�������Ҳ��û��˳��ġ�
&emsp; �ֵ��iteritems�������ã���items����������ô�����ͬ��ֻ�����ķ���ֵ�����б�����һ����������

###sorted(iterable[,cmp[,key[,reverse]]])
�������ͣ�
1. iterableָ��Ҫ�����list����iterable�����ö�˵��

2. cmpΪ������ָ������ʱ���бȽϵĺ���������ָ��һ����������lambda�������磺
studentsΪ������list��ÿ����Ա����������sorted���бȽ�ʱ�����Լ���cmp��������������Ҫͨ���Ƚϵ��������ݳ�Ա�����򣬴����������д��
students = [('john', 'A', 15), ('jane', 'B', 12), ('dave', 'B', 10)]
sorted(students, key=lambda student : student[2])
1. keyΪ������ָ��ȡ������Ԫ�ص���һ��������򣬺����������������˵�����������£�
sorted(students, key=lambda student : student[2])
keyָ����lambda����������ȥԪ��student�ĵ������򣨼���student[2]�������sorted����ʱ������students����Ԫ�صĵ�����������������
���������operator.itemgetter������Ҳ�����øú�����ʵ�֣�����Ҫͨ��student�ĵ����������򣬿�����ôд��
sorted(students, key=operator.itemgetter(2))
sorted����Ҳ���Խ��ж༶��������Ҫ���ݵڶ�����͵�������������򣬿�����ôд��
sorted(students, key=operator.itemgetter(1,2))
���ȸ���ڶ����������ٸ��ݵ�����������
1. reverse�����Ͳ��ö�˵�ˣ���һ��bool��������ʾ�����ǽ������У�Ĭ��Ϊfalse���������У�������ΪTrueʱ�����������С�

###�����ӡ��ȫ����,��ʡ�Ժ�
```
import numpy as np  
np.set_printoptions(threshold = 1e6)#���ô�ӡ��������ֵ
```

###��jupyter notebookĬ��·��
1. ��C:/Users/����˻�/.jupyter/jupyter_notebook_config.py
2. �޸� #c.NotebookApp.notebook_dir = '' Ϊ c.NotebookApp.notebook_dir = '����ҪĬ�ϴ򿪵��ļ���'��**����#ȥ��**
3. ��ʼ�˵��ҵ� jupyter notebook ��ݼ����Ҽ�->����->���ļ�����λ�ã��Ҵ��ݷ�ʽ���ļ��е�λ�ã��Ҽ�->����->Ŀ�꣬ȥ������ %USERPROFILE%

###self�������ʵ��

###�㲥ԭ��
�㲥��ԭ�������������ĺ�Եά�ȣ�trailing dimension������ĩβ��ʼ�����ά�ȣ����᳤������������е�һ���ĳ���Ϊ1������Ϊ�����ǹ㲥���ݵġ��㲥����ȱʧ�ͣ��򣩳���Ϊ1��ά���Ͻ��С�








###matplotlib.pyplot ��plt.add_subplot(331)
331��ʾ�ѻ����ֳ�3��3�д������ң��������µ�һ��

###python��Ƭ
��Ƭ�����������ʽ��o[start_index:end_index:step]
&emsp; step:���������������ɣ�����������ң���������ҵ���ʡ��ʱĬ��Ϊ1��**��ȡ����ǳ���Ҫ**
&emsp; start_index����ʾ��ʼ�����������������������ò���ʡ��ʱ����ʾ�Ӷ��󡰶˵㡱��ʼȡֵ�������Ǵӡ���㡱���Ǵӡ��յ㡱��ʼ������step����������������stepΪ���ӡ���㡱��ʼ��Ϊ���ӡ��յ㡱��ʼ��
&emsp; end_index����ʾ��ֹ�������������������������ò���ʡ��ʱ����ʾһֱȡ�����ݡ��˵㡱�������ǵ�����㡱���ǵ����յ㡱��ͬ����step����������������stepΪ��ʱֱ�����յ㡱��Ϊ��ʱֱ������㡱��

###str.format()
```
"{1} {0} {1}".format("hello", "world")  # ����ָ��λ��
'world hello world'
```

###shape��*shape������
shape��ӡ�Ǹ�������״��Ԫ�飬*shape���Ԫ���е�Ԫ��ȡ��Ϊ����ֵ
���ӣ�
```
m1 = np.array([[2,3,4],[6,7,8],[10,11,12]])
print(m1.shape)
print(*m1.shape)
```
�����
```
(3, 3)
 3 3
```

###pandas.DataFrame()
����excel�Ķ�ά��,ͬʱDataFrame������������columns������index
���ӣ�
```
type_dict = {'3': ['foo'], '4':['bar'],'5':['foobar'], '6':['foobarbar']}
df = pandas.DataFrame(type_dict)
print(df)
```
�����
```
     3    4       5          6
0  foo  bar  foobar  foobarbar
```
**ʹ��get_values()�ɵõ�����ֵ**
```
print(df.get_values())
[['foo' 'bar' 'foobar' 'foobarbar']]
```

###���׼��
&emsp; numpy.std() ���׼���ʱ��Ĭ���ǳ��� n �ģ�������ƫ�ģ�np.std��ƫ������׼�ʽΪ������� ddof = 1��
&emsp; pandas.std() Ĭ���ǳ���n-1 �ģ�������ƫ�ģ�������numpy.std() һ����ƫ����Ҫ���ϲ���ddof=0 ����pandas.std(ddof=0)
&emsp; DataFrame��describe()�оͰ�����std()��





### enumerate()
���ڽ�һ���ɱ��������ݶ���(���б�Ԫ����ַ���)���Ϊһ���������У�ͬʱ�г����ݺ������±꣬һ������ for ѭ�����С�
```
>>>seasons = ['Spring', 'Summer', 'Fall', 'Winter']
>>> list(enumerate(seasons))
[(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]
>>> list(enumerate(seasons, start=1))       # �±�� 1 ��ʼ
[(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]
```


###range����÷�
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
���Կ���o�������һ��һά���飬ÿ�а�y�ı�ǩ���

###python�̳�
```
class Person(object):
    def __init__(self, name, age):
        self.name = name
        self.age = age
        self.weight = 'weight'
    def talk(self):
        print("person is talking....")

class Chinese(Person):
    def __init__(self, name, age, language):  # �ȼ̳У����ع�
        Person.__init__(self, name, age)  #�̳и���Ĺ��췽����Ҳ����д�ɣ�super(Chinese,self).__init__(name,age)
        self.language = language    # ������ı������� 
    def walk(self):
        print('is walking...')
```

###�ֵ�in����
�����жϼ��Ƿ�������ֵ���
```
dict = {'Name': 'Runoob', 'Age': 7}
 
# ���� Age �Ƿ����
if  'Age' in dict:
    print("�� Age ����")
else :
    print("�� Age ������")

�� Age ����
```

###��ȫΪint���б�תΪ����
`x = int(''.join([str(i) for i in a]))`