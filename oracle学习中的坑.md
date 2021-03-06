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

5.账号：scott 密码:tiger  
账号:system 密码:manager  
账号:sys  密码:任意字符
>我们一般使用的是scott登录数据库，这时候有可能出现账户未解锁的状态，这时候可以在sys用户下执行

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

12.别名中有特殊字符（空格、小括号、数字···），要用双引号括起来

13.[权限管理](http://www.cnblogs.com/shlcn/archive/2011/07/21/2112879.html)

14.创建视图语句里含有 with check option 子句时，当你操作视图时就会受到创建视图的where子句的限制。

15.varchar/varchar2/nvarchar/nvarchar2的区别和联系:  
>1)联系：
>>它们都是用来存储可变长度的字符串  
它们的值都是1~4000

>2)区别:  
>>varchar/varchar2其值表示字节  
varchar2把所有字符都占两字节处理(一般情况下)，varchar只对汉字和全角等字符占两字节  
varchar2字符要用几个字节存储，要看数据库使用的字符集  
比如GBK，汉字就会占两个字节，英文1个  
如果是UTF-8，汉字一般占3个字节，英文还是1个  
>>nvarchar/nvarchar2其值表字符  
nvarchar2中所有字符均按照2个字节计算;nvarchar中字符为中文则一般按2个字节计算，英文数字等按照一个字节计算

16.--查询各科成绩的前三名

	SELECT ZTS#,ZTSNAME,ZTCNAME,ZTSCORE,ZT.r 排名 FROM
		(SELECT SC.S# ZTS#,ST.SNAME ZTSNAME,c.Cname ZTCNAME,SC.SCORE ZTSCORE,
			dense_rank() over(partition by SC.C# order by SC.SCORE desc) r FROM SC 
			LEFT JOIN STUDENT st ON SC.S#=st.S#
			LEFT JOIN COURSE c ON SC.C#=c.C#) ZT
		WHERE ZT.r<=3;

>over:  在什么条件之上。  
partition by SC.C#:  按课程编号划分（分区）。  
order by SC.SCORE desc:  按成绩从高到低排序（使用rank()/dense_rank() 时，必须要带order by否则非法）  
rank()/dense_rank():  分级  
那么rank()和dense_rank()有什么区别呢？
>>rank():  跳跃排序，如果有两个第一级时，接下来就是第三级。  
dense_rank():  连续排序，如果有两个第一级时，接下来仍然是第二级。
