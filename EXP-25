#include <stdio.h>
#include <sys/stat.h>

void show_perms(mode_t m) {
    printf("Owner : %c%c%c\n",
        (m & S_IRUSR) ? 'r' : '-',
        (m & S_IWUSR) ? 'w' : '-',
        (m & S_IXUSR) ? 'x' : '-');

    printf("Group : %c%c%c\n",
        (m & S_IRGRP) ? 'r' : '-',
        (m & S_IWGRP) ? 'w' : '-',
        (m & S_IXGRP) ? 'x' : '-');

    printf("Others: %c%c%c\n",
        (m & S_IROTH) ? 'r' : '-',
        (m & S_IWOTH) ? 'w' : '-',
        (m & S_IXOTH) ? 'x' : '-');
}

int main() {
    struct stat st;

    if (stat("test.txt", &st) == -1) {
        perror("stat");
        return 1;
    }

    printf("Permissions for test.txt:\n");
    show_perms(st.st_mode);

    return 0;
}

OUTPUT
stat: No such file or directory
