# Processes
Instance of related tasks (threads) executing on computer
- not same as command (can start multiple processes) or program

Processes can be single-threaded or multi-threaded.
Processes can be of different types, such as interactive and non-interactive.
Every process has a unique identifier (PID) to enable the operating system to keep track of it.
The nice value, or niceness, can be used to set priority.
ps provides information about the currently running processes.
You can use top to get constant real-time updates about overall system performance, as well as information about the processes running on the system.
Load average indicates the amount of utilization the system is under at particular times.
Linux supports background and foreground processing for a job.
at executes any non-interactive command at a specified time.
cron is used to schedule tasks that need to be performed at regular intervals.

## Process Types
1. Interactive P. - Need to be started by a user, either at a command line or through a graphical interface such as an icon or a menu selection.
   1. bash, firefox, top
2. Batch P. - Automatic processes which are scheduled from and then disconnected from the terminal. These tasks are queued and work on a FIFO (first-in, first-out) basis.
   1. updatedb
3. Daemons - Server processes that run continuously. Many are launched during system startup and then wait for a user or system request indicating that their service is required.
   1. httpd, xinetd, sshd
4. Threads - Lightweight processes. These are tasks that run under the umbrella of a main process, sharing memory and other resources, but are scheduled and run by the system on an individual basis. An individual thread can end without terminating the whole process and a process can create new threads at any time. Many non-trivial programs are multi-threaded.
   1. firefox, gnome-terminal-server
5. Kernel Threads - Kernel tasks that users neither start nor terminate and have little control over. These may perform actions like moving a thread from one CPU to another, or making sure input/output operations to disk are completed.
  1. kthreadd, migration, ksoftirqd

A critical kernel function called the scheduler constantly shifts processes on and off the CPU, sharing time according to relative priority, how much time is needed and how much has already been granted to a task.
Processes are usually in 2 states:
**running**
When a process is in a so-called running state, it means it is either currently executing instructions on a CPU, or is waiting to be granted a share of time (a time slice) so it can execute. All processes in this state reside on what is called a run queue and on a computer with multiple CPUs, or cores, there is a run queue on each.
**sleeping**
However, sometimes processes go into what is called a sleep state, generally when they are waiting for something to happen before they can resume, perhaps for the user to type something. In this condition, a process is sitting on a wait queue.

**PID** - unique process ID
- init process is usually 1
- PPID  Process (Parent) that started this process. If the parent dies, the PPID will refer to an adoptive parent; on recent kernels, this is kthreadd which has PPID=2.
- Thread ID (TID) - Thread ID number. This is the same as the PID for single-threaded processes. For a multi-threaded process, each thread shares the same PID, but has a unique TID.

To terminate a process, you can type kill `-SIGKILL <pid>` or `kill -9 <pid>`.
- you can only kill your own processes; those belonging to another user are off limits, unless you are root.

The priority for a process can be set by specifying a nice value, or niceness, for the process.
The lower the nice value, the higher the priority.
In Linux, a nice value of -20 represents the highest priority and 19 represents the lowest.

## Background and Foreground Processes

Linux supports background and foreground job processing.
A job in this context is just a command launched from a terminal window.
Foreground jobs run directly from the shell, and when one foreground job is running, other jobs need to wait for shell access (at least in that terminal window if using the GUI) until it is completed.
This is fine when jobs complete quickly.
But this can have an adverse effect if the current job is going to take a long time (even several hours) to complete.

In such cases, you can run the job in the background and free the shell for other tasks. The background job will be executed at lower priority, which, in turn, will allow smooth execution of the interactive tasks, and you can type other commands in the terminal window while the background job is running. By default, all jobs are executed in the foreground. You can put a job in the background by suffixing & to the command, for example: updatedb **`&`**.

You can either use CTRL-Z to suspend a foreground job or CTRL-C to terminate a foreground job and can always use the bg and fg commands to run a process in the background and foreground, respectively.

## Tools for Monitoring and Managing Processes
`jobs -` to show background jobs
`ps` - show information about processes
`top, htop, atop` - update process info (and show) at regular intervals e.g., 2 min
`ps -u` show processes for specific username
`pstree` - shows relations between processes in form of tree

