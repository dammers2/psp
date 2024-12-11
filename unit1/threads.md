Threads

In computer science, a thread of execution is the smallest sequence of programmed instructions that can be managed independently by a scheduler, which is typically a part of the operating system. In many cases, a thread is a component of a process.

The multiple threads of a given process may be executed concurrently (via multithreading capabilities), sharing resources such as memory, while different processes do not share these resources. In particular, the threads of a process share its executable code and the values of its dynamically allocated variables and non-thread-local global variables at any given time.

Background

Threads made an early appearance under the name of "tasks" in IBM's batch processing operating system, OS/360, in 1967. It provided users with three available configurations of the OS/360 control system, of which Multiprogramming with a Variable Number of Tasks (MVT) was one. Victor A. Vyssotsky was credited with the term "thread".

We can find several kinds of threads; 

Kernel threads

A kernel thread is a "lightweight" unit of kernel scheduling. At least one kernel thread exists within each process. If multiple kernel threads exist within a process, then they share the same memory and file resources. Kernel threads are preemptively multitasked if the operating system's process scheduler is preemptive. Kernel threads do not own resources except for a stack, a copy of the registers including the program counter, and thread-local storage (if any), and are thus relatively cheap to create and destroy. Thread switching is also relatively cheap: it requires a context switch (saving and restoring registers and stack pointer), but does not change virtual memory and is thus cache-friendly (leaving TLB valid). The kernel can assign one or more software threads to each core in a CPU (it being able to assign itself multiple software threads depending on its support for multithreading), and can swap out threads that get blocked. However, kernel threads take much longer than user threads to be swapped.

User threads

Threads are sometimes implemented in userspace libraries, thus called user threads. The kernel is unaware of them, so they are managed and scheduled in userspace. Some implementations base their user threads on top of several kernel threads, to benefit from multi-processor machines (M:N model). User threads as implemented by virtual machines are also called green threads.

Fibers

Fibers are an even lighter unit of scheduling which are cooperatively scheduled: a running fiber must explicitly "yield" to allow another fiber to run, which makes their implementation much easier than kernel or user threads. A fiber can be scheduled to run in any thread in the same process. This permits applications to gain performance improvements by managing scheduling themselves, instead of relying on the kernel scheduler (which may not be tuned for the application). Some research implementations of the OpenMP parallel programming model implement their tasks through fibers.

Threads vs processes

Threads differ from traditional multitasking operating-system processes in several ways:

processes are typically independent, while threads exist as subsets of a process
processes carry considerably more state information than threads, whereas multiple threads within a process share process state as well as memory and other resources
processes have separate address spaces, whereas threads share their address space
processes interact only through system-provided inter-process communication mechanisms
context switching between threads in the same process typically occurs faster than context switching between processes
Systems such as Windows NT and OS/2 are said to have cheap threads and expensive processes; in other operating systems there is not so great a difference except in the cost of an address-space switch, which on some architectures (notably x86) results in a translation lookaside buffer (TLB) flush.