# Error decoder
#Feign , #config 
## Description 
Creating default error decoder 
### Code example 
```java 
public class FeignErrorDecoder implements ErrorDecoder {  
  
    private final ErrorDecoder errorDecoder = new Default();  
  
    @Override  
    public Exception decode(String methodKey, Response response) {  
        return errorDecoder.decode(methodKey, response);  
    }  
}
```