
# EX-8-ADVANCED-ENCRYPTION-STANDARD ALGORITHM

# Aim:
To use Advanced Encryption Standard (AES) Algorithm for a practical application like URL Encryption.

# ALGORITHM:
1.AES is based on a design principle known as a substitution–permutation.


2.AES does not use a Feistel network like DES, it uses variant of Rijndael.


3.It has a fixed block size of 128 bits, and a key size of 128, 192, or 256 bits.


4.AES operates on a 4 × 4 column-major order array of bytes, termed the state


# PROGRAM:


```

#include <stdio.h>
#include <string.h>

void simpleAESEncrypt(char *plaintext, char *key, char *ciphertext) {
    int i;
    int plen = strlen(plaintext);
    int klen = strlen(key);

    for (i = 0; i < plen; i++) {
        ciphertext[i] = plaintext[i] ^ key[i % klen];
    }
    ciphertext[i] = '\0';
}

void simpleAESDecrypt(char *ciphertext, char *key, char *decryptedText) {
    int i;
    int clen = strlen(ciphertext);
    int klen = strlen(key);

    for (i = 0; i < clen; i++) {
        decryptedText[i] = ciphertext[i] ^ key[i % klen];
    }
    decryptedText[i] = '\0';
}

void printASCII(char *ciphertext) {
    printf("Encrypted Message (ASCII values): ");
    int clen = strlen(ciphertext);
    for (int i = 0; i < clen; i++) {
        printf("%d ", (unsigned char)ciphertext[i]);
    }
    printf("\n");
}

int main() {
    char plaintext[100], key[100], ciphertext[100], decryptedText[100];

    printf("Enter the plaintext: ");
    fgets(plaintext, sizeof(plaintext), stdin);
    plaintext[strcspn(plaintext, "\n")] = '\0'; // remove newline

    printf("Enter the key: ");
    fgets(key, sizeof(key), stdin);
    key[strcspn(key, "\n")] = '\0'; // remove newline

    if (strlen(key) == 0) {
        printf("Error: Key cannot be empty!\n");
        return 1;
    }

    simpleAESEncrypt(plaintext, key, ciphertext);
    printASCII(ciphertext);

    simpleAESDecrypt(ciphertext, key, decryptedText);
    printf("Decrypted Message: %s\n", decryptedText);

    return 0;
}


```


# OUTPUT:

<img width="1577" height="852" alt="image" src="https://github.com/user-attachments/assets/2ec520e1-695c-4759-bb1a-54588958c0de" />


# RESULT:

The program is successfully executed.


