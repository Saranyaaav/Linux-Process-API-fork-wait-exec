# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to print process ID and parent Process ID using Linux API system calls
```
// C Program to print process ID and parent Process ID using Linux API syatem calls
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
int main(void)
{	//variable to store calling function's process id
	pid_t process_id;
	//variable to store parent function's process id
	pid_t p_process_id;
	//getpid() - will return id of calling function
	process_id=getpid();
	//getppid() - will return process id of parent function
	p_process_id=getppid();
	//printing the process ids
//printing the process ids
	printf("The process id: %d\n",process_id);
	printf("The process id of the parent function: %d\n",p_process_id);
	return 0;}
```

## OUTPUT
![Screenshot 2024-04-02 155914](https://github.com/Saranyaaav/Linux-Process-API-fork-wait-exec/assets/144870813/5b7dd0ec-9280-4e2b-b567-6837d674ba08)

## C Program to create new process using Linux API system calls fork() and exit()
```
//C Program to create new process using Linux API system calls fork() and exit()
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
int main()
{
    int pid;
    pid=fork();
    if (pid==0)
    {
        printf("Iam child, my pid is %d\n",getpid());
        printf("My parent pid is : %d\n",getppid());
        exit(0);
    }
    else{
        printf("I am parent, my pid is %d\n",getpid());
        sleep(100);
        exit(0);
    }
}
```

## OUTPUT
![Screenshot 2024-04-02 160159](https://github.com/Saranyaaav/Linux-Process-API-fork-wait-exec/assets/144870813/236e1aaf-da59-4107-ad61-6eae3b74540c)

## C Program to execute Linux system commands using Linux API system calls exec() family
```
//C Program to execute Linux system commands using Linux API system calls exec() family
#include <stdlib.h>
#include <stdio.h>
#include <sys/wait.h>
#include <sys/types.h>
#include <unistd.h>
int main()
{
    int status;
    printf("Running ps with execlp\n");
    execl("ps","ps","ax",NULL);
    wait(&status);
    if (WIFEXITED(status))
        printf("child exited with the status of %d\n",WEXITSTATUS(status));
    else    
        puts("child did not exit succesfully\n");
    printf("Done.\n");
    exit(0);
}
```

## OUTPUT
![Screenshot 2024-04-02 160538](https://github.com/Saranyaaav/Linux-Process-API-fork-wait-exec/assets/144870813/2feed1dc-f374-4c54-8ad8-21b6a89b0023)

# RESULT:
The programs are executed successfully.
