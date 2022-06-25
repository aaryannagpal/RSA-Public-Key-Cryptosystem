# RSA Public Key Cryptosystem

RSA (Rivest–Shamir–Adleman) is an asymmetric public-key cryptosystem that is widely used for secure data transmission.

In a public-key cryptosystem, the encryption key is **public** and distinct from the decryption key, which is kept **private**. 

## Idea of RSA

The idea of RSA is based on the difficulty in factorizing a large integer. We create this integer by multiplying 2 large prime numbers with each other.

Both the public and private keys are derived from the same integer.

## Proofs of Correctness

### Assuming that we know these theorems:

- For any 𝑛 > 1, 𝑖𝑓 gcd⁡(𝑎, 𝑛) = 1, then the equation 𝑎𝑥 ≡ 1 mod n has a unique solution modulo 𝑛. Otherwise, it has no solution. This unique number 𝑥 is called the multiplicative inverse of a modulo 𝑛

- Fermat’s Theorem for Prime Numbers

- Chinese Remainder Theorem

- xy 𝑚𝑜𝑑 𝑚 = (𝑥 𝑚𝑜𝑑 𝑚)(𝑦 𝑚𝑜𝑑 𝑚)

### The Proof
$$𝑴^{𝒆𝒅} \equiv 𝑴 \textrm{ mod } 𝒏$$

Here, $p$ and $q$ are huge prime numbers. 

We assume  $n = pq$ and $m = (p − 1)(q − 1)$

For $e$ and $d$, they are multiplicative inverses modulo $m$.

Now, for some $k$ :

$$𝑒𝑑 = 1 + 𝑘𝑚 = 1 + 𝑘(𝑝 − 1)(𝑞 − 1)$$

Thus if $M \not\equiv 0 \text{ 𝑚𝑜𝑑 } p$, we have:


$$𝑀^{𝑒𝑑}   ≡ M(M^{p−1})^{k(q−1)} \text{ 𝑚𝑜𝑑 }  p$$ 

 $$\equiv 𝑀(1)^{𝑘(𝑞−1)} \text{ 𝑚𝑜𝑑 }  𝑝$$
 
 $$ \equiv 𝑀 \text{ 𝑚𝑜𝑑 } 𝑝      $$           

If $𝑀 \equiv 0 \text{ 𝑚𝑜𝑑 } 𝑝$,
we anyway have that $𝑀^{𝑒𝑑}≡ 𝑀 \text{ 𝑚𝑜𝑑 } 𝑝$,

Repeating the same argument,

$$𝑀^{𝑒𝑑} \equiv 𝑀 \text{ 𝑚𝑜𝑑 } 𝑞$$

Hence,

$$𝑀^{𝑒𝑑} \equiv 𝑀 \text{ 𝑚𝑜𝑑 } 𝑝𝑞 \equiv 𝑀 \text{ 𝑚𝑜𝑑 } 𝑛$$

## Our RSA

### Generating the prime numbers

Let 
$𝑝$
and 
$𝑞$ 
be our large prime numbers.

To check whether these numbers are prime, we use the ***Fermat’s Primality Test***

#### Fermat’s Primality Test

If $𝑝$
is prime, then,


$$𝑎^{𝑝−1} \equiv 1 \text{ 𝑚𝑜𝑑 } 𝑝$$


for all 
$𝑎 \in \mathbb{Z}_𝑝^{∗}$

## Efficiency

Both encryption and decryption require repeated multiplications (modulo $𝑛$) 
of $𝑥$
-bit numbers.

For encryption, multiplication of 2, followed by reduction modulo
$𝑛$. Both take time complexity $𝜪(𝒙^𝟐)$.

For decryption, the $𝑥$
-bit would undergo $𝑑$
multiplications. As $𝑑$
is of complexity $𝑛$
, we get time complexity $𝜪(n𝒙^𝟐 )$.

## Security

RSA is not a impenetrable cryptosystem and thus faces a few security threats:

- If $𝒎^𝒆$ is strictly less than the modulus 𝒏, ciphertexts can be decrypted easily by taking the 𝒆th root of the ciphertext over the integers.

- If someone asks access to the private key 𝒅 to decrypt some harmless ciphertext, one can decrypt another message using the same key, due to the multiplicative property$^1$ in RSA.

- If one obtains the private exponent 𝑑, any private key can be generated against a public key by simply factoring the modulus 𝑛=𝑝𝑞.

- If the same clear-text message is sent to 𝑒 or more recipients in an encrypted way, and the receivers share the same exponent 𝑒, but different 𝒑,  𝒒 and therefore 𝒏, then it is easy to decrypt the original clear-text message via the Chinese remainder theorem$^2$.


###### 1. $\text{If } m_1 \text{ and }  𝑚_2  \text{ are ciphertexts, then according to the property, }𝑚_1^𝑒 𝑚_2^𝑒 = (𝑚_1 𝑚_2 )^𝑒 (𝑚𝑜𝑑 𝑛)$
###### 2. Chinese remainder theorem states that if one knows the remainders of the Euclidean division of an integer 𝒏 by several integers, then one can determine uniquely the remainder of the division of 𝒏 by the product of these integers, under the condition that the divisors are pairwise coprime!

# References

- https://en.wikipedia.org/wiki/RSA_(cryptosystem)
- https://www.geeksforgeeks.org/rsa-algorithm-cryptography/
- https://en.wikipedia.org/wiki/Chinese_remainder_theorem
- RSA key values and Time Complexity - https://www.youtube.com/watch?v=-NZApqGCYeA


