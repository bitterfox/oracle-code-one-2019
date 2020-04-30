# Code One Community Keynote: Game On [KEY1108] (09:15 〜 10:30) @ Moscone North - Hall F
- お遊戯会

# Condy? NestMates? Constable? Understanding JDK11 and JDK12s JVM Features [DEV3407] (11:30 〜 12:15) @ Moscone South - Room 205
- Nestmate
  - Accecssing private field from outer class was actually bridge method(with ACC_SYNTHETIC) invocation
  - Difference of accesibility for private between JVM Spec and Lang Spec
    - JVM: accessable by same class
    - Lang: accessable by same or nested classes
  - Considering reflection
    - access private member of inner from outer via reflection
      - IAccessException occur
  - Introduce Nestmates attribute
    - For JVM to know nestmate relationship and accept private access from outer to inner
    - New Reflection methods
      - getNestHost, getNestMembers, isNestmateOf
    - Update reflection access rules
  - Etc
    - invokevirtual, invokeinterface can target private methods
      - bytecode generator are happy to reduce checking calling method is private or not
  - Future plan
    - dinamy nestmate: add a class into nestmate relationthip at runtime
      - more variety of feature for bytecode generation
- condy
  - indy
    - bytecode generator can choose invocation rules
    - rules for other invocation bytecode are fixed by JVM
    - Can be used to return some constant, but there is a overhead
      - Callsite -> MethodHandle -> Constant
  - condy is something like indy to return constant
    - No Callsite, MethodHandle
    - So less overhead to archive it using indy
  - ConstantPool
    - Null, Enum constants, primitive type class are not accepted in ConstantPool
    - Pass those as String to Callsite in past
    - ConstantBootstraps has methods for those usecases(???)
  - Usecases
    - JDK8186216
      - Condy for non captureing lamba
    - JEP303: http://openjdk.java.net/jeps/303
      - lazy initialization using condy?
      - defining constantpool entries from java code
      - "Below the Fold", BrianGoetz@JVMLS 2018
  - VarHandle
- JVM Constable API
  - API for JVM constant pool symbols
  - ConstantDesc
  - Constable
  - dynamicContantDesc
  - Future
    - JVM can return ConstantDesc

# Java/JDBC Scalability and Asynchrony: Reactive Extension and Fibers [DEV6323] (12:30 〜 13:15) @ Moscone South - Room 308
- ADBA(Async DB Access) is dead
  - No one care about ADBA
- Fiber(Loom)
- Oracle DB JDBC drivers are Fiber-Ready
  - 20c is Fiber-Ready
- Async extention in Oracle DB JDBC library

# The Lean, Mean... OpenJDK? [DEV4996] (13:30 〜 14:15) @ Moscone South - Room 304
- Performance
  - Throughput, Latency, Footprint, Startup
- Jigsaw improved Footpring
 - In JDK9, there is startup regression by Jigsaw
  - However, improved it and in jdk11, wins than JDK8
- Lambda
  - Using lambda in JDK8 causes bad startup time by overhead of lambda
  - JDK-8198418
  - Improving across 8 to 13, finally a few of overhead
- Compact String
  - Improved footpring and throughput
  - 2.9x better throughput, 6.4x less garbage
- Indy string concat
  - Slow string concat in JDK9, because of bootstrapping invokedynamic string concatation
  - Improved in jdk13
- G1GC improvement
  - In JDK 13, G1GC is small bad throughput than parallel
  - Startup time when using G1GC was improved in JDK13/9?
  - 3%~10% penalty on throughput(common)
- ZGC
  - Startup time might be slower than Parallel, G1
    - No CompressedOops, CDS, and so on currently
- AppCDS
  - 2x improvement on startup time
    - 20%~50%
  - -XX:ArchiveClassesOnExit=hoge.jsa
  - -XX:SharedArchiveFile=hoge.jsa
  - Improvement on footpring on startup
    - no bytecode verification
- AoT and Graal JIT

# You Can Write a Garbage Collector for HotSpot in 30 Minutes Too [DEV1587] (14:30 〜 15:15) @ Moscone South - Room 206
- What is best GC policy
  - next one under development

# Enhancing the Garbage Collector in Java SE 11 and 12 [TRN6116] (15:45 〜 16:30) @ Moscone West - Room 3007C
- GC Basis
- G1
  - snapshot-at-the-beginning
  - String deduplication
    - new String("hoge")
    - After young collection, refer same cahr[](not string object)
  - concurrent class unloading
  - Eagerly reclaim humongous regions
    - Remove humongous regions when young collection if such regions are referred only from the young regions
      - There're index from old region to old regions
  - Adaptive start of conccurent mark
    - 11, G1UseAdaptiveIHOP(default: enabled)
- ZGC


# Simplifying NVIDIA GPU Access: A Polyglot Binding for GPUs with GraalVM [DEV6097] (18:00 〜 18:45) @ Moscone South - Room 314

