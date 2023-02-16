- **Lecture 1 **(Lower bound on sorting)
    - Algorithms and Problems 
        - What does it mean to say Insertion sort runs in time $O(n^2)$?―It means that if we run insertion sort on an input list of size n and count the number of discrete steps taken. The largest possible number of steps on that same input size will eventually be bounded by a constant multiple of $n^2$. 
This is because $O$ is worst case.
        - What does it mean to ask, what is the complexity of the **sorting problem?**―It means the lower bound on the number of steps taken. What is the best possible time complexity?
    - Asymptotic complexity review 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Szdo2lS8WmKQvH8jFN5OcSz90VZKYqSEm9710ZxBk8YFZTgwCxNlvEErkyJg4ggMzXyva26ctY0e4UToGnj2pmydPeWv-t5ciDT173XwRTReXMFi2lc-Fe3aye2_a7mC.png) 
        - Explain the difference between $f = O(g), f = \Omega(g), f = \theta(g)$  ↓ 
            - $f= O(g)$ is saying, f is no worse than g by some constant factor. So O is an upper bound.
            - $f= \Omega(g)$ is saying f  is as least as bad as g. So omega is a lower bound. 
            - $f= \theta(g)$ if $f=O(g) \ \land \ f=\Omega(g)$ . I.e. f is exactly the complexity of g.
        - If we can find the lower and upper bound, we've found the exact complexity of the algorithm.
    - Lower bound on sorting 
        - Describe the argument for forming a lower bound on sorting―Consider a binary tree containing all the decision points for an algorithm.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gIqeI92NlQcsGyPy4Pg1r-Pck7gfDY2T-GB3R33f8HmoMSZSPsyl8QGFZcznE4BQEX6AGBcSjPDuhnvDTxalGuj47fKZEvLfPc1eNE1OYZubkdE8m4hY2-WaE6qBhb3n.png) 
The algorithm must have these decision points, as otherwise it would behave the same on multiple inputs and we could craft an input that would defeat it.
To work for every permutation of an input list $a_1,...,a_n$ it **needs to have **$n!$ **leaves. **Therefore the height must be at least $$h \le \log_2(n!) \le (n\log n )$$
So the height is at least $n\log n$, giving us a lower bound. We know the upper bound is $n \log n$ from merge sort.$$\therefore \theta (n \log n)$$
Or you could do this to get a lower bound:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/OqoZ_xD-eTLtoIutr9JSneuil2kjIQbm1VVSMVck2n4Z1k7ZfAlLTB1L1vt_Hqx1HXUQ9Ydzv2kFS9ijBgQ5BLmHkBIiTbFzvanJwUTqG5pKynGTvbWkWyCONMGodDZA.png)
 
        - How can sorting be nlogn when radix and bucket sort are linear?―Because those algorithms cannot sort an arbitrary list of numbers. **If you don't limit the radix, iterating through the **$\log n$** digits n times is just nlogn.** 
    - Travelling Salesman 
        - Given a set of nodes and a cost matrix of travelling from one node to another. 
Find an ordering of the nodes, such that the total cost of going from one to the next and finally back to the start is the smallest possible.
        - We can find a lower bound by performing exactly the same analysis as the sorting problem. We find a lower bound: $$\Omega(n\log n)$$ 
    - 
- **Lecture 2** (Running time, Turing machines)
    - Formalising Algorithms 
        - To prove a lower bound on the complexity of a problem, we cannot use a specific algorithm - we instead need to proof a statement about **all algorithms**. 
        - To do this we need a mathematically precise definition of an algorithm, for this we will use a **Turing Machine. **These are well suited for proofs about all algorithms. 
    - Turing Machines 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6KTR1WbjpY8b-uhImigsS8NA4NRY5GnsOHKOKHeP8Yag5nM1RWUZHYy80cYWR2enR9P63w0SC-m2YWGlSTz7HgI8m8WE5cmN4JktY5eKuM2pOLoYXcG4OGshtCFW2rxJ.png) 
        - The transition function takes the current state and symbol, and outputs (the next state, the symbol to write, how to move).
        - What is the configuration of a Turing machine? hint: qwu  ↓ 
            - The configuration is a snapshot of all the information about the machines current progress.$$(q, w, u)$$ 
            - $w$ : The string of all symbols up to and including the  position the head is. 
            - $u$ : The string after the head up to a point, where after that point all cells are blank.
            - $q$ : The current state of the machine 
        - What happens when we read a left hand marker?―The machine is guaranteed to leave the left hand marker and move right.
        - Describes how the configuration changes:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9pEIPssJLuTmMNKn5-6bGJKOuP4tFNWG0QnuCWL5kd53er9yaPgjOTD5o-KcV9Sw93mRX93dleTsNf7AahVZhyWeEq1OvANSADGtJs7Ckc475GjUYFOFkB4I5k-t4koI.png) 
        - A sequence of configurations c1,...,cn where for each i $$c_i \rightarrow_M c_{i+1}$$
. Each transition is called a computation.
        - Starting in a specific configuration, there is a unique series of computations to reach another configuration. $\rightarrow_M^*$ means a non-zero sequence of computations. 
        - The language accepted by the machine is the set of strings, such that a configuration is reached with the acc state after some number of computations.
        - A language is **recursively enumerable **if {{it is L(M) for some M.}} A language is decidable, if it {{is L(M) for some machine M which halts on every input.}}  
A language is semi-decidable, if it is recursively enumerable. A function is computable if you can start at the configuration $(s, \rhd, x)$ and ends in $$(acc, \rhd f(x), \varepsilon)$$ 
    - Running Time 
        - For any Turing machine M, we associate a function $r: \N \rightarrow \N$ called the  _running time_  of M.  
        - r(n) is the length of the longest  __accepting __ computation of M, on an input of length n. The time taken for M to compute it's most tricky input - think a reversed list for bubble sort.
        - r(n) = 0 iff M does not accept any inputs of length n. 
    - Complexity 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NALCngAO-xDYhVKG6r9C_XrAY6Du5HJz8XD91nyoVkHs0QtxqXb-rWQQXnSCCV5USQqfoJVje0yiFrRORmMGJW6y5Sj6cAjrlYPbanOcmBkB3WsvQ9o3X66CLFQnzbNq.png) 
        - So for $f : \N \rightarrow \N$ the machine takes linear time. For a machine $f : \N \rightarrow \N^2$ the machine would take quadratic time etc. 
    - Decidability and Complexity 
        - For every decidable language L, there is a computable function $f$ such that $$L \in \text{TIME}(f)$$ 
        - We can know the running time is computable, because for the accepting machine M (which halts on all inputs by definition of decidability) simply enumerate all possible inputs of length n and count the running time of all of them - we then take the running time to be the largest value found.
        - If L(M) is not decidable, prove there is no r which computes the running time of
- **Lecture 3 **(Complexity classes, polynomial problems)
    - Decision Problems 
        - We'll always be interested in decision problems - of the form "is this string in a language L(M)"
For more complex optimization problems, if we find a related decision problem is NP hard - then so is the decision problem.
    - Complexity Classes 
        - What is a complexity class?―A complexity class is a **set of languages** determined by three things: A **model of computation **(Turing machine, register machine etc.), a **resource** and a **set of bounds** (functions that bound the amount of resources we can use).
        - The complexity class P is defined for a {{Turing machine}}, {{time as a resource}} and the {{polynomial functions}}.
    - Polynomial Time 
        - While being of polynomial time is a property of a {{language}}, members within that class like quadratic or linear are sensitive to the {{model of computation}}. For example a two-tape machine might be linear for a problem while a Turing machine might be quadratic. 
        - $$P = \bigcup_{k=1}^{\infin} \text{TIME}(n^k)$$ 
        - Polynomial serves as our formal model for what is feasibly computable.
    - Reachability 
        - Given a directed graph $G=(V,E)$ and two nodes $a,b \in V$ - we want to find out if there is a path from a to b. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qmW30wtygqYDgBGiYMxuhLRNWlfQAwwKD00nmMg3cgDVMnNNbi6m5ipiMgyoMf4hsg8CKv3PT5jSZS_zdqC09w5HU1IH_vDIPBa14-LwZ4Yq-YobK26-sVcl--vMgCz_.png)
To formally define reachability we would need to―Translate (E,C,a,b) into a string, and formalize it as the set of strings accepted by a Turing machine with Polynomial running time. 
        - This algorithm requires O(n^2) time, as it depends on the number of edges in the worst case. It's also O(n) space.
Therefore $\text{Reachability} \in P$ 
    - Euclid's Algorithm 
        - Consider the following decision problem:
$$\{(x,y)\  |\  \gcd(x,y)=1\}$$ 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zJVL0hNMSfuhdAuqtzBXUfjA6I68MgXmdPxIZr31kvny33vaLLlPSVij6ZWZdoPwEQkw8SGAMnx1ef8WGPNN1e32W-AktHtgsUcLSKE4iR-9ZIO_yNlUy0vBgtIl_akO.png) 
        - Why does Euclids Algorithm terminate?―Every iteration y becomes x mod y - and by the definition of y this is always decreasing (if x < y, then when we swap them the opposite will be true).
        - Give a patchwork proof that Euclid's algorithm is logarithmic―![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/0cl-TEBJ7Of4hLhb1NluXHBLtslCJ-KdekJw5aBEw7Ca7i3sYxap156fg3mhgzYCHsljLFRCXeqrBv4yUzqdL8o7AtlaUpV5qI-4CKKaR5FkIZEefTMRhKo1uGHsmFXs.png) 
        - Why would Euclid's algorithm not be Polynomial if it took $\theta(x)$ steps to terminate?―Because the **length **of the input is $\log(x) + \log(y)$ - that would be **exponential** in the length of the input. 
    - Primality 
        - Consider the decision problem:
$$\{x \ | \ x \ \ \text{is prime} \}$$ 
        - An obvious algorithm would be, for all y with $1 \lt y \le \sqrt{x}$ check where $y|x$. This requires $\Omega(\sqrt{x})$ steps - is therefore **not **polynomial in the length of the input ( $\log_{10}(x)$ ).
    - Boolean Expressions 
        - Boolean expressions are built up from an infinite set of variables:
