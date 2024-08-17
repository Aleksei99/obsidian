#creation_date:  2024-08-17 11:42
#modification_date: Saturday 17th August 2024 11:42:10
> [!quote] Heedfulness is the path to the Deathless. Heedlessness is the path to death. The heedful die not. The heedless are as if already dead.
> — The Buddha

# Embeddable
#Embeddable, #Jpa, #DB

> [!DESCRIPTION] 
> The `@Embeddable` annotation is used to specify that a class can be embedded in another entity. The fields of the `@Embeddable` class will be mapped as columns of the entity that embeds it. This is typically used when you want to reuse the same set of fields across multiple entities or when you want to encapsulate a group of related fields into a single class. 
### Code example 
```java 
@Embeddable
public class ConsultationFollowUp {  
  
    @NotNull  
    @Size(min = 2, max = 30, message = "PatientIssue length should be between 2 and 30 characters.")  
    @Pattern(regexp = RE20, message = "Invalid patientIssue format.")  
    private String patientIssue;  
    @NotNull  
    @Size(min = 2, max = 450, message = "Recommendations length should be between 2 and 450 characters.")  
    @Pattern(regexp = RE21, message = "Invalid recommendations format.")  
    private String recommendations;  
    @OneToMany(mappedBy = "appointmentRecord")  
    private List<LabTest> labTests;  
  
}
```