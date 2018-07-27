# Process Lists

#### ps 
is a command with which we can see a list of processes, along with certain information related to 
these processes. The information returned by ps varies depending on the options used.

We can use three types of options with ps:

Unix98: single-character options that can be grouped and preceded by a single hyphen (-).
BSD: single character options that can be grouped and NOT GO preceded by a single hyphen (-).
GNU Long: multi-character options can not be grouped and each of them is preceded by two hyphens (--).
States of a Process in Linux
During execution, a process changes from one state to another depending on its environment/circumstances. In Linux, a process has the following possible states.

Some interesting options are:

All processes -a -e x
Additional information -f -l j l u v
Hierarchy of processes -H -f --forest
Show an output greater than 80 columns -w w, normally ps truncate, or cut, the information to 80 columns. Very useful if we redirect the output, either to a file or to another command, since we will be able to use the complete information (imagine a program that uses the path of the file and it is truncated, surely we do not obtain the desired results)
Processes of a user -u user, user U, --user user

````bash
$ ps
  PID TTY          TIME CMD
22824 pts/3    00:00:00 sudo
22825 pts/3    00:00:00 su
22826 pts/3    00:00:00 bash
30377 pts/3    00:00:00 ps

$ ps -a
  PID TTY          TIME CMD
22824 pts/3    00:00:00 sudo
22825 pts/3    00:00:00 su
22826 pts/3    00:00:00 bash
29643 pts/3    00:00:00 ps

$ ps -e
  PID TTY          TIME CMD
    1 ?        00:00:01 systemd
    2 ?        00:00:00 kthreadd
    4 ?        00:00:00 kworker/0:0H
    6 ?        00:00:00 mm_percpu_wq
    7 ?        00:00:01 ksoftirqd/0
30156 pts/3    00:00:00 ps
````
#### top
It is a tool that shows us information about the status of the processes
that are running the computer, it is a tool similar to ps but interactive.
When we execute top, it shows us a structured list in three zones, from top to bottom we find an area
that informs us of the processes in execution and their status, the use of the CPU according to types 
of processes, and the use of memory.

````bash
$ top
top - 14:07:03 up  4:14,  1 user,  load average: 1,24, 1,15, 1,60
Tareas: 263 total,   2 ejecutar,  197 hibernar,    0 detener,    0 zombie
%Cpu(s):  7,5 usuario,  3,7 sist,  0,0 adecuado, 88,8 inact,  0,0 en espera,  0,0 hardw int, 
KiB Mem :  8041640 total,   314280 free,  3575316 used,  4152044 buff/cache
KiB Swap:  8257532 total,  8215036 free,    42496 used.  3635716 avail Mem 

  PID USUARIO   PR  NI    VIRT    RES    SHR S  %CPU %MEM     HORA+ ORDEN                    
 1467 root      20   0  334236  35204  24600 S  15,0  0,4  11:30.48 Xorg                     
 2535 antonio   20   0 1160308  66312  40572 S   7,0  0,8   7:20.91 gala                     
 7427 antonio   20   0  555028  38356  25052 R   7,0  0,5   1:21.48 pantheon-termin          
 2830 antonio   20   0 1011852 109936  30156 S   4,7  1,4   4:02.97 io.elementary.a          
 2890 antonio   20   0 98,091g  83432  49484 S   2,0  1,0   1:43.64 wingpanel                
 2891 antonio   20   0  700732  34676  24020 S   2,0  0,4   1:25.82 plank                    
 2912 antonio   20   0  491484  26672  19216 S   2,0  0,3   0:59.84 bamfdaemon               
 5352 antonio   20   0 1471480 333708  80320 S   1,0  4,1   1:54.41 slack                    
26997 antonio   20   0 1250736 166392  72892 S   1,0  2,1   0:31.57 chrome                   
 4569 antonio   20   0 1312172 275540 105720 S   0,7  3,4  19:49.85 chrome                   
    8 root      20   0       0      0      0 I   0,3  0,0   0:15.84 rcu_sched                
 1865 root      20   0  441504  14940   4720 S   0,3  0,2   0:32.31 dockerd                  
 4665 antonio   20   0 1526688 141372  77164 S   0,3  1,8   0:53.58 slack                    
 4723 antonio   20   0 2643556 371412  84832 S   0,3  4,6   3:02.72 chrome                   
 5049 antonio   20   0 1196040 140656  70780 S   0,3  1,7   1:45.07 chrome                   
````
https://www.tecmint.com/12-top-command-examples-in-linux/

#### glances
glances is a relatively new system monitoring tool with advanced features.

````bash
$ glances
envenz ("elementary" 0.4.1 64bit / Linux 4.15.0-24-generic)                     Uptime: 4:49:07