$$X = \{x_1, x_2,... \}$$
**AND **the two constants  __true __ and  __false__ . 
        - An expression with variables can be evaluated **given **a truth assignment to it's variables.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/eM9dNHgitrq0-CXl_BGwATJjWsoXH2T56t2hg-VLNJPvIpYqEmVCEYzE0I2kfguWduOEsO7GAktmY6_84TiKWrekHxlJgmQGrsV_OBqchZ1IunvBzPmaV0cRKdfv2lgl.png) 
Expression 3 is unsatisfiable.
Expression 1 and 4 are valid.
Expression 2 is satisfiable. $x_1 \land x_2$ 
    - Boolean Evaluation 
        - There is a Turing machine which given an expression of length n (**without variables**) will determine in $O(n^2)$ time whether the expression evals to true. 
        - We do Boolean evaluation with the following rules:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FMcIth4Zo7uM3kzs3e-Yd2LWsXwRbcBfxczKRois3_eIy6hUQRsTtnIYnrqspZeRSSDYEn9ogh1ncB-OGCnG2_eXtv2Cu3uGT9MCNH2JybZb8gWBIFfHs7QSiUdnXx-9.png) 
Why is boolean evaluation $O(n^2)$?―Because every boolean formula will have at least one applicable rule from this list - then every O(n) scan reduces the formula by at least one symbol. 
So we require O(n) scans to finish, and each scan takes O(n) time - thus the complexity is $O(n^2)$. 
    - Satisfiability 
        - Is ther an assignment of truth values which would make the formula evaluate to true? 
Is a formula in SAT (the set of satisfiable functions).
        - The satisfiability of a boolean expression can be decided in time $O(n^2 2^n)$, why?―We've already found that evaluating a boolean expression is $O(n^2)$, and there are $2^n$ truth assignments. So we need to evaluate the boolean expression at most $2^n$ times! 
        - The question is $\text{SAT} \in P$ is a million dollar question. And is equivalent to proving is $P = NP$ 
    - Composites 
        - Consider the decision problem defined by $$\{ x \ | \ x \ \ \text{is not prime} \}$$ 
        - This is the **complement** of the language Prime. Composite is in P iff Prime is in P. 
    - Hamiltonian Graphs 
        - A path on a graph starting and ending at the same node, such that every node appears in the cycle exactly once. 
        - A graph is called **Hamiltonian **if it contains a Hamiltonian cycle. Encodes the language HAM. 
        - An example solution is to simply examine all $n!$ arrangements. We don't know if a polynomial problem is possible. 
    - Graph Isomorphism 
        - If you're given two graphs, are they really identical?
Is $\text{Graph Isomorphism} \in P$? 
        - There are $n!$ bijections we could test - e.g. reorder the vertices in n! ways.
        - An algorithm to compute this in: $$2^{({\log n})^c}$$ 
Exists.
    - Polynomial Verification 
        - Note that the search space of the previous problems is **exponential**. However, given a potential solution - deciding whether or not that is a solution is  __**easy**__ . 
- **Lecture 4** (Verifiers, completeness)
    - Verifiers 
        - What is a verifier?―A verifier for a language L has the following property given strings x & c: $$L = \{x \ | \ (x,c) \ \text{is accepted by V for some c} \}$$ 
I.e. A verification method for composite numbers would be check if $c\ |\ x \ \text{for some c}$. c stands for certificate.
If V runs in polynomial time **in the length of x **(not in the length of the whole input), then L is polynomially verifiable.
V is to demonstrate the whole idea of hard to generate but easy to test problems in NP. 
    - Nondeterminism 
        - If we relax the condition on $\delta$ being a function, and instead allow an arbitrary relation - we obtain a nondeterministic Turing machine.  
        - How do deterministic and non-deterministic Turing machines differ?―For nondeterministic machines, we relax the condition on $\delta$ being a function, and instead allow an arbitrary relation. E.g. There can be multiple options from a configuration:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9xbcGkwyRVnDmvCRFjHIZgznpfHnMt0n5zqRNkVHquJcf4dlSvDV3xS1ZrUW6HSCg3-3DC86YUpuQTVgkaPX-XH2EhK8avpfpxoriFnwYZjLJvVBzSYSpkvqWKLU9h4w.png) 
Note that the number of branches does **not **depend on the input x. 
        - For nondeterministic languages, a string is accepted if there is **some **computation path such that there is an accepting state.
    - Nondeterministic Complexity Classes
        - NTIME(f) is defined as the class of languages L accepted by nondeterministic Turing machine M, such that there is an accepting computation for every string in the language that completes in running time $O(f(n))$ - where n is the length of the input.
        - $$\text{NP} = \bigcup_{k=1}^\infin \text{NTIME}(n^k)$$ 
        - What is the NP class?―The collection of Languages who are accepted by nondeterministic Turing machines in polynomial time.
    - Nondeterminism 
        - If we bound the tree at f(n) for an input of length n - we lose nothing. Strings that are accepted do so, and strings that aren't clearly still wont be in the cutoff time
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/wpdXN11Xl1V1M41ECP23tL8OR3Hfr5gAmSaf2bGYoNnQ3wpsGQomlG8ehvjFQ6I_g_DbrT1_4Ihou9rn3dW6zPg0DrdxKhdqalaA0j_dIZVw2i-RYLeBoWUt3DkzqZOU.png) 
    - NP 
        - A language is polynomially verifiable **iff **it is in NP. 
Give a run through of the proof for this claim. ↓ 
            - ⇒ Assume L is polynomially verifiable. RTP that it is in NP.
For the language {0, 1}, consider a NTM that takes the input, and appends a 0 or a 1, then another 0 or a 1 and continues for p(n) steps: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/cOPDRwhcmI_pCoIdkjdWxcLLRslraHinHB4DgMSXvTDONGA8MC2k3nRDkEyRpF5XmtIJzIOpv2J5nij1ISBSQ-6Zarp2ro2FZvyOXuPK_BTDO1z60KdAQhrvOtGTgPuL.png) 
If an accepting state, this NTM will have a branch where it accepts it - otherwise it will reject. All in $\text{NTIME(p(n))}$.
Therefore, this Turing machine is NP. 
            - ⇐ Assume the non-deterministic machine M that accepts a language L is in NP. That is, it can accept/reject a string in polynomial time. 
RTP that L is polynomially verifiable.
Take V to simulate M. Take C to be a string which **deterministically, **tells you which branch of M to follow at each step - this will either accept or reject in polynomial time.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/BoMSLUJEPCeSwvPIJiCovJXO1u6gKp9KS9MAp005aHdnmEgESS83cEq2XvwxZBJwrd78J8yLHmkS9Tv0OqvsOqa3uh6KwFDesmUxZVnHkeZ37rXisoaxR2fk3GGHqxOh.png) 
    - Generate and Test
        - We can think of nondeterministic algorithms in the generate-and-test paradigm:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/atPmJfzPf3yIKyIFSYrUxIzvffIuXZmN9bzuwgBGit39IE7RFof3_1cWJc-W3WT8BmurQ6qqOrqYJzR9cfrQC9eWIWY1JdbZoQL1eEQkrBZT0cwUH9__i4LNCfV04zqv.png)
Where the generate is {{nondeterministic }}and the verify phase is {{deterministic }} .
    - Reductions 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/BkLVLu07OTSyXnGGNKapmGr5u4feGU8TOoHgEhajJgoEzzwGT_-rHNErz1biQgtt1hOYnKGJxL9WthU06ySQsPO8z8wTAoq5gFEBpBqXcAm0XWeCC1DltQIg86ItScOv.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/aBJIkrhqtR918iYAQCfHC5o0AsB1iCj6oh5PxXiTEKjRfFEQ-gt3drk91PtipEacV658y1rUZNqR9GNt95zSZJ772I9s2ac1RoC9aNQcMofjcSJPHMMA4emBCZ0VEaDG.png) 
        - What is a reduction?―A function (call it $f$), which given two languages L1 and L2 has the following property: If $x$ is in L1, then $f(x)$ is in L2.
I.e. a method of mapping from strings in one language to strings in another.
        - Given there exists a reduction of L1 and L2. Give a quick proof that if L2 is decidable, so is L1―For input x from L1, compute y = f(x) - then decide if y is in L2. 
We know ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/hMHi0ixunUKSHGYrWBnjQnD4VfEFUgv8au7zhNWNjv7ptUCzN17N11Ad-64FD9eoW32CAMUfiHq0BCsT4rvmK7AfZOwqMQwO7rnZojfaqMdBAMH2vQWYmFiMZnVvUzip.png), therefore $x \in L_1$. 
        - This also tells us, if $L_1$ is undecidable **then so is **$L_1$ and vice versa. This follows from the IFF. 
    - Resource bounded reductions 
        - If f is computable by a polynomial time algorithm, we say L1 is polynomial time reducible to L2. 
We write:
$$L_1 \le_p L_2$$ 
        - We can then say if $L_1 \le_p L_2$ and $L_2 \in P$ then $L_1 \in P$ - because computing f is polynomial, and verifying a given f(x) is also polynomial. So the whole thing must be polynomial.
        - In words what does $$L_1 \le_p L_2$$
actually mean?―In computability terms, L2 is at least as hard as L1. E.g. if L1 is not polynomial then neither is L1.  If L2 is polynomial so is L1.
Think about the fact that this is saying we can go from an element of L1 to L2 in polynomial time.
    - Completeness 
        - These reductions is that they allow us to establish the relative complexity of problems, even when we cannot prove absolute lower bounds.
        - What is NP hard?―A language L is NP hard, if for every language A in NP $$A \le_p L$$
So if we find a P time algorithm for L, we have one for all other languages. Since we can map between them.
        - What is NP complete―A language is NP complete, if it is NP hard and it is in NP.
        - 
- **Lecture 5** (SAT is np complete, compose reductions)
    - SAT is NP-complete 
        - SAT in NP proof
            - To establish this we need to show that for every language L in NP, there is a polynomial time reduction from L to SAT.
