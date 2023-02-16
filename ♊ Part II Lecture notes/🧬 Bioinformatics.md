- To Ask supervisor
- 
- Lecture 1
    - Biology (Unexaminable)
        - We view DNA as a string of DNA bases, we only need one strand - because the other strand (in the helix) can be derived as the bases correspond.
        - Protein's are viewed as a labelled graph.
        - DNA and proteins are viewed as networks.
    - Parallel technological evolution
        - In the past large supercomputers were needed to sequence genomes, now it can be done on a small personal device.
        - DNA is big data, on the same order of magnitude as those collected by astronomical devices. Can be used for computing and storage.
    - Compressed information
        - Each base of DNA encodes 2 bits of information - because you have to choose between Purines and Pyrimidines and then within each class...
        - You have 46 chromosomes in each cell, in each cell the DNA strand could be stretched to 2 meters - and we have 3.7*10^13 cells in our body.
        - DNA is transcribed into RNA, and the RNA is translated into a protein.
        - A strand of DNA is copied into a strand of messenger RNA which leaves the nucleus - in the cytoplasm, through ribosomes the information in the messenger RNA is translated into a sequence of amino acids. The amino acids fold into a 3D graph.
        - A gene is a string of DNA, that produces something meaningful. Most genes act as instructions to make proteins. 
    - Gene and protein interactions as Graphs
        - Genes are activated or repressed by regulatory proteins which make the transcription easier or more difficult. Limit or enhance activity of a gene.
Genes are thus part of a genetic network.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/F5186hISK4XgmVk1FX8aVCjgiEr2GWz7dIuls0cdEzl76eTckozu0ri3w5hZ1mrO4kZfXk150Oyh9fS9g8nOUc3f2SmUd9EHYbh9oMVsYqSJWoIWABmZZSIiKyx7g1pt.png)
        - Proteins bind in different positions in the gene, they may form logic gates. An and gate can be formed from them some how.
        - Nature is programmed for self-assembly, construct complex mechanisms. This does not happen with our current technology.
    - Sequence Alignment (Examinable)
    - Sequence alignment is useful in bioinformatics if you want to find the insertions or deletions in a genome, for example due to mutation, if you want to find the similarities between genomes. Consider finding the part of a bacterium that causes death in people - you would want to track that in other bacterium and find similarities.
    - Computing LCS
        - For a prefix $v_i$ of length i and a prefix $w_j$ of length j, we can calculate LCS($v_i, w_j$) using the following formula:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9aU-fqMhK-IdrZ85TLrG457YdbbFwp6b8onr1TMv4GTpUcwd_kPTckVfchmxCa3KdZEEXgbeest6BUSPYi093x_CIcYVmsatz4YWk8z_aHyggS_8ixbz-96uRtiofYrF.png) 
Explain this formula→At every point where we're examining a letter of each string, we have two choices - we can step along $v_i$ and increment the value by zero (if the characters are not equal), we can step along $w_j$ (this can be done recursively) OR we can step along both because the string is the same.

NOTE: This does not only find continuous substrings, for example the strings:  __crashing__  and  __can __ will produce an output of 3 - we find the c, step along v until we find "a", and then continue until we find an a.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5w7C_V9sXAZzfg8hZsLufVUFXTPD37PNaUXuKYCdOnh8M5cSaxplSjanibkFKpQ3CtAKd7scsCaCtde-fZXHMSBxrKC8CUL8PpgeGAj5qKEa67sGE9QQiRwByO2NOl_9.png)
 
        - How could you alter this code to create a list storing the steps we took along our path towards the longest common substring? w will be the "y axis" and v will be the "x axis" of this list.```python
def lcs(v, w):
    if len(v) == 0 or len(w) == 0:
        return 0

    a = lcs(v[1:], w)
    b = lcs(v, w[1:])
    c = 0
    if v[0] == w[0]:
        c = lcs(v[1:], w[1:]) + 1
    
    result = max(a,b,c)
    return result
```→Our methodology will be to check if result is a, b or c - then depending on which one it is we'll either add a $\nwarrow$ if it's **c**, a $\uparrow$ if it's **b** and a  $\leftarrow$ if it's **a**. 
This can be done simply like the following:
```python
def lcs(v, w):
    if len(v) == 0 or len(w) == 0:
        return 0

    a = lcs(v[1:], w)
    b = lcs(v, w[1:])
    c = 0
    if v[0] == w[0]:
        c = lcs(v[1:], w[1:]) + 1
    
    result = max(a,b,c)

    y = len(ls) - len(w)
    x = len(ls[0]) - len(v)
    
    if result == a:
        ls[y][x] = '<'
    elif result == b:
        ls[y][x] = '^'
    else:
        ls[y][x] = '!'

    return result
``` 
    - Given you have a list of paths in the longest common substring traversal problem (like this except take v to be the x axis and w the y axis:)
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Tl63ChretKbMQr5scSSvV0OxWsMR6bhkozYMifQ2KRGxwfh1Juz7lqvzhLDlm9BMZfqMtT1qgEzYZmd7JATJLTs5uj2byc4CrXhJX_BOiLLgDbTj8obplM9zdhpo5bON.png) 
How would you go about writing a method to print out the string - it will have the following function signature ` print_lcs(v, y, x, ls):`  and will be called using: ` print_lcs(v[::-1],len(w)-1, len(v)-1, ls)`↓ ↓ 
        - We'll trace our path along the route starting from the bottom right.  
        - So - if the symbol at position ls[y][x] is a diagonal arrow - we'll call print_lcs(v[1:], y-1,x-1, ls) **and print out v[0] ** __**afterwards.**__  
        - If the symbol at ls[y][x] is an up arrow, then as v is the x axis it's unchanged so we call: print_lcs(v, y-1, x, ls)
        - Finally, if the symbol is a left arrow, then we call print_lcs(v[1:], y, x-1, ls)
        - ```python
def print_lcs(v, y, x, ls):
    if v == "":
        return
    if ls[y][x] == "!":
        print_lcs(v[1:], y-1, x-1, ls)
        print(v[0], end="")
    elif ls[y][x] == "^":
        print_lcs(v, y-1, x, ls)
    else:
        print_lcs(v[1:], y, x-1, ls)
``` 
        - What are hamming distance and edit distance and which is better for finding string alignment?↓ ↓ 
            - Hamming distance compares the ith letter v and w and checks if they're the same, if not add one to the distance. Trivial to compute
            - Edit distance finds the number of insertions (add a char), deletions (remove a char) and substitutions (switch one char to another) to **transform **one string to the other. This is non-trivial to compute. But note that's not what we're doing below - so wtf is he saying edit distance here for. The edit distance would be 2 - add a T at the beginning and delete the T at the end. 
            - Edit distance is better, consider this case:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4vPxCG52QVEYNqgc6CR7WuCJ3LQ11iDiJTbveJAhlrV5z0MgTUUfWpPHYEdlZ2d3YoDib4UIC0tdm-v3lUFs5li-H-ELL7MBa8o4zTAwMhqE3G6TIPzd3VhKnx624BD_.png)
