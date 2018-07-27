# Unix-Linux-processes

#### What are the processes?

Processes are programs that are executed at a given moment. When we use a GNU / Linux operating system such as Ubuntu for example (or any other, also within windows and mac can be applied) there are a series of processes that are constantly running and that are what make the operating system usable.The processes in GNU / Linux are organized in a hierarchical way, each process is launched by a parent process and is called a child process. In this way, all processes in GNU / Linux are children of init since this is the first process that is executed when the computer is started and init is the parent of all processes. If the parent process is killed, the child processes will also disappear.

#### The init process
* In Linux, each process has a process
father.
* "Init" is the first process that creates the
Linux kernel when the system starts (boot)
* All processes are children of init (from
direct or indirect way).
* The init process can not be killed (kill),
except when the system is turned off.
* The init process always has the PID = 1.


#### Types of processes

Basically there are two: user processes and daemons:

* User processes are the programs that the user usually uses and are connected to a terminal. The program will appear on the screen and interact with the user

* Demons on the other hand, they are not connected to a terminal, they work alone and do not interact with the user.

#### States of a Process in Linux

During execution, a process changes from one state to another depending on its environment/circumstances. In Linux, a process has the following possible states:

* Running – here it’s either running (it is the current process in the system) or it’s ready to run (it’s waiting to be assigned to one of the CPUs).
* Waiting – in this state, a process is waiting for an event to occur or for a system resource. Additionally, the kernel also differentiates between two types of waiting processes; interruptible waiting processes – can be interrupted by signals and uninterruptible waiting processes – are waiting directly on hardware conditions and cannot be interrupted by any event/signal.
* Stopped – in this state, a process has been stopped, usually by receiving a signal. For instance, a process that is being debugged.
* Zombie – here, a process is dead, it has been halted but it’s still has an entry in the process table.

#### Identifiers of a process

* Process ID (PID): Unique identifier.
* User ID (UID) and Group ID (GID): User and
group to which the process belongs:
* Real UID and GID (inherited from the father)
* UID and effective GID (processes with
Effective UID equal to 0 are privileged
since they run as superuser)
* Parent Process ID (PPID): Process PID
father.

#### Process status

* <High-priority (not nice to other users)
* N Low-priority (nice to other users)
* L Has pages locked into memory (for real-time and custom IO)
* s Is a session leader
* l Is multi-threaded (using CLONE_THREAD,
  like NPTL pthreads do)
* (+) Is in the foreground process group