What do we need to do to show this?―We would need to show, that there exists a polynomial time function which maps a string $x$ to a formula $\varphi$ ($x \mapsto \varphi$) such that $$x \in L \implies \varphi \ \text{is satisfiable}$$
and $$x \not\in L \implies \varphi \ \text{is not satisfiable}$$ 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/SE5lg3WQaWSP1820iBXXY-yQjYNkW2egRKyqPPwEqd0PkKUOHH7ibI-vM5pKIzAgwWJ7vB1UN4GzXbB3tqSfuSLmYgJlYVwmC0r8qoXSjuzn2HUEdELZnK3MaFn8mVQf.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Jj0_NKJYXpmz9U5Eac4ko7gafr4nX-CSVGsqkSSGDcnbuSBztUzIWPbcPmNmzidwowKkLVLfQ2gWa2fg46xkKHoxepx8zqdVOgHc2kUJWlGXCeuHkJsaXc1kS-ncmXMz.png) 
            - The total number of boolean variables is $$(|\Sigma| + 1) . n^{2k} +  |Q|. n^k$$
Which is clearly a polynomial in n. 
            - What does this mean: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/oMz3Z7vpTBvltpGkEnn3rOWgEnd87_ika3qjXCcTX9VANBkN_Hb8VkaJIIl7_TNjqUM64MzIvUiHgAn8dsixpn7YtWAIfnztXMiHHkCeaLgQJ_WOVNx7jDmI3b7SJROI.png)―The head is never in two places at once.
            - What does this mean: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/nOiMh8k_jUGWi6ccpGMQ0duLiDNEe-TwUSp_i38mmc5aIUxi5LRdExMf8T9y84-TwMLzW2k0etmDqvKDT7NpMCY9yxtE-iRkGBJywzpfQ3RWPEOCTJr83-OMqBPzFaga.png)―The machine can never be in two states at the same time
            - What does this mean: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3yo-MOJTElHwnpRST7LsISwLNZBU9rXJryCjmB-2LUtF3HUSJM974pBOqmVBlhvlekj8mNdgDbi1XW7Fos5vwbHZpf2I83zgzXjabv1bEH1Ya_KcjUOkUghBMHnN_66Z.png)―You can never have two different symbols at the same place on the tape. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/nGSJl-BmbB7ii7aUgve4Nq3eOX5jDsavplpS8LrRyB7yXURx_dIC1t7H2FtN2Mxb-Y-jhORVfw5_jq_9d9Lzjj8leY6txGSNbSGTUMiUhNzVxUIbgYOCkd0gpsyQucVO.png) 
            - Explain this, you bloody idiot hahaaha:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/rytWPekMhwhV460rP7u3NOcKq0ZWwYFpI1qbDDpDQngWzD0Y9o-UY5CjIQHjl9Ek1q0SHmRW5cSwZKDFnMLwQQ0jhrb5BpnbreHDZ2R_OOjrGjKGATlA4zSVOri7wjWP.png)
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZaejmvmYP0etW1X_A7uS1E1gpU7_89MKBA2bviiPW-2NRlp0dI5flibG0N0aqbQRZcuAJNECmRZ2TKeGdSKg9-LxEoeAYIQwEZBhweiCjk4AlJcAb2h0xONPZOiIO-8t.png)―This means all changes are done according to delta. We iterate over all the possible transitions and ensure that the new result is in there. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2V7AwZupanlbDAgN1eiL2tCju4Mz1VF3gW7NhzefjzZZdncdwto8C37PxT_xH-PZtWqKD0g-ntlGD-DWI70qOOnA8sk9o0N0ovDGFFbnDKGRefsNA8fYos2hxFzQKVKw.png) 
            - Describe the basic idea of the proof that SAT is in NP―We're going to come up with a function that maps every string to a formula that represents the **accepting computation **of that string. We do this by mapping variables to actions on the turing machine - i.e. by ensuring all the transitions of the delta function are represented, ensuring the accepting state is reached etc. ~
So then if such an accepting computation exists on the string x, then the language is in L and the corresponding boolean formula is satisfiable!
        - CNF 
            - Conjunction of a set of clauses, each clause a disjunction of variables or negation of variables.
            - Conversion a boolean expression to CNF can result in exponential blow-up.
            - But we can convert our SAT solution above to use CNF, this means―That the more restricted problem CNF-SAT, is also in NP.
        - 3SAT 
            - A boolean expression is in **3CNF **if it is in CNF and each clause contains at most 3 literals. Note that not every boolean expression can be represented in 3CNF.
            - While we can't represent all boolean expressions in 3CF - there is a way to represent a boolean expression in 3CNF such that if the original formula is satisfiable, so is the resulting one. How is this done?―Hook them together like so:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bmhpbw8d5VOzfiBXKXbxZo7MBhnXxOYwdTxc1nuzQDtm9ZJ5Sxi4RsdEdjpN8SRQ2QsK7DFS2jLQrTU7n_ODh9sNpJ3SsDSbhVOZgbH9ayqPa530joCZhDoS5AGmZiVT.png) 
            - This hooking translation can be done in polynomial time, so we have $$\text{CNF-SAT} \le_p \text{3SAT}$$ 
        - Composing Reductions 
            - Note that polynomial time reductions are closed under composition: $$(L_1 \le_p L_2) \ \land \ (L_2 \le_p L_3) \implies L_1 \le_p L_3$$ 
            - If we show for some problem A in NP that $$\text{SAT} \le_p A \ \ \lor \ \ \text{3SAT} \le_p A$$
it follows that―A is also NP complete. Because we've shown a way of going from any language in NP to SAT. And we've shown that 3SAT is at least as hard as SAT via:
$$\text{SAT} \le_p \text{CNF-SAT} \le_p \text{3SAT}$$ 
    - Independent Set 
        - What is the independent set of a graph?―A subset of vertices with no adjoining edges. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/0AoJJ5-lPqopyLcgCzlRc-I4rYjACov3pWGQEJH2waAQJ30EmhKt6Rm29TUq-Gy8vgozaW8sGA61pQ4D57rfZrITzQi_y3c2e0dR3GpUiLW7BjzTlDucfKUKbHWVDamO.png)
Why can we turn this optimization problem into the decision problem―The decision problem is at least as hard, because if we have a polynomial optimisation solution - we clearly can modify that to solve the decision problem.  
        - How can we clearly tell that deciding if a graph contains independent sets with K or more vertices is in NP?―Because a polynomial verifier is easy to generate. Given a list of K or more vertices as the certificate, testing those will be polynomial.
        - How can we reduce 3SAT to IND? I.e. find a polynomial time mapping between 3SAT and IND  ↓ 
            - A boolean expression in 3CNF with $m$ clauses, will map to the IND string $(G, m)$.  
            - We obtain the graph via this:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/p2lDZSP9SvHu3vhXcDDhE8m6xGDz44fFBt9Knm4Ai_pPx9C8Q5IYZNcFIQKsH98VSZmAK0VtawYlAam2ujEaqXCfahGmk7SfjfVgIuaTlj5zqSmJYD-mwFLmXNw33fvn.png)
Like this:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/0beB5zQkOMzevz52qH-He7IPRIuB0kw_e_uw8iZGbwCb3xypF1XuS48-m1ZpjRHUC0o8hd5TCZEzjeCAsDyDOhS0poFzd-Rz5SwFECoOZgXUitBBVlRFMqqgAxoDEuuH.png) 
            - So, we need that if $\phi$ is satisfiable then G has an independent set with m vertices. 
Consider that this is satisfiable, iff no two connected nodes are true at the same time. E.g. we can pick one node from each triangle.
        - 
    - 
- **Lecture 6 **(k-colourability, clique)
    - 
    - Clique 
        - Given a graph $G = (V,E)$, a subset $X \subseteq V$  of the vertices is called a clique - if every node is connected to every other node in $X$.
        - We can massage that into the decision problem, where we test if G has a clique with K or more vertices. 
        - How can we quickly determine that the language $\text{CLIQUE}$ is in $NP$?―Given X as a certificate, it seems obvious that we can polynomially verify if X is a clique in G with K vertices. So, because such a verifier exists it's in NP.
        - What is the complexity of finding a clique of size 3?―It's $nC3$, but $O(n^3)$ 
        - Describe the reduction that tells us $$\text{IND} \le_p \text{CLIQUE}$$ ↓ 
            - We need a way of mapping from IND to CLIQUE polynomially. 
            - First note that the complement is the graph $\overline{G}$, is where you delete any edges and convert any non-edges to edges.
            - Then note that any independent set in $G$ is a clique in $\overline{G}$. I.e. if we inverse an independent set - they'll all be connected.
So we can go from IND to CLIQUE.
        - We now have the reductions:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vbSu0SSq1TlnsX1e9Fl83FAU8WghHWa13rW6qaYtPoFY22GyGr2iF9QK4EYRhgRr18_2hf8e4uXDvcOh8Wy9Sw49fXbLk9Bnf35IAELudYfKkxQfBkLsGuB8FwOiXRTR.png) 
    - k-Colourability 
        - A graph is k-colourable if―every vertex with an edge between them has a different one of the k colours.
        - The decision problem then becomes, find me the minimum number of colours required to colour a graph.
        - Describe an algorithm for finding if a graph is 2-colourable―First choose a colour for a node, e.g. blue. Then choose the other colour for it's neighbours say blue. Continue this, colouring all neighbours of each node the opposite colour. If ever you get stuck, the graph is not 2 colourable.
