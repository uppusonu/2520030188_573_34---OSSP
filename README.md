Linux Debugging System

A menu-driven C command-line toolkit for demonstrating Linux process diagnostics, system and memory inspection, disk usage, Round Robin scheduling, inter-process communication, signals, POSIX threads, mutex synchronization, and a small tracked-allocation leak report.

Requirements

Ubuntu Linux (native installation or WSL2 with Ubuntu)

GCC compiler and Make

POSIX threads support (provided by the standard Linux development toolchain)

Install the build tools on Ubuntu:

sudo apt update
sudo apt install -y build-essential

Compile

cd linux_debugging_system_project
make

Equivalent direct compile command:

gcc -Wall -Wextra -Wpedantic -std=c11 -O0 -g -o linux_debugging_system linux_debugging_system.c -pthread

Run

./linux_debugging_system

Choose a menu option. For process inspection, enter a PID such as $$ is not accepted; use the numeric PID shown by echo $$ in another terminal, or enter the tool's own PID if displayed by the OS. The process listing option shows a short sample of visible /proc entries.

Output files

memory_leak_report.txt - allocation blocks intentionally left outstanding during the built-in leak demonstration. The demo reports the blocks, then frees them before returning.

linux_debug_report.txt - a snapshot containing the tool's PID details, kernel, uptime, memory and resource-usage fields.

Suggested demonstration order

Select 1 to show operating-system, kernel, CPU, RAM and resource information.

Select 2 and 3 to show /proc/meminfo and filesystem statistics.

Select 4 and enter a valid PID (for example, the PID of the tool itself, obtained from another terminal with pgrep -n linux_debugging_system).

Select 5 to list visible processes.

Select 6 and enter 3 processes with burst times 5, 8, 3, and a quantum of 2.

Select 7 to demonstrate parent-child IPC using a pipe.

Select 8 to demonstrate signal registration and delivery.

Select 9 to demonstrate two threads updating a shared counter under a mutex.

Select 10 to create memory_leak_report.txt and show the expected 2 blocks / 320 bytes in the report.

Select 11 to create linux_debug_report.txt.

Select 12 to explain all menu options, then 0 to exit.

Important scope note

The built-in memory tracker detects allocations made through TRACK_ALLOC in this program. It is an educational demonstration, not a replacement for a full external heap-analysis tool. For analysis of arbitrary C/C++ executables, use a dedicated tool such as Valgrind Memcheck where available.

Team

Roll number

Student name

2520030188

U. PRANEETH

2520030573

M. HARSHITH

2520030034

U. PRATHIK

Project guide: Dr. K. Anusha
Department: Computer Science and Engineering
Institution: K L (Deemed to be) University
