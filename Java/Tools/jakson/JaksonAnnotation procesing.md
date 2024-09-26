#creation_date:  2024-09-26 18:27
#modification_date: Thursday 26th September 2024 18:27:18
Error generating daily quote

# JaksonAnnotation procesing
#JaksonAnnotation procesing

> [!DESCRIPTION] 
> This Java code defines a custom annotation `@JsonMask` and a serializer `MaskDataSerializer` that masks sensitive data when serializing objects using Jackson, a popular JSON processing library. 
### Code example 
```java 
@Retention(RetentionPolicy.RUNTIME)  
@Target(ElementType.FIELD)  
@JacksonAnnotationsInside  
@JsonSerialize(using = MaskDataSerializer.class)  
public @interface JsonMask {  
  
  String replaceRegExp() default "";  
  
  String replaceWith() default "*";  
}

@NoArgsConstructor  
@AllArgsConstructor  
public class MaskDataSerializer extends JsonSerializer<String> implements ContextualSerializer {  
  
  private String replaceRegExp;  
  private String replaceWith;  
  
  @Override  
  public void serialize(String value, JsonGenerator gen, SerializerProvider serializers)  
      throws IOException {  
    String maskedValue = maskValue(value);  
    gen.writeString(maskedValue);  
  }  
  
  @Override  
  public JsonSerializer<?> createContextual(SerializerProvider prov, BeanProperty property) {  
    if (property != null && property.getAnnotation(JsonMask.class) != null) {  
      JsonMask maskData = property.getAnnotation(JsonMask.class);  
  
      return new MaskDataSerializer(maskData.replaceRegExp(), maskData.replaceWith());  
    }  
    return this;  
  }  
  
  private String maskValue(String value) {  
    if (value == null) return null;  
  
    if (!StringUtils.isEmpty(replaceRegExp)) {  
      return value.replaceAll(replaceRegExp, replaceWith);  
    }  
    return value;  
  }  
}
```


> [!INFO]
> - **`@JacksonAnnotationsInside`**: Tells Jackson that this custom annotation will internally use Jackson annotations (like `@JsonSerialize`).
> - **`@JsonSerialize(using = MaskDataSerializer.class)`**: Specifies that the `MaskDataSerializer` class should handle the serialization of fields annotated with `@JsonMask`.
> - **`@JsonSerialize(using = MaskDataSerializer.class)`**: Specifies that the `MaskDataSerializer` class should handle the serialization of fields annotated with `@JsonMask`.
    