- Lecture 2 
    - General Alignment Graph
        - General alignment graphs have the following equation:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gsQvqH8XMMazG0UYEsXO78-7eJQ5RkcOpEZm6wei9GFBh4bAupG-BDP0Ph9YQPK7LCVWJyufB4sLPdOBLG5U3ds-3_DeyXst_L0M-YAPhQ3M0i06Ul2sQ_fTyLDEfElh.png) 
Explain this→We add a reward for a match, and differing detriments to a non-alignment where we only search one substring and a  __different __ penalty if we move back along both strings. This is needed, because the best solution
TODO I DONT UNDERSTAND WHY THATS NEEDED 
        - Results in this:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2urK6YQZXIemgAxW3QDDx0tZYlbETUnYMSgVIq1E4UUOKS-YhsOPQ0c8FfZsdUuwAFUCcswWg1MHZVl3LQyxjltybM9gm_V-h_ziIgK7h7XQi15ME3YlTu10wm5VQyGo.png) 
    - Dynamic Programming solution to LCS
        - We want to solve the overall problem, by utilising computed solutions to sub-problems.
        - We notice three cases:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/h3rQA_v38Ratyg9ekCnOV2IOXkYlwRlDclEZ8nOdeTIt-nL2wap6nzASvm5gSUFzM10RYf20r6bBOZHK27ZhDrKan89fpZrdxOg1iBw1Mc9Ay3l7ZyikWImD0AzCEThU.png) 
        - We take the inductive assumption that $$F(i-1,j-1), F(i-1,j) \text{ and }F(i, j-1)$$are **optimal**. This is useful when working with $F(i,j)$. 
        - Describe local and global alignment ↓ 
            - Global alignment seeks to find the minimum edit distance for an  __entire sequence - __ This could be an entire genome. 
            - Local alignment seeks to find sections of exact alignment in the sequence. This will necessarily have at most an equal edit distance, and usually more, than global alignment.
        - The Needleman-Wunsch algorithm (for global alignment)
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/humgpeo4fZzIjWvRX38YV4y087CyIk6AyO4SSbp-U9t80GoRVX7oUHJusl7yw-AJVtsMMtFOyf0H76iajlqb9cr_CbO5MFKcHAO7N18-IhRcWXDUKJLMVFxUGu2H0zlQ.png) 
            - Explain the initialization step in the Global alignment algorithm:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yb2HoZn6w3txaekjP9QUBeV4980nh_8Vchv-0ldcaQfCtj3QTjRFwyIJMH1xQStBSVtFHFxT0nqyBmOOPRCdEns_hVRAPeG8xu80L9e4DHvCEqz67RN-pIpNZWn2PWn1.png)→We set the initial source to 0 - then we add a penalty along the x and y rows of our scoring matrix. These penalties correspond to setting a stretch of gaps.  I.e. if I add 2 gaps to i, then I am penalized -2d
            - Explain the main iteration of the global alignment algorithm:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/oupvXPstDA6SvUQx-G8iyEMmkxZzuUnkok4S0zojFhc-srDZlZjzHvkDO1u11SFogJ8-gI-J7WlbN2CZ_UcNaxW7hzwNa3ij5uLgqk6duiDoGwJli5toXwA0zRGAjV_b.png) ↓ 
                - We iterate over every pair of possible positions in our string use the subproblems to find the maximum in each case. s(x,y) means we compare the strings and give a reward if they're the same and a penalty otherwise.
                - We then only pick the maximum of those possible moves.
                - We also record our move so we can back-trace afterwards.
            - What is the space and time complexities of the Global alignment algorithm? ↓ 
                - The space complexity is clearly $O(mn)$. 
                - The time complexity is also $O(mn)$, because for each square we check in the matrix, the subcomponents will already have been computed - requiring only $O(1)$ add's. 
                - Note that backtracking also takes $O(m+n)$ (to get from one corner of the matrix to the next)
            - What problems could you have if two strings are different lengths, and how could you solve this?→If two strings are different lengths,  a large number of gaps may be required to properly align them. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/QXEAnRnM13eM41zfSi-WNTdAPy32r8DqtdIW4WHxAbjWRw7YszFoxH0Okf7GJBdc7_yCgKs1P7iTFuT5PwhjFlRiK7TvVae0cqWUQeccFVattOeA3e8sco1B6HW_nHaH.png)
To solve this we can make the initial gap cost 0 (when setting up the matrix):
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9QjZ7JZ0CbAWYsBNeFxqMj5YsSUiBBxuZGA4ZMdJu6dPc-cWAtTHC8NJSUFt2AFcMH2WrsBCyKMqRUfl8QakH0td13O-sB-NSWXh6TmGL3DYuIxWUyrxcEg0Spk2NKoA.png)
We could also change where we terminate - we would choose the maximum position to terminate at:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/RylCZ9yGgu4gWFHlDJnqp43WOZMzIyx_XXYsLNqYkYQkuRXqR09dvXP0OGyyb8D6ieAQbhrFSWa2iLVfmBHUH7cL3uoIeA8eQCGcLU957m4wWtfhyFwIpfgrauzVEx4f.png)
 
        - The local alignment: Smith-Waterman algorithm
            - Initialize with F(0,0)=F(0,j)=F(i,0)=0
            - We can either find the best local alignment, or all local alignments scoring more than some t - to find them all we'd iterate over all of them as usual and only take the ones more than some t.
        - Scoring Gaps
            - We previously assigned a fixed penalty $\sigma$ to each gap (indel). What could be the problem with this?→If we have many consecutive gaps, this penalty may be too severe. A series of k indels may represent a single evolutionary event.
