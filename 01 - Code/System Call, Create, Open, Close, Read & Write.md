
### DEFINITION
System call are the calls that a program makes to the `sytem kernel` to provide the services to which the program does not have direct access. as example the input and output of a keyboard. 

----
### File Table Entry
This refers to a table used by the operating system (OS) to manage open files while a program is executing. When a file is opened using a system call such as `open`, the OS creates an entry in this table, which contains various information, including the file's location on the hard disk, the mode of access, and the offset. Each entry in the table is assigned a unique identifier known as a `file descriptor`. This number corresponds to the index of the file entry in the table. Whenever the program needs to read from or write to the file, it uses the `file descriptor` to access the appropriate entry.

When a process is started, the OS automatically opens three file descriptors (FD) that are important for communication with the user.

- fd 0 -> stdin, used to read data passed to the user
- fd 1 -> stdout, used to display results or outputs in the terminal
- fd 2 -> stderr, used to display error messages

By default, these FDs refer to a file called `/dev/tty`, which is a special file representing the terminal where the process is running. It acts as an intermediary, connecting the process to the terminal. **interface**.


---
based on
https://www.geeksforgeeks.org/input-output-system-calls-c-create-open-close-read-write/