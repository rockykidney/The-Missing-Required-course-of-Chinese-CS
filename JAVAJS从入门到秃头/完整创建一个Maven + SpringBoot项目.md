## 一、前言

---

　　偶然发现，网上介绍Maven+SpringBoot的项目都有挺多的，偏有些五花八门，现在我就来说上一说。

  

## 二、Maven和SpringBoot的介绍与作用

---

### 1.Maven是什么？Maven的介绍与作用

  

　　`Maven`是一个项目管理工具，对`Java项目`能够进行构建，同时依赖管理。简单点说，就是你的`Java项目`缺点啥工具，在`pom.xml`文件里添加上依赖，`Maven`去找，找到了并且下载下来（拿过来），然后就能用了。

  

　　大白话：`Maven`就是一个工具箱，能够你完善你的小作品、大作品，你需要啥工具，告它一下，呐，你就拿去用吧！

  

### 2.SpringBoot是什么？SpringBoot的介绍与作用

  

　　`SpringBoot`是`Spring`超强化版，`Spring`是一种框架，Java平台上的一种开源应用框架。它可以是你Java项目的小地基，你的小作品的内容介绍目录。

  

　　大白话：`SpringBoot`是`Spring`加强版的框架，又加多了很多工具合成于自身。本来Spring配置是需要加上`Tomcat`完成Web项目的，但是SpringBoot的话，是已经把`Tomcat`合并一块。

  

## 三、它们两者之间的关系

---

　　首先，`SpringBoot`只是一个很好辅助开发的框架，相当于一个很好的工具。因此，我们要先有工具箱啊，没有工具箱哪来的工具呢。

  

　　话不多说，我们先简单卷起来一下，搞个简单的项目（Maven+SpringBoot）。

  

## 四、搞一个简单的Maven + SpringBoot项目

---

### Eclipse版

  

**创建Maven项目**

依次点击——》File——》New Maven Project

  

![微信截图_20220519181927.png](https://ucc.alicdn.com/pic/developer-ecology/e37e3be0bf544f3b897fa4313d135766.png "微信截图_20220519181927.png")

  

Next——》

  

![微信截图_20220519181941.png](https://ucc.alicdn.com/pic/developer-ecology/0ac3079cf0374b7384f8e9958fba1922.png "微信截图_20220519181941.png")

  

填写Group Id、Arifact Id——》Finish

  

![微信截图_20220519181954.png](https://ucc.alicdn.com/pic/developer-ecology/1730ab9afd424e389a6ed8fb3d8c52b8.png "微信截图_20220519181954.png")

  

成功创建`Maven`项目，查看`pom.xml`文件

**![微信截图_20220519182007.png](https://ucc.alicdn.com/pic/developer-ecology/f98033c152e84f6f85e74754946a109f.png "微信截图_20220519182007.png")**

**添加SpringBoot框架**

这里我就会很简单、粗暴。

  

直接在pom文件添加上`parent`便签和`开发web项目需要依赖`便签

`<parent>标签`（`project标签`下）

  

<!-- 继承SpringBoot父级项目提供的依赖 -->
    <parent>        <groupId>org.springframework.boot</groupId>        <artifactId>spring-boot-starter-parent</artifactId>        <version>2.2.6.RELEASE</version>        <relativePath />    </parent>

  

`<dependency>标签`（`dependencies标签`下）

  

<!-- springboot 开发web项目需要的依赖 -->
         <dependency>            <groupId>org.springframework.boot</groupId>            <artifactId>spring-boot-starter-web</artifactId>        </dependency>

  

**完整的pom.xml文件**

<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">    <modelVersion>4.0.0</modelVersion>    <groupId>com.nanfangzhe</groupId>    <artifactId>anpai-demo</artifactId>    <version>0.0.1-SNAPSHOT</version>    <packaging>jar</packaging>    <name>anpai-demo</name>    <url>http://maven.apache.org</url>    <properties>        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>    </properties>    <!-- 继承SpringBoot父级项目提供的依赖 -->    <parent>        <groupId>org.springframework.boot</groupId>        <artifactId>spring-boot-starter-parent</artifactId>        <version>2.2.6.RELEASE</version>        <relativePath />    </parent>    <dependencies>        <!-- springboot 开发web项目需要的依赖 -->        <dependency>            <groupId>org.springframework.boot</groupId>            <artifactId>spring-boot-starter-web</artifactId>        </dependency>        <dependency>            <groupId>junit</groupId>            <artifactId>junit</artifactId>            <version>3.8.1</version>            <scope>test</scope>        </dependency>    </dependencies>
</project>

  

添加后，可能要等待Maven库更新一会。

  

**完善启动类（App.java的操作）**

添加`@SpringBootApplication`注解

主方法（main方法）中添加`SpringApplication.run(App.class, args);`**App.java的完整代码**

package com.nanfangzhe.anpai_demo;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
/**
 * Hello world! * */
@SpringBootApplication
public class App {
    public static void main(String[] args) {        System.out.println("Hello World!");        SpringApplication.run(App.class, args);    }
}

  

**成功结果**——》启动项目——》成功展示结果

  

![微信截图_20220519182029.png](https://ucc.alicdn.com/pic/developer-ecology/3869fa961bc64a1baa333b7db0d3bf9d.png "微信截图_20220519182029.png")

  

## 文章小尾巴

---

文章写作、模板、文章小尾巴可参考：[《写作“小心思”》](https://juejin.cn/post/7041996365487931423)

  

　　感谢你看到最后，最后再说两点~

  

　　①如果你持有不同的看法，欢迎你在文章下方进行留言、评论。

　　②如果对你有帮助，或者你认可的话，欢迎给个小点赞，支持一下~

  

　　**[我是南方者，一个热爱计算机更热爱祖国的南方人。](https://link.juejin.cn?target=https%3A%2F%2Fnanfangzhe.gitee.io%2F)**

  

　　（文章内容仅供学习参考，如有侵权，非常抱歉，请立即联系作者删除。）