#creation_date:  2025-01-03 15:03
#modification_date: Friday 3rd January 2025 15:03:31
Error generating daily quote
#rabbit #compose #docker 

```yml
rabbitmq:
    image: 'rabbitmq:3.10.7-management'
    environment:
      - 'RABBITMQ_DEFAULT_PASS=secret'
      - 'RABBITMQ_DEFAULT_USER=myuser'
    ports:
      - '5672:5672'
      - '15672:15672'
```

