一 Tomcat服务器
===========

 - **简介**
 
    apache下开源的项目，在JavaWeb中做服务器。 ---[官网地址][1]
		[1]: www.apache.org

 - **作用**
 
    接收客户端请求，相应结果。

 - **项目结构**
    
    * bin
    * lib
    * conf
    * temp
    * webapps
    * work
    * logs
    
    > 其中要注意的是conf为tomcat的配置目录里面存放了两个中要的配置文件，server.xml 和 web.xml

    > 修改端口号、增加虚拟主机等在 server.xml 中进行修改，web.xml 中存放的是一些 MIME 类型的说明文档，是客户端与服务器之间说明文档类型的。
    
    
 - **注意事项**

    > Tomcat服务器安装分为两种，一种为解压版，一种为安装版；要想使用它们需要增加相应的环境变量，Java_Home,catalina_home Tomcat的安装依赖于Java。

    > Tomcat 的默认端口号为：8080 （容易冲突）

 - **具体操作**
    
    > 开启和关闭tomcat服务，在 bin 目录下进行操作 startup 和 showdown 文件！

二 JavaWeb目录结构及相关文件
==================

- **一个JavaWeb项目的目录结构：**

  - WEB-INF

        - classes

        - lib

        - web.xml

- **Web.xml中相关文件的说明**
    
    * 指定当前访问当前项目的第一个页面，可以按照顺序依次查找。
    ```
    <welcome-file-list>

        <welcome-file> [页面名称] </welcome-file> 
                    ...

    </welcome-file-list>
    
    ```
- **说明：**