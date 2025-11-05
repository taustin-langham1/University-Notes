

## Agenda

1. Isolation Capabilities
	1. MPU vs MMU, CHERI
2. Secure Boot
3. Firmware Updates

## Isolation

we do not want
- an application to interfere with the state of the operating system
- the os to interfere with our application
- functionality to interfere / be interfered with
	- e.g., the network stack - prime target for remote code execution

### How do non-embedded systems provide isolation?

Hardware
- CPU protection rings
	- provides kernel space and user-space
- Memory management unit allowing for virtual memory
	-  each process gets its own memory space
- Kernel
	- executing a system call requires a swap into kernel space before returning to user-space


### virtual memory

- every process gets their own virtual memory space
- not possible for other processes to access it (isolation)
- the cpu via mmu maps virtual memory to:
	- ram
	- nothing
	- hardware peripherals

### Isolation on embedded systems

- embedded cpus rarely come with a MMU, instead use a memory protection unit (MPU)
- an MPU lets you  define different memory regions and set permissions on them
	- for example, you may have a combination of read, write and execute
	- these permissions can be set at two levels, privileged, and unprivileged
	- only a limited number of regions
	- MPUs can only be configured by privileged code


### Limitations

MPUs can be hard to configure
	can only be configured in privileged state, but os fails to change to lower privilege for applications (RIOT)
No protection in some contexts (e.g., interrupt handlers)
peripherals
- some memory regions unprotected
- minimum 32B regions mean peripherals with smaller memory use cannot be protected
Need to frequently reconfigure MPU
	every time there is a context switch
	relatively high overhead

