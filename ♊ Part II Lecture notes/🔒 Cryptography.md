- Supervision Work
    - Supo 1
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NvFmXMRAigspiEUeWmFlruJYEQlSi2FUggDIFhvXChmTzTpl4qO0zzfkCODj8tG9iF5FHQ9OFnZ35-y-CmcN_xNtftgYAtTlZ2hS9LqhO_RKbzYiKTIULZNog6DgCyNh.png) 
            - a.) 
                - RTP:
$$P(C|M) =P(C) \iff P(M|C) = P(M)$$
                - 
                - Assume $P(M|C) = P(M)$: 
                - $$\therefore P(M) = \frac{P(C|M)P(M)}{P(C)}$$ 
                - $$P(C|M)P(M) = P(M)P(C)$$ 
                - If P(M) ≠ 0:
$$P(C|M)P(M) = P(M)P(C)$$
                - $$P(C|M) = P(C)$$ 
                - If P(M) = 0 then P(C|M) is undefined so P(C) is undefined. But as P(C) is greater than zero this cannot be the case.
                - 
            - b.)
                - $$P(C|M_0) = P(C|M_1) \iff \forall M. P(M|C) = P(M)$$ 
                - FIrst we prove ⇐:
                - Assume: $$\forall M. \ \ P(M|C) = P(M)$$ 
                - Instantiate M with $M_1$, then use what we learnt from question a:: $$P(M_1|C) = P(M_1) \iff P(C|M_1) = P(C)$$ 
                - Instantiate M with $M_2$. $$P(M_0 | C) = P(M_0)$$ 
                - Multiply them together: $$P(M_0 | C) P(C) = P(M_0) P(C|M_1)$$ 
                - $$\therefore P(C|M_1) = \frac{P(M_0 | C) P(C)}{P(M_0)} = P(C|M_0)$$  
                - As required.
            - 
        - 
- Misc notes 
    - Remember $\sum_M P(C|M) P(M) = ?$→$P(C)$ 
    - What should be inside this sum? 
$P(C) = \sum_M ?$→$$P(C) = \sum_M P(C|M)P(M)$$ 
- 
- Lecture 1 - Simple encryption schemes
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/R9x7XH2bqp73TO4mPCgTM4dM1Td7KMyvT5mArZy3vPER8QeWIbNaAF_Px6C7t9EcXDBrCJ4K-5dgrG4ngjBmTsHYL-kWSKIncMMGeDwBQmWqQYPv-pfp_CxgchIPu-4q.png) 
Note the eavesdropper is passive while the middle-person attack is **active.**
    - Encryption Schemes
        - Algorithm triples of (Generator, Encryptor, Decryptor) aimed at facilitating message confidentiality. Generator creates the keys.
        - For a private key
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vhYn8wSQlZAQ3LZJt3FMfNQIKDFN2dnAP2NSnzUOM6M0PTPDJeLTfL96_7nDNqs1054lfXx3957phg-BeqhN7yqWjt4OcHd5l8pw9LhDDWKe9V7IuZLfyTp2_3cZQWCR.png)
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/xFpRglDWTa8KWLBytxC4WKllmvs860zgHQ-uVp3Bd6VMifq2lUM7yKemmXTEhxAvJ2E_9mysqdjUB-N5Ki2GoS5xGy30UQtyYqaYH1Uy-ky5BHcHazi6AZMNkIq8ykC0.png) 
    - Message integrity schemes
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-DRVdJZUsc0jiPQsdSW0v17ei5hjgFrgmSHmlJWIYglD2LsfwhFmTvCPSExFTU2RBnp_stai6yBPgc8aq9ugLw6RUcZThaMoTmAaIkdTzDgYCzJnpRY_kbBhHRJj8c2u.png) 
        - Generate a message tag that can be recalculated.
    - Key exchange
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/BAJc68552_I3wPOPBej_vFwhE9xS8zEn8gBEEGndvztfwwIq5IW0XDKPF1dQiSuoc61mf6uNp1Ax4ZZFAOhRWnQgG9T9ITty4AmYYcWeuBwExmKlHeG2aP27uuov0zHW.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/RRtd0R_DbQLbtSI1h9CbvMRn_zJYubUfm9ymJtjwb0hsVgvEfg7e9WS0STIqmh8os7ANkRuA31grxUG-Aunf6i2O_o1g8kzLWioQPPw78WcR63oWhR41K6ToReEoIPDh.png) 
        - How does the Diffie-Hellman protocol work? ↓ 
            - Alice and Bob know of 3 large public numbers $p, q,g$. 
            - Alice and Bob both choose secret numbers $x$ and $y$ respectively. Where $0 < x < q , \ \  \ 0 < y < q$  
            - Then A ⇒ B:
$$PK_a = g^x \mod g$$
And B ⇒ A:
$$PK_b = g^y \mod p$$
These act as the public keys.
            - Both Alice and bob know that:
$$K = (g^y \ \mathrm{mod}\ p ) ^ x \ \mathrm{mod}\  p = (g^x \ \mathrm{mod}\ p ) ^ y \ \mathrm{mod}\ p$$
So they can calculate those independently with their secret keys and use the result a secret key between the two of them.
        - Private keys are symmetric keys while public/secret key pairs is asymmetric.
        - Ephemeral/session keys are only used briefly and are usually generated fresh for each communication session.
        - Static keys stay the same for months/years - generally part of a signed certificate wherein a trusted third party certifies the public key.
        - Master keys are used to generate other derived keys.
    - When is a cryptographic scheme secure?
        - If no adversary can...
            - Determine **any** character/bit of M 
            - Determine any information about M from C?
            - Compute **any **function of the plaintext M from ciphertext C 
        - For an integrity scheme:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/DWLYvWQlhL_fIJAW19JLBRR10EBS1BDDSIHsYnlrQU37t1O7CjnPe-qWtc56hoaNdKmKUqCV-vpOKWmZ8xSv2AC-Yp7yVEdQ8r-50vACvWSFK2PeOB2Z44FlPQ9D9tFu.png)
    - What capabilities may the adversary have?
        - Access to the ciphertext C
        - Access to some plain-text cipher text pairs where each cipher is produced with the same key.
        - Ability to encrypt plain-text of the adversary's choice (oracle access)
        - Ability to trick the user into decrypting some ciphertext of the adversary's choice (oracle access)
        - Modify C
        - Some amount of computation time
        - Knowledge of the algorithms used
    - Kerckhoffs' principles
        - **Requirements for a good traditional military encryption system** 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4Ghc0odLYTd2q0aNjpLR0UeOJJmvNt7K-1GWhzjzowfnNao9cuymvlm5B47403FCQ6LyKlDGLulbg5s0sBdF94GDejnC-C_yTP5vdRyO0qku2KFpjwaGz9vKDVP2ZaGB.png) 
            - What is the defining Kerhoff principle?→ __The system must not require secrecy and can be stolen by the enemy without causing trouble__ .
