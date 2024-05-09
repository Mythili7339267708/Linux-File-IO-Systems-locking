# Linux-File-IO-Systems-locking
Ex07-Linux File-IO Systems-locking
# AIM:
To Write a C program that illustrates files copying and locking

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux IO Systems locking

### Step 3:

Execute the C Program for the desired output. 

# PROGRAM:


```
#include <unistd.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <stdlib.h>
#include <stdio.h> // Include for debugging

int main() {
    char block[1024];
    int in, out;
    int nread;

    // Open input file
    in = open("filecopy.c", O_RDONLY);
    if (in == -1) {
        perror("Error opening input file");
        exit(1);
    }
    printf("Input file opened successfully\n");

    // Open or create output file
    out = open("file.out", O_WRONLY|O_CREAT, S_IRUSR|S_IWUSR);
    if (out == -1) {
        perror("Error opening/creating output file");
        exit(1);
    }
    printf("Output file opened/created successfully\n");

    // Read from input file and write to output file
    while ((nread = read(in, block, sizeof(block))) > 0) {
        printf("Read %d bytes from input file\n", nread);
        if (write(out, block, nread) != nread) {
            perror("Error writing to output file");
            exit(1);
        }
        printf("Wrote %d bytes to output file\n", nread);
    }

    if (nread == -1) {
        perror("Error reading from input file");
        exit(1);
    }

    printf("End of input file\n");

    // Close files
    close(in);
    close(out);

    printf("Files closed successfully\n");

    exit(0);
}

```
## OUTPUT


![image](https://github.com/Mythili7339267708/Linux-File-IO-Systems-locking/assets/144260246/6fd9697c-045a-45c1-a841-cd146cbca5f3)


![image](https://github.com/Mythili7339267708/Linux-File-IO-Systems-locking/assets/144260246/2800ac6c-5340-4c29-976b-ce1660a1ba4c)


![image](https://github.com/Mythili7339267708/Linux-File-IO-Systems-locking/assets/144260246/2dbb9001-376a-4fb4-9891-79d71d849e38)


![image](https://github.com/Mythili7339267708/Linux-File-IO-Systems-locking/assets/144260246/ea3dc61f-2670-4cfe-8567-ad8def11fd32)






# RESULT:
The programs are executed successfully.
