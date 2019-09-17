# Java Shell: Replacing Native OS Scripting with Power [TUT1329] (08:45 〜 10:45) @ Moscone South - Room 305
  - Use JShell OS shell scripting
    - + crossplatform
    - - overhead by JVM
    - - More code than OS scripting language
  - Greping
    - performance
      - 33 secs by windows shell script
      - 27 secs by linux shell script on VM
      - 35 secs by jshell-based scripting on Linux on VM
  - More complex scripting
    - Java is extream faster than bash
  - ハズレ
    - 2時間のセッションが20分で終わった・・・

# Java Language Futures: 2019 Edition [DEV5937] (11:30 〜 12:15) @ Moscone South - Room 203
- Keeping compatibility at language level
  - but it takes longer development for new language feature, ex generics -> planed in 1.3, 1.4, finally released in 1.5
  - Waiting until get right answer is good idea when implement language feature beacause it's forever once implemented
  - Language feature for solve programming problem and it's on new hardware
  - Adopting language feature development to 6 month release cycle
    - Need many feedback to make laguage feature right
    - Add preview feature
  - LVTI(JDK10)
    - Able to declare variable with the type we cannot write it before
    - Make bad developer writing bad code by LVTI? -> no. In addition, new language feature enable us to good code
  - Switch Expr.(JDK12)
    - switch expression(yield-able value)
    - enhancement case(case xxx,yyy -> ...)
  - Text Blocks(JDK13)
    - content is between """ and """
    - Eliminate spaces before the content hulisticly
    - When develop new language feature, they adopt it to usecase and customize language feature, so there're N different behavior for N languages for same language feature
  - Records
    - record Point(int x, int y) {}
  - Sealed Types
    - ???
  - Pattern matching
   - instanceof + casting
     - might be solved by flow typing, but it's complicated
     - obj instanceof Integer invValue
     - ```
       euqlas(Object o) {return (o instanceof T t) && this.size == t.size};
       ```
     - With switch stat. and expr
   - Matching to Record type + Sealed Types

# Lets Talk About Communities [BOF3992] (12:30 〜 13:15) @ Moscone South - Room 305

# G1 and ZGC: A Look into the Progress of Garbage Collection in Java [DEV4459] (13:30 〜 14:15) @ Moscone South - Room 304
- G1
  - Parallel Full GC in JDK10
  - changes more than JDK10 in JDK11
  - Rebuild remembered set on the fly: improve latency and throughput
  - Abortable Mixed GCs
    - Improve bad latency by choosing wrong regions to be collected
  - 10% throughput improvement in JDK11 from JDK 8
- ZGC
  - Allocation Rate > Collection Rate => Allocation Stall
    - To avoid this
      - Generate less garbage
      - Collect garbage faster
        - ZGC move some processes in GC into application thread
  - Barrier
    - Other GCs uses write barriers, but ZGC uses read bariers == Move GC tasks into application thread
    - ~4% execution overhead by testing load barrier thanks by CPU predictive branch
  - Tuning
    - Increase heap size or GC threads
  - JDK 13
    - Increase max heap size to 16TB
  - Future plan
    - Stability
  - Potential improvements
    - Segmented array clearing (clear to 0 by parallel)
    - Improvements are in not only GC, but also JVM

# Oracle Code One Keynote [KEY6320] (14:30 〜 16:30) @ Moscone North - Hall F
# Whats New in the Java Language and Tooling [DEV4681] (17:00 〜 17:45) @ Moscone South - Room 301
# Cross-Platform Development with GraalVM [DEV3907] (18:00 〜 18:45) @ Moscone South - Room 301
# Groundbreakers Unconference [UNC1104] (19:00 〜 22:00) @ Moscone South (Level 3) - The Terrace
