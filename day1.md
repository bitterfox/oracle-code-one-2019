# JDK Mission Control: Where We Are, Where We Are Going [DEV4284] (09:00 〜 09:45) @ Moscone South - Room 301
Skipped to keep better seat for keynote

# Java Keynote: The Future of Java Is Now [KEY1099] (10:00 〜 12:00) @ Moscone North - Hall F
TODO

# Open Source Java-Based Tools: Hacking on Cool Open Source Projects [DEV6544] (12:30 〜 13:15) @ Moscone South - Room 314
My session

# The Quest for the Language GraalVM: One JVM to Rule Them All [DEV1646] (13:30 〜 14:15) @ Moscone South - Room 202
Skipped for lunch

# Reactive Performance on GraalVM [DEV1878] (14:30 〜 15:15) @ Moscone South - Room 201
  - Reactive Streams is 95% performance of Java Stream
  - 5x slower than for-loop
  - Lifecycle
    - Publisher -> Subscriber <-> Subscription (Reactive)
    - Operation (Java Stream)
    - Nothing (for-loop)
  - There're object overhead
    - 15%~3%(so on) overhead: depends on N elements
  - Method call overhead
    - Many stacks of method invocation
      - Hit to max calls of inlining
  - Optimization basis
    - Object escape
    - Inlining
    - Profiling
      - 分岐予測
    - Partial Escape Analysis
  - Graal
    - GrallEE is 1.5~2x faster than JDK8 for Reactive
    - GraalCE is 1.1x faster
  - Etc
    - C2 vs Graal CE/EE are small difference when small object allocations(ex. Netty)

# Choosing Right Garbage Collector to Increase Efficiency of Java Memory Usage [BOF2061] (16:00 〜 16:45) @ Moscone South - Room 210
  - G1PeriodicGcInterval=ms
    - Run G1GC collection every N ms
    - G1PeriodicGCSystemLoadThreashold
    - ZCollectionInterval, ZUncommitDelay
  - (ハズレ)
    - They focus on reduce java committing memory size in container to reduce fee by pay-as-use in cloud
    - They mention nothing about choosing by performance

# JavaFX 12 and Beyond [DEV4112] (17:00 〜 17:45) @ Moscone South - Room 202
  - Removed from JDKs(Unplugged)
    - Download SDK and put it on module path
    - Download JMODs
    - maven dependencies
  - JavaFX12
    - Enhancement Skining and Extending TableView
    - Image smoothing
    - JMC, JFR support
    - WebView FileReader API
  - JavaFX13
    - NIO BUffer-backed WritableImage
      - Don't copy pixels array
    - Point 2D/3D implements interpolatable
      - Helps implementing timeline of animating
  - Contribution
    - Github mirror
    - Project Skara
      - They're moving to git(hub) based development + Additional automation by tools for their requirement like checking OCA

# Groundbreakers Unconference [UNC1101] (19:00 〜 22:00) @ Moscone South (Level 3) - The Terrace
