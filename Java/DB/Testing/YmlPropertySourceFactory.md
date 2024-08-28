#creation_date:  2024-08-28 09:37
#modification_date: Wednesday 28th August 2024 09:37:36
> [!quote] By believing passionately in something that does not yet exist, we create it.
> — Nikos Kazantzakis

# YmlPropertySourceFactory
#YmlPropertySourceFactory

> [!DESCRIPTION] 
> PropertySourceFactory for yml files 
### Code example 
```java 
public class YmlPropertySourceFactory implements PropertySourceFactory {  
  
    @Override  
    public @NotNull PropertySource<?> createPropertySource(String name, EncodedResource encodedResource) {  
        YamlPropertiesFactoryBean factory = new YamlPropertiesFactoryBean();  
        factory.setResources(encodedResource.getResource());  
        return new PropertiesPropertySource(Objects.requireNonNull(encodedResource.getResource().getFilename()),  
                Objects.requireNonNull(factory.getObject()));  
    }  
}
```