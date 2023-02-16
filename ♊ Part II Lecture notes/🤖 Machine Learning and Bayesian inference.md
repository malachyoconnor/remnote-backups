- Lecture 1 
    - Notes on the handout
        - Random variables are given capital letters.
        - If we say $\Pr(X_1, X_2,...,X_n)$ what are we saying?→We are computing the probability of X1 AND X2 and ... and Xn. The comma's represent conjunction. 
        - What does $$\sum_{x_i \in X_i}(...x_i...)$$mean?→The sum over **all values **of a random variable. I.e. if X1 is binary then ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/aQ7qmORXlIqT0-bhjc4pwDqffpLpde0U-yUsFCqWGv82Kv_xn2ZCgSBvZ7aqdwU_XglVjnPH8PkDlpB0xHMLyHEKyokNXcAllwi_HlFthVkHTqqqwnmVyprRwmHR2AZZ.png) says the sum of all probabilities that x1 AND X2 are true. I.e. $\Pr(true, X_2) + \Pr(false. X_2)$ 
        - If $X'= \{ X_1', ..., X'_m\}$ how would we compute $$\sum_{x'\in X'}(...x_i',...,x_m'...)$$→We would have to sum over every item in the set - e.g:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mCcF_JhZ2eGWiu-Z48WiPqe96BhDHWtE6_g8ALLbiNvwxUP_enhRt9q7tyeY2zOiHYf8-tUMIg3brb7CQ0yfKeoukngtPIlOPE6mqMZQckqm9FpFPr8uyXoK2hyOzoqf.png)
        - What is the marginalising trick? ↓ 
            - If we have a set of random variables but we want to get rid of some - we sum over them.
            - E.g.: If we have a set Y = {X1, X2} and we only want X2 then we compute $$\Pr(Y \backslash X_1) = \Pr(X_2) = \sum_{x_1\in X_1}(\Pr(x_1, X_2))$$ - for booleans this would result in $= \Pr(true, X_2) + \Pr(false, X_2)$ 
            - In general $$\Pr(X \backslash X') = \sum_{x_i \in X'}\Pr(x_i, X)$$ 
            - For continuous RVs we can do the same:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gaYv6cxbK1AAZyY3vCgiXDWJoFsvP67V6FHR1B-a_DzW0woS202pLiiyleg3QuvR_7GsHz-7BjKb5JRwxbcl79fUfRcxa7WRchk-z7FRSLkRZ-nPw5jl4a4_4qV-a2z-.png)
        - When could treating a conjunction of RVs as an RV be useful and what does that mean ↓ 
            - If we have an RV representing a dice role and an RV representing a coin toss. Rolling 6 AND getting heads is an event with a probability in it's own right. 
            - We can then use these conjunction of RVs in formulae like Bayes theorem:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6oApQgq9_KzjQGCpW-FWBCa1UXA1OXmt_B_fEsjsqy8TXqKUxmrb_rE9UflWxnwjx2aJL0pU33gS5l90N1aNtH3Qp6g8q5yb1SQCOPWoI1A2aHHK_DO6Ua8MsY2u4O67.png)
        - Conditional probability distributions are still probability distributions! How could we reduce $\Pr(X_1, X_2 | X_3)$ to get rid of $X_2$?→We can use marginilising again **as long as we leave the conditioning RV **(behind the | ) **alone**. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/EhgdL9QxiTvr9Ad0YPBWYZCwkQt8_0qvabC1pmNmbdlMlyJPgb6f1pL7dm4PfkT3J1vV3dmGB98R3D7BVInqs3lbDxQPefGsZhqJSWiipbxjkfIFHVo8kkqIzKH2U3mT.png)
In general:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/1R4hgR0mWtD4G1HOVBQlQ43B7k-y0DXYi_7OCqdm5_doRNCrhwZGAtQmOeIu9G54TDVtyTZaG6ktzio0lsFz7AL5A8y3HE-murytu9kXFWqU7o3BRKyn1sN3T_XJHed_.png)  
        - For a set of RVs ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/D1gvGGar4rBZnJYXVKChpm9YEU2dbTJiAFKQXY1KZoudNSc76e4-qebH1LnPbNRJyn0a6BuOcTmymxm45nXRiWQKfLU0OTE09aURmaK0MEIEREBBY2DgonqdQFLdO4wI.png)
How would we derive this? (just the idea)―Start with 
Pr(X | Y, Z)  and Pr(Y | X, Z) - when we apply Bayes theorem both will have Pr(X,Y,Z). Cancel and rearrange and we will find the magic.
        - Are either or both of these true? $$\sum_{x\in X} \Pr(X|Y) = 1 \ \ \lor \ \ \sum_{y\in Y} \Pr(X|Y) = 1$$→Only the left is true. The probability of me getting heads given that I've rolled a 6 plus the probability of me getting tails given that I've rolled a 6 is one. 
