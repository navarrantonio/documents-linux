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

#### ¿What is the loading of Linux?
The boot process in Linux is the process of initialization of the operating system that makes Linux the kernel (a component of this computer system), the program in the system that allocates the resources of the machine to the other programs that it executes.

#### ¿What is a Linux daemon?
A daemon is a program that runs in the background, waiting for certain events to occur and offering services. A good example of this is a web server that waits for a request to deliver a page or an ssh server waiting for someone trying to connect.

#### ¿What are the processes in Linux?
The processes in Linux (or in any operating system) are programs that are running and are identified by the PID. The PID (Process Identifier) is the number that is assigned to a process when it is started.

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

#### Types of processes
Basically there are two: user processes and daemons:

User processes are the programs that the user usually uses and are connected to a terminal. The program will appear on the screen and interact with the user

Demons on the other hand, they are not connected to a terminal, they work alone and do not interact with the user.

#### States of a Process in Linux
During execution, a process changes from one state to another depending on its environment/circumstances. In Linux, a process has the following possible states:

* Running – here it’s either running (it is the current process in the system) or it’s ready to run (it’s waiting to be assigned to one of the CPUs).
* Waiting – in this state, a process is waiting for an event to occur or for a system resource. Additionally, the kernel also differentiates between two types of waiting processes; interruptible waiting processes – can be interrupted by signals and uninterruptible waiting processes – are waiting directly on hardware conditions and cannot be interrupted by any event/signal.
* Stopped – in this state, a process has been stopped, usually by receiving a signal. For instance, a process that is being debugged.
* Zombie – here, a process is dead, it has been halted but it’s still has an entry in the process table.

#### Identifiers of a process
Process ID (PID): Unique identifier.
User ID (UID) and Group ID (GID): User and group to which the process belongs:
Real UID and GID (inherited from the father)
UID and effective GID (processes with Effective UID equal to 0 are privileged since they run as superuser)
Parent Process ID (PPID): Process PID father.
Process status
<High-priority (not nice to other users)
N Low-priority (nice to other users)
L Has pages locked into memory (for real-time and custom IO)
s Is a session leader
l Is multi-threaded (using CLONE_THREAD, like NPTL pthreads do)
(+) Is in the foreground process group

#### kernel
is a software that is a fundamental part of the operating system, and is defined as the part that runs in privileged mode (also known as kernel mode) .It is the main responsible for providing the different programs with secure access to the hardware of the computer or in basic form, is responsible for managing resources, through system call services. Since there are many programs and access to hardware is limited, it is also responsible for deciding which program can use a hardware device and for how long, which is known as multiplexing.

#### General description of the typical gnu / linux boot process
In Linux, the control flow during boot is from the BIOS, to the boot loader and to the kernel. The kernel initiates the scheduler (to allow multitasking) and executes the first user space (that is, outside the kernel space) and the initialization program (which establishes the user environment and allows user interaction and initiation of session), at which point the core is inactivated until it is called externally.

The boot loader stage is not absolutely necessary. Certain BIOS can load and pass control to Linux without using the charger. Each boot process will be different depending on the processor architecture and the BIOS.

