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