HOWEVER, the probability of me getting heads given I've rolled a 1 + prob of me getting heads given I've rolled a 2 ... is still a half.  
        - How would we compute Pr(X|Z) if our agent is interested in the RVs {X,Y,Z}? ↓ 
            - $$\Pr(X|Z) = \frac{\sum_{y\in Y} \Pr(X,Y,Z)}{\Pr(Z)}$$ 
            - Furthermore, the Pr(Z) is just a normalizer made to ensure the overall value is 1. So:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jZpvQTITYfyzP1zAv35O2hdNwqVlhX739LgkOZCBMQM3Kqion0KX6ldmUbkw87xOIUbwORQ_k9i24gpupAa6vYl5iATKmj90SlHIJsvWTeLS3HnWyxfSemtl-Xpz-NFr.png)
            - This quantity Z is called a partition function and clearly:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6gow8K7oltZn7CzyXH6qm-30wuafZVHxJQJGIv9mQXFfz57-6nlW5tnV8VmpIQPsAdj_uW6RJpJSbkuMtjtunE9dY7APtKMPKiFTfgqUl5NT_hI7UoVNt8WrvCSeXng6.png)
        - What's going on here? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5pTYwhkA99uMZ4wdcg1A3bYfJhk6f6KAL10_yx7c7WStm7J-gfDUdLf9PNj09_vEQgPqPnPsPt-HY3JLSkvkpWJTgOrq62cZeOtZNqN8QCJir_hqsEjOcuYZuT5-vjZN.png)→Simply saying that x is sampling from some distribution P(X). Then we get the expected value of the RV X when f is applied. 
        - How would you calculate this? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/fhsG8sAiCIp8OrOrUfxM4AajFgirzmgZZFDVmwnKefjYrgmMTyR0eM6E77c9OLD_163YV23nSoPwAUnfb6gMCsf93Ii6LgYIfPKlhGFJ_-UkY8Ny_aSgVGGzTAP7asvR.png)→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/a5aHL1tqHLtzz__IG6zY2LDeoJ-GvSBlNKvMwSOLUqLg0v6LvSIXjsLoVeiRG_RGaqALgOBYu_AIjyVfn_eVa66MMqFyXTLtyF7_iOwJTGK5MwZahGsap7U1sCn1tbIA.png) 
        - What is the expected value of the expected value of X |Y? E.g.:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/OJzKcbfX7xR5_gnCKOnkOWNMLMAsEQAdpM9BWHkmBESE2E3hSW-rNP0qOdeU55hC1AnvzcV5QJWq4yaP-jj-148NrwyQrzpbTgYw6KeDHsA9XjiB2Cdtsp8ykKNLuaUZ.png)→The working:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/eD9IoyAV8ZKo67_BFh7ah9hC2l-h2uoEsikdCgL3nRaKUluKYh5eE0UGMxgd3lursA7kvhMlYW6tWVMoSuXDE4xwaYFhgCEPr-vuYKYoMg-o6SjM1lQG5cJgQ2YxSFKC.png)
I.e. it's the expected value of X.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KvCY5iM_879XNZhujUc-qtWHGyiximo3llsg2UouHr2lURFkrac13cd8JYizR-DANQ6OdsPQ3GyUXExyEoZV3010vv664JHdref6hD2LdedyLUBfjIIMOPZK00m7wZJS.png)
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/hFkJiZg_R_GGx6UbIB_6m4Kvqirxt5REttuRT_M9PRoYCdzOWRafXLLSX8PgVc0Lep9I242x_UVo1hnjudmXIQxAUgbigR7lM4CYrAPTJgdbYCuv_B2SFzch7xbS4zT-.png) 
        - What is the indicator function $\mathbb{I}$?→For true it returns 1 for false it returns 0. 
        - What would this give:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bpKIeUfmeN_e-ayIhNKg2-7i9_6SLp3W4cXhxk2swiuNoH-r0w2nUVUFTVO7qRy3fHMF3AeWB8eEffcDxn0fWEKaL9lGNf3UehmZ8TKfY0RBF6zD_T3QQ9CZBjH1ty2g.png)→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/xfNZd9fQmd-wgM-X3kxZ3ai4AecTB5LrAZKRp0t-iIUF0PNiT97qc4bgeeWPK0quGzDnPxEbOLp1JTqcndQFN2Q9JRwXAa-997LYKGGE1VhG4-xHMQsA6mnLGyKSzzGS.png)We're left to calculate the probability that f(x) is true because the sum of Pr(x) over x is just 1.
This tells us **the probability of an event is equal to the expected value of its indicator function!** 
        - 
    - Bayesian Inference - Moving from logic in classical AI, to knowledge representation by setting up probability distributions - inference is then the application of conditional probabilities. The payoff being the ability to quantify uncertainty.
    - What have we seen so far
        - Logic used - this has drawbacks
            - Laziness - it is not feasible to build an exhaustive set of laws, if we could then they would be impossible to use. (Humans aren't thinking through a billion laws when taking a step).
            - Theoretical ignorance: Insufficient knowlege **exists **to allow us to write all the rules. (When you start your car, do you know all the rules? Do you know where every atom of wiring is situated?)
            - Practical ignorance: Even if the rules have been obtained there may be insufficient information to apply those rules.
        - Instead of true or false - deal with degrees of belief using probability theory. Summarise the uncertainty due to laziness and ignorance.
        - We examined planning a sequence of actions to achieve a goal - however all these approaches suffer in the same way as inference. All benefit from considering uncertainty. 
            - Utility theory is used to assign preferences to different world states - then decision theory combines probability theory and utility theory.
            - A rational agent should act to maximise expected utility as time passes
        - We examined some ways of learning from examples - with no real mention of uncertainty. 
        - **We replace the knowledge base with a probability distribution that represents our ** _**beliefs**_ ** about the world.** 
        - **Logical inference is replaced with ** _**computing conditional probabilities!**_  
    - The big picture
        - The world is represented by N random variables.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/GcpozKtFNqIVp2yG7IK03bDdovWOvNBv_DGDXH1FEov00yiAHAy4xo7x1RekJUORGV4tlSvYzKO8xnOfqUDJxjmwPFFbQNvevQaOY-_CnlPi8TfgKrbuj0OavC_0kW_w.png) 
        - Say we have  __observed __ the values of a subset of m RVs, we know said values. Then if we are interested in some subset Q of  __query variables__ .
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/SnS7DP92iPpuLn9p9Sl4wCtYDUhB6-6xSNKGhF5FL5VwFI7TboFkDDThiNDo4KpmfIVcgMNTPcOTHgd4dRE4TLfpbumfpHetQPxfM0JIeqiz5MRDRjuUQt9kZm9Jj_sy.png) 
        - The latent variables are all the RVs  __not __ in the sets Q or O. 
        - Given our queries, our latent variables and our observed variables - how would we find Pr(Q | o1, o2, ..., om)? ↓ 
            - First we note that $\Pr(Q | o_1, o_2, ..., o_m) = \sum_{l \in L} \Pr(Q, L | o_1, o_2, ..., o_m)$ 
            - Then we note: $$\sum_{l \in L} \Pr(Q, L | o_1, o_2, ..., o_m) = \frac{1}{Z} \sum_{l \in L} \Pr(Q, L , o_1, o_2, ..., o_m)$$ 
            - So, $$\Pr(Q | o_1, o_2, ..., o_m) = 
 \frac{1}{Z} \sum_{l \in L} \Pr(Q, L , o_1, o_2, ..., o_m)$$