The BIOS performs the specific startup tasks of the hardware platform.
Once the hardware is recognized and started correctly, the BIOS loads and executes the code for the boot partition of the designated boot device, which contains phase 1 of a Linux boot loader. Phase 1 loads phase 2 (most of the boot manager code). Some loaders can use an intermediate phase (known as phase 1.5) to achieve this, since modern large discs can not be fully read without additional code.
The boot manager often presents the user with a menu of possible boot options. Next, it loads the operating system, which unpacks into memory, and sets the system functions as the essential hardware and the memory paging, before calling the 
````bash
$ start_kernel () function.
````
The BIOS performs the specific startup tasks of the hardware platform. Once the hardware is recognized and started correctly, the BIOS loads and executes the code for the boot partition of the designated boot device, which contains phase 1 of a Linux boot loader. Phase 1 loads phase 2 (most of the boot manager code). Some loaders can use an intermediate phase (known as phase 1.5) to achieve this, since modern large discs can not be fully read without additional code. The boot manager often presents the user with a menu of possible boot options. Next, it loads the operating system, which unpacks into memory, and sets the system functions as the essential hardware and the memory paging, before calling the start_kernel () function. The start_kernel () function then performs most of the system configuration (interrupts, the rest of the memory management, device initialization, controllers, etc), before continuing the inactive and planner process separately, and the Init process (which runs in the user space).The planner takes effective control of the management of the system, and the nucleus is asleep (inactive).The Init process executes scripts necessary to configure all services and structures that are not operating system, in order to allow the user environment to be created and presented to the user with a login screen.In the shutdown, Init is called to close all the functionalities of the user space in a controlled manner, again through scripts, after which the Init ends and the kernel executes the shutdown.

#### Early user space
Early user space is used in the most recent versions of the Linux kernel to replace as many functions as possible that would originally be made in the kernel during the startup process. Typical uses of early user space are to detect which device drivers (Drivers) are necessary to load the file system of the main user space and load them from a temporary file system.

#### Boot charger phase
A boot loader is a program designed exclusively to load an operating system in memory. The boot loader stage is different from one platform to another.

As in most architectures this program is in the MBR, which is 512 bytes, this space is not enough to fully load an operating system. Therefore, the boot loader consists of several stages. The first operations are performed by the BIOS. In this stage, basic hardware operations are performed. In this first stage the boot sector (or MBR) is located and the loader of this sector is loaded (usually a part of LILO or GRUB).

From that moment, the boot process continues as follows:

The first stage of the boot loader loads the rest of the boot loader, which usually gives a message asking what operating system (or type of session) the user wants to initialize. Under LILO, this is done through the installed map that reads the configuration file /etc/lilo.conf to identify the available systems. It includes data such as the boot partition and the location of the kernel for each one, as well as the customized options where appropriate. The selected operating system is loaded into RAM, an initial minimum file system is established in the RAM from an image file ("initrd"), and together with the appropriate parameters, the control is passed to the operating system activated recently. .

#### LILO and GRUB differ in some aspects:

* LILO does not understand file systems, so it uses raw disk shifts and the BIOS to load the data. The menu code is loaded and then, depending on the response, load, or MBR sector of the 512-byte disk as in Microsoft Windows, or the image of the Linux kernel.
* GRUB on the other hand comprises the common file systems ext2, ext3 and ext4. Because GRUB stores its data in a configuration file instead of in the MBR and because it contains a command line interface, it is often easier to rectify or modify GRUB if it is misconfigured or corrupted.

#### GRUB

* GRUB is loaded and executed in 4 stages:

The first stage of the loader is read by the BIOS from the MBR.
The first stage loads the rest of the boot manager (second stage). If the second stage is in a large unit, an intermediate phase 1.5 is sometimes loaded, which contains additional code to allow cylinders above 1024, or LBA-type units, to be read. The boot manager 1.5 is stored (if necessary) in the MBR or in the boot partition.
The second stage of the boot manager executes and displays the GRUB start menu that allows the user to choose an operating system and examine and modify the startup parameters.
After choosing an operating system, it is loaded and passed the control.
GRUB supports methods of direct starting, chain-loading, LBA, ext2, ext3, ext4 and even "a pre-operating system on x86 machines totally based on commands". It contains three interfaces: a selection menu, a configuration editor, and a command line console.

#### LILO

* LILO is older. It is almost identical to GRUB in its process, except that it does not contain a command line interface. Therefore all changes to your configuration must be written to the MBR and then reboot the system. An error in the configuration can leave the disk unusable for the boot process to such a degree that it is necessary to use another device (diskette, etc.) that contains a program capable of fixing the error. Also, he does not understand the file system. Instead, the location of the image files are stored directly in the MBR and the BIOS is used to access them directly.

