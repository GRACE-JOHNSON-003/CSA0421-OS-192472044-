#include <stdio.h>

int main() {
    FILE *src, *dest;
    char ch;

    src = fopen("a.txt", "r");
    dest = fopen("b.txt", "w");

    while ((ch = fgetc(src)) != EOF) {
        fputc(ch, dest);
    }

    fclose(src);
    fclose(dest);

    printf("Copied Successfully");
    return 0;
}

Output
Copied Successfully