So we want to distinguish between:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/8oiIRBXK-ym_YxiJ8Q-P8u1Koy4VezDoJMdrzhyfM24O7KpGwpj04-2nCSWtJd9AJPkpVMKVm8t0bKbNPVNElRfc2CsDlfsV-zZLn8jzksjb4mxgqHRBbA6Nu4cD_GqW.png)
            - You could also distinguish between A⇒G and A⇒T (for example) as one could represent a larger difference.
            - What is the PAM 250 log odds matrix?→Compares mutations against each other and gives a log score of the likelihood of the mutations. E.g. Y ⇒ P = -5 and Y ⇒ F is 7 - meaning Y⇒F is far more likely to occur. 
It was generated from a large dataset. Note that PAM 250 was computed using:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/MuA7su3b6oUHRKZ_NNa49o0DNBEJgrNwWN_uoJDOj_121WHvoJByk8RzSai0GZtT_RsFHCpAwf3DHZEYKCF83qllQaCQBW10LhaZ82G2ZNcMfCiQrxczrFCNrgjn-Us8.png)
            - How could we solve the problem of over penalising large gaps?↓ ↓ 
                - We could have distinct gap opening and gap extending scores - i.e. it costs more to open a gap than to extend it once it's open. 
This could be done with three layers, when we open a gap we switch, when we delete we switch layer:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/B-CGsimU2Mx9-za4bScPnow4s24gC28RcAKklrkGbhhWPIjkJgP6mcx2sXtjEEMKk7vVU4pNTQZM1oqzsny2SZ1u9Fa_BtpsqVGvS5vvx2e8ehu4v0oh6QXFVC39MRmh.png) 
                - We could even use a convex function measuring the score of continuing a gap 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/61YiNf4KBoLRfOd3Kgr5mOObrGYsEeARSF1ZD4TkqYWSchn0eSN0YN5czcF5nl8qtJuXUvFpm8yf_4cRJvcQRTvCBzjRpm4ZLJRrZ35FajrqsXQfnlB-p1LJuX-kmRM9.png)
            - What is the affine gaps algorithm?→A combination of two linear functions to calculate how to score a sequence with a certain number of gaps. Where $n$ is the number of gaps, $e$ is the cost of extending and $d$ is the cost of opening: $$\gamma (n) = d+(n-1)\times e$$
It's faster to compute than alternative scoring functions and it's effective. 
            - Banded Dynamic Programming
                - Describe banded dynamic programming→If you know the sequence is very similar, and thus the path through the graph will be close to a diagonal - then we can band the squares we examine to decrease time complexity. We do this we do our normal DP, but with ```python
for i in range(1, M): # as usual
	for j in range(i-k, i+k): # banding
		... 
```
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vgLXTLGF6mSsS8PS6TYU2GA_teL0AeTKjYjHyuSd0ABdGpmjkAAoE2E2ajoemgSMWROaSqNg0mEGzi_x27JfmZGhiFHlw2ZXM1-BUTWULscct_cjNxO7PJhzX9d-Kzju.png)
 
            - Computing alignment with linear memory
                - Computing the Prefix(i)
                    - The prefix(i) is→The length of the longest path from (0,0) to (i,m/2) -i.e. to the middle column:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9x_kEBvI0Xa_dziDNC4nBNiOL6Jht2dwGKvaTfLoUbhiMNdurPtcwLhrpvZNL2fBoY7ywKFdLT-H2KqwFGljMK4eaRfWGB9tvtkXDQKOdBGTr-YibLk9oStPdLbqZ6Im.png) 
                    - The suffix(i) is→The length of the longest path from (i,m/2) to (n,m) (the sink). 
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Iq3dL7cTjedDPuFnfmIu2bvBgEwlnbdowSJH150zNjylUL_jFvcRR8HD6l4UbbXni5JPx5tJxmqwmy5GL0vxqDcPnqjT80XvNyIPezURsG0N9NYHGlUXemrdx8wnr-XC.png)
We use these columns to compute the lengths using linear size memory - store in two columns as we go.→TODO I DIDNT UNDERSTAND THIS slides are in lecture2_lineartime
                    - 
- Lecture 2.5?
    - Four Russians technique
        - What are blocks in the four Russians?→Blocks are $t\times t$ partitions of the scoring matrix - rather than working square by square, blocks are inserted or deleted and aligned with each other. 
