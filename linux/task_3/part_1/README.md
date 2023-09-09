## Task3.Part1

1. How many states could has a process in Linux?

A process in Linux can have several states, but the most common process states include:

**Running (R)**: The process is currently executing or in a running state on the CPU.

**Sleeping (S)**: The process is waiting for an event (e.g., I/O operation) to complete and is currently not using the CPU.

**Stopped (T)**: The process has been stopped, often by a signal, and can be resumed or terminated.

**Zombie (Z)**: The process has completed its execution, but its entry remains in the process table until its parent process acknowledges its termination. Zombies are typically waiting to be cleaned up by the parent process.

---
2. Examine the pstree command. Make output (highlight) the chain (ancestors) of the current process.

The **pstree** command is used to display a visual representation of the process hierarchy on a Unix-like system. To highlight the chain of ancestors of the current process (i.e., the process tree leading to the current process), you can use the **pstree** command along with the **-s** option and specify the PID (Process ID) of the current process.

```bash
pstree -s <current_process_pid>
```

---
3. What is a proc file system?

The **/proc** file system in Linux is a virtual file system that provides an interface to access and interact with kernel and process information as if they were regular files and directories. It is not a traditional file system with data storage but rather a dynamic view into the system's internal state.

---
4. Print information about the processor (its type, supported technologies, etc.).

You can print information about the processor, including its type and supported technologies, by using the lscpu command in Linux. Here's a short answer:

```bash
lscpu
```

