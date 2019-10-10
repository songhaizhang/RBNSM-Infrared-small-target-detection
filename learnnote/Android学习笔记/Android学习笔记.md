###四大组件：
活动，服务，广播接收器，内容提供器


###5类日志方法：
Log.v():用于打印最琐碎，意义最小的日志信息，级别 verbose
Log.d(tag,msg):用于打印一些调试信息，级别 debug,比verbose高一级  
                         tag:传入当前类名，msg:想打印的具体信息
Log.i():用于打印一些比较重要的数据，级别 info,比debug高一级
Log.w():用于打印一些警告信息，级别warn，比info高一级
Log.e():用于打印程序中的错误，级别 error，比warn高一级


###总是提示failed to resolve    com.android.support:appcompat-v7:27.+  解决：
在build gradle module:app 中将compileSdkVersion 和targetSdkVersion和最下方的compile改为26


###在xml中引用一个id
 则使用@id/id_name   在xml中定义一个id使用@+id/id_name


###安卓分两种资源文件：
1.在res下的可编译的资源文件，这种文件会在R.java里面自动生成该文件资源的id，除res/raw
2.放在assets中的原生资源文件，不会被R文件编译


###Fragmeng回调周期：
####1.onAttach() 
作用：fragment已经关联到activity，这个时候 activity已经传进来了， 获得activity的传递的值 就可以进行 与activity的通信里， 当然也可以使用getActivity(),前提是这个fragment已经和宿主的activity关联，并且没有脱离，有且只有调用一次。
####2.onCreate()
系统创建fragment的时候回调他，在他里面实例化一些变量 
          这些个变量主要是：当你 暂停 停止的时候 你想保持的数据 
          他只调用一次。
####3.onCreateView()
第一次使用的时候 fragment会在这上面画一个layout出来， 为了可以画控件 要返回一个 布局的view，也可以返回null j 就什么都没有显示。 
           当系统用到fragment的时候 fragment就要返回他的view，越快越好 ，所以尽量在这里不要做耗时操作，比如从数据库加载大量数据 
####4onActivityCreated()
当Activity中的onCreate方法执行完后调用。
注意了：
从这句官方的话可以看出：当执行onActivityCreated()的时候 activity的onCreate才刚完成。
所以在onActivityCreated()调用之前 activity的onCreate可能还没有完成，
所以不能再onCreateView()中进行 与activity有交互的UI操作，UI交互操作可以在onActivityCreated()里面进行。
所以呢，这个方法主要是初始化那些你需要你的父Activity或者Fragment的UI已经被完
整初始化才能初始化的元素。
####5.onStart()
和activity一致，启动Fragement 启动时回调,，此时Fragement可见。
####6.onResume()
   和activity一致 在activity中运行是可见的。激活, Fragement 进入前台, 可获取焦点时激活。
####7.onPause()
和activity一致 其他的activity获得焦点，这个仍然可见第一次调用的时候，指的是 用户 离开这个fragment（并不是被销毁）
通常用于 用户的提交（可能用户离开后不会回来了）
####8.onStop()
和activity一致， fragment不可见的， 可能情况：activity被stopped了或者 fragment被移除但被，加入到回退栈中，一个stopped的fragment仍然是活着的如果长时间不用也会被移除。
####9.   onDestroyView() 
Fragment中的布局被移除时调用。表示fragemnt销毁相关联的UI布局， 清除所有跟视图相关的资。
然后这个知识移除视图  并没有销毁而且还没有脱离activity
####10.onDestroy()
销毁fragment对象， 跟activity类似了。
####11.onDetach()
Fragment和Activity解除关联的时候调用。 脱离activity。


###Actionbar占有屏幕顶端的一片区域，通常持续在整个应用程序的使用过程
###actionbar的主要目的是：
使重要的行动（例如，刷新或搜索等）更方便于用户访问。
支持导航的一致性，方便应用在不同的视图间切换。
提供不常用动作来减少繁琐的操作流程
给你的应用一个显著的标识符
ActionBar主要由四个部分组成：AppIcon（应用标识、向主界面导航）、ViewControl（视图切换，或者显示一些描述信息）、ActionButtons（显示应用程序中最重要的动作、长按图标会提示该动作的描述）、ActionOverflow（相对不太常用的动作）


###tomcat启动服务点击bin文件目录下的startup 然后在网址输入http://localhost:8080


###Servlet:
Java Servlet 是运行在 Web 服务器或应用服务器上的程序，它是作为来自 Web 浏览器或其他 HTTP 客户端的请求和 HTTP 服务器上的数据库或应用程序之间的中间层。使用 Servlet，您可以收集来自网页表单的用户输入，呈现来自数据库或者其他源的记录，还可以动态创建网页”。我们把任何实现了 Servlet 接口的类都叫作 "Servlet"。Servlet 的作用主要是对 Request 的请求数据进行解析、按照业务逻辑处理并将结果封装成 Response 返回我的理解就是“读-计算-写”，像数学计算器一样，输入操作数、操作符按"等于"就显示出结果；也像人的脑神经元一样“接受刺激-信号处理-作出响应”。

###JNI和NDK关系
![](https://raw.githubusercontent.com/nanfengchuiyeluo6/images/master/JNI%E5%92%8CNDK%E7%9A%84%E5%85%B3%E7%B3%BB.png)

###JNI方法名
关于方法名Java_scut_carson_1ho_ndk_1demo_MainActivity_getFromJNI 
格式 = Java \_包名 \_ 类名_Java需要调用的方法名
Java必须大写
对于包名，包名里的.要改成_，_要改成_1 
如我的包名是：scut.carson_ho.ndk_demo，则需要改成scut_carson_1ho_ndk_1demo 
最后，将创建好的test.cpp文件放入到工程文件目录中的src/main/jni文件夹 
若无jni文件夹，则手动创建。

###在Android的Bitmap.Config中有四个枚举类型
**ALPHA_8**：每个像素都需要1（8位）个字节的内存，只存储位图的透明度，没有颜色信息

**ARGB_4444**：A(Alpha)占4位的精度，R(Red)占4位的精度，G(Green)占4位的精度，B（Blue）占4位的精度，加起来一共是16位的精度，折合是2个字节，也就是一个像素占两个字节的内存，同时存储位图的透明度和颜色信息。不过由于该精度的位图质量较差，官方不推荐使用

**ARGB_8888**：这个类型的跟ARGB_4444的原理是一样的，只是A,R,G,B各占8个位的精度，所以一个像素占4个字节的内存。由于该类型的位图质量较好，官方特别推荐使用。但是，如果一个480*800的位图设置了此类型，那个它占用的内存空间是：480*800*4/(1024*1024)=1.5M

**RGB_565**：同理，R占5位精度，G占6位精度，B占5位精度，一共是16位精度，折合两个字节。这里注意的时，这个类型存储的只是颜色信息，没有透明度信息





