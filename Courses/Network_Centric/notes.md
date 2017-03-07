---
layout: page
title: Network Centric Programming
permalink: /Courses/Network_Centric/
---

# Introduction

- This course covers coding network programs in the C programming language.
- Topics that the course covers
  - Files, IO, Network Communication
  - Socket Network programming
  - Network Server Design
    - Multi-threaded programs and synchronization
  - Secure Programming
  - Profiling and Performance Analysis
  - Remote Procedure calls

# Input and Output in C

## File Operations

- Key functions
  - fopen - returns pointer to FILE structure(file pointer)
  - fclose
  - fread
  - fwrite
  - fgetc / fputc
  - fgets / fputs
  - fseek / ftell



## Low-level File I/O Functions

- Unbuffered I/O
- Every read or write call invokes a system call
- Open files are identified by file descriptor(nonnegative integer)
- Shells follow this convention
  - 0 = STDIN_FILENO
  - 1 = STDOUT_FILENO
  - 2 = STDERR_FILENO

- System Calls
  - open
  - read
  - write
  - lseek
  - close

### fopen/open

- Both of these statements open a file and creates a file pointer to identify the location of the current file position in the file.
- The syntax from the fopen statement is
```C
FILE* fp = fopen(const char* pathname, const char* mode);
```
  - returns a file pointer (to buffer)
  - Mode
    - "r" - read only
    - "w" - write(create new file or overwrite)
    - "a" - write or append if file exists
    - "r+, w+, a+" - different read or write modes
- The syntax from the open statement is
```C
int fd = open(const char* pathname, int oflag, ...)
```
  - Oflags
    - Required: O_RDONLY, O_WRONLY, or O_RDWR
    - Optional: O_APPEND, O_CREAT, O_SYNC, O_EXCL

### fclose/close

- ```fclose(FILE* stream)```
- ```Close(int filedescriptor)```
  - cleans up kernel data structures
  - Files automatically closed if program ends

## Error Handling

- Most system call library functions return -1(or sometimes 0) when an error occurs
  - Must be checked after every function call
- The global errno variable contains an error number that describes why the function failed
  - Errno is only valid if an error has occurred
- Use strerr() or perror() functions to convert error numbers to meaningful strings
- Sample code for error Handling

```c
#include	<errno.h>
#include	"ourhdr.h"

int main(int argc, char* argv[])
{
     // … some library call here

	fprintf(stderr, "EACCES: %s\n", strerror(EACCES));

	// another example – perror directly prints to stderr
	errno = ENOENT;
	perror(argv[0]);

	exit(0);
}
```

## File Pointers and Seeking

- The system remembers the position in a file through a file pointer(32-bit offset), which automatically advances when you read or write
- These functions can query or modify the position of the pointer:

```C
long ftell(FILE* fp);
int fseek(FILE* fp, long offset, int whence);
void rewind(FILE* fp);
```

- In the fseek function, to access key locations of the file, we can use special codes in the offset section of fseek
  - SEEK_SET - beginning of file
  - SEEK_CUR - current file position
  - SEEK_END - end of file

# Files and Directories

## Getting File Metadata

- ```Int stat(char* filename, struct stat* buf)```
  - Fills in the stat data structures with information about file type, size, permissions, time, etc.

- The stat data structure is

```C
struct	stat
{
  dev_t		st_dev;
  ino_t		st_ino;
  mode_t	st_mode;
  nlink_t	st_nlink;
  uid_t		st_uid;
  gid_t		st_gid;
  dev_t		st_rdev;
  off_t		st_size;
  // SysV/sco doesn't have the rest... But Solaris, eabi does.
#if defined(__svr4__) && !defined(__PPC__) && !defined(__sun__)
  time_t	st_atime;
  time_t	st_mtime;
  time_t	st_ctime;
#else
  time_t	st_atime;
  long		st_spare1;
  time_t	st_mtime;
  long		st_spare2;
  time_t	st_ctime;
  long		st_spare3;
  long		st_blksize;
  long		st_blocks;
  long	st_spare4[2];
#endif
};
```

- lstat
  - Similar to stat, but does not follow links

- fstat
  - Used for already opened files

## File Types(modes)

- Regular file
- Directory file
- Character special file
  - device access, e.g serial port
- Block special file
  - device access, e.g disk
- FIFO
  - pipes
- Socket
  - Network connection
- Symbolic link
  - pointer to another file

