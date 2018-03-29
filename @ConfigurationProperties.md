# @ConfigurationProperties
## concept
把properties或者yml配置直接转成对象

## demo
```
server:  
  port: 8080  
  
spring:   
  redis:   
    dbIndex: 0  
    hostName: 192.168.58.133  
    password: nmamtf  
    port: 6379  
    timeout: 0  
    poolConfig:   
      maxIdle: 8  
      minIdle: 0  
      maxActive: 8  
      maxWait: -1  
```
```java
@Configuration    
@EnableAutoConfiguration  
public class RedisConfig {  
      
    @Bean    
    @ConfigurationProperties(prefix="spring.redis.poolConfig")    
    public JedisPoolConfig getRedisConfig(){    
        JedisPoolConfig config = new JedisPoolConfig();  
        return config;    
    }    
        
    @Bean    
    @ConfigurationProperties(prefix="spring.redis")    
    public JedisConnectionFactory getConnectionFactory(){    
        JedisConnectionFactory factory = new JedisConnectionFactory();    
        factory.setUsePool(true);  
        JedisPoolConfig config = getRedisConfig();    
        factory.setPoolConfig(config);    
        return factory;    
    }    
        
        
    @Bean    
    public RedisTemplate<?, ?> getRedisTemplate(){    
        RedisTemplate<?,?> template = new StringRedisTemplate(getConnectionFactory());    
        return template;    
    }    
      
}  
```
## insight

## reference
[ref1](https://blog.csdn.net/guduyishuai/article/details/70879952)