And a block path must path from block to block **via it's corners! ** 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/rnGBdkfv8aOJq8QOKLepvTdnN0N2Il4_CEaDzPztYpTNqz7xfdu03yxoJyx-Bi5Gxx-dbkl5JuKAHCY4HWPAOByMlBTSWmja8hgZY1J6YtQrlecrt7mNthkh37LeSYBO.png) 
        - You can insert or delete blocks as normal, meaning you have to solve a smaller alignment problem with runtime $O(n/t \times n/t)$ (if we don't include solving the smaller alignment). 
Then for each block we have to solve alignment, with size $t \times t$ - we have $n/t \times n/t$ of these, so the overall time complexity is $O(n^2)$.
Run DP on the corners of the blocks.
        - What value do we take t to be in the four Russians and why?→We take $t = \log n$ - then we calculate $4^t \times 4^t$ minialignments for **all pairs of strings of size t **and put them in a lookup table. 
This isn't too huge if t is small, if $t=(\log_2 n )/4$  then $4^t \times 4^t=n$. 
$n$ represents the total number of alignments, and thus the required size of the lookup table.
        - Give some intuition why storing the blocks in a lookup table helps speed up the calculation→Consider two strings u and v of length 4000. Then consider what happens if we take t to be 4. That means we have $\frac{4000^2}{4^2} = 1,000,000$ blocks.
Then if we're aligning DNA {T,C,G,A} there are 4 possible characters. That means there are $4^t = 256$ possible strings to align - then there are $4^t \times 4^t = 65536$ total possible alignments. 
As there are far fewer alignments than blocks, that means we must be computing the same alignments multiple times! We solve the same problems nearly a million times.
        - What is the final complexity of the four Russians, and why isn't the cost of generating the lookup table included in the complexity? ↓ 
            - Once we have the lookup table, we have n/t blocks in each string - the cost of aligning those blocks is $O(\frac{n^2}{t^2})$. Every time we do the alignment we look in the lookup table, which takes logn time, giving an overall complexity of $$O(\frac{n^2}{t^2} \times t) = O(\frac{n^2}{t}) = O(\frac{n^2}{\log n})$$ 
            - Creating the lookup table is comprised of computing $4^t \times 4^t = n$  computations of cost $t^2$ (I.e. we have 4^t possible strings, and each pair costs t^2 to align) - resulting in a total cost of $O(n t^2) = O(n (\log n)^2)$. 
Because $O(\frac{n^2}{\log n}) > O(n (\log n)^2)$ (as n goes to infinity) when you add the two the cost of first creating the matrix goes away in the big O.   
    - Block alignment in LCS
        - How does block alignment differ for the longest common subsequence?→We no longer just care about the corners of the blocks, instead we care about every block.  
                        ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Dp9T8Jphxyk1eTVEp5H97Jtobrek_4Qf02eCK8Pi1wmYEfz9h7I-n0zjO5zVQKLusBJZpYZjoNbu1J8o3uN3GfSxHRdSLFjDxCPrxUyM5p48LImxMAmuLLavEts1_rca.png)
        - Describe why there are $2^t$ possible scores for the LCS path through a block?→Because the score of a path is monotonically increasing and only ever increases by one, i.e. 0⇒1⇒2⇒2⇒3⇒4, we can encode that in a binary number of length t - where 1 is an increase and 0 means it stays the same. E.g.
                     ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/AZorl2flgs21LT6nRzzweOKbQUcO_XfE3CO0Z5asHUf2NVz99UkoEK8ofzmWZIZUuJHxUK18531UPbw3lSF_sdsrQo45_wTOiM8cjQC0Fj9Ej_-2r7jNLl6yBGBheeQ9.png) 
And this binary number has $2^t$ possible values.
        - What will the total size of the lookup table for the LCS path through a block be, and thus what will the complexity be? ↓ 
            - We've shown that each path has $2^t$ possible values, and we know there are $4^t$ possible strings. We are building a lookup table of **all **pairs of scores and **all **pairs of sequences.
So the lookup table will be $(2^t \times 2^t) \times (4^t \times 4^t) = 2^{6t}$. If we let $t = \frac{\log n}{4}$ then the lookup table is of size $n^{3/2}$.  
            - Filling up the lookup table takes $t^2 n^{3/2} = n^{1.5} (\log_2 n)^2$ which is dominated by the block alignment time. 
    - Computing RNA local folding
        - This part of the lecture is **even worse **than the previous part 
        - We store a set of paired positions on the interval [i,j], this tells us which bases are paired in the subsequence $x_i$ to $x_j$. 
We can form an optimal structure of pairings, by extending optimal substructures.
        - Suppose we know all optimal substructures of length less than $j-i+1$. The optimal substructure for [i,j] must be formed in one of four ways
            - i & j paired
            - i unpaired
            - j unpaired
            - A bifurcation where i and j are connected via a connective tract.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/0JEZjIRx-4ac1WjuuBdz5W3D28HobuQmeQQZf9DROXdIw2d3HVO4gE0VoAl0tGcG95ZBQWN--AgO3qb5-9XqCEfGvLw3DylGQ2_WIMgyz7Zb-OZqFQLd2RVMVKLG-EU-.png) 
            - Explain the Nussinov Folding algorithm and this formula used in it:
$$\gamma (i,j) = \max\begin{cases} 
\gamma (i+1,j) \\\gamma (i,j-1) 
\\\gamma (i+1,j-1) + \delta(i,j)
\\ max_{i<k<j} [\gamma (i,k) + \gamma (k+1,j)]

 \end{cases}$$↓ ↓ 
                - First, note that gamma gives the maximum number of base pairs in the segment [i,j]. This is a local alignment problem, but instead of one string on the row and one on the column -  __it's one folded string we're trying to align__ ! Also, the algorithm is trying to find the structure with **the most **nucleotide couplings. 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/AxvvIRBc9kXzKghWKRVFHjWP_dTsBLrrAJHJXWPek_KlDj8rqx_GtymhT6FDJi4e8TndRbxena4dEY15TClHaqzLOmmzWShtezRu1hZqEt3LLeJRUBxA1t52uN23gYUm.png) 
We first create the initial matrix. i.e. where i=j and j=i-1.
The i=j means the nucleotides are **not coupled to themselves. 
**The zero below, refers to the fact we **already know the nucleotides are in a chain! **  
                - $\gamma (i+1,j):$ This examines the element below our current position in the matrix. This is if i is unpaired, so we shift the sequence along and examine i+1 and j:
                                   ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jZlp63QPI41wywqCB45OvUj9ZZ27io0j7AcEqi_PRNIFszRenJfDLQIZqAaAFyAqxI-rMXlwYeMfWRyHB5m7ST9vh6QWiViyquMd-fK7o_qDvLJc_HSaE5LldYQyMaFi.png) 
                - $\gamma (i,j-1):$ This examines the element to the left of our current position.
                                    ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NDA8sSNhvQb3rdltqfO4QJuvfNv2GmTgDPwJcpImg3q11p3wRf1P7nFvMODAxDYuvx4SkaOg3U_8W2CXBlh-vfq-lSSZI8YT3GjrE3V4E-3ghG581f0CnptFVaukvRo2.png)
                - $\gamma (i+1,j-1) + \delta(i,j):$ This the element diagonally to the left **plus **a score (of 1) if $x_i$ and $x_j$ are a complementary base pair (0 otherwise). 
                                   ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/MJW0YeweLuZASU6TpmfcTQUGeFGkCUbiiaNnSsU5F07Ldw8RRcyiEXOgyLWZpFJrDRgCi5d5pOEmr00LQBTANkD48xTEGYZw0ZJCg-8HsklZXw2Uv7DJfPuibpwNrAbU.png)
                - $max_{i<k<j} [\gamma (i,k) + \gamma (k+1,j)]:$ You examine the current row, and the current column below you.
                         ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FjLisMzzfXZv2ZpDVabonFGRPq6l1jb23s29NedIKxfU5z3Y-qdsHD6r5XQ6q9sV2wYcp27o3v4JtlmH-3xK-tocQk8upKXgYpZ0DOfFXAlHjF7qE2cm-gt73j9JwabG.png) 
            - What is the complexity of the Nussinov Folding algorithm?→There are $O(n^2)$ squares, so that many terms to be computed - and each term takes $O(n)$ time to compute. So $O(n^3)$ time complexity and $O(n^2)$ space complexity. 
            - 
