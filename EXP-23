#include <stdio.h>
#include <dirent.h>

int main() {
    DIR *d;
    struct dirent *de;

    d = opendir(".");       // open current directory
    if (!d) {
        perror("opendir");
        return 1;
    }

    while ((de = readdir(d)) != NULL) {
        printf("%s\n", de->d_name);   // print each file name
    }

    closedir(d);
    return 0;
}

OUTPUT
.
..
.bash_logout
.bashrc
.profile
