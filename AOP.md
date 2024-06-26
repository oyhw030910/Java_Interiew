## AOP

### 1.描述一下AOP

AOP全称为面向切面编程，是对OOP的补充，其主要被用来做一些统一重复代码的实现，如日志等，AOP中主要有以下几个概念

1. 切面Aspect：通知和切点的集合，是AOP的主体
2. 连接点：待切入的函数
3. 通知：指切入时机
4. 切入点：连接点的集合，通常用表达式匹配
5. 引入：添加方法 DeclareParents
6. 目标对象：被aspect通知的对象

### 2.通知种类

1. 前置通知 Before
2. 后置通知 After
3. 围绕通知 Around
4. 返回之后通知 After Returning
5. 抛出异常通知 After Throwing

后置通知可以看做是4,5的集合版

### 3.代理

静态代理，直接修改字节码

动态代理，在内存中临时为方法生成一个AOP对象，这个对象包括目标的全部方法，并在切点部分做了增强

目前有两种主流的动态代理模式：jdk和cglib

jdk：通过反射来实现代理，要求被代理的类必须实现一个接口

cglib：通过继承来实现代理

Spring中若被代理对象实现了接口，那么默认使用jdk代理，如果没有实现接口，那么默认使用cglib。