Note the right hand is our WHOLE knowledge base.  
        - Bayes Theorem:
$$\Pr(A|B) = \frac{\Pr(B|A)\Pr(A)}{\Pr(B)}$$
        - How does this formula give us a way of updating our knowledge? $$\Pr(A|B,C) = \frac{\Pr(B|A,C)\Pr(A|C)}{\Pr(B|C)}$$→If we know $\Pr(A|C)$ then this gives us a method of updating our probability given a new measurement $B$.
Note, this is **new **information, not the discovery of old information. You can't fill in the value of $o_x$ and count that. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/EYK2k6vI7ElaTVHWTltYkklusz0jhjJ-Jv6exkcjMbf3x5_1nKvfK5UN5L4qtqSX8ttHX7wh3zIRJ1TAsw2WaVzENdYFG0ZmDtXDsXXg6Z04y77JsDV3Djn4SFN7FFZa.png)
    - Problems
        - If done naively, if all our RVs are just Boolean storing the knowledge base Pr(V) means storing $2^n$ numbers. Why?→Because you would need to store every permutation of $\Pr(V, L | o_1 = \text{true}, o_2 = \text{false}, ... )$which comes out to $2^n$ 
        - The time complexity for the summations (over all latent variables) is also $O(2^n)$ and we would need to **get **$2^n$ values - all these problems get worse for non bools.
    - How do we get around these problems
        - You can be clever representing your knowledge base to avoid storing all these numbers.
        - You can take that a step further and exploit the structure of the knowledge base to get good time-complexity
        - You can do  __approximate inference__ . I.e. approximating integrals.
    - 
- Lecture 2 
    - Labelling based on two variables, e.g. kittens into cuteness & furriness:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zcYE74OrUwzDg-UDImLtH1f22huQpw04X20orc-MGKM0VlU5pMz7HJCS7uhMinTkUoCORm4f4-4VX53wny6uI9Qd-bHLdyA8Ngxf5lPgP41GGeHS99LhH0hLNQlg4Dlp.png)
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/1iavMLkz3Jqhmh2MkjbeN950_L75Pa7BuGrnfoTuXVrHLtUrZ5WIB5yZDjfoP8qoIPxW4vZPt60kKyvjbpjx4Ye_uOsrub-XLgkx7ZTlFxWM2ZF3EsTVmBpccqcA8jT4.png) 
        - Feature vectors $x_1, x_2...$ Will contain cuteness and furriness
        - Labels for kitten or not
        - A hypothesis that takes the cuteness and furriness to a label. $h : \R^n \rightarrow Y$ 
        - The hypothesis will be written $h_w(\bold{x})$ where w is the weights.
            - If $Y=\R$ then the result can be regarded as continous eaning we're doing a  __**regression**__  
            - If Y has a finite number K of categoies, $Y=\{c_1, c_2, ... c_n\}$ - then we're doing  __**classification**__  
            - If we're doing classification we might treat Y as a random variable, and find a hypothesis $h_w : \R^n \rightarrow [0, 1]$ of the form:
$$h_w(\bold{x}) = \Pr(Y=c_i|\bold{x})$$
I.e. The probability that some particular class is the value for Y. 
    - Supervised learning as Curve fitting
        - We have some hidden function that generates our data - and we want to find the correct function to model that data. You need to manage complexity:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/a2-VwkvIQfjR82QbuQlnSv7YMLcAYsT4ZfdkggYlq0PPMCsu4SxMCw89C1IWkuVtBW0sHU1ydL47J8JcKAKcOi_txc_1ZDmrWtOKqWcs5SZxWY2YjGKTe7zWZ5Pa_Sgd.png)
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/0-x_v5COy8PNRHaw6GMCAFGzPK0sLP0H-g5HzACCIBMmEC_KwPtYqSNlA981paR0jKZMSxc9cCFqO_kzqzm3ryiOHIBgDGleBTWnRGPSnrDLSOA5NSpH2OAMwlPjMcys.png) 
        - We **generalise **this idea of fitting a linear function by taking multiple inputs and building a  __perceptron__ . 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/LphJneHPANiigb4dds8bKiX13WrLWwK-uLJZh7oLwPmu0OcXJ0Xo0ZPdiAzL1dq-NQICup4bxI8qAG60mF9EaMVXknbUFBZAfKXoAENJOd7pblslfJSm1W11qXgyh4jk.png) 
        - Note: This model of neurons came from **spinal **neurons which are far simpler than neurons in the brain. 
        - We then differentiate the error function and use gradient descent:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zcaZURjjnjB84R5txZUKh8O8k4T52S1GkYcrmuzM_ARxfo07BEtuXtzrTKj8X3malEiMOObEiRKmm7khYRbYsBcVbTMUqZrBFh1vJr-fnQbw8DG66DEyiQmdvNAh4Ydh.png)
        - AI is not only just being used - in the 1990s multi-layer perceptrons were being used for trading dollars against yen. Additionally, 1980s 90 miles on the freeway via self-driving.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/rih8op9CFs6uyrk0mYtFRRm-AD3KqBR9ZoYHlgb4yHSSVzANZ7SsIDcZFMZLl19sqPED0WzpCDHBE_6CDkWlIQC4OFQS35_eQ9TGm-5DvWhwVUyAmgF_Zxm2-183pq-8.png) 
        - If you've got enough hidden layers - you can approximate anything to arbitrary precision.
        - We can then use backpropagation for computing the change in the error function with respect to the weights.
    - Unsupervised learning
        - What if we have  __no labels? __ Unsupervised learning we have m vectors in $\R^n$ and we want to find some **regularity:
