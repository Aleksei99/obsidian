#creation_date:  2024-08-28 09:20
#modification_date: Wednesday 28th August 2024 09:20:31
> [!quote] Our strength grows out of our weaknesses.
> — Ralph Waldo Emerson


## With TestContainers
#No_Spring_Boot_testing, #Test, #liquibase, #TestContainers

> [!DESCRIPTION] 
> Code sample of how to quickly launch test on db with liquibase using TestContainers and without rising whole Spring Context
### Code example 
```java 
@ExtendWith(SpringExtension.class)  
@Testcontainers(disabledWithoutDocker = true)  
@EntityScan(basePackages = "com.andersenlab.schedulemicroservice.model.entity")  
@EnableJpaRepositories(basePackages = "com.andersenlab.schedulemicroservice.repository")

//@TestPropertySource(properties = {  
//        "spring.liquibase.enabled=true",  
//        "spring.liquibase.change-log=classpath:/db/changelog/db.changelog-master.yaml"  
//})  
@PropertySource(value = "classpath:application.yml", factory = YmlPropertySourceFactory.class)  
@ContextConfiguration(classes = TestDatabaseConfiguration.class)  
@Import(value = {  
        LiquibaseAutoConfiguration.class,  
        HibernateJpaAutoConfiguration.class  
})
public class DoctorRepositoryTest {  
  
    @Container  
    static PostgreSQLContainer<?> postgres = new PostgreSQLContainer<>("postgres:16-alpine");
    @Autowired  
DoctorRepository doctorRepository;  
  
	@Test  
	//@Sql()  here for example we can put our custom sql inserts
	void verify(){  
	    Doctor doctor = doctorRepository.findByUserId(UUID.randomUUID()).orElse(null);  
	    assertThat(doctor).isNull();  
	}
}
```

> [!INFO]
> - We can use @TestPropertySource like shown, (We CANT pass here our .yml property file)
> - Or we can use @PropertySource with our [[YmlPropertySourceFactory]]
> - `@Testcontainers(disabledWithoutDocker = true)` - disable this tests when running tests on gitlab
> - `@ContextConfiguration(classes = TestDatabaseConfiguration.class)` - Provide us with our DataSource

![[TestDatabaseConfiguration]]


## With H2
#No_Spring_Boot_testing, #Test, #h2

> [!DESCRIPTION] 
> The same as above, but we dont need @ContextConfiguration(classes = TestDatabaseConfiguration.class)  ,
> just add to @Import DataSourceAutoConfiguration.class, and change yml *file*
### Code example 
```yml 
spring:  
  datasource:  
#    driver-class-name: org.postgresql.Driver  
    driver-class-name: org.h2.Driver  
    url: jdbc:h2:mem:my-test;MODE=PostgreSQL;INIT=CREATE SCHEMA IF NOT EXISTS HEALTHCARE  
    username: sa  
    password:  
  jpa:  
    properties:  
      hibernate.default_schema: healthcare  
    database: postgresql  
    database-platform: org.hibernate.dialect.PostgreSQL10Dialect  
    hibernate:  
      ddl-auto: create-drop  
    show-sql: true
```