- Using MACROS to test file types
  - ```S_ISREG(m)``` - is it a regular file?
  - ```S_ISDIR(m)``` - is it a directory?
  - ```S_ISCHR(m)``` - is it a character device?
  - ```S_ISBLK(m)``` - is it a block device?
  - ```S_ISFIFO(m)``` - is it a fifo?
  - ```S_ISLNK(m)``` - is it a symbolic link?
  - ```S_ISSOCK(m)``` - is it a socket?

- The OS needs to be able to distinguish the type of a file to be able to know what commands/operations can be performed on the file
  - No seek on FIFO or sockets
  - No write on directory
  - Open on symbolic link requires redirection

## Directory Manipulation in UNIX

- mkdir - create a directory
- rmdir - remove a directory
- opendir - open directory for reading
- readdir - read directory entries
- rewinddir - move pointer back to the beginning of the directory
- closedir - close directory after reading is complete
- chdir - set the working directory for the current process
- getcwd - get the working directory for the current process

- A simple code to access a library through system calls. This an emulation of the ls command

```c
#include	<sys/types.h>
#include	<dirent.h>
#include	"ourhdr.h"

int main(int argc, char* argv[])
{
	DIR* dp;
	struct dirent* dirp;

	if (argc != 2)
		err_quit("a single argument (the directory name) is required");

	if ( (dp = opendir(argv[1])) == NULL)
		err_sys("can't open %s", argv[1]);

	while ( (dirp = readdir(dp)) != NULL)
		printf("%s\n", dirp->d_name);

	closedir(dp);
	exit(0);
}
```

## Symbolic links

- Can span over the user's file system, because the user can create links to directories on other parts of their file system
- They are represented by special files
- Loops are easier to remove
- Symlink(actualpath, sympath) - creates a symbolic link to sympath and the link will be located at actualpath
- Readlink(pathname, ...) - reads sympath which is located at pathname
  - These files cannot be read with the open command

## Common file Operations

- access - access control check
- chdir - change directory
- chown - change owner of a directory
- open - open a file
- opendir - open directory
- remove - delete file or directory
  - also unlink(file only), and rmdir(directory only)
- rename - rename directory

## Hard Links

- Every directory entry points to an i-node(which represents a file)
  - Multiple entries can point to the same file(hard links)
- ```Link(existingpath, newpath)``` - creates an additional directory entry to an existing file

## Problem: Loops

- Recursive listing of files does not work
  - This means that one link is pointing to another link, and the other link is pointing back to the original link
- There is no easy way to fix this
  - Unlink does not remove links in a directories
  - rmdir removes links to directories only when they are empty
- Only root users can create hard links to directories

# Socket Programming

## Client-Server Model

![Client-Server Model](/resources/images/net_cent/client_server_model.png)

# Debugging

- What happens if we have a segmentation fault, this means that some portion of our code is trying to access a piece of memory that it does not have access to. Now how do we debug this and find the problem?

- One way to find the error is the use print statements to find which statement doesn't print to show the location of the error. However, this may get the job done, but is very difficult to use on code with a lot of lines and it is very time consuming to find the right place in the code.

- GDB is a tool which allows you to inspect the program state at the moment of failure.
  - Look at variable contents
  - Look at which function was executed
  - Look at register values to see which address caused the segfault

- GDB is used through these shell commands

- ```gcc -g mysource.c``` - compiles the source code with the gdb flag and gdb compatibility with the -g flag

- ```limit -c unlimited``` - enables core dumps when using the gdb debugger

- ```./a.out``` - execute the compiled code until segfault

- ```gdb a.out core``` - allows you to use gdb and look at the current state of the code when it had the segfault


# Processes



# Threads



# Locking

## MUTEX

- Acts as a lock for certain lines of code in a tread which makes sure that a thread accesses a shared variable when another thread is not using it, to avoid corruption of data.

- To create a lock, we would execute the following code

```C
//To create a MUTEX lock
pthread_mutex_t childsum_mutex = PTHREAD_MUTEX_INITIALIZER;
```

- To start the lock, place the following piece of code at the beginning of the portion of code which you would like to lock

```C
//Mark the beginning of the portion of code you want to lock
pthread_mutex_lock(&childsum_mutex);
```

## File Locks - "Record Locks"

- Synchronize access from multiple processes from shared memory
- Allows you to specify what portion of a file to lock to improve performance

## Deadlock

- Can occur is threads acquire several locks for one operation

- Atomic instructions - thread safe instructions which already in your operating system
- Thread safe functions - functions which can be used without using a MUTEX lock
  - The only way to identify if a function is thread safe is to read the documentation for the function
  - A list of some functions that are NOT thread safe are listed on the man page for pthreads