CPU      16.8%  nice:     0.0%   LOAD    4-core   MEM     53.9%   SWAP      0.5%
user:    12.7%  irq:      0.0%   1 min:    2.16   total:  7.67G   total:   7.87G
system:   4.1%  iowait:   0.1%   5 min:    1.60   used:   4.14G   used:    41.0M
idle:    83.2%  steal:    0.0%   15 min:   1.38   free:   3.53G   free:    7.83G

NETWORK     Rx/s   Tx/s   TASKS 263 (1273 thr), 1 run, 201 slp, 61 oth sorted automatically
_143cab9d     0b     0b
docker0       0b     0b     CPU%  MEM%   PID USER        NI S Command 
enp3s0f2      0b     0b     14.7   2.4 31359 antonio      0 S /opt/google/chrome/chrome --typ
lo           5Kb    5Kb     10.5   0.4  1467 root         0 S /usr/lib/xorg/Xorg -core :0 -se
wlp2s0      11Kb    9Kb      9.3   1.4  2830 antonio      0 S io.elementary.appcenter -s
                             5.4   0.8  2535 antonio      0 S gala 
DISK I/O     R/s    W/s      4.5   0.5  7427 antonio      0 S pantheon-terminal 
dm-0           0      0      4.2   0.4 31778 root         0 R /usr/bin/python3 /usr/bin/glanc
dm-1           0      0      2.6   0.2  2474 antonio    -11 S /usr/bin/pulseaudio --start --l
dm-2           0      0      2.2   1.0  2890 antonio      0 S wingpanel 
sda1           0      0      1.9   3.6  4569 antonio      0 S /opt/google/chrome/chrome 
sda2           0      0   
sda5           0      0
2018-07-27 14:41:38       No warning or critical alert detected
````
https://www.tecmint.com/linux-performance-monitoring-tools/

#### jobs
The jobs command returns the task IDs of the processes launched from the console in which they are executed, they start at 1 and we should not confuse them with the PIDs. jobs has some options, to see them and a brief explanation, we must use help jobs, because with man and info we will not obtain any information.A practical use can be to make sure before closing a console, local or remote, that we do not leave any process started (whether it is running or stopped) due to security issues or that the process crashes.If you want to do a test,start a graphic terminal in this case and run gimp & (& makes gimp run in the background or background so you can run jobs from the same terminal).Once you start gimp and show us again the terminal prompt execute jobs, (without closing gimp).

````bash
$ gimp &
$ jobs
````
#### foreground and background

* ¿When will we launch a program in the background?
P.e. in a graphic terminal we launch gimp and we want to perform other operations from the same terminal, or we will launch a program that does not need interaction with the user (in the latter case we do not care whether it is an xterm or a text terminal.

* ¿When will we launch a foreground program?
With a process that needs interaction with the user, and this interaction is done through the terminal.

* ¿How can we launch another program from a terminal with another program running in foreground?
We press CTRL-z with what we pause the program in execution and foreground, we pause it with which it will stop working, and we will be able to launch another program eg. ls

We can do a test launch gimp and check that we can operate with it, then press CTRL-z and see how we can not work with gimp).
Now we want to start up gimp again so we can use gimp again

If we want to return it to foreground we will write fg.
If we want to return it to the background we will write bg (this would be the most logical option)
In the case that we have more than one program stopped we will have to indicate both to fg and to bg the task ID on which they will act, this ID can be obtained with jobs that we have seen in a previous section


#### ¿How to launch a program directly in background - &?
Following our example with gimp would be gimp &. The & tells S.O. to run the program in the background

````bash
$ gimp &
````
#### Manage process priorities - nice and renice

¿What is the priority of the process?
The process priority is used to decide the amount of time that the process can use the processor, by time interval. Step to explain, the / processors are shared by several processes (the processes are alternated in the use of or processors) giving the user feeling that all applications, tasks, processes are executed at once, well the priority it tells the system which processes can use more processor time and which processes go to a second place. This may lead to the execution of some process (s) never to be executed, since they are being displaced in the process queue towards the end by other processes with a higher priority.

Highest priority -20 (minus twenty)

Lower priority 19 (nineteen)

If we start a program normally, and there is no configuration for the user or group that modifies it, it will start with priority 0 (zero)

#### nice
nice assigns a specific priority to a program when it is executed, and by inheritance the tasks and processes that this program can trigger.

nice syntax

````bash
$ nice [argument] [command [command-arguments]]
````
The arguments can be passed in 3 ways

priority preceded by a - (positive priorities give a negative aspect eg priority 12 -> nice -12 program)
priority behind -n (eg nice -n 12 program)
priority after -adjustment = (eg nice -adjustment = 12 program)

#### renice
renice uses the parameters in the same way as nice

