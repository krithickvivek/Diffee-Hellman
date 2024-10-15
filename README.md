# Diffee-Hellman
## AIM:

To perform key exchange using the Diffie-Hellman method.

## ALGORITHM:

1. Select a public prime number p and base g.
2. Alice and Bob choose private keys.
3. Compute public keys using the formula public_key = (g^private_key) % p.
4. Exchange public keys.
5. Compute the shared secret using shared_secret = (public_key_received^private_key) % p.

## PROGRAM:
```
#include <stdio.h>
#include <math.h>

// Function to compute (base^exp) % mod
long long int powerMod(long long int base, long long int exp, long long int mod) {
    long long int result = 1;
    while (exp > 0) {
        if (exp % 2 == 1) result = (result * base) % mod;
        base = (base * base) % mod;
        exp /= 2;
    }
    return result;
}

int main() {
    long long int p, g, privateA, privateB, publicA, publicB, sharedSecretA, sharedSecretB;

    // Step 1: Input public prime (p) and base (g)
    printf("Enter a prime number (p): ");
    scanf("%lld", &p);
    printf("Enter a base (g): ");
    scanf("%lld", &g);

    // Step 2: Alice and Bob input private keys
    printf("Enter Alice's private key: ");
    scanf("%lld", &privateA);
    printf("Enter Bob's private key: ");
    scanf("%lld", &privateB);

    // Step 3: Compute public keys
    publicA = powerMod(g, privateA, p); // Alice's public key
    publicB = powerMod(g, privateB, p); // Bob's public key

    // Step 4: Compute shared secrets
    sharedSecretA = powerMod(publicB, privateA, p); // Alice's shared secret
    sharedSecretB = powerMod(publicA, privateB, p); // Bob's shared secret

    // Step 5: Display shared secret
    printf("Shared secret computed by Alice: %lld\n", sharedSecretA);
    printf("Shared secret computed by Bob: %lld\n", sharedSecretB);

    if (sharedSecretA == sharedSecretB) {
        printf("Key exchange successful. Both shared secrets match!\n");
    } else {
        printf("Key exchange failed. Shared secrets do not match.\n");
    }

    return 0;
}


```
## OUTPUT:
![image](https://github.com/user-attachments/assets/55840cdb-fc98-440f-9898-4aa9ef7fbb9e)


## RESULT:

The program for the Diffie-Hellman algorithm is executed successfully, and Alice and Bob have securely derived a shared secret key.
