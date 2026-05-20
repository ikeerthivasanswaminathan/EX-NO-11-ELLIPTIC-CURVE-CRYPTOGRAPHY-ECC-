# EX-NO-11-ELLIPTIC-CURVE-CRYPTOGRAPHY-ECC

## Aim:
To Implement ELLIPTIC CURVE CRYPTOGRAPHY(ECC)

## ALGORITHM:

STEP-1: Elliptic Curve Cryptography (ECC) is a public-key cryptography technique based on the algebraic structure of elliptic curves over finite fields.

STEP-2: Initialization
Select an elliptic curve equation ( y^2 = x^3 + ax + b ) with parameters ( a ) and ( b ), along with a large prime ( p ) (defining the finite field).
Choose a base point ( G ) on the curve, which will be used for generating public keys.

STEP-3: Key Generation
Each party selects a private key ( d ) (a random integer).
Calculate the public key as ( Q = d × G ) (using elliptic curve point multiplication).

STEP-4: Encryption and Decryption
Encryption: The sender uses the recipient’s public key and the base point ( G ) to encode the message.
Decryption: The recipient uses their private key to decode the message and retrieve the original plaintext.

STEP-5: Security
ECC’s security relies on the Elliptic Curve Discrete Logarithm Problem (ECDLP), making it highly secure with shorter key lengths compared to traditional methods like RSA.

## Program:

```
#include <stdio.h>

long long mod(long long a, long long p) 
{
    return (a % p + p) % p;
}

int main() 
{
    long long p = 17;
    long long Gx = 5, Gy = 1;
    long long Pmx = 9, Pmy = 7;
    long long k = 4;
    long long C1x = mod(Gx * k, p);
    long long C1y = mod(Gy * k, p);
    long long C2x = mod(Pmx * k, p);
    long long C2y = mod(Pmy * k, p);
    printf("ELLIPTIC CURVE CRYPTOGRAPHY (ECC)\n\n");
    printf("Encrypted:\n");
    printf("C1 = (%lld, %lld)\n", C1x, C1y);
    printf("C2 = (%lld, %lld)\n", C2x, C2y);
    long long inv = 0;
    for(int i = 1; i < p; i++) 
    {
        if((k * i) % p == 1) 
        {
            inv = i;
            break;
        }
    }
    long long Px = mod(C2x * inv, p);
    long long Py = mod(C2y * inv, p);
    printf("\nDecrypted:\n");
    printf("Pm = (%lld, %lld)", Px, Py);
    return 0;
}
```

## Output:

<img width="1911" height="901" alt="ex11op" src="https://github.com/user-attachments/assets/7d6031b9-27db-41ca-acb6-4ef403963abb" />

## Result:
Thus, the implementation of Elliptic Curve Cryptography (ECC) had been executed successfully.
