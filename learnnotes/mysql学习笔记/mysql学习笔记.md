MYSQL��½��
-D		��ָ�����ݿ�
-h		���������ƣ����ػػ���ַ��127.0.0.1��
-p		����
-P		�˿ںţ�Ĭ�϶˿ںţ�3306��
-u		�û���
-V		����汾��Ϣ���˳�

�������ݿ⣺mysql  -u  root  -p

MYSQL�˳���
mysql > exit;
mysql > quit;
mysql > \p;

MYSQL�������
��ʾ��ǰ�������汾��SELECT  WERSION();
��ʾ��ǰ���ڣ�SELECT  NOW();
��ʾ��ǰ�û���SELECT  USER();

MYSQL���淶��
�ؼ����뺯������ȫ����д
���ݿ����ƣ������ƣ��ֶ�����ȫ��Сд
sql�������ԷֺŽ�β

�������ݿ�:	CREATE	{DATABASE|SCHEMA}	 [IF NOT EXISTS]	 db_name
�鿴���ݿ��б�SHOW {DATABASES|SCHEMAS}
�޸����ݿ⣺ALTER  {DATABASE|SCHEMAS}  [db_name]
ɾ�����ݿ⣺DROP {DATABASE|SCHEMAS} [IF EXISTS] db_name
�����ݿ⣺USE  db_name
��ʾ��ǰ�򿪵����ݿ⣺SELECT DATABASE();

������CREATE TABLE [IF NOT EXISTS] table_name(
		column_name data_type,
		...
		)
����
	CREATE TABLE tb1(
	username VARCHAR(20),
	age TINYINT UNSIGNED,
	salary FLOAT(8,2) UNSIGNED       //������8λ��С���������λ
	);

�鿴���ݱ�SHOW TABLES [FROM db_name];
�鿴���ݱ�ṹ��SHOW COLUMNS FROM tb_name;


ɾ��һ����¼�� DELETE FROM tb_name WHERE ����

1.MySQL����׼��:
    a.��װ���֮���޸������ļ�my.ini,[client]��[mysqld]���޸�default-character-set = gbk
    b.Ȼ�����û�������,Path:;%MySQL_HOME%\bin;
    c.����mysql����:
      ����:net start mysql
      �ر�:net stop mysql
      ж��:sc delete mysql 

2.��½MySQL:mysql -h ������ -u �û��� -p �س� ��������.

3.ʹ��ĳһ�����ݿ�:
  use db_name ����
  mysql -h ������ -D db_name -u �û��� -p �س� ��������.(����һ��-D)

4.ִ��ĳSQL�ű�:< MySQL.sql ("<"��Ϊִ�нű�����)

5.�޸�root�û�����:mysqladmin -u -p old_password new_password

6.MySQL��������������:
    ��������:tinyint,smallint.mediumint,int,bigint
    ��������:date,time,datetime,year,timestamp
    �ַ�������:char, varchar,(tinytext, text, mediumtext, longtext)
    
    
�������ݿ�:create database db_name character set gbk;
ɾ�����ݿ�:drop database db_name;
�鿴���ݿ�:
  �鿴�������ݿ�:show databases
  �鿴��ǰ�û��򿪵����ݿ�:select database();
�޸����ݿ�:
  //�޸�Ĭ���ַ���
  alter database db_name
  character set = gbk;
  //����
  rename database db_name_old
  to db_name_new;
  
  �������ݱ�:
  create table students(
    sname varchar(10) NOTNULL,
    sage tingint null,
    sid varchar(5) primary key auto_increment
  );

ɾ�����ݱ�:
drop students;

�鿴���ݱ�:
  �鿴�������ݱ�:show tables;
  �鿴��ǰ���ݱ�:describe students;