E.g. even if the way our protocol works is leaked, there's nothing you can do [😝](../😝.md) 
    - Message length
        - Why does message length pose a problem for encryption?→We always assume messages have a fixed length m - but note **a longer message will generate a longer cipher-text**. This is hard to hide & does provide some information - we can tell the difference between a tweet and an essay. File lengths alone can uniquely identify which website you've travelled to.
        - Why does compression cause a problem for encryption?→Compression can leak information - it gives us a relationship between the content and the **resulting size **of the output. For example, if I append my password to a known form and it's compressed - all we need to do is iterate over many text+password compressing until we find what we want. 
    - Historic Ciphers
        - Shift ciphers, i.e. Caesar Cipher. K=13 is rot 13
    - Transposition Cipher
        - K is some permutation of the letter position - the key space is n! where n is the permutation block length.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ePP7yAtBU-AaagBx5MhREuOHbI0ZD9_7ic2COfRG3C0fxnpLPyD0cFsSdezUGq7AOaktmyR8xB8phpErSboIGhzUhaAkObft9NgkPE0EOTCmDlplXcMYZHBvqq3um3-D.png)
        - If you have a black box transposition cipher where you can feed in strings and get output. If we have $\log_a(n)$ slots and an alphabet of size $a$ it would take you $\log_n(a)$ tries.
We just give each different position different letters.
    - Substitution Cipher
        - Key is permutation - swap one key for another
        - Examine the statistical properties of plain text - examine common letters, digrams and trigrams.
        - 
- Lecture 2 - Perfect secrecy + one time pads
    - Vigenere cipher
        - Multi character key - repeat the key to match the length of the plain-text key. Then do a modulo 26 addition to find the cipher text.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5-aERh0YICWogVcsiKBMGn_1LhCnaHKSqudVH0zEEW2E7wTLvOVZ0Jp_OEEfRloJ6DZIQhjfP3zYGLjYKHRserEWAsZ84OJv-G7j6gbERC0SgypMnfG2En9F1PRY0xT8.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sqCVCFhsjeaiuI6CTnarg85xti_ejICJW-6KnLTO1XZeukN9fbZvEXyywqRBMagraDiRfzDS-LLA8Ud-VHvJLkJDQiL8GN22X273e0YIPZetSSNcqvUcutXDFJ70fSXP.png) 
        - How can you break a Vigenere cipher given an encrypted message?↓ ↓ 
            - We will split the message into separate messages $M_1M_2...M_l$ encrypted by cipher texts $C_1C_2...C_l$. 
So first we must find the key length $l$.  
            - Take a guess at the key length and examine the letter frequency of each message $M$. 
            - Form a letter frequency histogram **from each group**. I.e. How many S's in group 1, group 2... group l.
If the letter frequency histograms are as they would be for your target language (except rotated) you've guessed right.
If not then the letter frequency histograms will be flatter (with less pronounced peaks!) as they are the combination of multiple rotated letter frequency histograms.
            - To decide if a histogram is flat or not you calculate the **index of coincidence **that is:$$IC(C_i) = \sum_{a\in A} p^2_{a,i}$$
 This is **minimal **if the probability of each letter is 1/26 (or one over the alphabet size). And is increased when peaks are present. This is also the probability that two randomly chosen letters from $C_i$ are identical.
            - Finally, pick the key length $l$ that leads to the highest $\frac{1}{l} IC(C_i)$ 
            - Finally, we have a monoalphabetic shift cipher - just use the language statistics.
If we don't know the language, we can look at the difference between the peaks in the histogram to find the difference between two consecutive letters. Then brute force.
    - Perfect secrecy
        - What is computational security→If the most efficient algorithm for breaking a cipher would take more time than possible to perform.
        - What is Unconditional security→Adversaries do not have enough information to decide from the cipher-text if one plain-text is more likely to be correct than the other.
Even with unlimited computation.
        - Consider a private-key encryption function with an encryption function and a decryption function:
$$\text{Enc: } \mathcal{K} \times \mathcal{M} \rightarrow \mathcal{C}, \ \ \text{Dec: } \mathcal{K} \times \mathcal{C} \rightarrow \mathcal{M}$$

Where the decryption function is simply the inverse of the decryption function.
        - Let  $\mathbb{P}(M)$, $\mathbb{P}(K)$ be the adversary's a-priori knowledge of the probability that the plaintext M or key K is used. 
        - The adversary can then calculate the probability of **any **ciphertext $C$ as:
$$\mathbb{P}(C) = \sum_{K \in \mathcal{K}} \mathbb{P}(K) \cdot \mathbb{P}(\text{Dec}_K(C))$$
I.e. iterate over **all **the possible keys and find the probability of that key **and **the message. 
I.e. generate a key, and see if the result looks like an actual plaintext message.
Note $\mathbb{P}(\text{Dec}_K(C))$ = $\mathbb{P}(M_K)$, E.g. the message for that decoding key:
$$\mathbb{P}(C) = \sum_{K \in \mathcal{K}} \mathbb{P}(K) \cdot \mathbb{P}(M_K)$$ 
        - And can also determine the conditional probability:
$$\mathbb{P}(C|M) = \sum _{\{K \in \mathcal{K} | M = \text{Dec}_K(C)\}} \mathbb{P}(K)$$
Iterate over **only **those keys which give the plaintext M. Then find the probability that all those corresponding keys could have been chosen.
        - The adversary can then find the probability of the **plaintext **given the **ciphertext:
** ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/DqSsn8LPOAmzgimlbBd4rY4jNiWGExH9GC5En-pJiF7JNJJ9IC6I0jvq8FRg0RctuVgeodc1nqoPpTxn84-ZzWLhgKLNSFUEF8J_KzImqHgE32rP2c-fQcWem5DiaBvn.png) 
        - What is the definition of perfect secrecy?→If for every probability distribution over $\mathcal{M}$ and every message $M \in \mathcal{M}$, and every ciphertext - with $\mathbb{P}(C)>0$ we have $$\mathbb{P}(M|C) = \mathbb{P}(M)$$
I.e. a ciphertext tells you **nothing **about the probability of a message - you get no new information. 
    - One time pads
        - Shannons theorem:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/lBz6ZldQDTmEzf1SZa9HHZJouQjbdIi76quQ4GB82P-U3IsAD2yW_s-3nFR3vonaOMgBEgAHYiR7gpMvxjvorkORcoWekfvDnv4XMbJDnMBsWBUPN0Z-mWtBeh_NMIux.png) 
        - What does Shannon's theorem? (Hint: it's about perfect secrecy)→A encryption scheme is perfectly secret **if and only if:
**$|\mathcal{M}| = |\mathcal{K}| = |\mathcal{C}|$ (I.e. the size of the sets of messages, keys and ciphertexts is the same). 
 ⇒ The generator chooses every K with equal probability.
 ⇒ For every message and every ciphertext there exists a **unique **key such that $C = \text{Enc}_K M$ 
I.e. for **every message **there are millions of keys which would encrypt that message to the same ciphertext (and they're all of the same probability). So the message could be a plot to destroy the world or a shopping list. 
        - The classic example is the one time pad:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bBWjIVZtIDz8Ts2lfgiuqi8CYGSY7dD_XToSPDtHeJDLxTuBru_PoGtP2RwISARypa59wf0YBFxBnA3eqNKcIIVdzNRsP2QjU2f8tZyS9mjw9WhbePSW89whzV4obY7R.png) 
        - What is the one time pad→A method of perfect secrecy where we uniformly randomly choose a binary key (with the same length as the message)  and encrypt our binary message via: $K \otimes M$ . Decrypt the same way.
