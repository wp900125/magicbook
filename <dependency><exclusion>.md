# \<dependency\>\<exclusion\>
## tags
`maven`
## concept
依赖过滤

## demo
```xml
<dependency>    
  <groupId>org.apache.hbase</groupId>
  <artifactId>hbase</artifactId>
  <version>0.94.17</version> 
  <exclusions>  
     <exclusion>	 
       <groupId>commons-logging</groupId>		
       <artifactId>commons-logging</artifactId>  
     </exclusion>  
  </exclusions>  
</dependency>
```
```xml
<dependency>
  <groupId>org.apache.hbase</groupId>
  <artifactId>hbase</artifactId>
  <version>0.94.17</version>
  <exclusions>
    <exclusion>
      <groupId>*</groupId>
      <artifactId>*</artifactId>
    </exclusion>
  </exclusions>
</dependency>
```
## insight

## reference
[Maven依赖排除 禁止依赖传递 取消依赖的方法](https://blog.csdn.net/jiesa/article/details/51777455)
