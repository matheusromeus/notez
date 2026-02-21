All the parts of your computer inside the case are connected by a *bus*. Physically, the bus is what you plug your controller cards into PCI, for Peripheral Component Interconnection, is the bus used on most modern PCs.

In order for programs to run, then, they have to be *in core* (in memory, RAM).

The first thing a computer has to do when it is turned on is start up a special program called an *operating system*

Your computer knows how to boot because instructions for booting are built into one of its chips, the BIOS (or Basic Input/Output System) chip.
The BIOS chip tells it to look in a fixed place, usually on the lowest-numbered hard disk (the *boot disk*) for a special program called a *boot loader* (under Linux the boot loader is called Grub or LILO). The boot loader is pulled into memory and started. The boot loader's job is to start the real operating system. The boot loader then loads the kernel. 

Most of the messages emitted boot time are the kernel autoprobing your hardware through the I/O ports, figuring out what it has available to it and adapting itself to your machine.

After the kernel fully loads, the kernel hands control to a special process called 'init' which spawns several housekeeping processes.

The init process's first job is usually to check to make sure your disks are OK. Disk file systems are fragile things; if they've been damaged by a hardware failure or a sudden power outage, there are good reasons to take recovery steps before your Unix is all the way up.

A daemon is a background process that runs continuously and performs specific functions or tasks without direct user interaction.

Init's next step is to start several *daemons*.

Init starts a copy of a program called **getty** to watch your screen and keyboard. The next step is to start up various daemons that support networking and other services. 

The next step is to start up various daemons that support networking and other services. The most important of these is your X server. X is a daemon that manages your display, keyboard, and mouse. Its main job is to produce the color pixel graphics you normally see on your screen.
When the X server comes up, during the last part of your machine's boot process, it effectively takes over the hardware from whatever virtual console was previously in control. That's when you'll see a graphical login screen, produced for you by a program called a *display manager*.

when logging in, the login name is looked up in a file called /etc/passwd, which is a sequence of lines each describing a user account.

only the kernel has access to your hardware, user processes have to request the kernel for permission if they have to do anything other than interacting with memory. these requests are called as system calls.

You will run programs in one of two ways: through your X server or through a shell. Often, you'll actually do both, because you'll start a terminal emulator that mimics an old-fashioned textual console, giving you a shell to run programs from. 

The shell is called the shell because it wraps around and hides the operating system kernel. It's an important feature of Unix that the shell and kernel are separate programs communicating through a small set of system calls. This makes it possible for there to be multiple shells, suiting different tastes in interfaces.

The shell is just a user process. Let's say you type ‘ls’ and Enter to invoke the Unix directory lister. The shell applies its built-in rules to figure out that you want to run the executable command in the file /bin/ls. It makes a system call asking the kernel to start /bin/ls as a new child process and give it access to the screen and keyboard through the kernel. Then the shell goes to sleep, waiting for ls to finish. When /bin/ls is done, it tells the kernel it's finished by issuing an exit system call. The kernel then wakes up the shell and tells it it can continue running. The shell issues another prompt and waits for another line of input.

When you're running programs through the X server rather than a shell (that is, by choosing an application from a pull-down menu, or double-clicking a desktop icon), any of several programs associated with your X server can behave like a shell and launch the program. I'm going to gloss over the details here because they're both variable and unimportant. The key point is that the X server, unlike a normal shell, doesn't go to sleep while the client program is running — instead, it sits between you and the client, passing your mouse clicks and keypresses to it and fulfilling its requests to point pixels on your display.

It's the operating system's job to watch for such interrupts (a keystroke). For each possible kind of interrupt, there will be an interrupt handler, a part of the operating system that stashes away any data associated with them (like your keypress/keyrelease value) until it can be processed.

Every kind of interrupt has an associated priority level. Lower-priority interrupts (like keyboard events) have to wait on higher-priority interrupts (like clock ticks or disk events). Unix is designed to give high priority to the kinds of events that need to be processed rapidly in order to keep the machine's response smooth.

In your operating system's boot-time messages, you may see references to IRQ numbers. You may be aware that one of the common ways to misconfigure hardware is to have two different devices try to use the same IRQ, without understanding exactly why.

Here's the answer. IRQ is short for "Interrupt Request". The operating system needs to know at startup time which numbered interrupts each hardware device will use, so it can associate the proper handlers with each one. If two different devices try use the same IRQ, interrupts will sometimes get dispatched to the wrong handler. This will usually at least lock up the device, and can sometimes confuse the OS badly enough that it will flake out or crash.

# <span style="font-family:SFUIText-Bold;"><b><u>About multi tasking</u></b></span>

Computers can only do one task (or process) at a time. But a computer can change tasks very rapidly, and fool slow human beings into thinking it's doing several things at once. This is called timesharing. One of the kernel's jobs is to manage timesharing. It has a part called the scheduler which keeps information inside itself about all the other (non-kernel) processes

One of the kernel's jobs is to manage timesharing. It has a part called the scheduler which keeps information inside itself about all the other (non-kernel) processes in your zoo. Every 1/60th of a second, a timer goes off in the kernel, generating a clock interrupt. The scheduler stops whatever process is currently running, suspends it in place, and hands control to another process.

1/60th of a second may not sound like a lot of time. But on today's microprocessors it's enough to run tens of thousands of machine instructions, which can do a great deal of work. So even if you have many processes, each one can accomplish quite a bit in each of its timeslices.

In practice, a program may not get its entire timeslice. If an interrupt comes in from an I/O device, the kernel effectively stops the current task, runs the interrupt handler, and then returns to the current task. A storm of high-priority interrupts can squeeze out normal processing; this misbehavior is called thrashing and is fortunately very hard to induce under modern Unixes.

In fact, the speed of programs is only very seldom limited by the amount of machine time they can get (there are a few exceptions to this rule, such as sound or 3-D graphics generation). Much more often, delays are caused when the program has to wait on data from a disk drive or network connection.

An operating system that can routinely support many simultaneous processes is called "multitasking". The Unix family of operating systems was designed from the ground up for multitasking and is very good at it — much more effective than Windows or the old Mac OS, which both had multitasking bolted into them as an afterthought and do it rather poorly. Efficient, reliable multitasking is a large part of what makes Linux superior for networking, communications, and Web service. Your operating system also has to divide them in space, so that processes can't step on each others' working memory.The things your operating system does to solve this problem are called memory management.