**![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/y7kJHyWyTwja6kfsVjQjR2vvwSoLiktT5ihyDVS8zsfxkaGs0_U08V2yolOOnOE8uCq0IWlvAfe4qVnUJmP6Yp80tbwB3eRB476bFYVZ809FWVx98iR2Fh2h7_gyU8wr.png) 
        - What is Semi-supervised learning?→We have some labelled data, but mostly unlabelled. Its far cheaper to generate unlabelled than labelled. 
    - Reinforcement learning
        - What if we want to learn from  __rewards __ not labels. 
        - Describe reinforcement learning→We are in a state and can perform an action - when we perform an action we move to a new state and receive a reward (likely  __zero __ or  __negative).__  
We have no knowledge in advance of how actions affect the new state or the rewards!
We want to learn a policy to maximise our rewards.
    - Notation
        - $\R^{m\times n}$ is a matrix with $m$ rows and $n$ column 
        - Vectors are lower-case bold while matrices are in upper-case bold.
        - Vectors are assumed to be column vectors - transpose with upper case T
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/64BzNFBQKyrxajbIzsHZDLOjD5zvQZzgM2OVKjfqbTARpUsYPDNdtJOroxH25tN9p8ehkZZ0ZMTdh02uEX9EG9LsZ3mDI5pU3I-Cvh5ibvlkcSaIsW_6d7znyWEM0Cr_.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/UWvYR85nd4V465HPatVaWOififoIsofAX_m4I5CoFWMFg5gMDCot9M7aGlC4Q3HCHNUm6V0UZUpIhusBkiEkQ3bCGUVptsX9pEUqWEhBYt6MPzvrIJCTew9vH8eGwPCl.png) 
        - Random variables are uppercase and can take a set of values.![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YC3gcmopKUuP3h_Y9r1NQMV0A1P2nfvUea1MhFIcztcaTPx09bHKGjOCKgCjLQSp_nqR8sKKQrMLLTzC3wraBRouoXqw3Yz-OtXiEyHMybprrVoEBlgEKZ2tASW3Qr2P.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ulcBeOaH-W0eGBlpliex_U3s3wQe2hjh6BEmzIO2W0cD5qoQd4BGyMOccjBP3kbViub0PQbZfxOU7lndvdgRWl_hOiF43iusxdR2cJhqrRyWFsg8JkLbsRSe9fp3dy2F.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Q06C8MWm4iurN2zTwgUchEyqEsHIn0NRgj1ZnqPStBands9rM3NfgAGOoOdaOosATo3u6lVo6287Zr8pkoBTtjen_RZYwGqc1YQt2uziHRLJeZLj0Y1u1Rp1zdl2E-Gu.png)
Why?→Because its a continuous function, the probability for any one value will be zero. 
- Lecture 3
    - Optimal Classificatioon
        - In order to talk about optimal methods, we need to put it into a probabilistic context - this will lead to a better understanding of choosing weights to minimise an error function.
    - Probabilistic models for generating data
        - Assume data is generated by some unknown distribution $p (\bold{X}, Y)$ (X's given labels Y) 
        - We form a independent identically distributed training set:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/W_6r5RaCHI0xCPkfEUUlZp_cCv68i66OVGP77uMwmQRliTT2e_5Mksd7Eb0hLKmCaamZvDP1uvrJKOG0h8adSgoj3pZtpKDzY5s5qRl91a6ujbV9XuUnUeh0dEXLMEww.png)
        - We can then write $$p(\bold{s}) = \prod_{i=1}^{m} p(x_i, y_i)$$ 
        - For example, if we want to guess a polynomial given points - we have a function $h_w(x)$ where $w$ is the parameters we want to guess. We need to identify w by analysing s. 
        - You might then add some normal distribution noise:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/U0WrfeCrk8O1YtO9-ij1A09xZxiqqNYOkf9YZZq69RDJ5FnSL3-7OFpc1-W2MVusZ2zXfaBwX9MGDFGtUIKKx5sUvoQ9XWFF1S86MLUiJlOkEIgojtX7-36xPy_iXMAT.png)
        - When we add noise to our function $h_w(x_i)$ (x is uniformly sampled) we get:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/lDtMN7S9ELAjbqUPekE-uoX25PKmVrF_d6UcJMBYmYZ9FobwIn7gFWWQDXC68P2Wz_STgStVeVMd8kTM5geceueCXcY3Nn18-BDechOxirMxQcJny4_DnzeFhbQ7Ef0a.png) 
        - What distribution does computing $h_w(x) + \epsilon$ give you? (here $\epsilon \sim N(0, \sigma^2)$  )→Gives go $$N(h_w(x), \sigma^2)$$ 
    - The likelihood function
        - The quantity $p(y_i | x_i, w)$ is the likelihood.  
        - Can be written as $L(w|x_i, y_i) = p(y_i|x_i, w)$ - the likelihood function. 
        - Here we have the assumption that w is **fixed **but hidden. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/u374hDp5WPdmoSZTCVgmcOra23HvfcyN-_u24_tRP9QK27rDaLSpj08n79oPmrUaFaczfc3B-3hqNJKpFQgmjz--dlyVAYqzEMpgWSKgVtd5B61Fe0PNH-U4eEaGW8X5.png) 
