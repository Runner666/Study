#### 一、该搭建方式是采用vue-cli脚手架进行的开发环境的搭建，使用该方式搭建做如下准备：

1.安装nodeJs，在这个过程中会顺带安装npm（nodeJs环境下的包管理器）  

2.为了提升后续开发中下载模块的速度，可以安装npm的淘宝镜像：  

    npm install -g cnpm --registry=https://registry.npm.taobao.org  
    
3.安装webpack(编译工具)：  

    [c]npm install webpack -g  
    
4.安装vue-cli：  

    [c]npm install vue-cli -g  

#### 二、正式开始使用vue-cli搭建项目

1.使用vue脚手架搭建

    vue init webpack project-name

2.控制台会有如图所示参数配置的步骤
![vue-cli参数配置](Picture/vue-cli_to_init_project.png)