- Lecture 3 - Trees
    - Algorithms to Build Trees
        - Trees where the leaves are species - tells us about evolution. We have the ancestral node, the root, the internal nodes (fossils) and the living species as terminal nodes. We know trees are connected graphs with no cycles.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/1y-3Zpr8V1W3pj2DFEne2JqHMS3tCMULjIV5OS2RLXAkcvJfqf1LvnEUvhSswoj28GHjwIPPVMr4xC8p_C25c7mn-PMPc1IOVvVAzbc_80hyu14pa0AZH645r23Y73yR.png) 
        - What is an unrooted tree?→A tree with multiple nodes at the root level.
                                    ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ErWyP2IF1QLjqd70bjjiQF36-izIX_xAYvOuc40-qeoxMXPGvjZtlq1tgZVLn-lFZbTGc3bW7xtkB_dFAW_3WuuWrBEmkf0fQRxq_qLaNvf2lcFiwqt4j4S623XWpysG.png) 
So an unrooted tree is still connected and has no cycles, but it has no root!
        - These trees can have hundreds or thousands of species, so algorithms are needed. Additionally, while pairwise alignment can be useful and doable by humans - multiple alignment is more difficult, so difficult that humans find it near impossible.
        - What is a distance matrix?→A matrix with species as the axes, and the difference between their genomes (pairwise) as the values. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7fvtZB3nVW3c8401DJYqJPkESI_XTZ1SmNI_X3dhOC5g_4J1-b0hEs9_EBXOFLtZo7CJV5gnu9khF8G99VTrR7cQtjk0-RETk4R1scN9dJ0r2C5hARIFoW-SYKyELzvs.png) 
        - 
        - Distance based Phylogeny problem
            - What is the distance based phylogeny problem?→Given a distance matrix, construct an unrooted tree describing this matrix:
                     ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/SOdHY5WjwYWYt6Bzs7N64RRm2R8kpumdEce8fwvyzEdMw6sN3u0CvQYNvmPzKD8fkdQzEwV0cIyrX83b5yFKLAbV1QBqEd8bwjA6pIw_MnmgL_VAesxg7BwV9DK_99Ls.png) 
Phylogeny is the relationship between all organisms on earth that come from a common ancestor.
    - Additive Phylogeny
        - What's the difference between a distance matrix and an additive matrix?→All additive matrices are distance matrices, but the** inverse is not true**. 
An additive matrix is a matrix from which an unrooted tree can be formed, for some distance matrices you **cannot form such a tree**. 
        - What is a simple tree? How does this relate to additive matrices?→A tree with no nodes of degree 2 (e.g. no nodes with 2 edges connected to them). 
There is always a unique  __simple tree fitting an additive matrix.__  
        - Simple trees with at least 2 nodes, always contain neighbouring nodes - i.e. nodes that share a parent.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/w6MPGwnzdHRUJeS-2aIuRZ4F-z6BLLFCT4gaVvhbmFau5VTlWnY_jD_xTBe-J3-rBrnnVOKWkI0SMfAXBE8Axl4u4ZUXJL1oq-O8mddA1kbCKdb0DyPgLG3t9yixbs7V.png) 
        - Note that you can use this to remove i from the matrix while keeping all the information. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vR0QpjGsR2WKAsCFxluletGybwWMVtlKR9JRia9xx3GNJdAKpuqYeeCKiygVrqqqqaJD7t2PA9Hchi0NkvUVX1cVjEEhgoQTiEYroHVfik0wokCJgli4fqlNRCY9wERg.png) 
        - Trims until there are 3 nodes left.
    - Least-Squares Phylogeny
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/reYERG4AmYQ-Ck_jNILGgrMWUAHwK9EVSZGCZEObsllwrT8XL3ij5tmXm1U0PM5WReP5P12wJDTejw5E3QaCjdivgS64V5vZQB9iUzJ9rwTSxNZNdt8s8BB6WkOUcd5i.png) 
        - $\text{Discrepancy}(T,D)$ tells you what?→The least squares difference between a node in the tree and a value in the distance matrix: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gpH05nHbvrNoNJ9gjGOmJNEthPxax5ccD16hw_e0_PIVyksGB_Ey8GkHX89KFU-l3IFZosbuxYuHUNYJXVcUUwrhJtHbwpM2ssJX7G7NgUehfDxY4dMftpu4gYJ8ysqZ.png) 
        - Finding the tree that minimizes the square error is NP complete. 
    - Ultrametric Tree
        - What is a rooted binary tree?→There is one node of degree 2, and all others are degree 1 or 3. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/lXHxcx4xFLZ9GpuhbysJKLfAYDkuM85S_pffuPbw0nmJjrEDwGnFPd5QcJv7sE4Fhq5MbjATZoLFAPSYJgS05xKxcu279sXao9FnglHkIU5UJXu8DXTY8dSL0Pe0zgVV.png) 
        - What is an ultrametric tree?→A rooted binary tree where the distance from the root to any leaf is the same. 
    - UPGMA
        - Form a cluster for each present-day species, each containing a single leaf. Then Find the two closest clusters according to the average distance. 

        - Then Form a new node to connect those two clusters
        - Iterate until a single cluster contains all species
        - UPGMA doesn't "fit" a tree to a matrix - but it produces a tree for **any **matrix. The tree doesn't necessarily fit an additive matrix though.
    - Neighbour Joining
        - The neighbour-joining matrix is the matrix D* defined as![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/0tLj-USiggsxk5yhK8gitrxvoSluztq1m3F57HVuTqnqEgo2e7GqTbPoB1jkJwSfY6x4G_uOp5Lj6QRqos56Fsp2dxEr1BeD72-QoBqdoMaIHHCXwF1D6pEKA1DxHNck.png)
