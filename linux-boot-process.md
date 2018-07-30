# Linux boot process
The boot process in Linux is the process of initialization of the operating system that makes Linux the kernel (a component of this computer system), the program in the system that allocates the resources of the machine to the other programs that it executes.

#### kernel
is a software that is a fundamental part of the operating system, and is defined as the part that runs in privileged mode (also known as kernel mode) .It is the main responsible for providing the different programs with secure access to the hardware of the computer or in basic form, is responsible for managing resources, through system call services. Since there are many programs and access to hardware is limited, it is also responsible for deciding which program can use a hardware device and for how long, which is known as multiplexing.


#### General description of the typical gnu / linux boot process
In Linux, the control flow during boot is from the BIOS, to the boot loader and to the kernel. The kernel initiates the scheduler (to allow multitasking) and executes the first user space (that is, outside the kernel space) and the initialization program (which establishes the user environment and allows user interaction and initiation of session), at which point the core is inactivated until it is called externally.

The boot loader stage is not absolutely necessary. Certain BIOS can load and pass control to Linux without using the charger. Each boot process will be different depending on the processor architecture and the BIOS.

The BIOS performs the specific startup tasks of the hardware platform.
Once the hardware is recognized and started correctly, the BIOS loads and executes the code for the boot partition of the designated boot device, which contains phase 1 of a Linux boot loader. Phase 1 loads phase 2 (most of the boot manager code). Some loaders can use an intermediate phase (known as phase 1.5) to achieve this, since modern large discs can not be fully read without additional code.
The boot manager often presents the user with a menu of possible boot options. Next, it loads the operating system, which unpacks into memory, and sets the system functions as the essential hardware and the memory paging, before calling the start_kernel () function.
The start_kernel () function then performs most of the system configuration (interrupts, the rest of the memory management, device initialization, controllers, etc), before continuing the inactive and planner process separately, and the Init process (which runs in the user space).
The planner takes effective control of the management of the system, and the nucleus is asleep (inactive).
The Init process executes scripts (Scripts) necessary to configure all services and structures that are not operating system, in order to allow the user environment to be created and presented to the user with a login screen.
In the shutdown, Init is called to close all the functionalities of the user space in a controlled manner, again through scripts, after which the Init ends and the kernel executes the shutdown.

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

