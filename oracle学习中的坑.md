1.oracle登录：  
以管理员身份登录：

	在命令行里输入：sqlplus  /  as  sysdba;
2.修改管理员sys密码:

	alter user  sys identified by newpassword;
3.Navicat连接oracle数据库报错：ORA-2854：connection to server failed,probable Oracle Net admin error  
原因：oci.dll版本不对。因为Navicat是通过Oracle客户端连接Oracle服务器的，Oracle的客户端分为两种，一种是标准版，一种是简洁版，即Oracle Install Client。而我们用Navicat时通常会在自己的安装路径下包含多个版本的OCI，如果使用Navicat连接Oracle服务器出现ORA-28547错误时，多数是因为Navicat本地的OCI版本与Oracle服务器服务器不符造成的。  
解决办法：下载OCI使之与我们所安装的Oracle服务器（版本号）相符合。  
[OCI下载地址：](http://www.oracle.com/technetwork/database/features/instant-client/index-097480.html)