There are millions of messages and key combinations which would give the same ciphertext.
        - Note that if x is a random bit with **any **probability distribution and y is a bit with a uniform 50/50 distribution. $x \otimes y$ will have **uniform probability! **This also works for addition modulo $m$ or **any finite group.** 
        - The problem with one time pads is that one bit is necessary for **each **message bit! This is hard to safely courier around. 
    - Random number generators
        - An idea would be to send a shorter key, and use that as a seed value for a random number generator. Split the message M into chunks as long as the random number generator and then XOR as usual?
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/O71RlgmH2Ymt7fUzv0ECKA4IlvF4ZoGzOWgySgxYUSg1cFb2DGhQMvenqU_n6k19Yx74yFOZDzr6D9FbbQWEnNk_LaJoA2kAvHy4tr_QiJyyBS4MeZ2jnThQUHeIuyZ9.png) 
    - Private key encryption schemes
        - A **private-key encryption scheme **is a tuple of random generetor, encryptor and decryptor it contains: 
            - The **key generation algorithm **which receives a security parameter L and outputs a key. Note that the $|K| \ge l$ - this security parameter controls how long the key is. 
            - **Encryption algo **maps the key and a plaintext to a ciphertext 
            - The **decryption algorithm **just does the inverse. 
        - What is a negligible function?→A function that $f : \N \rightarrow \R_{\ge 0}$ (outputs more than zero) which as n increases, gets arbitrarily close to zero faster than the inverse of any polynomial. I.e. Could be inverse exponential.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/1MeR1GRaHKxEZiiHDejXJIlPHn1jnK2onauffAycsOpcJ8q3qS6PtnbkQnHeWlGxHmkhg2OBnOAuZ5hmXNMXyt-tezhRQoNpLHc6nrecV2hmyKdkSEQx_sETiyrG0CMA.png) 
        - Security as a game
            - A challenger uses a encryption scheme and an adversary tries to demonstrate a weakness in the scheme. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/D9JVfnYuulzeGNCKkgtdPz6OAR4Fl-G9qbwgoRLKSnAvmB5bNuPTOeospL-DufpeUGnmDUwP8mnnJs1TlzAqYirpdp9oYFFzTDHrZdEorNkTA7sLI2zxUB0YtjQ1ad9D.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CsRuLsQP2LTpy3m5ZDCTKlb8cAX8vsxTpwxdFe8G8TgmpzGp5q8hLbvnPBvGRnpm-jfuRRdlj7SxI9nj1Cab8zyp-kGBeZ6BrdDYLRKUMUIf5Q7FDQqNVhegs0NfU7I7.png) 
            - We want that probability to be **very small **for every bit. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/O5F2NAKxpimg4fMiHiKtJr0RmkpuPsLrH8w7E3PcrkaHz74GBuPlEimSs3AgHDC7NP4lTpPPpHBzVsBt1kefMkahGcqf8i6oR05ZCeHUKHTbeGVdfhKOU-fBDFmtHKbL.png) 
            - 
    - 
    - 
    - 
    - Supervision 1 working:
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/fzo_jZvFj4Vcb31WrpcY6nqgr9aQOSvdnsCO1Hp5scixy7_FJuNRH6Ld32sphdWOZns0_4iCSXoLcRWMbeN79_Tn85aBYt2N3PX-tMsB0cX9peJAdAFszsfPC-qwheSO.png) 
    - We know: $$P(C|M) = \sum_{\{K | M = \text{Dec}_K(C)\}} P(K) \ \ = \frac{1}{26}$$
As for shift ciphers, given a ciphertext and a message there is **one **unique key which turns a given message into a given ciphertext.  
    - So we have: $$P(M|C) = \frac{P(M) \cdot \frac{1}{26}}{\sum_K \frac{1}{26} \cdot P(\text{Dec}_K(C))} = \frac{P(M)}{\sum_K P(\text{Dec}_K(C))}$$ 
    - We then note that the sum of the probabilities of each message is simply 1.
$$\sum_K \text{Dec}_K(C) = 1$$  
    - $$P(M|C) = \frac{P(M)}{1} = P(M)$$ 
    - 
    - $$P(M|C) = \frac{P(M)}{c}$$ 
- Lecture 3 - Pseudo Random generators
    - Indistinguishably in the presence of an eavesdropper
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tvCaC65j9rCQaHNK_9ggHE9YA851HY6P3pI6_KoOCf7wll30T8D5pMgaDORWo-CqoiY1ZtML5Ghj0Um-Wf3-qS728CSpGmHlaH8QE7H4RzTULeQ0RGPrisy2hVAUSZn4.png) 
        - Challenger generates a random bit and your key generator to create a new secret key.
        - The adversary is invited to send two messages, use the secret bit decides which message to pick.
        - Encrypt the chosen message, send it back and the adversary must decide which of the two messages were sent back.
        - A private-key encryption scheme offers above if for all probabilistic, polynomial-time adverseries (i.e. the function that decides what b was) there exists a negl function s.t:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4oYHxzKS1rxSqSTtEG7tJ2EBqMXcUjBEZHPwqglG3Dg5zWCHabEg2tiN4FaXij75M7q0-TysUcnmkrxji7nokO3by2R1PYYuRx5NWISvrjo7tnHMDWFrxS0AVh2W84zG.png)
        - **So, **as we increase the security parameter $l$ the adversary gets closer to making 50/50 guesses. 
    - Pseudo-Random generator I
        - G will take some binary string and expand it to by some polynomial expansion factor.
Input of length $n$ outputs $e(n)$ bits.  
            1. $e(n) > n$ 
            2. The probability that the **distinguisher **(Which attempts to check if the string was random or generated) is equally probable (with some negligible difference) to guess correctly and incorrectly for a random string vs a generated string.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bg-iO2yDNfMt9VSCxF_q9461aymDClW9UXFWYzgeg9HBEiWlezPT18q25bYhy3bPwqInmiztYa0tWaZ0z83QVlmLvvazY-DGtg71tidEp_4fa0fNzT19Gz7vLnMkRbdu.png)
Note the sub-R indicates random choice. 
        - A brute force distinguisher would iterate over all $2^n$ possible keys and check if they generate the input it received. 
What does the second formula mean, and what would the problem with such a distinguisher be? :
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/iZSFphQiTBt930ZIQNmYqUfOv80vfb3lYmHOTV1ykVAIqgkKr0QwNFfn6-_kB5k5bCauQgtk6gumSRGhLF9XXCJLs-kwgs-L9IvGJG6Hb10A_gLwNMYhVYPuxlB_xi73.png)
What's the problem with this?↓ ↓ 
            - We feed the pseudo-random generator $n$ bits, so it can only have $2^n$ possible outputs. Then we divide by all the possible strings that the **expanded **bits can produce (which we will brute force search will look through). 
Therefore, the second line gives the **probability **the distinguisher misfires and thinks a random string is pseudo-randomly generated.  
            - The distinguisher needs to be polynomial - this is an exponential algorithm. 
        - Encrypting using a pseudo-random generator
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bPl3-2ejAId156BClxmyk2VCa3aN0k1vDWbB6gbb6QUHw62KSWtmhYaBJCXywXb_JHIeGeJ0enXztFaNACzWYPbQv0w1hAtLxbGsiuWy2ATQKkbrRSr9VkVzkR62N37o.png) 
            - This method of encryption has "indistinguishable encryption in the presence of an eavesdropper" assuming G is a psudo-random generator.
        - What are stream ciphers?→We generate a random key, then use a pseudo-random generator with that key as input to generate a random string. This string is then XOR'd with our message to get the ciphertext.  
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yTW6JKIveJiw-2XT1DE-uf95LkLpQ-KoU2Yb8XS6URPoawkxcqUivhG2H7wq66DLpyI9t5uT-Um6b9Kc_aaRUy9TpXWwBKhe5558UxM3OIp_PrdJCTUrI6ng7p14bkHi.png)
        - How could we prove that a **stream cipher **has indistinguishable encryption in the presence of an eavesdropper? (Assuming it uses a pseudo-random generator)→Our stream cipher is encrypted using a pseudo random generator - Assume some decryptor for the cipher exists.
