#creation_date:  2024-08-17 10:07
#modification_date: Saturday 17th August 2024 10:07:39
> [!quote] The beginning of knowledge is the discovery of something we do not understand.
> — Frank Herbert
# Feign Client
#Feign , #FeignClient
## Description 
How to use feign to get/send data from/to other ms 
### Code example 
```java 
@FeignClient(name = "notification-microservice", url = "${APP.SERVER.URL}:8150/api/v1/email", configuration = FeignConfiguration.class)  
public interface NotificationMicroserviceClient {  
  
    @PostMapping(path = "/send", produces = "application/json")  
    boolean sendDataToEmail(@RequestBody EmailRequest emailRequest);  
}
```