Where total distance is {{the sum of distances from i to every other leaf}}, and n is {{the size of one of the sides of the square matrix}} 
        - There are $n-2$ leaves outside of the ones we're currently considering. 
        - The total distances gives a regularization to make a fair comparison of i and j with respect to all other leaves.
        - What is the Neighbor-Joining theorem→If D is additive, then the smallest element of D* corresponds to neighbouring leaves in Tree(D):
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/pN07KLoCmSrtUuZwNbR0DKr4mXk1OT5xUaCExOykKsIWFnd1W9SbaZlLYMjM8yPkStxS_60hqJJpYFK5Y4krs1HoFBePA_s3SRUgce4oz9k1L-mmzN8UKokqemdUkC-I.png)
I.e. i and j are neighbours.
        - Describe the process of neighbour joining ↓ 
            1. First Construct the neighbour-joining matrix D* 
            2. Then select the smallest item in D*, finding nodes i & j
            3. Then compute $$\Delta_{i,j} = \frac{\text{TotalDistance}(i) - \text{TotalDistance}(j)}{n-2}$$ 
            4. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/AoAuiD2tqAweynWeis_SM6KOHauhMR30RUIS788xODC2N9GRCnWXscRSdzHRw_Nkl7HnCPfhPCFECWSO8Oi4dypElVfjBWe2UnMaf_pm4z7b98Oe3PFQI7PLINf0-eaX.png) 
            5. ??????????????? TODO
    - Small and Large Parsimony - trees and multialignment
        - In Parsimony, rather than a distance matrix - the characters themselves are used.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zuBHn8xQisa8Aw3ISVmU5kB83Xid4-E-L1LhlcMHB_jZbCB6iPEU71tSDEkHbpzrt6yUrtE9U2OipG4PYxV4ZJdKdIYLVj0Q8vG7PTkpM91bHE0WezV-6JIhuBhXNfX8.png) 
        - What is the parsimony score?→Sum of hamming distances along each edge
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/MhKWGII6k_DNRDl8eLVrJ-CNYyP4SRVv-jL5o4aDeadiYXKQ6S9R-lvQEOgluOnGygM3RMRJTIOPNqVr6iRo6PBrqeoeZWz592FW4O20_UponwUTjhjB0aOVDbdh6sKt.png) 
This gives us the total parsimony score of the tree - the lower the better.
        - Small parsimony problem
            - Find the most parsimonious labelling of the internal nodes of the rooted tree.
            - What is the small parsimony problem?→We try and find the most parsimonious labelling of a tree, by examining character by character - e.g. examine single symbols at a time. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vk4ghRaUy4MvyOQVfE4jCocdd7m2RFm6O4DeWQ2LdvXQVYCQD9xhwxO7f7yCWDkjmLPaBpQqKuEJoCDzI6ylMmtPeqpi-FKQpFT-SSe6JpHFuil4jvMd71DM8OC7xYTg.png)
            - Where $T_v$ is the minimum parsimony score of a subtree with root $v$, we define $s_k(v)$ (note the k) as the minimum parsimony score of $T_v$ over all labelling's of $T_v$ - assuming that $v$ is labelled by $k$. 
The minimum parsimony score for the tree is just the minimum value of $s_k(root)$ when we loop over k.
            - $$\delta_{i,j} = \begin{cases} 
{0 \ \text{  if  } i=j}\\{1 \text{otherwise}} \end{cases}$$ 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/wK3W8LV0I4EYeaY8XC5ogGh37fb8BeIH8_n935VZwvLFV5Ea16ZTk-ZENvs9NJ3hi1rtG-9R42jgc46fSoA1I6nZyXLH95gZcMaNm1YFG_m0aWEjpHVw-9rvZtYCAmPN.png) 
            - Describe the dynamic programming algorithm for solving small parsimony - what is the complexity?↓ ↓ 
                1. First build a binary tree with leaves equal to one set of aligned characters
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qTARUNroYY7m5lypLiThRP7dFlZu4dQY6ZWQawWroU6CxDaexPTGmuLnHnv11H9pbA8J0kmKLnJioWVdg_yXK-hSOSrXu9zUHF0yLgMABS-F5f2vclchebP0-w0g2lfa.png)
                2. Then work up and calculate the costs of every character
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mYQGXUsr9iSd9QOcCev5eTg26a0IHgqTKQvj-5xPI6rFw9v7xTjEftFm2xYktN-sSeKzIS7mY6-1vlXc3QFXIdCapxCN-mXbFYr1wyJub9-mtaThKrTE-S8jh_Cg_d7_.png)
You do this by iterating over the symbols, and take the symbol at each child to be the one with the minimum cost (previously calculated) - then put the cost of choosing each symbol to be based on the children nodes.
                3. We work up to the root, and choose it's symbol to be the minimum - then backtrack and flow down the tree choosing symbols as we go.
                4. The complexity is $O(mnk^2)$ where m is the number of species, n is the number of characters and k is the number of states (states = gcta for DNA). 
            - How do you small the small parsimony problem for an unrooted tree?→Iterate over all the nodes in the unrooted tree, take that node to be the root and calculate the max parsimony - then choose the highest result when you're done. 
        - Large Parsimony Problem
            - What's the difference between the large and small parsimony problem?→In the large parsimony problem, we need to consider who are neighbours - i.e. we need to find the most parsimonious tree of all the neighbours.
This problem is NP-Complete.
            - Given a set of strings, find a tree which has the minimum parsimony score. Takes strings of equal length and returns a rooted binary tree which minimises the parsimony score.
            - What is a nearest neighbour interchange?→Note that removing an internal edge, an edge connecting two internal nodes produces four subtrees:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ao7gjlXZXFu3TFROf2OwXIrh_K98piknNpFIFR76dYa_FxTWC1liRQ4S8Weqfin-_xdY00SirMcBkc5LifiP4STsr1ZNSrDTfwatlFHSHFLBPzTQdp6yML3NKp_sn0zb.png) 
