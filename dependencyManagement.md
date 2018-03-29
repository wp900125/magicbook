# \<dependencyManagement\>
## tage
`maven`

## concept
统一控制依赖的版本

## demo

```xml
//parent pom.xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>love.llnn</groupId>
    <artifactId>mavendep</artifactId>
    <version>1.0-SNAPSHOT</version>
    <modules>
        <module>web</module>
        <module>service</module>
    </modules>
    <packaging>pom</packaging>

    <name>mavendep</name>

    <dependencyManagement>
        <!-- 片段1 start -->
        <dependencies>
            <dependency>
                <groupId>org.mybatis</groupId>
                <artifactId>mybatis</artifactId>
                <version>3.1.0</version>
            </dependency>
        </dependencies>
        <!-- 片段1 end-->
    </dependencyManagement>
</project>

//web pom.xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <parent>
        <artifactId>mavendep</artifactId>
        <groupId>love.llnn</groupId>
        <version>1.0-SNAPSHOT</version>
    </parent>
    <modelVersion>4.0.0</modelVersion>

    <artifactId>web</artifactId>
    <packaging>war</packaging>
    <name>web</name>

    <dependencies>
        <dependency>
            <groupId>love.llnn</groupId>
            <artifactId>service</artifactId>
            <version>1.0-SNAPSHOT</version>
        </dependency>
    </dependencies>
</project>


//service pom.xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <parent>
        <artifactId>mavendep</artifactId>
        <groupId>love.llnn</groupId>
        <version>1.0-SNAPSHOT</version>
    </parent>
    <modelVersion>4.0.0</modelVersion>

    <artifactId>service</artifactId>
    <packaging>jar</packaging>

    <name>service</name>

    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>

    <dependencies>
        <dependency>
            <groupId>org.mybatis</groupId>
            <artifactId>mybatis</artifactId>
            <version>3.4.0</version>
        </dependency>
    </dependencies>
</project>
```
如果存在“片段1”，web打包之后mybatis版本是3.1.0 
执行
```cmd
mvn dependency:tree

[INFO] --- maven-dependency-plugin:2.1:tree (default-cli) @ web ---
[INFO] love.llnn:web:war:1.0-SNAPSHOT
[INFO] \- love.llnn:service:jar:1.0-SNAPSHOT:compile
[INFO]    \- org.mybatis:mybatis:jar:3.1.0:compile (version managed from 3.4.0)
```
## insight

## reference
[Maven中dependencyManagement的一点点说明](https://blog.csdn.net/longly_me/article/details/52642930)