If the graph is separated, pick a different uncoloured vertex and start again in each separated part. No backtracking.
    - 3-Colourability 
        - To show NP-completeness, we can construct a reduction from 3SAT to 3-Colourability.
        - Describe the reduction from 3SAT to 3-Colourability ↓ 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/HNa9ccf6lJSvlXIeE2snbPA1aJ8Y3tlqYsW8OOL82dvtycR68p4aboQMDLgY8sUWkR7-576w0hjDXLFjLX_XXnnBJQdEj-VQ3dKb3rIsWdykNLlJ8UnZtBGAP0hhw9Gh.jpeg) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/eBEbq1shFIyOo85CAPO2FwXUL0wjYBlirP91juFASm0820PE50MXzq71Y0Km8gSv6JAXYeaN0zk5ZTr5O8X0GWNBh8rc7XLglbj-oePtl1kxZO8wkBSJAD4rYxna-Fvx.jpeg) 
    - Current reductions 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FK5PdD4f0x-XAY29McLuL6PdvIAQn0l81y4-DeFbyS9jA5pAXPvs54krCryrxZu3UP8u6tC4k6P1ucjCmDaS3e_C0qit8YaDEWR8fCSU9BHPEcTgSq-24eCr5FkumADs.png) 
    - Hamiltonian Graphs
        - A note on proofs using 3SAT 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/LtzPVYLKQNIGwY9NPfDHylPQOwXpu7XqiYbueuUY5BuMHpfg9rflMzMCCo2ohs3oIm-wO-i-8d6ly1c5E7_HEKP1URX1megTfZHrMp2YevvBWeAqx75aicbPjJDMttix.png) 
            - When reducing from 3SAT to other problems, we have two pieces. We have the {{variable gadgets}} and we have {{constraints}}.
e.g. We have the pieces of the graph that encode a variable {{being True or False (some connection between }}$X${{ and }}$\overline{X}${{).}} And we have the sections that {{constrain the graph to behave as we'd like}}.
E.g: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/BHAJh8QvrIRVLg39-RD0qk48MSvrRjDKuER22IO3kc6l3dTlYLSbBA6k9hgO_lhtDnyh67qIdlt-dNlz7iLeR9kRzpY-CBYaRdhhPa94R9XW6bntWhWwFybxX28JC9ON.png) 
    - Travelling Salesman 
        - Decision problem version, does there exist a path which returns back on itself and has an explicit target cost $t$. So we pass: $$(V, c:V \times V \rightarrow \N, t)$$ 
        - Clearly the problem is in NP, we can verify it using a certificate. Total cost less than or equal to t.
        - Describe the reduction from **HAM **to **TSP**: ↓ 
            - We're mapping $(V,E)$ to the triple $(V, c:V \times V \rightarrow \N, n)$. 
            - We can do this by making the cost function:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_KT34ohpyQmGXJSK0yszyqwbLVQMf73I2BfsVu9mm0qc75UgYwmu5QWspt2CodhRCUE4NVIdQQHXmHPet1zClJkHfajt1_gc7mv7Gu170sqScdt3fFBaU6_O3lOuhxLj.png)
This will mean the shortest path will always be the Hamiltonian cycle! 
            - So if a Hamiltonian cycle exists, then there exists a shortest path of length n (Where n is the number of vertices). 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/czqnrM54kQYkDEnPmdKz2MscJUy61K1PWvqEj4mhH0h1ALgH8o7VIL02mDBwdeWUuw2mcUkza2CB1za_Ze99-0xQ4fDUxomfWpIaN0MXtmFdIuECBgsEXcAwiy45hnXp.png) 
    - 
- **Lecture 7** (3D-Matching,Knapsack)
    - Bipartite Matching 
        - Problem where you want to match a set X to a set Y optimally - e.g. match all X to a compatible Y. Consider X to be your organ donors and Y to be organ recipients.
        - This is solvable in polynomial time.
    - 3D matching 
        - 3 sets x,y,z and you want to form optimal triples (x,y,z). The decision problem is―Is there a set of triples M', such that each element X Y and Z appears in exactly **one **triple in M'. 
        - We can show this is NP-complete by a reduction from 3SAT.
        - Reduction proof 
            - Take $\varphi$ to be a **3-CNF **formula with n variables and m clauses. We will then form X, Y and Z.
            - We create $x_{v_i}$ and $y_{v_i}$, one for each variable v and clause i. 
We also add $z_{v_i}$ and $\overline{z}_{v_i}$.![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gMWXggiC7HhudRejVygtQCQuC-fLLpGywJA-apFLJbZwusp_3ENHbaMKDdZguVoIapXZZMVBlCO9Xq4q5Yz-3-Ot0jBCuHBf0fH5oxOjn-fhcbc5DNxuxVEepCYTFayO.png) 
            - We form the triples $(x_{v_i}, y_{v_i}, z_{v_i})$, $(x_{v_i}, y_{v_{i+1}}, \overline{z}_{v_i})$ for every i. Resulting in:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NfPLS6_g7dVcFos3DLjqhk9Iwf9b1UxQdozZqvhIULLaCieik65EjwRxl69SxJUz-KIkXOg7798DxBMe_h3jiUbjzOxtq_JVHxeDbUKvACEIz4Q1lE4WJ4OJ2dsGmZVp.png) 
            - So every element of x appears in two triples, every element of y appears in exactly two triples and every element of z appears in exactly one triple.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/MCJADSq8PzoobScy8wBLh9Xf01275a6lXJ9IFQgdeE-Gfugf0W8YrOJQ20J5hZghoa_OWnAAXqSpnVN2WgwmgLR2RCbftSJsxGruU0BgxBdzmOh_ONbBbk3UBgxVY_06.png) 
            - Note that when we take one triple, our next actions are forced. Meaning either all the $z$'s or all the $\overline{z}$'s are free for other triples.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/WEO6MzLl2AzrZkc89xLelPDoAFlpMoYMMGf01Qztu5BSIayXG8vD7pPDdpNKpSmdcSmcz6B_MC4aQV33SR5ItewU6eAgfKGHuiuDUMsFt-Up-YWC2w5NKA7kiq2tHQZ1.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ctC51e6cRZfjm6hYajJbIucd24TTMAAucRewT9zIEbWvaMpW7KiUpJMneKAjlnPybd227rWj-cJfZeFy5m85qFAvuDe82aDnv5UOD-sizoLfpsBPcYA9HmpvayBDs_4n.png) 
    - Set Covering 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jh6OLvU9FDLa7qRff2SPYxHdeFQxNk8HhLc-9yJP4_gkesW87w4PTtPoMt1bT_4lvMPG5smZpHH8nLJbzESeTyk-v9HOrbdeROS9Cie90Go9-Kgg3S7fJ56n_Qv0Ms5F.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/j4NJd193NEkbSI23VblHsFNVeQPUUsXqGFCf-AHr1cPECex4BsmWOcwR4DWoHJnHFZY8CZ3fnYQzAhlcNVc0-O1-tZwuq-mxAxOpOBV5fuxX_RHGI26rW1_CP0yYeisp.png) 
    - Knapsack 
        - We are given n items, we want to maximize value while minimizing weight. Can we select a subset of items who's weight is at most W and value is at least V. 
        - Reduction proof 
            - We will reduce from the Exact Cover by 3-Sets.  
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CAhhuQTyCBDYgPCuvzTg5sbsCWKu91uoKwiAzhEX1s8MDRdQXqbSujqep5ghWheRhsusECYpXaKUgZfb4LBjy-zT44i3n1hvdpjzaQbyquUUAKL8IBb67DkDMQf38pT2.png) 
            - 
            - Consider a table containing each subset S and the items 1-3n. Then we can form a binary number encoding which items each subset contains. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gvm4Rr3y6WmNuK0NIj81TnEbqf5XpZdGSQ3kRgiyvl8Tziag0LZtkMgi8iiOtzMenIZqTBXhPGgB5Tzniq6FBcENSC2RiJSsasLmeYGzO5UNOFB4_B6DS-6k0Zf2L9_I.png) 
            - The question then becomes, is there some sum of subsets such that the result is all ones (11111...1111) - however this can result in a carry in binary. So we view these as numbers in base (m+1). So we can never get carries.

            - So for every S we get: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZVMlKa6HgWVyChtu4AP5LbLfDnmxcwAwspUoAUg9AuGrnf6WbCGECr2UZrqoShyVpNV0yHvaOugqsN7KSb6BGDVsxqSWHJ3I_P4hS8xnwyp6QGFp2vwAy_vVQhFVo6Kv.png) 
            - The the target weight and value of all ones is: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7qJxiY7KGxuxcLXsbt-G5oPS09F-zIiQbJhbjH8KXRtME2yOlTQL7CBk1TShgpTt--l2o4wQHNmS8Wyv4Nf1KtwSBGYP3W8fW7eo7MOVnaJZq8BOihz8BeuSBnRBITS2.png) 
            - So if I can get all ones in the 3 cover problem, I can reach target weight and value in the knapsack problem.
    - Scheduling: 
        - Timetable design 
            - Given a set of work periods, a set of workers who can only work during certain periods and a set of tasks and assignments for workers so all tasks are completed?
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/AXo-n5HTNxG1dK8oCYoVdMyfP92aM-1MqaKwAcwhj8S6atIphVcxhgl5x0IBh7pSu-FyxokHjd-LowbIeEb1Z9KQqPkS77MvVRbqJo0v31IsOapbfRYMzNNBGCYGSV8P.png) 
- **Lecture 8** (Co-NP) 
    - Responses to NP-Completeness 
        - Does asymptotic complexity matter in your case?
        - What's the critical size (n goes from feasible to infeasible)? Is scalability important?
        - Are there guaranteed restrictions on the input? E.g. can we stray away from the worst case, e.g. is there a special purpose polynomial algorithm.
        - Will an approximate solution suffice? E.g. no more than double as bad as the best path
        - Are there useful heuristics to constrain the search? E.g. ways of ordering your choices that reduce backtracking
        - Can you use a SAT-solver? These are engineered to be **highly **efficient. 
    - Validity 
        - We define VAL as the set of valid Boolean expressions - e.g. those that are always true. Given that the inverse of a valid expression must not be satisfiable. We can reduce to SAT, by taking the not and finding if that's satisfiable.
        - We don't know if VAL is in NP, because the certificate would take exponential time to test.
    - Complementation 
        - If we exchange accepting states in a DTM, we get a machine that accepts $\overline{L}$. So if $L$ is in P then $\overline{L}$ is in P. 
