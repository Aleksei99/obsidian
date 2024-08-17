#creation_date:  2024-08-17 09:45
#modification_date: Saturday 17th August 2024 09:45:43
> [!quote] Living at risk is jumping off the cliff and building your wings on the way down.
> — Ray Bradbury
# Adding headers to feign requests
#Feign, #headers, #config
## Description 
- Configure default encoder and decoder
- Configure [[ErrorDecoder]]
- Creating `RequestInterceptor` bean to intercept all feign requests before sending. And populate them with our request headers.
### Code example 
```java 

@Bean  
public Decoder decoder() {  
    return new JacksonDecoder();  
}  
  
@Bean  
public Encoder encoder() {  
    return new JacksonEncoder();  
}  
  
@Bean  
public ErrorDecoder errorDecoder() {  
    return new FeignErrorDecoder();  
}

@Bean  
public RequestInterceptor requestInterceptor() {  
    return template -> {  
        RequestAttributes requestAttributes = RequestContextHolder.getRequestAttributes();  
        if (requestAttributes != null) {  
            final HttpServletRequest httpServletRequest = ((ServletRequestAttributes) requestAttributes).getRequest();  
            Enumeration<String> headerNames = httpServletRequest.getHeaderNames();  
            for (Iterator<String> it = headerNames.asIterator(); it.hasNext(); ) {  
                String header = it.next();  
                if(header.equals("content-length")){ // fixes sending big objets 
                    continue;  
                }  
                template.header(header, httpServletRequest.getHeader(header));  
            }  
        }  
    };  
}
```

![[Feign usage]]