**1、环境变量配置**  

用鼠标右击“我的电脑”->属性->高级->环境变量
JAVA_HOME ：D:\Program Files\Java\jdk1.6.0_12(JDK安装路径)
Path ：%JAVA_HOME%\bin;（若已经有Path项，无须另外新建，直接在后面加，但需用;与前面已有的项分隔开）
CLASSPATH ：.;%JAVA_HOME%\lib;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;
其中“.”表示当前路径
测试环境变量是否设置成功：运行->cmd->输入javac

**2.path和classpath的作用**  

运行路径path变量记录的是各个程序所在的路径，系统根据这个变量的值来查找运行程序（各种命令），使得在运行的时候不用输入全路径名。  
类路径classpath环境变量通常用来记录当前路径和java类库所在的路径。在类库中包含java系统所提供的各种软件包，其中包括各个类和接口等