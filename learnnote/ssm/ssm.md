###解决ecplise新建maven web项目 pom.xml报错的问题
+ 首先cmd进入maven的本地库
+ 然后`find ~/.m2 -name "*.lastUpdated" -exec grep -q "Could not transfer" {} \; -print -exec rm {} \;​ `
+ 然后`cd %userprofile%\.m2\repository`
+ 然后`for /r %i in (*.lastUpdated) do del %i`

这样就删除了下载失败的jar，然后右键项目maven->updateproject

####这是手动将jar放入本地库
mvn install:install-file -Dfile=F:\software\xstream-1.3.1.jar -DgroupId=com.thoughtworks.xstream -DartifactId=xstream -Dversion=1.3.1 -Dpackaging=jar

###使用 Eclipse 构建的时候会出现 run as 中没有 maven package 选项
1. 项目右击-->Run As-->Run Configurations
2. 在左侧Maven Build下选中自己的工程名
3. 然后在右侧Goals输入框中输入“clean package”
4. 点击Apply完成配置，如图
![](https://raw.githubusercontent.com/nanfengchuiyeluo6/images/master/打包maven工程.png)

###解决Failed to initialize component [org.apache.catalina.webresources.JarResource
有两种可能，一种是jar错误，cmd到工程目录，输入mvn test可以看到一些jar错误，如果没错也可手动看。第二个是tomcat和spring版本的问题，调整spring等的jar的版本可以解决此问题


###eclipse配置spring环境
####1.下载以下三个东西：
1. spring插件包：http://download.springsource.com/release/TOOLS/update/3.7.3.RELEASE/e4.5/springsource-tool-suite-3.7.3.RELEASE-e4.5.2-updatesite.zip（将前面的版本改成对应的即可下载）
2. logging日志api
####2.打开help-install new software-add-archive-选择下载的插件包，勾选四个带IDE的选项，取消最下面的contact all update选项，然后一直下一步

###VirtualBox 未能启动虚拟电脑，由于下述物理网未找到:
**错误提示：**
![](https://raw.githubusercontent.com/nanfengchuiyeluo6/images/master/错误提示.jpg)

**解决方法：将链接方式转为内部网络**
![](https://raw.githubusercontent.com/nanfengchuiyeluo6/images/master/内部网络.jpg)

**如果还是配置出错ping不同本地**
![](https://raw.githubusercontent.com/nanfengchuiyeluo6/images/master/ping不同本地.jpg)

**虚拟机平本地的ping不通解决方法：防火墙未能关闭**

###在 VirtualBox 虚拟机上显示鼠标指针
首先关闭虚拟机，然后该镜像的设置->系统->指点设备改为usb触控板

###虚拟机无法ping通电脑，但是电脑可以ping通虚拟机
**一般是防火墙开启导致的，关闭防火墙即可**

###解决springoot项目右键没有run
点击src->mark directory as ->sources root

###DAO层，Service层，Controller层、View层
**DAO层：** DAO层主要是做数据持久层的工作，负责与数据库进行联络的一些任务都封装在此，DAO层的设计首先是设计DAO的接口，然后在Spring的配置文件中定义此接口的实现类，然后就可在模块中调用此接口来进行数据业务的处理，而不用关心此接口的具体实现类是哪个类，显得结构非常清晰，DAO层的数据源配置，以及有关数据库连接的参数都在Spring的配置文件中进行配置。   
  
**Service层：** Service层主要负责业务模块的逻辑应用设计。同样是首先设计接口，再设计其实现的类，接着再Spring的配置文件中配置其实现的关联。这样我们就可以在应用中调用Service接口来进行业务处理。Service层的业务实现，具体要调用到已定义的DAO层的接口，封装Service层的业务逻辑有利于通用的业务逻辑的独立性和重复利用性，程序显得非常简洁。   
  
**Controller层:** Controller层负责具体的业务模块流程的控制，在此层里面要调用Serice层的接口来控制业务流程，控制的配置也同样是在Spring的配置文件里面进行，针对具体的业务流程，会有不同的控制器，我们具体的设计过程中可以将流程进行抽象归纳，设计出可以重复利用的子单元流程模块，这样不仅使程序结构变得清晰，也大大减少了代码量。   
  
View层 此层与控制层结合比较紧密，需要二者结合起来协同工发。View层主要负责前台jsp页面的表示，   
  
DAO层，Service层这两个层次都可以单独开发，互相的耦合度很低，完全可以独立进行，这样的一种模式在开发大项目的过程中尤其有优势，Controller，View层因为耦合度比较高，因而要结合在一起开发，但是也可以看作一个整体独立于前两个层进行开发。这样，在层与层之前我们只需要知道接口的定义，调用接口即可完成所需要的逻辑单元应用，一切显得非常清晰简单。   
  
DAO设计的总体规划需要和设计的表，和实现类之间一一对应。   
  
DAO层所定义的接口里的方法都大同小异，这是由我们在DAO层对数据库访问的操作来决定的，对数据库的操作，我们基本要用到的就是新增，更新，删除，查询等方法。因而DAO层里面基本上都应该要涵盖这些方法对应的操作。除此之外，可以定义一些自定义的特殊的对数据库访问的方法。   
  
**Service逻辑层设计**   
Service层是建立在DAO层之上的，建立了DAO层后才可以建立Service层，而Service层又是在Controller层之下的，因而Service层应该既调用DAO层的接口，又要提供接口给Controller层的类来进行调用，它刚好处于一个中间层的位置。每个模型都有一个Service接口，每个接口分别封装各自的业务处理方法。   
  
在DAO层定义的一些方法，在Service层并没有使用，那为什么还要在DAO层进行定义呢？这是由我们定义的需求逻辑所决定的。DAO层的操作 经过抽象后基本上都是通用的，因而我们在定义DAO层的时候可以将相关的方法定义完毕，这样的好处是在对Service进行扩展的时候不需要再对DAO层进行修改，提高了程序的可扩展性。

###spring boot注解总结
1. @RunWith(SpringRunner.class)
   当一个类用@RunWith注释或继承一个用@RunWith注释的类时，JUnit将调用它所引用的类来运行该类中的测试而不是开发者去在junit内部去构建它。我们在开发过程中使用这个特性。

2. @Autowired （自动装配）
   去除setter方法，当使用为自动连接属性传递的时候，Spring 会将这些传递过来的值或者引用自动分配给那些属性。
3. @Entity
   对实体注释
4. @Id
   声明此属性为主键
5. @GeneratedValue
   指定主键生成策略
6. @Data
   注解在类上，简化java代码书写，为该类提供读写属性，还提供了equals(),hashCode(),toString()方法
7. @RestController
   会处理返回的数据格式，使用该类型的注解后返回的不再是视图，不会进行转跳，而是返回json或xml数据格式，输出在页面上。一般注解在类上。
8. @RequestMapping
   用来处理请求地址映射的注解，可用于类或方法上，用于类上表示类中的所有响应请求方法都是以该地址作为父路径。
9. @Transient
    1）一旦变量被transient修饰，变量将不再是对象持久化的一部分，该变量内容在序列化后无法获得访问。（如不希望序列化银行卡的密码等），再或者是数据库中没有的字段。


    2）transient关键字只能修饰变量，而不能修饰方法和类。注意，本地变量是不能被transient关键字修饰的。变量如果是用户自定义类变量，则该类需要实现Serializable接口。

    3）被transient关键字修饰的变量不再能被序列化，一个静态变量不管是否被transient修饰，均不能被序列化。
10. @JsonSerialize
    此注解用于属性或者getter方法，用于在序列化的时候嵌入我们自定义的代码，比如序列化一个double时在其后面限制两位小数。
11. @Bean
    标注在方法上(返回某个实例的方法)，等价于spring的xml配置文件中的<bean>，作用为：注册bean对象。一般和@Configuration或者@Component使用
12. @Component
    将切面定义为Spring管理Bean

###spring的Assert
中文叫断言，它断定某一个实际的运行值和预期值一致，否则就抛出异常。



###控制反转（ioc = inversion of Control）
简言之，ioC就是一个对象定义其依赖关系而不创建他们的过程
1. 使用私有属性保存依赖对象，并且只能通过构造函数参数传入，可以将对象传入构造方法，而不能在新类中new对象，或通过非构造函数传入依赖
2. 并不用new，而使用spring控制new过程。Spring 启动时会把所需的类实例化成对象，如果需要依赖，则先实例化依赖，然后实例化当前类。因为依赖必须通过构建函数传入，所以实例化时，当前类就会接收并保存所有依赖的对象。这一步也就是所谓的依赖注入。

综上：在 Spring 中，类的实例化、依赖的实例化、依赖的传入都交由 Spring Bean 容器控制，
而不是用new方式实例化对象、通过非构造函数方法传入依赖等常规方式。
实质的控制权已经交由程序管理，而不是程序员管理，所以叫做控制反转。

###spring bean
1. Bean容器或称spring ioC容器，主要用来管理对象和依赖，以及依赖注入。
2. Bean是一个java对象，根据bean规范编写出来的类并由bean容器生成的对象就是一个bean。
3. bean规范：
   1. 所有属性为private
   2. 提供默认构造方法
   3. 提供getter和setter
   4. 实现serializable接口


###idea快捷键
1. Alt + Insert：自动生成某个类的 Getters, Setters, Constructors, hashCode/equals, toString 等代码。
2. Ctrl + /：对单行代码，添加或删除注释。
3. Ctrl + Shift + /： 对代码块，添加或删除注释。
4. Ctrl + Alt + L：格式化代码 
5. Ctrl + Alt + O：去除没有实际用到的包，这在 java 类中特别有用。
6. Ctrl + D：直接复制本行代码并粘贴到下一行
7. Ctrl + shift + 回车：直接跳转到下一行输入
8. Ctrl + P：显示方法的参数
9.  Ctrl + Alt + B：弹出接口的实现类

###关于Correct the classpath of your application so that it contains a single, compatible version of xxx错

***************************
APPLICATION FAILED TO START
***************************

Description:

An attempt was made to call a method that does not exist. The attempt was made from the following location:

    org.springframework.orm.jpa.support.PersistenceAnnotationBeanPostProcessor$PersistenceElement.<init>(PersistenceAnnotationBeanPostProcessor.java:665)

The following method did not exist:

    javax.persistence.PersistenceContext.synchronization()Ljavax/persistence/SynchronizationType;

The method's class, javax.persistence.PersistenceContext, is available from the following locations:

    jar:file:/F:/ideapro/sell/lib/javax.persistence.jar!/javax/persistence/PersistenceContext.class
    jar:file:/C:/Users/nanfengchuiyeluo/.m2/repository/javax/persistence/javax.persistence-api/2.2/javax.persistence-api-2.2.jar!/javax/persistence/PersistenceContext.class

It was loaded from the following location:

    file:/F:/ideapro/sell/lib/javax.persistence.jar

**解决办法：** 在这两个路径中删去其中一个即可

###springBoot+jpa 测试自增时数据库报错Springboot-jpa Table 'sell.hibernate_sequence' doesn't exist
`@GeneratedValue(strategy = GenerationType.IDENTITY)`
```
@Entity
public class ProductCategory {

    //类目id
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Integer categoryId;
    //类目名字
```

###jpa通过解析方法名创建查询
JpaRepository会对Repository层所有未加@Query的方法名进行校验，不符合规范会报错,除非添加@Query注解；
![](https://raw.githubusercontent.com/nanfengchuiyeluo6/images/master/jpa.jpg)
按方法名解析的查询方法通常只适用于单表查询，且建议where条件参数不多于三条的情况下，返回值通常上对应表的实体Bean，通常用实体类List类型；具体要看返回结果，当返回值与类型不匹配时会造成查询错误；

###lambda表达式
语法格式：
(parameters) -> expression
或
(parameters) ->{ statements; }
例子：
```
// 1. 不需要参数,返回值为 5  
() -> 5  
  
// 2. 接收一个参数(数字类型),返回其2倍的值  
x -> 2 * x  
  
// 3. 接受2个参数(数字),并返回他们的差值  
(x, y) -> x – y  
  
// 4. 接收2个int型整数,返回他们的和  
(int x, int y) -> x + y  
  
// 5. 接受一个 string 对象,并在控制台打印,不返回任何值(看起来像是返回void)  
(String s) -> System.out.print(s)
```

用到Stream：是一个来自数据源的元素队列并支持聚合操。元素是特定类型的对象，形成一个队列。 Java中的Stream并不会存储元素，而是按需计算。
**map方法：** 用于映射每个元素到对应的结果，用到lambda表达式，如下
```
List<Integer> numbers = Arrays.asList(3, 2, 2, 3, 7, 3, 5);
// 获取对应的平方数
List<Integer> squaresList = numbers.stream().map( i -> i*i).distinct().collect(Collectors.toList());
```

**Collectors：** Collectors 类实现了很多归约操作，例如将流转换成集合和聚合元素，可用于返回列表或字符串。

###在网址中的#的作用
 #代表网页中的一个位置，其右面的字符，就是该位置的标识符，例如http://www.example.com/index.html#print，就代表网页index.html的print位置。浏览器读取这个URL后，会自动将print位置滚动至可视区域。

**#是用来指导浏览器动作的，对服务器端完全无效，所有http请求中不包括#**

###关于get和post请求
1. 哪些情况下，浏览器会发送get请求：
   1. 直接在浏览器输入某个网址
   2. 点击链接
   3. 表单默认的提交方式
2. 哪些情况下，浏览器会发送post请求：
   1. 设置表单method=“post”
3. get请求的特点
   1. 请求参数会添加到请求资源路径的后面，并且只能添加少量参数，因为请求行只有一行
   2. 请求参数会显示在浏览器的地址栏，路由器会记录请求地址
4. post请求特点
   1. 请求参数添加到实体内容里面，可以添加大量的参数（这也解释了为什么浏览器地址栏不能发送post请求，在地址栏里只能写url，并不能进入到http包的实体当中）
   2. 相对安全，但是post请求不会对请求参数进行加密处理，可以通过https协议保证数据安全

通俗理解：GET从指定服务器中获取数据，POST提交数据给指定的服务器处理。

###关于dto，vo，do等区别
1. VO（View Object）：视图对象，用于展示层，它的作用是把某个指定页面（或组件）的所有数据封装起来。
2. DTO（Data Transfer Object）：数据传输对象，泛指用于展示层与服务层之间的数据传输对象。
3. PO：持久对象(persistent object)，就是在Object/Relation Mapping框架中的Entity，PO的每个属性基本上都对应数据库表里面的某个字段。
4. BO：businessobject业务对象。主要作用是把业务逻辑封装为一个对象。这个对象可以包括一个或多个其它的对象。比如一个简历，有教育经历、工作经历、社会关系等等。我们可以把教育经历对应一个PO，工作经历对应一个PO，社会关系对应一个PO。建立一个对应简历的BO对象处理简历，每个BO包含这些PO。
5. POJO：是一个简单的、普通Java对象，它包含业务逻辑处理或持久化逻辑等，但不是JavaBean、EntityBean等，不具有任何特殊角色，不继承或不实现任何其它Java框架的类或接口。 可以包含类似与JavaBean属性和对属性访问的setter和getter方法的。
    1. POJO持久化之后==〉PO
    （在运行期，由Hibernate中的cglib动态把POJO转换为PO，PO相对于POJO会增加一些用来管理数据库entity状态的属性和方法。PO对于programmer来说完全透明，由于是运行期生成PO，所以可以支持增量编译，增量调试。）

    2. POJO传输过程中==〉DTO

    3. POJO用作表示层==〉VO

    PO 和VO都应该属于它。


###java反射
通过反射，我们可以在运行时获得程序或程序集中每一个类型的成员和成员的信息。程序中一般的对象的类型都是在编译期就确定下来的，而 Java 反射机制可以动态地创建对象并调用其属性，这样的对象的类型在编译期是未知的。所以我们可以通过反射机制直接创建对象，即使这个对象的类型在编译期是未知的。

反射的核心是 JVM 在运行时才动态加载类或调用方法/访问属性，它不需要事先（写代码的时候或编译期）知道运行对象是谁。

Java 反射主要提供以下功能：
1. 在运行时判断任意一个对象所属的类；
2. 在运行时构造任意一个类的对象；
3. 在运行时判断任意一个类所具有的成员变量和方法（通过反射甚至可以调用private方法）；
4. 在运行时调用任意一个对象的方法

getFields(): 获取某个类的所有的public字段，其中是包括父类的public字段的。
getDeclaredFields()：获取某个类的自身的所有字段，不包括父类的字段。
对于私有的成员变量来说，要操作其属性值的话，就需要设置setAccessible(true);
field.setAccessible(true)就是让我们在反射时可以操作私有成员属性的值。
```
Field[] fields = student.getClass().getDeclaredFields();
        for(Field field : fields){
            // 获取原来的访问控制权限
            boolean accessFlag = field.isAccessible();
            if(!field.isAccessible()) field.setAccessible(true);
            System.out.println("成员属性:"+field.getName()+" 成员属性修饰符: "+field.getModifiers()+" 成员属性值: "+field.get(student));
            field.setAccessible(accessFlag);
        }

        // 成员属性:studentNumber 成员属性修饰符: 1 成员属性值: 20191223
        // 成员属性:grade 成员属性修饰符: 2 成员属性值: 99.0
```
getModifiers():获取访问权限。
1. public
2. private
4. protected 

![](https://raw.githubusercontent.com/nanfengchuiyeluo6/images/master/java运行.jpg)

首先我们了解一下JVM，什么是JVM，Java的虚拟机，java之所以能跨平台就是因为这个东西，你可以理解成一个进程，程序，只不过他的作用是用来跑你的代码的。上图是java的内存模型，我们关注的点，一个方法区，一个栈，一个堆，初学的时候老师不深入的话只告诉你java的内存分为堆和栈，易懂点吧！假如你写了一段代码：Object o=new Object();运行了起来！首先JVM会启动，你的代码会编译成一个.class文件，然后被类加载器加载进jvm的内存中，你的类Object加载到方法区中，创建了Object类的class对象到堆中，注意这个不是new出来的对象，而是类的类型对象，每个类只有一个class对象，作为方法区类的数据结构的接口。jvm创建对象前，会先检查类是否加载，寻找类对应的class对象，若加载好，则为你的对象分配内存，初始化也就是代码:new Object()。上面的流程就是你自己写好的代码扔给jvm去跑，跑完就over了，jvm关闭，你的程序也停止了。为什么要讲这个呢？因为要理解反射必须知道它在什么场景下使用。题主想想上面的程序对象是自己new的，程序相当于写死了给jvm去跑。假如一个服务器上突然遇到某个请求哦要用到某个类，哎呀但没加载进jvm，是不是要停下来自己写段代码，new一下，哦启动一下服务器，（脑残）！  反射是什么呢？当我们的程序在运行时，需要动态的加载一些类这些类可能之前用不到所以不用加载到jvm，而是在运行时根据需要才加载，这样的好处对于服务器来说不言而喻，举个例子我们的项目底层有时是用mysql，有时用oracle，需要动态地根据实际情况加载驱动类，这个时候反射就有用了，假设 com.java.dbtest.myqlConnection，com.java.dbtest.oracleConnection这两个类我们要用，这时候我们的程序就写得比较动态化，通过Class tc = Class.forName("com.java.dbtest.TestConnection");通过类的全类名让jvm在服务器中找到并加载这个类，而如果是oracle则传入的参数就变成另一个了。这时候就可以看到反射的好处了，这个动态性就体现出java的特性了！举多个例子，大家如果接触过spring，会发现当你配置各种各样的bean时，是以配置文件的形式配置的，你需要用到哪些bean就配哪些，spring容器就会根据你的需求去动态加载，你的程序就能健壮地运行。

###json解析
最基本的方法有两个：
1. toJson(obj,type): 将对象转化为Json字符串
2. fromJson(obj，type)： 将Json字符串转为type对应的对象

###springboot 报错 Invalid character found in the request target. The valid characters are defined in RFC 3986
RFC 3986文档对Url的编解码问题做出了详细的建议，指出了哪些字符需要被编码才不会引起Url语义的转变，以及对为什么这些字符需要编码做出了相应的解释。
也就是URL中不能包含的特殊字符:
+ 键盘上那些控制键:(<32或者=127)
+ 非英文字符(>127)
+ 空格(32)
+ 双引号(34)
+ #(35)
+ <(60)
+ \>(62)
+ 反斜杠(92)
+ ^(94)
+ TAB上面那个键,~(96)
+ {(123)
+ }(124)
+ |(125)

**解决方案: 添加一个配置文件即可**
```
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class RfcConfig
{
    @Bean
    public Integer setRfc()
    {
        // 指定jre系统属性，允许特殊符号， 如{} 做入参，其他符号按需添加。见 tomcat的HttpParser源码。
        System.setProperty("tomcat.util.http.parser.HttpParser.requestTargetAllow", "|{}");
        return 0;
    }
}
```

###解决freemarker后网页总是白板的问题
去maven库找到G:\apache-maven-3.5.3\LocalLib\org\springframework\boot看看有没有spring-boot-starter-freemarker的文件夹，如果没有需要手动下载jar，然后配置进去。

###深拷贝与浅拷贝
+ 基本数据类型：直接存储在栈中的数据。
+ 引用数据类型：存储的是该对象在栈中的引用，真实的数据存放在堆内存中。

浅拷贝只是复制某个对象的指针，不复制对象本身，新旧对象还是共享一块内存。而深拷贝则会另外创造一个一模一样的对象，新对象和原对象不共享内存，修改新对象，不会改到原对象。

###linux设置静态地址
```
vim /etc/sysconfig/network-scripts/ifcfg-eth1
```
修改ip地址即可
然后`service network restart`