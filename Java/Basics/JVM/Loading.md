#creation_date:  2024-08-11 12:51
#modification_date: Sunday 11th August 2024 12:51:55
> [!quote] Give whatever you are doing and whoever you are with the gift of your attention.
> — Jim Rohn

### Loading

The Class loader reads the `.class` file, generates the corresponding binary data, and saves it in the method area. For each `.class` file, the JVM stores the following information in the method area:

- The fully qualified name of the loaded class and its immediate parent class.
- Whether the `.class` file is related to a Class, Interface, or Enum.
- Modifier, Variables, and Method information, etc.

After loading the `.class` file, the JVM creates an object of type `Class` to represent this file in the heap memory. Please note that this object is of type `Class` predefined in the `java.lang` package. This `Class` object can be used by the programmer for obtaining class-level information such as the name of the class, parent name, methods, and variable information, etc. To get this object reference, we can use the `getClass()` method of the `Object` class.
