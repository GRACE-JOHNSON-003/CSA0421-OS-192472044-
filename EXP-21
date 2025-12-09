/* file_demo.c
   Small demo of UNIX file-management system calls.
   Demonstrates: open, write, read, lseek, fstat (stat), close, unlink
*/

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <fcntl.h>      // open
#include <unistd.h>     // read, write, close, lseek, unlink
#include <sys/stat.h>   // stat
#include <errno.h>

int main(void) {
    const char *fname = "demo.txt";
    const char *text1 = "Hello, UNIX syscalls!\n";
    const char *text2 = "Appending a second line.\n";
    char buf[64];
    ssize_t n;

    /* 1) Create/truncate and open file for writing */
    int fd = open(fname, O_CREAT | O_TRUNC | O_WRONLY, 0644);
    if (fd < 0) {
        perror("open for write");
        return 1;
    }

    /* 2) Write to file */
    n = write(fd, text1, strlen(text1));
    if (n < 0) {
        perror("write");
        close(fd);
        return 1;
    }
    printf("Wrote %zd bytes: %s", n, text1);

    close(fd);

    /* 3) Reopen for append and add another line */
    fd = open(fname, O_WRONLY | O_APPEND);
    if (fd < 0) {
        perror("open for append");
        return 1;
    }
    n = write(fd, text2, strlen(text2));
    if (n < 0) {
        perror("write append");
        close(fd);
        return 1;
    }
    printf("Appended %zd bytes.\n", n);
    close(fd);

    /* 4) Open for reading */
    fd = open(fname, O_RDONLY);
    if (fd < 0) {
        perror("open for read");
        return 1;
    }

    /* 5) Read the first 32 bytes */
    n = read(fd, buf, 32);
    if (n < 0) {
        perror("read");
        close(fd);
        return 1;
    }
    buf[n] = '\0';
    printf("Read first %zd bytes:\n%s", n, buf);

    /* 6) Use lseek to jump to file start */
    off_t pos = lseek(fd, 0, SEEK_SET);
    if (pos == (off_t)-1) {
        perror("lseek");
        close(fd);
        return 1;
    }

    /* Read whole file */
    n = read(fd, buf, sizeof(buf)-1);
    if (n < 0) {
        perror("read whole");
        close(fd);
        return 1;
    }
    buf[n] = '\0';
    printf("Full file contents (%zd bytes):\n%s", n, buf);

    /* 7) Metadata using fstat */
    struct stat st;
    if (fstat(fd, &st) < 0) {
        perror("fstat");
        close(fd);
        return 1;
    }
    printf("File size from fstat: %lld bytes\n", (long long)st.st_size);

    close(fd);

    /* 8) Delete file */
    if (unlink(fname) < 0) {
        perror("unlink");
        return 1;
    }
    printf("File '%s' removed.\n", fname);

    return 0;
}

OUTPUT
Wrote 22 bytes: Hello, UNIX syscalls!
Appended 25 bytes.
Read first 31 bytes:
Hello, UNIX syscalls!
AppendingFull file contents (47 bytes):
Hello, UNIX syscalls!
Appending a second line.
File size from fstat: 49 bytes
File 'demo.txt' removed.