This decryptor could be used to distinguish messages from the pseudo-random generator - but this violates our assumption.
**Note: **These would all have to be polynomial time also.
        - Proving stream ciphers work
            - Claiming indistinguishability in the presence of an eavesdropper if G is a pseudo-random generator.
            - If $\Pi_\text{PRG}$ did not have I.P.E (indistinguishably...) then there would be an adversary for which:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/MaIkMWca0C3NR3UGn3sfElwpr02hDVTZVY-Ej8elvuMFfC0er_N6C8yt0e-v14zVzrN73OGfyQRXuX9CKyZw1q04ds2s_5eiiLPtoMmPzTPqgwoOiJV_ylSNKIni50OT.png)
And $\epsilon (l)$ Is **not **negligible. This just means the probability that **it wins **is more than negligibly above 1/2.
            - 
            - Explain the process of constructing a suitable adversary to prove that $\Pi_{PRG}$ (the encryption scheme using a pseudo-random generator) has indistinguishability in the presence of an eavesdropper **if **$G$ is a pseudo-random generator ↓ 
                - First, consider using **either **the pseudo-random generator to create input W **or** using truly random bits r. (Assume G is a pseudo-random generator)
                - Then ask the adversary to generate two messages $M_0$ and $M_1$ which we will randomly pick between to encrypt and send back. 
                - Encrypt our chosen message via: $M_b \oplus W$ and send it back to the adversary.  
                - If the adversary can distinguish between the two messages with a non-negligible probability, e.g.: $$\mathbb{P}(\text{PrivK}_{\mathcal{A}, \Pi}(l)=1)-\frac{1}{2} = \epsilon(l)$$
Then we've got output from a pseudo-random generator. 
                - For the case of random bits, we're essentially dealing with a one-time pad (as r is never seen by the adversary and is only used once) which is **perfectly secret**. So the probability of detection will be $\frac{1}{2}$.  
                - Note that this means $|P(D(r)=1) - P(D(G(K))=1|$ is equal to $|1/2 - (\epsilon(l) + 1/2)| = \epsilon(l)$ 
This is not negligible, so we contradict our initial assumption.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/fiN1z2R99Y8hSfkjhHRD8QdlK5i3ugYTtXoJVenjkwyOO938zWSalux_LjtlEDXwaaLsXQKhh-t4cImjpkbKEf0stal65rQJIkQpifZvZagjqJL70QUfQIluWf8eZh6h.png) 
    - Security Proofs through reduction
        - We have not shown the encryption scheme $\Pi _{PRG}$ is secure. 
        - We have shown that $\Pi _{PRG}$ has one particular security property, **if **G has another one. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NkMZihfo8KlEP3UZUYCIITVtqLBMwpyEeBnNN5ySqa9-hGs0jM-5AZ5cLk89moqpsdUUnIFsp-99F_zV8-kK94soNmTg7f6N1EefpDgd8u0mzJhibJzx9JDd789GNiGM.png) 
        - I.e. We have shown how to turn an attack against  $\Pi _{PRG}$  **into an attack against G** 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zu5arR4uoj7_Av9c2vgp0dRCAYVYPAFCPkjZa8HejGqpC9qfk5mdG19a0wQst1w1sXzF5ysbqyIcw0qzJ5d5eaEBzDUVYQMGsNiVjucJWTQEF7Vb-tBq__pkdKhhqWmP.png) 
    - Security for multiple encryptions
        - The game for I.I.P.A (indistinguishability in the presence of an eavesdropper) uses the fact that the **adversary only sees the output of a key once,** the key is then regenerated. For real usages, keys will be reused.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ht5V1-IYYPelQK3KxtNYFulumFeX9uGbQW7EdzJ45D6xDUYRZimUuCSP62_XB04hiIPQ0Rxo0fKhTfX7Z0-ZUU9jlaea53HJe97CkgaJIPzL7TtFsdZ-jSi3RflI0xSW.png) 
        - Here the adversary plays the game $t$ times, and generates new pairs of messages each time.
        - We say an encryption scheme $\Pi$ has  __indistinguishable multiple encryption in the presence of an eavesdropper __ if:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/n7_IWQ5iKoNT6uTBbKPL-8OKJKLFapp6u3lfpLFPicWMW12faOa6o3HqdkcguBiWRIKiz6kT-GPeqeCPP0GUcX6KgZ8_OjaSzJWRGsa3Sf7VRZIa7CoKvpiclFpgStGT.png) 
        - Do stream ciphers exhibit  __indistinguishable multiple encryption in the presence of an eavesdropper? __ Why or why not→No, we can consider sending 4 messages - the first pair are both all 1s from which we can figure out the key. Then we can use that key to distinguish the next 2. 
Or even simpler, first send a pair of messages $M_1$ then send $M_1$and some other message $M_k$ - then if the ciphertext is different in the second pair we know we've received $M_k$. 
        - Note that any **deterministic **encryption scheme fails this property. 
        - To solve this we do:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tGJbGmAst2DUmM3pFNKTJ2moCHib-TnnOpNlKlSoZ2bIrvZ6yTuXT_pcWI_GsKUZQQIQ4cSbZQxjRSmcTcQdeKxvdoDAfV4jY6vmfvB2NaOxdsPozXNHIUFNBgwue0OV.png) 
        - But there's a problem with maintaining a communication session using this - we don't have explicit access to its internal state.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/W0HpOnZ6OGTsobD6QGKeKgAz07R5_a83ARqZYBuRP6nwXGEjYpwUjT_xIVXE-AzxZnbUfAJUgeRYdw5a0iLDOjJ1D3ixB20HiiGEJb5CEoSDL4oRGj3cl-AJAfJ9_X3I.png) 
    - Security against chosen-plaintext attacks (CPA)
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/kxLLHC_4AGDAa0Y4CGDMcGZwYTnCbqAh1yImD02ikv_N77Nu4-V2A2gozVACnDsHNY8qyUa4KBZ4-6Ug-bOvfGZI0zDGGdEWscga4JSbfGxtawBLBMmvcqgJS_NzdJLT.png) 
        - The adversary can encrypt messages as it likes, before playing the normal game again.
If this is still secure, then the encryption scheme has  __indistinguishable multiple encryptions under a chosen-plaintext attack.__ 
    - Random functions and permutations
        - Consider all possible functions of  the form $f : \{0, 1\}^m \rightarrow \{0,1\}^n$  How many such functions are there?→LOOK OVER THIS, THE LOGIC IS:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ltSw3MQnAEoqQc8pcuaxXllbQFgdwZH0EMKlK48BTLCjrRTujNssdVRIsqi0MbGs71Aa1FEzqGwgZpCYMC0Djv8pdNhyXbgiV-yQIS9eeOb8ddK6ibSn79kkN8B274-E.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/f8TIA4g_yo3MAVpCJ9EdHEBCKFUCAXJrQGlJjBFRMAzd08TWa8aPsYCYfdaaHY4gqNik_V0cq9gwQb4WG5LoVB06Gwq7_eCdP0gSOTCHzB9ZSq4dHcdFh7RYw-1i8cWI.png) 
        - What is a pseudo-random function?→A fixed efficiently computable function $$F: \{0, 1\}^k \times \{0, 1\}^m \rightarrow \{0, 1\}^n$$
