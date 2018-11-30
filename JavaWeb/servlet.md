一 Servle简介
=============

- 定义：
        
    > JavaWeb的三大组件之一，存在于服务器端的小程序，服务器中进行对客户端的请求进行处理的类．
        
- 功能：
        
    > 接收请求
    
    > 处理请求
    
    > 完成响应
    
- 特点：

    > Servlet是单例，服务器端只会创建一次，所以它是线程不安全的,在Servlet中不应该添加成员。
       
二 Servlet的实现方式
===================

- 一共有三种：
    
    > 实现javax.servlet.Servlet接口
    
    > 继承javax.servlet.GenericServlet类
    
    > 继承javax.servlet.HttpServlet类

- 实现方式：
    
    > 一般采用继承HttpServlet的方式来实现，因为请求的方式都和http有关。
    
- Servlet接口：

    * void init(ServletConfig);
    * void service(ServletRequset,ServletResponse);
    * void destory();
    
    > **说明：**以上三个方法为servlet接口中的三个生命周期方法，其中init和destory只会调用一次，但是每次请求都会调用service方法，所以与响应相关的逻辑操作全部放在里面进行。每个Servlet类型只会创建一个实例对象，对象由tomcat服务器为我们自动创建，创建的时间为第一次请求servlet或者开启服务器时创建（此种方式需要进行在web.xml中进行相关配置）;在服务器关闭时，会先调用destory方法在再销毁相关的servlet对象。
    
- GenericServlet类：
    
    * void init();
    * void init(ServletConfig config);
    
    > **说明:**该类实现了Servlet接口并且还是实现了ServletConfig接口，其中init()方法为该类自己的方法，而init(ServletConfig config)是重写的Servlet接口中的init方法，因为在该类中存在一个config成员对象如果继承它的类重写了该方法，那么该类中的其他方法都不能使用该对象了，所以想做一些初始化操作，直接重写init()方法即可。
    
- HttpServlet类：
    
    * void service(HttpServletRequest req,HttpServletResponse resp);
    * void service(ServletRequest req,ServletResponse resp);
    
    > **说明：**该类继承自GenericServlet，它提供了对Http请求的特殊支持，并且service(HttpServletRequest req,HttpServletResponse resp)为该类自己的方法，它会把ServletRequest，ServletResponse强转为HttpServletRequest,HttpServletResponse并调用继承的service方法，并且在该方法中还会判断请求的方法，并执行响应的方法doGet和doPost方法，所以我们继承它之后，要重写相应的方法，不然会出现405。
    