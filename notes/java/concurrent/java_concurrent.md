<!-- GFM-TOC -->
* [一、基础知识](#基础知识)
    * [并发编程的优缺点](#并发编程的优缺点)
      * [并发编程的优点](#并发编程的优点)
      * [并发编程的缺点](#并发编程的缺点)
      * [并发编程的概念](#并发编程的概念)
        * [同步VS异步](#同步VS异步)
        * [并发VS并行](#并发VS并行)
        * [阻塞VS非阻塞](#阻塞VS非阻塞)
        * [临界资源VS临界区](#临界资源VS临界区)
        * [死锁VS饥饿VS活锁](#死锁与饥饿与活锁)
    * [线程状态和基本操作](#线程状态和基本操作)
         * [如何创建线程](#如何创建线程)
           * [继承Thread](#继承Thread)
           * [实现Runnable接口](#实现Runnable接口)
           * [实现Callable接口](#实现Callable接口)
         * [线程状态转换](#线程状态转换)
           * [New](#New)
           * [Runnable](#Runnable)
           * [Waiting](#Waiting)
           * [Timed_Waiting](#Timed_Waiting)
           * [Blocked](#Blocked)
           * [Terminated](#Terminated)
         * [线程基本操作](#线程基本操作)
           * [interrupt](#interrupt)
           * [sleep](#sleep)
           * [join](#join)
           * [yield](#yield)
         * [守护线程](#守护线程)
* [二、并发理论(JMM)](#并发理论(JMM))
    * [JMM内存模型](#JMM内存模型)
      * [共享数据有哪些](#共享数据有哪些)
        * [实例域](#实例域)
        * [静态域](#静态域)
        * [数组](#数组)
        * [抽象结构](#抽象结构)
      * [重排序](#重排序)
        * [什么是重排序](#什么是重排序)
        * [数据依赖](#数据依赖)
        * [as-if-serial](#as-if-serial)
      * [happens-before规则](#happens-before规则)
* [三、并发关键字](#并发关键字)
    * [synchronized](#synchronized)
      * [如何使用](#如何使用)
        * [实力方法](#实力方法)
        * [静态方法](#静态方法)
        * [代码块](#代码块)
      * [moniter机制](#moniter机制)
      * [synchronized与happens-before关系](#synchronized的happens-before关系)
      * [synchronized的内存语义](#synchronized的内存语义)
      * [锁优化](#锁优化)
        * [锁状态](#锁状态)
        * [CAS操作](#CAS操作)
        * [java对象头](#java对象头)
      * [锁升级策略](#锁升级策略)
    * [volatile](#volatile)
      * [实现原理](#实现原理)
      * [happens-before的关系推导](#happens-before的关系推导)
      * [内存语义及实现](#内存语义及实现)
    * [final](#final)
      * [如何使用](#如何使用)
      * [重排序](#重排序)
      * [实现原理](#实现原理)
      * [this逃逸](#this逃逸)
* [四、Lock体系](#Lock体系)
    * [Lock与synchronized比较](#Lock与synchronized比较)
    * [AQS](#AQS)
       * [AQS同步队列数据结构](#AQS同步队列数据结构)
       * [AQS模版方法](#AQS模版方法)
       * [独占锁](#独占锁)
       * [共享锁](#共享锁)
    * [ReentrantLock](#ReentrantLock)
      * [重入锁实现原理](#重入锁实现原理)
      * [公平锁实现原理](#公平锁实现原理)
      * [非公平锁实现原理](#非公平锁实现原理)
      * [公平锁与非公平锁比较](#公平锁与非公平锁比较)
    * [ReentrantReadWriteLock](#ReentrantReadWriteLock)
      * [读写状态](#读写状态)
      * [ReadLock获取释放](#ReadLock获取释放)
      * [WriteLock获取释放](#WriteLock获取释放)
      * [锁降策略](#锁降策略)
      * [Condition等待队列](#Condition等待队列)
      * [应用场景](#应用场景)
    * [Condition机制](#Condition机制)
      * [与Object的wait/notiy对比](#与Object的wait/notiy对比)
      * [底层数据结构](#底层数据结构)
      * [await实现原理](#await实现原理)
      * [signal/signalAll实现原理](#signal/signalAll实现原理)
    * [LockSupprt](#LockSupprt)
* [五、并发容器](#并发容器)
    * [ConcurrentHashMap](#ConcurrentHashMap)
      * [关键属性](#关键属性)
        * [table](#table)
        * [nextTable](#nextTable)
        * [sizeCtl](#sizeCtl)
        * [Unsafe](#Unsafe)
      * [重要内部类](#重要内部类)
        * [Node](#Node)
        * [TreeNode](#TreeNode)
        * [TreeBin](#TreeBin)
      * [设计到的CAS操作](#设计到的CAS操作)
      * [put流程](#put流程)
      * [get流程](#AbstractSequentialList)
      * [扩容机制](#CopyOnWriteArrayList)
      * [1.8VS1.7](#1.8VS1.7)
   * [ThreadLocal](#ThreadLocal)
      * [实现思想](#实现思想)
      * [set原理](#set原理)
      * [get原理](#get原理)
      * [remove原理](#remove原理)
      * [ThreadLocalMap](#ThreadLocalMap)
        * [底层数据结构](#底层数据结构)
        * [set原理](#set原理)
          * [如果解决hash冲突](#set原理)
        * [getEntry原理](#getEntry原理)
        * [remove原理](#remove原理)
      * [ThreadLocal内存泄露](#ThreadLocal内存泄露)
        * [内存泄露原因](#内存泄露原因)
        * [怎么解决内存泄露](#怎么解决内存泄露)
        * [为什么使用弱引用](#为什么使用弱引用)
      * [应用场景](#应用场景)
   * [BlockingQueue](#BlockingQueue)
      * [ArrayBlockQueue](#ArrayBlockQueue)
      * [LinkBlockQueue](#LinkBlockQueue)
      * [PriorityBlockingQueue](#PriorityBlockingQueue)
      * [SynchronousQueue](#SynchronousQueue)
      * [LinkedBlockingQueue](#LinkedBlockingQueue)
      * [LinkedTransferQueue](#LinkedTransferQueue)
      * [DelayQueue](#DelayQueue)
   * [ConurrentLinkedQueue](#ConurrentLinkedQueue)
      * [原理](#原理)
      * [数据结构](#数据结构)
      * [核心方法](#核心方法)
   * [Executor](#Executor)
      * [ThreadPoolExecutor](#ThreadPoolExecutor)
        * [为什么要使用线程池](#为什么要使用线程池)
        * [执行流程](#执行流程)
        * [构造器参数](#构造器参数)
        * [如何配置线程池](#如何配置线程池)
      * [ScheduledThreadPoolExecutor](#ScheduledThreadPoolExecutor)
      * [FutureTask](#FutureTask)
      * [Executors](#Executors)
      * [Executors](#Executors)
        * [newCachedThreadPool](#newCachedThreadPool)
        * [newFixedThreadPool](#newFixedThreadPool)
        * [newSingleThreadExecutor](#newSingleThreadExecutor)
        * [newScheduledThreadPool](#newScheduledThreadPool)
 * [五、原子操作](#原子操作)
     * [AtomicInteger](#AtomicInteger)
     * [AtomicLong](#AtomicLong)
     * [AtomicBoolean](#AtomicBoolean)
     * [AtomicIntegerArray](#AtomicIntegerArray)
     * [AtomicLongArray](#AtomicLongArray)
     * [AtomicReferenceArray](#AtomicReferenceArray)
     * [AtomicReference](#AtomicReference)
 * [五、并发工具](#并发工具)
     * [CountDownLatch](#CountDownLatch)
     * [CyclicBarrier](#CyclicBarrier)
     * [Semaphore](#Semaphore)
<!-- GFM-TOC -->