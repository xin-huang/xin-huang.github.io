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

## Parsing String

In my daily work, a usual task is to parse data from a big file. I usually read data as String and use `String.split()` to parse data. However, this approach is slow, because a pattern is built repeatly inside `String.split()`. To speed up, we can build the pattern first and use `Pattern.split()`. A faster way is to use `StringTokenizer`, which would return tokens according to the given String and delimiter. The fastest way I found is to use `String.IndexOf()` to find out the indices of delimiters, and use `String.substring()` to extract data between two delimiters.

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