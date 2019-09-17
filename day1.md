# Keynote

# My session

# Reactive&Graal TODO
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

# Choosing Right GC TODO
  - G1PeriodicGcInterval=ms
    - Run G1GC collection every N ms
    - G1PeriodicGCSystemLoadThreashold
    - ZCollectionInterval, ZUncommitDelay
  - (ハズレ)
    - They focus on reduce java committing memory size in container to reduce fee by pay-as-use in cloud
    - They mention nothing about choosing by performance

# JavaFX13
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