![](https://i.imgur.com/blyJ3Zl.png)

---
5. Use the ps command to get information about the process. The information should be as follows: the owner of the process, the arguments with which the process was launched for execution, the group owner of this process, etc.

You can use the ps command with specific options to retrieve information about processes, including the owner, arguments, group owner, and more.

```bash
ps -eo user,args,group
```

- **user**: The owner of the process.
- **args**: The command and its arguments used to launch the process.
- **group**: The group owner of the process.

![](https://i.imgur.com/WCNYgl2.png)

---
6. How to define kernel processes and user processes?

Kernel processes are processes that are created by the kernel. They are usually created during the boot process and are essential for the operating system to function properly. They are also known as system processes.

---
7. Print the list of processes to the terminal. Briefly describe the statuses of the processes. What condition are they in, or can they be arriving in?

You can print the list of processes to the terminal using the ps command. The ps command can be used to display a list of processes running on the system. The ps command can also be used to display information about the processes, such as the process ID (PID), the user who started the process, the amount of CPU and memory the process is using, and more.

```bash
ps -eo pid,ppid,cmd,state
```
- **pid**: Process ID.
- **ppid**: Parent Process ID.
- **cmd**: Command or program name.
- **state**: Process state (R, S, T, Z, I, etc.).

![](https://i.imgur.com/Q6pFDHs.png)

---
8. Display only the processes of a specific user.

To display only the processes of a specific user, you can use the **ps** command with the **-u** option followed by the **username** of the user whose processes you want to see.

```bash
ps -u <username>
```

![](https://i.imgur.com/mNly94r.png)

---
9. What utilities can be used to analyze existing running tasks (by analyzing the help for the ps command)?

To analyze existing running tasks and gain more insights into processes, you can use various options with the ps command. Here are some utilities you can use to analyze processes by analyzing the help for the ps command (using **ps --help** or **man ps** for more details):

- **ps aux**: This command provides a detailed list of all running processes, including user, CPU usage, memory usage, and more.

- **ps -ef**: Similar to ps aux, it displays a list of all processes but uses a slightly different format.

- **ps -eF**: This command shows a forest view of processes, displaying parent-child relationships.

- **ps -o**: The -o option allows you to specify custom output fields, allowing you to select and display specific information about processes.

- **ps -p**: You can use this option followed by a specific process ID (PID) to display detailed information about a single process.

- **ps -u**: This option lets you display processes for a specific user.

- **ps -G**: Use this option followed by a group ID (GID) to display processes for a specific group.

- **ps --sort**: You can sort the output based on various criteria such as CPU usage, memory usage, or start time.

---
10. What information does top command display?

![](https://i.imgur.com/URGU5ce.png)

The **top** command displays real-time information about system resource usage and running processes. Here's a short answer describing the key information it provides:

**System Overview**: The top of the display shows system-wide information, including the current time, system uptime, number of users, and system load averages.

**CPU Usage**: It displays CPU-related information, including the total CPU usage as a percentage and a breakdown of CPU usage by individual processes. It shows the percentage of CPU time used by user processes, system processes, and idle processes.

**Memory Usage**: Top provides information about memory usage, including the total amount of physical and virtual memory, as well as how much is currently in use and available. It also shows memory usage by individual processes.

**Swap Usage**: It indicates how much swap space is being used, both in terms of total swap space and current usage.

**Task Information**: Top lists all running processes with details such as process ID (PID), user, CPU usage, memory usage, and more. You can sort the process list by various criteria, including CPU usage and memory usage.

**Interactive Commands**: Top allows you to interactively send commands to control the display, such as sorting processes, changing the update interval, and killing processes.

**Load Averages**: It shows the 1-minute, 5-minute, and 15-minute load averages, which represent the average number of processes waiting for CPU time over different time intervals.

**Summary Information**: Top provides a summary section with overall statistics, including the total number of processes, the number of running, sleeping, stopped, and zombie processes.

**Resource Totals**: It displays totals for various system resources, including CPU usage, memory usage, and swap usage.

**System Information**: Some versions of top may also display system information such as the kernel version and system architecture.

---
12. Display the processes of the specific user using the top command.

Run the top command with the -u option followed by the username of the specific user whose processes you want to view. Replace username with the actual username.

```bash
top -u username
```

![](https://i.imgur.com/9Gqkuqe.png)

---
12. What interactive commands can be used to control the top command? Give a couple of examples.

The top command provides several interactive commands that allow you to control and manipulate its display. 

**Sorting by Different Fields:**

- **P**: Sort processes by CPU usage (default).
- **M**: Sort processes by memory usage.

**Changing Update Interval:**

- **d**: Change the update interval. You'll be prompted to enter a new update interval in seconds.

**Filtering Processes:**

- **u**: Filter processes by a specific user. After pressing u, you can enter the username to display only their processes.

**Killing Processes:**

- **k**: Prompt to enter the PID of a process to kill. Useful for sending a termination signal to a process.

**Toggle Highlighting:**

- **h**: Toggle highlighting of running processes, making it easier to distinguish them from others.

**Displaying Command Line:**

- **c**: Toggle between displaying the process command line and only the command name.

**Quitting:**

- **q**: Quit the top command and return to the terminal.

---
13. Sort the contents of the processes window using various parameters (for example, the amount of processor time taken up, etc.)

You can sort the contents of the processes window in the **top** command using various parameters. Here are some commonly used sorting keys:

**CPU Usage (Default**): To sort by CPU usage (highest to lowest), press **P** (uppercase 'P'). This is the default sorting key.

**Memory Usage:** To sort by memory usage (highest to lowest), press **M** (uppercase 'M').

**Process ID (PID):** To sort by Process ID (ascending order), press **N** (uppercase 'N').

**Username:** To sort by the username of the process owner (alphabetically), press **U** (uppercase 'U').

**Priority:** To sort by process priority (highest to lowest), press **R** (uppercase 'R').

---
14. Concept of priority, what commands are used to set priority?

The concept of priority in process scheduling refers to the relative importance of a process, with lower numeric values indicating higher priority.



```bash
//Use the nice command to launch a new process with a specific priority.
nice -n <priority_level> <command>

//Use the renice command to change the priority of an existing process.
renice <priority_level> -p <process_id>
```

---
15. Can I change the priority of a process using the top command? If so, how?

Yes, you can change the priority of a process using the top command interactively. 

1. Launch top by typing top in the terminal.
2. When top is running, find the process for which you want to change the priority.
3. Select the process by highlighting it (use the arrow keys).
4. Press the r key to open the renice menu.
5. You will be prompted to enter a new priority value. Lower values indicate higher priority. Enter the new priority value and press Enter.
6. The process's priority will be updated accordingly.

---
16. Examine the kill command. How to send with the kill command
process control signal? Give an example of commonly used signals.

The **kill** command in Unix-like operating systems is used to send process control signals to running processes. You can use it to manage processes by sending various signals for different purposes. 

```bash
kill -SIGNAL PID
```
- **-SIGNAL**: Specifies the signal you want to send. You can use either the signal name (e.g., TERM, HUP, KILL) or the signal number (e.g., 9 for SIGKILL).
- **PID**: The Process ID of the target process you want to send the signal to.
Commonly used signals and their purposes include:

- **SIGTERM (15)**: Termination signal. Gracefully asks the process to terminate.
- **SIGHUP (1)**: Hangup signal. Often used to restart daemons or reload configuration files.
- **SIGKILL (9)**: Kill signal. Forcefully terminates the process.
- **SIGINT (2)**: Interrupt signal. Typically generated by pressing Ctrl+C in the terminal.
- **SIGSTOP (19)** or **SIGTSTP (20)**: Stop signal. Pauses the process until resumed.
- **SIGCONT (18)**: Continue signal. Resumes a stopped process.

```bash
# Send a SIGTERM signal to process with PID 1234
kill -TERM 1234

# Send a SIGHUP signal to process with PID 5678
kill -HUP 5678

# Send a SIGKILL signal to process with PID 7890
kill -KILL 7890
```

---
17. Commands jobs, fg, bg, nohup. What are they for? Use the sleep, yes command to demonstrate the process control mechanism with fg, bg.

The commands **jobs**, **fg**, **bg**, and **nohup** are used for managing and controlling processes in Unix-like operating systems. Here's what they are for:

- **jobs**: This command is used to list the background jobs or suspended processes in the current shell session.
- **fg**: The fg command is used to bring a background job to the foreground, making it the active process in the terminal.
- **bg**: The bg command is used to resume a suspended (stopped) background job in the background, allowing it to continue running.
- **nohup**: The nohup (short for "no hang up") command is used to run a command or script in a way that it continues running even after the terminal is closed, and it also disassociates the command from the terminal session.

```bash
# Start a background process using the 'sleep' command
sleep 300 &

# List background jobs
jobs

# Bring the background job to the foreground
fg

# The terminal will be occupied by the 'sleep' process. To suspend it, press Ctrl+Z.

# List background jobs again (the 'sleep' process is now suspended)
jobs

# Resume the suspended 'sleep' process in the background
bg

# List background jobs once more
jobs
```

![](https://i.imgur.com/1aXKBNU.png)