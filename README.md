# EX.-NO-1-E-IMPLEMENTATION-OF-RAIL-FENCE-ROW-COLUMN-TRANSFORMATION-TECHNIQUE

|

## AIM:
  To write a C program to implement the rail fence transposition technique.
  
## ALGORITHM:

STEP-1: Read the Plain text.

STEP-2: Arrange the plain text in row columnar matrix format.

STEP-3: Now read the keyword depending on the number of columns of the plain text.

STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.

STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

## PROGRAM:
```c
#include <stdio.h>
#include <string.h>

int main() {
    char text[100], enc[100], dec[100];
    int rails, len, i, j, k, row, dir;

    printf("Enter plaintext: ");
    scanf("%s", text);

    printf("Enter number of rails: ");
    scanf("%d", &rails);

    len = strlen(text);

    // Encryption
    k = 0;
    for(row = 0; row < rails; row++) {
        dir = 1;
        int r = 0;
        for(i = 0; i < len; i++) {
            if(r == row) enc[k++] = text[i];
            if(r == 0) dir = 1;
            else if(r == rails-1) dir = -1;
            r += dir;
        }
    }
    enc[k] = '\0';
    printf("Encrypted: %s\n", enc);

    // Decryption
    char temp[100];
    int mark[100] = {0};

    // Mark positions
    for(row = 0; row < rails; row++) {
        dir = 1; int r = 0;
        for(i = 0; i < len; i++) {
            if(r == row) mark[i] = 1;
            if(r == 0) dir = 1;
            else if(r == rails-1) dir = -1;
            r += dir;
        }
    }

    // Fill characters in order
    k = 0;
    for(i = 0; i < rails; i++) {
        for(j = 0; j < len; j++) {
            if(mark[j] == 1) {
                temp[j] = enc[k++];
                mark[j] = 0;
            }
        }
    }

    // Read zigzag
    row = 0; dir = 1; k = 0;
    for(i = 0; i < len; i++) {
        dec[k++] = temp[i];
    }
    dec[k] = '\0';

    printf("Decrypted: %s\n", dec);

    return 0;
}
```

## OUTPUT:
<img width="505" height="252" alt="image" src="https://github.com/user-attachments/assets/2f859476-d69f-4240-bfe5-b439ec32ff58" />


## RESULT:
  Thus the rail fence algorithm had been executed successfully.
