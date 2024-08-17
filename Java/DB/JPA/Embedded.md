#creation_date:  2024-08-17 11:29
#modification_date: Saturday 17th August 2024 11:29:59
> [!quote] Love is rarer than genius itself. And friendship is rarer than love.
> — Charles Péguy
# Embedded 
#Embedded, #Jpa , #DB 

> [!DESCRIPTION] 
> The `@Embedded` annotation is used within an entity to specify that an instance of the [[Embeddable|@Embeddable]] class is to be included (or embedded) within the entity. The fields of the embedded class are mapped as if they were fields of the entity itself.

### Code example 
```java 
@Embedded  
@AttributeOverrides({  
        @AttributeOverride(name = "patientIssue", column = @Column(name = "patient_issue")),  
        @AttributeOverride(name = "recommendations", column = @Column(name = "recommendations")),  
})  
private ConsultationFollowUp consultationFollowUp;
```


![[Embeddable]]