Rearranging these subtrees is called a **nearest neighbour interchange.** 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vV0997ApslWzb6pDR902L1fEaI5K_0BG8iyzYJbJbrcTZxeZI1NBex6j6ozigLsqoQbziL8HUm_oJNmw4TLW2V9pwb39Yee6IMdGCJkzFML3NslgzPquHeI5KXUVeT0N.png)
(These are the only 3 options)
            - Describe how you perform the greedy heuristic for large parsimony ↓ 
                1. Start with some arbitrary arrangement of the species in an unrooted tree structure
                2. Perform all possible nearest neighbour interchanges with respect to every internal edge
                3. Solve the small parsimony problem for every such tree
                4. If the parsimony score for any of them is better than the current tree, set the current tree to that tree and go to (2). Otherwise, return your current tree.
            - Describe tree validation with the bootstrap algorithm ↓ 
                1. Given a sequence of N nucleotides and an ancestral tree for those nucleotides (we'll call the tree T), we select X characters from all of them and replace them with something else.
                2. Then, we perform the same tree building as before. Resulting in a tree we can compare against T.
                3. Every internal branch that's the same as T  __**in terms of topology**__  get's a score of 1 (otherwise no points added). 
                4. This procedure of resampling, tree reconstruction and comparison is repeated 100s of times and the percentage of agreement is recorded.
                5. Finally, the percentage is given and if it's 95% or higher for a given branch - that branch is considered to be correct. Note will not be too large, so the bootstrap value is looking for broad stroke correctness - we don't want a tree to be based on just a few columns!
        - Generalising Pairwise to multiple alignment
            - How do you generalise pairwise to multiple alignment?→Instead of building a path within a 2D matrix, instead we build a path within a 3D cube (or higher dimensions) flowing through the cube using DP as normal with a DP algorithm like:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/s9vmIRC1Hh8MMPAKTpR8cvXUrp65WnQfRvjGTgjU49vTVcLseJ8Js5zd9GuqAJW9voub-qJDV7Ra0jWWjywDCqaWSv6w_xLpJXhbVyGIcQr_8DxEZ46Xden_uknxv3Ut.png) 
            - For 3 sequences of length n, the runtime is proportional to $7n^3$. For k-way alignment - the runtime is $2^k n^k$. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/OvkUThaOMWp0Dr_6oK-3IrTfo4E1yGL-xmBn0l0U9ySZUx-GtqZNcbJQErtbSkChM7QhEOpA15R4ElWCTrVq4EOYqpfSxdVQbKyLFDJVBpM12i2uLfBtcdhG50n9u-QX.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NvwuCX8O3yz9O38bV6tDPWLubDEoxHqMvwQLviaUYtr8EO6FamMJCSHlMUH6OSgcuz3pJ3bea_Jh25S8UJVv7nIDQXwL043y9iEQZFU3rj8Z_QbCoRZLJuncmLlFHcng.png)TODO→TODO 
    - Evolutionary tree reconstruction today
        - Anatomical or behavioural characteristics can be controversial - genetic analysis gives a more objective view (maybe).
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/M5sCN9OXZ2gfUVJF7WyS2eBqM0CqtjOPxjHZgp6PXmA3cJaeM9wa3Cw-k3GC7sQkVWtepHYO4cS5Y4RvJ4Ve7W6ORsV80i5lTHIhYkWm5nNKds3kopq_CxUaDg23sm3Z.png) 
        - Because non-Africans and Africans have a common ancestor, and the common ancestors of Africans were before non-Africans - this gave rise to the out of Africa hypothesis. 
        - Differing genetic datasets can result in different phylogeny! 
- Lecture 4 - Genome Sequencing
    - Yeast Genes responsible for Wine-making
        - Wine is created in sealed barrels, because when the yeast finishes converting the glucose to ethanol - it's metabolism changes to allow it to feast on the ethanol to survive (the diauxic shift) **this shift can only occur in the presence of oxygen**.  
        - Whole Genome duplication model - big leaps in evolution would **not be possible **without whole genome duplication. If we have to form new metabolising cells, easier to start from a copy of the first - without impacting the first.
    - Gene Expression Matrices
        - How do we form an expression matrix?→We measure the expression of various yeast genes at 7 checkpoints along the timeline of the diauxic shift (or any such biological construct) to form a gene expression matrix.