Why does this argument not work for NP?―For NP we say a string is accepted if there exists a **path **to an accept string for that state. There can still be a reject state in the tree. So if you flip the acc and rej steps, there can still be an acc in there:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/pmQ25jUdBrAZ46IZehmcUWtPm16ubkc7ECQdz6du91FzjoaW889XBGH5CroXOFPkfnQxo-MptoEg4TtCWxls0SgzpeMvVZAXmKx45SW7LFqDjpJ2zVLj4iYAuB9Hxk5M.png) 
    - Succinct Certificates 
        - NP problems can be characterized as $$L = \{ x \  | \exists y \ R(x, y)   \}$$, describe the conditions R must satisfy.  ↓ 
            - R must be decidable in polynomial time, where y is the certificate for x. 
            - R must be polynomially balanced. I.e. y must be succinct. E.g. there must be some polynomial $p$ s.t. if x is n characters long then the length of y is at most p(n).
    - Co-NP 
        - The languages whose complements are in NP. We can thus take the complement of L and find: $$L' = \{ x \  | \forall y \ \lnot R(x, y)   \}$$
E.g. x is in Co-NP if for every string, all certificates deny it's membership in polynomial time. Written with the bounds on y we get:
$$L' = \{ x \  | \ \forall y \   (\ |y| < p(|x|) \implies \lnot R(x, y)\  )  \}$$ 
        - How do NP and co-NPs certificates differ?―NP is the language with succinct certificates of membership. Co-NP is the language with succinct certificates of disqualification.  
        - Most theorists think: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sKsbjpuKbuxQWxeoW2CB4dbBxcu4Ayi4yQ9eHS1AgbES6jXZrU1MoZxJZsj3JmXQRe6ACREDlUCKPlllMFBqR9LjW4y_qwqGbZ1nsFmol-8TGK2oqx0S0l4HwsZKBkGk.png)
E.g. all different. 
    - co-NP-Complete 
        - L is co NP-complete if L is in Co-NP and for every language A in co-LP $L \le_p L$. 
        - Why does $A \le_p B \implies \overline{A} \le_p \overline{B}$?―If I have a reduction that takes an element of A to an element of B - it must also take strings that are **not **in A to strings that are **not **in B. $$\text{x in A} \iff \text{f(x) in B}$$
Implies if x is not in A, f(x) must not be in B. 
    - Prime Numbers
        - PRIME is clearly in co-NP, as it is the complement of COMPOSITE which we know to be in NP (certificate exists). 
        - Is PRIME in P?―No! Because it's $\sqrt{n}$ in the **length of the input n** which is $\log(n)$!!! 
        - Testing if a number is prime is in NP:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/E7cxkG7-47-7eTj-g5jLPHLxaF-bGj69wL7gYT2qn8QVYGG-fpvukedMO6QhT1CW2fmQcCopV6fKEWTcCZQyTQL1VeZiqaLBTZKMu8iX61o71rVZu9BAZrUwHc8TVSMC.png)
We take a number r and all the prime divisors of your prime number p-1 as the certificate. However, you need to check that all the prime divisors are really prime - so you do this recursively and the result is still polynomial.
        - Testing if a number if prime is **in P!**
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/U1GC2X45o57hBKma1oEGTH68kSxb98cE2tyVupquXsl0054ECi8OFaOQDpL_EcUtkb_XEtTBNJNh6TYiHotEUfBu7lDu5-XFdaRS1zoB25gyamadL0qOTCjUywxGxeq-.png) 
    - Factors 
        - Given a number x and a number k, we ask if x has a factor s.t. $\text{1 < factor < k}$.
Show that FACTOR is in NP and Co-NP ↓ 
            - Clearly it's in NP, the certificate would just be the factor. 
            - We can also easily provide a certificate of disqualification, the prime factorisation of x - we could note that all values are above k and then multiply them all together to show they factor x. 
    - Graph Isomorphism 
        - Given two graphs, are they the same?
        - Shown to be quasi-polynomial time : $$\text{TIME}(n^{(\log n)^k})$$ 
    - Give an argument that $P \subseteq \text{Co-NP}$  ↓ 
        - We know for any language $L$ in $P$, $\overline{L}$ is also in $P$ as we can just invert the states of the Turing machine.  
        - We also know Co-NP is the set of all languages, which $L'$ such that $\overline{L'}$ is in NP. 
        - From 1 all languages $L$ in P are in NP, and from 2 $\overline{L}$ must be in Co-NP. Finally we know $\overline{L}$ is polynomially computable and thus in P.
Therefore, $P \subseteq \text{Co-NP}$  
    - 
- **Lecture 9 **(Cryptography and one-way functions)  
    - Factors 
        - We know that $\text{Factor} \in NP \ \cap \ \text{co-NP}$ 
    - Cryptography  
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/urgOB-faxvwY8VPdBKAxLLPMiyvlf4DIVWiTI1Fs6tg-JO1jggu_bsB02XS3oYlXv6vWYN38V6uwpEivOcB0LL_7Gb_it8S_d2nRMR4QSHuQBrOWqsCx6X1AyNfukger.png) 
        - In a **private key system**, we have the encryption key $e$ and the decryption key $d$ and we have two functions such that: $$D(E(x,e),d)=x$$ And $e$ AND $d$ are secret! 
    - One time pad 
        - The only way eve can decode a message, is by knowing the key.
If the original message $x$ and the encrypted message $y$ are known, we can get the pad.
$$e = x \oplus y$$ 
    - Public key cryptography 
        - Encryption key $e$ is public, decryption key $d$ is private! 
        - How does this set K relate to public key cryptography? $$K = \{ (y,z) \ | \ \text{for some }x\ \  x \le_{len} z , \ E(x,e) = y  \}$$―If this set is in P, then we can use it as a black box and find x with a binary search. E.g. exhaustively search all the possible strings. We also assume $|x| \le |y|^k$.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NGw00WuMszeIgx4HAeBAoeGKkji5ORsInC0ObTWbSQdaSbIjVjyliOi02jBP0btIh9qCY5q2FoZPLxm0Ji1Qm1GCEc4Bem_ddgv7OIBfWG6tt1Hz6sbbhc_r878mZAyM.png) 
    - One way functions 
        - One way functions must be:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/VeRv1DR0puQ0rCzvK8DLlmQ4aS1Jxr7TMn38pj-INhIR_nynFl0rNGr6q5Q4a9uUziN7rMQEnz4FNqlEYxI3wB2T1HKdwpMwCi2Dxlkhrxa444pbvMTMdjT7H_pc9-25.png) 
        - We can't prove the existence of one way functions **without at the same time proving P ≠ NP.** 
        - We would like to build our function such that the inverse is definitely in P, rather than something like FACTOR which we don't know if it's in NP or not.
    - UP 
        - A nondeterministic machine is unambiguous if―For any input x, there is at most one accepting state of the machine.
        - UP is the class of languages accepted by an **unambiguous NTM, **in polynomial time.  
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/GvHjU4A9gJtxjr8UtE1m79CV0nN-VZJvqzRgApurflBXz-7GD9id8YGrb-MkWdPhrGBHvM-sYoyDr3fMkGDoqRlaQmMkVTMmaHE5UsJB9KRLCBYHq6cRjh-Kgx1APiRI.png) 
e.g. **There's only one certificate!** 
        - Why is $P \subseteq UP$?―A **deterministic **Turing machine is like a unambiguous NTM - Theres only one computation path for each string! (and it either accepts or rejects). 
        - Why don't we think there are NP complete problems in UP?―?? TODO TODO 
        - One way functions exists **iff **$P \ne UP$. 
    - Proving one way functions iff P≠UP 
    - One-Way functions $\implies P \ne UP$ 
        - Suppose f is a one-way function, we will define the language $L_f$ by: $$L_f = \{(x,y) | \exist z. (z\le x \ \land \ f(z) = y )  \}$$
We will then show that $L_f$ is in UP but not in P. 
            - How do we know $L_f$ is in UP?―Because there is only a single z that can be used as a certificate because f is one-to-one. E.g. A non-deterministic Turing machine generating all the possible z's would only have **one **accept state.
            - How do we know $L_f$ is **not **in P?―If $L_f$ was in P, then $f^{-1}$ would be computable in polynomial time. However, this is a contradiction with our definition of f.
Because we could use our $L_f$ decider as a black box, and do the binary search.
    - $P \ne UP \implies$One-way functions exist 
        - Suppose L is a language in UP but not in P. Let $U$ be an unambiguous machine which accepts L. Then form the function $f_u$ which does the following:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/8Eh-ifXYSDGqBcuCqd8J9IeO9ELC_AtQ0fMDqpUInLGoSyVS6zOaQKnh1m7HVNUs3-xazBNiM7X42-NTeoCJuKollWKoiVOY-3NMD7P7WdQE6yGDoyEIbDvcl3JS7qNK.png)

            - Why is f one-to-one?―Clearly, for an input 0x there can only have been one input - x.
For 1y, x must be an accepting computation of y - and because U is unambiguous, there can only be one such computation.
            - Why is $|x|^{1/k} \le |f(x)| \le |x|^k$? ↓ 
                - Clearly $|f(x)| \le |x|^k$, as the length of f(x) is $|x|+1$ OR $|y|+1$ but y is in the first configuration described in $|x|$.
                - RTP $|x| \le |f(x)|^{k}$ . If $f(x)$begins with a zero, then $x$ is strictly less than $f(x)$. 
If $f(x)$ begins with a one, because U runs in polynomial time - the length of input y is less  
            - f is clearly computable in polynomial time.
            - Why does $f^{-1}$  being computable in polynomial time imply $L(u)\in P$ ?―Given a string z we simply add a one to the front and apply $f^{-1}$. If the computation this results in is valid then we accept, otherwise we reject. 
        - So we rely on $UP \ne P$ for one-way-functions to be correct. 
- **Lecture 10 **(Space complexity)
    - Space Complexity 
        - We define SPACE(f) as the languages accepted by a machine which uses $O(f(n))$ tape cells on inputs of length n. Counting only work space. 
        - NSPACE(f) is the class of languages accepted by nondeterministic Turing machines in O(f(n)) space.
        - Some definitions:
