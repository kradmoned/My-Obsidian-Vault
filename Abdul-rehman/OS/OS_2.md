OS_2
28/01/2026

# Blocking and Non Blocking

In Blocking , when something is requested, and till you don't do a specific command such as save till then it won't do anything
,To understand how these concepts operate at the kernel level, we have to look at the **System Call** interface and the **Device Status Table**, which is the kernel's "ledger" for managing I/O.

---

## 1. The Process via System Calls

When a user program needs to read data (e.g., from a disk), it doesn't talk to the hardware. It issues a **System Call** (like `read()`).

### Blocking I/O Flow

1. **The Call:** The process executes a system call. This triggers a **Trap**, switching the CPU to kernel mode.
2. **The Table Update:** The OS finds the device in the **Device Status Table** and marks it as **busy**.
3. **The Wait:** The OS moves the process to a **wait queue** for that device. The process's state changes from _Running_ to _Waiting_.
4. **The Interrupt:** While the process sleeps, the CPU works on other tasks. When the hardware finishes, it triggers a **Vectored Interrupt**.
5. **The Cleanup:** The **ISR** (Interrupt Service Routine) runs, moves the data to the process's buffer, and marks the device as **idle** in the status table. The process is then moved back to the _Ready_ queue.

### Non-Blocking I/O Flow

1. **The Call:** The process issues the `read()` call with a non-blocking flag.
2. **The Check:** The OS checks the **Device Status Table**.
3. **Immediate Return:** If the data isn't ready, the OS does **not** put the process to sleep. Instead, it immediately returns to the user program with an error code (e.g., `-1` with `errno` set to `EAGAIN`).
4. **Program Choice:** The program can then do other work and try the system call again later.

---

## 2. The Device Status Table

The **Device Status Table** is a kernel data structure that tracks every I/O device in the system. Each entry typically contains:

- **Device Type:** (e.g., Disk, Keyboard, Network Card).
- **Device Status:** (Idle, Busy, or Not Functioning).
- **Request Queue:** A list of processes waiting for this specific device.

### Interaction with Polling vs. Interrupts

- **In Polling:** The kernel looks at the Status Table, sees the device is "Busy," and stays in a loop constantly checking the hardware registers until the status in the table can be updated to "Idle."
- **In Interrupt-Driven:** The kernel updates the Status Table to "Busy" and then **context switches** to a different process. It only looks at that table entry again when the hardware "rings the bell" via an interrupt.

---

## Summary Table: System View

| Concept          | System Call Behavior                                   | Device Status Table Role                                       |
| ---------------- | ------------------------------------------------------ | -------------------------------------------------------------- |
| **Blocking**     | Suspends process; returns only when data is in buffer. | Links the process to the device's wait queue.                  |
| **Non-Blocking** | Returns immediately; data might not be ready.          | Checked once; if busy, return "Try again" code.                |
| **Polling**      | CPU loop checks hardware status registers.             | Table entry is updated by the CPU itself during the loop.      |
| **Interrupt**    | CPU performs other tasks after the call.               | Table entry is updated by the **ISR** when the device signals. |

---
