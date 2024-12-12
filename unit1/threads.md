**Threads**

In computer science, a thread of execution is the smallest sequence of programmed instructions that can be managed independently by a scheduler, which is typically a part of the operating system. In many cases, a thread is a component of a process.

The multiple threads of a given process may be executed concurrently (via multithreading capabilities), sharing resources such as memory, while different processes do not share these resources. In particular, the threads of a process share its executable code and the values of its dynamically allocated variables and non-thread-local global variables at any given time.

An operating system (OS) can execute multiple processes, and each process can create multiple threads.
---------------------------------------------------------------------

**Background**

Threads made an early appearance under the name of "tasks" in IBM's batch processing operating system, OS/360, in 1967. It provided users with three available configurations of the OS/360 control system, of which Multiprogramming with a Variable Number of Tasks (MVT) was one. Victor A. Vyssotsky was credited with the term "thread".

---------------------------------------------------------------------
**We can find several kinds of threads;** 

*Kernel threads*

A kernel thread is a "lightweight" unit of kernel scheduling. At least one kernel thread exists within each process. If multiple kernel threads exist within a process, then they share the same memory and file resources. Kernel threads are preemptively multitasked if the operating system's process scheduler is preemptive. Kernel threads do not own resources except for a stack, a copy of the registers including the program counter, and thread-local storage (if any), and are thus relatively cheap to create and destroy. Thread switching is also relatively cheap: it requires a context switch (saving and restoring registers and stack pointer), but does not change virtual memory and is thus cache-friendly (leaving TLB valid). The kernel can assign one or more software threads to each core in a CPU (it being able to assign itself multiple software threads depending on its support for multithreading), and can swap out threads that get blocked. However, kernel threads take much longer than user threads to be swapped.

*User threads*

Threads are sometimes implemented in userspace libraries, thus called user threads. The kernel is unaware of them, so they are managed and scheduled in userspace. Some implementations base their user threads on top of several kernel threads, to benefit from multi-processor machines (M:N model). User threads as implemented by virtual machines are also called green threads.

* Fibers *  
Fibers are lightweight scheduling units that operate on cooperative scheduling. This means that a running fiber must explicitly "yield" control to allow another fiber to execute, making their implementation simpler compared to kernel or user threads. Fibers can run on any thread within the same process, enabling applications to enhance performance by managing scheduling themselves rather than depending on the kernel scheduler, which may not be optimized for specific applications. Some experimental implementations of the OpenMP parallel programming model utilize fibers to handle tasks.

**Threads vs. Processes**  
Threads and processes differ in several significant ways:  
- **Independence**: Processes are generally independent, while threads are components within a process.  
- **State Information**: Processes maintain more extensive state information, whereas threads within the same process share the process state, memory, and other resources.  
- **Address Space**: Processes have distinct address spaces, but threads share a single address space.  
- **Interaction**: Processes communicate through system-provided inter-process communication mechanisms, while threads interact more directly within the same process.  
- **Context Switching**: Switching between threads of the same process is typically faster than switching between processes.  

Operating systems like Windows NT and OS/2 are known for "cheap threads" and "expensive processes." In contrast, other systems show less disparity, except for the cost of switching address spaces. On architectures such as x86, this often triggers a translation lookaside buffer (TLB) flush, which can affect performance.
=======
---------------------------------------------------------------------

*Table resume on Threads vs Processes (just seeing how it would be seen on plain text)*

_______________________________________________________________________________________________________________________________________________________________________________________
| Characteristic         |    Threads                                                               |  Processes                                                                      |
|------------------------|--------------------------------------------------------------------------|---------------------------------------------------------------------------------|
| Definition             | Program in execution                                                     | Segment of a process                                                            |
| Independence           | Typically independent, isolated units                                    | Exist as subsets of a process                                                   |   
| State Information      | Carry more state information                                             | Share process state, memory, and resources                                      |
| Address Space          | Have separate address spaces                                             | Share the same address space                                                    |
| Communication          | Less efficient, only through system-provided inter-process communication | More efficient, direct sharing of data within process                           |
| Resource Usage         | Consume more resources                                                   | Consume less resources                                                          |
| Creation Time          | Takes more time for creation                                             | Takes less time for creation                                                    |
| Termination Time       | Takes more time to terminate                                             | Takes less time to terminate                                                    |
| Context Switching      | Takes more time for context switching                                    | Takes less time for context switching (faster between threads in same process)  |
| Memory                 | Isolated memory space                                                    | Share memory                                                                    |
| Resource Cost          | "Expensive" in systems like Windows NT and OS/2                          | "Cheap" in systems like Windows NT and OS/2                                     |
| TLB Impact             | May require TLB flush on architectures like x86                          | Minimal impact                                                                  |
_______________________________________________________________________________________________________________________________________________________________________________________

Note: The relative cost difference between threads and processes varies by operating system. Some systems show less pronounced differences except for address-space switching costs.
