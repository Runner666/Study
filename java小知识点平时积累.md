1、关于y=++x和y=x++的问题  

	int y,x;  
	y=++x;  
本质上的运算：  

	int temp=x;  
	temp=temp+1;  
	x=temp;  
	y=x;

    y=x++;  
本质上的运算：  

	y=x;
	int temp=x;
	temp=temp+1;
	x=temp;


4、哪项技术可以用在WEB开发中实现会话跟踪实现？  
Cookie和session配合使用，通过验证cookie来跟踪会话，cookie是由服务器创建，保存在客户端的硬盘和服务器中；  重写URL；  
隐藏域（表单的input里属性写成hide类型）

5、哈希表：散列表（Hash table，也叫哈希表），是根据关键码值(Key value)而直接进行访问的数据结构。也就是说，它通过把关键码值映射到表中一个位置来访问记录，以加快查找的速度。这个映射函数叫做散列函数，存放记录的数组叫做散列表。
给定表M，存在函数f(key)，对任意给定的关键字值key，代入函数后若能得到包含该关键字的记录在表中的地址，则称表M为哈希(Hash）表，函数f(key)为哈希(Hash) 函数。

我的理解：哈希表就是存储给定值的计算出来的关键码值，真正的值存储在关键码值指向的地址里

6、1）无论如何，Integer与new Integer不会相等。不会经历拆箱过程；  
2）两个都不是new出来的Integer，如果数在-128到127之间，则是true,否则为false，java在编译Integer i02 = 128的时候,被翻译成-> Integer i2 = Integer.valueOf(128);而valueOf()函数会对-128到127之间的数进行缓存；  
3）两个都是new出来的Integer,都为false ；  
4）int和integer(无论new与否)比，都为true，因为会把Integer自动拆箱为int再去比较。

7、集合常考点：  
1）list和set都继承自collection  
2）list存储的元素有顺序，值可以相同；set元素无顺序，值不能重复  
3）Vector是线程安全的，ArrayList不是线程安全的  
4）hashMap不是线程安全的，key-value允许null值；hashtable是线程安全的，key-value不允许为空

8、Java中的byte，short，char进行计算时都会提升为int类型。

9、StringString(大姐，出生于JDK1.0时代) 不可变字符序列     <StringBuffer(二姐，出生于JDK1.0时代)  线程安全的可变字符序列    <StringBuilder(小妹，出生于JDK1.5时代) 非线程安全的可变字符序列

10、重载和重写的一些知识点：重载（overload）只要方法名一致、参数列表不同，其他（返回值）怎么折腾随便；重写（overriding）只有实现的功能代码 不一致 ，其他的（函数名、参数列表、返回值类型）必须都一致。

11、静态变量只能在类主体中定义，不能在方法中定义

12、json对象要求属性必须加双引号，例如：{“name”:小张}

13、抽象类中可以包含非抽象的普通方法，接口中的方法必须是抽象的，不能有非抽象的普通方法（但是接口中可以默认不写public abstract，）

14、关闭浏览器意味着会话ID丢失，但所有与原会话关联的会话数据仍保留在服务器上，直至会话过期