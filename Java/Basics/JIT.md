#creation_date:  2024-08-11 00:34
#modification_date: Sunday 11th August 2024 00:34:44
> [!quote] Freedom is what you do with what's been done to you.
> — Jean-Paul Sartre
#### JIT (Just-In-Time) Compilation
- **Overview**: Part of the JVM that improves the performance of Java applications by compiling bytecode into native machine code at runtime.
- **Types of JIT Compilers**:
  - **Client Compiler (C1)**:
    - Optimizes for quick startup time.
    - Suitable for desktop applications.
  - **Server Compiler (C2)**:
    - Optimizes for long-running applications.
    - Performs more aggressive optimizations.
- **How it Works**:
  - When a Java method is called frequently, the JVM compiles it into native code.
  - This compiled code is then used for subsequent calls, improving execution speed.
- **HotSpot JVM**: Uses adaptive optimization, which involves interpreting bytecode initially and then compiling "hot" code paths into native code as needed.