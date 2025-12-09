#include <stdio.h>
#include <fcntl.h>
#include <unistd.h>
#include <sys/stat.h>
#include <dirent.h>

int main() {
    int fd;
    struct stat st;
    struct dirent *de;

    /* open file */
    fd = open("sample.txt", O_CREAT | O_RDWR, 0644);
    write(fd, "Hello\n", 6);

    /* lseek */
    lseek(fd, 0, SEEK_SET);

    /* fcntl example: get flags */
    int flags = fcntl(fd, F_GETFL);
    printf("File flags: %d\n", flags);

    /* stat */
    stat("sample.txt", &st);
    printf("File size: %ld bytes\n", st.st_size);

    close(fd);

    /* directory listing */
    DIR *d = opendir(".");
    printf("Files in current directory:\n");
    while ((de = readdir(d)) != NULL) {
        printf("%s\n", de->d_name);
    }
    closedir(d);

    return 0;
}

OUTPUT
File flags: -1
File size: 64 bytes
Files in current directory:
.
..
.bash_logout
.bashrc
.profile