We know that $x_i$ does **not **depend on the value of w. 
    - Maximising likelihood
        - This tells us how **probable **the data s would be, **if a particular vector w had been used to generate it.** This suggests that we could simply choose  w that is **most likely **to have generated it. $$w_{opt} = \text{argmax}_w p(\bold{s}|w)$$ 
        - Get some data, and propose a good method for generating it, then choose the most likely parameters for generating it. **Maximum likelihood algorithm.** 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZRAuHSc1MF9FpbGR2Yccm8rB9e-63rXdrM2rBCDQ1yJ7Dp-z2_Qz7VUnTs1swwY6kiQAqvEewx8ODcvpd1XBljaFWesFrRAiOa0qzRvm-RS4AuX_Eg7VWMoiojGlP6Lx.png) 
        - If you're trying to maximise something, what function can you apply to help you?→Maximise over the functions log, gives the same.  
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5tNqareHiIN_yA3-tbx69u4KcQD9BgSFUXbYN2h1bYtrthuA8LQ1kH5-xy9xuE0vLyxbjdYsbs9K65CMosQ-mlw5kjoTm6JaHh9BA1hHbb0BWmoxvkvioP5l0Ya82U3E.png) 
        - So this tells us, to maximise a normal distribution - we find the minimum of the sum of the squared error. 
We go from max to min bu noting that the sum we care about is negative, and to maximise a negative is when it's closest to zero. We take away the negative, and not that to get a value as close as possible to zero we minimise it.
        - We've assumed the noise is **Gaussian **and that maximising the likelihood **is the right thing to do.** 
    - Maximising the posterior
        - What if we don't regard w as being fixed in advance, but make it an RV as well. Meaning we need a distribution $p(w)$ - known as a **prior on w.**
We use a higher dimensional normal distribution:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/etYmOQELz3xs6__7na9s5jFrxfMZxE8pnA_XqxbhXaaJde8ycw_qOWzz0mvi2XKIsnksmT9nIpJ1G2oscpbUquCQKLabOxyl6uQXDzmgw9nPSvlOOqUk1pvRugozDcBa.png) 
        - We choose $w \sim N(0, \lambda ^{-1} I)$ then we get:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/n0BNQHjW2G5QAiSARzijVa44yU9SThpz_B2lKE2Kh9V7N1iL9kUnrwS32aCWv34QjS9uvsI_AoYftp6WBfLu0nIG0CSyDz9mhazlw95FoFC-sA1ifktOCGlfGNBBFof_.png) 
        - Instead of figuring out the probability of the set given w, we flip that around and decide on the weights given w:
 ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YWBMoJ7rC9IZrdLcLrZTbVyYznsXGKFgjolaKrc0IAjZ9W6Y5j9yXIvE-yA8W2_A0PwVMtrPdtV2XQRwVQ2ZM8ToDVvLYv2fh1BX2UjHjDCfrXq_jwH2zxE7ORv3uOWq.png)
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/S3MXbIUksm3CHLfp--B-4RMlBXadph-Scvd6Kn5Is6OT7M6BnGStNaeCP2biW-E1fearICaNZOy3Y4Z7rNCZcVMwi9C5TeV8fzVkZu1T8Vvo06Xda4SGvjptAcYni_HQ.png)
This is called weight decay - usually used for regularisation to stop fitting the noise, this term keeps the weights small to help that. 
        - Note: This assumes the choice of w, is made **according to a Gaussian**.
We are also assuming some kinds of w are more likely than others.
    - The likelihood for classification problems
        - The likelihood $p(y|x,w)$ is a density, and can take any value in $\R$ as long as the density is non-negative and integrates to 1.  
        - What about this for **classification problems?** 
        - For a binary classification we have:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ur6G8UR-UXfxvIXGH6XGrkJZnxBgE8YMuYCPan6Qfi-JRIkPJm7ZQohF5bfRzsU9Pl6rXVEGEWPNrlcFGWp3VSEk_SDdpBE7eP0TR98smorchV9ZuWLNq6vpaUhsvhxs.png) 
We **can't just add real values noise to Y, **it's discrete and is either 0 or 1.
        - We can do that with: $$\Pr (Y=1|x,w) = \sigma_\theta (h_w(x))$$
We squash the real values into between 0 and 1. So we can get the property that the two probabilities sum to 1.
$$\sigma_\theta = \frac 1 {1 + \exp(-z\theta)}$$ 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/P8EGlAoOUz3KI8z1_XiuwBOeEbOOBvoSkPUIjT_8CJXoW4ySKdeKBp1WSGyrS-vWLESMmI6hq_dbcw9N5-cGZZ1oyfg4crjcU0oI2jRQSPz9D8_JMBfEcq6qgH8XskAX.png) 
    - 
    - 
    - 
- Lecture 4
    - Likelihood for classification problems
        - What is the probability a sequence was generated with some w?
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/b7ZsRNDnxs26w3-z_CskEt_xphHJTobeZjduSgS2QpiNTITeMx3Xcgh66X_4IvZDOGD9nEZvUOzcFk2HsysWfFEFeV1RHdvaAgLnvjH69CAVhlcnWK7pJENTKWSIxO3n.png)
We find the probability of choose some class Y=1, then the probability of choosing the class Y=0 is just one minus that probability. 
        - So when Y is a known value we can write:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/m7OvzhbykZiQurXY8neUXmZ39F1-EI4RrK49BI7E62l6tsalD3d44I_CFqiN5FWQHyZdOk-1aaI0-eegwHXrV5t0rv6En8HquAVYGibY9xripSk9LIKMyM0scuafXPeF.png) 
        - We can write down the complete likelihood via:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/LwZC8OOuVQkBOW2MtCvbUz2RLofTrRLs3a_SpuInO4E1w7CI1kIdpxIbZ6XZ-ensx3BlxyM_RFCjOl6Vrm3USEG3EN4JGvgFXRK-AcJX_cLWaygL8hvnKIh1K27RKZBw.png)
        - Note that both $\theta$ and the previous $\sigma ^2$ both have similar purposes. Modelling noise in some way. 
    - The next step
        - This has all involved choosing a **single hypothesis - **but we'd like to be able to generalise. We want to find a hypothesis that works well for  __previously unseen examples__ . We have to define what good generalization is and ask what model might do it best. 
    - Bayesian decision theory
        - Take a set of K classes and a set of L actions - one action might be to say we **wont classify x. **Another might be that we classify $x$ as part of $c_1$ 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sWh4aDAUSZix8jC1TrqOJCoGGkl2cVVRYmrMqGt0ltodAghE_qyd-p8J5WpaydAsup_yOaTpUo3pWLCa7iSmVoaF2X82if_SEFxG93wJf5_N9D4WlOo1i24Ksaa-1SrJ.png) 
        - We also have a **loss **$\lambda_{ij}$ - this is associated with taking action $a_i$ when the class is really $c_j$. Also written $\lambda (a_i, c_j)$ 
    - Bayesian decision theory
        - In learning to diagnose cancer, loss of 0 if we take the action is "say the patient has cancer".
