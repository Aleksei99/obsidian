#creation_date:  2024-08-11 00:32
#modification_date: Sunday 11th August 2024 00:32:27
> [!quote] Get busy living or get busy dying.
> — Stephen King
#### GC (Garbage Collection) Algorithms
- **Overview**: Automatic memory management feature in Java that reclaims memory occupied by unreachable objects.
- **Common Algorithms**:
  - **Serial GC**:
    - Single-threaded collector.
    - Suitable for small applications.
    - `-XX:+UseSerialGC`
  - **Parallel GC** (Throughput Collector):
    - Uses multiple threads for garbage collection.
    - Suitable for multi-threaded applications.
    - `-XX:+UseParallelGC`
  - **CMS (Concurrent Mark-Sweep) GC**:
    - Aims for low pause times.
    - Uses multiple threads to scan the heap and mark objects for garbage collection.
    - `-XX:+UseConcMarkSweepGC`
  - **G1 (Garbage First) GC**:
    - Divides the heap into regions and performs garbage collection within these regions.
    - Aims to achieve high throughput with low pause times.
    - `-XX:+UseG1GC`
  - **ZGC (Z Garbage Collector)**:
    - Designed for low latency and high scalability.
    - Handles heaps ranging from a few hundred megabytes to several terabytes.
    - `-XX:+UseZGC`
