PROCESS SCHEDULER
-----------------

A Process Scheduler is a component of the operating system responsible for managing the execution of processes in the CPU.
Its primary role is to decide which process gets to use the CPU and for how long, ensuring efficient use of system resources while maintaining fairness among processes.

**Batch processing** is a task execution method where a group of processes or jobs is executed sequentially without user interaction during the execution.
Essentially, tasks are grouped into "batches" that are processed by the system at a scheduled time or when resources are available.

It makes sure that tasks or "jobs" run when they’re supposed to, in the right order, without needing manual intervention.
These tasks are organized in something called a job queue.

Main features:

- Workflows and dependencies: You can set tasks that depend on others to run.
- Automatic execution: Schedules tasks to run automatically.
- Monitoring: Tools to check if tasks are running properly.
- Priorities: Helps decide which tasks should run first.
  
Common architectures:

Master/Agent: There’s usually one main server (master) that controls smaller agents on machines where tasks run.
Cooperative: Each machine can plan its own tasks or pass them to others, sharing the load dynamically.
Basic schedulers like cron (Unix) or Windows Task Scheduler do the job for simple setups.
But modern ones offer extra features like retrying failed tasks automatically, sending alerts, creating reports, or keeping logs for regulations. 
These advanced schedulers are widely used in businesses, where processes and systems need to be synced and managed efficiently.