The gene expression level is the number of transcripts the gene produces.
        - We see which genes' expression levels increase or decrease:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gCR-k_Bey0692mFFWEbXC2gL7fGATEZNQEom244-ddXSNWSqWwkO0pZ6P6OqugqGSkL38hSVuiVRgZITKANBQ1880WmSDWIIQEmc_ROdke1ty_24lYkSVhUBC7aJ4Hno.png)
        - We then take logarithms of the genes expression levels, plot them all and try and cluster them!
    - Genome Sequencing
        - Genomes cannot be sequenced in one continuous read, we need to break it down into smaller reads and then combine them afterwards:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZlkM4jRI-SAJBkCGLQWdzPX9QihRXhMubq6knf91-h1I94tnHFejE49D9LdTkSt-LbpJtrWypTAftESvsIxAr2ataePIQO1FGHJn1efP7dWt3tXQ4afYPisd9_5RGHZj.png) 
        - The newspaper problem
            - If we had 100s of copies of the NY times for a day, we blow them up and we want to reconstruct from the remaining pieces.
            - We don't know where each read comes from - we only assume we have all the data.
        - Reconstructing a string
            - k-mers are substrings of length k which you may use to reconstruct the string.
            - First we arrange the k-mers in lexicographic order - then we draw arcs on the graph which mean we could slot one node somewhere to connect two nodes.
            - Once you have this graph, we need to find a **Hamiltonian path! **I.e. a path that visits every node exactly once. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YQ1kPbn3UBPMtR4xLNwpTPn3VpvdtEBTb7W5lpY3KMuolnC26Tq46ANodpLxk5WV36t4qfuek3XaLHhey7cGRSlTMIjUJ3HL2aj5E_Hg_wTAexzdpKayv7Cvtfxfuq8X.png)
            - How do you go from k-mers as nodes to k-mers as edges?→Take the k-mer as the edge, and the nodes as the prefix and suffix of the k-mer:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sG7niHkPAcWoSScR7q4sa2VDoeSuElkKvM3zsOR0fqOCo8iiwF2tKcz0Nv7vWhMxz3u0lNZqTN1-YPf7DXzUrpUbBsUFKs09K82jfd0GDep-3udjB4xfXtJ4vghTHbGa.png) 
            - Describe the process of reconstructing a string with k-mers as edges ↓ 
                - First build all your pairs of nodes, then glue together identically labelled nodes:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/LyeBJwgI1ndBd4q56A25Bo1RnE3IB-VUdzgOazK1IZl39lXF8yiYyfpdxuL_KR6gqUyDqf4rLzOwfCDIOhzVC0qvJ5m9CjMUj9WbVA9ERm7lzfUdQSf-yOF-dYATSJ71.png)
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/kEaF-AbIl2jjxtGb4Rhn9Prw05cd94qUStRXEQ44bhBeAGB05y_wF7KfDcWaCkB10je4-Rn1ppE6xuC8fHhynny7vBZ9x3zyWILe4BSYtEmmXQ9LI-9kbrHYRdzFFXxg.png)
                - We then glue together identically labelled - possibly forming cycles in the graph: **Giving us the De Bruijn Graph**
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/GxM73AqK6r937RW53IY_Fal0uuNqH4olk5ScTrN50hqJq4WuyIh6CAMGys1V2zsWk3LNi6NONobzkQjrm5SJFUVRat_RKjDec_OR-IaJy1flE1MBCYzyvOoPQGMYZaYM.png) ⇒
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/m8F6ZfI845mQnSY9DYKvuVTuGMsmhS68uqqu361xDqKgFcY8AFaGjptbZVAYN6c36uUYSYxMyrugGPjWOg0UDVYyj3EptMkd2pIs0zMpkQ3ZQRxA8LehPGITQDAJtaRh.png) ⇒
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/pdua5b2x9LxqUa-xmSP5L5A-M5KgjBchN-jxqG2pcc4IS9lODryyoomSSmufmTHMkdbphGgj6F_1oZavHIIB07plGGwUQEeYW-xAXZHXnFCdde-duznZFaUfgkxQaH9S.png) 
                - Then you find the **Eulerian path **(a path which visits each edge exactly once). Note that Eulerian paths is in P, while Hamiltonian paths is in NP.
        - Eulerian Paths
            - What is a balanced graph?→A balanced graph is a **DIRECTED **graph where every nodes in degree equals it's out degree (incoming vs outgoing nodes) - 
$$\text{Balanced graph} \iff \text{Eulerian Graph}$$ 
            - 
    - 
- Lecture 5 - Clustering
    - Clustering as an optimization Problem
        - Elements in the same cluster should be closer to each other than elements in different clusters. 
        - Describe the good clustering principle, what's the problem with it and what's the alternative?↓ ↓ 
            - The good clustering principle is: Find clusters where there exists a $\Delta$ s.t the distance between elements in the same cluster is less than $\Delta$ and the distance between elements in different clusters is greater than $\Delta$. 
            - There exist many clusters where there is no partition satisfying the good clustering principle - most datasets do not have partitions that satisfy it.
            - Instead we find centers of clusters and minimize some notion of distance from the data to the centers.
        - Finding centres of clusters
            - We define the max distance as the maximum distance from a center within a cluster - we would like to minimize those max distances.
            - Finding the max distance is NP complete.
        - Farthest First Traversal
            - Describe the process of farthest first traversal↓ ↓ 
                1. First we choose an arbitrary **Datapoint **as the first center of the cluster
                2. We then choose the next center as the datapoint  __furthest away __ from that first center.  
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/U2pYbIuzYPBa7ekWnIj1eu8fJrxHOGPwht84KmaUTV7KBE2GQeAw-DW3fYDMHGLupWAUsp70GYSgo0YjdJy_QqREzHdC5liC6f0tbgYpD9uziDAqTYO9MQkq9c61aDjk.png)
                3. For every center, we then find the distance from that center to every datapoint - and the datapoints closest to that center are associated with it.
                4. Then we choose a new center as the datapoint furthest away from every other center. 
                5. Then we loop from 3 until we reach the number of centers we wanted. 
            - What is wrong with FarthestFirstTraversal? What do we replace it with.→It minimizes maximum distance, but biologists are generally interested in average distance - the maximum distance is often an outlier. 
Instead we try and minimize the sum of squared distance divided by the number of datapoints - called the Distortion. This results in k-means clustering.
        - The Lloyd Algorithm and k-means
            - What is the center of gravity for a set of points? How does this relate to k-means clustering?→The sum of their vectors divided by the number of items there are - gives the center point. If trying to cluster a set of items into a single cluster, you can use center of gravity to find the center point.
            - Describe the process of the Lloyd Algorithm↓ ↓ 
                1. Select k arbitrary datapoints as centers
                2. Then assign datapoints to their closest clusters and find the center of gravity of these cluster
                3. Then assign datapoints to their closest clusters again and find the centers of gravity.
                4. Repeat 2 & 3 until all points stop moving.
            - The Lloyd algorithm converges because→When we assign a datapoint to different closest cluster, the Distortion is reduced - when we assign a new center the distortion is reduced, as the center of gravity is the only point minimizing the distortion.  
            - 
- 
- Supervision Notes
    - Bifurcation - we choose regions [i,k] and [k+1, j] to form two separate groups from
    - For additive phylogeny the base case is adding a node in the middle - which acts as a hub for the other 3 nodes. 
    - When you recurse backwards in additive phylogeny, you set the intermediate node to be 0 away from your new node in debald - 
    - For neighbour joining - you will get the same tree regardless of which minimum you pick.
    - For UPGMA with a heap - if you join i and j into k, the other 
    - Bioinformatic Algorithms
    - Remember the Smith-Waterman is for {{local alignment}} while the Needleman-Wunsch algorithm is for {{global alignment}}! 
    - TODO redo this - wrong for some reason→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/z9o0wf5y3kaxEbQ21VHu3VEc8oGBuiv9Rc5WpuLlLwUpNm8LyxiIvzqBhi7XkaCW2qADUHWkt0kU2r1pYIRgc4bB8eKqM6tEjdU_h9Nlpv8-zEkc4uGYnN8mlCfuZh0f.png) 
    - Don't forget $\Delta_{C,D} = TotalDistance(C) - TotalDistance(D)$ 
