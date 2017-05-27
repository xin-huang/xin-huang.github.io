---
layout: post
title: Optimization in Java
date: 2017-05-14
category: notes
tags: [Programming]
use_math: true
---

Here, I record several notes for optimizing performance of Java programs.

<!-- more -->

## Read/Write data

In my daily work, a usual task is to parse data from a big file. I usually read data as String and use `String.split()` to parse data. However, this approach is slow, because a pattern is built repeatly inside `String.split()`. To speed up, we can build the pattern first and use `Pattern.split()`. A faster way is to use `StringTokenizer`, which would return tokens according to the given String and delimiter. The fastest way I found is to use `String.IndexOf()` to find out the indices of delimiters, and use `String.substring()` to extract data between two delimiters.

Java provides two packages for reading and writing data: `java.io` and `java.nio`. In `java.io`, we can use `InputStream`/`OutputStream` for reading/writing binary data, such as zipped files. And we use reader/writer for character data, such as text files. It is important to set buffer size for reading/writing data fast. According to [Java Performance: The Definitive Guide](https://www.safaribooksonline.com/library/view/java-performance-the/9781449363512/), always use a `BufferedInputStream`/`BufferedOutputStream` to wrap the underlying file stream for file-based I/O using binary data; and always wrap the underlying stream with a `BufferedReader`/`BufferedWriter` for file-based I/O using character data. Another package `java.nio` provides non-blocking mode for reading/writing data, which means a thread will not become idle when it does reading/writing tasks but haven't got data. Sometimes this mode will increase great performance than blocking mode. According to Javarevisited, the fastest way for reading/writing data in Java is [memory mapped file](http://javarevisited.blogspot.com/2012/01/memorymapped-file-and-io-in-java.html) using `RandomAccessFile`, `FileChannel` and `ByteBuffer` in `java.nio`.

## Concurrency

As our computers get more and more cores, we can gain more computation power from muliple cores, though it is harder to write multiple-threading programs. We should take care of threading hazards, such as deadlock, thread starvation and race conditions. At first, I tried [AKKA](http://akka.io/), which applies the Actor Model successfully in many applications. After building AKKA for two hours and failed, I gave up and returned to concurrency utilities in Java.

Java provides many concurrency utilities:
- Executor framework
- Synchronizer
- Concurrent collections
- Locks
- Atomic variables
- Fork/Join framework
- Parallel stream

## Profiler

Usually, I want to know how long my program runs and how much memory it consumes. A naive approach to obtain these information is use some functions provided in Java, such as `System.currentTimeMillis()`, `System.nanoTime()`. However, this approach can only provide rough estimations of performance. A more precise way is to use [HProf](http://docs.oracle.com/javase/7/docs/technotes/samples/hprof.html), a built-in tool in JDK for profiling. However, it is not easy to trace information provided by this profiler.

Finally, I found [JProfiler](https://www.ej-technologies.com/products/jprofiler/overview.html) is simple to use with good visualization. It can monitor both local and remote JVMs. This is conveinient for me to test my programs in our server. I think a good profiler is like a good teacher, which can quickly and clearly point out where the problem is, and would save my valuable time.

## Benchmark

For me, there are two reasons for benchmark:

1. To improve performance of my applications;
2. To display performance of my applications precisely and robustly.

However, benchmarking in Java is difficult because the dynamics of JVM components, such as the interpreter, the garbage collector and the JIT-complier. We cannot know how exactly our codes work at runtime. Daniel Mitterdorfer listed several [flaws and dangers of Java microbenchmarks](http://daniel.mitterdorfer.name/articles/2014/benchmarking-flaws/). To overcome these problems, we can use a framework called [JMH](http://openjdk.java.net/projects/code-tools/jmh/) for benchmark.

I followed [Jakob Jenkov](http://tutorials.jenkov.com/java-performance/jmh.html) to start my first JMH benchmark. After build up `target/benchmarks.jar`, we can change the settings, such as benchmark modes and time units, of JMH using command line. To get the help information, use `java -jar target/benchmarks.jar -h`. To avoid some part of codes being measured, we can use benchmark state classes and state variables. There are some rules for writing good benchmarks:

1. Avoiding loops in benchmark methods in general.
2. Avoiding dead code elimination using `return` or `blackhole.consume()`.
3. Avoiding constant folding using state classes.

To learn more examples of JMH benchmarks, we can see the samples in [JMH offical site](http://hg.openjdk.java.net/code-tools/jmh/file/tip/jmh-samples/src/main/java/org/openjdk/jmh/samples/).

[Cruftex.net](https://cruftex.net/2017/03/28/The-6-Memory-Metrics-You-Should-Track-in-Your-Java-Benchmarks.html) proposed six memory metrics in Java benchmarks.

## Build tools

- [Gradle](https://gradle.org/)
- [Maven](https://maven.apache.org/)