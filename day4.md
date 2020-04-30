

# Building a DSL with GraalVM [DEV1124] (09:00 〜 09:45) @ Moscone South - Room 310/311
# Solving Java Memory Leaks [DEV4442] (10:00 〜 10:45) @ Moscone South - Room 203
# Hunting Down Scalability Bottlenecks in Java [DEV3217] (11:15 〜 12:00) @ Moscone South - Room 205
- Senario
  - add resource, but not get faster
- Concurrency
  - reduce latency
  - hide latency
  - increase throughput
- Scalability
  - Horizontal, Vertical
- How to check scalability
  - add some resource,
- Resouce utilization
  - doesn't tell which part of internal resource is bad
    - ex: 100% CPU utilization, missing cache?, missing cores?
- Laws
  - Amdar Law
    - There is a limit by increasing threads
  - Universal Scalability Law
    - There is a max performance by increasing threads
      - performance decrease if increasing threads too much
- HW
- SW

# Enhanced Java Flight Recorder at Alibaba [DEV3667] (12:15 〜 13:00) @ Moscone South - Room 203
- JDK in Allibaba
  - 1 million JVM instances
  - Middleware/Software on AJDK on Aliyun Linux
  - a billion lines of Java code on AJDK
- Profiling
  - HotModule
- JFR
  - Alibaba backported OSS-version of JFR in JDK11 to their AJDK 8
  - Alibaba Dragonwell GA in June 2019
  - 8u-jfr-incubator
- Motivation to extend JFR
  - GC performance(Frequency, Duration)
  - G1GC Young
    - Frequency depends on
      - allocation rate, size of eden space
    - Duration
      - size of live objects
  - JIT Deoptimization
    - High cost
    - Major causes
      - Unstable if
      - Nullcheck
      - Class check
    - Frequency
    - Printcompilation
- JFR extension
  - GC
    - Allocations inside/outside TLAB(ThreadLocalAllocationBuffer, fast)
      - If many allocation in outside, it will be slowpath because need to synchronize with other threads
        - reduce object size to be allocated
      - Useful find such cases
      - sampling
  - JMCX
    - cmd line tool to parse JFR event results
    - `jmcx flamegraph`
    - easy to find the cause of many allocation by visualization
  - JIT deoptimization
    - Do similar things to Feedback Optimization(FDO) in JVM
      - Generate deoptimization infomartion with reason at original execution
      - Use it to optimize well when next run
        - Disable speculative optimization
        - Don't optimize methods which causes many deoptimization
      - 10% cpu saving at peaktime

# JFR in Rakuten
- JFR
  - Failure management when something down
  - Low overhead
    - under 3%, log4j was 15%
- Realtime analysis
  - JFR -> JSON format by jfr tool -> fluentd -> norikra -> elasticsearch/Kibana

# Migrating Beyond Java 8
- Her opinion
  - Keep LTS on production, and test latest on CI/CD pipeline eg beta
- Jigsaw
  -
- Migration concern
  - Removals
  - minor behavior changes
- 8 -> 11
  - Security
    - Solaris -> Unix for SlarisNumericGroupPrincipal
  - AWT APIs
    - peer are removed
    - button#getPeer -> #isDisplayable
  - EE
    - jaxb
  - Thread
    - Removed destroy, stop
  - Runtime
    - getLocalizedInput/OutputStream
    - runFinalizersOnExit
    
    
# Career
- Just-in-Time learning rather than a lot learning
  - Find a problem to solve, and learn to solve it
- Mentor
  - Not a gulu, Not command
  - Ask question and help
- Our job is make a boss successfull
- Try to tell what your long term is ...
