###tensorflow组成
tf = tensor + 计算图
tensor：数据，可以使=是常量也可以是变量，1维或n维
op：操作
计算图：数据操作的过程,搭建神经网络的计算过程，只搭建，不计算
session是运行的环境,执行计算图中的节点运算

###tf.matmul()
两矩阵相乘
###tf.multiply()
两矩阵的对应元素相同，而不是矩阵相乘，注意相乘的元素必须是同类型

###tf.placeholder()
相当于占位操作，此时并没有把要输入的数据输入模型，只是分配必要的内存，等建立session，在会话中运行模型时通过feed_dict来向占位符喂入数据
例如：
<font size=5>
```
data1 = tf.placeholder(tf.float32)
data2 = tf.placeholder(tf.float32)
dataAdd = tf.add(data1,data2)
with tf.Session() as sess:
    print(sess.run(dataAdd,feed_dict={data1:3,data2:4}))
print('end!')
```
</font>


###tf.rreduce_sum():
'x' is \[[1, 1, 1],
        [1, 1, 1]]
###求和
tf.reduce_sum(x) ==> 6
###按列求和
tf.reduce_sum(x, 0) ==> [2, 2, 2]
###按行求和
tf.reduce_sum(x, 1) ==> [3, 3]
###按照行的维度求和
tf.reduce_sum(x, 1, keep_dims=True) ==> \[[3], [3]]
###行列求和
tf.reduce_sum(x, [0, 1]) ==> 6


###tf.argmax()
有两个参数，第一个参数是矩阵，第二个参数是0或者1。0表示的是按列比较返回最大值的索引，1表示按行比较返回最大值的索引。即取行或者列的最大值的位置
例如：
<font size=5>
```
list_a = [[1,2,3,4,5],
         [3,3,3,1,6],
          [5,1,2,1,1]]
sess = tf.InteractiveSession()
argmax0 = tf.arg_max(list_a, 0)
print("argmax 0={}".format(argmax0.eval()))
argmax1 = tf.arg_max(list_a, 1)
print("argmax 1={}".format(argmax1.eval()))
```
```
结果：argmax 0=[2 1 0 0 1]
 	   argmax 1=[4 4 0]    
```
</font>





###tf.cast(x, dtype, name=None)
TensorFlow中张量数据类型的转换
第一个参数 x:   待转换的数据（张量）
第二个参数 dtype： 目标数据类型
第三个参数 name： 可选参数，定义操作的名称

###tf.reduce_mean()
假设x = \[[1,2,3],[4,5,6]]
tf.reduce_mean(x):是把所有元素加起来取平均值
tf.reduce_mean(x, 0):按列取平均值 结果为：[2.5,3.5,4.5]
tf.reduce_mean(x, 1):按行取平均值

###tf.equal()
比较两矩阵或向量相等的元素如
<font size=5>
```
A = [[1,3,4,5,6]]
B = [[1,3,4,3,2]]
with tf.Session() as sess:
    print(sess.run(tf.equal(A, B)))
```
```
结果为：[[ True  True  True False False]]
```
</font>

###tf.constant()
创建一个常数张量，传入list或数值来填充
例如：
<font size=5>
```
Constant 1-D Tensor populated with value list.
tensor = tf.constant([1, 2, 3, 4, 5, 6, 7]) => [1 2 3 4 5 6 7]
2-D tensor `a`
  a = tf.constant([1, 2, 3, 4, 5, 6], shape=[2, 3]) => [[1. 2. 3], [4. 5. 6.]]
```
</font>

###tf.Variables()
创建一个变量，TensorFlow中，变量必须初始化
利用init = tf.global_variables_initializer()
  sess.run(init)

###tf.assign(data2,dataAdd)
把dataAdd赋给data2