It depends on the **key**. Each choice of the key leads to a different function $F_K$. 
        - We standardise the security parameter to $n$ for clarity - i.e. all lengths are $n$. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Xj_ChcqYisqWlZYdu_veh2JS2W2GJJkWxLrQdbCdG_U6-sQbpc8tej99TdREqU-OZPh-Yq10V8IjlwgG8UJVUNZjXkZPnJbJn751726IjsnP9oTdnlHQa8xErYDnLwT3.png)
        - What is oracle access to a function?→The adversary can given an arbitrary amount of inputs to the function, and look at the output. 
        - What is this saying?![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KA3jtYgHKKe4iKJn9fgixrbOX-o1bivWggKPVeJnGE6cGH2INqwYZ7yB3yTwIVgtgWjeAv5PZqWPxgROsGFEgaqKdfZrwlpQDZRnj2fuVHMNUKkhS_S2B4ZvmiIV5E7x.png)→We have about the same chance of deciding if a **real** random function is being sampled or a pseudo random function with a specific key applied. Even with oracle access to those functions.
        - Note a full description of these functions would be $n\cdot 2^n$ bits long, which cannot be read in polynomial time. 
        - We define the following fixed-length private-key encryption scheme:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/nkvb3t9HG-5-XaYjCkqkYuUANlMNT0_PyMxiDr-pVon6lqpXg0m2hAJfa8oMSdOiJG2-_9eHfYVzRm2UIqFGzEHXrCkHIF3H0cVXCCuzZJkoyhP4pfogiUKWNuDpaWfK.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/o96TRLRKCLdRGD6BFkIh84geLnB07s_AVAoTOyb0CwV9B_otq9pwm4ntd1iekav6cR0ADe3Vb0RMVZIUYloB0tXPvMWwY8LPq0sd-pOHaO9diWvn1dbyiN_qPEsJl7Pz.png) 
    - 
    - 
- Lecture 4 - Block ciphers
    - CPA-secure encryption with a pseudo-random function 
        - Describe this method of encryption
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/goXsAeR0qJrJQ1cVD18N7qYXmH9pUIBsgzX4sPt-0qvKiIQCV7GySEx1KkdU43GmoDbz-sgrIij-TZh0SOk1NcLJi1AJdwSxU4cGd5qrSuDwGjOp4jvcqI3iVmaRvhMf.png)→We choose a random function key, we also choose a random input to our pseudo-random function. Our ciphertext is then the concatination of the random input, and the XOR of the keyed pseudo-random function with the message.
Then to decode it, we have our pseudo-random key already, and we can just look at the random input - we can then use those to decode M.  
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/r8vt8WMoXjYCgnrNkH6hn08amWWSj39Tup1etjb9YXvkiuf8rIKU9i27UJWgAXPLuWaqaHeXDh1U-c9wZYVEg5J6AMTUYD9R8-xDIywTmV3Wzu1XcFgJc9oeskesfkBP.png) 
        - If our pseudo-random function is a true random function - the best that the adversary can do is keep asking for new oracle values and hope that one of the values they tested shows up in the the real test: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/8ZSFRvUUR_HVPB8vvCF8XP3MuiLP_LVWuMp8RkDZYn0gfI22ekZsOph7-uTStImjAb4TY5musIeS20E8kv7v4vzM3-oqLp1yjbk3Fwu_6A6HfR57QhmQfB21pgo1sO-a.png)
Note that P(A and B) <= P(A)
        - We do a proof by contradiction, assuming we have an attacker with non-negligible performance against the encryption scheme - it will also have the limit above so:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KUGo-aa-76pNLO6cozIgCtoS--XnbpF780hpzX3XTskqSt9jsJ4-NRoizkTHjFx4G7O_IYL18j_vWe2dRisZSnYMloj_D4kS9p9RTOd-3OMZGHQMN2s637W2hKnl5R5_.png)

        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vzVP19leAE9F4hc_UrohOx5pQpYU5AjK40gn4mAsoB-YbcqNP34upFxJrZroUMFxCGJaH-8a_bhcopzHBiI3GaqOzYV7nPWiI019xlKJCSk9wlz1xadR7FVYUVWk6UQ7.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Lk0LRjx72NNfsGMlj9pdz5Ob62DKZ3ms2oKXqKhygkmkbaJ6bxr9FdQQxjigHwe_BpCOyQzZ4NY0KEG889Ml4ppUvcifg3MsBWbMDaQmbkcbgi_p_vXdczsaDg0r-IDo.png) 
    - Pseudo-random permutation
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/DT1_-mlcIQOMsTZj5l2NGoWrMrgGGRWJS2C5mCSz0ZhkjRDrctqB-xCGx0LmNAlynsfr42a0WTHDwbDu_ln2Bx75tGm2kXKFXUObY81R_kYUA2rHT0tyo7cqbiKvzrkY.png) 
        - What is a pseudo-random permutation?→A pseudo-random function where for every key, there is a 1-to-1 relationship for inputs and outputs. $F_K$ and $F_K^{-1}$ can be calculated with polynomial-time algorithms. 
Also, you can't distinguish some random $F_K$ from a random permutation.
        - A  __strong pseudo-random __ permutation remains indistinguishable even with oracle access to the inverse. 
        - Can you tell a pseudo-random function and a pseudo-random permutation apart?→Not in polynomial time - the chance of a repeated value when you've read $f(x)$ items is $2^{-n} \cdot \frac{f(x)}{2} (f(x) + 1)$ 
    - Birthday problem
        - We need to remember the **number of pairs **not the number of people. I.e. if 50 people meet in a room, there are 1960 combinations of two people - and thus the $1/365$ pales in comparison. It grows with the **square **of the number of people. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/MdeJWQJ_2BrPTwgV7kMAJ35fico3BvAPwsLJjRbkzfBYgiiH0rq9Q0O9isCvwBFvwNNIaJ-0tXUXUn0sHPv0eF9A9PJIARaZVpyuMHip0SQT8xcm3DLB7-sg_vHFq68E.png) 
        - When we reach the **square root **of the number of bins, we shoot up to near 1.  ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3CjEZiqXA5EsWj86VT9DSg9j-X5X8XX7fLtHvmlUzAlp2Q5SYbXec47pLD60tpFKpQN8FCbFceKPiLdcIT_CoDAbSPbgvf0sAdruSTHj-tILI8dku42Qjd2_vopEZONx.png) 
    - Iterating a random function
        - Consider a function that does the mapping:
