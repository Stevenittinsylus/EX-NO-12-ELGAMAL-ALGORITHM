0# EX-NO-12-ELGAMAL-ALGORITHM

## AIM:
To Implement ELGAMAL ALGORITHM

## ALGORITHM:

1. ElGamal Algorithm is a public-key cryptosystem based on the Diffie-Hellman key exchange and relies on the difficulty of solving the discrete logarithm problem.

2. Initialization:
   - Select a large prime \( p \) and a primitive root \( g \) modulo \( p \) (these are public values).
   - The receiver chooses a private key \( x \) (a random integer), and computes the corresponding public key \( y = g^x \mod p \).

3. Key Generation:
   - The public key is \( (p, g, y) \), and the private key is \( x \).

4. Encryption:
   - The sender picks a random integer \( k \), computes \( c_1 = g^k \mod p \), and \( c_2 = m \times y^k \mod p \), where \( m \) is the message.
   - The ciphertext is the pair \( (c_1, c_2) \).

5. Decryption:
   - The receiver computes \( s = c_1^x \mod p \), and then calculates the plaintext message \( m = c_2 \times s^{-1} \mod p \), where \( s^{-1} \) is the modular inverse of \( s \).

6. Security: The security of the ElGamal algorithm relies on the difficulty of solving the discrete logarithm problem in a large prime field, making it secure for encryption.

## Program:
```
#include <stdio.h>

long long mod(long long b,long long e,long long m){
    long long r=1;
    while(e){
        if(e&1) r=r*b%m;
        b=b*b%m;
        e>>=1;
    }
    return r;
}

int main(){
    long long p,g,a,A,k,m,c1,c2,d;

    printf("p,g,a,m,k: ");
    scanf("%lld%lld%lld%lld%lld",&p,&g,&a,&m,&k);

    A = mod(g,a,p);

    c1 = mod(g,k,p);
    c2 = m * mod(A,k,p) % p;

    d = c2 * mod(c1,p-1-a,p) % p;

    printf("Pub:%lld\nEnc:(%lld,%lld)\nDec:%lld\n",A,c1,c2,d);

    return 0;
}

```


## Output:

<img width="359" height="198" alt="image" src="https://github.com/user-attachments/assets/2d5c0ac1-eccc-44be-9068-19717c210ca3" />



## Result:
The program is executed successfully.
