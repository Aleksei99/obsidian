#creation_date:  2024-10-31 16:17
#modification_date: Thursday 31st October 2024 16:17:00
Error generating daily quote

# AOP
#AOP #EnableAspectJAutoProxy

> [!DESCRIPTION] 
> - `@Pointcut` - The method annotated with `@Pointcut` serves as a pointcut signature, and it must have a `void` return type. This is the annotation which tells what to observe
> - `@Around` - is used to create advice that surrounds a join point, such as a method invocation. This type of advice is the most powerful because it allows you to control the method execution completely, including modifying the input, altering the return value, or even skipping the method execution altogether.
### Code example 
```java 
@Aspect  
public class ServiceAspect {  
  
  @Pointcut("within(@org.springframework.stereotype.Service *)")  
  public void serviceBeans() {}  
  
  @Around("serviceBeans()")  
  public Object logService(ProceedingJoinPoint joinPoint) throws Throwable {  
    return LoggingUtil.logMethod(joinPoint);  
  }  
}
```
So this can be done for other annotations or whatever you want

```java
@Configuration
@EnableAspectJAutoProxy  
public class AopConfiguration {  
  @Bean  
  @ConditionalOnProperty(prefix = "service-logging", name = "enabled", havingValue = "true")  
  public ServiceAspect serviceAspect() {  
    return new ServiceAspect();  
  }
 // other beans here ... 
}
```

#### Usefull UtilityClass for logging
#logging

```java
@Slf4j  
@UtilityClass  
public class LoggingUtil {  
  
  public static Object logMethod(ProceedingJoinPoint joinPoint) throws Throwable {  
    MethodSignature methodSignature = (MethodSignature) joinPoint.getSignature();  
    String method = methodSignature.toShortString();  
    Object[] args = joinPoint.getArgs();  
    String params = Arrays.toString(args);  
    log.info("Enters on method: {}, with params: {}", method, params);  
  
    try {  
      Object result = joinPoint.proceed();  
      log.info("Exiting method {} with return {}", method, result);  
      return result;  
    } catch (Throwable e) {  
      log.error("Exception in method {}", method, e);  
      throw e;  
    }  
  }  
}
```