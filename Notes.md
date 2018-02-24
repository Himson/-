## Parallel Computing
 ### 基础的概念

  #### 线程与进程
  进程是我们在任务管理器中看到的一个个程序．线程则是计算机执行命令的最小单位．
 ### 语法
    #pragma omp [directive] [clause]

    [Good Article](https://kheresy.wordpress.com/2006/09/13/%E7%B0%A1%E6%98%93%E7%9A%84%E7%A8%8B%E5%BC%8F%E5%B9%B3%E8%A1%8C%E5%8C%96%EF%BC%8Dopenmp%EF%BC%88%E4%BA%8C%EF%BC%89%E8%AA%9E%E6%B3%95%E8%AA%AA%E6%98%8E/)

    openMP 由Compiler Directives（编译指导语句）、Run-time Library Functions（库函数）组成．

    
 ### 控制线程的数量
    num_threads
 ### critical 与临界区段
    临界区段就是 为了防止程序同时调用一块共用资源而划分的
    critical命令即可让后面的代码只会被
 ### 线程的执行顺序问题
    omp_get_thread_num 可以获得线程的编号。线程编号与执行顺序是没有必然联系的。线程的执行是并行而不是同步的。
 ### for 语句的执行
    这个不能出现逻辑上的混乱，否则编译器会报错
 ### section 语句
 　 用sections　命令框住要进行并行的代码段．通过section命令来区分．
 ### master 与主线程
    主线程完成开启进程，开启子线程，关闭进程等操作．
    master　命令使指定的代码段仅由主线程执行
 ### barrier　设置障碍
    设置一个障碍，使各个线程执行完全之后进行下一步的操作，从而达到同步的目的
 ### 锁的理解与使用openMP实现锁
    当一个线程进入一个临界区段的时候，它把这个区段的运行锁住，然后执行完成之后，再解锁．
 ### Gustafson定律
    系统优化某部件所获得的系统性能的改善程度，取决于该部件被使用的频率，或所占总执行时间的比例。
 ### flush　处理的数据的位置　与共享数据
    硬盘－＞内存－＞寄存器－＞cpu(线程)
    在这个过程中，线程完成的时候，数据是不一定由寄存器写入内存的．为了确保我们相互独立的线程共享数据，flush命令可以指示所有线程对所有共享对象具有相同的内存视图（view of memory）
 ### order与迭代顺序
    值得强调的是for directive的ordered clause只是配合ordered directive使用，而不是让迭代有序执行的意思