Core component of linuix

Architecture of linux :
- Linux architecture includes Hardware, kernel , user space 

-Linux segregate meemory space in two ,in one is where kernel exist and has priviledge to accesssystem resourses like hardware .while anothere is User space where all other application , shell , processes, even systemd exist which are restricted to access system resources directly. 
-when a user level application need to perform that require kernel mode access, such as accessing hardware devices or modifying system settings, it must make a system call to the kernel. The OS switches the processor from user mode to kernel mode to execute the system call, and then switches back to user mode once the operation is complete. 

This switching between user mode and kernel mode is known as mode switching or context switching.

- kernel is the heart or core component of OS which  manages system resources, where all the code exist.
- shell - is an interface between user and kernel , shell interprets the command and send it to kernel for execution.
- application - are the all other application like IDE, Terminal , Docker ,Kubernetes.

flow -
Switch on - motherBoard - Firmware(BIOS) - Bootloader(GRUB) - Kernel(Linux kernel) - init/systemd(PID1) - all other processes.

systemd - this is the 1st process that kernel starts to manage system services. It further creates and manage other processes.systemd starts the services required for the system to operate.

Process - A process is an instance of an program executing. It has its own sytem resources, memory, cpu state , open files and state.Whenever we execute any command or application , linux executes it and create a process for it and assigns the PID to it for identification and management.

process execution- Foreground and background processes
type of process - 
1. Parent and child process
2. Zombie and Orphan Process
3. Daemon Process

states of processes- 
1. New - The process is newly created.
2. Ready - process is ready and waiting in queue util CPU becomes avaialble.
3. Running - CPU is executing the process.
4. Waiting - Pocess is waiting for events e.g I/O , User input.
5. Terminated - Process execution is completed.
6. Stopped -process is paused and temporarily cannot continue executing until it receives a signal to resume.We can stop a process using kill -STOP PID and resume it using kill -CONT PID.
Commands - 
ps/ps -ef- to track ongoing process
top -monitoring process in real time
ps aux - a means all users, u means detailed info of CPU and Memory ,x means processes without a terminal too like daemons.

commands for daily use

cd - to change directory
ls - list all the files and directories
mkdir - to create a new directory
touch - to create a new file
pwd - to view present working directory
df -h -to view disk detailed info
free -h - to view RAM detailed info
