#creation_date:  2024-08-17 11:12
#modification_date: Saturday 17th August 2024 11:12:41
> [!quote] I can't imagine a person becoming a success who doesn't give this game of life everything he's got.
> — Walter Cronkite
# SuperBuilder
#lombok, #SuperBuilder, #Builder

> [!DESCRIPTION]
>  A feature that extends the capabilities of the `@Builder` annotation to support inheritance and complex object hierarchies in Java.
### Code example 
```java 
import lombok.experimental.SuperBuilder;

// Superclass
@SuperBuilder
public class Parent {
    private final String parentField;
}

// Subclass
@SuperBuilder
public class Child extends Parent {
    private final String childField;
}

// Usage
public class Main {
    public static void main(String[] args) {
        Child child = Child.builder()
                           .parentField("Parent value")
                           .childField("Child value")
                           .build();

        System.out.println(child);
    }
}

```

> [!INFO]
> ### Limitations:
> **Not Compatible with `@Builder`**: `@SuperBuilder` cannot be used together with `@Builder`. If you need inheritance support, you should use `@SuperBuilder` for all classes in the hierarchy.

 