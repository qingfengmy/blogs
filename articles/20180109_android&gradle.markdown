### 1. gradle-wrapper.properties
文件位置：
```
当前项目/gradle/wrapper/gradle-wrapper.properties
```
项目内容：
```
distributionBase=GRADLE_USER_HOME
distributionPath=wrapper/dists
zipStoreBase=GRADLE_USER_HOME
zipStorePath=wrapper/dists
distributionUrl=https\://services.gradle.org/distributions/gradle-2.14.1-all.zip
```
android studio启动时，会根据.properties的配置文件，先在本地gradle库中寻找，没有就会去distributionUrl下载。

而本地默认的gradle库，在`C:\Users\Administrator\.gradle`目录下，如果配置环境变量，key为`GRADLE_USER_HOME`,value为其他路径，则gradle库就在其他路径下。

gradle有很多版本，查看这些版本可以查看:http://services.gradle.org/distributions/

gradle plugin和gradle不是一个东西，gradle plugin依赖gradle，他也有自己的版本号，他是android自己用gradle写的插件，他的版本号可以查看：
```
buildscript {
    repositories {
        jcenter()
        mavenCentral()
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:2.2.0'// 
        classpath 'com.neenbedankt.gradle.plugins:android-apt:1.8'
    }
}
```