###eval()
和sess.run()区别：可使用sess.run()在同一步获取多个tensor值
例
<font size=5>
```

t = tf.constant(42.0)
u = tf.constant(37.0)
tu = tf.mul(t, u)
ut = tf.mul(u, t)
with sess.as_default():
   tu.eval()  # runs one step
   ut.eval()  # runs one step
   sess.run([tu, ut])  # evaluates both tensors in a single step
```
</font>

###tf.assign()和=的区别：
tf.assign()是创建一个操作符，这个操作符具有赋值的功能，但是=只是python的赋值，TensorFlow的函数操作会创建一个新的节点，但=不会，只是将变量引用到新节点上，而使用tf.assign()的话计算图中有赋值节点，分清哪些是TensorFlow的操作，哪些是python的赋值操作，就能分清哪些是在建图，哪些只是在改变引用
例如：
<font size=5>
```
a = tf.Variable(3)
op = tf.assign_add(a,1)
with tf.Session() as sess:
    sess.run(tf.global_variables_initializer())
    sess.run(op)
    sess.run(op)
    sess.run(op)
    sess.run(op)
    print(sess.run(a))
>>7
```
```
a = tf.Variable(3)
a = a + 1
with tf.Session() as sess:
    sess.run(tf.global_variables_initializer())
    sess.run(a)
    sess.run(a)
    sess.run(a)
    sess.run(a)
    print(a)
    print(sess.run(a))
>>Tensor("add:0", shape=(), dtype=int32)
4
```
</font>

### 矩阵基础
<font size=5>

```
data = tf.constant([[1,2,3],
                    [4,5,6],
                    [7,8,9]])

with tf.Session() as sess:
    print(sess.run(data[0])) #打印一行
    print(sess.run(data[:,1])) #打印一列
    print(sess.run(data[1,0]))#打印某行某列
```

</font>

###矩阵初始化相关
<font size=5>

```
#初始化为0
mat1 = tf.zeros([2,3])
#初始化为1
mat2 = tf.ones([2,3])
#初始化为特定值
mat3 = tf.fill([2,3],10)
#初始化为像mat4的零矩阵
mat4 = tf.constant([[1],[2],[3]])
mat5 = tf.zeros_like(mat4)
#分11等份
mat6 = tf.linspace(0.0,2.0,11)
#随机矩阵
mat7 = tf.random_uniform([2,3],1,10)
with tf.Session() as sess:
    print(sess.run(mat1))
    print(sess.run(mat2))
    print(sess.run(mat3))
    print(sess.run(mat5))
    print(sess.run(mat6))
    print(sess.run(mat7))
```

</font>

###画图相关
<font size=5>

```
#画折现
x = np.array([1,3,5,7,8,9])
y = np.array([15,20,35,24,46,27])
plt.plot(x,y,'r')
plt.show()
#画柱状
x = np.array([1,3,5,7,8,9])
y = np.array([15,20,35,24,46,27])
plt.bar(x,y,0.5,alpha=1,color='b') #0.5是底边占的比例，alpha是透明度
plt.show()
#画子图
plt.subplot(2,2,1)#表示把画板分为2行2列，当前位置是1
#图的坐标轴名称
plt.ylabel('Accuracy', fontsize=16)
```

</font>

###TensorBoard（keras）可视化

<font size=5>

```
from keras.callbacks import TensorBoard
```

```
tbCallBack = TensorBoard(log_dir='./logs',  # log 目录
         histogram_freq=0,  # 按照何等频率（epoch）来计算直方图，0为不计算
         batch_size=128,     # 用多大量的数据计算直方图
         write_graph=True,  # 是否存储网络结构图
         write_grads=True, # 是否可视化梯度直方图
         write_images=True,# 是否可视化参数
         embeddings_freq=0,
         embeddings_layer_names=None,
         embeddings_metadata=None)

```
```
#在model.fit_generator()中
callbacks = [tbCallBack]
```

</font>
然后cmd进入到文件保存的路径，输入

`tensorboard --logdir=log `(log为一个文件夹名称)

或者直接在浏览器输入http://localhost:6006也是OK的


