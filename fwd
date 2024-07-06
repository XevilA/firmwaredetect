#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/utsname.h>

void get_kernel_version() {
    struct utsname buffer;
    if (uname(&buffer) != 0) {
        perror("uname");
        exit(EXIT_FAILURE);
    }
    printf("Kernel Version: %s\n", buffer.release);
}

void get_firmware_version() {
    FILE *fp;
    char path[1035];

    fp = fopen("/sys/class/dmi/id/bios_version", "r");
    if (fp == NULL) {
        perror("Failed to open /sys/class/dmi/id/bios_version");
        exit(EXIT_FAILURE);
    }


    if (fgets(path, sizeof(path) - 1, fp) != NULL) {
        printf("Firmware Version: %s", path);
    } else {
        perror("Failed to read firmware version");
    }

  
    fclose(fp);
}

int main() {
    get_kernel_version();
    get_firmware_version();
    return 0;
}
