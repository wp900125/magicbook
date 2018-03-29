# profile
## tags
`maven`
## concept
定义一系列的配置信息，然后指定其激活条件

## demo
```xml
<profiles>
    <profile>
        <!-- 本地开发环境 -->
        <id>dev</id>
        <properties>
            <profiles.active>dev</profiles.active>
        </properties>
        <activation>
            <!-- 设置默认激活这个配置 -->
            <activeByDefault>true</activeByDefault>
        </activation>
    </profile>
    <profile>
        <!-- 发布环境 -->
        <id>release</id>
        <properties>
            <profiles.active>release</profiles.active>
        </properties>
    </profile>
    <profile>
        <!-- 测试环境 -->
        <id>beta</id>
        <properties>
            <profiles.active>beta</profiles.active>
        </properties>
    </profile>
</profiles>
```
```cmd
mvn package –Pdev
```
## insight

## reference
[maven profile动态选择配置文件](https://www.cnblogs.com/0201zcr/p/6262762.html)
