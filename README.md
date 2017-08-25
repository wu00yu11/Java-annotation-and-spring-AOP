---
title: README
tags: Java Annotition,Spring AOP
---

[toc]

### 第一章 Java Annotation
Annotation (注解) 表示的是能够添加到Java源代码的语法元数据。类、方法、变量、参数、包都可以被注解，可用来将信息元数据和程序元素进行关联。

#### 作用
   - 标记作用，用于告诉编译器一些信息
   - 编译时动态处理，如动态生成代码
   - 运行时动态处理，如得到注解信息

#### 基础注解
   - @Documented：是否会保存到 Javadoc 文档中
   - @Retention：保留时间，可选值 SOURCE（源码时），CLASS（编译时），RUNTIME（运行时），默认为 CLASS，值为 SOURCE 大都为 Mark Annotation，这类 Annotation 大都用来校验，比如 Override, Deprecated, SuppressWarnings
   - @Target：可以用来修饰哪些程序元素，如 TYPE,METHOD, CONSTRUCTOR, FIELD,LOCAL_VARIABLE,PACKAGE, PARAMETER ，未标注则表示可修饰所有。
   - @Inherited： 是否可以被继承，默认为 false

#### 自定义
+ 定义
``` java
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
@Inherited
public @interface MethodInfo {
    String author() default "renhui";
    String date();
    int version() default 1;
}
```
+ 实例：

``` java
public class App {
    @MethodInfo(author = “renhui”,date = "2016/01/14", version = 1)
    public String getAppName() {
        return "demo";
    }
}
```

> (1). 通过 @interface 定义，注解名即为自定义注解名
   (2). 注解配置参数名为注解类的方法名，且：
        a. 所有方法没有方法体，没有参数没有修饰符，实际只允许 public &             abstract 修饰符，默认为 public ，不允许抛异常
        b. 方法返回值只能是基本类型，String, Class, annotation,    enumeration         或者是他们的一维数组
    c. 若只有一个默认属性，可直接用 value() 函数。一个属性都没有表示           该 Annotation 为 Mark Annotation
   (3). 可以加 default 表示默认值

### 第二章 Spring AOP


### 引用
[注解基本概念][1]
[自定义注解][2]
[注解解释器][3]


  [1]: http://www.cnblogs.com/peida/archive/2013/04/23/3036035.html
  [2]: http://www.cnblogs.com/peida/archive/2013/04/24/3036689.html
  [3]: http://www.cnblogs.com/peida/archive/2013/04/26/3038503.html