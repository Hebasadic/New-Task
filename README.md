#include <stdio.h>
#include <stdlib.h>

// Function to create and write data to a file
void create_and_write_file(const char *filename, const char *data) {
    FILE *file = fopen(filename, "w"); // "w" mode to create or overwrite the file
    if (file == NULL) {
        printf("Error opening file for writing.\n");
        return;
    }
    fprintf(file, "%s", data); // Write data to the file
    printf("Data written to %s.\n", filename);
    fclose(file); // Close the file
}

// Function to read data from a file
void read_file(const char *filename) {
    FILE *file = fopen(filename, "r"); // "r" mode to read the file
    if (file == NULL) {
        printf("Error opening file for reading or file does not exist.\n");
        return;
    }

    char ch;
    printf("Data read from %s:\n", filename);
    while ((ch = fgetc(file)) != EOF) {
        putchar(ch); // Print each character from the file
    }
    printf("\n");
    fclose(file); // Close the file
}

// Function to append data to a file
void append_to_file(const char *filename, const char *data) {
    FILE *file = fopen(filename, "a"); // "a" mode to append to the file
    if (file == NULL) {
        printf("Error opening file for appending.\n");
        return;
    }
    fprintf(file, "%s", data); // Append data to the file
    printf("Data appended to %s.\n", filename);
    fclose(file); // Close the file
}

int main() {
    const char *filename = "example.txt";

    // Create and write data to the file
    create_and_write_file(filename, "This is the first line of the file.\n");

    // Read data from the file
    read_file(filename);

    // Append new data to the file
    append_to_file(filename, "This is an appended line.\n");

    // Read the data again after appending
    read_file(filename);

    return 0;
}