#### Loadlin
Another way to load Linux is from DOS or Windows 9x, where the Linux kernel completely replaces the operating copy of these operating systems. This can be useful in the case of hardware that needs to be connected through the software and the configuration of these programs is only available for DOS and not for Linux, due to issues of industrial secrets and proprietary code. However, this tedious way of starting is no longer necessary at present since Linux has drivers for a multitude of hardware devices. Even so, this was very useful in the past.Another case is when Linux is on a device that the BIOS does not have available for boot. Then, DOS or Windows can load the appropriate driver for the device overcoming that limitation of the BIOS, and load Linux from there.

#### Kernel phase
The Linux kernel is responsible for all operating system processes, such as memory management, task scheduler, I / O, interprocess communication, and general system control. This is loaded in two stages: in the first stage the kernel (as a compressed image file) is loaded and decompressed in memory, and some fundamental functions such as base memory management are established. The control is then changed to the final stage to start the main kernel. Once the kernel is fully operational - and as part of its commissioning, after being loaded and executed - the kernel looks for a startup process to run, which (separately) sets a user space and the processes necessary to a user environment and finalize the entry. The core itself is then allowed to become inactive, subject to calls from other processes.

#### Loading phase of the kernel
The kernel is normally loaded as an image file, compressed into another with zlib as zImage or bzImage. It contains a program header that makes a minimum amount of hardware installation, decompresses the image completely in the high memory, taking into account any RAM disk if it is configured. Then, it carries out its execution. This is done by calling the kernel startup function (on the x86 processors through the startup_32 () function of the file / arch / i386 / boot / head).

#### Start phase of the kernel
The boot function for the kernel (also called exchanger or process 0) establishes memory management (paging tables and memory paging), detects the type of CPU and any additional functionality such as floating-point capabilities, and then switches to the kernel functionalities for non-Linux-specific architecture, through a call to the start_kernel () function.

* start_kernel executes a wide range of initialization functions. It establishes interrupt handling (IRQ), configures additional memory, starts the initialization process (processes the first user's space), and then starts the inactive task through cpu_idle (). In particular, the kernel startup process also mounts the initial RAM disk ("initrd") that was previously loaded as the temporary root system during the boot phase. This allows the driver modules to load without relying on other physical devices and drivers and keeps the kernel smaller. The root file system is changed later through the call to pivot_root (), which unmounts the temporary file system and replaces it with the real one once it is accessible. The memory used by the temporary file system is then recovered.

* Therefore, the kernel initializes the devices, mounts the root file system specified by the boot loader as read-only, and Init (/ sbin / init) is executed, which is designated as the first process executed by the system ( PID = 1). You can also optionally run initrd to allow installing and loading related devices (RAM disk or similar), to be manipulated before the root file system is mounted.

* At this point, with the interruptions enabled, the programmer can take control of the general management of the system, to provide preventive multitasking, and initiate the process to continue loading the user environment in the user space.

#### The start process 

Init's job is to "get everything to work as it should be" once the kernel is fully operational. In essence, it establishes and operates the entire user space. This includes the checking and assembly of file systems, the commissioning of the necessary user services and, ultimately, switching to the user environment when the system start has been completed. It is similar to the Init processes of Unix and BSD, from which it derives, but in some cases it has been separated or made to measure. In a standard Linux system, Init is executed with a parameter, known as execution level, which has a value between 1 and 6, and which determines which subsystems can be operational. Each level of execution has its own scripts that encode the different processes involved in the creation or exit of the determined execution level, and these are the scripts that are necessary in the boot process. Init scripts are usually located in directories with names like "/ etc / rc ...". The highest level configuration file for Init is / etc / inittab.

During the system startup, it is verified if there is a default execution level in the / etc / inittab file, if not, it must be entered through the system console. Afterwards, all the scripts related to the specified execution level are executed.

After all the specified processes have taken place, Init is lethargic, and waits for one of these three events to happen: - which processes started end or die; a failure of the power signal (energy); or a request through / sbin / telinit to change the execution level.
