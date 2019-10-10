MYSQL登陆：
-D		打开指定数据库
-h		服务器名称（本地回环地址：127.0.0.1）
-p		密码
-P		端口号（默认端口号：3306）
-u		用户名
-V		输出版本信息并退出

进入数据库：mysql  -u  root  -p

MYSQL退出：
mysql > exit;
mysql > quit;
mysql > \p;

MYSQL常用命令：
显示当前服务器版本：SELECT  WERSION();
显示当前日期：SELECT  NOW();
显示当前用户：SELECT  USER();

MYSQL语句规范：
关键字与函数名称全部大写
数据库名称，表名称，字段名称全部小写
sql语句必须以分号结尾

创建数据库:	CREATE	{DATABASE|SCHEMA}	 [IF NOT EXISTS]	 db_name
查看数据库列表：SHOW {DATABASES|SCHEMAS}
修改数据库：ALTER  {DATABASE|SCHEMAS}  [db_name]
删除数据库：DROP {DATABASE|SCHEMAS} [IF EXISTS] db_name
打开数据库：USE  db_name
显示当前打开的数据库：SELECT DATABASE();

创建表：CREATE TABLE [IF NOT EXISTS] table_name(
		column_name data_type,
		...
		)
例：
	CREATE TABLE tb1(
	username VARCHAR(20),
	age TINYINT UNSIGNED,
	salary FLOAT(8,2) UNSIGNED       //整个有8位，小数点后有两位
	);

查看数据表：SHOW TABLES [FROM db_name];
查看数据表结构：SHOW COLUMNS FROM tb_name;


删除一条记录： DELETE FROM tb_name WHERE 条件

1.MySQL服务准备:
    a.安装完成之后修改配置文件my.ini,[client]与[mysqld]下修改default-character-set = gbk
    b.然后设置环境变量,Path:;%MySQL_HOME%\bin;
    c.操作mysql服务:
      启动:net start mysql
      关闭:net stop mysql
      卸载:sc delete mysql 

2.登陆MySQL:mysql -h 主机名 -u 用户名 -p 回车 输入密码.

3.使用某一个数据库:
  use db_name 或者
  mysql -h 主机名 -D db_name -u 用户名 -p 回车 输入密码.(增加一个-D)

4.执行某SQL脚本:< MySQL.sql ("<"即为执行脚本操作)

5.修改root用户密码:mysqladmin -u -p old_password new_password

6.MySQL有三种数据类型:
    数字类型:tinyint,smallint.mediumint,int,bigint
    日期类型:date,time,datetime,year,timestamp
    字符串类型:char, varchar,(tinytext, text, mediumtext, longtext)
    
    
创建数据库:create database db_name character set gbk;
删除数据库:drop database db_name;
查看数据库:
  查看所有数据库:show databases
  查看当前用户打开的数据库:select database();
修改数据库:
  //修改默认字符集
  alter database db_name
  character set = gbk;
  //改名
  rename database db_name_old
  to db_name_new;
  
  创建数据表:
  create table students(
    sname varchar(10) NOTNULL,
    sage tingint null,
    sid varchar(5) primary key auto_increment
  );

删除数据表:
drop students;

查看数据表:
  查看所有数据表:show tables;
  查看当前数据表:describe students;

mysql修改表名，列名，列类型，添加表列，删除表列 
alter table test rename test1; --修改表名 
alter table test add  column name varchar(10); --添加表列 
alter table test drop  column name; --删除表列 
alter table test modify address char(10) --修改表列类型 
alter table test change address address  char(40) 
alter table test change  column address address1 varchar(30)--修改表列名

  
原型数据表:
create table [if not exit] students(
  sname varchar(10) notnull,
  sid varchar(5) notnull primary key auto_increment,
  ssex enum("男", “女”) default 0
);

增加数据记录:
  //一次插入一条完整的记录，default可以省略
  insert into students 
  values("张三", "0001", "女");

  //插入记录的一部分.
  insert into students 
  (sname) values ("李四")
 

查看数据记录
  select * 
  from students
  where sname="李四";

  select sname, ssex
  from students
  where sid="0001";

修改数据记录
update students
set sid = "00002"
where sid = "00001";//不加查询操作将对所有数据记录进行操作

删除数据记录:
delete from tbl_name WHERE 要删除的记录
  
  查询条件:where [条件];
  1.'='、‘>’、'>='、'!='等
  2.or、and连接字句
  3.is null、in、like、is not null

eg:
select *
from students
where sid="00001" or ssex="1";

select *
from students
where sname like %李% and ssex="1"

sesect *
from students
where name in("李四", "王五");

根据指定的列对输出进行排序:order by 
eg:

select *
from students
order by sname;
//sname 是字符型，故将按照字母进行排序

select *
from students
order name desc;
//desc指的是降序,asc指升序


insert插入语句无法输入中文时，在安装目录下
在my.ini里找到sql- mode='STRICT_TRANS_TABLES,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION'把其中 的STRICT_TRANS_TABLES,去掉
或者把sql- mode=STRICT_TRANS_TABLES,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION注释掉，
然 后重启mysql就ok了”

显示数据库编码： show create database t_name;
改变编码：set names utf8;
改变数据库编码：alter database lhms character set utf8;

1.在安装数据库的过程中将默认的拉丁文-->GBK。
2.在创建数据库时设置选择GBK或者gb2312。
3.Mysql安装目录下的my.ini文件，将 "default-character-set=xxxxx" 中的xxxxx改成GBK或者gb2312。
4.Mysql安装目录下的\data\databasename(数据库名)\db.opt文件打开
default-character-set=gbk
default-collation=gbk_chinese_ci; 如果上面不是gbk和gbk_chinese_ci则改成支持中文的GBK或者gb2312。
5.进入Mysql的dos命令下:进入某数据库后 show full columns from tablename ;查看数据类型，如果不是支持中
文的类型则执行alter table tablename convert to character set gbk 。
6.在创建数据库时(用命令创建时)create database databasename CHARACTER SET gbk;不显示

无法插入中文或不显示汉字可参考：http://www.2cto.com/database/201410/341144.html

默认约束：age  tinyint default 20;
性别用enum：
create table t (
    id int auto_increment primary key,
    sex enum('F', 'M'),
    name varchar(20) not null
);


当在Mysql下删除有一个建有外键的表的数据时可能会报此异常，所以可以启动MySql命令行模式，运行如下的sql语句来关闭外键检测：
SET FOREIGN_KEY_CHECKS = 0;
执行你要的操作后把再把外键检测恢复
SET FOREIGN_KEY_CHECKS = 1;
其他相关的有：
关闭唯一性校验
set unique_checks=0;
set unique_checks=1;

TRUNCATE table1;              //在清除数据

###mysql一行记录太长换行了，不想换行则在查询语句后，分号之前加入\G