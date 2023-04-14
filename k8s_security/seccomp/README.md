## Understanding syscalls in linux 

### User space vs kernel space

<img src="space.png">

### How any user space operation is using syscall to let the kernel know 

<img src="sys.png">

### Demo of tracing a syscal 

```
root@ip-172-31-21-222:~# strace -c touch  /tmp/hello1.txt 
% time     seconds  usecs/call     calls    errors syscall
------ ----------- ----------- --------- --------- ----------------
  0.00    0.000000           0         3           read
  0.00    0.000000           0        22           close
  0.00    0.000000           0        18           fstat
  0.00    0.000000           0        22           mmap
  0.00    0.000000           0         3           mprotect
  0.00    0.000000           0         1           munmap
  0.00    0.000000           0         3           brk
  0.00    0.000000           0         6           pread64
  0.00    0.000000           0         1         1 access
  0.00    0.000000           0         1           dup2
  0.00    0.000000           0         1           execve
  0.00    0.000000           0         2         1 arch_prctl
  0.00    0.000000           0        19           openat
  0.00    0.000000           0         1           utimensat
------ ----------- ----------- --------- --------- ----------------
100.00    0.000000                   103         2 total

```
