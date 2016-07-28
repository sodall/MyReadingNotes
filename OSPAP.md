# C1 Introduction
## Definition
- Referee
  - resource allocation
  - fault isolation
  - communication
- Illusionist
  - virtualization; virtual machine
  - atomic
- Glue

## Design Patterns
  - Cloud computing
  - Web browsers
  - Media players
  - Multi-user database systems
  - Parallel applications
  - Internet

## Evalutation Criteria
- Reliability and availability
  - mean time to failure (MTTF); mean time to repair (MTTR)
- Security and privacy
  - enforcement mechanism
  - security policy
- Portability
  - abstract machine interface (AMI)
    - application programming interface (API)
  - hardware abstraction layer (HAL)
- Performance
  - efficiency; overhead
  - fairness
  - response time and throughput
  - predictability
- Adoption
  - network effect
    - proprietary
    - open system
- Tradeoffs

## History
  - Runtime libraries
  - Multi-user OS
    - batch OS: direct memory access (DMA)
    - multitasking
    - virtual machine monitor
  - Time-sharing OS
  - Modern OS
    - desktop, laptop, netbook
    - smartphone
    - embedded systems
    - virtual machines
    - server
    - server clusters
  - Future OS
    - very large scale data centers
    - very large scale multicore systems
    - ubiquitous portable computing devices
    - very heterogeneous systems
    - very large scale storage

# C2 Kernel Abstraction
- The Central Role: protection
- OS kernel: full access to HW; trusted to do anything

## Process
- executable images: a sequence of machine instructions, and static data with their initial values
- process is an instance of a program
- process control block: info about a particular process

## Dual-mode Operation
- user-mode: processor checks each instruction to verify that the instruction is permitted to be performed by that process
- kernel-mode: protection checks turned off

### HW minimal requirement:
- privileged instructions
  - concept: instructions available in kernel-mode but not in user-mode
  - processor exception: processor to transfer control to an exception handler in the kernel
  - system call: processes transfer control into the kernel
- memory protection
  - base and bounds:
    - base: specifies the start of the process's memory region
    - bound: length
    - unable to:
      - expandable heap and stack
      - memory sharing
      - non-relative memory address
  - virtual address
- timer interrupts
  - HW timer: set to interrupt the processor after a specified delay

## Safe control transfer
### User to kernel mode
- exceptions: any expected condition caused by user program behavior
  - powerful tool for virtualization (of HW), virtual machine and memory management
- interrupt: an asynchronous signal to the processor that some external event has occured that may require its attention
  - polling: the kernel could loop checking each IO device to see if an event has occurred
- system calls: any procedure provided by the kernel that can be called from user-level

### Kernel to user mode
- new process
- resume after an exception, interrupt or system call
- switch to a different process
- user-level upcall

### Safe mode switch
- context switch:
  - limited entry
  - atomic changes to processor state
  - transparent, restartable execution
- interrupt vector
- interrupt stack
- interrupt masking
  - disable interrupt
  - enable interrupt
- HW support for saving and restoring registers
  - x86 processor status word
  - pushad, popad, iret
  - interrupt handlers: top and bottom halves

### System calls
- calling convention
- pair of stubs: two short procedures that mediate between two environments
  - kernel stub tasks:
    - locate system call arguments
    - validate parameters
    - copy before check; Time of Check Time of Use, TOCTOU attack
    - copy back any results
    
### Starting a new process
- copy arguments into user memory
- transfer control to user-mode

### Upcalls
- concept: virtualized interrupts and exception
- UNIX: signals; Windows: asynchronous events
- immediate event delivery:
  - preemptive user-level thread package
  - asynchronous I/O notification
  - interprocess communications
  - user-level exception handling
  - user-level resource allocation policy
- signals
  - types of signals: defined by kernel
  - handlers: defined by process
  - signal stack: allocated by user
  - signal masking: automatically
  - processor state: kernel provides to the handler

### Future directions
- fine-grained protection
- application-layer sandboxing
- HW support for virtualization

# C3 Programming Interface
  
**Read on Page 101**
