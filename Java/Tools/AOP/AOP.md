#creation_date:  2024-10-31 16:17
#modification_date: Thursday 31st October 2024 16:17:00
Error generating daily quote

# AOP
#AOP

> [!DESCRIPTION] 
> - `@Pointcut` - The method annotated with `@Pointcut` serves as a pointcut signature, and it must have a `void` return type. This is the annotation which tells what to observe
> - @Around - is used to create advice that surrounds a join point, such as a method invocation. This type of advice is the most powerful because it allows you to control the method execution completely, including modifying the input, altering the return value, or even skipping the method execution altogether.
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