L, NL, PSPACE, NPSPACE, co-NL, co-NPSPACE
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/PumdKfa1TGUy-C0AHhPFzS1cmQfwTrg9dAsC4Va_dTUxU6SS5QC6GwOGSNRHsIYU8RYkbDfEPDHalKiHtDIrdfLgHP9d8dwc0v9AfLzbpJmJsZbXTnM8SgiJVYD2zZ0R.png) 
        - What are the languages **L, NL, PSPACE, NPSPACE**? ↓ 
            - L is SPACE(logn) - Deterministic Turing machines which use logn space. 
            - NL is NSPACE(logn) - NON-Deterministic Turing machines which use logn space.
            - PSPACE is the languages decidable by a Deterministic Turing machine in polynomial space 
            - NPSPACE is the languages decidable by a Non-Deterministic Turing machine in polynomial space
    - Constructible functions 
        - We want to prove $NP \subseteq PSPACE$ - and we will find the more general result $NTIME(f) \subseteq SPACE(f)$. It then follows immediately that $NP \subseteq PSPACE$ for **well behaved functions.** 
        - A function is constructible if  ↓ 
            - It is non-decreasing $\forall n. \  f(n+1) \ge f(n)$. 
            - There is a deterministic machine M which on any input of length n replaces the input with the string $0^{f(n)}$ and M runs in time $O(n+f(n))$ and uses $O(f(n))$ work space. 
Kind of saying if we can compute f, and we can only do that within the bounds of f.
        - If $f \ \& \ g$ are constructible then so are $f+g, f * g, 2^f$ and $f(g) \text{This last one provided f(n) > n}$ 
        - Describe how this :
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/twsCLVoV3hUrfQluCkHCAxYtD_4UQ1F-5tzJAMZ3EOWlMnCaWMV93OrpGlOjZcJZkyXJ__G6Ewb2n2XMOXQ-14h2-m_Oqp2WZhVnb0r6lShMXh0IMdy2E67dOOg6ecjD.png)
and this
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/dvqgObyZ04TMBjRtRnMqfg-EYSX5q5fS10NSKEwcwrOAjatCwBq0dmag26Juj02Uj21SJ_QkcV70sFaaLYcYJcO9WrKACrugSQk9s35Rx5Ao3lW4SCWt1mwcIkUkpRHp.png)
are related to this feature of constructible functions:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9-MeDGxRFI6U-aXEW-iEw2lX8s31D6HUF4gNYP6_kFK77Hhqcs9ZjRPooLqFhSizdTwBlZRacRQ-Z_sMI577S20ntT2syhiD-WzsdGjen2lV77MxSVu6Wfywt7LlTzXP.png)
 ↓ 
            - The difference between statement 1 and statement 2 is that statement 1 doesn't contain the "there is at least 1 accepting computation of length at most $O(f(n))$".  
            - The machine in which **all **computations can be completed in length $O(f(n))$ is just the machine from 1 but cut off at f(n) steps. This accepts the same language.
            - This is why we need 3. because we need the overhead of computing f(n) to not impact the time complexity.
    - Establishing Inclusions 
        - We will establish:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/BxKCNjbrkDAJ8OtfDrnaXNF9t3a1Rr8LG19TrMGTLibhZYXvbRYp3bX2DEu7aB0izpkcL6MXyAW2ZFIxUIeQiypHvuWUEsN9xRacYXzwIj0KM-MwGTqixMRSi4ob9ehE.png) 
    - Proving $\text{NTIME(f(n))} \subseteq \text{SPACE(f(n))}$ 
        - Consider a non-det machine:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/alqunfr2-dOJvrG7na2KbLNERaX5CQxsImMuBjopuH-vCLigXpIS1xdnVdy_7lAevjQuu4jrLZPbKyB9SlQrLbLPic1Lu7ZqMP4Ry-qu7tiv2Gr2Q1eghqEGkO5k66QN.png)
The branching factor is determined by the machine, and the **height **of the tree is determined by $f(n)$ (as long as it's constructible) 
        - Breadth first search by a det machine would have it's queue grow exponentially in the height of the tree. $b^{f(n)} \cdot f(n)$ 
        - Depth first search by a det machine, stack grows to at max $f(n) \cdot f(n)$ because we assume the size of each configuration is no bigger than $f(n)$ and the height of the tree is $f(n)$.  
This already implies $\text{NP}\subseteq \text{PSPACE}$, why?―Because NP is the non-deterministic machine whose time bound f(n) is polynomial. And any polynomial squared is still a polynomial. 
        - How do we improve on $f(n)^2$ time for our depth-first search?―Keep a stack of records of which branch you went down, this will be size $\log b \cdot f(n)$. Then when you reach a leaf go back to the start. You also have the current configuration which is $O(f(n))$. $$O(f(n)\cdot k + f(n) ) = O(f(n))$$ 
    - Proving $\text{NSPACE(f(n))} \subseteq \text{TIME(}k^{\log n + f(n)})$ 
        - Consider a non det machine in NSPACE(f(n))
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Iyd5yF4Bd_sTcvdMqSt5uB4WCIUNNFJCVecccU_srlXp4_uRVVWU0UvbvDszXldu7KILCUh2uWupUlyvvoXUAu1qOsPg0X4pKDI9uwyfokF4iEB3wiEPOLYHCo0pkIVt.png) 
We know only it's space bound, and thus if it exceeds f(n) cells used we can stop the computation.
        - The number of different possible strings on the tape is: $$|\Sigma| ^{f(n)}$$ 
So if you follow a computation branch, and it's longer than that - then the computation is in a cycle and will run forever.
So we have a time bound, exponential in $f(n)$ 
So we can simulate in $$b^{|\Sigma|^{f(n)}} \text{time}$$ 
        - Reachability 
            - Given a directed graph, determine if there is a path from two nodes a and b in the graph.
We can solve this with a simple algorithm in $O(n^2)$ 
            - We can simplify that to $$c^{f(n)} \cdot n$$ 
We keep n, as f(n) could be logarithmic or smaller, in which case n would be larger.
            - 
        - How many possible **configurations **are there for a non-det turing machine with input tape length x and working space bounded by $f(n)$? 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ncw714pwX6BWm7y4xgM1kPwfjrkmIffjok6MSJGgjfwtxJHnX1_XOMgdjdZGxMdFEH4VYD2HgrGxB-59Vx6KoM2GhVLVl24x8q8KZ7zLVcIfVSARWZuJILzg3iymTr-M.png)―$$|Q| \cdot c^{f(n)} \cdot f(n) \cdot n$$
Current state we could be in TIMES
number of symbols that could be on the tape (before and after) TIMES
number of places the head could be TIMES
number of possible places on the input tape the read head could be. 
        - Configuration graph 
            - Define the configuration graph to contain all the configurations, with edges between them if the machine can transition from one to the other in one step.
            - We then want to know, if the accepting configuration is reachable from the starting configuration.
            - Using the $O(V^2)$ algorithm for reachability, and a graph with $O(nc^{f(n)})$ configurations we get:
$$c' \cdot (n c^{f(n)})^2 \sim c' \cdot (c^n \cdot c^{f(n)})$$
We can bound n under $c^ {\log n}$. Then: $$c' \cdot (c^{\log n} \cdot c^{f(n)}) \sim  c' \cdot (c^{2(f(n) + \log n}))$$
Finally:
$$\sim k^{f(n) + \log n}$$ 
    - NL Reachability 
        - Describe the NL Reachability algorithm  ↓ 
            - Each node can be represented in $\log n$ bits. Write the index of your starting node. 
            - The repeatedly, if the current index i = b - then accept.
Otherwise, guess another index j and write it next to the first. If $i\rightarrow j$ is an edge, then replace i by j and continue else reject. 
            - This will guess all the paths in log(n) time and find the right one.
        - Savitch's Theorem 
            - We can show that reachability can be solved deterministically in $O((\log n)^2)$ space. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/aFAoAyIaolViowwg0w0j-R5coIUeobiF3e1TyiCjAxWzL27hJnux7wZcLJFg6KyOFSh1WVw3fwrO0EXBcscXSlFsmNTOYVmYOE3WDZNrkaZ8rfDg9U2iBjwzC39n47yT.png)
Finds the midpoint on our path - and connects the two halves. 
Depth of recursion is logn because we halve i each time. 
            - We can use this to show $$\text{NSPACE(f)} \subseteq \text{SPACE(f}^2)$$
As we can use the Savitch reachability algorithm to simulate the machine on the configurations:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/HQIKleY1xv69iNluTd9gq_L-L_amHYiGEp6mzxb3NJdcSGJZzF6gG7mjfh0FbjSbunrbseS4XvMh44iRYiQ3arxbVos-XkdkO7-k0N_xOSeZKpSpWpbG70PXhVYAA-R8.png) 
            - Note that we don't store the entire configuration graph on the working tape. We only need the graph to check if a pair of nodes are connected - we'll simply check if a given transition on a machine is valid.
            - By this:
$$\text{PSPACE = NPSPACE = co-NPSPACE}$$
As the square of a polynomial is a polynomial. 
        - We also have that $\text{NL=co-NL}$ by a proof we don't cover in the course.  
    - 
- **Lecture 11 **(Time Hierarchy, Logarithmic space reductions) 
    - Complexity 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jYOcpmRQcdutGXqGpWiq642-o4kqL_VvG0wiU9z8DDQjkwl9M4j7Lx2HUc7WLfcoPKg-5ECa0Rw2M626bPCqQQ-KkVthOE4mDs0I2sx-ZBhkwLpXbGjae_i2dRA4c_kt.png) 
    - Logarithmic space reduction 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/0AUN9U4pdTU3aSbgqcXeW-pUveMv2cK5TH_tMYEcfmQMChPkwGvyH1vqxXzyTF0KuBRZPKQphtitiprC1AZktn3f84hzl-JHE4nPV9TdmvlQGTDXN4drGrWES6gZZl5W.png) 
        - We form a machine with three tapes, an input tape (read-only), a working tape (limited to $O(\log n)$ tape cells), an output of size $f(x)$ (write only).