Similarly, if the patient is healthy and we take the action "say the patient is healthy"
        - The loss would be **higher **if we assign a patient with cancer as healthy, than assigning a healthy patient cancer.
        - The extra action could be to **defer to a human.** 
        - Classes have probabilities of occurring, and there are probability densities for seeing X when the class is C $p(X|C)$. 
        - We model this in a **slightly different, but equivalent way** now we say - Nature generates a class, which gives rise to a feature vector. Before we said the opposite:
 ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/rcXQ9kvM7FrM8MploRwsNTF1O2bpXcEWJJSnAW4aGRTPeqS5VkljJGvwe43UsMBIcccdOSwCrHarqFqipwSfGnFtqtgi2zRb-cHsQ9OH_aTF39T5bvXBl0CpLARpCVss.png) 
        - Say, nature shows us x and we take action $a_i$. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/DSOtrO8UWaN-gHI9RZYyEW8yL4EGmtZkcN_ksyM-uoLVtZPSG-eDExBxTTHgJ7aMGnwVanopfp_FdtBWAjaUtdDa6eVjn5w_BE7Y04S19WjB7Vv_yvE3jrWu7u5BqopM.png)
        - What is the conditional risk $R(a_i, \bold{x})$?→This just gives you the expected value of the loss if we **always **take action $a_i$. Just the loss for a pairing, times the probability of that pairing.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ujQ7c5XDoZ9jquTtfcphMEJ6oP-imMqgti8xXAmFYj_bKyOISbWwzwJFnxvHjmNysf3yrVogUnxhHFZMW14iGtCOOrAhc1t0AyoAuGXOCU6L80cH-QGSHfocueiEX85t.png)
        - Say we have a decision rule, telling us what action to take on seeing a feature vector. The average loss or risk is:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CjepCbvDiiG1adGmmI22__M-BEZm9AJpKQVo_8F4cyj_hfVj6JoVsY-bFjchifqLIb2jd8lNSrWbKoAmmfRXpXnb5JYkJ5eQ5vkEz2GLSfwXQENidEJuHMqhP68thEEw.png)
        - What is the simplification of $\mathbb{E}[\mathbb{E}[X|Y]]$?→$\mathbb{E}[X]$ 
Remember: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gCgS8-5DG6LmV8h5ZcV-LE6QdUP3KwEUV9RkiIMXPaIz8i17z5JTJ85_e-RP5G9jTztRMw-postof3wJifuvImdgvHJPF4DBq0hGL5shDAtLs7yWoUfwDF2r2ISW_WEs.png)
        - We want to **minimise our expected loss. **We can minimise the integral: $$\int R(D(x)|x) p(x) \ dx$$
By minimising the value of $R(D(x)|x)$ for every x. You choose $D$ to minimise this value for every x. 
        - This is the **Bayes optimum decision rule, **minimising the conditional risk. 
    - Minimum error rate classification
        - Minimise the probability of making an error when predicting the label for a previously unseen example.
        - We know $$\Pr(E) = \mathbb{E}[\mathbb{I}(E)]$$ 
So to minimise the error, we can minimise the indicator value for the event.
        - So if we have K classes, and the same number of actions - action $a_i$ means put the input in $c_i$. 
        - We then set the loss as:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5ynaHviz4ol_GKW5VxsInis0vQrryYiBcTeoN3fiVxtdqS1VmhWJg0xewHzB9YqA9dpyFzMaCj-EkQIUZu56kAeATL1hsqD0TOmm96BwPQ9MymZrSd6c5vGMjKao0af7.png)
        - The risk is then:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/IXiJhl3acOHoFV7qVWcbMEp1f1GS916CYdIO-S6vHJmeOQ3upOrEJEJqKkYsxcR9pd4mrILak-_99BcqAPBCMxrT6ootTh7b-YtglGYKVDVBlOoJWCmGVz7zt4BpxksT.png)
        - If we choose the same action i repeatedly:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mzd5R7AabWY8U8XbWmIFs9nlE_KDvGFN648lnKojnzJIN2JnqJ8Xj6KFCSf-kQKZN0EUf2m2s3P3WezLQhYVyn4ttl95xLAW3zHXHWsiHKKgm7MPGAFBtnngA06kWguN.png)
        - **So, **to minimise the risk we should **maximise **$\Pr (c_i |x)$ - i.e. choose the class $i$ that is most likely to be correct given $x$. 
This minimises the probability of error.
        - Shouldn't we use the training sequence
            - Shouldn't this depend on the training sequence $s$? 
            - It should **if there is uncertainty about the mechanism used to generate the data.** 
            - The above assumed the mechanism being **fixed ** 
            - If we let the conditional risk be condition on $x$ **and **$s$ - we get that **you should maximise **$$\Pr(c_i | x, s)$$ 
    - Bayesian supervised learning
        - The uncertain underlying hypothesis $h$ doesn't appear yet! 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/OJnsgF-hRdHt4ClA4rr8wVRsvYJfpM0Hk49l_C_RDDdxol0KxtCMXmuvvOecZnQwWTJGfw8CE37-j0-6zPo2YXxmBz2ctzd5zN3HVjuQ-1S0mC2WQ7wBGhwhLmnpusPz.png)From step 2-3, we say that the probability of the hypothesis is dependent on the training data, not on this new thing we haven't seen before.
