## gradle
官网: https://gradle.org
参考书:《实战gradle》
### 1.install
https://gradle.org/install
#### 1.1 要求
java版本8以上
```bash
$ java -version
java version "17.0.4.1"
```

#### 1.2 安装
##### 1.2.1 下载
去下载自己喜欢的版本 https://gradle.org/releases
##### 1.2.2 解压
```bash
$ mkdir /opt/gradle
$ unzip -d /opt/gradle gradle-7.5.1-bin.zip
$ ls /opt/gradle/gradle-7.5.1
LICENSE  NOTICE  bin  getting-started.html  init.d  lib  media
```
##### 1.2.3 配置PATH
```bash
 $ export PATH=$PATH:/opt/gradle/gradle-7.5.1/bin
 ```
##### 1.2.4 验证
```bash
$ gradle -v

------------------------------------------------------------
Gradle 7.5.1
------------------------------------------------------------
```
### 2.常用Command-Line Interface
https://docs.gradle.org/current/userguide/command_line_interface.html
gradle [taskName...] [--option-name...]
一些option的形式 `--console=plain`用`=`设置值；`--build-cache`开启cache，用`--no-build-cache`关闭cache; 用`-h`简写形式代替`--help`
运行task
```bash
gradle taskname 
gradle task1 task2 # 执行多个task
gradle task1 --exclude-task task2 # 在task执行链上，exclude一个task，可以用-x代替--exclude-task
gradle init # 初始化一个gradle项目
gradle clean # 清空build目录
gradle classes # 编译业务代码和配置文件
gradle test # 编译测试代码，生成测试报告
gradle build # 构建项目
```
使用`gradle tasks`查看所有可执行的task
<html xmlns="http://www.w3.org/1999/xhtml">
<body>
<pre>
<span style="font-weight:bold;">$ gradle tasks</span>
<span style="font-weight:bold;">&gt; Configure project :</span>
config helloworld task


<span style="font-weight:bold;">&lt;-------------&gt; 0% EXECUTING [32ms]</span><span style="font-weight:bold;">&gt; :tasks</span>
<span style="font-weight:bold;">&gt; Task :tasks</span>

<span style="font-weight:bold;">------------------------------------------------------------</span>
<span style="font-weight:bold;">Tasks runnable from root project 'hello-world'</span>
<span style="font-weight:bold;">------------------------------------------------------------</span>

<span style="font-weight:bold;">Build Setup tasks</span>
<span style="font-weight:bold;">-----------------</span>
<span style="color:green;">init</span><span style="color:olive;"> - Initializes a new Gradle build.</span>
<span style="color:green;">wrapper</span><span style="color:olive;"> - Generates Gradle wrapper files.</span>

<span style="font-weight:bold;">Help tasks</span>
<span style="font-weight:bold;">----------</span>
<span style="color:green;">buildEnvironment</span><span style="color:olive;"> - Displays all buildscript dependencies declared in root project 'hello-world'.</span>
<span style="color:green;">dependencies</span><span style="color:olive;"> - Displays all dependencies declared in root project 'hello-world'.</span>
<span style="color:green;">dependencyInsight</span><span style="color:olive;"> - Displays the insight into a specific dependency in root project 'hello-world'.</span>
<span style="color:green;">help</span><span style="color:olive;"> - Displays a help message.</span>
<span style="color:green;">javaToolchains</span><span style="color:olive;"> - Displays the detected java toolchains.</span>
<span style="color:green;">outgoingVariants</span><span style="color:olive;"> - Displays the outgoing variants of root project 'hello-world'.</span>
<span style="color:green;">projects</span><span style="color:olive;"> - Displays the sub-projects of root project 'hello-world'.</span>
<span style="color:green;">properties</span><span style="color:olive;"> - Displays the properties of root project 'hello-world'.</span>
<span style="color:green;">resolvableConfigurations</span><span style="color:olive;"> - Displays the configurations that can be resolved in root project 'hello-world'.</span>
<span style="color:green;">tasks</span><span style="color:olive;"> - Displays the tasks runnable from root project 'hello-world'.</span>

To see all tasks and more detail, run <span style="font-weight:bold;">gradle</span><span style="font-weight:bold;"> </span><span style="font-weight:bold;">tasks --all</span>

To see more detail about a task, run <span style="font-weight:bold;">gradle</span><span style="font-weight:bold;"> </span><span style="font-weight:bold;">help --task &lt;task&gt;</span>

<span style="font-weight:bold;color:green;">BUILD SUCCESSFUL</span> in 521ms
1 actionable task: 1 executed


<span style="font-weight:bold;">&lt;-------------&gt; 0% WAITING</span><span style="font-weight:bold;">&gt; :tasks</span></pre>
</body>
</html>

### 3.gradle wrapper
![](imgs/the_wrapper_flow.png "the wrapper flow")
```bash
gradle wrapper
> Task :wrapper

BUILD SUCCESSFUL in 0s
1 actionable task: 1 executed
```
将当前的gradle打包到gradle/wrapper/gradle-wrapper.jar，其他下载这个项目的人就能使用你我们相同的gradle版本构建项目。当然，我们需要把这个jar包放到版本控制库中。
详情见：https://docs.gradle.org/current/userguide/gradle_wrapper.html#sec:adding_wrapper