$$f:\{1,...,n\} \rightarrow \{1,...,n\}$$
There are $n^n$ such functions. This is because each number can be mapped to **any **of the n numbers in the range (including itself) - so we have $n\times n \times ... \times n$ options. It's like factorial but we can repeat our choices. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7VYC5OZcAIcDR4c9zX9w21kmpI7Ovmdy6c11utUQVHTBh4bLp1na3tIzR1e7wEi8313o2SNWYJHqh8Z0xXvhdvjoa0FHThFXuFsjpJ9xugkZMwd8_eWXqp_nnGdYnaDa.png)
We can walk through this graph and find cycles.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/cKrU5u5UmnaW89SW2pm8SakAOjz9pU8TCRSvu2GNjCIrD87BWTDdxE4ezw_actED9f5evvfWXXqkmWB7RdrYSwxN8sGtiLfuvzCCWedvPy400qHOExObEW_WLiLv-FTF.png) 
    - Block ciphers
        - Practical, efficient algorithms that try to implement pseudo-random permutations are called block ciphers.
    - Feistel structure
        - We want to build a pseudo-random permutation which is **invertible **using pseudo-random functions which are **not **invertible. 
        - We split the plaintext block into two halves and apply the non-invertible function each round and XOR the results.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/cQiH3RJ1sF2aahDmJjoB0NhWQUkGOIFoiRSPOIftBxOhdx1BFS_j4oyotsaPi7DoIaHz92-nFzXqDPBYet0xYdQSM1k6B2ToHkOTOOw8elGBGj0SCuuoZO2S4VqgSShP.png) 
        - Note if you change a bit in $R_0$ after 2 rounds, **half the bits **will change! 
    - Data Encryption Standard (DES)
        - Block size of 64 bits and key size of 56 bits. Short key size! Led to limited protection against brute-force key searches.
        - Uses a 16-round Feistel structure. Its round function is **much simpler **that a pseudo random function. 
        - Designed for hardware implementation so the same circuit can be used for encryption + decryption.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zRe6cQLqw0gSdEfWYPDFb4fv8iRVEjjXjjZHBLSrwYMFZooFihF8WbM0d-AoUbL3oIvxOByeo9jZ-qz3vpocz-vdaDUsZMBZIg3G1rJq-EJjcJuFH12c2qRYZjqDbyCA.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/eK9t3NqiTlrgDHO9NEVaTevj-4HzLcOhC3hkdXu2en3TMWK63lkWKakgUPbsiN182nmfHN1G9DEFJkuVHHCHmRtQxdWu3iLtgxl6E84udHgQYqa2UAvacYIg-KRIUwq-.png) 
        - The overall key is split apart into a set of different keys:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/34DjTfpmi0b2BWqYtFEgOWt1kF154qejvdgVfZ2K_jEPj3Ndhz4B6ekxxu-fhwJVPArbbtWSpB9QXqSNWfqgjrP9CB0ebMejmeqWVjFqjTcDUwnQCJXH0aRb0avtk-QF.png) 
    - Strengthening DES
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yufxBaiwbyObi9ToLcOBB0Z7UCfp7KJ7PvWPMHfk56SjILqTpb1wdgT11PcydUb34u5R_ZWfSHSzk5Kl9ocvayD6bJ3U5UXqLAWuijhI57Jf5ubMqx_dUWucyNGn0W-p.png) 
        - 
    - 
    - 
- Lecture 5 - Different ways of using Block ciphers
    - Multiple Keys with DES
        - Is encrypting with DES multiple times as secure as using one long key. - **No** 
        - $$\text{C = DES}_{K_1}(\text{DES}_{K_2} (M))$$
How could we find the two keys if we knew M and C - and we were able to iterate over all $2^{56}$ bit combinations - but not all $2^{112}$ combinations.→Iterate over all possible ways to **encrypt **the message, also iterate over all possible way to **decrypt **the ciphertext. When both give the same value, you've got the two right keys.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/AY9QGZuBfxjjcfFi5rSflHsI7HZBzSyXg4uj8yjT5IlHJQerj3iIEa3tBGngBn_g2zPFkKeUCucjQYYbqc17sDlwKlzgUJbBiNVV2MySECQ9V895cdc9D3DokB-A-u5I.png)

        - Triple DES is used instead
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/lWcp9UGbbpyWcogkZ_HeieR0sOf0zI75UHCpGj74qOMvyGlEst7XGbC0PU6y5VpXCNIQbjbuWYC9Oske_KKboIYl-dPRu8jKZqXeTazNz3qoUsewwAQVG9aACb9ByM3-.png)
    - Advanced Encryption Standard (AES)
        - Successor block cipher competition - the Rijndael cipher appeared.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4qD7rOwdj1zUK89e5WwsqIdMOS8HD4mwPHCwJ9yBo7ABDOnKXPD03O5extMeZCPcfnGwjYgNgtYn_uo7fJUGLSFG8DTuvw9_C3y3yDGsONEakaOFD3SuAxylmxMdTjQb.png)
The multiplication with the 4x4 matrix is done on a binary Galois field - it's like addition but without the carry bits. Behaves the same as XOR.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/eJrXRNaZ-3knxHiA0pvknLpeMylq018WDSZfDDMa9wZY3KWv56wMdbMNDSQSl5GNUtNgVvf6ybAVWSyz5pBahe909Dimdd4BohYr-xyngaync6UIBS__EKAnd9xVSqoW.png) 
        - An actual implementation would be very expensive, but you can build up a table from substituted bits to the output of the matrix multiplication. Then add up the 32 bit outputs for different bytes.
Possible because the Matrix multiplication is linear.
    - Modes of operation
        - The problem comes if you have a message longer than 128 bits. Furthermore, **these schemes are deterministic.** 
        - Electronic Code Book
            - Simplest mode of operation for block ciphers, cut the message into m $n$-bit blocks.  
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Oruo3P_iSX4q6zhZp1P_pvMnSkyEs5YtLxO_Y9TcTfapRfHew7rB0uwtMgSgHDSQ5exCWWIbK6QpcCT9MvHeYoLIF3MjInOMImtEjQKXJyoUGjwPSgNqENdrkfnJ4rVd.png)
            - This is a deterministic encryption scheme - **so it is not CPA **(chosen plaintext attack) **secure.** You should not learn anything about the plaintext **if the ciphertext is repeated.** 
                - If you spot a repeated ciphertext, this gives you information. (i.e. Russia sent message to invade before, we read that again at some point we know what's coming)
                - Plaintext blocks are not uniformly distributed, ASCII has half 0's.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ayZVXTjdkitQ5ITmQueYxrX-96PTlU2XmbBTdW6SEWP6l6gnZVYpEroU-1ewn10KIYCl6An4IaS5VznTR680ZWOM2OT0ljxYsL4A2d1Zc27qSjtPlY6JZHYV2BKO7r8X.png)
We can recognise the background (all 0s)  - and we can tell non-background apart from background.
        - Randomised encryption
            - Any CPA secure algorithm must be randomised, encryption algorithm has access to an $r$-bit random value that is not predictable to the adversary. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/MjMljpzns8K7dEazoed0RFcJJedzkAkxCEFo9S1zMp8WhxYt8XSTH3_sksZNwk-BCxjT2V2IWD8KXafGhanq1Ante7ThxuQcIQthOJTog4Ang8qgaR0NpBb37apCFuFI.png) 
            - Note that with randomised encryption, the ciphertext **will **be longer than the plaintext. 
We attach the random value to allow for decryption:
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ziX_nyklkPAo3m2vj4EaGoaTfBHvlUQEI9vwvygUN0DHEw0q7fCk3zQhSkfBdslhG7KGeThhbyvHv-U3PVa8Z-Yq29vbbreSGVfofqvXIhS7UhunxV6bluOarjzJzHPE.png) 
        - Cipher Block Chaining
            1. Pad the message $M$ and split it into $m$ $n$-bit blocks, to match the alphabet of the block cipher used. $M_1 || M_2||...||M_m= M||\text{padding}$ 
            2. Generate a random, unpredictable $n-$bit initial vector $C_0$. 
            3. Starting with $C_0$, XOR the previous ciphertext block into the planitext block before applying the block cipher $$C_i = E_K(M_i \oplus C_{i-1})$$ 
            4. Output the $(M+1) \times n$-bit cipher text 