Similarly, the probability of the class depends on the hypothesis and the new data - **not on the training set.** 
        - We sum **over all possible h's, **but **weight them ** __depending on how probable they are!__  Not just using one fixed $h$. 
        - So our classification should be:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/F1o68wIovk3KKNa4UqKO-ahodQvUndd9t08Ukw9nXFlu8G6PrRTC-d1DPSlRlgfvv_3VSNyv1xTleydvS7dp1nVRvbsX01rKzsY10eV5FHgKZWGCFaKyMLKMtf4ZNtUm.png)
        - When dealing with hypotheses defined by weights, the sum is an integral:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/pcjbLZbzNHg4uZSGmzJDtaQuvkkbs7bXaxxVe1M4MxHP0MlgfdlEy4pJKME2cYUcVlqmPGhCKJDdOP4pDSa0L8RvQn7Cfoqt19ndB2DCauwYZHZI6mIqFNSZaCNl4Xjd.png)
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/M32O6RMxpYm4xV7-AyZ1rLq1yV6IN5OXRN8GvVAO7wqEIYlRqvdwi-0OiwqvEgTgzPOkKGZzSS9SGsdMvLhDj53ZyJEqAwM-t4OoYyV132J74G55RmfmoQNgC-c5lPnu.png) 
    - Word of caution
        - We know the optimal classifier - this **doesn't solve supervised learning.**  
        - This is **usually ****intractable!**
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/0XZMyHwof7bldQbAngeCaI8k67_FScVGAIQ_lVUJC528UgQHT603u47TglwtFhw51pHOQX2QrEbpbW8X_GKMxtYCd0FLmESYTwXoE01Z4zwtqDQpkdQFauuqEJ3OjX-i.png) 
- Lecture 5
    - The road to Support Vector Machines
        - Not all machine learning is inherently probabilistic, because those things are **hard to compute.** 
        - We will use only **linear **methods - this is a good idea, because linear methods are  __easy.__  
    - The problem with linear classifiers
        - Good for some problems, but awful for others
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/C2cDWcYJiVNU8NkTHHgutzZUeAOCfZIPMV09daBhQY48SMv3SW9K6qGdRjZ9WdocfB0CRtlDjaNerlxUvmC3z85_pndLMZkFuFP7VRp6HroCCZlkRgA-1aNM0JxxiZ4F.png)
        - Perceptron
            - $$h_w(x) = \sum w_i x_i + w_0$$ 
            - In two dimension, the solution that makes this equal to zero is a straight line in the plane: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3E-7iNIK7sb7UppWPJbkbPAQ6s1ith5MTabAgjkZTDSGs07fas9XJw9V9WovakqDrdEb5U9myGIOw7of1tVrLKfLy4PO4ZG5CT47l5GYN5eKiF3VK4cV-Q5_ejPt54eE.png)
This is where $h_w(\bold x) = 0$ 
            - We're saying $$w_1 x_1 = -w_2x_2 \implies x_2 = - \frac {w_1} {w_2} x_1$$
This defines a line on the plane. 
            - The weights can give you the **direction of the line **and how far away **from the origin **it is. $||w||$. 
            - On one side of the dividing line, $h_w(x)$ is greater than 0 and on the other it's less than 0. 
The activation function then outputs class 1 on one side of the dividing line, and class 2 on the other.
        - The kernel trick
            - What is the kernel trick? 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZMlvXg9uP8Ol5DKEPClWSJkwGd5CVW_RoTEjdqo_KrX9K2_0KYe_l5G0d-N8qiiWF2nB95j0Wg3pSfnpWFVZGfFHny3avYS6-_LSzAir19XDGXmLgY-wMFNeQXka44r_.png)→We add a third dimension to the data, equal to the product of the other two dimensions. This maps it to a bigger space, and we hope it's more separable here:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Clu5YI8B4A5nr3xjJD80iUB-hjq-BHV50a4NTkptvKqhYcQ7QhN5cWK4HGjEHAgaqj_8KfBDssNWl1rhzUf_xUMyfNZ2baof1YZrj3mUpxIhBA6xnf_OiIW-X4V7y2Sl.png) 
So now a **3-dimension classifier can split these classes:
**![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/aZNRz6tNwrHZ8UCsFZQtEXaS-y79x-l1S8C8QKTYMp7QOcPixyaB3YF1dMXDyXBIqpRVaXVSw7EHX-F3660o8vHqOILB9tvB_nh2fiorM0UNJVkj7U9rbr9eCeCRuW1U.png)
    - Linear classifiers
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/PuDdQGCH03hqQGcLoa66WuO7nRHnRSBnNUCO09RGno1uR_nsqP_2zPeLsVK6urRs_hbXM_pI2uZrpF6xWomcOWeQiqcYeDyIhHb3hJwJQPb-pbBT3ogVT-d_nqLrhIL3.png) 
        - Or $h_w(\bold x ) = \sigma(w^T\bold x)$ **if we introduce an extra element having constant value 1 to x**. 
I.e. add a bias. 
        - We make it nonlinear by introducing **basis functions **$\phi_i$. There are many different basis functions:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/HqCFoJbCrQSq26rjLh3G-SRqAyabRejvDBJtaO1BH_HEQ44V-V11xYS6DeKcuN5XtZIlLNfpI5FchJY_VUhuCtwJwluQAWZJElnNss3sohO3-UGpohsMrWnb4mmoRhmU.png) 
        - We first map x to a higher dimensional space.
    - Linear regression
        - We've already seen linear regression - we use $\sigma(x) = x$ and we have training data s.
