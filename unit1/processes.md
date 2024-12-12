Definition: A process is an instance of a program that is being executed. It includes the program code and its current activity. 
Depending on the operating system (OS), a process might consist of multiple threads of execution that execute instructions concurrently.

Components of a Process:

    - Program Code (Text Section): The set of instructions to be executed.
    - Program Counter: A register that holds the address of the next instruction to be executed.
    - Process Stack: Contains temporary data such as function parameters, return addresses, and local variables.
    - Data Section: Contains global variables.
    - Heap: Memory dynamically allocated during process execution.

Process Control Block (PCB): The OS maintains a data structure called the Process Control Block for each process. The PCB contains:

    - Process State: Current state of the process (new, running, waiting, etc.).
    - Program Counter: Address of the next instruction to be executed.
    - CPU Registers: Various CPU registers where process-specific data is stored.
    - Memory Management Information: Information about process memory allocation.
    - Accounting Information: CPU used, clock time elapsed since start, time limits.
    - I/O Status Information: List of I/O devices allocated to the process, list of open files.

Process Scheduling: Scheduling is the method by which work assigned to the CPU is managed. The main goal is to maximize CPU utilization and allow multiple processes to be executed simultaneously.

    - Long-term Scheduler (Job Scheduler): Decides which processes should be brought into the ready queue. This scheduler controls the degree of multiprogramming.
    - Short-term Scheduler (CPU Scheduler): Decides which of the ready processes should be executed next and allocates the CPU.
    - Medium-term Scheduler: Swaps processes in and out of memory to balance the load on the CPU.

Context Switching: When the CPU switches from executing one process to executing another, the state of the current process must be saved and the state of the next process must be loaded. 
This is called a context switch and involves saving and restoring the PCB of the processes.

Inter-Process Communication (IPC): Processes often need to communicate with each other for various reasons, such as data sharing and synchronization. IPC mechanisms include:

    - Pipes: Simple communication channels that use a buffer to hold data being passed between processes.
    - Message Queues: Allow processes to send and receive messages.
    - Shared Memory: Allows multiple processes to access the same memory space.
    - Sockets: Provide communication channels over a network.

Process Creation and Termination:

    - Creation: Processes are created through system calls like fork in UNIX, which creates a new process by duplicating the existing one. Other system calls like exec are used to replace the process’s memory space with a new program.
    - Termination: Processes can be terminated voluntarily by calling exit system call or involuntarily by receiving a signal (such as kill).
