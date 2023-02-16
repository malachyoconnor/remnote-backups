- Lecture 1
    - Probability space:
        - Triple of Sample space, event space and probability measure:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/LaQIJwaVQWYuVddxrjcv1_Q5UEm8rbaoWmIm9DwvU5fY3Bc6ewSLNEXo0TI4EvmU0i03-I33mXu1GgVkXSLxOc97o6J2UkCFaSAk_iudIa58y3hX1xMQun9MhDKi5g6G.png)
    - Random variables:
        - Function that maps the sample space to the reals - mapping each sample outcome to a real number. 
    - Union Bound
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yFFCe2KFu3A8GQWWD4uYpmVa6Ga4Z1pwDZFJStps8EfUjbivGCPMFCw8hZN4bS1r3kC1K1zvZNrYrOnM-5nEpYEYUXnaQj9kT8gWhOlY1SmxQtuYzMZNRbQn3bWGtK9f.png) 
    - Max-Cut randomised algo
        - E(A,B): We wish to define a set of edges with one endpoint in A and one in B
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3xc_ui-c87Rv0q3KXaAUv76kpRfSqgCEG2J9lwEBMrwiA7-GUBkBOD6Atlxtmtq94myf92BKIEU2jogN-XEKUMuDP8zDWIXPuGtemyzEN7rPCgUDT6IqRUy4iI0r6vRc.png)
Split into two parts, where the edges between them is maximum. 
        - What is a 2-approximation algorithm?→An algorithm which returned cost is at most twice the optimal. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yqbJ-aXtDaOI4z5g_3bH25z2Nxk8b_UHFabYzuDoGlF1y4cuh_Vbvz3R0edELEapBu9SarsG1oSD-fKJepEFvXxEiniX2wJXS2SvPRAy3yEBUarub6_0YKF4CEmaJwDZ.png)
Note we're ranging over **all pairs **of nodes - so the probability of one or the other node being in a set is the same. 
    - Coupon collector
        - Suppose there are n coupons to collect - every morning you open a new box and get one coupon. What would the probability for getting all coupons be.
            - It takes $$n \sum_{k=1}^n 1/k = n \log n$$ 
            - Use union bound to prove the probability it takes more then nlogn + cn to collect all n coupons is e^-c. 
Remember $1 -x \le e^-x$ 
    - Concentration Inequalities
        - Concentration refers to the phenomena where random vars are very close to their means. Useful as it can indicate an almost deterministic behaviour
        - Chernoff Bounds
            - Chernoff bounds are strong bounds on the tail probabilities of sums of independent variables
            - Usually these bounds decrease **exponentially.** 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/l64Q0R053SZWf_RCVP8CWkY53HWF0OZC4_m_3UYYdJv4dJwcVX9Ri9hperH4Yh-psGPufSg15_FQAT_1FrHJOnSi1ygyQNFWsIWchJy9wlvpQI5AlBzGMo5ELlZouSvQ.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/0DUvQf7SqN9JfEFMxy3usuQ_WTODCT2EHjwsdRktELYtKdnH0AGktd4XootuvBx32I9VJBK2XWBiteM6ar--36DaDm8bCulcxA1XUGPSN6JgLUR-2wgO1Or-NYsnZ2qW.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qVbAf35sRv0CHXu4xQ1vORUyhxjRLZ4fhXcziiPqqypRjqmhQgd4AVQpUJKEyLtVGhKAOUyWS5sQl28BJvSNJPnpeP2T2X9SF6YihJiP51I9exQc7_fYJIo2U05bACeJ.png) 
            - These use the first and second moment of the random var - if we go highe rwe get Chernoff bounds
        - First Chernoff Bound
            - n independent bernoulli random vars with a parameter p_i. Let X be the sum of them and mu is the expectation of the sum. Then for any delta > 0 it holds that:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jmfsDmRVnT5_81xv3y2uk9Gor5dtbPy2547UZoR5M5zHFnoMeqpyGtYcjtAeKGj-uwprJk27ZIdvTKwogYdr4tbBf_fG6mv-zb87vCjqhWNPvTi3fUA2k0HoYDEaMMGJ.png)
        - 
- Lecture 2
    - Recipe for deriving Chernoff bounds for $X = X_1 + X_2 +...+X_m$ where n tends to infinity. 
        - We work with $e^{\lambda X}$ rather than X - then find the Expected value of e ^lambda x
        - Calculate an upper bound of this using independence
        - Then optimise the value of lambda to obtain the best tail bound.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9JqiHvboWaqNI1Ttnb4IjTqKHhJIB8qxgxVpgC9A_MeFinfmk0IpMNtY7YCI_ngdpIeE2clYp7Ttj-7TomRBL7_4jtiwf_QWPZWz-PU7723Gev-ByQU2_TsSbq5emgl7.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/0QR5eiYddBeabhUB6-llRn1WBDmcz5EYxP3Vq6dZ1MFal_uTqqugfZX6XLqdmFfLrNBnoP8P2gBjQNA8Bz4WUjYab0SmNAMSpfZ7utY2icmqzls_mtOGCsCyMEGjJeyD.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/joQJHE6FjwdgNQKZo3Txis-TJZ8I1yssWpytyevC2C9_RCx0I2b9bBlhz5VEJZm9ek6r3_51lRpcVWLtsxNm37_hwQmlFoJuhfBVPuAgs4RbkST2ifbcoZ0MgH2NxIdD.png) 
    - Balls into bins
        - m balls and n bins - each ball is put into a bin independently and uniformly at random. Can be used for bins as hash tables, bins are processors balls are jobs etc.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/OCLGaO2vhDulWOfl7S1NlT9-RuyIZNacpgh-w5Dw6lxuaGZpQG0HjFONMyT3zo_64OZq51IxehAgi3XFg-b4fXAqWjpLCBSFL3sRHF4AbdEkJ2lVmRE6_ZKSUz94wLxN.png)
        - **Question 1**: How large is the  __maximum load __  if $m=2n\log n$?  
            - Focus on bin i, load $X = \sum^m X_i$ - where each $X_i$ is a bernoulli (does it go in this bin or not!) - $\text{Ber}(\frac{1}{n})$. 
            - $\mu = E(X) = \sum E(X_i) = \frac{m}{n} = 2\log n$ 
            - Chernoff bound: $$P(x \ge t] \le e^{-\mu} \cdot (\frac{e \mu}{t}) ^t$$ 
            - He chose $t = 6 \log n$ - the probability that the load exceeds t is $\le n^{-2}$. 
            - HE SKIPPED OVER THINGS - WRITE UP
        - Question 2: **How large is the maximum load if m=n ** 
            - HE SKIIPED OVER THIS 2 WRITE UP
    - 
