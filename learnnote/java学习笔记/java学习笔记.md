作用域中创建的对象循环一次就别释放，例：
while (rs.next()){
Contract cont = new Contract();
}   是可以的

resultset结果集取出数值应该在next()方法后，例
ResultSet rs=st.executeQuery();
System.out.println(rs.getString("Name"));
问题出在这里，不可以这么用
String name = "";
if(rs.next()){//或者while(rs.next()) 
   name = rs.getString("Name");
   if(name == null){
        name = "";
   }
   System.out.println(name);
} 

Statement类对象stmt创建：Statement stmt = con.createStatement();
只声明的话会指向null

字符串类型判断是否相等时要用equals方法，例
if(user.getPassword().equals(truePass) )

正则表达式：
\d：表示匹配任何数字
\D：表示匹配任意数字之外的字符
\w：表示匹配任何ASCII单字符

网址（URL）	                                                       [a-zA-z]+://[^\s]*
IP地址(IP Address)	                                               ((2[0-4]\d|25[0-5]|[01]?\d\d?)\.){3}(2[0-4]\d|25[0-5]|[01]?\d\d?)
电子邮件(Email)	                                                       \w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*
QQ号码                                                                 	[1-9]\d{4,}
HTML标记(包含内容或自闭合)	                       <(.*)(.*)>.*<\/\1>|<(.*) \/>
密码(由数字/大写字母/小写字母/标点符号组成，四种都必有，8位以上)	(?=^.{8,}$)(?=.*\d)(?=.*\W+)(?=.*[A-Z])(?=.*[a-z])(?!.*\n).*$
日期(年-月-日)	                                                       (\d{4}|\d{2})-((0?([1-9]))|(1[1|2]))-((0?[1-9])|([12]([1-9]))|(3[0|1]))
日期(月/日/年)	                                                       ((0?[1-9]{1})|(1[1|2]))/(0?[1-9]|([12][1-9])|(3[0|1]))/(\d{4}|\d{2})
时间(小时:分钟, 24小时制)	                               ((1|0?)[0-9]|2[0-3]):([0-5][0-9])
汉字(字符)	                                                               [\u4e00-\u9fa5]
中文及全角标点符号(字符)	                               [\u3000-\u301e\ufe10-\ufe19\ufe30-\ufe44\ufe50-\ufe6b\uff01-\uffee]
中国大陆固定电话号码	                                       (\d{4}-|\d{3}-)?(\d{8}|\d{7})
中国大陆手机号码	                                               1\d{10}
中国大陆邮政编码	                                               [1-9]\d{5}
中国大陆身份证号(15位或18位)	                       \d{15}(\d\d[0-9xX])?
非负整数(正整数或零)	                                       \d+
正整数                                                                    	[0-9]*[1-9][0-9]*
负整数	                                                                       -[0-9]*[1-9][0-9]*
整数	                                                                       -?\d+
小数	                                                                       (-?\d+)(\.\d+)?

java正则表达式（Invalid escape sequence (valid ones are \b \t \n \f \r \" \' \\ ) 原因:
把\全部替换成\\;

JDBC步骤：
1.加载驱动程序
2.获取数据库连接
3.通过数据库的连接操作数据库，实现增删改查

mvc:
m:model 模型层
v：view 视图层
c：control 控制层

jdbc url：jdbc:mysql://localhost:3306/test
driver:  com.mysql.jdbc.Driver

###synchronized
代表同一时刻只有一个方法可以进入到临界区，同时它还可以保证共享变量的可见性。

###java运行
![](https://raw.githubusercontent.com/nanfengchuiyeluo6/images/master/java运行.jpg)