$$C = C_0||C_1||...||C_m$$
The extra n bits is $C_0$
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/nPgaUhQXxOnw025erm49H-7wjqtasvitqZCzhkJb1i9klOEQLDjLuhwumd8tu-_eUcLvF3voB9goDNPNLNQATrfKVKApi9_96WZ2ax2L0_N003SHzHRUbBiyCJ13D_YP.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/oyZVtREBH5xVAxu7piRxplWwTi0P-5wFlfBiIf3luJ_rwdaKxBVtczAtJ8RPGf3dJKyfq4-06ScDdm2ekfWRaB6nnwz8GbZd3ff72ZuJjq0lFtRmLltrf4SpHyw4Fka1.png) 
            - The input of the block cipher $E_K$ is now uniformly distributed 
            - How can we form more uniformly distributed bit-strings if we have one already?→XOR a bit string with a uniformly distributed bit-string, and the result is uniformly distributed. 
            - After how many repeated encryption operations (of the same message) would we expect a repeat in Cipher Block Chaining?→After $\sqrt{2^n} = 2^{\frac n 2}$ blocks have been encrypted with the same K - where n is the block size in bits. Due to the birthday paradox.
Remember, it's uniformly distributed.
            - How do you decrypt a cipher block chain?→$C_1$ is decrypted and XOR'd with C_0 to give $M_1$ - then $C_2$ is decrypted and XOR'd with C_1 to give $M_2$ and so on. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/hKdTgJlOSUDc9o9VFIqk_MrTK21fzPOpCzpr6Kr8H9lbIl5ZN7zgGektd-GvImBf6yoV6AgjeOETAxtBw-stPy1e_LV0RnPCVD2suHr2BSNj4HixLHZ-8PX_J4sYokVv.png)
            - What happens if you have a single bit wrong in you cipher-text in cipher block chains?→Only a single block, and a single bit in the next block will be effected:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FM3FdaJjRI_aHA2e11rLVE00w6Z9FiOHlZeeBSmfTQOJZz9LGqVj0HAt5L1sZBxVViJM0yCkp3w2xp_MtUYA6Ug1R0VmBX18LnibNQ5Thr-fq-9jCTTz9yCIXYzWHAZu.png)
If $C_1$ has a bit wrong, the whole of $M_1$ will be wrong, and only a single bit in $M_2$ will be wrong 
        - Cipher Feedback Mode
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/iXJhAojmwJyeEZwQ9hpDkqsdjIYzhbvpavtUcpl_dIfXDUzhdhDVq5P9C8-zXOUc98ZMwQL9zE5rF6lY4QcZXmOay79r7rFERhncjmmvV2_lbRiTxQZ5JyP7VrXE0hx9.png) 
What are the advantages of this cipher feedback mode over cipher block chaining? ↓ 
                1. The block-cipher step needed to derive $C_i$ can be performed before $M_i$ is known, so incoming plaintext bits can be encrypted and output immediately. Don't need to wait for another $n$-bit block to fill.  - **reduces latency.** 
                2. No padding of last block needed. The previous block will be the required length, and we just XOR with that.
        - Output Feedback Mode (Stream cipher)
            - Works thusly:
                1. Split the message into $m$ blocks - the last block can be shorter (no padding):$$M_1 || M_2 || ... || M_m = M$$
 
                2. Generate a unique $n$-bit initial vector $C_0$ 
                3. Start with $R_0 = C_0$, then iterate
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_6zQv7i_jgHQnkO-_Hg49j8gWKhkYhZ9wngodZyDo2DYpXkZ4P9Qncx5IQJkFG9X1x_LokuxEswUfjGU1UeCUGgUYkf9YvSoBrUs07PD34qVEomx2s2sIKDOdF1fcOpV.png)  ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/GQ-nOh61hOWo8Ma4Q2kBPTcRRFuXiYfmUoj9VTvPhooHb8OEz9xoA-hK5RuwfzyjuCtl1_yuQmW-HTzc6BeOlWuX6kk-euNIAgWB3P4aO4mCOfNiql6WZ-cTbTanNl_e.png) 
(Use only the leftmost bits needed for the last block)
                4. Output the ciphertext $C = C_0 || C_1 || ... ||C_m$ 
            - Replace the key before creating $2^{\frac n 2}$ blocks. 
            - Counter Mode (CTR)
                - This is a stream cipher **with a counter**. Count up the number of blocks encrypted, then include that in the item
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4tL6Go4J82IvWnRMOz2WJx5r-R2tV3NQQXmJqs-H_Lg892Hl19awU8KpPMaBnbxIo0-wHo6jAqoKC2nm4mmA-zSeD3qPbab9yLJHw-mHvre4b5lh6VyGTFsoqiQmrY8X.png).  
                - 
            - Advantages of output feedback mode
                - Allows fast random access
                - Both encryption and decryption can be parallelized
                - Low latency
                - No padding required
                - No risk of short cycles
            - Counter mode is generally preferred over CBC, CFB and OFB.
    - 
- Lecture 6
    - Security against chosen-ciphertext attacks
        - Allow the adversary to have access to a **decryption **oracle as well! We do not allow them to use the decryption oracle on the message sent to them. The can modify it by one bit and decrypt that though. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qLL24n8XOSwQvC2VOZUfIS1DSmqZbBo_XnqjZpMUTq3SoQ_67hGOKCXOKyA9-uueqP6kT6fIm8l5I3hkZR45e_uyjzfe4neUq-vC4lN5Ul0vCLlQf1QqlyjXoi0iAIa9.png) 
    - Malleability
        - What is a **malleable **encryption scheme?→If an adversary can modify the ciphertext and cause a predictable change to the message. 
If we can modify a ciphertext and flip a certain bit, we could flip control bits in encrypted messages.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/hFlvGAV5BL1giQEdPMT79CckpELS1yC7E1H4qg_z76dxqxg0nqmWs0J2R86McirqjohiXQfuAF77P6y33bWKqhKXRvMjK627VPmUQzju_jdc6SkLP_IbHmCYC_QBw5pw.png) 
        - Why would malleable encryption schemes not be chosen-ciphertext attack secure?→We're given a possible encrypted message $M_0$ - if our scheme is malleable, then we can flip a certain bit, decrypt that. Then do it again with a different bit, and see if only the expected parts have changed.
You can do this multiple times to make sure. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tPSXc2HDCuz-neVN3OQMbf5wu7RNGtpafilgAoc0WO2yy66a4rQhydSYiEfO2rfBsurJdoGap5cx1IOrv5TGNrfF8DeL6TwmoH3wleIVfBmCUEpsKIm979hhJlVQhf1B.png) 
    - Message authentication code (MAC)
        - **Key generation algorithm** - generates random bits
        - **Tag generation algorithm** - maps a key and a message to a tag $$T \leftarrow \text{Mac}_K (M)$$ 
        - The **verification algorithm** maps a key, a message and a tag to an output of valid or invalid (a single bit). $$b := \text{Vrfy}_K(T, M)$$
Tells us if the tag was generated by someone who knows the key. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/rih5CxW7QIt2MUg1p9gMiq0zhWcRSKDLBXwu9cgDPmOkYolEW6jR1qsHNeAymVcxblsgLw_trLHlV0WJ3S-YB6EkNmq-obex7vx695TQq1rmvKFLzSps7tjrBAbLazzo.png) 
    - MAC security definition: existential unforgeability
        - The adversary is given access to $\text{Mac}_K( \cdot)$ - (but not the key itself)