This is what computable in logarithmic space means.
        - $$A \le_L B \ \text{means} \ \\ x\in A \iff f(x) \in B$$ 
        - Why can a logarithmic space machine by simulated by a polynomial time machine?―Because the number of configurations is bounded by some polynomial, and we can do the reachability algo to simulate.
    - Can we compose logarithmic space functions 
        - To compose the machines, we can't afford to write out f(x) on our second machine - so we need to do something else.
        - ^^Didn't really understand this part^^
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ik3U068KM75Y4WIGGaDovYi-eqkkhlVe0hOt4WVDfVa6CsY8SznKzFo1MnDR9SzayRphDOR3n0tJrOXMJEII8eS1z6VijVqgPUaiQYLnhRWtabVpDfwQzl7iQgJbluAP.png) 
    - NP-complete Problems 
        - All the NP complete problems are complete under polynomial time AND logarithmic space reductions.
        - Clearly any logarithmic space reduction is equivalent to a polynomial time reduction - as they are equivalent.
        - Don't think you really have to understand, in the polynomial reductions the space used is very small.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/D_us1qbSGGCuZmb_rZlBKxhqUhcukTimV7vPdMOEpis7VRgvbsYKgaNwT55jstafJMUqA6_slDaeNDxvxd52daYNnoYiJnaMA4lMkDyZBwLEaDSqqS4ZQOiCFqU93-UT.png) 
    - Circuits 
        - Compact way of representing boolean formulae:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FkYv3dc_pbOJ4mOoMfiXc80CaoDJ8STqTiHgEi6zX2yBDpdsOb7gtudAY8X3SQ5d35TSdmg0jSptGodB2nPRTdLx3OSy_G7VtBRNy1fHZf4-B9Uq69mLRx8_QNNkF6pg.png)
Where subexpressions don't need to be repeated.
These can be so compact, that translating them to boolean algebra results in an exponential blowup. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JW9zBwqZ2Vh1JiJ4DG0zOttsI2p5ndK4jU5aAaY2TrIOOf7ZMrxZHYLopJv2Xol5j90WEb8BCEp2n-oYibM8vf1f0Yh0T0ScYid4bRRZ1p3p_XmoZqgJ7vG3-wuK2qkQ.png)
edge (i,j) then i<j just ensures an acyclic graph.
Every node V has indegree at most 2, just means each node has 0, 1 or 2 incoming edges. 
        - At each point $\lnot, \land, \lor$  you evaluate the result - until the final node when you have evaluated the whole circuit.
        - What is the circuit value problem?―Given a circuit, determine the value of the result node n.
This is solvable in polynomial time.
    - Reachability 
        - Note reachability is NL complete.
    - Provable Intractability 
        - We want to prove that some algorithms **cannot **be solved in polynomial time. We can prove $$P \ne EXP; L \ne PSPACE; NL \ne PSPACE; \\ NP \ne NEXP$$ 
    - Time Hierarchy Theorem 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JgVEygqFs-5LrQfwa9wABjqiaco32-4yVFyUACoA4KZFR87pZzW2nIUuRhSa421SVYnz9tRENwUXNVeIR6SN7xHHTdkr9HtxSfsSkeObWHK5JeiHnwk6R7GiMO5t4aE0.png) 
        - The f-bounded halting language is the language of encodings of Turing machines and inputs s.t. the encoded Turing machine accepts x in $f(|x|)$ steps:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YFvad_rknv_6y70xG74DduAmBxjFRKbimxIQp6qySs__JYTkR31Z_3fHnkd5TQup-qf3JzFAJVria3aAyBae0QxyQ4kV_kB_PeZkXCLB6cNfs_lPqsbm6jtZ-jMLQt4T.png) 
        - Then it can be shown that $H_f \in \text{TIME(}f(n)^2)$ - 
        - We do this by first putting [M] and x on the tape, THEN put a marker inbetween and calculate $f(|x|)$ to use as a counter. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ro015jaiCXaMC9_nKBuNklpFZk0UGBHVW2WyNEMbn07_iRCkXWkx62bjQK245FPSpybhSHaX2mX7q8RAMxh3L--DktOH4ukbLfzNJEwWa-4hHvMSttsBgxV2iITszCtn.png)
Then we simulate the machine to the right of $f(|x|)$ - and at every step we check of one step in $f(|x|)$. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_s6IGCBTQC4w4fHYpf0OYn00tHyBLHHG9tcUSIARljSp0bOBlT8EDtl6-Eofxq3Z8sJR8Rs4e5mjp-3uVnK9FiehYOVdi7JDDxKhsgN_ll35g9J2yUqKAkqzCx7CJtbI.png)
If we get to the end we reject, if we accept inbetween then we accept.
What is the running time of this?―We first write $f(|x|)$ which takes $f(|x|)$  time - and then at each step walking backwards and simulating takes roughly $f(|x|)$ steps. Therefore the running time is:
$$O(f(|x|)^2)$$ 
        - We can also show $$$$ - we do this by proving it's undecidable using the halting problem diagonalization argument
        - Suppose $H_f \in \text{TIME(}f(\lfloor{n/2 \rfloor}))$ - 
Define a new machine N does the following:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Spq1O7MzZi1XPNFYdshhxhtUNg57tqsM2Ba3Rq6rSVV3D-JCo8tixoVTPiBpYOWtR5haoWfX3ruJ8WRTmC4RdGcNCEfaDEze8r4nHNHLOOnuvoaj9ZVdR73Gy5h7zLSu.png)
Then note that the size of the input is $2|[M]| + 1$, THEREFORE this takes time $f(|[M]|)$ by our assumption.
THEN feed N input [N]:
N accepts [N] $\iff$ [N][N] NOT in $H_f$
                        $\iff$N does not accept [N] in
                                 $f(|M|)$ steps (by definition of 
                                  $H_f$.
                        $\iff$N does not accept [N]
 This is a contradiction, so our assumption must be false.
        - So we have generated a language which is in $\text{TIME(}f(n)^2)$ but not in $\text{TIME(}f(\lfloor{n/2 \rfloor}))$. And as $(2\cdot \lfloor n/2 \rfloor +1) = n$  we have the time hierarchy theory.  
    - Consequences of time hierarchy 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/TBM-fT4fxWy-aCL3EmGFoe-lEYMpkrIviKya8asVXw2zsCAcGKhikH0u9b-bZMNbOWk8uPeMuFVDitJT5cZZlL_mgvUZmb70lFQuB8-5jOB8VERx_RZIDGIUppQQdLaS.png)
So there's no power where we can calculate all polynomial languages with just that time complexity. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/c_Vs12d06oGEoNSBaIYJYrHwV2_OK1Bd6A1wK-C0fydCLkQkd5QJ3IWBt8X5oDvAlJcbIisDd_wmz69ukboiIfeMj30URNbc4ZpuQxxdpYIoADROumo3ie3hZUMH946c.png)
There are languages in higher classes of EXP, that cannot be decided by a lower class of EXP - Therefore there are languages in EXP that are not in P, as P is a subset of the lower class.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/OA2kHhW7WxyGLKqjDeqQVSTWCoEeye9lfkRmS6w6x7T4a2gqskkYG_qyKEtCOn5vgfb070pnBtm6yRB5i7XUt3zdDYvrpJrSvm8VbIhbKK6H2Uyo-3e7f9sFWOU5Ffye.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qomP6ROLkmRHFMlJbQ8W5cCmmOdrVkMVSg5GXKmk1F9kW14-0zhCOxaAWZ0n52pgvt8bWE7TcjoNVS58BT8lksd5uGNsXLqNBSHlCvcsbCVGuoBMlSaj7G3K0i2hDtGS.png)
By the first one, theres no one power in P such that it can solve all problems - so there is no such linear reduction. 
    - 
- 
- 
- **Supervision 1**  
    - Question 1 
        - Consider first that the salesman must travel to every node on the graph, of which there are $|V|$. Then consider the decision points of the algorithm, it must have a way of deciding between every possible route somewhere in the decision tree - otherwise we could craft an input to fool the algorithm. As there are $|V|!$ possible permutations of the $|V|$ nodes thus the length of one path along the decision tree is $\log( |V|!)$ (i.e. the number of comparisons to complete the algorithm) which we know is less than or equal to $|V| \log |V|$. So the lower bound on complexity is $|V|\log|V|$.

We can improve the lower bound by reasoning that there must be more than $|V|!$ nodes in the decision tree. For that we can consider paths where nodes can be visited more than once (which the above solution does not account for). For example consider a situation like this:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/lXDN3jkO7leNKz8Qi1Q7eKre3KtgzuIeAVo-71M906flc3aXWXcw4EcMMyn1rLXjmmdQe1GYKqO1l8Bjx8OmViezYXTVQWRksAutc-mAXC4LzMErJpEBz-Rj_fTadS_e.png) 
Where travelling back to a node is necessary.
Consider, if there is no possible way of repeating a node we would just have a one way line of nodes. Where the best path can be found in O(n) time.
^^CONTINUE^^ 
    - Question 2 
        - ```python
def TSP(start_node, nodes):
    visited[start_node] = True
    Cost = MAX_INT
    if len(nodes) == 2:
        return dist.get((list(nodes)[0], list(nodes)[1]), 
                        dist.get((list(nodes)[1], list(nodes)[0])))
    else:
        for i in nodes:
            for j in nodes:
                if i == j or i == start_node or visited.get(j, False) or not dist.__contains__((i,j)):
                    continue
                Cost[(i, nodes)] = min(TSP(j, nodes - {j}) + dist[(i,j)], Cost.get( (i,nodes), 0))
                Cost = min(Cost, Cost[(i, nodes)])
                visited[i] = True
    return Cost

``` 
        - There are a maximum of 2^n * n  subproblems, and each one is solvable in linear time. Therefore the problem is $O(n^2 2^n)$. 
    - Question 3 
        - Consider the finite automata M, which does the following:
