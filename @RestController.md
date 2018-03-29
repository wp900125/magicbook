# @RestController
## concept
返回json,是@ResponseBody和@Controller的组合注解

## demo
```java
@RestController
public class HelloController {

    @RequestMapping(value="/hello",method= RequestMethod.GET)
    public String sayHello(){
        return "hello";
    }
}
```

## insight
```java
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
@Documented
@Controller
@ResponseBody
public @interface RestController {

	/**
	 * The value may indicate a suggestion for a logical component name,
	 * to be turned into a Spring bean in case of an autodetected component.
	 * @return the suggested component name, if any
	 * @since 4.0.1
	 */
	String value() default "";

}
```
## reference
[SpringBoot 中常用注解@Controller/@RestController/@RequestMapping介绍](https://blog.csdn.net/u010412719/article/details/69710480)
