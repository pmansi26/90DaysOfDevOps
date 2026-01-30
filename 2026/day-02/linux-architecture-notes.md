DAY-2
Tasks:-
1.	The core componets of Linux
•	Kernel :-
	What:- The kernel is the core(heart) of Linux.
	Why:- Applications cannot talk directly to hardware so kernel is needed to control CPU, memory , disk and devices safely 
	How:- Receives requests from the user programs ,Decides CPU time , allocates memory , communicates with hardware using drivers.
•	User Space:-
	What:- It is a space where users and application run
	Why:- To keep system safe and stable , Prevent user programs from damaging hardware.
	How:- users runs commands or apps.
•	Init/Systemd:-
	What:-Systemd(or init) is the first process started by the kernel(pid=1). 
	Why:-  System needs a manager to keep services running.
	How:- Starts during boot
o	Launches system services(network , ssh , docker).
o	Monitors and restarts failed services.

2.	How process are created and managed
	What:- A process is a running program.
	Why:- uses processes so it can
o	Run many programs at the same time
o	Keep the system stable
	How:- You can run a command
o	Kernel creates a process
o	Kernel gives it CPU time
o	Process ends when work is done.
•	Process States:-
	New :- Process is just created.
	Running :-  Process is executing on CPU.
	Waiting / Sleeping :- Process is waiting for input (keyboard , disk , network).
	Stopped :- Process is paused manually or by system .
	Terminated :- Process has finished or is killed.
	Zombie :- A process that has finished execution , but its entry still exists in the system.
•	Ubuntu / Linux Process Management Commands
	ps → show running processes
	top → live process view
	htop → interactive process view
	kill PID → stop a process
	nice → set process priority
	renice → change priority
	bg → run process in background
	fg → bring process to foreground