Considerations
When a program starts with nice without arguments it starts with a priority of 10.
Both nice and renice allow us to change the priority of programs or processes without interfering in the execution of the program or process.
If we want to change the priority to a process, we must use the pid of that process (with man you can find its syntax).
We can change the priority of several processes at the same time eg. 
````bash
$ renice priority pids -u users
$ renice [-n] <priority> [-p|--pid] <pid>...
$ renice [-n] <priority>  -g|--pgrp <pgid>...
$ renice [-n] <priority>  -u|--user <user>...

````
Alter the priority of running processes.

Opciones:
 -n, --priority <num>   specify the nice increment value
 -p, --pid <id>         interpret argument as process ID (default)
 -g, --pgrp <id>        interpret argument as process group ID
 -u, --user <name>|<id> interpret argument as username or user ID

 -h, --help     display this help and exit
 -V, --version  output version information and exit

For more details see renice.
* We can use and combine priority changes for independent processes with their pid, users and groups.
* Only root can use them to increase the priority.
* Any user can use them to decrease the priority to the processes that have permission.
* We can use and combine priority changes for independent processes with their pid, users and groups.
* Only root can use them to increase the priority.
* Any user can use them to decrease the priority to the processes that have permission.

# Destroy processes - kill and killall
#### kill

A kill must pass a signal of completion, with which we will tell you how we want to destroy the process, we can pass both the number and the constant that represents it, the most common signals are:

````bash
$ kill -l
 1) SIGHUP	 2) SIGINT	 3) SIGQUIT	 4) SIGILL	 5) SIGTRAP
 6) SIGABRT	 7) SIGBUS	 8) SIGFPE	 9) SIGKILL	10) SIGUSR1
11) SIGSEGV	12) SIGUSR2	13) SIGPIPE	14) SIGALRM	15) SIGTERM
16) SIGSTKFLT	17) SIGCHLD	18) SIGCONT	19) SIGSTOP	20) SIGTSTP
21) SIGTTIN	22) SIGTTOU	23) SIGURG	24) SIGXCPU	25) SIGXFSZ
26) SIGVTALRM	27) SIGPROF	28) SIGWINCH	29) SIGIO	30) SIGPWR
31) SIGSYS	34) SIGRTMIN	35) SIGRTMIN+1	36) SIGRTMIN+2	37) SIGRTMIN+3
38) SIGRTMIN+4	39) SIGRTMIN+5	40) SIGRTMIN+6	41) SIGRTMIN+7	42) SIGRTMIN+8
43) SIGRTMIN+9	44) SIGRTMIN+10	45) SIGRTMIN+11	46) SIGRTMIN+12	47) SIGRTMIN+13
48) SIGRTMIN+14	49) SIGRTMIN+15	50) SIGRTMAX-14	51) SIGRTMAX-13	52) SIGRTMAX-12
53) SIGRTMAX-11	54) SIGRTMAX-10	55) SIGRTMAX-9	56) SIGRTMAX-8	57) SIGRTMAX-7
58) SIGRTMAX-6	59) SIGRTMAX-5	60) SIGRTMAX-4	61) SIGRTMAX-3	62) SIGRTMAX-2
63) SIGRTMAX-1	64) SIGRTMAX	

root@venz:/home/antonio# ps -l
F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
4 R     0  4249 22826  0  80   0 - 13404 -      pts/3    00:00:00 ps
4 S     0 22824  7437  0  80   0 - 19876 poll_s pts/3    00:00:00 sudo
4 S     0 22825 22824  0  80   0 - 19756 wait   pts/3    00:00:00 su
4 S     0 22826 22825  0  80   0 - 11559 wait   pts/3    00:00:00 bash
root@venz:/home/antonio# kill 9 4249
bash: kill: (4249) - No existe el proceso
root@venz:/home/antonio# kill 9 22825

root@venz:/home/antonio# Sesión finalizada, parando la consola ...exit
 ... parada.

````
* 1	SIGHUP: End interactive programs, and make many demons reread their configuration file.
* 9 SIGKILL Ends immediately, without leaving the completion tasks.
* 15 SIGTERM Ends the process allowing completion tasks.

#### killall
It allows us to eliminate a process based on its name instead of its pid, so we can eliminate all instances of a process. With the parameter -i we will be able to ask ourselves interactively if we want to eliminate a specific instance of the process or if on the contrary we want it to continue its execution.

In some systems it destroys all the processes of the user that executes it.

If you run it, you should be careful because you could delete all the instances of a process even if they are not yours, although sometimes it is exactly what you want.

It is highly recommended to study the documentation of these commands well in each particular system to familiarize yourself and fully understand what exactly they do in our system.

````bash
$ killall firefox
````
http://www.desarrollolibre.net/blog/linux/los-comandos-kill-y-killall-en-linux#.W1tuqnZKjDc

