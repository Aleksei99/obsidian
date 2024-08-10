#creation_date:  2024-08-10 15:56
#modification_date: Saturday 10th August 2024 15:56:00
> [!quote] They say that time changes things, but you actually have to change them yourself.
> — Andy Warhol
# Complex object mapping
#Mapper, #Mapping, #Named , #MappingTarget, #Context
## Description 
- How to map objects using other mappers.
- How to map objects using custom logic
### Code example (We use abstract class as we want to inject our services)
```java 
@Mapper(componentModel = "spring", uses = UsedMedicalServiceMapper.class)  
public abstract class InvoiceMapper {
	@Autowired  
	protected DoctorService doctorService;  
	@Autowired  
	protected PatientService patientService;

	@Mapping(target = "doctor", expression = "java(mapDoctor(invoiceRequest.getDoctorId(), userInfo))")  
	@Mapping(target = "patient", expression = "java(mapPatient(invoiceRequest.getPatientId(), userInfo))")  
	@Mapping(target = "bankDetails.name", expression = "java(capitalizeFirstLetter(bankDetailsDto.getName()))")  
	public abstract Invoice toEntity(InvoiceRequest invoiceRequest, @Context UserInfo userInfo);

	@Named("mapDoctor")  
	protected Doctor mapDoctor(UUID doctorId, UserInfo userInfo) {  
	    Doctor doctor = doctorService.getDoctorByIdOrElseThrow(doctorId);  
	    verifyDoctorMapping(doctorId, userInfo, doctor);  
	    return doctor;  
	}  
  
	@Named("capitalizeFirstLetter")  
	protected String capitalizeFirstLetter(String input){  
	    return input.substring(0, 1).toUpperCase() + input.substring(1);  
	}
}
```

- `uses` - for injecting other mappers, will be used with equal names like `invoice.usedMedicalService` and `invoiceRequest.getUsedMedicalService()`
- `expression` - for using custom java logic
- `@Named` - for naming of our methods to future references
- `@MappingTarget` - can be used for update your passed object