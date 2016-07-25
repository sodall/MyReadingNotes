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
  - system call: processes transfer control into the kernel
- memory protection
- timer interrupts

**Read on Page 51**
