Implement DES Encryption and Decryption
## AIM:
         Implementation of Pseudorandom Number Generation Using Standard library.
## ALGORITHM:
•	Key: 64 bits, but only 56 bits are used (the remaining 8 bits are parity bits).
•	Block Size: 64 bits.
•	Rounds: 16 rounds of permutations and substitutions.
1.Initial Permutation (IP): The 64-bit plaintext block is permuted using a fixed initial permutation table.
2.Rounds (16 iterations):
•	The 64-bit block is split into two 32-bit halves.
•	Each round involves:

o	Expansion: Expanding the right 32-bit half into a 48-bit block.
o	XOR: The expanded block is XORed with a 48-bit round key.
o	Substitution: The result is passed through 8 S-boxes to produce a 32-bit block.
o	Permutation: The 32-bit block is permuted.
o	XOR: The result is XORed with the left 32-bit half.
o	Swapping: The left and right halves are swapped.
3.Final Permutation (FP): After 16 rounds, the final result is permuted using a final permutation table.

## PROGRAM:
```
#include <stdio.h>
#include <string.h>

void simpleAESEncrypt(char *plaintext, char *key, char *ciphertext)
{
    int i;
    for (i = 0; i < strlen(plaintext); i++) 
    {
        ciphertext[i] = plaintext[i] ^ key[i % strlen(key)]; 
    }
    ciphertext[i] = '\0'; 
}

void simpleAESDecrypt(char *ciphertext, char *key, char *decryptedText)
{
    int i;
    for (i = 0; i < strlen(ciphertext); i++) 
    {
        decryptedText[i] = ciphertext[i] ^ key[i % strlen(key)]; 
    }
    decryptedText[i] = '\0'; 
}

void printASCII(char *ciphertext) 
{
    printf("Encrypted Message (ASCII values): ");
    for (int i = 0; i < strlen(ciphertext); i++) 
    {
        printf("%d ", (unsigned char)ciphertext[i]); 
    }
    printf("\n");
}

int main() 
{
    char plaintext[100], key[100], ciphertext[100], decryptedText[100];

    printf("Enter the plaintext: ");
    scanf("%s", plaintext);

    printf("Enter the key: ");
    scanf("%s", key);

    simpleAESEncrypt(plaintext, key, ciphertext);
    printASCII(ciphertext);  

    simpleAESDecrypt(ciphertext, key, decryptedText);
    printf("Decrypted Message: %s\n", decryptedText);

    return 0;
}


   ```


## OUTPUT:
 ![image](https://github.com/user-attachments/assets/cffb83e8-870a-47b2-8ec8-b636cd0cd778)


## RESULT:
The program to implement DES encryption and decryption is executed successully.


