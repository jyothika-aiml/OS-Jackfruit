# Multi-Container Runtime (OS Jackfruit Project)

## Author

* **Name:** Jyothika M
* **SRN:** PES2UG24AM070

---

## Project Overview

This project implements a lightweight Linux container runtime in C with a long-running supervisor and a kernel-space memory monitor.

It demonstrates key Operating System concepts including:

* Process isolation
* Inter-process communication (IPC)
* Synchronization
* Memory management
* Scheduling

---

## System Architecture

### 1. User-Space Runtime (engine.c)

* Acts as the supervisor process
* Manages multiple containers
* Handles CLI commands
* Maintains container metadata
* Implements logging using producer-consumer model

### 2. Kernel-Space Monitor (monitor.c)

* Implemented as a Linux Kernel Module
* Tracks container processes
* Enforces memory limits (soft and hard)
* Communicates with user-space via ioctl

---

## Features

* Multi-container execution
* Supervisor-based container management
* CLI commands:

  * `start`
  * `run`
  * `ps`
  * `logs`
  * `stop`
* Logging using bounded-buffer (producer-consumer)
* Memory monitoring:

  * Soft limit warning
  * Hard limit enforcement (process termination)
* Scheduling experiment using nice values

---

## CLI Usage

```bash
engine supervisor <base-rootfs>
engine start <id> <rootfs> <command>
engine run <id> <rootfs> <command>
engine ps
engine logs <id>
engine stop <id>
```

---

## Files Included

* `engine.c` – Supervisor and runtime
* `monitor.c` – Kernel memory monitor
* `monitor_ioctl.h` – Shared ioctl definitions
* `Makefile` – Build configuration
* `cpu_hog.c` – CPU-intensive workload
* `memory_hog.c` – Memory stress test
* `io_pulse.c` – I/O workload
* `OS_Project_Report_Jyothika.pdf` – Screenshots and results

---

## Demonstration

All required screenshots are included in:

[OS_PROJECT_JYOTHIKA.pdf](./OS_PROJECT_JYOTHIKA.pdf)

The report covers:

1. Multi-container supervision
2. Metadata tracking (`ps`)
3. Logging system
4. CLI execution
5. Soft memory limit
6. Hard memory limit
7. Scheduling experiment
8. Clean termination

---

## Key OS Concepts Used

* Process Management (fork, exec, wait)
* Namespaces (isolation)
* IPC (pipes, sockets)
* Synchronization (mutex, buffer)
* Kernel programming (LKM)
* Memory monitoring (RSS tracking)
* Scheduling (nice values)

---

## Conclusion

This project integrates multiple core OS concepts into a working system. It demonstrates how user-space and kernel-space components interact to manage containers, enforce memory limits, and control execution behavior.

---

## Notes

* Implementation is designed for Ubuntu VM environment
* Screenshots are provided instead of live execution
