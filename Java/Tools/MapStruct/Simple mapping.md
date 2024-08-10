#creation_date:  2024-08-10 15:03
#modification_date: Saturday 10th August 2024 15:20:03
> [!quote] Time is the most valuable thing a man can spend.
> — Theophrastus
# Object mapping 
#Mapper, #Mapping
## Description 
How to map two objects with **the same** and **different** field names of the same data type 
### With the same names
```java 
@Mapper(componentModel = "spring")  
public interface BankDetailsMapper {  
  
    BankDetailsDto toDto(BankDetails bankDetails);  
  
}
```

### With different names or from other internal object
```java 
@Mapper(componentModel = "spring")  
public interface DoctorMapper {  
    @Mapping(target = "firstName",source = "user.firstName")  
    @Mapping(target = "lastName",source = "user.lastName")  
    DoctorDetailsDto toDoctorDetailsDto(Doctor doctor);  
}
```
- target - `DoctorDetailsDto`
- source - `Doctor`

#### [[Complex mapping]]