### Top
1. in `top` in the first line you see thre values
2. The second line of the top output displays the total number of processes, the number of running, sleeping, stopped, and zombie processes. Comparing the number of running processes with the load average helps determine if the system has reached its capacity or perhaps a particular user is running too many processes. The stopped processes should be examined to see if everything is running correctly.
3. The third line of the top output indicates how the CPU time is being divided between the users (us) and the kernel (sy) by displaying the percentage of CPU time used for each.
The percentage of user jobs running at a lower priority (niceness - ni) is then listed. Idle mode (id) should be low if the load average is high, and vice versa. The percentage of jobs waiting (wa) for I/O is listed. Interrupts include the percentage of hardware (hi) vs. software interrupts (si). Steal time (st) is generally used with virtual machines, which has some of its idle CPU time taken for other uses.
4. The fourth and fifth lines of the top output indicate memory usage, which is divided in two categories:
5. last one is load average: The load average determines how busy the system is. A load average of 1.00 per CPU indicates a fully subscribed, but not overloaded, system. If the load average goes above this value, it indicates that processes are competing for CPU time. If the load average is very high, it might indicate that the system is having a problem, such as a runaway process (a process in a non-responding state).

Physical memory (RAM) – displayed on line 4.
Swap space – displayed on line 5.
Both categories display total memory, used memory, and free space.

You need to monitor memory usage very carefully to ensure good system performance. Once the physical memory is exhausted, the system starts using swap space (temporary storage space on the hard drive) as an extended memory pool, and since accessing disk is much slower than accessing memory, this will negatively affect system performance.

If the system starts using swap often, you can add more swap space. However, adding more physical memory should also be considered.

Each line in the process list of the top output displays information about a process. By default, processes are ordered by highest CPU usage. The following information about each process is displayed:

Process Identification Number (PID)
Process owner (USER)
Priority (PR) and nice values (NI)
Virtual (VIRT), physical (RES), and shared memory (SHR)
Status (S)
Percentage of CPU (%CPU) and memory (%MEM) used
Execution time (TIME+)
Command (COMMAND).


`at` - used to schedule tasks
Suppose you need to perform a task on a specific day sometime in the future. However, you know you will be away from the machine on that day. How will you perform the task? You can use the at utility program to execute any non-interactive command at a specified time, as illustrated in the diagram:

`cron` - time-based utility program (launch routine background jobs)
It can launch routine background jobs at specific times and/or days on an on-going basis.
- Basically that an at job is run once, while cron configuration is much more flexible
- cron is driven by a configuration file called /etc/crontab (cron table), which contains the various shell commands that need to be run at the properly scheduled times. There are both system-wide crontab files and individual user-based ones. Each line of a crontab file represents a job, and is composed of a so-called CRON expression, followed by a shell command to execute.
- crontab -e
- The entry `* * * * * /usr/local/bin/execute/this/script.sh` will schedule a job to execute 'script.sh' every minute of every hour of every day of the month, and every month and every day in the week.
The entry `30 08 10 06 * /home/sysadmin/full-backup will schedule a full-backup` at 8.30 a.m., 10-June, irrespective of the day of the week.

`sleep` - sleep suspends execution for at least the specified period of time, which can be given as the number of seconds (the default), minutes, hours, or days. After that time has passed (or an interrupting signal has been received), execution will resume.
sleep NUMBER[SUFFIX]...
`s` for seconds (the default)
`m` for minutes
`h` for hours
`d` for days.

`sleep` and `at` are quite different; sleep delays execution for a specific period, while at starts execution at a later time.

Process Metrics:
load averages and other process metrics.

# Job Control

for jobs (running tasks) SIGNALS are really important
`man SIGNAL` to read more about them
CTRL-C is only one of them
- research more on them (this signal does not necessarily stop the application)
- there is also a signal to suspend the app
- `jobs` to check background tasks
- `kill -STOP %1` (not so intuitive but rather convenient, send STOP signal to the process with `1` identifier)

- `bg` continue running the process in the background
- `&` add this simbol at the end of command to make it NOHUP or to run in background or something like that
- `fg` put the process in background and reatach it to the STDOUT

Signals: (also add their shortcuts, eg CTRL-Z)
- `HUP` - Hang Up
- `STOP` - Stop
- `KILL`
- `CONT`
- `INT`


# Time
- (when executing some application/program there are) 3 concepts of time:
1. real time (entire length of time from start to finish)
2. user time (time that your program spent on the CPU doing user-level cycles)
   - in UNIX you can run User level code or Kernel level code
3. system time

to measure how much time some app consumes you can prepend a certain command with `time`
- eg, `time curl https://comillas.edu &> /dev/null`
  - `&> /dev/null` in the upper command this holds on only on the `curl` not its wrapper `time`


Profilers are tools which add metrics (usually based on time) to measure performance of the applications
- there are `tracing` and `sampling` profilers

[perf](https://www.tecmint.com/perf-performance-monitoring-and-analysis-tool-for-linux/) command for analyzing performance
- measures performance of your code
- eg, `sudo perf report`

check also flame graph and call graph (they are both used as part of profiling)

one of the basic tools is `htop`
also `du` (disk usage)
- `du -h <dir-name>` (human-readable output)
