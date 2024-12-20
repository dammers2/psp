**Threads**

In computer science, a thread of execution is the smallest sequence of programmed instructions that can be managed independently by a scheduler, typically part of the operating system. Often, a thread is a component of a process.

Multiple threads within a process may execute concurrently (via multithreading capabilities), sharing resources such as memory, while different processes do not share these resources. Specifically, threads in a process share executable code and the values of dynamically allocated variables and non-thread-local global variables at any given time.

An operating system (OS) can execute multiple processes, each capable of creating multiple threads.

---

**Background**

Threads first appeared as "tasks" in IBM's batch processing operating system, OS/360, in 1967. This system provided users with three configurations, including Multiprogramming with a Variable Number of Tasks (MVT). The term "thread" was credited to Victor A. Vyssotsky.

---

**Types of Threads**

**Kernel Threads**

A kernel thread is a "lightweight" unit of kernel scheduling. Each process contains at least one kernel thread. Multiple kernel threads within a process share the same memory and file resources. If the operating system's scheduler is preemptive, kernel threads are preemptively multitasked. Kernel threads do not own resources except for a stack, a copy of registers including the program counter, and thread-local storage (if any), making them relatively inexpensive to create and destroy. Thread switching requires a context switch (saving and restoring registers and stack pointer) but does not change virtual memory, thus remaining cache-friendly (leaving TLB valid). The kernel can assign one or more software threads to each CPU core and can swap out blocked threads. However, kernel threads take longer to swap than user threads.

**User Threads**

User threads are implemented in userspace libraries, making the kernel unaware of them. They are managed and scheduled in userspace. Some implementations base their user threads on top of several kernel threads, benefiting from multi-processor machines (M:N model). User threads implemented by virtual machines are also called green threads.

**Fibers**

Fibers are lightweight scheduling units that operate on cooperative scheduling. This means that a running fiber must explicitly "yield" control to allow another fiber to execute, making their implementation simpler compared to kernel or user threads. Fibers can run on any thread within the same process, enabling applications to enhance performance by managing scheduling themselves rather than depending on the kernel scheduler, which may not be optimized for specific applications. Some experimental implementations of the OpenMP parallel programming model utilize fibers to handle tasks.

---

**Threads vs. Processes**

Threads and processes differ in several significant ways:

- **Independence**: Processes are generally independent, while threads are components within a process.
- **State Information**: Processes maintain more extensive state information, whereas threads within the same process share the process state, memory, and other resources.
- **Address Space**: Processes have distinct address spaces, but threads share a single address space.
- **Interaction**: Processes communicate through system-provided inter-process communication mechanisms, while threads interact more directly within the same process.
- **Context Switching**: Switching between threads of the same process is typically faster than switching between processes.

Operating systems like Windows NT and OS/2 are known for "cheap threads" and "expensive processes." In contrast, other systems show less disparity, except for the cost of switching address spaces. On architectures such as x86, this often triggers a translation lookaside buffer (TLB) flush, which can affect performance.

---

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

