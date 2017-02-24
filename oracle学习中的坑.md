1.oracle登录：  
以管理员身份登录：

	在命令行里输入：sqlplus  /  as  sysdba;
2.修改管理员sys密码:

	alter user  sys identified by newpassword;
3.Navicat连接oracle数据库报错：ORA-2854：connection to server failed,probable Oracle Net admin error  
>原因：oci.dll版本不对。因为Navicat是通过Oracle客户端连接Oracle服务器的，Oracle的客户端分为两种，一种是标准版，一种是简洁版，即Oracle Install Client。而我们用Navicat时通常会在自己的安装路径下包含多个版本的OCI，如果使用Navicat连接Oracle服务器出现ORA-28547错误时，多数是因为Navicat本地的OCI版本与Oracle服务器服务器不符造成的。  
>解决办法：下载OCI使之与我们所安装的Oracle服务器（版本号）相符合。解压下载的文件，在Navicat客户端里修改OCI的路径（工具--选择--OCI:将OCI library指向刚解压出来的OCI文件）
[OCI下载地址](http://www.oracle.com/technetwork/database/features/instant-client/index-097480.html)

4.PL/sql下切换用户：connect username;根据提示输入口令。（连接管理员：connect sys / as sysdba;）

5.账号：scott 密码:tiger   账号:system 密码:manager  账号:sys  密码:任意字符
>我们一般使用的是用scott登录sysdba，这时候有可能出现账户未解锁的状态，这时候可以在sys用户下执行

	alter user scott account unlock;
	
>来解锁账户。解锁之后可能会要求你改密码：可以用

	alter user scott identified by tiger;
>再登录

	conn scott/tiger;

6.查询表结构:desc 表名

7.字符串和字符串连接
>Java中的字符串使用""，oracle中字符串使用''，例如'123'
>Java中字符串连接是 + 号 ,oracle中字符串连接是 || 号
>需求：查员工的姓名和月薪, 数据的显示格式如下   
>姓名: SMITH，月薪:800
	
	select '姓名:'||ename || ',月薪:' || sal as ename_sal from emp
	
>如果字符串中本身就有’，想显示这个单引号,需要使用两个单引号进行转义,即’’代表‘
>例如想显示 员工姓名 连接上 123’4 需要使用如下sql语句

	select ename||'123''4' from emp
	
8.事务之COMMIT/ROLLBACK  
数据库事务起始于SQL语句，终止于以下4种事件之一：  
>1、COMMIT或ROLLBACK语句  
>2、DDL/DCL隐式提交  
>3、用户退出时自动提交  
>4、系统强行关闭时取消事务事务结束后，下一条SQL语句将开始一个新的事务。

9.隐式事务提交：  
>  一个事务在下列情况下会被自动提交:DDL语句 DCL语句;用户正常退出数据库，而缺少显式的COMMIT或者ROLLBACK.  
>  一个事务在下列情况下会被自动回退;用户异常退出数据库;系统强行关闭.
   
10.oracle数据库可以用create or replace的对象有：functions, procedures, packages, types, synonyms, trigger and views，就是没有table，也没有sequence。

11.SQL Select语句完整的执行顺序:  
>1、from子句组装来自不同数据源的数据；  
>2、where子句基于指定的条件对记录行进行筛选；  
>3、group by子句将数据划分为多个分组；  
>4、使用聚集函数进行计算；  
>5、使用having子句筛选分组；  
>6、计算所有的表达式；  
>7、select 的字段；  
>8、使用order by对结果集进行排序。
