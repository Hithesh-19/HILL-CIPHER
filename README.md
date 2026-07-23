# HILL CIPHER
HILL CIPHER
EX. NO: 3 AIM:
 

IMPLEMENTATION OF HILL CIPHER
 
## To write a C program to implement the hill cipher substitution techniques.

## DESCRIPTION:

Each letter is represented by a number modulo 26. Often the simple scheme A = 0, B
= 1... Z = 25, is used, but this is not an essential feature of the cipher. To encrypt a message, each block of n letters is  multiplied by an invertible n × n matrix, against modulus 26. To
decrypt the message, each block is multiplied by the inverse of the m trix used for
 
encryption. The matrix used
 
for encryption is the cipher key, and it sho
 
ld be chosen
 
randomly from the set of invertible n × n matrices (modulo 26).


## ALGORITHM:

STEP-1: Read the plain text and key from the user. STEP-2: Split the plain text into groups of length three. STEP-3: Arrange the keyword in a 3*3 matrix.
STEP-4: Multiply the two matrices to obtain the cipher text of length three.
STEP-5: Combine all these groups to get the complete cipher text.

## PROGRAM 
```
#include <stdio.h>
#include <string.h>

#define MAX 100

int main()
{
    char msg[MAX];
    int n, i, j, k, t;
    int key[10][10], inverse[10][10];
    int plain[MAX], cipher[MAX], decrypted[MAX];

    /* Input Plain Text */
    printf("Enter Plain Text (CAPITAL letters only): ");
    scanf("%s", msg);

    /* Input Matrix Order */
    printf("Enter the order of the matrix: ");
    scanf("%d", &n);

    /* Input Key Matrix */
    printf("\nEnter the Key Matrix (%d x %d):\n", n, n);
    for (i = 0; i < n; i++)
    {
        for (j = 0; j < n; j++)
        {
            scanf("%d", &key[i][j]);
        }
    }

    /* Input Inverse Matrix */
    printf("\nEnter the Inverse Matrix (%d x %d):\n", n, n);
    for (i = 0; i < n; i++)
    {
        for (j = 0; j < n; j++)
        {
            scanf("%d", &inverse[i][j]);
        }
    }

    int len = strlen(msg);

    /* Padding with X if required */
    while (len % n != 0)
    {
        msg[len] = 'X';
        len++;
    }
    msg[len] = '\0';

    printf("\nPlain Text after padding : %s\n", msg);

    /* Convert letters to numbers */
    for (i = 0; i < len; i++)
    {
        plain[i] = msg[i] - 'A';
    }

    /* Encryption */
    for (i = 0; i < len; i += n)
    {
        for (j = 0; j < n; j++)
        {
            t = 0;

            for (k = 0; k < n; k++)
            {
                t += key[j][k] * plain[i + k];
            }

            cipher[i + j] = t % 26;
        }
    }

    printf("\nEncrypted Cipher Text : ");
    for (i = 0; i < len; i++)
    {
        printf("%c", cipher[i] + 'A');
    }

    /* Decryption */
    for (i = 0; i < len; i += n)
    {
        for (j = 0; j < n; j++)
        {
            t = 0;

            for (k = 0; k < n; k++)
            {
                t += inverse[j][k] * cipher[i + k];
            }

            decrypted[i + j] = t % 26;
        }
    }

    printf("\nDecrypted Text         : ");
    for (i = 0; i < len; i++)
    {
        printf("%c", decrypted[i] + 'A');
    }

    printf("\n");

    return 0;
}
```

## OUTPUT
<img width="1917" height="907" alt="Screenshot 2026-07-23 202858" src="https://github.com/user-attachments/assets/cf3a8155-2403-47a8-9407-3e7fcdf2e91c" />

## RESULT
Thus, implemented a C program to the hill cipher substitution techniques.
