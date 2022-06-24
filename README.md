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


$$𝑀^{𝑒𝑑}   ≡ M(M^(p−1))^k(q−1) \text{ 𝑚𝑜𝑑 }  p$$ 

 $$\equiv 𝑀(1)^𝑘(𝑞−1) \text{ 𝑚𝑜𝑑 }  𝑝$$
 
 $$ \equiv 𝑀 \text{ 𝑚𝑜𝑑 } 𝑝      $$           

If $𝑀 \equiv 0 \text{ 𝑚𝑜𝑑 } 𝑝$,
we anyway have that $𝑀^{𝑒𝑑}≡ 𝑀 \text{ 𝑚𝑜𝑑 } 𝑝$,

Repeating the same argument,

$$𝑀^{𝑒𝑑} \equiv 𝑀 \text{ 𝑚𝑜𝑑 } 𝑞$$

Hence,

$$𝑀^{𝑒𝑑} \equiv 𝑀 \text{ 𝑚𝑜𝑑 } 𝑝𝑞 \equiv 𝑀 \text{ 𝑚𝑜𝑑 } 𝑛$$

## Creating our RSA

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