We want to minimise the sum of the squared errors 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/A7ckTITn9OZKEcVsP7ZwmM9O_fc4XTgbMVp7AOSTgoLeH2AXkEZh-JfB84xatqmYZKn5ekB9Xl3j9WZBvoCV-GQf7qsC9NdxQhbcvFkUVNPNgxFgOjy0q7wepgS2wjSl.png)
        - Previously we would have done:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Puo5Wgx389gZ1hL1HeQld-lYRHK_zl3Fzdh1hvPLxKriJW78mHQAK8ChWydIxuNpmIJDm-4BCyTD7UqwUFHpfY8I1CZuMxF6i97zZVk6Ziw1vAwN65LoCJs_RrbQQcPL.png)
        - But for linear regression there's an easier way with the basis functions - we can **directly solve **$$\frac {\partial E(w)} {\partial w} = 0$$ 
        - Calculus with matrices
            - It is easier to handle this calculation in matrix/vector format rather than writing it in full.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Hzbn8VS5iBKE8Nw23oGCLOEv2OflB-o4QHZswv_Fbd0AyV3RpEbWyLDKkpvKZO7a4RqU7da3mN9kCAYpQlAsrU1SyLwEZEBvo5i5vPv2l6zVuDwwfW5Hlq64Im7leKcj.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3jMRGUuNQiIK77oxPctASroTxlLhA7Dv0r-msMR1nEIoqFcIAW9wxQ_lSECPXduDOH8RkSq6ZFdkpjx1-fn5GDlbmu8CEQQ42KNovJBO7stpMjiq56tbuqyhtS4vnb-S.png) 
        - Write: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qWjm1gFRYuSGrFPjkXOH6eTAoXFlDz79pi0Q3UCQupKFAyT71wJ92IpRSe-YB3eLDtzUJWi8JcQYPkJOjyw5HX6xE2CgmoFPIFdPULPEJNBFXswN-bEOgx1PpIbNy1sJ.png) 
        - Then the error function is:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/z7E-ou_O3D2iyJrislhNofO9VLHDUYCHWBjnwfQ8hG9iHa45LA7c7DfaVma3c9FZTgFoLBXFt5h-8uwqGJkzzidb5FJRFCwhmdEZLpMvis7zwbkmUOAIP3NkuDNGivbm.png)
This just gives the sum of squared differences as normal. 
Apply the transposes then multiply out (This works as these are just vectors I think...)
Then we differentiate with respect to w (notice the half! Also w^2 in there)  
        - Remember $\Phi w$ =  ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JLSWESy206nr9TG_TW04EW7JgYd83vrwjSyrPEQuIRGfaeAUHf7pH7tYXp1pRIUSVNYhPgAg78ojvYhjSYfCqzearATxeo4ljT2ZsDtFnl5cMe3LzPItQUXv_0KzeM8E.png) 
        - So the optimum solution is obtained by solving:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/kRybLxLUekXaewT-td5sUSEho9Xr0FIpxhbj3otXXS8SsivVBIjXJpoygG0tf2Z33GeL98Tx4Sha3jienRrQJKkT8U6MHLt6XGPX768D5e6XUTmY-hsBRW79R3OwTB8Q.png)
        - This is the maximum likelihood, assuming noise is **Gaussian**.  
    - Linear regression, the MAP solution
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Who4lQUGuy6hXUq_FrR28QbI39773SuWj2-_jXdu5heyuQyXmZ-9I2uvW3M86qs1Q0oBZdU3Xd0QuKMp-JZtpBsh3QWKuXBCobMBqPlTZwH_al75E117JyUz4AbdJmVa.png) 
        - Remember the hyper parameter is preferring w to be **small **- so we don't fit to the noise! Large values of $\lambda$ mean the weights have to be tiny 
    - Iterative re-weighted least square
        - What about if we're **classifying **rather than doing regression 
        - We now need to use a non-linear $\sigma$,  typically the sigmoid function- so:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gaTSFu82-uCqFhhTrhjxEDM2yr6OHTckv4DYyhsG8R6LBn42FFKnYYZucBBlMlnUaFrpf0kVBMOaDpiWGOxOn4UQvHcKJ-6OyNwEIpnp4fWs7nuwdDbqxoTJ5xYjkvgV.png) 
        - We can't do this analytically, but we can solve faster than gradient descent. We need a different iteratvie solution, using **Newton-raphson.** 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZzSroNo2zxWO7W0jpojrp_31ZVreFybF8XW-7ERBpC4wWYu5Hjx5IdoLbc_DT8xdk4juZq7Ah9uODtxmOCBigvz1Gs_VcnZJ-s-FrRJ_riLDMDfHE0rnMxVmnOggqrEi.png) 
        - Generalising Newton-Raphson
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/L3k__MAFA81ok5ZCeZj3KDqgWvp_aNOllQlWDtWRm5QRMYMfUooUoLWX3ddv_osObT_OpJz_d8sngIrJjbQ4_ymHnqL3XVI-eWp6Kd7_y2deJvvF9TKRHE89iFvW8LOo.png) 
            - What is the Hessian matrix?→It's the matrix containing all combinations of second partial derivatives $$H_{ij} (x) = \frac {\partial^2 f(x)}{ \partial w_i 
 \partial w_j}$$ 
            - First we take the first derivative for use in Newton-Raphson. Note the use of the chain rule.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5GYMc-3VuUd7j3GJz9EPxvRaGtGXWaG4-1GNPKZ3druZnOmmdR5-IwgkifXGpH4QI8KJHbaakAaAWMXbpyGfZ-Odaj0lGh0H_bkrNWhJmJRx41qx4PLMs2mv7tPul0pE.png) 
            - Then we figure out the differential of $z_i$
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/xMM-tNXKaKIWTzJnhTLlticzjyqsZGCSBbLVsMfFQwXNQzAphJbrD2-TzIO5MAHazfG4qpcopCwmjn7Qp0xoP71ngzX0Hs3yZvx5wOE7coM9xW6ajQr-av13HA1nP9Lu.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2JJDIY7pKQ3fCzDBVcUQCMZFvhU9ZjtSS1YNRNeyit_mu4NpzT4a0rIrHkVr-6FVLqyj27-YMc4nvXpoRMUXiznSS0MqRQSq-TRmmkSR2NeD1yQFEuXsBFnS_wo-MFmv.png) 
