#include <stdio.h>
#include <string.h>

int main(int argc, char *argv[]) {
    if (argc != 3) {
        printf("Usage: %s <pattern> <file>\n", argv[0]);
        return 1;
    }

    char *pattern = argv[1];
    char line[256];

    FILE *fp = fopen(argv[2], "r");
    if (!fp) {
        perror("fopen");
        return 1;
    }

    while (fgets(line, sizeof(line), fp)) {
        if (strstr(line, pattern)) {   // check if pattern exists
            printf("%s", line);
        }
    }

    fclose(fp);
    return 0;
}

OUTPUT
Usage: /tmp/p0SgMEon51/main.o <pattern> <file>
