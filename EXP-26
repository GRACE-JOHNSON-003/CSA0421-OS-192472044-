#include <stdio.h>
#include <stdlib.h>

int main() {
    FILE *file;
    char filename[100] = "file_demo.txt";
    char content[100];
    
    // 1. Create and write to a file
    file = fopen(filename, "w");
    if (file == NULL) {
        perror("Error creating file");
        return 1;
    }
    fprintf(file, "Hello, this is a sample file.\n");
    fclose(file);
    printf("File created and data written successfully.\n");

    // 2. Append to the file
    file = fopen(filename, "a");
    if (file == NULL) {
        perror("Error opening file for appending");
        return 1;
    }
    fprintf(file, "This line is appended.\n");
    fclose(file);
    printf("Data appended successfully.\n");

    // 3. Read from the file
    file = fopen(filename, "r");
    if (file == NULL) {
        perror("Error reading file");
        return 1;
    }
    printf("\nContent of the file:\n");
    while (fgets(content, sizeof(content), file)) {
        printf("%s", content);
    }
    fclose(file);

    // 4. Delete the file
    if (remove(filename) == 0) {
        printf("\nFile '%s' deleted successfully.\n", filename);
    } else {
        perror("Error deleting file");
    }

    return 0;
}
output:
File created and data written successfully.
Data appended successfully.

Content of the file:
Hello, this is a sample file.
This line is appended.

File 'file_demo.txt' deleted successfully.
