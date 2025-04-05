# 🧵 Java Multithreading - Basics

---

## 🔹 CPU

- The CPU is the brain of the computer.
- It performs all operations like arithmetic, logic, conditional execution, etc.
- Everything that happens, happens through the CPU.

---

## 🔹 Core

- The core is like a mini CPU inside the CPU.
- Earlier there used to be a single-core CPU.
- Now we have multi-core CPUs like dual-core, quad-core, etc.
- Multi-core allows parallel processing.

---

## 🔹 Program

- A program is a set of instructions that perform a task.
- Examples: Microsoft Word, OBS Studio, etc.

---

## 🔹 Process

- A process is a program in execution.
- When we double-click on Word, a process starts in the OS.
- Process is the active state of a program.

---

## 🔹 Thread

- A thread is the smallest unit of execution within a process.
- A process can contain multiple threads.
- Each thread can perform a task independently.
- Threads inside a process share the same resources (memory, files, etc).
- Example (MS Word):
  - One thread for text writing
  - One for spell-checking
  - One for auto-saving

---

## 🔹 Tab Example

- Imagine you're using a browser like Chrome.
- When you open multiple standard tabs, each one functions like a thread — they run independently but share the same memory and resources of the parent browser process.
- For example, one tab may be loading a website while another is playing a video.
- However, when you open an incognito tab, it often runs as a separate process.
- That incognito process can have its own threads (multiple incognito tabs) that share resources among themselves, but remain isolated from the standard browsing process.
- So:
  - Standard tabs → threads within a process.
  - Incognito tabs → separate process (but threads within that process still share resources).

---

## 🔹 Real-life Multitasking

- OBS Studio recording your screen.
- Simultaneously you're watching YouTube.
- This is multitasking — both programs are running together.

---

## 🔹 Multitasking Definition

- Running multiple **processes** simultaneously is called multitasking.
- This is enabled by the Operating System.
- If the OS is single-tasking, then only one task runs at a time.
- If the OS is multitasking, multiple programs can run concurrently.
- Example:
  - While watching a video, you're also writing code.
- This is possible only because the CPU has **multiple cores** or is fast enough to **context switch**.
- Earlier with single-core systems, multitasking was due to time sharing between processes using context switching. Now, through multiple cores true parallelism is achieved and system multitasks concurrently.
- Multitasking can also be achieved using multithreading.

---

## 🔹 Summary

- CPU: Brain of the computer
- Core: Mini processor inside CPU (multiple cores = parallelism)
- Program: Set of instructions
- Process: Running instance of a program
- Thread: Lightest unit of execution within a process
- Multitasking: Multiple processes running simultaneously

---