First it counts the number of a's in the input. To do this, the machine will start with it's head over an a - it will then write an x and move all the way to the end of the string (moving right at every a) until it meets a 0 or a 1 - it will then add one to the little endian binary number stored there, before moving backwards before it meets an x. This process will be quadratic in the size of n.
Then having counted the n number of a's, it first find $\gcd(n,2)$ and if the answer is not one then terminate, do the same up to $\gcd(n,n-1)$.  
If all of the gcd's were 1, then the machine will accept the string - as n is prime.
Finding the GCD using Euclid's algorithm is polynomial,  (we can ensure this by setting the size of the binary strings as the minimum required to represent n), and we do this n times so the entire process is polynomial in n. 
Therefore the complexity is the sum of two polynomials, and is thus polynomial.
    - Question 4 
        - Assume Unary-S is in P, so there is some machine M which can verify if a string of a's is in Unary-S in polynomial time. 
Then consider a second machine M', which will convert a string in Unary-S into a string of a's beginning after Unary-S and then run M on that string of A's in polynomial time. 
The machine will function as follows:
1. When the machine encounters a 1 - if its at the first position on the tape it proceeds to the first empty space on the tape and writes an "a" - then it moves back to the first non-zero item on the tape. 
If it's not in the first position it writes a 0, walks backwards along the type writing ones until it reaches the first position and writes a 2.
2. When the machine encounters a 2, it writes a 1 and does the same as above - transitioning to the end of the string and writing an "a" - before retreating back to the first non-zero item.
3. When the machine iterates through the whole binary string only encountering 0's, it runs machine M on the string of a's.
        - An example execution is as follows
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ER6WMtwtKbwYzHKcDLdVbhaHeEomxgan3vRzQXevl5MCeM98idoGMAEJfgLpuc_hvd9JlRp5XMVYiqdodj1hl0n-6CZNDvzw6DMPHKwcJdiZJ4RLdLICjt8kb75wqqwi.jpeg) 
        - For a given binary digit, this reduces that digit to the sum of the previous digits + 1, which gives the same value - $2^n = 2^0 + 2^1 + ...+2^{n-1} + 1$, we can prove this from the geometric sum formula.  
        - The translation from binary to a string of a's has exponential running time, we can prove this as for a worst case input (a string of ones) we have to move n spots and then 2^i spots, where i is the number of a's we've written. We do this $2^n$ times (we know this as every 1 in 2^n eventually reaches the first spot) so the running time is: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/eA1SD9Vjul9YY7QWuYH3YsZz3NfY2akEXi7Vl7TjMBh39hCuE6T5uGD89e-vBNgpi8AAX1mwMwntRSt6mcg0hBPYXq62s-ER-c_K_wZCJBs7xsbcGksfI7BPYnl8FyHH.jpeg) 
        - The second part of the computation would be polynomial, so the exponential would continue to dominate. Resulting in a total running time of $2^{cn}$. 
    - Question 5 
        - a.) Assuming $q$ and $\lnot q$ are not distinct variables there are $n/2$ max possible vertices.
We can have $m$ max possible edges. 
        - b.) 
RTP( path $\implies \phi$ unsatisfiable  )
Assume paths from $x$ to $\lnot x$ and vice versa exist.
If a path exists from $x$ to $\lnot x$ , that implies that for a path P: $x, a_1, a_2,...,a_n, \lnot x$
Then we that our CNF statement contains the following: $$(x \implies a_1) \land (a_1 \implies a_2)\land...\land (a_n \implies \lnot x) \land R$$
Where R is the rest of the CNF formula. Consider that if x is true, then a1 must be false for the CNF to remain satisfiable. This continues with a2 needing to be true etc. Up to $\lnot x$ needing to be true. But this is impossible, so $a_n \implies \lnot x$ is false and the entire statement is unsatisfiable. Therefore, in order to ensure satisfiability $x$ must be false.

We can do the same with the path from $\lnot x$ to $x$, giving  $$(\lnot x \implies b_1) \land (b_1 \implies b_2)\land...\land (b_n \implies x) \land R'$$ 
By the same argument we find that $\lnot x$ must be false,  but that is a contradiction. We can't have both x and not x being false, so we will always arrive in one of the two states that result in unsatisfiability. Therefore the statement is unsatisfiable.

RTP ( $\phi$ unsatisfiable $\implies$ path)
Assume $\phi$ is unsatisfiable and no such path exists.
Then we have some implication chain in our CNF resulting in: $$T \implies ... \implies F$$
However, in a system where all we have is implication chains and variables. The only way of establishing falsehood is if we have $p \implies \lnot p \implies p$. So we must have chains $p \implies \lnot p$ and $\lnot p \implies p$. 
There fore ( $\phi$ unsatisfiable $\implies$ path).
 
        - c.) We can employ a method similar to finding cycles in a graph.
For every $p$, $\lnot p$ pair in the graph, compute a DFS from both of them - and if both searches reach the opposite node (e.g. not p reaches p) then report unsatisfiability.
DFS is $O(V)=O(n)$ and we can do it a maximum of n/2 times - resulting a time complexity of $O(n^2)$.  
        - d.) 
From b.) if a given formula is unsatisfiable, it must have a path $\phi$ in it which we can search for using c.). So, the algorithm from c.) can be used to find inconsistent CNF formulas in $O(n^2$) time.
Furthermore, converting from 2CNF to the form needed for graphing can be done in linear time - as there are only 4 combinations of variables.
Finally, converting from that form to a graph is linear in the number of vertices + edges. 
Since all of these operations are polynomial, the entire process is polynomial. 
        - e.) Because you cannot form the same implication chains with 3 distinct variables in each clause. 
    - Question 6 
        - Spent a good amount of time on a and couldn't make progress.
    - Question 7 
        - Assume $L_1 \le_p L_2$ , then there is some polynomial time algorithm for going from a member of L1 to a member of L2. So, if the result of that algorithm is in L2 then the argument to that function must have been in L1.
Assume $L_2 \in \text{Quasi-P}$ (This implies a machine M that accepts string in L2 in Quasi-P time exists), then an algorithm for testing if a string x is in L1 is as follows. 
First apply the aforementioned algorithm and get a resulting string $f(x)$ - then apply M to $f(x)$, if f(x) is in L2 then x is in L1 otherwise x is not in L1. 
This algorithm is in time Quasi-P, as the polynomial section will be dominated by the Quasi-P section for large enough x.  
^^Note that the input to the second alg^^^^orithm is of polynomial length, as we've spent polynomial time creating it. If you substitute for some ^^$n^c$^^ for n it falls out. ^^ 
        - Very iffy on this answer
    - Question 8 
        - a.) Start by colouring a certain vertex of the graph green, then colour it's neighbours blue - then colour their neighbours green etc (switching between green and blue each time). If we meet a green node that we were about to colour green, don't search it's neighbours. Continue until the whole graph is coloured or we try and colour a green node blue or vice versa.
If the graph is disconnected, repeat the process on those disconnected sections.
Since we encounter each node at most twice, this algorithm is linear in the number of vertices. Thus we can solve 2-colourability in polynomial time.
        - b.) To show k-colourability (L1) reduces to k+1-colourability (L2) we must show there is a polynomial algorithm from a k-colourable graph to a k+1 colourable graph. So if a graph is in L1, the transformation of this graph is in L2.
An obvious polynomial algorithm is to do nothing, because if a solution exists with k colours then we can solve it with k+1 colours. As we simply use the same colouring, there is no obligation to use all our colours. 

We know 3-colourability is in NP, so as we can reduce 3-colourability to 4-colourability - 4-colourability must be in NP. And we've previously found 3-colourability to be NP complete so 4-colourability (and in fact k>2 colourability) must be NP complete too.
- 
- **Lecture 12 **(NOT IN THE COURSE Descriptive Complexity)
    - Descriptive Complexity 
        - Complexity on the basis of how difficult it is to describe the problem. This is independent of particular machine models. 
We look at syntactic resources of definability in logic. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/wfsO0DcB6ioJ_c9zQ4ZSHIoYGod931o2lgps0HieGefvgfuMwTGrmr0UoXds4of2Np-B8rNp5NiM0aCbxKbFLAyqVaopEqyAKNlK4NeA_YkpBjQmgtv2QJK7hPrHV2fF.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/kn9n8TruetH8F_RX4CwDKoJcbP3UAW4KmerI8iYF3V_Yiog-TOAuNb11nwJcpwWBQrOdK13tVss5cJYaRJMeDNt9mtdKVpyi6UiM_rzPrySmK_MCw-886ZHWDAedunw3.png) 
        1. Needs 3 pointers, each needing logarithmic space 
    - Logical Definability 
        - In what kind of formal language can these decision problems be specified or defined?
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FjBa86DLUzUDZmP7djdq_iS5nTeLWDXc7S1NDjNsluXC-NAxTcGNXhKuz1G9DcnGYIyGTMBiCzWdcoYOwoq9X3Wc3VMFwA1zDTqYcQYWoKH_jIecBQtIiDVoCNP6jU4T.png) 
    - First-Order Logic 
        - First-order predicate logic formed from a collection of variables and formulas: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/84RY9MwIWISFZdjH5ofbyULPofx4-lI8xaVZwAvFeAX5v9_IMF7Ei-3UNOK8e09ZPTK8ALvXoGh5PYiW3XNMOOCszi9RQ1y9EXeTD3SQbdE9fN_EMtwf2yZsAKNDWqag.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/xX6m50KF5cl7RmMvtVoJKk-T_tESuQOfjb_yL20GsqCfciiFtFY5qA1B2LE-mBFhlC20CdVPeYJld03AtO-WaWwX8LYaIi66Xrnegc7cnYcxJ_P71BwG3lRAfAq9uB4A.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4HFmk5P8swe0hMHn16Qfbpc5Qk65jwSynUnOHgV5ydiDTIk9qpUa3g-ep2i4jl3LA1PIKKS3fQ9WfONl5rqC46t4sUbuH2XeqUFNp7OlOvFiKqtHC_R7xiTZt4QbwNyx.png) 
        - 
- 
