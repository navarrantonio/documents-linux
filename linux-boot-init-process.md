# Linux boot process
The boot process in Linux is the process of initialization of the operating system that makes Linux the kernel (a component of this computer system), the program in the system that allocates the resources of the machine to the other programs that it executes.

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

* init. In Unix-like systems, init (short for initialization) is the first running process after loading the kernel and which in turn generates all other processes. ... Debian, RedHat and some other Linux distributions now use Systemd as a replacement for the traditional initialization process.

#### Daemon
A daemon is a program that runs in the background, waiting for certain events to occur and offering services. A good example of this is a web server that waits for a request to deliver a page or an ssh server waiting for someone trying to connect.

#### BSD style
The BSD init executes the initialization script in / etc / rc, similar to what was done in the original Unix of Bell Labs. There are no execution levels (runlevels), the file / etc / rc determines which programs are executed by init. The advantage of this system is that it is simple and easy to edit manually, although subject to errors. because a simple error in that script could make the system boot procedure unusable.

Without this, the other initialization systems in the scripts would not exist.

#### System V Style
In GNU / Linux is the file responsible for establishing the available runlevels, so that it can be read by init. Below is an example of the start of this file, in which runlevel 5 is established, and its characteristics:

/ etc / inittab: init (8) configuration
$ Id: inittab, v 1.9 2001/05/31
The runlevel by default
id: 5: initdefault:
Runlevel 0 is to stop
Runlevel 1 is single user
Runlevels 2-5 are multi-user
Runlevel 6 is restart

#### Systemd
systemd is a set of daemons or system management daemons, libraries and tools designed as a central management and configuration platform to interact with the core of the GNU / Linux operating system. Described by its authors as a "basic building block" for an operating system, 4 systemd can be used as a Linux boot system (the init process called by the kernel or Linux kernel to initialize the user space during the Linux boot process and subsequently manage all other processes). The systemd name adheres to the Unix convention of distinguishing demons easily by having the letter d as the last letter of the file name.In May 2011, Fedora became the first major Linux distribution to enable systemd by default.By 2015, most of the major Linux distributions have adopted systemd as their default startup system.

#### systemd, replacement of sysvinit
In UNIX systems, the first process that is created and is responsible for initializing the rest of processes is known as init. Since 1980 this task was carried out by «System V init» (sysvinit). However, given that the services are released in a certain order and the current devices are very diverse and dynamic, they are no longer adequate for these times. In 2006 Canonical developed Upstart with the aim of creating a replacement for sysvinit. Upstart is an event-driven system so that when a certain circumstance occurs, some action is taken, such as "the network device has been mounted", thus better supporting the dynamism of the systems. Upstart seemed the successor of sysvinit, however, the migration of sysvinit to an event-driven system such as upstart is not simple.

systemd was launched in 2010 by Lennart Poettering, also known for developing pulseaudio, also as a replacement for sysvinit. systemd is beginning to replace sysvinit as the process responsible for booting the system in several distributions such as Fedora, openSUSE, Mandriva and Arch Linux for several of its features.

systemd activates all the sockets that processes use to communicate before none is booted so that they are available for when they do so, once the sockets are initialized systemd initiates all the processes in parallel without any pre-established order or on demand when sending a message to your socket. When one process needs another one communicates through the sockets, if the recipient process is not yet available to receive the systemd message, it enqueues it so that it does not get lost and dispatches it when the destintario process is available. In this way, a total parallelism is obtained between the processes that initiate the system.

https://danielmiessler.com/blog/the-differences-between-bsd-and-system-v-unix/