They can get a load of tags, when they query the oracle with a load of messages.
Then we test if the adversary can generate a correct message, tag pair. **The message can't be one of the messages used to query the oracle.**
        - A MAC is  __existentially unforgeable under an adaptive chosen-message attack __ if there's a negligible probability of their forged Mac code being correct. 
        - 
    - 
- 
- 
- 
- Lecture 9 - Secure Hash applications
    - Constructing meaningful collisions
        - Our function generates two random bit strings, but it tells us nothing about the contents of those strings - we use a text generator function e.g:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/j9Xey8LvXVcLYcTbPUj9AmndiYHLtBS17jzu2cr1EhKBe_eQlFcJfhMp5YLguTOvVSi4Wnn35QJroRJFSKpNC_71oQE43rsgMvT9M6cAB8lLw06wgw9S1byuESSX4f-s.png)
        - We apply the tortoise-hare algorithm to:
 ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qeVsIiXDWq_GH-fMI1-2T3oEq1eMehAccBugUHbc2L_Zo_q3H06V2KXzJHuJwjhULN0RS8OJIGbwvPvsjYo6jk0rhHjAc8bFJUT88ND_NeRYMqSB4AvXjAkSBRYOGOHX.png) 
    - Secure hash applications
    - Hash and MAC
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/SgHaBEItBfCxJr_wDuXSeHYyIdeSsN3icNq7jPsfFCvVzX-rF5EW0i4i01jhOpZ3S8kWF2_UdM7zeoQmSYEKdW1jvZJQQkfeNMgGbtrUH9ekfh3NhVk8_9uqH73rjhCC.png)→????? TODO 
    - Hash-based message authentication code
        - Can we not use hashes directly as a message authentication code.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2P1Y6DwOtB5cUHW73z7idl5UjlDjWn8IeeLPX3D3VrueFfMI4AkXGKtCLFlzIHTIhj08Lid_KUBLi8yiPlAG05uuDfrOpD_REW3lu73cF9mWVfrciHh0IIyo92I3mCiB.png)
If the hash function was a random oracle, this would be secure!
        - This is also considered secure with fixed-length m-bit messages or with sponge-function based hash algorithms such as SHA-3.
        - But you **cannot **use hash-based MACs with the Merkle-Damgard construction - why?→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6DWHv6BdNOuGqFdqFkt2UNIxaRoKx57_TW1ZiEBKTptH5bRdydH0UH4oksY69GQ3wqpk2JBb8m9F2p7kK7vDsudJE-IjJwCLAKmaPCanCYt6ZEYT9nmYdO7vSdHZZjUA.png) 
TODO TODO
    - HMAC 
        - Takes a key, XORs it with a value that is as long as the blcok size of the compression function. Then we call the compression function and pass in the first section. We continue with **another **padding of the KEY:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/b0YW4Kb9nl-usRwmdfganPO1r6u5XCMV34Jq9BhXCJtqRow1yClgAR5UsG3wsdaZq7lifDLfX3vr30P5DLcZPGaBP2oIKCebrMHSsjX4BRDtZUu9fFbLB6ZYQRI7brAC.png) 
    - Secure commitment
        - If we want credit for an idea, but think it's dangerous and don't want to share it. A secure commitment protocol will allow you proof of that.
        - You could write down a message M and publish $h(M)$ - this will work if the message is very long. The **risk **is that if the idea is small there is a high risk the adversary can invert the hash function. 
        - Solution
            - Pick a secret, 128 bit random number
            - Publish $h(N,M)$ (as well as $h$ and $|N|$) 
            - When the time comes, reveal $M$ and . 
        - Useful for online auctions, online games where several people move simultaneously.
    - Merkle tree
        - We want to make sure that our files cannot be modified without us noticing - we could get the hash value of our file every time we change it, but that would be very slow.
        - Instead we use a hierarchical hash function - this tree structure requires only logk recalculations of hash values along path from h(f) to root (not rereading every node):
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JAA7o6xaGKFCjBeH38vgZtHZcTsol_vkMTSKf01qWjGpqDj9QgZltHQn5qB3S1qqTomJTI24EpUNmny2s83wgBxuIVZqykZZdqG0xmsiRNf3gsivLPw2IfgtLYhCPU_9.png)
    - One-time passwords from a hash chain
        - If using untrusted hardware, and using it to login somewhere - one solution is to use a one-time password. We generate a chain of them so we can log in multiple times.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9v923_5ZOA1NUg69TRMls2dyQVuKfrNM1gt-clydUOTgWcx_h_zA0rkUwp7Idd8A243qMsabQLjOVWZSrBbovwJWo5l6IcksD4kdPdcWebt9rYiLqyYlVR_TQu6A-3Ar.png) 
    - Broadcast stream authentication
        - Alice wants to sent a long stream of **immediately verifiable **messages! It's too expensive to sign each message. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/IYyiiaX2hdqWXkW610cl15iHO6Czxey1kHI4AXXHiQTRGbFzMD1R13c8r37T-N3-4zqJdbrYdK1N5kOYJ9P5JbH5uNvF9Uu6sXhTkgHu0nG42ZT2yh_nHGo5My2JnQqX.png) 
The problem is... Alice needs to know M_n when she sends the very first message.
    - Times Efficient Stream Loss-tolerant Authentication (TESLA)
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FspnOLQ0QHYA7nnFmfF2Sp-IYT7p4vWIHXZiW1aOjmeKt87amtexq3FLNLzTXwk3qbbZ0i_Pd33Q4RWHDFn6WIKfvBjjJe39J1cbx_p6Hfy6ZxtV1MEH-6Dlfq4m3IOP.png)→TODO DIDNT UNDERSTAND THIS
    - Hash chain, block chains and time-stamping services
        - How to agree publicly on a series of message - use a **block-chain time stamping service.** Receives client trasactions $M_i$ and may order them by dependency, validates them and batches them into **blocks** (Including a hash of the previously published block).
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/h91HmLD10Fk3JXQMhD_OwXdN-xdRntFJ0a9VKpd-F1gqskYOu4V8aDa3LD-TAPVyu_Z2yCkt3G3G_qE1vL-Elo8BDJDvd5kliRIbG8SZzWrr8EUqOadh3Gl_6rkrH5ul.png) 
        - New blocks are broadcasted to and archived by clients - clients can:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/kNLhzR8dRt76BmEd_VCaz7_EczFXCa-brsrRLSm-0MR1nandMP2JHFujpEJE7yS1U4WcXyokwcLPKoUhUVQdWPRspSBJ8wkKA84Rtwqu4bCt_PWLzAmF1UtZzPEr3MkA.png)
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/snd_b3U5VKVLzvlpkG-rMRPws-hww-gwOzEVcDJh9oYSnRf7c6BD3x2CdOIpqZV4cEc1ugv1tzQseqmMmUxnykdzFUcZidAbLgAhnGyBbpLZzfVad8xc0I-h-3QzJXyL.png) 
    - Potting
        - Block access using RAM, when the device detects someone putting an oscilloscope in they just switch off and the keys are delted.
        - Tamper-sensing membrane, the entire circuit board is enveloped with polyeurethane arranged in a mesh - this mesh is consistently tested for conductivity etc. If tampering is detected the SRAM is zeroized.
        - 
    - 
    - 
    - 
    - 
    - 
    - 
    - 
    - 