mysql�޸ı����������������ͣ���ӱ��У�ɾ������ 
alter table test rename test1; --�޸ı��� 
alter table test add  column name varchar(10); --��ӱ��� 
alter table test drop  column name; --ɾ������ 
alter table test modify address char(10) --�޸ı������� 
alter table test change address address  char(40) 
alter table test change  column address address1 varchar(30)--�޸ı�����

  
ԭ�����ݱ�:
create table [if not exit] students(
  sname varchar(10) notnull,
  sid varchar(5) notnull primary key auto_increment,
  ssex enum("��", ��Ů��) default 0
);

�������ݼ�¼:
  //һ�β���һ�������ļ�¼��default����ʡ��
  insert into students 
  values("����", "0001", "Ů");

  //�����¼��һ����.
  insert into students 
  (sname) values ("����")
 

�鿴���ݼ�¼
  select * 
  from students
  where sname="����";

  select sname, ssex
  from students
  where sid="0001";

�޸����ݼ�¼
update students
set sid = "00002"
where sid = "00001";//���Ӳ�ѯ���������������ݼ�¼���в���

ɾ�����ݼ�¼:
delete from tbl_name WHERE Ҫɾ���ļ�¼
  
  ��ѯ����:where [����];
  1.'='����>����'>='��'!='��
  2.or��and�����־�
  3.is null��in��like��is not null

eg:
select *
from students
where sid="00001" or ssex="1";

select *
from students
where sname like %��% and ssex="1"

sesect *
from students
where name in("����", "����");

����ָ�����ж������������:order by 
eg:

select *
from students
order by sname;
//sname ���ַ��ͣ��ʽ�������ĸ��������

select *
from students
order name desc;
//descָ���ǽ���,ascָ����


insert��������޷���������ʱ���ڰ�װĿ¼��
��my.ini���ҵ�sql- mode='STRICT_TRANS_TABLES,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION'������ ��STRICT_TRANS_TABLES,ȥ��
���߰�sql- mode=STRICT_TRANS_TABLES,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTIONע�͵���
Ȼ ������mysql��ok�ˡ�

��ʾ���ݿ���룺 show create database t_name;
�ı���룺set names utf8;
�ı����ݿ���룺alter database lhms character set utf8;

1.�ڰ�װ���ݿ�Ĺ����н�Ĭ�ϵ�������-->GBK��
2.�ڴ������ݿ�ʱ����ѡ��GBK����gb2312��
3.Mysql��װĿ¼�µ�my.ini�ļ����� "default-character-set=xxxxx" �е�xxxxx�ĳ�GBK����gb2312��
4.Mysql��װĿ¼�µ�\data\databasename(���ݿ���)\db.opt�ļ���
default-character-set=gbk
default-collation=gbk_chinese_ci; ������治��gbk��gbk_chinese_ci��ĳ�֧�����ĵ�GBK����gb2312��
5.����Mysql��dos������:����ĳ���ݿ�� show full columns from tablename ;�鿴�������ͣ��������֧����
�ĵ�������ִ��alter table tablename convert to character set gbk ��
6.�ڴ������ݿ�ʱ(�������ʱ)create database databasename CHARACTER SET gbk;����ʾ

�޷��������Ļ���ʾ���ֿɲο���http://www.2cto.com/database/201410/341144.html

Ĭ��Լ����age  tinyint default 20;
�Ա���enum��
create table t (
    id int auto_increment primary key,
    sex enum('F', 'M'),
    name varchar(20) not null
);


����Mysql��ɾ����һ����������ı������ʱ���ܻᱨ���쳣�����Կ�������MySql������ģʽ���������µ�sql������ر������⣺
SET FOREIGN_KEY_CHECKS = 0;
ִ����Ҫ�Ĳ�������ٰ�������ָ�
SET FOREIGN_KEY_CHECKS = 1;
������ص��У�
�ر�Ψһ��У��
set unique_checks=0;
set unique_checks=1;

TRUNCATE table1;              //���������

###mysqlһ�м�¼̫�������ˣ����뻻�����ڲ�ѯ���󣬷ֺ�֮ǰ����\G