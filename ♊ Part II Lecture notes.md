- Term 1
- 🧬 Bioinformatics
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
- Latex & MatLab
- 🦿 Introduction to Robotics
    - Lecture 1 - Introduction
        - What is a Robot?
            - A robot is an {{autonomous system}} that exists in the {{physical world}}, can {{sense it's environment}} and act {{on that environment}} to achieve some goal/s. 
            - Autonomous robots makes its own decisions and is not controlled by a human.
            - Building robots is becoming more affordable due to 3D printing and cheaper parts.
            - Robots are useful in the 3 D's - dirty, dull or dangerous. These are tasks **a human doesn't want to do **but need to be done. - So she says 
            - How does optimization improve robots' usefulness?―Giving robots a task means that process becomes computable and can be optimized over - this can make a task more efficient, safe and fast. 
For example, automated vehicles working together to optimize driving. Similarly, truck platoons to reduce drag & increase fuel efficiency.
        - What this course is about
            - The basics of autonomy are―Perception, decision making and action - these are controlled by the control architecture. 
These are instantiated in different ways for different types of robots. For example in mobile autonomous vehicles - Perception ⇒ location control, action ⇒ motion control,  decision making ⇒ Reacting now and planning later
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4dLjRk7hmirbCLzLJaLnTx3rsKAsq2TVamuf1HFR2UEmehiakpdaB9jP4lBqdn6mToxKo3RsjiPPNH_bRGCHk9IpLsBAUOCEhk37opMZLwzzA-m9E64hbOZEQgiNKRiq.png)
            - For multi-robot system you build upon these and add communication between robots.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/IhEtcFCqltUjJCKuWWBavdtG5voeJ9guplmoWUY95r4ng0moy2oztMYCcucWaxTRCZQ-WUXpaDCl9e1n0CZAAF0ijhOp4b_D0LnJa-TJcZOJF8v8HdHN601dO__4t2Jz.png)
        - Basics of Autonomy
            - Robots provides implementations of the following 3 modules - it also provides an architecture for combining these 3: Perception, action and decision making are useful for respectively― ↓ 
                - Sensing and modelling the world
                - Processing that information and taking action - for example modelling how exactly the motors must be actuated to reach a goal perception.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/TcUskQ-0F4yHWTWhfg7uLDG10OiVXL5IFi3wTv5fmmpWoBuDg6SJNX7wkoCMY86jepIzJ73IdclBvMhVEygf6r2wDDA8Ol7g1SosefXQHC_wO3aE9QMwPDJNFCmAw8FB.png)

                - Reasoning and planning in the face of uncertainty - for example compute a path to a goal that does not collide with any objects.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/dNChga1JzEDOSGVioShUVMeFL1j-B0C5pC-783i2oKSAQRR23uaL8j6FYRM8_L5ZY3SvmHw2TfJte3MmVVXHLGXFCqs1v_hPwXwlggQM7QX5ckNoc4cd2OGiWon1LnRg.png)
            - What are proprioceptive and exteroceptive sensors? (These relate to perception)― ↓ 
                - Proprioceptive sensors tell you something about the internal state or the actions of a robot. For example a gyroscope that tells the robot it's orientation or an **odometer **that tells the robot how far it's travelled. 
                - An exteroceptive sensor tells the robot information about it's surroundings. For example a camera or a microphone.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yJjm6NbYX16kThqAVT9kk3sfE8a8vX6sWwUibNxQ81aUdnjI_lQO2JHMEyO1fXijTG8RK6RRFfJqtgW6-mJAOUB3w24oO6Wc1f_YTWogt-5T4X0RCFMmnDWuzR_wwLJi.png)
        - An extremely simple robot
            - Consider an early Roomba with bump sensing, cliff sensing, wall sensing and an optical encoder (measures how far the robot is travelled given how much force it's exerted on the wheel.)
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/WkqUsmtV5kXarBYGNxlOpLuV1GjIPNDyPFoRcYLEu08WO_j231_ssD80CyxXqfHQ_dsqL9nWX6953j_Z9BJc7gIVXQSvIMEY8CDB7UjOsjXPCHxMgaxstTUp2HtlmWKd.png)
            - These simple sensors allow for wall following if it bumps into a wall, spiralling if it finds a dirty spot and going straight (turning at a random angle if it bumps into something or has travelled a certain distance)
        - The history of Robotics
            - Robotics came as an influence from Control Theory, Cybernetics and AI. 
**Control theory** being the mathematics of controlling machines, differential equations being very useful.
**Cybernetics **being the integration of sensing, action and the environment.
**AI **at the time being classical AI of decision making, not a neural network in sight. 
            - The first Robot:, built in the 1940s!
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/RtHTPVNS71uj3CPAmZXDOJcmhsTduWilp538NIpnbr2bMIoIm1jxkKj-jzHR-_ith3OJ3_Payhq4VZv8XvbnMD4U0eh-0uAa8ktPcEKHiALP7gJKHpDlQb5fQeSP1sUn.png) 
            - Braitenberg - a famous scientist who considered **reverse engineering **processes to reproduce the same behaviours we see in nature. He tried to reproduce complex behaviours with simple robots (Gedanken experiments, not real robots) ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/V2kO3cSVXb6Eqpj6tHqEC3qWriGIFeypVgdrYWsshlkFoy6ebG-r5dRvyJ6E_ju7c9rldF3SopbP_fAfeGtKP5drKlntiaY8M93T7pxmr0gHp6NASI2OSqfBRATpq5Np.png) 
        - Advent of artificial intelligence
            - The origin of AI is said to be a research project/workshop in Dartmouth with many famous researchers. They decided on 6 things that needed to be in place for AI:
                - Internal models of the world
                - Searching through possible solutions
                - Planning & reasoning
                - **Symbolic representation of information **(How do we do this - should it be human understandable?) 
                - Hierarchical system organization
                - Sequential program execution
            - They then went forth and built **Shakey **(a robot that shakes when it moves). It contained cameras, vision algorithms in the black and white world. 
            - Describe the paradigm shift away from Shakey an early robot―The problem with shakey was that it implemented classical AI planning algorithms in an age where the compute was to slow to support it. As a result the machine was too slow to accomplish any truly useful tasks.
The paradigm shift was moving away from this long term planning, and making robots more **reactive**. Based around decisions on what the robot can perceive **right now**. This is called behaviour based robotics
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7MbNzFo2YsBf5os4q7XRdTcHNxW2iNDJv5s9bHqXp7wso5IxM7lw5IjjDvKMolZXFz8_WUILBz245Y-Ts-F0DFu3pOBLS6YFlh7qhAIR18SkfUXapQf-sTh9WZWns_bl.png) 
            - Behaviour based Robotics
                - Basic rules giving rise to reactive behaviours. 
                - Didn't take heavy compute.
                - Lead to swarm intelligence:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Eu_rnHkVXcAJ_iPcyNjZbPK3PS9JAYSeUzc673IgFPnDRR8He3zg-2IWjbdT3S1xJiVZms_yjC40UcCpd6Jxl46ilGMyP_ei9G6ZUJtRslQVkmO0DjRySrQ8ClgoUrqi.png)
                - Also useful for:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2BajjF2B4I_OIn1Iwv9C3L46HXiVTdos5EyjG8SulK1gcynRxjjq_cr3UOdmipsGysmtAHCu8vvtshDBq9oSdwyZOe0ev0Qd3hkHbuhyW9QtAXzn2p18-UeAAjFKwpXj.png)
    - Lecture 2 - Control Architectures
        - Perception-action loop 
            - Need to consider what is the robot and what is the world
            - What are the three main variants of robots employing the perception-action loop? ↓ 
                - Reactive without memory. Usually instantaneous reaction 
                - Reactive with memory. Acts on new information conditioned on older information
                - Deliberative. Foresight, planning, goal-orientation - models the interactions first and then takes a step.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/osgYzbV12rSuEsmBTn8E1e_GEBn5YwXdHWzRoGGZtS6jHSLOy_0sF1NBOWOub9NsjaGzadcJJMtGyio38F-sQhZtRClePOQ3q-tWiXP-fkHqUhMkGkpwk6yGcbK4rySt.png) 
            - A robot on the moon will receive information after 2.5s - so we need to be able to make predictions 2.5 seconds ahead, we don't want the robot wandering into a crater because we haven't given it any 
            - What's the differences between reactive and deliberative schemes― ↓ 
                - Reactive robots have control using **current **estimates of the world, time-invariant rules produce the action - FAST to compute. Braitenberg vehicles. Don't provide guarantees on conversion, or optimality.
                - Deliberative schemes make predictions of future stats - they then take **sequences **of actions to **optimize **some metric. A* algorithm. Need to have a model of robot and world, does provide optimality guarantees.
            - Describe open-loop vs closed-loop planners― ↓ 
                - Open-loop planners do not adjust their internal representation of the world as they go - i.e. after the plan is done, close your eyes and follow it up.
                - Closed-loop planners update their plan as it goes, if a table has wheels a Roomba will need to update it's position when it bumps into it. (**Model-predictive control**) 
        - Control for Wheeled robots
            - Five basic types of 3-wheel configurations:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/SCX7RrqIrRtdBjVAylVtM3c4SjrO9XZGmyz-SpTo9kFMmuI_aT6tt6BaAsF45GrrGqPIKiOQdKfjjcyO3fRxABBqMcM1WRd5_0pZEqzI2E0zEqF5S1In0KUZbhNV_EI-.png)
            - Omnidirectional - more difficult to design, and more expensive.
            - Swedish wheels - allow the robot to move in any given direction, no turning constraints so popular in factories.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7GkVjQICwDWrINRK2j9YSroxx-ct7yKqxKVf9LAdtes4waxzem_Wx3LofaHwgkRyOjFXaLt9Cbnur1Td8wV_EmzcL1AquuXxM6-3n9A4YgJ9VNO14WqfqKAe-cgrljP6.png)
            - Kinematics
                - Describe forward kinematics―Given the control parameters (you know how you're moving it, e.g. wheel velocities), and the time of movement $t$ - **find the pose **($x,y,\theta$) reached by the robots. 
                - Describe inverse kinematics―Given the final desired pose ($x,y,\theta$), **find the control parameters **to move the robot there at a given time $t$. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/1E6Z3lxiKCMQqohVlXO1spZmspfQ5ZWWy9Au5OsArQAg4MRhmpiRahiL8WBcGuuOcrhh2OBT77iQjs9oBvBDPMuciqembQF9JiiymzmWzlL-AlETZa4EK7houXvTriZD.png)
                - Differential equations describe robot motion, for the differential-drive model. Remember **x cannot change without y changing**.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YaK6pUMHSwF3Y3DbBdR98byEdkVC2D0VKx6dOk7c1u5DVUpCdGZOg-DAxvMYs1a1DOemS_cEO1Wz4pjm784d6xodaJwwiuEE7KEwgrrBzXNxi-hTMZ_UwnT4_aBVtiPc.png)
        - Braitenberg Vehicles
            - An imagined vehicle, gedanken experiment.
            - Make a braitenberg vehicle card―TODO 
            - Purely **reactive behaviour**: ...  
            - Motors and sensors, with motors connected between them - exhibitory of inhibitory, the more excited a sensor is the more it will drive the motor:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NGbN-l_GIi-9TsvXoHv6wx7u30yPvwyy_rFpFv4t22Oizqt35-akdPr_lArdDF_BXik0Oo9vOqdMJrHUanolr7JR2Rl7M60I5KMm7cPq-7b6czaCSY6RdZCKK8L0OmIa.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/QkkRd_rwB6HxYm8N1rLdJpRnlSxyEPQ_1OJi9sLocorhTMtF7ecS6lmWdwW_6S3xtQAHYFyQTMwHOrXMzo7STgKu_Kk4d5XtzVFMzPBOKRyQGSnzOdqn447h3h5Rx6N0.png)
Analysis through synthesis. 
            - Applied Braitenberg
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tWvgLq3hE4UttFOzYZpq4BWwRCkpAn2RAd1l-nFJvakrxHqqGCoX4BKFmVKhG7GqJSPhLwT7rN2fELHK9i2zZVrSDXS3MRY2uG2BJGJHnPYhQoPUPyytYaGMLSl1xiJu.png)
Base forward velocity, and a weight for each left and right wheels - will the sensors be inhibitory or excitatory?―Inhibitory, because we have a bias for forwards velocity. 
            - Artificial Neural network
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/pBJFX4k6olsEsS5Ah6OGvJEHQujHbXArthYgiVA5uy-LlMwwyG0e6vus6LS_62WBnWwQEc_E0oeluhcfQty8XQrJHp7z7fpGMZmD_98SbuFekHocdRrExaQhQZKzvYbX.png)
Neuros responsible for input to each motor, they take input - apply a weight and add a bias. Then we take that and apply it to tanh - a formalizable and differentiable function. 
        - Control Architectures
            - Pick up the trash competition, where robots were tasks with finding red soda cans and putting them in blue rubbish bins.
            - Finite State machines
                - Extension of the Braitenberg machines with memory. Transitions are perceptions and states are actions.
                - Example rubbish robot FSM:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bS_q2mG3jkhnszBcB2pHnCM0G1DLRmcrgL0MX-pwuMEMdk7N2WXF9DxP-eR_5I3Zqo9VrF5q_Y3paWv0FjhKDn1CuaJiF9Evo4udGQhhMGF8tbxSiYAZX0PHMjkdhc44.png)
                - Need lots more state transitions for if we drop the can, can't grab it, can't drop it etc.
            - Two paradigms of Serial & Concurrent behaviour
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/VIGkOtwGUMpZTn_xmbgprHgCfUuBxMAXKVpoFZxitVFSr_7g1eFQPJDgYh4fIyLKzr2qHn1fjzyptB49D6bmqsa2cfK1GWwnFJRGBYX_fQvCLUFZn4f1QEKN9x9-ia9C.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JJEqI7fykyUN8Is-XNkDmKidJNZRN1_Hxv_zV9ubDZNUTdpkBDfOHcAJ32SDcIAaRVffh3z29hwn7JR226GxSPbsl847Hgy6cjiUS7WwLA2mA-ea1R_zxhZ3wA5w393l.png)Many smaller brains given partial control of the different motors.
**Need **to be able to  __prioritize__  and  __combine__  actions!
                - Robot has several behaviour modules (basic behaviours), each of which is represented by an augmented FSM. Then the response t o sensor input is predominantly rule-based (discrete)
                - Coordination of behaviours: priority-based, via **inhibition **and **suppression**. 
            - Subsumption Architecture
                - Describe the subsumption architecture―Inputs and outputs go to and come from the behavioural module - these are inhibited and suppressed, the suppressor will **replace the output with a different signal. **The inhibitor simply stops the input.![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/uXCTIuvi9KRaRcp59_CPh3iVze0QFqr8t6wRJuB4qwYvFtupAM30R93sFtx-38qjKkLPO3SR6pCZkt5PVwi0W5zu_gtjqSxrUZHrKvdtzO1Bh0W5-xOZxUbAgcojLarI.png) 
You then stack multiple layers, where higher levels **subsume lower levels when they with to ** __take control__ **. **Each layer runs independently and concurrently:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/T2tKHlCVAB0I5mTRcFAbByCWbCvzZmygWOoK9DKs_Qu9iXQjpuunX3Wy0xN3_oWmJTicPohkmF9Uka9LrE5khX9gPR_4tOzB6tpxDiM2IHrTxg9OAiFAfw6huF9c6Gpj.png)
                - Example Robot:
                    - Layer 0: Make sure the robot doesn't come into contact with other things
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zkhntYURyW2kyBCO367flhzegfbZ2wrsczjub5_KhgsO13g5NMX-e1ItTykM3TcA0WnFGIWPl8sy4RnY50WbUyZI9PlJzqdZcAh-iPnNXh0HvHn39vcnTuTeWaBVO58h.png)

                    - Layer 1: Ensure the robot can wander and explore without colliding - we can **subsume **the runaway force to allow for **avoiding **objects.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yS21fmFjbcys77UUTrO1GQeGCDGUavdpRdPOPwJuizmxH2gLw1HFbPpEZOszOHXF9CFx2F1-glu8VSPIFftR9TRtyr25CEL0sRqrO3fIjk9nztzMztIQXo4-Yj96b6wR.png) 
                - Pick up trash in the Subsumption architecture:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tddt1aR9s2X4Cq67LnAAPvyBTqR19FTgStOXkSYkyAmYPNB0UJGhjex15XUYtNXp1N3l5iLbpCQniizPRgGLiA0tZ2KlmICFBtN85IyAavNtblc0b396CqhcIjaIt6vJ.png)
Explain the inhibitors and supressors here: ↓ 
                    - TODO
            - Sense-Plan-Act
                - For pick up trash - we sense and construct a model of the world. Then invoke the planner, then execute those actions.
                - We note that the world would need to be static, complete and error-free. Furthermore, the sequence of actions should be optimal. Finally, the motion plans in the execution should be optimal. 
                - make flashcard on sense-plan-act―TODO 
            - End-to-End learning
                - We form a sensor-model - for an infrared sensor, the higher the voltage the closer the object **and this relationship needs to be calibrated**. Rather than calibrating by hand, we could learn that relationship using machine-learning. We can learn the world from our sensors.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/QNIATEwF5bcAHu5cv80BCHquGmBHsxB1D5_UK5AqIz8tqbN5h8L_l-CWLuKCwY7e8v4V69w6yRObn0URom0EydtYJ7r73S9BX8EYPEbx1uipj9afP357t1eJiFRYh-dM.png)
                - Similarly, it may be more efficient to learn a motion model than to do it by hand - if we want to know how to move a quadcopter, we cannot know the exact effects of wind. 
Similarly, search algorithms can be altered by learnt heuristics
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/88g3A4_YSrMdCM_w3JrAzzaXh-Vwf150VvXtVQafkAXDrKOlrvpePZTucfMPJnR--kmwI7avIEs3LHWTPoRXjE-48AaXQZ6kVbwnqB3p97cJ_ALAg_PjLbRceMnyIB_F.png)
                - Finally, actuator models can be learned:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/EELxn6Zxooe17NTnIkzM8rerh_IT1KCM-jUlyN2qWRQxttgyaS7yC4nY9iVadWQ1GFFSf0iSxeO1odZT5N54hLBLvRsC2vddSZPXAUFJMRqnAV0FPnJ9GS505mHQHvWW.png)
                - **But, **the fully end-to-end system is one with the sensor input going to a neural net and the output goes straight to the actuators:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/j4GEBPMcNpiOgf2Tn57u5NK5zODMHUwaCVHUXolMWwprd-tG73Hb0H6qcQSK0TlHYUGpwlG6ArqyuQHLPVpixMHZvRrpKDO46yEDF-sLkKjyi5WzwB_-R-4flLv_vqAU.png) 
        - Current trends in control architectures
            - Principled architectures being replaced by end-to-end mechanisms
            - Challenges:
                - Where does the training data come from?
                - How to generalize to arbitrary environments?
                - How to transfer from simulation to reality? Can we model friction correctly, if I train in situations which differ from reality I'll learn bad/wrong habits.
Red gripper in simulation, blue in reality and it won't work.
        - Considerations for control architectures
            - What is the application?  
            - Need for parallel behaviors? 
            - Is the environment very dynamic? 
            - Robustness to failure and large uncertainties  
            - Computational complexity 
            - Need for re-planning? 
                - How often? 
                - On-board computational constraints? • 
            - Fast + reactive, versus slow + deliberative 
            - Predictability of robot behaviour (proofs and guarantees)
                - Can we guarantee that robot will reach goal destination? ‣ Can we prove that the robot will never collide with a human  
        - Decision Making agents
            - Environment receives agent actions, and emits the next observation and reward. 
We then want to **maximise **the reward. 
    - Lecture 3  - Introduction to Kinematics
        - Robot motions
            - Motor controllers connect everything together.
            - Different purposes for different robots - wheeled, legged vs manipulation vs heating or sound emission.
            - How many control inputs are there for a RC car driver?―2, steer and accelerate (ignore each wheel steering) 
            - Degrees of Freedom
                - Most actuators control a single **degree of freedom** - a motor shaft controls one rotational DOF< a sliding part on a plotter controls one translational DOF―todo make flashcard 
                - How many degrees of freedom does this robot have? 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YtA3Gww1aAKp-7ccl9Bpi7xGy45i0RNoc2WJZAEVJfw7Q9_zyANtVVN-DVv1F25IJNffeCITpwwXCSd9OMAgLN9HJgRTHbpQsp78t4KMxuuPE2k59WvgCcZE5715UoAD.png)―$x, y, \theta$ so 3 degrees of freedom.
            - Holonomic Motion
                - Degree of mobility―Number of DOF that can be **directly accessed **by the actuators. DOM = 2. E.g. this robot cannot move in the y direction.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9xe29Ue-GCOBTKliIQvqI7usY03cmhfTFuePxjMwBP2X-jUO3Nkm_YDSCkdjpkGkWEXyINJp_BDfUBKx-vF_e1TmGDZCX2JQ8l6VWfGk6tVA9UgVHpWlb3QB_PxukvU5.png)
                - What is a holonomic robot?―A robot where the number of DOF is equal to the robot's DOM. 
                - Describe the main problem with non-holonomic motion―The robot can activate the motors with the same power, but at different times and end in a different position - meaning the history impacts the movement. 
                - An example of a holonomic robot:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/DvolksPW4U8inlOksuI3fgbAwyagFFy6_LmCWzRHyakyY0MxzFeGtOOa-0ZTmO5mgA3DK8LVYk9R-I9agdWOmuyAi50V-yqBhR-ATWHNCuqeWnpuJ98AU61qQHSFQ0c4.png) 
            - Distance, Velocity, Time
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_698dKJRcC6jvaKkktOB0pr10ZtCos6x_kW3uNGqBt7ESqA_mghqF2aqAuzGaDk2uBQJfPyd0S66s5tYBu-RSdGOSymh2vbbgIPT2ywsinnGPCKckWL00AYxXCqWmhLZ.png) 
            - Forward Kinematics
                - Differential equations describe robot motion
                - Give equations for the x, y and theta for ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/GxbsSWk1Fdpe9GhpCbWQab1MMaTgklmBtVseh2b3CW1xLRVYKJhK62TOal0tGEcXDQx9rITxjiH9LSZCEgfsU6LKctj1un9Xo1kT9A-BD9QyBvv3OxbBRUVIDTMkOaUE.png)―![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/caNPb_mRMk92UMUJDFtF5HUeDRkWiSKT-R6dR8tQNElEtLkGrQeYgcoatdC4BbNu2mpc0HOWGtAVb6oq7JpeCH2zXh9BelVZATkoR442TeiOCz3zUTubEIVE0K5yW4cu.png) 
                - For diffferential-drive, we have left wheel speed **and **right wheel speed. Describe the equation for total velocity and rotational velocity
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5UvHNWTiUaA73YZQhupoajrHqgNVzlziS5HYFY4ofzWdpIBJ65vMjNu5MkpDO5Je_WbzrVVvzUNEjgF1gBXqORvxHHRNt9DgR9O-qArhH6UqykB7oWooJV1OPHuQBUaP.png)―The total velocity is thus the average of their rotational velocities times their radius:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9mDxpCS68JpLbpXDyLiCwpSfBO6oD4LeGFYBrh5tQH7srgNwgQqLDTdy-QNBsjESDpYP8evaVKPzQbvTDeAHnZUm-pyra6xL5DEKvS3t7GQ1Xur3c3aMb_HBQ5won4i9.png) 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9mDxpCS68JpLbpXDyLiCwpSfBO6oD4LeGFYBrh5tQH7srgNwgQqLDTdy-QNBsjESDpYP8evaVKPzQbvTDeAHnZUm-pyra6xL5DEKvS3t7GQ1Xur3c3aMb_HBQ5won4i9.png)
                - Moving from local to global coordinates using a rotation matrix
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/EA43mkIj4dN_5kt0cS0G4JatNNYoCowj7Hp6RFLMpriCJiltXr5TpxHYjZBkAvFN3JpLSsjbRfqDli7XRptzO5kCnATGWzKLPWTvTvfA9zz5M2-Lg5kOco8L5-nkaT0M.png) 
                - A second-order model
                    - More is needed for a quadcopter, because the rotation of the wings no longer directly corresponds with the vertical velocity.
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/i-MRBJbGGPWJMmnl-tT3JrGGoj-jjMwFKExk2gtJTego9xWj3GaZ5TX99cYQBmTJGPlIgnhTTpGUutQeNnO7S0ony7_cM6VGMuruP5sZSW9hJjGM138XY6VVTeIODydd.png) 
            - Inverse kinematics
                - We invert the previous equations to find control inputs - this is done under the constraints that $\dot{x} \sin \theta = \dot{y}\cos\theta$ 
                - If our robot was holonomic - what equation could we use for inverse kinematics?―![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/XIuFH5Olkj_jBwyCliemrTRLSK4pEbRDFo5sj9OqTYnwQU-pkvEDCM19bR7EvQktH5KHiKRNYsylZrE_Vw_fQqDGksVFJDLSO5Fk9GFNVHixlVug8cx7MiNH6UR03wSJ.png) 
Just adjusting each dimension independently over time.
                - Trajectory Generation
                    - To satisfy our constrains, we need a smooth trajectory. For example Cubic Bezier curves ensuring the robot waypoints lie on a feasible trajectory:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ldx5jh-7-lcEZo1XAF8t-kgoTagU235vXLE00GqmvxjffcEols0rcnkjV5wND1kGsPwCNf_cLlEA4eibC4RX8ALVGZpSi_boLOhggPGFjk5cXGGwuRI6qGmhC5PEDfyN.png)
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3SYpxUB-oYMqBhOmyg7ZANyh-NJc1lyQ9kIsmMuF45W6WB0sjFU6MmcIVjP9Q7YhxYCMnYu4uu94jDVNmi29q2OR8OfJaPpMAjHgXJgxp-_X-TJyM1L3Yx6mvXZKVhtg.png) 
                - Feedback Linearization
                    - Imagine attaching a robot to a rod that can move holonomically, then view the effects as you move the rod directly to the desired point.―TODO go over these slides wtf is this 
                - Describe open vs closed loop trajectory tracking―Open-loop means the robot blindly follows the path - closed-loop means the robot stops and checks out the environment as it goes. 
                - Closed-loop is beneficial because― ↓ 
                    - Noisy sensors could cause wrong estimation of position
                    - Noisy actuation could mean we don't move how we think we move
                    - Unforeseen events, dynamic objects need to be handled
            - A simple closed loop controller 
                - The robot measures the error and corrects, using an on-off / bang-bang controller. If error is in one direction, apply one motor, otherwise apply the other one.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sxGBncesz2w_boWQZFO-bP9VCrjLc2LsIoBAtuC4_cBzlbh-KhTur_-3I989hUkHw26v5gq9LkxacERwYHnhqOWXn7xhzE3qumP4GfDUdOlcEz1d9w9lFoTB00PiFi2x.png) ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/xzzA7IoqLWi2IE00eX9SdwRXQqqlCsuUl7OPTWuw5iGnPYT48oBFjs4m9V5WodVetC58drHQzSlEuCO00i7a39M0TbmEQttVpmNgS6OXLHBTChOqgNr9yt58Hb-ClvCL.png)
This results in a zig-zag behaviour. Note that error is a Euclidean distance - i.e. a single number
            - Proportional control
                - The robot adjusts control as a function of error - the lower the error the lower the motor output. Note that you do this continually!! Meaning that the robot will start adjusting error immediately -
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Cm5m6yVA2mEfhadp9HY_xQ_xFUdNhrqn_dX8PHuhd-TfM3x12Bh7XAj6xPWSvxVlOJZbj19p35Jnt8A2gdl6ovN22yCPr7uW33Z15KvRhtEGwYxKBhfNUGGekwg63Di3.png) ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ABPB0SkcQYF8k47DECUPGbzfLbEDjVD90zOiCdeAu-umu_XRwTOStscRCyopLh551FAGCwzbD022S8hc8FWsvBku7FgTwhTpJeDQmUEixRVBi6dSef4CijPOVsMKeTFj.png) 
                - The behaviour can mirrored exponential: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JcgqZHZxMtwk-Ardapy8_LMEsdX74xGSjuM9FkysoTB8TfkPA1kWIM35IrrsM5-iMaelPcD67ClsQay_1lJcakQ29tcSy0_FrtJE3KtMlQKED5Z2opxZt93rEHsOPhAG.png)
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Q_Ss89p_23iZnZ_OYSNxU_Znri-87fQ8jz45TX40hI0AfG5oVOwzcDrHe9g-35Dyv_wgEeAa3X-RA1pkVKRyseVsXy9oqdlwJZwJm_Gi_rbvPZ01x_OG5SJ9aB8sStIS.png)

            - Kinematics of Robot Manipulators
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/iJhu_KLRu5GNKHN8GftMNd4pQTja728q-2c-98E3ombmhTZcj2VK8UN_MeTQkJKOaP3kygwLUZnqEDnYx67hZO-Xte1zfnSjV3Zxp2IuhTMDBaM9pLsATFP7kYqsec71.png) 
                - Two-Link Arm (Holonomic)
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/F656qz1dTreun_GMnNxYGjYUDBEh0rFswJVAdcJaYVCNlamkzug_QoJHMvsEu0GoSpL18iLW6aztqI37BC3G2lpISBIj207GIRnZFjVCpyz3-lbcc9oPrGc4CBJEqkxC.png) 
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7sp9wYslLi4mGvO7-SGGNj2S8Z58kAYh3VYJYLO0zqe9ONnFIEL-lehJutshsjBzn-xbYGAmfwgt-SO9f3BO15XaKuSW8rZcCAroXdy_brtqR7YNfcpQVeBwUeqoePJT.png) 
                    - We can generalize the forward kinematics with the Jacobian Matrix What is the jacobian matrix?―The relationship between one coordinate system and another: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_3EGYEgckMqFYU0CnL6kpPx42wYmEr-6P9s474cjfZOZXohWITBDQqPzgJD-3cXwn5qvX-IYDTGr6PClAWuIk6d6rTB7-KbivIxjBS8mPzUbE9g5rBs41XEwKvWZvg9X.png) 
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/p7CtQbf8fEJNj2cNcJEMnDvZUoqWEo_2zrVuELyl2XbyT-raFwJ4PqMdWQUk82V94aJIjBMVK9uN-uSYIZLCaD0IdrwhKLlxgquprLqBQL7dQdUWv13tToZh-tkQCybY.png)―TODO he said to try out figuring out the Jacobian here 
            - What is this diagram showing?![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/x6XyhcjWhCNoGb7G2GSiLVEYbGJjiZx1Tm1QBeYr00mCAvDcUJbNeCY6b0ngXYIQfWrLAWtnmbyYezy2KAkgwhOGJndGp0JIrSBBjn7Ntgurqwf8W9HRRUgGbVoftFHa.png)―Robots can maintain balance if their center of balance stays within the support polygon of the legs! 
            - 
        - 
    - 
    - Lecture 5 - 
        - 
        - 
        - Sensors have errors - we can minimize via calibration, take a measurement of known ground truth and fit a model for how the sensor measurements relate to the distance
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/cC1qVR4a7CYocH_npdXvIzrBHaZW8AQrajaLRfLBqwM1YQL561LbsMlj6HCzdASw-VgQ3iBNZ3pGvNG73i83dBx3Fs9F--nK94Eq6NsHq15U8cPGbZp5mG2OFjSYL1YT.png) 
        - Central limit theorem means gaussian!
        - LIDAR - mirror that spins with a laser, tells you how far away things are. 
        - We want to estimate this the probability $p(z_t | x_t)$  where z is our sensor reading and x is the ground truth - however LIDAR can have many error sources.
            - Inherent noise
            - Something unexpected in the way
            - Sensor fails to get a reading
            - Random unexplainable results
        - Start with a gaussian for the **noise**.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/i4-Pfe8Tb9pkxsdQAN1nU6WkoewbufwK9OlVdWmpF80_vme2vJr8sHwZelWuW0MFMNjUFNM3NjzVDk9DbFSzqWkyVqBXoJcFGHyPFyOsHGPg6QXhr3OcLgTKMQOFB0VH.png) 
        - **Unexpected Objects **are measured using an exponential distribution - more likely to be closer than further. Because objects further away will appear smaller - so further away more likely. (Stops after the object stops)
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/RaljKzi5scb7P-buSftp0Yy_04zb7hOJbQXrDZKwIyqsNQ3sCAqIiD6zEw3__GUjVr9-dvlxd4eW1zYoVGSlQgJd4uQJwXS6JyrK0bR3aNsckSaTX42eIeWeiBZ9I_Wg.png) 
        - 
        - False **max range detections** are added as uniform:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/r5VsUEXk_fJc2raUg5bLfJlCqPlT-qyQIrPdpJYwsCoxq-9Nhun04ZC3RmSiqNeoyiVwPujyrySZwELPQgMI9d_emyHP9vgBAbgKqfLmiw-qY2HrOoZkgs1XNFb_dV1W.png)
        - **Random failures **are added as uniform:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yil2wonjUZp52GBaUIQ75s6D-3KpE20Zwr1Qf0Ao83hq3smLzXbvDWzuHrOJ8ZCkk2E5SxDMzemQcUlFJejiqKQaCF55P8KZAOUHzFZXzcWtZULOklP4CPWgaWxU467Y.png) 
        - The **Result **is this:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bIqNiuUptkmVXbOtW-zSn6WO0prs5Tim44lzu0bMOpvpQhu-k_hRNgCKMiKc_mXwRRoSsAlGLwBaf4L49Q2PHeJYazNQxKHrUudtMkRYiZCSkGAE_Z8_FM0nF5FRCif8.png) 
We then need to fir this to the data - we'd want to find the variance of the Gaussian and the exponential decay rate (and also maybe the size of objects).
        - Probabilistic Robotics
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6qxM5gxydnSlqq7YFIVF_sbB3ArfBVcL6cKvrQqqWh2hTdPCilGJh-gJASYmY4Wwv3Bj7F7JUMaLeJv69DuZlmk_87241Ms7fh42RHZkd_YZKSrj0F4eF3Frk8qNpVkE.png) 
            - We change to a markov model as we cant solve this:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/1s1Ex0nz3LcvyCpiibGv8yst7CdUobQXp39YLkvpSZcaNcmWSsVPvVBeH9SKMcUjWvioM00DTcQFJwVp-v9GVZsLWzMH3Hsa7kr1LFSuouhAZuKR_S_NRD7zeuTZkey8.png)
            - $z_T$ = any controls we've made 
            - $u_t$ = any measurements we've taken since then 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JWC6Byzv0PPVcuHmKWG67LOswhrrOqBOLrQryG40mq0nt19h-RtLlteQBa6UVzBjVZ6B_hFD3H6Sq3VlRvXpcXFM3nGUamVrFFZpzHqXApVd-8qnkf4xj4YPUv7IZTWd.png) 
            - Prediction Step:
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Xwi4QhGb-er-5_7kI1o1ZeTRMvmPR2NUibbd4PHii0UsdMaF_SVRek7xxNBl48mOs4eOsoMR6O21e4HlfHaH0gYF1LJRHpOabQhRQvquBR0Orr00lyuJH4JAvhmkn2Nf.png) 
This equation means, the probability you're at a given place - is the probability you're at that place given where you were last and the measurements you've taken - multiplied by how certain you were of the last move - integrated over all the possible places you could have been!
            - 
            - Odometry sensor
                - ?? TODO
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/u4dU2rYyuwgP_Rdf1cf1lihd1HQMeZlgmvkqfnS2kvUwxy2x_0EK6bB9AXAvHZ2JGyWUtKY387NR_47UUySSLthzkNFXG-eXzF9Ba7KFkhVMN3VOuHJSl7cs_-jQ-8hY.png) 
            - We assume you moved linearly
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/D82L54xui9y_cjd3tgEt9q_wgeqeVXSVlVzYC2RBbiQ_Pza7TEHLb3dfkHSMG7tcVdJvv4G3ll8t8V9Z-urWyBVJOJvgK9C6Q8jH8xW2vJ4bCCW04NR6QFwOnrnOayO6.png) 
                - We break it down into turning, moving in a straight line and then turning again!
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/UBVyn3654f5k12fs7QTHYgb_Ffz7nIoflvJHoaC_v9qvP8RAoDLz0jh2ybAbCB-Vy1B7GNWXcTAf66TXgY-SjsSro8ORin_7h9wFEtGmZA9ENa0fE1aJEVENqD0K-6kM.png)
This is using the x y yaw from the odometer reading. 
                - NOTE: $u_t$ = ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qiljog_oCssHE66j2tWa8-bAcSlTTypBBXQlU4tEutMaJFursJC3t7yl8OLTKtVt_HJ7ctVOBP7zEanSNcIWO6I8aGm6chYHGona3of-bkwAno872twKBwnfL0OEClBP.png)  (control input)
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/T3Liv9s4RU5Qv-BX4Xi2UHumXvO6rXu0XzaAoNrnXCGoSP1kZ-z-vzm8olZz8SDGs5io-tMleyPiWdw384v_mXjIGDtFlDA5eZl9cBO0EYTGi2yHx0w7z1gH06gE4F1n.png) 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gWqEy38-PwXrsCccEb6nKABLtVSs7Qfn7mVJ6EkmKpNriZOmIDXNdAg7Q7hPZoWVEtLdsrDiZPYV-nsh880KXhnWC9umKbtVb6prvB_2CtScBmIQkOdeD7pZv_ceJUls.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gTqyLlMbLNNv2kmpy2siSBZH6u-OeAUjirTeioYGmtclWPw7WRkBbUbz-49FuUu-XF8NFnBcacp5qumIh6mdhB9HxyjUYVNL-EXsl5zx1nIjJJTiOW3DyKYc3wvFLvH5.png)
Then we work out the components if we really did go from $x_{t-1}$ to $x_t$ 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/82oXcfxjUMwvkREIZw08zZEVFAsxCJbYVl2Ul3iMdN87uJUkqSuQ4DjdVWrTPZbSdBiJVG4x-QXES8sNL9ZEc9XI65WJKlneAts6CtzVliPvYUUUD-vEsrA3Gny2WILL.png) 
                - Assume independence and return final prob:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/dGftqaHU-Gn6WEcOLhyK1YXn-ht1XPFdEIYM5xTxwfT2XRBCkVoR23MT_gSaqSj062fiDt8EtnPvcK_eBwNVmAvkxJhbkXmDgSBPu4w7YSwC4onl7-Rm2EZ3K5wZNx3W.png)
            - 
            - Bayes Filter: Correction
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/WxCzbeGsSQdaAlTGEXJr0sCbnwVexAslIwkOJYkTlaRlMq-h7TSNSodUpAolTqO_L0SAyEtfAexImL5dnwXB6b-40i-SFE-fOGZ8x__UGAaKy4ae26sODRTMEersHTYm.png) 
The measurement given the state multiplied by the belief we're in that state! Eta is just a normalisation constant
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/PFYFXyvv82WDDqOWOanyVe01FwCTqJDCQFWQPowp2PfHzC4A09lnSwQhxgcyWtYNDNWpVp5d1_ehb3J0IE0nK9KzHog3dgecHB8keQnkm3tnsO2bGZN--Bn2Uj0kHti3.png) 
                - But we used our sensors in the predict step!
            - 
            - Kalman Filter
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/TnZeewGj8OarwFP82zNzL9VEvFCujs5JYfOyUPmWirDbMRMIctENIPxfnxAWhSxt1roWs6F7NMKtaew2XGIdW3Wr1jvFQs5vXysSdwEeZPh7MhWuRU6wLA9DSfjaqQv3.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/nhusfjg2oCo5Vu6xLKRuxbG_n-Xdn_BrCxmPuPC5eWPc6h9SuBCHZfRJ2Hm4-cTfKlfaIju0oOSGftIHq3kQjvjbd6UOtfJWX5psvuBHPHOXqXHE26bOrnok7jA9dvqt.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FYQH0fx5xReYPxl4laJKDoR2rdQ-eMpO2x1KVDJyG_6mLHX4TMUuOWznF04Lsn0owTegYi9cjgMGTYW0MUiBTTSB2va329BlFh_TT4zPf7UoKfhEBzDvG7QCrqyO6Pm2.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/LG0VnuN50IQ11lo5hjr5i1ltZLRfxbVJg7NvU-6k_Tndl2btMeMuJAxgmEQ3E5xpf7EW9rKhARbrTLuYFNtMIX_GFJwEdkEFktazjIy6zZezmqpDelf_xSeH0s5uhB0o.png) 
                - Key! We need to add in noise, meaning we add gaussians - we add noise to the gaussian. The more I walk with my eyes closed, the less certain where I am.
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/p56z3WcU3tVT6MmV7wQtcuNVVMj3czx1PrZaskOyQnEgGxNQlOVxCncAOveqiFxlClzZGfgbcs0Q96d7_MY3fwN59BPk0MZNslFoF764tQlUEk4DExVu1J20i_EXyuON.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Xf8ZqN3IOcU_lzqb47e2RiJyBVujntoS7rEJzimTX_U00UCDO7hMNO02Cnhqzm2GN_F9Fu5YoBABjy6tjXustpXrYLtkyV4lLIcIyu0vRWJhNLkspgzPT81WpZS4PBzf.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ryZDEhqyIjwNJb_uAe2X-cCnKK7m21OidfZNgwurh0mOtC_xMiAOXCr-wNoHyIOwkeH9TQjhQJMoJ8m6APKzJkoFYkSV_hhNjUpOV4wyKmcczQM4k3zB2sS-sLRmywRk.png)
Multiply your prior and your measurement and you get another gaussian! We end the cycle and we're ready to go round again! 
                - The real world is non linear! So we would start with a gaussian and end with something else:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gGWDeOJlih15QoYmW9qkVdxt5Qsx3e49p7Z5TC2gEOnRJW_nkwBXhB2qWaIxhJiS9NEMyUQ0IA28FjO0GFOcWCBNYTqgcK6nqpvSbVCYADCm0C9XYdH_R_tEIcL0ZEeQ.png)
So we take a linear best fit:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/raI1qGbRv5qNyE1ArRkmTeOU-BeiwFRXx6iS22H_z67Azx4GLGe5YxvxgrOfBaUcDEsKOSb8eb-idQ1LJvcsj3PpWzhzP4bQ0BCRd2JTnX1o9FjSUKVmX3l6_EhEMkMS.png)

                - We move from gaussians to histograms:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Sgwa5r5gfPooRcS7OnX_xAmeRVcIZoRpbQrU3oyl3-EwmbRjF9gHP8ZX_QQUr0LcSIUjwyeqdOP-tGLfK0D4m4blhGAeKbg0hGODh96P0i59ZkBV_Gg-BxpkoXxBbKbA.png)
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mQnv_K_BkQ5rMwxKw8L1P1C57FgYIBk0onnuft-CqgKgcMryjhot71dBzhGBG_IHOrOiSlfMM5VYcxN5GMMo-8zHB72R58HUiHxklFkauyAQIfq_c9-ifBW49E0_pzsj.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CmrZc1PBr_tB5dns6J-sz1hpcpq3s4s0rTGVYjWWoa7Jjvzmvbz5mdyHdhxCV4GnMj5JzuR_9V5yIDc39UCIcGYgv_I2bYRcqRRDMCOvN_GKGXu42ljpleJhHWT-7Cld.png)
Multiply each bar by each bar and normalise at the end. But is very computationally expensive
            - Particle Filters
                - Single hypothesis of current system state! Each particle has a weight, the probability that the hypothesis is correct.
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/LQj1EQ8DXynmUBykztECa62MwzOAS4hpvSqZXBUvjpdGGrAah80Bme7zdkE9fF1EC2i3pBR6eu0GQy9yFXfPQ4-7bMcoUeBcXcsP_15HeoDfLhu9MAv_CHHLDzMNCEBP.png) 
                - We move them all forward depending on our motion model
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sQ4P-ETTl0f92jsO2g8u6wu00fhWs26Ofa-I7yyUqVWhjStv6UWrLkzsTk_GLgJtwAyKfjEAnvjBDaVa6ArxgfQUJs1SI8hp3cs3xwvXYTfbR8Tk6PtlUIM_falhkL4o.png) 
Note we add noise to each value! They start to disperse
                - 
                - 
                - 
                - We then go through and apply our sensor model to estimate the probability $p(z_t | x_t$) for each particle. We need this for bayes to get prob of $x_t$! Where z is our sensor reading.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/DBKWC2Lxu2bbNEMFMQHhCfWKgrbhGCzeQt8g0gtuZuBzS0NbDf929Z6-S1QnP655uKp4xN_xZB1DdVfQj82eCm12KHpJSMqTtlXBDriSBlKqS_KICLYCAMPcj5p0t8Q-.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mEYaX_qpI66m6SkJsF-cWDMtq9BytYp5rkXcQHHNR1zg2PfaYIJkKNS-R0TgfRKb_g2NPXGtlwDjJGPVqIktjkDSN-pmWShEzTq4Fpd0HdENgsahGeaac2OkIthe8zAT.png) 
                - Also if our particle is inside a wall, the probability is zero and we need to kill it.
                - We want something like:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yDIcEcjHFSpaTu-dCa31ptNpNwhFt4cE-senY1HN-jIamxVVWPBl2QxeR0ceVCZlMTupay0zcBA52X8bD5BIFTufMBINzi-p4pibqMoAtEuI4nGcKP9JRjKbtnAIlJ51.png)
                - Take our particles and draw out a histogram:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7Z-mZlcZKK07VbOIIFhFu0nQC63IxeGXX_drIl_CA2H5Fge0Lu7DJC3y4TBHe1khV6ong3dew85iliP24hXY7MuQdX4gK4n7SOhdbLBJjuiLDUpx3fN8Iug83BCPVkFt.png) 
                - Then resample based on random uniform guesses between one and zero from this histogram:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/A1Ej6MOj1qP98BRWBwZ-k5IKD73Bp--oyA5CObG9q7UhgV3onGPjzsb4dV0M1pip1wzCPdiNWR-kVZHdaUR74hlbnQa-UVVMlatVY2dlr5xtMRh0-8-9h8anupCSW2-_.png)
Then we clone those ones - we're going to randomly change those anyways. Then give them all uniform probs:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_ENGoba7P9CzP-b88NIigGhldtOAa8rxSQWuzA38vMWrbgGUGgiRItZoGmOmkVaVpstyGc1O0jP8OxemllAKfv6WbR7syHaJONrylLezSXHlO3XQtQjBWIWe9YMA-0_f.png) 
                - 
                - Easy to break by "kidnapping" the robot - grab it and move it somewhere else.
                - Poor sensor/motion modeling
                - Underestimated errors screw you - you want to overestimate the error.
    - Lecture 6
        - Navigation and Path planning
            - Focussing on Motion control and navigation
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/S2_v-CYLk3pW0m5NoxFmFpcKTdTQ3JIPJWBMKQcFzCi61HdW5tm4-dBVPOaEqTX6rrrnwFMMmWRBM_4WJyr3ba06KGsk6HuyGSgB5wz4mHLb5PvO0lqzAeh6eyJd1sIK.png) 
            - Motion Planning
                - Planning is more than simply coming 
                - Need to understand how to execute the motion controls while respecting the robots kinematics **and **the environment - this is a difficult problem. 
                - Search-based algorithms for planning problems can be used.
            - Configuration Space
                - The world has two entities **robots and obstacles**. Considered subsets of the world:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jpbrouCxmi3mIGFGRvakx0mLyLDsKFBmVn2Lm1WjsNVhPADyJdwN0mhBiEeleOfEwJ7ygd6WzpMTo-LFu_2nzDXCU_eaIkgJoKevyml3UkbpoCjK-Gw3-fkgzw1UJkNI.png) 
                - The space for motion planning is **the set of possible transformations that could be applied to the robot **(considered as a rigid body). 
                - The configuration space C ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/c3lBEDysLhtMGauHi2Hkq4GTK74v6_3ZJqUx-X1oy99JDKuMQmDcnZlFSvAwIrEnev-BAQ3dsfr5q1p8sOzFma4z4j6OiqyzaMDWD7DBH1qP2mpqfdK6KNoYAzWjKAaK.png) - allows us to solve the problem for different geography and kinematics.
                - The robot is mapped to a **single point **in C-Space 
                - We can then use anything that deals with points in high-dimensional space to help us solve this problem. I.e. Vector of generalized joint coordinates.
                - A configuration **q **is expressed as a vector of the degrees of Freedom of the robot, store everything that's important. e.g. $x,y,\theta$ for a differential drive robot.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tGF52mFWDHak2mKpjyyJu47iOHPeiZxmAGVb1MVOVGPMoYyiC-BaCHIVRMRfA1GnhsYxBDgWFMc9ylSqQWVD75uzMlqzVPk546uoc1A8hLvbVwAMHFXz_mD2ySNkLdsH.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Dtlcl0NqSY7Wjr2whzk-JoqUbxiNcFvrkuO_EXu1ThRQ-UvgUA6TcJQx7o81oYUWc_i4GoEx315IooTucbH-38W8PsKC_pWK0yzB3o58tyhrc-XH8VzaBf_OIs_k6lQ2.png)
A(q) are the points occupied by the robot. 
                - The world has an obstacle region - how do we represent an obstacle region in the configuration space? 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/c7PPLsEeNfgKi2ByUlZR_ks2WRj3eXAKHjLUWlE5oa--mBT-UizKhwjyKqjI9odkBAHjkYKQXHqdCDlQzmbHo1BKZ1gtyJHTPw54A_vXIRSZTHU7QHpI_w91pJwjPxTN.png)
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/U6knR4MwbjG3aHASyvgOA0d9TnscAv0Y30oCEPChN6Vgq2DWYVeLBkgooO-0QQnhRHzzFQfkuhvyS40y8e47yZGXTUQ4lfDZ5OGxHH1jX5FL2tpZ5hGBVF3JJkmA-qvP.png)
We move the robot around the space, and find points where the robot does not collide with any obstacles.  Results in almost dilated objects, within which the robot will collide with the object.
                - Minkowski Sum
                    - Formed by taking each vector in a and adding them to each vector in B:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/QMkPmWMHaFYk--74qdrgbhZEeK-xRKfrLRm690kU0lzwRFqWkBwP4fcnyF7Oj-oi4ZTcTWVVOnHcv45UACz2MsDYndUepltrK09vCeta41uULKBedkFUgjxIjA7bH5Jk.png)
Results in this dilation of points the robot **cannot **inhabit! 
                    - Using negative A gives the other part.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/laiNUVDJfDt8JKWkNAoNJQBlAVpVa7OwcjKLDG2yiIrh0Gft2elHef-E1O52PD7GxRC_LhtO9JkpuHd6wQ9e3Y5_2vdG0j85J9t2v3bTLCXWA80vBKxisvFGtqmRnhxG.png) 
            - The Path Planning Problem
                - Given a query with an initial configuration and a desired goal configuration:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/pn5nZyXGNMqTiVYl3uznWV0Hb3L2h1639wL99kUI2qRtnzalNfD3nds8g4XiHzIxxVzI6ihu185p8om8_0SB9gMKcvGHbG362RjrYbvURJUMuZdMc59UGZKCpHKRFRXq.png)
We want to compute a path that's parameterised with respect to time and means we reach the final configuration at the end of time:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/nR_CsPYvvZpnSBy9yzvIUnFyNLglpQQu-Eu1O9hQMMXbpBTUY2JYRY08PKToVsgCKT1qTVTQESAezp4QqmvjAqsedfhhrhFt2zYlvt-MxDW1FjWRZXR3TPyFO-Hz3jpH.png)
                - Guarantees
                    - Complete: If a solution exists, it finds one or it returns failure.
                    - Semi-Complete: If a solution exists, it finds one; otherwise it might run forever
                    - Resolution-complete: If a solution exists, it finds one; otherwise it terminates and tells you no solution within a specified resolution exists.
                    - Probabilistically complete: If a solution exists, the probability that it will be found tends to 1 as the number of iterations tends to $\infin$. 
                - Combinatorial Methods
                    - Requires discretized spaces! Squares in the configuration space.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/llU7hIAYrw8_9lc1QfeQBIt7CDd5xQ64Bh7hY0auTqqlN_lOhBK3uNtQgo84GLJvSU94bZ9jXF1JddbBx0hFDjcNaJzHT0PErUBm7wcD35gWT3wUXsHfqtwN-00kvq-h.png)
                    1. Compute the C-Space
                    2. Generate a roadmap (graph) in Cfree
Use celldecomposition methods to discretize the state space.
                    3. Compute the **minimum-cost path **from initial to goal configuration. (Need a cost function).
                    4. Results in a path that travels a distance from time 0 to time 1.
                - A*
                    - Remember, admissible heuristics **underestimate **the true cost. 
                    - Memory inefficient and grows exponentially with the exponential growth of the dimensionality of the state space.
                - Complexity of Path Planning
                    - General motion-planning is PSPACE-hard - uses a polynomial amount of memory. The C-spaces are usually high dimensionality, meaning it's very very hard.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/H47MKa2DADeno5w_BSCzu-n--2zRMaGRA1scC52_pGes2Gj_ceH0N68vJB9wP6ASQFUzj6iicl1gOBlx4Wz-WEvGWZGFR9zGAxk2A98RONRqzRiEF-fe3JkNxDvlE3ca.png)
                    - Attention has thus turned to approximation and randomized algorithms which trade full completeness of the planner for major gains in efficiency - e.g. sampling based methods
                - Sampling-Based Methods
                    - Probabilistic Roadmaps - we want to find a better way of generating the search space 
                        1. Initialize an empty graph G - vertices correspond to robot configurations, and edges are collision-free paths
                        2. Sample configurations a(i) in Cfree
                        3. Use a metric to compute a neighbourhood set of a(i) of vertices q already in G
                        4. Local Planner: check if a(i) can be connected to points q in the neighbourhood, if so add the edge (a(i), q) to the edge set if no collision is detected
                        5. Terminate when N edges are added to the roadmap
                    - **Connected graphs not guaranteed!**![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/W1max6o8CMqRSK9T4hRfyKT5QRi4aDeRkzh5cVbGx3HxSfiIAhjClZIXGOqQM7R52axrAr2Qw0zQujepogtpNYfGQPj8i3HZwQbHEtACcpjfUlXDmv5ZW23V8OmKhicK.png) 
                    - PRM requirements:
Method to sample configurations in free C-Space
Method to check for collisions in C-space
                    - Pros:
Probabilistically complete
Apply easily to high-dimensional C-spaces
Fast query processing - search overs state space
                    - Cons:
Doesn't work well for narrow passages
Hard to connect vertices for differential motion constraints
Hard to sample uniformly in configuration space.
                - Rapidly Exploring Random Trees (RRTs)
                    - Similar to PRMs but for single-query problems (to solve a new planning problem I have to create a whole new tree).
                    - Build a tree by generating next states that are achievable
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/eEYI4fE34VUu6Mdw8ZEk-G0FwPb7t3J5KIruGNTBFFfX1VRxnIN_NQQPKGtzFga40LtUe6H7DsFHlhYZeTVIic9nc49z-yJi8zwmTgLqPB67SYT2yiS4aHkPWM3goAoY.png)
Only occasionally do we sample qG, only then do we plan a path to it. 
                    - Primitives required
                        - Method to sample configs in c-space
                        - Method for collisions in C-space
                    - Pros:
                        - Probabilistically complete
                        - Exponential rate of decay for the probability of failure
                        - Asymptotically optimal (RRT*)
                    - Cons:
                        - For non-holonomic robots, generating edges to sampled configs requires solutions to the two-point value problem.
                    - **You could only sample values that are feasible for your robot to reach from any current edges.** :
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/1qtvhlJfSs3V5P6QZlUfg74UkHJgZjeI-LBw_zn1-AHi3a0_3Y4oURSREVNWV07-DWfTfGZ0aJkMk8qbDG87xW08t6S6oS7DZuf13vGrqHWvL1aVo80IvGwK8zI-13oD.png)
                - Potential Field Method
                    - No explicit roadmap - instead construct a real-values potential function:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/0gpKNewmSQhY87cD5OxLmtDVvT-U2tbnGGyncIk2gNQcKesLXKi92mOQr3OmT-6M7Oz-L3PE3x8v78fR4z82KWUnix6ONU6oVFe-seRyGVLT8Qu0jK_LC3rC8QJFRCh9.png)
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/wr-NgfgMIUaUtheKQqbEtuFr1M9sXwq1RBMSWshtKQlOJOoakX6Te5MVFEKVIe3pndRJy9C28glXcWGYdy2WTatS43MGF02ZxUmdKnXXpiFrcS6RJJyUgk2EABMj4HqG.png) 
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/lLTSuzVUyTQ595nZIPlWcjNQT9_nX-NTucrVNJkt2nk32qTOaBMrTLK7ZohIMNCk7IbsNdzFPTTSIs8olvGVClFvVoQROxZ_iMxuJDNcoedt34ywm1WJczQFk-TR6MrW.png)
Derivative with respect to the different controls! 
                    - Creating a potential field in C-Space is **difficult! **One strategy is to create a potential field in the robots work space instead of the C-space.  
                        - Then compute gradient
                        - Use feedback linearization to get control inputs
                        - Compute gradients in C-space from control inputs
                        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KhGE6hT2PdyKcVtQJ6vV1cAdNHkld2wHiQJ9Txc_lpHAMO9evniGhimzLGN2-Sxxk8ojG-3bulzn4fl_c8KV0cBqXRWa0Mr2O91-bWPcT2MVM86wEoYuf5pq-fJeLSM8.png) 
                    - Feedback Linearization
                        - Imagine a carriage being pulled along by horses that can move in any direction
                - Requirements
                    - Representation of work space
                - Pros
                    - Computationally efficient once we have the C-space
                    - More than one path
                - Cons
                    - local minima require methods to resolve them
                    - Representation of C-space in high dimensions
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jsmx_ETwIR4aaAQEXS7eRwios7jAimmPxwzoptEhUlBTxvMuUMdLcjItyenWPwzKt1jls2HvPpGz54S8GVGPrC4F4hf6t_B6xuh4u5kl-rDjazpeDq-6LFtB0x5URA2s.png) 
        - Multi-Robot Navigation and Path Planning
            - Focus on multiple robots, connected via some form of communication.
            - Multi-Robot Systems
                - Robot swarms/robot teams/ robot networks
                - Needed for distributed problems, Also adds robustness and resilience through redundancy - additionally the whole is more than the sum of parts.
                - **Coordination **- linear gains from increase in number of robots 
                - **Cooperation **- Robots take small hit to solve overall problem. Non-linear, threshold which can improve system. Need a certain number of agents working together before the benefit is seen 
                - **Collaboration **- When robots need each other, other robots have complementary skills that we can leverage. 
            - Taxonomy
                - Architectures can be centralized or decentralized. 
                - Implicit vs explicit communication - can observe the robots position implicitely, but it's battery needs to be communicated explicitly.
                - Disk models are used to represent communication range - very crude approximation.
            - Communication Topologies
                - Start topology, fully connected or random meshes.
                - 
            - 
            - MISSING A BIG BIT
            - 
            - Decentralization
                - Want similar performance as centralized control. As information percolates they converge to the same values.
                - Advantges
                    - No single point of failure
                    - Any-comm algorithms which gracefully degrade under poor comms
                    - Any-time algorithms which continuously improve the solution
                - Challenges:
                    - Communication delays and overhead
                    - Input: Asynchronour with rumor propagation
                    - Sub optimality with respect to the centralized solution.
            - Collective Movement
                - Properties: No collisions, without an apparent leader; tolerant to loss or gain of group members. Coalescing an dplitting and reactive to obstacles.
                - Benefit from energy saving and better navigation accuracy
            - Flocking with Boids
                - A boid reacts only to its neighbours
                - Neighborhood define d by distance and angle (region of influence)
                - 3 steering rules - separation (stay away from neighbors or will collide), cohesion (want to stay in a group don't go too far), alignment (stay in the same direction as neighbors)
                - Boid wide field of view, no delays, no noise in measurements.
                - Behaviour-based with priorities
                    - Low priority acceleration requests towards a point or in a direction to direct the flock
                    - Highest priority to obstacle avoidance, steer to avoid!
            - The consensus Algorithm
                - Reach decentralized agreement purely based on local interactions.
                - Based on graph topological definition of multi robot systems useful for motion coordinate and synchronization.
                - 
                - Discrete:
                    - Iterate over neighbors and get their values. Take the measurement and sum them, average them to find x at time t+1.
                    - All robots eventually converge to average of initial values. Convergence rate is exponential.
            - Formation Control
                - Formations are **specific **geometric configuration as opposed to flocks - some applications require moving in certain formations/groups (think trucks in formation on the road).
                - Need to know something about yourself **and **other robots. Challenges with noise, anonymous robots and non-holonomicity
                - 
    - Lecture 7
    - 
    - 
    - Project Notes
        - Part 0
            - Useful Commands
                - ros2 topic pub -r 1 /my topic std msgs/String ’data: hello’
                - ros2 topic echo /my topic.
                - ros2 topic type /my topic.
            - 
            - Exercise 4
                - ROS 2 is middleware, anonymous publish/subscribe for different ROS2 processes to talk to each other. ROS graph contains the different nodes and the connections between them all.
                - Nodes, Messages, Topics and Discovery:
                    - Nodes are items which send ROS2 messages
                    - Data type used when publishing to/reciving from topic
                    - Topics...
                    - Discovery: Process for nodes determining how to talk to each other
                - Client Libraries
                    - ROS client libraries allow ROS clients written in different languages to communicate - ATM Python and C++ centrally supported. 
                - Discovery: 
                    1. Nodes announce their presence to ROS nodes on the same ROS domain - settable with the ROS_DOMAIN_ID environment variable. Then appropriate connections are made
                    2. Periodically, nodes announce themselves so connections can be made to newcomers.
                    3. Nodes announce when they're going offline.
                - Nodes will only connect  __if they have compatible QOS __  
            - Exercise 5
                - Initially - ros2 not working. Working on fixing this by checking if ros. ⇒ Fixed this by creating a command to set up the sources. Don't forget to run ". ./start.sh" to load the aliases into the current working script.
                - b.) Daemon is down - this daemon sits around and records nodes arriving and leaving the network. Useful if a node has a short lifespan and doesn't want to spend ages discovering neighbours.
                - c.) Empty
                - d.) parameter_events and rosout
            - Exercise 6
                - a.) Publishes hello to my topic continuously -r 1 sets the message to be published at 1 Hz.
                - b.) Listens for the topic and prints hello
                - c.) Tells you the datatype of the topic - tells you how to handle the data
            - Exercise 7
                - a.) Makes a publisher producing a twist message by .1 in x linearly and the angular .2 in z every .2 seconds. 5 is the QOS history
                - c.) ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jgUqxBg5k_qbRgGn75YwXY_n7kyIT2rFz2OUetOz9nlZNKc-Zhi4foHBbEqRoG44qdTEwpKsCun1GJXQivIW5RQKHeSsxgpwsUnhCPLbdTiNgsDLlPTH-2XPHTtmlKbR.png) Produces this. 
                - d.) had to change to robot0/cmd_vel then it worked 
        - Part 1
            - Euler's Method
                - Basically step along the tangent of the curve repeatedly.
                - $$y_{n+1} = y_n + hf(t_n, y_n)$$ 

                    - Where h is the step size
                    - n is how many steps in the iteration you are
                    - t is the time (When your differential equation needs it)
                    - f is the differential of the function you're attempting to approximate
        - 
        - 
        - 
        - 
        - 
        - 
        - 
        - 
        - 
- 📡 Principles of Communication 
    - To ask Supervisor
    - 
    - Lecture 1
        - What is Routing
            - What is routing?→The process of finding a path from sources to every destination in the network. Can be one to one, one to many, many to many etc.
What route should you take to connect to Antarctica from your laptop? 
Routing handles what routes you should take, are there faster routes and what happens if a link goes down along the way.
            - What is a routing protocol→A routing protocol builds a routing table for routers and switches to route packets in a network. Node then make  __local __ decisions (next hop location) that are based on  __global __ topological information (the shape of the graph). 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mn1cSkfQdXfaa-1x-KpBukDxqmqkoPCVRAC7e1ixecOQIIc6gsXZgg8c7XfEoQxikP5eHrVga7C1Q17bCFaKN3-uf65HCD2iwVYz_E4_iTqfmpAZcEtf6_j1Nv3reOBV.png) 

            - What are the differences between local and global decisions? ↓ 
                - Given that global decisions rely on global state, this state can be dynamic (a link going down or one path being found to be faster) and changing - where as the routers contents will not change on their own. Additionally, global state can be **hard to collect **as a system can crash without your knowledge. 
                - One difference is in the **timescale **of these events. Local decisions involve deciding where a packet should be routed with < 1 millisecond to make that decision (using a routing table). However, global decisions require data from around the network - this information is bounded by the speed of light. Thus, by the time we've found out a link has failed many packets might already have been sent.


            - What is route **oscillation **and what are the problems with it?→Route oscillation is when the listed route oscillates from one path to another from minute to minute (or whatever timescale,  more impactful when it happens more often). 
Consider if the route to Facebook was oscillating. The traffic along those routes would vary wildly from minute to minute, this would impact the users (the traffic load along those routes would vary enormously, thus capacity would vary enormously) along that route and the load balancing algorithms would perform poorly if the latency was changing wildly from minute to minute.
            - What are the requirements for routers? ↓ 
                - Minimize routing table space to make them fast to use and ensure there's less information to exchange when it is exchanged.
                - Routers should be robust to not allow black holes (information silently disappears into a defective router), oscillations or looping (A ⇒ B ⇒ C ⇒ A - work is being done but the packet will never arrive at it's destination). 
                - Should use an Optimal path (for some measure of optimal)
                - Minimize number & frequency of control messages - we don't want to flood the network, and we would like the system to be resistant to a lack of such messages.
        - Features of Internet Routing
            - Internet routing varies from the traditional circuits in a number of ways
            - Packets not circuits, meaning timescales can be much {{shorter}}. As we need not create an expensive connection. 
            - Topology is complicated and heterogeneous (diverse in character) - as opposed to telephone lines which were very much tied to businesses and were painstakingly designed. 
            - Tens of thousands of internet providers (contributes to the complicated nature) **and **many different types of connections. Fibre, radio, cable etc. (these affect capacity **and reliability**)
            - Traffic source is bursty! With a huge range of source behaviours
            - The traffic matrix is unpredictable, what does this mean?→The matrix of sources to destination cannot be predicted. We can't tell what websites a user is going to visit (messaging protocol might change). Far less predictable than who we're going to call.
            - Goal: Maximise throughput, subject to minimum delay, cost and energy.
        - Internet Routing Model
            - Describe the 2 key features of internet routing→Dynamic and distributed. Meaning it's dynamically routed, and distributed (rather than centralised).
            - Describe Intra and Inter-AS routing↓ ↓ 
                - AS means autonomous systems, for example Facebooks interconnected set of local networks.
                - Interior Gateway Protocols are used within a autonomous system. Generally optimizes for shortest path, whether that be shortest stop count, lowest delay or highest throughput.
                - Exterior Gateway Protocols are used for AS to AS routing.
            - Describe the requirements of Intra domain routing for high and low end AS's↓ ↓ 
                - **Convergence time** (the speed at which changes to the network are propagated throughout the network.). For smaller entities this may be less important, as the change in latency may be smaller for short routes and some connectivity disruptions will be tolerated. 
For larger entities (especially for whom speed is a requirement, e.g. trading) the convergence time is crucial.
                - **Should scale for the size of the AS**, low end AS's may only have 10s of routers while higher end AS's may have up to 1000s.
                - **Operational/Admin/Management complexity**. For low end AS's this will be simple and self configuring. Don't want too much human intervention.
For higher end AS's this will be complex and require operator hooks for control.
                - **Traffic engineering capabilities** (high end only) - for large networks you may create some boutique intra domain traffic engineering to optimize the system based on knowledge of the topology. I.e. you might want maximum throughput in one place, and minimum latency in another - (streaming one path and gaming another)
            - Describe the requirements of Inter domain routing↓ ↓ 
                - **Scale for size of the Global Internet **- focus on **reachability **not optimality (e.g. we don't want google.com to suddenly fall off the map). Sometimes we cant optimize, because different networks can be designed for  __different things.__  (For optimization, Google, Netflix etc. will put a server  __in __ (or very near)  __every ISP)__  
                - Should use IP aggregation techniques minimize the size of the core routing table.
                - Allow **policy-based routing **between autonomous systems! Business relationships (which forge the connections between AS's) are arbitrary! I may only allow a certain number of connections, a given speed etc.  __Qualitative relationships that get turned into routing decisions__ 
Needs to be extensible to meet demands for newer policies.
            - Explain this image and how it relates to routing:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/MLv_NefWOyKGcX9aR1BBUiszy9PCshxAspmDsNt5HqMRXYmmWjqqqfSFpaKlXevfY8-YZmIS_8zNmLzPo6DliwG6-8prhMBLOvCoUIXZg8YAN-J7M4TTHwGitHazFy9q.png)→This image shows how an AS's are linked via Inter-domain connections. These ISPs (A, B and C) have users within them, and certain users are connected to other domains ( __**border routers**__ ). Thus a higher level topology forms  __between AS's __ - the inter domain level. The **Gateways ** will perform both inter AS routing with the other gateways and intra domain routing with nodes within their AS. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/93ln84Qx3G1SIZ0oC-zbLezY011WO-WSywyCB5f3JoHEY0OX2UgA9BDgsZrwsjSaAeB0iwfHiDpQYyqU9gyO-vZLA6hcg9jxERW2O8i1NkTQfzmOFVGHELVEavuGCIXi.png)
Layering:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-RcIB2Yym-PJiE_gGx6gvYMV5q4-S15VKW--0mh0iAj-y8jkO-hI_ieZWBhCb-H8oqqkwR31ZETOYzniHjWDlabVw7dDfcS4IDnFc5e8sUk233HrO_ucRTOvTu6-ZEZ6.png) 
        - Basic Dynamic Routing Methods
            - There are other ways to do routing than how the internet mostly does it, by→forwarding on IP network prefixes. Each network has a unique IP  and each router that the packet traverses will examine this IP destination address and look for a match in its routing table to figure the next hop of the journey.
            - What is **Source based** routing?→Source based routing means the entire path is computed at the source (based on a stored topology) and it then communicates that path to the routers who will obey. This can be done be encoding the route into packets (can be large & inefficient). This can be used to recover from outages or avoid certain paths. Could possibly be used as an attack vector
            - What is **Link state** routing?→Per-link information is known to routers, and periodically routers flood the network with their link information to get a map of the network. This map will be the same for **all routers.** Need to do Dijkstra. Fast convergence
            - What is **Distance vector** routing?→Per-node information - at every node store distances to destination nodes in a vector. Set this up by peeking **only at your neighbours signposts! **This can be better as you need not flood the network and share your entire network with competitors. (will converge to same) 
            - Give a reason for choosing either Centralized vs distributed routing→Centralized is simpler (and can be optimized better), but is prone to failure and congestion.  
            - Give a reason for choosing either Source-based vs hop-hop→Source based allows for easier network engineering, as it allows for specified routes. But you have to encode a lot of data in the packet header.
            - Give a reason for choosing either stochastic vs deterministic routing→Stochastic routing adds randomness to the route. This can spread network load and avoid oscillations **however **results in misordering. 
            - Give a reason for choosing either state-dependent vs state-independent→State-dependent can allow for recovery from failure. However, state-signals are always going to be a little bit stale and it means more communication & complexity is required. 
    - Lecture 2
        - Central routing
            - Within a single network, assume all nodes involved are part of a single security domain.
            - Describe SDN→SDN (Software defined network) is based on antithetical architecture where you can reprogram the operations of the network. Switches and routers have an open API, allowing adding and removal of entries to the routing information.
            - Describe where traditional routing wins and where SDN wins in manageability, flexibility, scalability and robustness ↓ 
                - Manageability: Clearly SDN is more manageable. We can route gamers traffic one way etc.
                - Flexibility: SDN is much more flexible. Trade off queues and delay to get an improvement.
                - Scalability: Traditional networks are scalable by design. Scalability of SDN depends on the network.
                - Robustness: Traditional networks are very robust, SDN's are **not **robust - if the central node crashes, you're screwed.
        - Fibbing
            - Describe briefly what the  __Fibbing __ protocol is?→Fibbing is an attempt at a middle-ground between traditional routing and SDN's. Wherein you have some control over link-state IGP's.
Want high manageability, flexibility and robustness.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sEDR9MH1qVaN5XxBD_QnwLfaKy0OPC2jJ9-ZnIc0Gbc-FZxNj5aGH5LMV25Zo3nZ4resT-yn0jWvdnv1R7gEPT4To5XxFk2OgVgjK51EFIJwtpU6F8lBXQgxDtz0Yl72.png) 
            - How does the  __Fibbing __ protocol work?→Instead of replacing the normal routing protocol, we instead  __lie __ to it (using carefully-computed information) to provide alternate routes. 
So if a route is going unused (because it's not the shortest path), Fib first inverts the shortest path computation to figure out what needs changing. 
Then it invents a virtual node V1, and tell your source node that the path to the destination via V1 is the same or better than the shortest path. Note that FIB pretends to be one or multiple routers, and shares routing information.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ViINGwGcNzO58xtLjE8fMu3fs2ONsX6bFbNSVHzsat9vw1dovFYRV_uYgsntuDqWpIGXy92cZVuEC00bpMw2GMI0W6zSBihWI71RES3P1BHJJZyBkAZwP8-7Dr5Qm853.png) 
Note that the virtual link  __still physically goes via A.__  
            - In some cases, you might require multiple virtual nodes. But you  __can __ merge multiple virtual nodes. 
            - How many nodes would need a virtual node attached in order to get this to work? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CB3mFUFi_GAk577TTQxjKj2k47UW6l9OKkHtJpHSW7O1oJflvdx0bqmwYZ01o_9J4rutLYwfaGuKJsjdlW9NX4ipOX_x5JbnuLld3yhXul1xgiNWCoWqdIR34jqW2MBC.png)→In the simple algorithm every node except F would need one
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/j-Tfy6chlaMbVod2qP5Ky1ctSQ9j8ASZaNby3fhwrA0sNVp9g-taXza04DoddNr3G5PZvGWsRlD21DHGn6X6xNabSIpna8x-DZ05ATPsT7D5SQ5YqGrAUzjicUPbNpz4.png) 
However, we don't need the nodes at D or E - because once you're on that route there won't be a reason to double back. And you don't need them at C or A because  __we only need to lie about the link from B to F__ ! 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bKIgBBJUwpx7lbBmN_vZf1G3Ic_MIss4XYr7msLDw_BS19VL_8BebHannSj9z1KvcKwQEcxIFX-FzPpQrt2tD-hIPznYq8FIbRBIkLKH7jeASN4Yuvdxv1bvhkEVHx-a.png)
            - How does the Fibbing protocol achieve robustness?→It can distribute fibbing controllers, having multiple on the network in case one or more fail. 
Also, if a real network link breaks and you're left holding a link that's lying - that's fine! The distributed network protocol will realize its broken and act accordingly - finding the real shortest path.
    - Lecture 3
        - More on Fibbing
            - Note that fibbing has a very low impact on routers - meaning it scales well.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/hlgAjXuHRH__9RLioNFteZC0iRuhH8kdRoGjT0f3DNcO17GaS9At7cbsmCP8zeIRyvItSpcNtJM1olz2q5i8mOyBSTB5rsz5ZVUsduPdaw1esbDOJCAb06_ZTRIUz2w8.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/joXnjEnbWpmXyzgwlX3pZfVDcyaWsN18Tt9Dlio3sEttxedC_w9MV0biF0e8L2x67_dj97SdEn3maZwIs9P5XC2ELUpCxaw1WWn8Ssci3O7INVBYz7JSrmc60iPda1ua.png)
Here the failure occurs at the end when the controller cannot be reached at all. This is only the case if the red flow was a special case which the controller was controlling -  meaning once the controller goes down, we don't know handle the red traffic.
        - Multi-Protocol Label Switching (MPLS)
            - What are port fields?→A field stored in the packet which defines the destination process. 
            - What is MPLS→Multi protocol label switching. This is a forwarding scheme designed to speed up IP packet forwarding. 
The idea of MPLS is to use a fixed length label in the packet header to **decide packet forwarding **(As opposed to longest prefix matching - which is complicated and isn't just a hash table)**.** 
Instead use a 24 bit label that maps to an output port & that's it!
Note that labels  __only have significance in a given switch.__  
            - Called a shim layer, stands between the link layer and the network layer
            - Describe the MPLS Header format ↓ 
                - 20-bit label value
                - Exp: experimental use - can indicate the class of the service
                - S: bottom of stack indicator, 1 for bottom, 0 otherwise. This is used because you can stack MPLS headers.
                - TTL: Time to live:
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_vFZAA3XzWc21ULJIoHrlN7BP1RIU3cViA9PgE0WUR1S7fdorm5x3A-1Bscl8vtBEO3ttoxKN3ILg1gZCzI6mwucC0TOLwWahXdyD9KOV1aUFSFfOw9SesSSixquyKTf.png) 
            - Forwarding Equivalence class
                - MPLS capable routers are called  __label switching routers (LSR)__  
                - What is a forwarding equivalence class?→A subset of packets that are all treated the same way by LSRs (label switching routers) - for example if I don't know anything about a packet destination, just send it to switch X. It's just a group to bundle a class of packets that will have similar network behaviours.
A packet is assigned to an FEC when it enters a MPLS domain.
                - What can determine a packet's FEC? ↓ 
                    - Source/destination IP 
                    - Source/destination Port number
                    - The protocol ID
                    - The Incoming interface
                    - Differentiated services code point (bits in the headers that will tell you we want high bandwidth not low latency or vice versa)
                - Different {{scheduling and discard}} policies can be defined for a given FEC.
            - MPLS Operation
                - Describe what will happen to a typical MPLS packet starting at the ingress to an MPLS network ↓ 
                    - First it get's strapped with an MPLS header, with a FEC class encoded which depends on feature of the packet.
                    - At subsequent LSRs: The label is used as a key into the forwarding table, the value will have both  __the next hop __  __**and **__  __the new label to wrap the packet in.__  
The old is replaced by the new and the packet is forwarded to the next hop.
                    - Egress LSRs strips the label and forwards the packet to the final destination based on the IP packet header.
            - Label Switched Path
                - What is a label switched path?→For each FEC, a specific path is needed. This is the LSP which is assigned and **unidirectional **(goes in one direction).
                - To set up an LSP, what must each LSR do? ↓ 
                    - Assign a label for packets along the LSP (label switched path) depending on the FEC (forwarding equivalence class).
                    - Inform the **previous** LSR upstream of the label we've set.
                    - Learn the label from the next LSR so we know where to send a packet next.
                - To propagate the labels we've set, we need a label distribution protocol - the forwarding table is then created as a result of the protocol.
                - LSP Route Selection
                    - What options do we have to decide on a route ↓ 
                        - Hop-by-hop routing: Use the route determined by the dynamic routing protocol (shortest path).
                        - Explicit routing (ER): The sender LSR can specify an  __explicit route __ for the LSP. This can be selected ahead of time, or done dynamically.
                    - Explicit routing allows for establishing LSP's based on policy, QoS, etc. Additionally, we can have pre-established LSP's that can be used in the case of failure.
            - Diffserv-Aware MPLS
                - What is Diffserv-Aware MPLS?→Switches and routers have special case scheduling, where different users get a different share of the network. Differentiated service! 
You can then bill people for their different service and collect $200 as you pass go.
                - How is Diffserv-Aware MPLS done?→At ingress, packets are given their standard MPLS packet but also an extra one which defines what type of service they will receiv.
Core routers then process the packets based on the labels and Exp fields and the networks will do different things with queueing and scheduling etc.
                - Bandwidth brokers then buy and sell bandwidth, higher bandwidth and lower latency.
            - MPLS Protection
                - Link-state routing has a restoration epoch time of seconds.
                - How does MPLS enable fast failure restoration?→Compute the next best route, then if a path breaks we can immediately shuttle the new start label to the ingress point. This path would have to be link or node disjoint, so if any link/node fails, we're still okay.
The timescale would then be RTT - rather then whenever the next epoch occurs in link-state routing.
            - Label stacking
                - A packet can carry multiple labels, organized as a stack. Processing is always done on the top label.
                - What is the purpose of label stacking?→Using label stacking we can group multiple LSPs into a single route, called a tunnel. 
This new path get's pushed on top of the stack and will get popped off at the end of the tunnel point. 
    - Lecture 4
        - Segment Routing
            - What is segment routing?→Segment routing is a loose type of source routing where instead of every hop changing the routing behaviour, the routing behaviour changes from segment to segment - i.e. initially a stack of segment header is pushed on, then at each segment node the top segment is popped off and the packet is forwarded to the next segment.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sMzM0xK8qxQ_1_ik9BIF-wNlyhpjJ6pQkxaEgPgTJSUrqQtIWAYGtG0XKfTIg2FdJH589o7MYrsxxAXcGUAkfnqfGwhmGhrw6sQw4hUBVFYXzIfr_Hgxr7pymj6jeuFT.png)
            - Operates on the IP layer (kind of) - treat packets differently not just based no shortest path forwarding, but note that you may not have to do something special on every hop.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/XaJjvuPAK9tNWHbnE_N7mXsyd4XfWKbWpxMmzvOlr3pFyyfKCpEy6H0IyTjouV5VRSOFuI2QIn9J6l2WpeYtmaJ6Ikjkghg6vAkvB7L1k7MvpTAG8yKfFNBD1oLTO-gL.png)
            - What benefits does segment routing give you? ↓ 
                - You can do the traffic engineering, send a packet along one segment if it's low latency and another segment otherwise.
                - It means your paths are more resilient: You have distinct routing along segments that share no nodes, and segment routing can facilitate fast recovery (don't need to wait for router advertising).
                - Easy to expand to IGP (inter-gateway protocol), as you can advertise the segment in the Link-state advertisement state)
            - Describe the synergy between IPv6 and segment routing→Segment routing headers can be implemented using IPv6 headers set to forward to the next header (You store the list of segments in the segment routing header then adjust the IP header when you reach a segment node).
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FvjFDiR8jaANTYPaK4SPcbehWIOnWs2UiwJMqMvuX-qSaFUD47KIiYaNt-OnDyl66o05kSPAuihDV3byMWlalnQAuBJ_yq8ctu5CH5OF3k74YnTOn29yWBRZreKxdg43.png)
This means routers that support IPv6 can support segment routing out of the box - they don't need to learn the segment routing header language.
        - BGP
            - Customers & providers - running costs and initial investment costs need to be offset by charging people. 
            - If I need to connect my West Dorset ISP to a network in Canada, I have no choice but to talk to a bigger network like British Telecom - they will then be connected to people with fibre under the pacific, through this packets can be forwarded.
            - Peering
                - Describe the "peering" relationship?→Peers are backbone providers that talk to other backbone providers - providing transit between their respective customers. Note that peers do **not **provide transit  __between peers! __ Because they would be acting as a provider for another peer:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/N72Ff8PHN17313wDaX66Di07dMu82CmGhyMRKZsOOdNjoOQWaMpvh2rTvnBmCwi1MDrZ5qyG8Dol7nsrESn4s8Pxx4yP61t9xYdk8FZqJOgZOynLZBSwkg5aocIvQCH6.png) 
Traffic is not allowed along the dotted line!
Note that peers do not exchange $$$$$ - they seek for traffic to be equal from and to them, meaning both can provide a service.

                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CWFJn9fk0GrNw4BqKDAQof0Oag8uFBRlrumDyDBEsq-Es5Uyhbcj49X9Ziqle-n0O4ORZKXihnPAUk_6ZLBQmjeEwvt1ZpcljpBFo5NNCnXAQQUNZrEm29MgQu1DCTWD.png)What does this image show?→Demonstrates the hierarchy of providers, providers can have providers - meaning you go up the chain and then back down 
                - What are the reasons to peer or not peer (3 pro, 3 con)?↓ ↓ 
                    - Pro: Reduces upstream transit cost
                    - Pro: Might be the only way to connect your customers to Tier 1 internet providers

                    - Pro: Can increase end-to-end performance
                    - Con: You would rather have customers - you would like someone to pay you to connect to your users, not pass over connections for free
                    - Con: Peers are usually your competition who you will be benefiting by giving more users.
                    - Con: Peering relationships will need to be renegotiated periodically
            - Forwarding
                - What is the difference between routing & forwarding?→Routing defines end-to-end paths, forwarding defines the next hop. 
                - Border routing gives you interconnectivity between AS's, however you don't have enough information (ISPs don't publish all internal topology) to form full routes. 
                - Why wouldn't an AS publish it's internal topology to allow for better inter-domain routing?→You would have to flood the world with all your router information, this would kill the network and does not scale.
Additionally, a given ISP has customers it's optimized for - if you knew how and where they've done that you could steal their customers.
                - In what two ways are forwarding tables populated→Statically and dynamically 
                - Describe static forwarding table population→Administrator manually configures forwarding table entries. Giving more control, allows for not just destination-based forwarding. 
But obviously it doesn't scale and is slow to adapt to network failure.
                - Describe dynamic forwarding table population→Routers exchange network reachability information using routing protocols - routers then use that to compare the best routes.  
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/r8mspHPETYebvtI-S20A96ZqDWyIHB-ibanVzHtqZ3_yn2bbuba5CoMM2WTO8T08IJ7d1mSpcImpnguKBqq_M8ct525nIE7wLIUxKVTCDNb52rMqSsgu9rn4x9zQx5nL.png)
            - Architecture of Dynamic Routing
                - How do edge routers learn and share routing data?→The edge router hears the internal and external routing - it then takes information from the outside world and maps it into the inside world in the forwarding tables. I.e. it will share that data so other routers can figure out where to forward so the correct edge router receives a packet going to a different AS.
                - BGP is a {{vectoring}} protocol. Meaning each router knows a little about {{network topology}}, only {{best-next}} hops are chosen by each router for each destination network. The convergence focuses on {{connectivity}}, not optimizing some metric - then the network {{converges}} on the best paths.
                - Routing computation is distributed among routers within a routing domain, routing messages are usually not routed - but exchanged between physically connected routers. 
Note that shared routing data can be stale.
                - A border router opens {{TCP connections}} to all it's neighbour routers! Even though those neighbour routers, may not be {{one hop away.}} This is because you could have disjoint bits of the network connected by multi-IP hop bits of network - e.g. the same AS can be in different places around the world. Here, the turquoise bit is all one AS, as is the white: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ShM4LqdcI6HsFR6ucrjwWYxS2GqQ7uAbaxugD6V5ZQ5B1jfMuV_Ydm7E2HPsRPuk5XDVAybH_GjlqAuMh7B1Ug70RhFFwQV0SNgXAFWuoP440Sk-NA7AQkk480-2LStH.png) 
                - Autonomous systems are given numbers, these are centrally allocated.
                - In this case, BGP will not be needed - the network will simply find the shortest path to one of the border routers.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/hBw3yxm--Nz7ELIBjovG_Bcd9q9BdRdt-mWPRQbVihqrPM2nDGUkRKBD_7EjUlpYnamJ5TCmvLwRQav6az37k7JjlDFhX8aIK6VnLPwGNTw9O17Crhi8IV7X55mfCvs1.png) 
                - How can ASNs be shared?→Paths in BGP will be computed using the IP prefixes NOT simply the AS number.  
                - Autonomous Routing domains are not the same as autonomous systems because→ARDs can share the same ASN, or can have multiple ASNs.  
    - Lecture 5 - BGP inter-domain routing
        - BGP - Border Gateway Protocol
            - A policy-based routing protocol which is the de facto EGP of today's global internet. It's a relatively simple protocol, but configuration is **very complex** and the entire world can see and be impacted by your mistakes. This has been done in reality, when an AS in China advertised itself as the best route - meaning they received all internet traffic for a time.
            - Describe the process that occurs when a border rooted is turn on under BGP?↓ ↓ 
                - The router first sees it's neighbours and connects to them via TCP to learn about the world through the BGP protocol. 
                - It then starts to exchange information like what are the IP prefixes that are **in their AS ** __or__  __** **__ **Reachable across their AS**. I.e. Exchanging all active routes.
                - They will continue to exchange incremental updates over time.
            - What is iBGP and what is the problem with the mesh configuration→The router also needs to learn about other border routers **within their domain**. This is needed so the other border routers within the AS can share routes and IP prefixes with each other.
iBGP (internal BGP) is used to communicate using IGP (internal gateway protocol). So all the border routers have TCP connects to each other! 
Under the mesh configuration, we have bad quadratic scaling: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FkaUTMKaac7MDJIEu1uA7ZrCwDBTtzsJkJ7j3hB7dI6fcMDv6i9HrPV0Lts7Qy6r8cpozIaFxZHOyVOPPR4FZ8Rg6VTdAFQoQW8LwYFb6831Tmd3WUOP0eMXgD0D-ilu.png)  
            - What are the fours solutions for the iGBP mesh problem? ↓ 
                - Buy bigger routers
                - Break AS into smaller ASes - adds complexity and operational costs.
                - Route reflectors are used to build a star network rather than a mesh: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/GXtPR0JYW3hWwmrHd4N_8f7IrCDYXoSBnm0nCR9SKbpYzFlXxQKRz-sRn_Z6h7aE78NE6pwC9Z5WEbABygdZWqppGXrC2D8KvkL7ymJf4Lxm09nbTw2x6fwnZRlmoyLu.png)
These reflectors past iBGP updates to clients and perform some filtering - only allowing the best routes.
                - BGP confederations -
            - What are the four types of BGP message? ↓ 
                - Open: Establish a peering session
                - Keep-alive: Periodically handshake again to make sure everyone's still alive
                - Notification: Close a peering session
                - Update/Announcements: Announce new routes or withdrawing previously announced routes. 
            - What are BGO announcements?→Messages that announce new routes are withdraw previously announced routes - they are **prefixes** + **attributes**. 
            - What are BGP attributes?→These are pieces of data/configuration used to decide the best route. 
If a router is advertised the same prefix from multiple places, we need to be able to make a decision.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bht_ewP9ucARLh2St1E7Rjg3OulPllzqdTYFm729eWQP1Zd5x4e_eBC3RK7jqBAbGCg-_3fYI7QMwZCKt0gxin_ToxotUb8zJ9oefL-044jVEnwdVtVgI9HUko8HK1Xq.png)
            - BGP Attributes
                - What is the AS_PATH attribute→Whenever a route passes an AS, the router adds the AS number of the AS it is travelling through - if the path of the AS was previously in the AS_PATH then the route is ropped.
                - What is the NEXT_HOP attribute→This stores the IP of the router that ADVERTISED THE ROUTE (**NOT **the next hop along the route):
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/kPTkXDyyi76XmWVjKZvNomqykeXJMdmK76-f85iVr5iVDsy7Ytdcwsw1GJFEMWpPHpNkn0fhA5fE6EtcvUw9QVoWqjkN2Dmt1om4LZd4HScSO3gTgn-nFjpjp7x8gYSr.png) 
                - What is the MULTI_EXIT_DISC attribute?→Multi exit discriminator - if there's multiple choices to enter a AS, we use this attribute to decide which border router to enter via. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/b8uGkALXRWS5edF16UKt8CbwX1MPPHQTCjYldof5VIddAdr1g9wvHyp-r-7eVhaDtN7BfLLKBjZ3h_OExUjB1WOOkNNz8flIUGTeYHRwV_C6gydVl0qBwOFXiINBj2EU.png)
I.e. here the top AS notes that the bottom AS prefers to receive traffic via the left router, so it chooses a border router appropriately.
                - LOCAL_PREF: Used to choose external BGP paths - i.e. choose the border router to **exit via.** 
                - What is the COMMUNITY attribute?→Way of aggregating routes together. Useful for differentiating customers, providers and peer routes. 32 bit way to group things with no predefined values.
                - ORIGINATOR_ID:
                - CLUSTER_LIST:
            - How is route selection done in BGP?→You work down an ordering of attributes, and try to break ties as you go.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ik1k-KSpgsxOsRQSsOP-r4vF3VCEUcBF9mS4pMR9suWpODZ2FXw09UB1FiHYqWgS3FSkqgJebYNq8a-PXnj0oeXEuzJSt6GykFyub3K120kilJggjquY_Ks1NbaV5J_5.png)
            - BGP Route Processing
                - Describe the 6 stages of BGP route processing↓ ↓ 
                    - First we **receive **a BGP update 
                    - Then we apply our import policies. The policies are specifically written code that control things like route filtering and tweaking attributes.
                    - Best Route selection is decided based on attribute values
                    - Create the Best Route table, and install forwarding entries for the best routes in an IP forwarding table
                    - Apply export policies, more route filtering and attribute tweaking. Also open ended programming like import policies. You filter the information you've learnt over the process because you might not want to tell everyone what you've learnt (for traffic reasons, business reasons etc.)
                    - Send a BGP update
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/s1Lwilw8VUYzAvFcdgRMkfRUwbsvMpcDTjiBXrgEJFe3eL0DLw3FOKxRyqf7WQNqPHfg3OUP3SfvYzpCOdrP-SzfCvjwCHqDuLhFymvRrJtsxx4_vjSMAY6yh3BCPyTs.png)
            - Combining EGP and IGP
                - What will the following combination of forwarding table and EGP result in and why (For the router pointed at by the pink arrow):
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/lvgRxidvsFdIzh4RCXCuGyau4XJBUCuHyaS3TT9X3mgF4-Ze95QbnzKDCE53D3a7eAsIPFbCxex_wMyWrBR1dyNU7GqZBoicIj7_UOD1UuzlPCxd2QZeAteXLw-G9exg.png)![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/s-2ZBFH8x4jaT5BQaVxI7krJwjgwGXs91N5znnmnl_F2X-U9a1rXJYR4qHEpa0M51X5id8_vtDmiXKdw2SX7EZNYPczEDj2ChGt2qwZsMXfeTfxYUL3axTNemNq7kmc6.png)→This results in:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2W-fOBhbNRlXR1YqE0OJVN3m4cTbP765TY5Owcss_45hGLBO1PJJsMkHBROJrRi-y0WXnTnKlLjxDlKja5XuyakKw-L3Mle43fItrdGWaCuKYh78wpQiyFUeKB3WfYuy.png) 
For 135.207.0.0/16 We know we received a message from AS2 at this address - and to send there we can find the best next hop address.
Similiarly, for the connection 192.0.2.0/30
            - Implementing Customer/Provider and Peer to Peer relationships 
                - What do we filter out when we export routes to providers and peers? How about customers?↓ ↓ 
                    - We filter out the routes gathered from other peers and other providers. Only providing customer and ISP routes.
The ISP routes are the ones we know about already.
                    - We do no filtering for customer, we love them. 
                - First we import routes from peers, from customers and from providers into a database - note we also store ISP routes that we know ourselves!. 
When we send to  __providers and peers __ we  filter out any data from peers and providers, only sending customer and ISP routes. 
We give everything to customers.
                - How would it be decided which route to choose?
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Z3IOiRjZpK03quUpnbE_ZJhEU7VrGwgRnGkvdkyKK0qvM1A657WHMcsLE48yBxMpdJ2pTRtXDft36OnIycq1TPu9JoV7Qlvb-yLIPyh22eD1-SauxP6MO4y_WujchuOo.png)→This would be based on local preference - iBGP is used and decides it's local preference for each route, it will then choose the highest one. 
This still allows for recovery from failure, once we know that a connection/route has failed along the way - we go the next highest local preference.
Incoming announcements are tagged with a local preference.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/IvDN3ogn79I_OoIziS9WGTPxMPwfMaAE-hLUNvnmyjDsfmBubJxuYCFZEPnm2XIV3ThJmmSW601wFqfhYlB2Q4WJz3N7KYLd_xAYhLPLrlan7yd4TQ38dtW1aMzBkkAD.png) 
In this case it will go via AS 2.
                - Why don't we just run a ping application via different AS's and decide local preference based on the fastest one?→Because we are routing via whole AS's - it could be 1 router hop one day and 27 the next. The internal and external routing worlds may differ a lot.
Note that shortest AS path is not necessarily the best choice either:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5TwB6Mxy3GsK90satISoo3U9b_gbFA2KBdWYCAjGEgVsteXYYH3JoIzlV_x88izgOIffbV-xKLUv2kekXssihgQY6j4-gtOTzxtV5ssSUiKjTDRL-zevRK6ZCiHUfoMD.png) 
            - Traffic Engineering with BGP
                - How can you do traffic engineering inside and outside an AS?↓ ↓ 
                    - Within an AS, you can tweak metrics on the link state protocol to change the routes however we like. 
                    - At the BGP level it's much more course grained, and we don't get to tell people about real performance metrics (other than AS hops). We **can **tweak attributes for outbound routes to get other people to do things we want. 
                - How is BGP route advertising different from link state flooding?→In BGP route advertisements, not everyone receives the same information and the information is not sent in a timely manner (necessarily). 
Routers may filter out AS's that they communicate routes to AND routers may wait while they perform some computation before forwarding a route. We don't want other providers to steal our customers.
                - Does traffic always follow the ASPATH? Why or why not?→No, an AS along the path may decide to filter routes with a destination with a specific prefix or for too specific subnets (to not pollute the world with a very specific prefix and increase routing table size) - in which case the route will go another way 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/0Uh_AlU3hFGmw-FdWs_gR5fSQyDgpG_xNIyCfGD_Z0eFEezFQcMSoz2oIOQJbNyDkIQsmlNuDzDeVVB9AfUF1P_5RgssQ1-n_88LQJ8-kzwGzruTbb7gvi6ranH8qcOY.png)
    - Lecture 6 - More BGP
        - AS Graphs depend on Point of View
            - Peers don't transit for other peers - they transit for other peers **customers **into their customer base or upstream into a higher tier network - but they don't transit for transits sake.
            - What would the network look like for router 4 here and why?
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FtRKtTZVNoZMs_oP8vfpPcc0dPMRky42qSvc0IOk9meqtGXUyM0YASq2hDG6b2VX4JZqHFOLa9hBVwS8gygb8wBprB2SJJiRQuseATVbiFlGYeRkiCKDr6i9fPAta0IT.png)→It would look like this: 
You can figure this out by simply following the routes to each node. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gFWR4jkTpYwdEGb6qyONemLOaYKxEWSzS4-kwNso_4GzpiUMRqJJ6Lo3uQSpxHCOuJ2dNZmP5hUczAq8wB7d3eAfLUZla8fTEKqleVXfsugDziIjBmxS79IQJkO2SR4A.png)  __**
Because **__ peers don't transit to another peer, **unless **that message is going  __directly __ to one of that peers customers! So 4 could never have a message go from 1⇒2⇒3, because 2 would be a peer who's customers we **aren't** directly accessing! 
        - Implementing Backup Links with Local Preference
            - ISPs want **high redundancy** to allow for **high availability**, especially to higher up networks. So you will have backup links. You would like to control such that all traffic goes by the primary link unless it's broken - we can do that with **outbound** traffic, using local preference.
            - How can you manage inbound traffic in BGP?→Note that the ASPATH is a tie breaker between two equivalent routes, so at the backup link - we add the AS number multiple times to the AS_PATH. This is called ASPATH Padding and it's a ridiculous hack.
So for an AS 2, the primary link ASPATH = 2 and the secondary link ASPATH = 2 2 2
            - When does AS_PATH padding not work? What is the hacky solution to this problem?↓ ↓ 
                - If the path via the primary link is via a peer, while the path to the secondary link is a customer - the AS will prefer to send the traffic via the customer than the peer!
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bD70GK60HIpe3RiSnDQlpaX3kOaRhy9NhPWmFO4vrS3CM4wjDKp0PJ3aGLyaQqroU3_0VwxG667CcqVKnbarwkO3Mk4Iu1M7G_Kvuo4SGfd2Ab7bgk5fHbAvs5tS0i7i.png) 
                - The hacky solution is to call up someone at the other AS, and agree on the meaning of certain COMMUNITY attribute numbers - you agree on a mapping from community numbers to preference, then paths along the backup link will be given a community number representing a low preference. 
This is up to the other AS though...
            - What is hot potato routing and what's the problem with it?→Choose your egress point based on the IGP distance to the two border routers. This could be bandwidth based, latency etc.
                          ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qrBwh17_QZz0_DDmRV6mgmMontTE-mzYW4vytrzTDsOKFuQZEX-r9aQ2uA3CRNJ5MSRW8hABfK3HTG3XjxMrT5GrgMIYUNuKdHAczITfUJaXxGEsUDmRtHawUtARWMzT.png)
The problem is - that border router could be much further from your end user:
                       ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vABVW7E1OB_-C1jdFKityitQcp8v-PWqKg9b0lRgnGJnk3BKIkLiYxHbmEtM6z9mtzCtg5qPB0_Ygc6xr_AO7YnrY7BpbR2As5pAt-nIa6WJe8newQYQLQzdexdElVyg.png)

 
            - How do you control for making sure messages are symmetric AND why might an AS not pay attention to this control?↓ ↓ 
                - You can alter the MULTI_EXIT_DISC attribute and make the router your sending via have a lower value. It would make sense to link the MED to the IGP distance, but it's not always done that way. 
                - The AS now needs to consider the MED you've set **before **they consider the IGP distance - but that might be too slow or inconvenient for them, in which case they'll ignore your dumb ass. 
            - What is route pinning? What's the problem with route pinning?→When you have a primary and a backup link, if the primary link breaks and then recovers - some traffic will be pinned to the backup.
You could have a contract in which you say **you'll only use** backup link if the primary link fails, which you'd now be breaking. 
            - BGP is not guaranteed to converge to stable routing, it can {{livelock }}and oscillate. Furthermore, BGP **is not guaranteed **to recover from {{network failures}}. 
            - Describe the stable paths problem→The stable paths problem seeks to ensure that every node on the network has **one **path to some root node, while maintaining reachability. For example, here we have multiple routes to the root node - and we make a decision on routes that maintains reachability.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yGh-m5LwaOJ8MacaGodWIFYZr9A_fc-Mzptt2cEFzuIarOfANsmKIJ-LZ6RzYnZTPVXQnkHOpiA-VDIEQB2d33CqsLtAB4X4pWwSxd7H_ObH7uLONaEfd81qd9f0sr5K.png) 
The SPP can have paths that disagree, and you'd better choose the solutions that agree:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5McD2tw6zfMlBE6O8BU24xZJDrJdhZLtLLMH0YQKcM6Mc38UUhmGm-qOQANSP_C2FNMfJzX2wnuN35GdC0Eo0ie0o1Z2m6C4qpoBZ6WxD2kidTe14nOdJakNlNAYdCaw.png)
            - What is route triggering in the SPP?→When the primary link fails, paths along the secondary link are called upon and then both paths are in use when the primary link recovers: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/hCOztBEzTdw4oMTuaoNftVcU8bdT-7ZlQed2-V1w-Oh-vrMQ5Ggt7W-vD47KRKpFxWGoC7Y1d4b2YBlhbEYeE5cgoManN05JD1KLtUDoQVIwMrpSVKKZc-Ls0Bg-RiyL.png)
            - What is the bad gadget, and what do ISPs do to avoid that problem?→The bad gadget is a topology in BGP in which **no stable paths are possible**. I.e. no path where everyone has a set path **and **all nodes are reachable:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/TJF-iIF_I0DHY6K7bzqoRAmOEYimDZE9njD3m0IHMebRahb5IlcEy7I_bStqJ-ThG6O1-HVfXAtkFmstG9ZTX8-VU_hvpvdxBD4wHKC3uZi4Fd2-wU8yp_9BYVRBcjDd.png)
This topology can happen in the real world, and to combat that ISPs communicate extra information about BGP. The problem with BGP is that it's information hiding, so ISP's don't see this topology until it's too late - so they communicate extracurricularly (for this and security reasons)
        - Current Internet Growth Trends
            - Why does the growth of the internet affect routers in BGP? What could solve these problems?↓ ↓ 
                - Routers must store best routes and alternative routes. 
As the internet grows the becomes increasingly cumbersome to store and access quickly, especially for things like reflector routers - for iBGP you can form some hierarchy wherein you aggregate IPs together, but you cant do that in BGP.
                - If the routers die, a large CPU load is then required when calculating alternate routes - and that takes time, time in which certain IPs can't be reached.

                - Fingers crossed on Moore's law for the CPU and memory growing for large routing tables.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/1S9Je7BJWMUfClZO_23nZKQ2Hc2-MdbzhpAQKrYYaGbH4UG5IuKlGaw4VBImdDAFD4f15AZhIoB_-1eWn0JnWSZ_DFGDFcbWJ6pg2JkNyCXNGhTqwcJsEwDmLsdTPHHw.png)→TODO 
            - What is route flapping, how do you solve it in BGP and what's the problem with the solution?↓ ↓ 
                - When a route is advertised and then removed constantly - could be due to a flaky cable at a router.
                - You could Rate limit on sending updates - send a batch of updates every 30 seconds, a router might change it's mind many times in that time. Similar to keyboard key de-bouncing. This can really slow things down, because the 30 seconds is not synchronized between ASs meaning the update can take a long time to propagate
OR, route flat dampening - punish routes for misbehaving and dampen them more because of that - i.e. ignore them more and don't listen to their foolish updates.
Penalise , and decay the penalty exponentially - when the penalty score exceeds the suppress limit stop sending the advertisements.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5gJGPwwHzusO1wO5rfdsFBEDNmphDMpxvrXWrnq7O8KC0N1s1HsRtxTuJ888UGxUgfP0XS9EArxv-FbTFEoZUhDck5ZTNHUfyNOoiNdSZEQfmXEWOhgsGpRKNx9QG09c.png) 
                - 
        - 
    - Lecture 7
        - How can IGP export internal instability to the world?→IGP tie breaking means ASPATHs can change when flapping is occurring (this could be due to faults, or due to internal rules). This changing ASPATH is then exported to the outside world.
             ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/H5qwmeolhGBgs9BLbzkh9Wmva3vypWuEfcDxN3FakBHS2LQVA2UfK-2Cr4bdVJquJ72pL-iwqRJC2nrncGOqOaR0mialwcu_LCHUBnDCGUAxq5wdg4lf1BbT4linVhkJ.png) 
        - Multicast routing
            - What are unicast and multicast? And what are the uses of multicast ↓ 
                - Unicast: Single source sends to single destination, specific interface going to specific host
                - Multicast: Hosts are part of a multicast group, packets sent by any member of the group are received by everyone.
                - Useful for multiparty videoconferences, radio & TV over the internet, distance learning, resource location (send a message to all printers and get some answers) etc.
Consider, for a streamer with 10000 viewers sending 1000 to each person per second - you need to send 10,000,000 packets per second if we used unicast.
            - Multicast group
                - Associates a set of senders and receivers with each other. Senders do not need to know receivers' identities. 
                - You need to have a mechanism for advertising groups, joining groups etc.
            - Addressing
                - Multicast groups have their own Class D address, it looks like a host address but isn't and indicates part of receiver set.
                - Senders send to the address from their normal unicast source address. Receivers in the world request packets from that address.
                - **Need to solve:** 
                    1. Find which groups are currently active
                    2. How to join a group
                    3. Discover the set of receivers in a group
                    4. How do we deliver data to members of a group
            - Expanding Ring search
                - What is Expanding ring search?→A way to use multicast groups for resource discovery - you set a TTL and multicast which reaches all receivers <= TTL hops away. This allows you to discover local resources first, which helps you decide (for example) which printer to use.
                         ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ETGQ6ELLZFD5F7IA68eC3djmXY4oa0HHqSUiKQ88CGynQ-o9CW7DtdovwtyfFtpoK0233UxM9Q47p47JFIXskrQ4OJESOacLJ_UaVcO4ZykCPEsBoTA5xyjO1ikYOfad.png)
            - Multicast flavours
                - When would you want point to multipoint vs multipoint to multipoint? ↓ 
                    - Point to multipoint - one sender with many recipients (Single source) is useful if you're trying to mimic broadcasting.
                    - Multipoint to multipoint (Any source multicast) - conference calls etc, where anyone can send to everyone.
                    - Note that you can simulate one with the other, but it's a matter of efficiency. If you're sending the same packet multiple times, then that scales with the number of messages. However, if routers can decide to duplicate a message then only some routers will receive and send multiple message - grows with $\log M$ .
            - Problems in wide-area multicast
                - Sources can leave or join dynamically - meaning we need to dynamically update our shortest path tree. We'd like receivers to be able to join or leave without explicitly notifying the sender, otherwise this won't scale as we have the unicast problem but with receiving rather than sending. 
What about leaf nodes of this sending tree makes this easier?→Usually those leaf nodes are broadcast Lans/ WiFi networks, these networks then blast the message out to their users who can then either accept of reject the message.
            - Multicast in a broadcast LAN
                - We can map between the multicast group and the physical layer - mapping from IP address to the{{ MAC address}} - Ethernet will multicast all packets with {{multicast bit }}set on a destination address. 
            - Group Management Protocol - IGMP
                - Describe IGMP Internet Group Management Protocol) ↓ 
                    - Detects if a LAN has any members for a particular group - if not we tell our parent who can then prune the shortest path tree
                    - Multicast capable routers periodically ping the local net, with a query message asking if they want to receive group messages.
                    - Hosts reply with a list of groups they're interested in.
                    - To suppress traffic, replies occur after a random timeout and are broadcasted - if someone else has expressed interest in a group, suppress your response.
                    - Then to receive multicast packets - translate from class D to MAC and configure NIC/adaptor 
            - Wide area multicast
                - Assume each endpoint is a router that can use IGMP to discover each member in it's LAN that wants to subscribe.
                - Simplest solution
                    - Flood the packets to the whole world. It's simple and always works, but routers receive duplicate packets and detecting if a packet is a duplicate requires storage which can be expensive for long multicast sessions.
                - What's the difference between flooding and broadcasting?→From my reading, it seems that broadcasting sets the MAC address to ff-ff-ff-ff meaning switches read that, check their lookup table and find it's not there - at that point the switch will send the packet to all it's ports. 
While in flooding the switch receives a MAC address it doesn't have in the lookup table, so it floods because it **doesn't know the destination**.  #[[To ask Supervisor]] 
                - Reverse path forwarding
                    - What is reverse path forwarding? How can you extend it?↓ ↓ 
                        - Method of broadcasting where we check where the packet came from, if it came from the shortest path (we assume the network is symmetric) then we forward it to all other interfaces - this way we don't need to remember past packets
                        - Additionally, don't forward the packet if you're not along the shortest path from the downstream router to the source. This can cause confusion if the downstream router has a choice of shortest paths to the source.
                - Pruning
                    - What is pruning, and how does it help RPF? ↓ 
                        - Each router tells its parent in the tree to stop forwarding messages for a certain group - i.e. after you flood, the information burden is split among many routers - as many routers are parents.
This trades router memory for selectivity.
                        - Reverse Path forwarding does not stop all routers receiving messages they don't need, consider:
                              ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6no7Jog66jmPaC3cSOIUYwQNfTDG7GG99QOb8UwvcKwhUIAdPF2SOp6oOkqHmNESX2F1WNASjdcEKw1JilGAPN_Bbgs9TzzhF6buew52O40EhW8JhoHHvPMbkR1yzX0o.png)
                    - How can a host on C's network join a group after being pruned? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/BsxSIXBqE1dVQzQCI5rjGrREyq61CI0acsCayy35YCI3D3zm68fe5zekJDvfUpUPoNrAFXf3psgfPca4kITBW5E12yhmySuyDhMYaSyMbyC-UXvbte6VlpDerno0Jn4k.png)→IGMP lets C know of the host's interest, C can either:
 ⇒ Send a join(group, A) message to B which propagates it to B
⇒ Periodically flood a message; C refrains from pruning
                    - Need to decide how long to cache information for.
                    - What do you do if a router does not support IP multicast?→Form virtual links between multicast-capable routers - meaning the shortest paths are via those virtual links/tunnels:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Sm9cxq3tqeKIAza6nKBZ5EeRIV6GfgjjoYI3o5C8Rv7WoePlksMAWEnvzAtROyW_-PUpDIyG7FGa9Z_6gNFMMc-THFb32vUzvFpf0G9rYKGbVvoVoORsfRkF7_Y8YULK.png) 
Routers need to calculate shortest paths, only taking multicast routers into account.
                - DVMRP - Distance Vector Multi-cast routing protocol
                    - Rely on existing path computations, and look at them backwards. Look at the source, and forward on all which aren't the shortest path to the source. 
                    - Only takes multicast capable routers into account. 
                    - Uses flood-and-prune to determine membership, 
                    - Uses RPF to decide where to send a packet, 
                    - Uses explicit join messages to reduce join latency without source information, so flooding is still required.
                - MOSPF
                    - How does MOSPF work, and why does it do what it does? ↓ 
                        - Router floods group membership information with the Link State Protocol advertisements. Then each router independently computes shortest-path trees that only includes multicast capable routers. 
                        - Routers then compute a shortest path from the source to all the recipient routers in a group. Run once for every group.
                        - This is done because we want complete knowledge of where the group members are. You don't know this with regular multicast and pruning.
                - Protocol independent multicast
                    - People send join messages to a core. E.g. the IGMP traffic
                    - Fault tolerance - multiple cores for the same group. 
                    - Two modes of PIM: 
                        - Avoids the flooding problem, for dense groups we might as well flood and prune. 
                        - Sparse mode, Core Based Tree used.
                    - Could still have issues with denial of service.
    - Lecture 8
        - Mobile Routing
            - To main questions ⇒ How to find the mobile host? How do we get to it? i.e. location & routing
            - Mobile Cellular Routing
                - Describe how cellular routing works?↓ ↓ 
                    - Base stations are arranged in cells, these cells work at different frequencies so not to interfere with one another:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/94cIy7_VJMWAzt5WuQhSWjq21rglQ5Gt-FYzEFCkvkl9EwDFVVhkDKEptUlL0Eas0nbj5z_VIhl_SbhKjX35dpDxQPywIbuv4MWwJLL06p00eeoRk0_CQp88iGN3Fn0-.png)
                    - Each cell phone has a global ID that it tells it's remote MTSO (mobile telephone switching office) when turned on and periodically from then
                    - The Remote MTSO tells the home MTSO - this home MTSO is the one your phone is initially registered to and is owned by your ISP
                    - Calls  __to the phone __ are forwarded to the remote MTSO and then to the closest base station. 
                    - Calls  __from the phone __ go from the closest base station to the remote MTSO and then to the home MTSO. 
            - Mobile routing in the Internet
                - Why do we have to create a tunnel when you move and change IP, why not just change your IP?→Because TCP carries a checksum which requires your IP. So if you change IP, the TCP connection will break. 
We can't just get HTTP to restart the connection, because it would require some endpoint/identifier that had stayed the same. (Note this can be achieved with HTTPS and TLS with an identifier)
                - Very similar to mobile telephony
                    - but outgoing traffic does not go through home, need to use tunnels to forward data.
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-N83Hduus8cCtDYmWbbJEZErIuEXUiAS0h9-f9Hm97xRLskepoXCk04kdTcdWSC6EE4dIoxrNyYd5kE0fLRXZ31j6QfeNMci5QPeuBnlRfJu--6PsetEo2aXrCrH5Iof.png) 
                - Security is tricky with this, mobile and home address agents share a common secret which is checked before we forward packets.
        - Routing in Telephone networks
            - Telephone network topology 
                - Describe telephone network topology↓ ↓ 
                    - Telephone networks have a 3-level hierarchy with a **fully connected **core.  
                    - Phones connect to central offices, these central offices are connected on a local exchange system which is connected to the core network (national phone network - connects every city to every other city).
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mywpM82a6lSQX93QOJC76wUk8ry2qbx2f6pHkhspilv_5vHkvpT3woJz61gpHf0YJwnnIk5uknss4kb69S8HG1vCZhxJdKwZah_3g0oHqyZOgJt2Scapox-aA_P9Nntm.png) 
                - ATnT used to set up telephone poles in the US, and as a result it was the biggest lumber company in ther world for a period.
            - Routing Algorithm
                - Describe how the telephone routing algorithm works for the different levels of the routing hierarchy? ↓ 
                    - If calls are within the same Central office, directly connect the circuits.
                    - If the calls are within the same local exchange, find a one hop path between central offices.
                    - Otherwise we send the call to the core, we use two-hop paths if a direct connection is full. We decide on a two-hop path by 
                - Describe the features of a telephone network ↓ 
                    - Stable load - we can predict the pairwise load throughout the day. Note that further longer calls cost more money, so short local calls are common.
                    - Extremely reliable switches - downtime is minutes per day
                    - Core is controlled by a single organization, so we can see all statistics of its use and use them to make predictions. (Not the case for international calls)
                    - Calls require resources - but all calls require the same resources
                    - Very highly connected network
                - Statistics used for telephone networks
                    - Poisson call arrival for the {{Independence assumption}} 
                    - Exponential call holding time, due to {{distance and time related billing}}. This is not the case for the internet. 
                    - We seek to minimize call blocking probability, subject to minimise cost of the network. However, demand changes over time - e.g. on New years eve or mothers day.
                - The cost of simplicity
                    - Simplicity of the routing was necessary for debugging, and because only 8 KB of memory was available.
                    - We still require reliability in every component, and a logically fully connected core.
                - Dynamic Non-hierarchical routing (DNHR)
                    - Describe DNHR and it's main problem↓ ↓ 
                        - Divide the day into ~10-periods
                        - In each period, each toll switch is assigned a primary one-hop path and a list of alternatives. These alternatives are calculated offline based on traffic predictions.
                        - Only overflow to the alternatives if the one-hop path is full.
                        - Drop only if all alternative paths are busy.
                        - Doesn't work well if the traffic differs from prediction.
                    - What is metastability in DNHR?→If many calls are routed via the second-best route, when the calls on the one-hop route end we don't switch back to the one-hop path. 
We don't have the capacity to measure and do something clever.
                    - How does TSMR improve on DNHR?→While DNHR measure traffic once a week to update secondary paths, TSMR updates once an hour - meaning the list of alternative paths is more up to date. 
                - Real-time network routing
                    - Describe real-time network routing in the telephone network. Give an example of how it would work in this network to get to B.![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/xxTGfXbdokR7FNAtLzjeKKN81V4eAC4WRVlCky0Uw6O6eP6EnmBmosh4n2NaFbGqK7ILWzSvikXz5kpMdvpOPuk7OnQs__cXCppqVNOhpRHrqQoC9AEtTEawdLenEKR7.png)↓ ↓ 
                        - This system has no centralized control, instead each central office maintains a list of lightly loaded paths. It then communicates with other central offices to find their lightly loaded paths - the intersection of those paths gives the best routes.
                        - E.g. A has a list C D E of connected offices, it knows the AD and AC are lightly loaded. It communicates to them both, D says DB and DE are lightly loaded - we then find the intersection. AD DB ⇒ ADB lightly loaded and is a good alternative path.
                - Dynamic Alternative routing
                    - Fully connected network with a relatively small number of nodes (e.g. 50 cities). Stochastic traffic, low variance when the link is nearly saturated.
                    - Describe dynamic alternative routing:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/A8CYYeFqOB2dZ49if0VubQ3U9LDlF_objagZf4in4Wx4Td89pxwqIL9aVF0upDNd9CT92ok18OsZvu7Zywmd3vAkBYErYv-Hos0etiIVbj2FBcJspHoP1GkB5EXycfUE.png) ↓ 
                        - Whenever link (i,j) is saturated, choose a tandem to go via.
                        - We could do fixed tandems, but it is inflexible during breakdowns and unexpected traffic at tandem.
                        - Instead we use sticky random tandems - if there is no free circuit along ij - pick a tandem at random and keep that as the tandem as long as it does not fail. If k does fail, the call is lost and a new tandem is selected.
                        - Trunk reservation is also used, we bias against using the two hop path by penalizing two link calls when the lines are busy. A tandem k accepts to forward calls if it has free capacity more than R.
We don't want to block calls going from k to j because we're going ikj
                    - Erlangs Bounds
                        - A node connected to C circuits with a poisson with mean v:
The expected value of the i-th call blocking is
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_5_6b-ItUo5qLY0pGC0uA0KvfRhFkIewp5FW6Lg5VAUNveZcQG5-3lceOFzTGZNMG62SgyPzoeKk3bj6-x-C-DGj9Td11gxKhYblOiXlFr4La3hlDSNRhGUWSmHpsRgv.png)
                        - We can bound the max-flow to find the capacity we get from the two-hop paths. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZlZk_38Ve87nGWLzsEP5NnDe2y1Bocu5ehR33LTUfYswOUQR4BFdZHW8FI2vHVY0k0tTVnJriRwv7gMPKWq39lUFi0HtlQlhtJMzh7ODYxQo5YqYSPRIYZMwQ4IjmAjf.png) 
                        - 
    - Lecture 9 (Flow Control)
        - Flow Control
            - Senders and recipients have different capabilities, you want to match the rate at which the receiver and network can process data. 
            - Sending too slow wastes time, and too fast leads to buffer overflow. We seek the find the correct rate.
            - How do we find the correct rate?
            - Considerations 
                - Simplicity
                - Low overhead
                - Scaling
                - Fairness between different apps and users
                - Stability
                - Generally tradeoff overhead for stability or simplicity for unfairness.
            - Usually done at the transport layer, ocasionally in the datalink layer.
            - Our model is a source, sink, server, service rate, bottleneck and RTT
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vhFqZO6ZmqUKNbaP9zCwhqwQEK5LPkATaA6GylaMtvtCzVQo3YA2az9scqybeFi9NEAsWG76KAgvgk7HqfVCSO6d4FcPsXpSdaLOLGuim3TzuBa6tysTa-H-pkwCHEOT.png)
            - Classification
                - What is open loop flow control?→The source describes it's desired flow rate and the network decides if that's feasible and admits the flow
                - What is closed loop flow control?→The source measures the available service rate and sends at this rate. Due to speed of light delay, errors are bound to occur. 
                - What is hybrid flow control→Source asks for some minimum sending rate, which is admitted by the network. It can then send more if available. 
                - Describe first-generation vs second-generation flow control ↓ 
                    - The first generation **only matches the receivers rate**. It's not responsive to the rest of the network. 
                    - Second-generation polls the network somehow (whether explicitly or implicitly) to determine how it should adjust it's rate. It can be decided whether the controls are enforced on the endpoints or within the network.
                - Open-loop
                    - Describe the two phases of open-loop flow control ↓ 
                        - Call setup: 
Network describes the parameters, the source chooses from those parameters and the network then admits or denies the call.
                        - Data transmission:
User sends within some parameter range, the network polices users and scheduling policies give users QoS. 
                    - Descriptors of flow
                        - How is traffic described in open-loop flow control?→An envelope is created which describes the worst case behaviour. This envelope is used as a basis for your traffic contract, and as input to the sources regulator **and **as input to the network policer. 
                        - Descriptor should be:
                            - Representative - adequately describes the flow
                            - Verifiable - we should be able to verify that the descriptor holds
                            - Preservable - it doesn't change through the network in an arbitrary way (if buffering occurs etc. should still stay within the envelope). I.e. doesn't break due to some scheduling done within the network.
                            - Should be usable - easy to describe and use for admission control algos
                            - Time series of interarrival times is representative, verifiable - but it's not usable (too slow).
Peak rate is verifiable, preservable and usable but **not representative.** 
                        - Describe linear bounded arrival process. Where does it struggle?↓ ↓ 
                            - Source bounds the number of bits sent in any time interval by a linear function of time
                            - The number of bits transmitted in any active interval of length t is less than $\#b < rt+s$ ($s$ is a burst).
                            - $r$ is the long term rate and $s$ is the burst limit.
                            - Struggles in multiple time scale traffic -  basically means when the quality varies quite often. E.g. in a movie going from a a talking heads scene to an action scene. Either the quality dips or the connection ends. 
This can be helped by changing the renegotiation time, e.g. every 5 mins we change our r and s depending on what we're doing.
                        - Describe the leaky bucket regulator for a linear bounded arrival process→Tokens arrive periodically in a token bucket, and a leak in the bucket means the packets drip out periodically in small "bursts". Goes from periodic bursts to continuous predictable drips of packets. These packets are sent out at the mean rate.
If packets arrive at a rate that overwhelms the bucket, those packets are dropped.
                        - Choosing LBAP parameters 
                            - Tradeoff between $r$ and $s$. 
                            - We want to find the lowest loss rate as we adjust r and s, we choose the knee of the curve:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/V1vR3HY1IvSFkbdtx3ATRugfragBFTDA-CAyryRhoW-ioJ3MSnU8A8pJP3nD2tTpMJjAXGAVn2BA9-v5vFYCuPU80dkxNNAWwnH8NAO7Ny6IVs60SyR0vA3dcNegMgoj.png)
                - Closed-loop
                    - Useful when we can't describe the traffic or the network doesn't support reservation (e.g. internet)
                    - Monitor the available bandwidth and adapt to it as we go.
                    - If not done properly we can have too much loss or unneccesary delay.
                - Explicit and Implicit Flow Control
                    - Describe Explicit flow control ↓ 
                        - The network tells the source it's current rate
                        - You get more control at the cost of more overhead
                    - Describe Implicit flow control ↓ 
                        - The source measure the network to find it's current rate
                        - Less overhead than explicit but at the cost of accuracy/effectiveness
                    - Flow Control Window
                        - Describe the flow control window ↓ 
                            - I can have this many packets in flight **before **I receive an ACC - adjust the window as we go. 
                            - If the window is full we slow down the rate. If a packet is missing that can tell us the network is congested.
                            - We note the missing packet, thus the window provides  __both __ error control and flow control. 
                        - What should the window size be?
                            - How do we figure out what the window size should be?→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/PsSV2Lp3kBtpvuIFOhsgYbmbSYErxWMcFthUEnRLK8Drya_z4W0c1ZcFTQvmJbrTuWZPz77ppC5LtbMLZvxdWlV7sBAHn195FS_vbhXwZ8iXD0oYZs5l2Pki6z3czlFD.png)
Basically computing how many packets we can send before we get a response with the bandwidth delay product. 
                        - Window vs rate
                            - What is adaptive rate and how does it measure up to using a window for flow control? ↓ 
                                - We directly control the rate, and we have a rate **per connection**. E.g. if the receiving connection gets congested we decrease the rate. 
                                - It requires a fine-grained timer (window control does not) and it's not self-limiting (as the window is).
                                - It does have better control than the window and it doesn't couple flow control and error control.
                            - Initially static windows were used, good if R and b are static.
                            - 
                            - What is an On-Off protocol and where would you use it? ↓ 
                                - Receiver gives ON and OFF signals, when the signal is on send at full speed otherwise stop.
                                - When the RTT is very small this is all you need, i.e. in a LAN or a serial line. We don't need complicated windows as the bursty signals will only build up for very a short amount of time.
                            - Stop and wait signal - send a packet and wait for an ack before sending the next packet
                            - Describe DECbit/ECN flow control→Every packet has a bit in the header which represents that a queue is building; routers set this bit when their buffer is starting to grow (doesn't have to be full). 
This is reflected in the ACK the sink sends, the source can then reduce it's window (and increase when the bit isn't set) to oscillate around the optimal size.
                            - How does the router decide when to set the bit in DECbit/ECN flow control? ↓ 
                                - Measure the demand and mean-queue length over some period for each source. 
                                - Then if the mean queue > 1 then set bits on that source.
                                - If the mean queue > 2 then set the bits on everyone because the queue is growing very quickly
                            - How does the source change it's window depending on bits in DECbit/ECN flow control?→Additive increase, multiplicative decrease. If more than 50% bits set then multiplicatively decrease the window (because we're hearing about this a RTT late, so more needs to be done now) - otherwise add some number of packets to the window size. 
                            - DECbit/ECN works with FIFO but **assumes cooperation! **Conservative window increase policy. 
                            - Describe how TCP congestion control works ↓ 
                                - The window starts at 1 then increases exponentially until we hit ssthresh, at which point we slow to linear increase. 
                                - The exponential portion (so called slow start) **increases by 1 at each acc**. You might think this is linear, but for each full window worth of packets sent the window will **double in size!** 
                                - The Linear portion increases the window by 1 whenever #acks = window size. This linear phase is called congestion avoidance
                                - If duplicate acks are received, we halve the window. If we get a timeout packet loss we set our window to be size 1.
                            - Describe the weaknesses of TCP↓ ↓ 
                                - Loss doesn't necessarily imply overload but TCP assumes it does - on wireless connections especially this assumption is flimsy.
                                - If the network is overloaded, TCP blames it's own connection and penalizes it heavily when other flows could be to blame. 
                                - Overload is **only **detected on a loss 
                                - Needs at least bR/3 buffers per connection
                        - Hop-by-hop vs end-to-end
                            - What are hop-by-hop and end-to-end flow control ↓ 
                                - Hop-by-hop: First generation flow control at each link, easy to implement. I.e. router to router the flow control is based on the sink rate.
                                - End-to-end: The sender matches its rate to all servers on the path
                            - Benefits of hop-by-hop flow control ↓ 
                                - Simpler
                                - Distributes overflow
                                - Better control
                            - Benefits of end-to-end flow control ↓ 
                                - Cheaper than hop-by-hop
                                - We know it works as it's in place currently
            - 
    - Lecture 10
        - Traditional Queuing behaviour in routers
            - How did queueing traditionally work in routers? ↓ 
                - Most boxes use the most naïve method of scheduling possible, no recognition of flows. Nothing explicit to tell you one packet is more important than another initially - you could infer some data but thats it.
                - Forwarding did not examine the type of traffic for priority.
                - No examination of traffic patterns.
            - We'd like an alternative to FCFS - going through the same interfaces can cause queuing delays and delay variance (and packet loss at the extreme).
        - Scheduling
            - Service requests at server is the packet at router inputs. The service order is the order we handle service and schedulers decide the service order and manage the service (output) queues.
            - Scheduler decides which output queue is serviced next.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sY2-Dp8YzwYCC8Ag5U95Yt9eyhzy8dB5dGMtwPU6pW70i1AIIQCDaSgA5qj5bf-wOqKGcKUwSJRJKHj9t92l0W5fw4v-Cwv97JEjbJhjzFqIsLVZrhVRgXpQRd50alsk.png) 
            - FCFS Scheduling
                - What's the main problem with FCFS scheduling→No differentiation at all between packets. As a result **no notion of flows of packets, **but lots of the internet uses TCP flows. 
                - FCFS is a **work-conserving **scheduler. 
                    - What is a work-conserving scheduler?→This is one that doesn't idle if there's something to send - if there's work to do do it. As opposed to hold a packet until some due date.
                    - What is the benefit of a work-conserving scheduler→Means we **don't waste network capacity.** No artificial delay added, we can't give  __all __ flows a lower delay than they would get under FCFS.  
                    - $$\sum_{n=1}^N \rho_n q_n = C$$ 
                    - What is the law this equation represents? What would happen if change one flow some way?
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zKc9xAlr96Iv9_nBbmWNzcw5VqjP8DWlfw1AjyVsYHjZ9SS5tKiHPNRum0CtWTFpB_IdTQ8jPIMLXQrEeBy1uI8ut6T6cX6KNjDHBzKjB94jDFLaj8gdaWEy0lqSIiSh.png) ↓ 
                        - Conservation law - n iterates over all the flows and the constant C remains the same.
                        - The conservation law says that changing the rate of one flow will keep C the same. The other flow will just slow down. You would need some clever scheduling trick. Trade-off delay and throughput.
                - Non-Work-conserving Scheduler
                    - What is a non-work conserving scheduler?→Can be idle even if packets waiting - allows smoothing of packet flows.
                    - How are non-work conserving schedulers created and what are 3 benefits and 2 downsides?↓ ↓ 
                        - We wait until a packet is eligible for transmission, eligibility is some fixed time per router or across the network.
                        - Less jitter
                        - Makes downstream traffic more predictable - less bursty
                        - Less buffer space - end-system de-jitters buffers
                        - But higher end-to-end delay
                        - And complex in practise - how do we synchronize time on these routers
                - Scheduling Requirements 
                    - What are the 3 main requirements for schedulers ↓ 
                        - Ease of implementation
                            - simple ⇒ fast. Implementation in hardware. High speed networks
                        - Fairness and protection
                            - Local fairness max-min
                            - global fairness maybe
                            - Protect any flow from the misbehaviour of others.
                        - Performance bounds
                            - Can we determine the delay someone will get
                            - per-flow bounds
                            - Deterministic / probabilistic
                - Max-min fair share criteria
                    - Describe max-min fair share criteria→Those who demand the least will get what they want - when there is not enough left to fully satisfy any flows, they all get a portion of what's left.
C=10, demands = 2, 2.6, 4, 5 - we give 2, 2.6, 2.7, 2.7 (sums to 10)
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZOCa2jScuez7-pSRd9vPM1Xzxt-ST7AnM0lzujXsedpWFQE8Uu7Ou9xWxJ234226yhaQ0tEI3CcsZBuxjih7yrnJBvdjWCjkEJbrvwk9L3zHkUCMTqKs1dJa9X2Z5li8.png) 
                - Scheduling Dimensions
                    - Priority levels, higher priority queues serviced first.
                    - Degree of aggregation, all of Cambridge get's this fraction of the capacity. Leaves it up to the organization that paid for this aggregation.
                    - Work conserving or not
            - Simple Priority Queueing
                - Describe Simple priority queueing and 2 benefits and 2 problems ↓ 
                    - K queues, queue k+1 has greater priority than queue k. Could be router to router control traffic most important
                    - Very simple to implement
                    - Low processing overhead, Just work down the queues and service
                    - No deterministic performance bounds
                    - Starvation of low priority queues
            - Generalised processor sharing
                - Describe Generalized processor sharing ↓ 
                    - Basically visits **flows **round robin! This gives you a bound, minimum of $1/n$ of the share. Delay is bounded by $n-1$ packet delays. 
                    - Provides max-min fair share and is work-conserving.
                    - It's not implementable as it serves an infinitesimally small amount of data from each flow - we cant send one bit of a packet and we can't equal the amount of data sent from each flow as packets are variable length.
                    - Provides an absolute fairness bound - fairness of scheduler compared to GPS for the same flow.
            - Weighted Round Robin
                - **Queues are per flow** 
                - What is weighted round robin→Simplest attempt at GPS - weight queues according to demands and mean packet size at each queue. Then use max-min fairness process to dole out capacity.
                - Service is fair over long timescales, as mean is unpredictable and possibly unfair over short timescales.
            - Deficit round-robin
                - DRR does not need to know mean packet size.
                - Describe Deficit round robin ↓ 
                    - Each queue has deficit counter (dc) initially zero
                    - If a packet is to be sent, we check if the dc is more than the length of the packet - if so then send and decrement dc by that packet size, if not then dc = quantum + dc.
Quantum is the schedulers attempt to serve one quantum of data from each non-empty queue
                    - Quantum set to max expected packet size.
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/q1Y7Wme0KZPPH1VaHe3lFni62fKW_2fjGH-BfQ4oagJ9YIsK4uE1djHwsH32RH-AcDkA85wQxOQrDZfXFMYaL518ubtMJFQrpdWmcdmR3NrObE9GIufUihrSAYn4eXCu.png)
Pretty fair. 
            - Weighted Fair Queueing
                - Describe weighted fair queueing ↓ 
                    - Simulate GPS by serving packets bit-by-bit. Packets are tagged by a finish-number, we sort the queues (other data structures exist to prevent sorting) by the finish number and release those with the lowest finish number.
                    - If a new flow start or an old flow finishes **you need to change your computation.** Other flows can be completed faster, these flows then finish faster so R needs to be changed again! In the worst case we evaluate R each time a packet arrives or leaves. 
                    - Rate of change of flows could be pretty big, flows could be appearing and disappearing often. 
            - Class-Based Queueing
                - Describe class-based queueing.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/1yUe_qeveUIT2QoNC642q2v1LPAtxNZKZJI0omqzQKCIwdmHJiQ9tfVsWOu3t3NzHePgKVDk8zQo7RermNyWpbg1hm66UdwUq3-dZ0bbjiV0knRovMt0tn_8c2_G-Z9c.png)↓ ↓ 
                    - First into which link, then which organization, then if it's real time or not, then the application their using etc.
                    - Assign a capacity/priority to each node.
                    - Node can borrow any spare capacity from the parent
                    - Allows for fine-grained flows.
                    - Requires a scheduler.
        - 
    - 
- 🔣 Types 
    - 
    - Lecture 1 - Review of Type Safety
        - What are Type systems
            - Type systems are both an essential part of programming languages and an essential concept in logic & proof theory. Thus, they form a link between theory and practice.
            - Give some uses of types ↓ 
                - Error detection via  __type checking__  
                - Support for structuring large (or medium) sized programs
                - Documentation
                - Efficiency - if we don't know the type of a variable, if I say x + y, we need to go through a long set of if statements to decide are we adding two integers, are we concatenating two strings etc... (runtime test needed)
                - Safety
        - A language of Booleans & Integers
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tkr5fElVeLYKIQOMUxVMRM94h5UwB5bhAsu6w2DSFxmB_9eDL8n2Ph4h3n4X4IHQMKIg_wKJODvs-kUPtPnu3BV65Jjh7uVIhfaPT7Hei5wgPvmUdMQ1-XXmMbcpNXwd.png) 
            - To ensure our language adheres to our rules, we need to specify types. A boolean type and a natural number type.  $$\tau ::= bool \ |\  \N$$ 
            - Then we make a **typing judgement **like: $$e : \tau$$ 
            - We then define typing rules, that form leaves of a tree:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zfVr_AiB3KhveYPS79GlmcMh8mdFNcyB0zaZDBKJBG43CVef_1QxbEk0C62rQ45Ny96JgkRqNEtQT8rxVWbi-VyhYdhXSAqmxZZJ4SPTwz84nYEzpvDme3aAs19xrRvx.png)
            - We can then add variables into our language, what would we add to our terms to add variables?→$$e ::= ... | \ x\  |\  \text{let x = e in e'}$$
This binds x to some expression e in e'. 
            - The typing judgement must know what the variables are - we create $\Gamma$ which associates variables with their type. Note that gamma is just a list (called a **context**): $$\Gamma ::= .\  |\  \Gamma, x: \tau$$
We can then say $$\Gamma \vdash e : \tau$$
What does this mean in English?→This means e has the type $\tau$ under the assumptions $\Gamma$. 
            - We get the following variable rule, ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/F_R1Z6SLETKeffQbS9jODBlMBAK9r6_SJ-QeTf81agJbwXn1sc6xpWJw3DcBqQdvIRT0qRh3iBZ5GJR88ni_8FAgLgp75Dn4y9IBumwpsR_H3DMWr-67YmPBFQyPc0Mr.png) 
        - Substitution
            - We have a host of substitution rules:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7z217o87GnUFzFtn-XugNiGKIyxCBvEoqtXpbhhv4EpEeauV61UYwTXgEdnqiCdZ51p_6w4ud8EFQOrwjLrKdRkM8RQ0fPb1E2jX8MPF5Oy5agjqUI9pbzbBulEKO8eO.png)
            - What should the substitution rules be for these three cases![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/iSZ3h9azTciBO8AO3AOgZqD6Kq93o36mpok1qEvb7j2nsFWbLNIRKePhWYIdwY-piK1llCtqzDRp2nm1c-XQKTC4AGOPhpTKJ_xOMaM676hI-rQnjkVjGA32JLdFWxzj.png)↓ ↓ 
                - $$[e/x]e_1 \land [e/x]e_2$$ 
                - $$[e/x]z = \begin{cases} {e \ \text{if z=x}} \\ {z}\  \text{if z != x} \end{cases}$$ 
                - $$\text{let } z=[e/x]e_1 \text{ in } [e/x]e_2$$ 
            - Describe the **Weakening **lemma→Weakening is a lemma that states, if a term typechecks in a context it will also typecheck in a larger context (if the context's do not conflict, assumed to be correct).  
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ge7dyBt8lh6pkPn2yPpuAv14S690-il17Jy6yJ47b44thsuygAi8h8npYXPsvjnBocXO2ncs4LJOpQvxBhm77r7EBT0Fn1o8N0lBWwTHh2MjjOfrldJLvJ7Fdw1do5bY.png) 
            - Describe the **Exchange **lemma→Exchange is a lemma that states if a term typechecks in one context, we can exchange different items in the context and the term will still typecheck. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/iA7EWKqOSB2lBcFtNHNr5pIGwbZvWzZK-j-qkmCo9ldvFMp3_rkICGyn_uN6JfPkVUa6aFGz7zDU37zsg-7xM4dDPdbIhyfIzXXZ_Ot586UZl19wkFW-_Ufayr8CuGo7.png) 
            - Describe the **Substi****tution **lemma→Substituting a type-correct term for a variable will preserve type-correctness. E.g. adding a type correct variable to the context is the same as substituting a type correct term to the equation 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Zx2KkTdSOmqpVs4yYoCKTyccaJ0OoyxK6utssDsr5Eh6Nj7RUg8-POlRqI4RXDnvTr8dBYzW5ChYSGCsdnC7-_x7RFuRt1rfUtE0gLgyUjFmA01wTjxdPM31N4hVkIA8.png) 
            - How would you prove weakening via  __structural induction__ ? ↓ 
                - For every type rule we start with a derivation of a certain type.
                - We then assume by induction that weakening holds for any subtree. That is, if we are trying to prove $\Gamma, \Gamma' \vdash e: \tau$ then on any subtrees **we assume **$\Gamma, x: \tau'', \Gamma' \vdash e: \tau$ 
                - We then show that if the subtrees hold it holds for the root.
                - For example: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/uc-cet6AaDv6D8O4_rAzjfdcO5_c2Gx1L3jjWuHDqBTdldMtvMb8fvxWRSq3zcHKBxPwbnwAE2pNuzSU42UVh0fY2Zsg8XJjyhXmUv24CQyW2HfGxQsWNN8USZWehHTH.png)
            - How would you prove weakening for this type rule (Write out the proof, 5 lines):
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/dr4xpcqhttvTZdAMlWt6twFFuPhaqKqE7UfBJ4tnaDZEW-Tq0SUBPm3nVmaZqYfWDmq6pLZ6Rm1DGeujpDKi5-R9X6j3z_8XoIMyJkpTGgvmjJpMi7ZN7kId7LBm6P7r.png)→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/aDHDd709E9uOHKlxA2aSozhqht3M6B-IvBGMrFEnC0jidc_c4PCQacmC6UEiJWIUxrDEmnAzl45TYmINWxAN8UkvvZgtHRR06ihcOKGO2uDBmVcmB56IDB-lW7SiHfaC.png)
We first apply induction on the sub-derivations, then we use the fact that PLUS carries with it context when it is applied. Consider that this is the same as $x:\tau''$ being inside $\Gamma'$ .
            - How would you prove exchange for this type rule? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/wg89SxFoijEEkk58wMVgmcDZUu_s_X4Fe10C7PGNIRFzgH5hhnfVL_eLzmyKRKzawV_bQallFAQim1dLAGL84y_KUEIEzRovDfraXhFH6PZvWUBw1fy9VLnNTNU7HcMn.png)→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-latSCqcXefOwlxsDS22Rpm5VuwM0z7NSaM--_ogc6-GAoYskFK4Lk7h_pE-Nf-YYV1Wr9Tcwsfv9CacHQVfLukrGT0Fa-OfVR0oQ1KJXAUntTPnuQwZltFgY23aQjhy.png)
Note that $\Gamma', z:\tau_1$ becomes an **Extended context**. This means we group it into a single thing and it acts like $\Gamma'$. 
        - Proof of Substitution
            - In broad strokes, how would you prove substitution using  __rule induction__ ?→We start with a proof of $\Gamma, x:\tau \vdash e': \tau'$ **AND** a proof of $\Gamma \vdash e : \tau$ ( __this is what we're going to subsitute for x__ ) - we can then apply substitution on the subtrees by induction and we eventually build the tree that concludes $\Gamma \vdash [e/x]e' : \tau'$ 
        - Operational Semantics
            - We want to define a grammar to find the  __value __ a program computes, this is useful because we can then evaluate our real systems and decide if they obey our operational semantics. 
            - We define a grammar of  __values, __ and a two-place relation on terms $$e \leadsto e'$$
meaning e steps to e' 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tomVW9_1wf7CaPhKzhITenWyZx_ianI0fmZQraDlzNJeY0yud0pj7iEBvJUiZc5WJ7PoVDdjSNxj4Su8BVZ2gKV4dciURe_8thAornQrF6uBr38psiqrJr8gMRH0mQoY.png) 
            - A term e is  __stuck __ if it doesn't result in a value and there are no more reduction rules that can be applied to it. Thus a program is safe if→it never gets stuck. 
            - Describe the **Progress** lemma→If a well program is well typed, then it is never stuck. E.g. If $. \vdash e:\tau$ then either e is a value or there exists some e' such that $e \leadsto e'$. (Note that the dot means that the context is empty) 
            - Describe the **Preservation **lemma→If a well typed program is not a value, then it can always take a step and maintain its type. If $. \vdash e: \tau$ and if $e \leadsto e'$ then $. \vdash e' : \tau$. 
            - How would you prove progress for ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jKdRjXh1DlDTqD2MzEv3N57E-nrBgnoFwL2E8OjF-pQnlYJT4DSipFalZssoCkeugNmoq_mJmQxNGB7Y8jfO39adWaGgACkueE9c3XDg3_qVe-JMnV-l9zmWYqcQkuP0.png)↓ ↓ 
                - We first apply induction on the first subtree, so we say $e_1$ is either a value **or **can step to e1'. E.g. $e_1 \leadsto e_1'$ 
                - Then we approach these two cases, if e1 is a value we can do substitution straight up, resulting in $\text{let }x=e_1 \text{ in } e_2 \leadsto [e_1/x]e_2$  by rule LETSTEP
                - If e1 can step to e1' then the whole let can step: $$\text{let }x=e_1 \text{ in } e_2 \leadsto \text{let }x=e_1' \text{ in } e_2$$
by rule LETCONG (see above) 
            - How would you prove preservation for: E.g. Prove the typing rule. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/x6jlctNzj_MuFuE2I9kOYoP97WgaaitS_ZcSm5X1MHyJMfHzZX1SEZi_2vYrWONnm3c4JKMTB1JEs2ZpS8O4uIjAei_KUlh3RZpNVCLk09VJtUo9vRPXVF4aJwzWDX0F.png)→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZS5_DpxrtgiSw5-P0w3hcXhaUmwZloQKgegWDszAQh0d7KwfazvRIGGNOxqAA_GAntcnzdChNLaE7xdAqTCZL8Kq-s2IfeCYAUlOzjA6SxTUJ9Jxz7m4iPcKHdvSJAs5.png) 
            - 
    - Lecture 2 - Curry-Howard Correspondence
        - Natural Deduction
            - After the advent of set theory, many proofs were almost contradictory (natural number set same size as even number set for example), thus mathematicians became worried. As a response to this, the system of natural deduction was invented - where the proof style was  __natural.__  
            - What are propositions?→They are the building blocks of propositional logic (i.e. no quantifiers like $\forall x$ or $\exists x$ ). For example T (true) is a proposition. 
$P \land Q$ is a proposition if P & Q are propositions.
$P \lor Q$ is a proposition if P & Q are propositions.
$P \supset Q$ is a proposition if P & Q are propositions. Meaning P implies Q.
$\bot$ is a proposition.
            - Some claims follow ($P \land Q \supset Q \land P$ ) and some obviously don't ($\bot \supset \top$ ). We decide which claims hold and which don't with **judgements! **Using inference rules. 
            - When does a judgement hold?→If we can build a derivation tree to the proposition under the rules of inference. 
So to prove $P \land Q$ you need to prove that P is true and Q is true, this accords to this rule:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/H-wp7laj0m077FKys0UP5v6R9dePvWey2d-Z56LT5u3j70De96ehtaeGhMObaf_arDLiR_izLxbo3cHEOn9K1QtWaNtaGEaHkfStJMLLWlnZ234BALl9E7WzBWMYwhb3.png)
            - What are introduction and elimination rules?→Introduction rules tell you how to form a symbol, and elimination rules tell you how to use it.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/pwMIgf9pf6KKVgcNMuQCbMRYL1N4bghVpUj7h6U_bqJlW8mBXQyYKnPj-Iur150Ch2ZL0NrgSGQu7LqUCE0EAyYzUJdgV3ZMqcjPZf4o7Tkd9KvTUS-Bb7O1WM9FX54n.png)
            - To prove P implies Q, we need to assume P and then prove Q. So our system of judgement needs to keep track of the assumptions we've made thus far.
            - What does this inference rule tell us? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/US240hjgU164wT_51TY79IK1IkPUrCBZ32fxmOt6dkOdMSq1LLItk5nlRLQpqw7PbqXHkY5V6V8tALeuiaSLWnF3j45FRHvOD6N6B800vykgOaPesSQJUVIvsT75DzFS.png)→Under the set of assumptions $\Psi$, we judge P to be true. We can judge P is true if ever you've assumed it.
            - What do these two propositional rules tell us? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5RArs7L_zGYIColZ9wvcz0MSdAsPSu27d_8BdO0rM37uWdwz-sLCvs84nGgPqRO-Yvg9eVJe2c_0nGjB0Ezrq9lZRj8xAPGdjvLLsMzqUZiB6u9yc6NS1VxVwqILiQPs.png) ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/rZkVbMufjMAH-DFM2pD9C2CwueqvBzdIkEfARZx3EMwvyhdY7qSQYerOVfLg6dYjfYPcaGZiMJ1lGA-D8xJCx0ClQTRJadR6yr0bnF1Y-yqNDOHnOniZbZSzb2m66Pxs.png)↓ ↓ 
                - The first rule tells us that if under $\Psi$ and P - Q is true, then P implies Q is true. This says that if we assume P and prove Q - then P implies Q is true. 
                - The second rule tells us that if we know P implies Q is true under $\Psi$ - and that P is true under $\Psi$, then  __we must __ conclude that Q is true.  
            - What are these type rules telling us? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vPahoJ3VDWwgx6ZaC9muzqCZJKu4BAWkHY3iSp7KzdbQpm_-4AjcxLrqlMCaX41fJqz0BxC87qM79d0ZHspSRj7FzfaW2lqS1Z_56qgdq_mjmgAvFuXJiBcYfyJSIpUV.png)―If we know P or Q is true (i.e. at least one of P, Q is true) and if R is true if either Q or P are true - then R must be true (all of this under our assumptions $\Psi$. 
            - What is this bizarre rule saying? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mEE5dsoAMUnxG3ONX1-b7Tp4rS56NniFTNh3tnNTlDppf0uBKuGpy1tFAOOvaMy-6mgOsjTKQPHUUQGDrHSHY7oQe_Tyd5zAQNX-b33Lcisb3dNI0ZCT-Az4RBldvysx.png)→If you've shown false to be true, you can prove any old shit. From false everything follows. 
            - Example derivation tree:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/IT85C9SNt6Oh--TJSRDj-w0lSjSBPEPCkTNIbI6oIFFo66zZggoYJCka06escjmDU_dUIi97tr2_sZqPS46jMje_a4FFvrNrZlFNyYsm4_WJjBfjf4DOndAQ0oCZpNRj.png)
        - The Typed Lambda Calculus
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-0B4YVHlM9XMHTqYsb4p08k9v7WmJVqKciQZQkpDNtsubPZxLyNRHj7euZEYUADpNqVDrdqElS0jHnVXGGqParqUE5N3v6eHFVDxB_Y3nPoycRRDGn0XZQ6Er4J--GOj.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ujHHUXBrr2qYtOFePiP-kTezfwAJNdpU4BR-rSioRJsphArc3bC7P27jWUNynVg2awrvnkdotpdTw5owuhgQMDI6bEMrjL7mISK-Rhioi7WauUnv9Gc_lPBCZkTqVe3g.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/htvHYz1UccjC2X_GitP1OfDEApJm5jpU9mTP7OIUKfUT48HG55K66ZPFl7D63ui465yl65YvOCHYGQxRKVGXAUUCfyAyP7xVLtb-u0Itb22GtAvnZsFopgCd66ODf5Hg.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/MkUebWZ3KjgIPFRogLgEyy-p3_3SU8H-asNGyf7F8QnkG5r19dceqdwslS8m1pA3yi6vo9dT3thfziFMywmIMXcoijCkRa1hkf2C18UwqqgolgIL6DybDolC96_0bDbb.png) 
            - Explain this typing rule: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4Ia-dar1OvU9RmuDBxkJMk9pefGQYd8v2aSNocEdXToFHO-GSHqhWgPPL6sAxLRf2vXu8Oxl4dUAYjjN1Y5tgS2VIOUQLTqU8ykvVcc0iKDe5x5nqMXSvsLSCuFrFSGn.png)→The unit always has type unit. 
            - Explain these typing rules: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jKO1ZbbSqtq2V2KNfT8qagx6LqOXR_TEGWEJsVRszynb1FAhGyHHQR-sa6GtufaV39rgmZ0aLh32mn2IFjjqA7Db4A4rdPOWPUTMGSbHh0w-hH8iAe7_bdZFbdzZy25X.png)
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/HLIirOK_a6m_xkcst0VXoI5TEXmsWOrzcWkh2FfN4XM_Bzre-rvazheRd20qSuNMTU98f2otWoQXagruoq_bcmxdy10Xw2i8rhGmcjiVMKplcBqzuMvJqho11g95Ev0z.png)― ↓ 
                - If you have expressions and you want to form a pair, you can do that given you know the types of your pair's items.
                - Then once you have a pair, you can project out the first or second items.
            - Explain these typing rules ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Q8UspJA_ew_iEf6FIbfDi59IRdEDZANDSncByvzzR7qjxE_fWT0GwQFtOxlYzj2jCcdCHb__nDRPWFJJ3kiBF-uHB55iQ7pRi8Qa6-cKhCKvbmpaAHzOTU-8oNmvXkS4.png)↓ ↓ 
                1. If x has type X in your context, then you can take that as it's type.
                2. If result of an expression, when x is substituted with type X (added to the context), is of type Y - then we can form a lambda function taking an X and the result will be a function from type X to type Y. $X \rightarrow Y$ 
                3. If we hold a lambda function that take's X's and turns them into Y's and we pass an X - we get out a Y.
            - Explain these typing rules ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/rPzdSxHx7eggRKkYEysV0HlU6KPjrnghMUwzvltABcFLrADMuz5GYaY9AACpoP2yx4-jqBuDWGbDaNgxP85R7D9grm0d2UAoSaQ1auYJgKXTcVhY3elgMgHCKUBq0FM2.png)↓ ↓ 
                1. If we hold an expression of type X, we can form a disjoint union of type X+Y - noting that the  __payload __ is on the left branch. 
                2. Similarly for Y.
                3. If we hold a disjoint union of type X+Y, and if the result of the expression when X is the payload is Z **and **if the result of the expression when Y is the payload are both Z - then when we case analyse the expression the result will be Z. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YJtsLNGCIzE6Io-uAz1o-Kb2Ct4y3xr869unk22lfna-iU2IszQm4RnsvcSXi0VLBr_zzDHN5whqHeCfWff2Sg8OQlpfk149s3LOcEYJf_hp9h11Im8TFEP3FYmXQNNM.png) If we ever form the empty type, we know we're in some kind of dead code - and we can form any type we like and abort.
        - The Curry-Howard Correspondence
            - States that any idea in programming has a corresponding one in logic and vice versa: Discovered in **1958** and **1969**
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/u9gFcqZtl05LlbZ7_MpIjShxxkun60MvEvIqdOeVYl5BMokLjDxInFB3ido0DC2gbDH3u2_g0n_Ncha08vEllbetGvFwaY4s4f2QueVkq0VPpW3Ls04sel5deZE2scHM.png) 
            - In programming you can run a program, so if we have this correspondence between proofs and programs -  __what does it mean to run a program?__  
            - Rules for evaluating the typed lambda calculus: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mearLg0TbHj13QFvtQEov6MiQ0_BwArofOfplOi4hNIsMh8VAdOLTCcUeBd6Odihg0dfAnG3-o7a6Z16XAx4ORv99TU_vz70XkqH-c9CQtL2LyQR4fkph5_QBPbnnJ1c.png)
            - Voids and sums rules:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9U71fOKb8jvjUGJ2hdYHylQwvu_ypRJuKktCbvFnzB8tYANxV4o2ve_oEE-h0-tetafx4wuLs3S_vwzDvsDwdnFHRFl5JC3MPapf3tpR83zLu2xwFivYTQWNRdhQ-jGq.png)
            - Finally functions:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yKL8JDgjLMAQa38m0ezDjqGBU1QZVg2Oo4BIy-AwM1OXiHDQxhhhZOGdvRaVm9x-vmeeh7Z0WyxzvOgOyeHf8Z5G2IEpH_1dIY7_XlAcXadw7v7Jmplcp-ePG0bfzNkb.png) 
            - Note that in the lambda calculus, expressions are evaluated from {{left-to-right}}.
            - What are  __congruence rules __ and  __reduction rules__ ? ↓ 
                - Congruence rules are rules in which no actual work is done, they simply tell you where to perform the calculation. **Controls evaluation order** 
                - Reduction rules are rules where some actual work is done. **Actually do the evaluation!** 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/wnPmR8W9CLXMVM8o2sJorvnJSW_SFzX-jOTQz_F-S_9UZRghecrdpAIjHWdZvcs3lcuZAuhmqq8G_tjDjDoU-2ZQS5b7T7FHhB2zWCP9CZC1BswQYxLGkehY0cFvXNqQ.png) 
            - In the case of function reduction:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/PGtcJ3uRTGRiNzDnNYF6ZnL5Qj7DYNLXuiVTOwDHPX_lhvAcOGMCDCTsoLCJ8PkybZ6nPGAiyvQsKR4jeGTRE2BCvRnDWqU0CbNUw0y4_eJ1xZCEI7rO2mE8wJmD_Uts.png)
Note that in this typing sequence, we first introduce the lambda and then **immediately **eliminate it. In the reduction relation, we immediately go from the statement to the substitution - removing this **detour**.
            - Every reduction is just such an {{introduction }}followed by an {{eliminator}} . We want to eliminate detours.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CqZ0wwB91YKN5OrWeqEjwbFho8E4MXzbUzuC1iaPM8-NYw0LJGP2dvmyF46ZjdFAOG-r52EMJErZu-HMxiWXwRr_bdBmPknuqFXXw0MjxwN25wPiloDSQMaFGakNFLDp.png) 
            - The values are introduction forms that  __cannot be reduced, __ the process of program evaluation converts an initially complex expression into a normal form of irreducible values. 
Which normal form you get depends on evaluation order.
According to this, what would be the curry howard equivalents of Value, Evaluation and Evaluation Order? ↓ 
                - Values are Normal forms
                - Evaluation would be proof normalization
                - Evaluation order would be Normalization strategy
    - Lecture 3 - Consistency & Termination
        - Logical consistency
            - What does it mean for a system to be logically consistent?→There are no proofs of $\bot$. Otherwise we can prove anything, the equivalent in lambda calculus being if we prove the nullary type we can prove anything - $. \vdash e : 0 \implies . \vdash abort(e) : X$ 
            - Note that there are no types with the null type - this in tandem with type safety (Progress and type preservation) means ↓ 
                - Progress (a well-typed expression is either a value or it can take a step) implies that (as no value has null-type) that a null-typed expression must always take a step.
                - Preservation (the type is preserved in a well-typed expression after stepping) means that the null expression will always step to another null expression.
                - Combining the two means that a null-typed expression will loop forever.
        - Proving $. \vdash e : X$ then there is a value $v$ s.t $e \leadsto^* v$ 
            - I.e. prove that every program terminates - to prove there are no closed term of null type.
            - Why does this naïve proof not work in the final step?
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/iBy-8cMTcej6hyHQ827QDcRjwDqvUk-mFTLrGTi9otnGd_33cH35Wdub48ujH2mLgRx1XpqnNbmz6KYJmwVF5FxRjWO_Oio6QrTjuihb_lGViARacpKR00IG3CIKjxlW.png)→Because you cannot do structural induction when the expression can grow larger than your initial expression (Consider substituting (1,2) into ((x,x), (x,x)) ). We can't do induction on the final expression $. \vdash [v' /x]e'':Y$
The Problem is that knowing a term evaluates to a function tells us nothing about whether that function terminates when given a value! We would need a stronger induction hypothesis
            - A minimal typed lambda calculus:
 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3SiqLFoCAb_tnm2cd8-Va1Xt5E4BhVIjuaomjAM36dQYvEenlsoNrdv5JWAdMoLI-Gwcoi9u_1rqQYSEGXEUNhoVIIxFl9cIoWDRpX6UPo6yhavg16Y5Lg0ZhGGniHh9.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/arYE19Ua-9dZ5qt_9JSSmUbkjMZ7YWTUa-pJn3_k5Ze80_FXUlb9c49f9r7OTtnKG3hXRG_PlPwtkAyokldvjQ52KKXrIs2zrsZaLQHpJuMBiJZ47CdfWMtN9Jngph3T.png) 
            - What does it mean to prove determinacy?→t means we've proved: if $e \leadsto e'$ and $e \leadsto e''$ then $e' = e''$ 
            - A Logical Relation
                1. We say that $\underline{﻿e \text{ halts}}$ if $e \leadsto^* v$. 
                2. We then define a type-index family of set of terms (Remember our simplified lambda calculus only has 1, 0 and $X \rightarrow Y$ for types):

                    - $\text{Halt}_0 = \empty$ - there are no expressions which do not halt
                    - $e \in \text{Halt}_1$ - e is in Halt1 just when e halts 
                    - $e \in \text{Halt}_{X \rightarrow Y}$ - when would this hold? ↓ 
                        - If e halts
                        - And for all t (Which we're going to sub in), if $t \in \text{Halt}_X$ then $(e \ t) \in \text{Halt}_Y$ 
                3. These definitions give us that
$\text{Halt}_1$ halts
$\text{Halt}_{1 \rightarrow 1}$ preserves the property of halting
$\text{Halt}_{(1\rightarrow1) \rightarrow(1\rightarrow1)}$ preserves the property of preserving the property of halting
            - We have now transformed our proof using these logical relations to - $. \vdash e : X \implies e \in \text{Halt}_X$  
            - Proving Closure
                - We first prove that if $e \leadsto e'$ then $e' \in \text{Halt}_X$ iff $e \in \text{Halt}_x$. I.e. we want to prove the halting relation is closed under induction. 
                    - Explain this proof of closure line by line
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/C1rO07JGsuyxzvB4pVBg2h6OEizDiDObswonxGZWsi-dozFTgbpxJbVBEB1B8hsj2hqhmWXB_4khOQbanA4xVQOwRVxdrHJ-0zJuJaJr3y2PoIiACTZyTBfjNBa6SIuJ.png)↓ ↓ 
                        1. TODO TODO
                    - Explain this proof of closure line by line  ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/or3sP3DZxlHQugqsuJl1BTb4xiCiJkF4GDtY75Z799BuaUWq6dk1SF8nTj5cBgbCNL-cWmAqNeGPz0X8E_z9gKmDEJoiSO0ioqJDlpsapQk11ui9Cce0p6EeeC2V8uk-.png)↓ ↓ 
                        1. We assume e steps to e' as it's in our proof statement
                        2. We then assume e' is in Halt$_{Y \rightarrow Z}$ because we are proving the implication from left to right - and we assume the left side of implications then prove the right. 
                        3. We know e' steps to a value by the definition of Halt$_{Y\rightarrow Z}$ 
                        4. Similarly we know that for all expressions in Halt$_{Y}$, substituting into types in Halt$_{Y\rightarrow Z}$ will result in a type Halt$_{Z}$. 
                        5. We know e steps to v, because e' steps to v in n steps - so e must step to v in n+1 steps by transitive closure.
**We then assume t is in Halt Y**
                        6. To evaluate e t, we would first evaluate e which would give e' t - therefore $e \ t \leadsto e' \ t$ by congruence. (He doesn't explain what he means by congruence)
                        7. We know this holds for e' t by 4 and 2. By induction (because Z is a smaller case) we have that if e t ⇒ e' t and e' t in HaltZ then e t in HaltZ
                        8. We already have this
                        9. By definition of halt Y⇒Z
                - Proving the Fundamental Lemma
                    - What does the fundamental lemma actually tell you?
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/EhpEF7881cNYyPj3-6oyGFhbX7TTOG_ZoAUdfolDUDI7w5xUUNY8RKO886PRXKtu93SVSF5HJNU5Js8L4MpZnL3BnLTHR89yWHiXbHmT35Kmp6SxVH-sl-sqaJTOH_Tz.png)→For every well typed term, if you sub in a bunch of terms that are well typed and halt - the result will be in the halting relation. 
                    - Explain this structural induction proof of the fundamental lemma:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yu_nSbgixqmIw9jwCfQYrvy_4Plv-6ZTAKq_J2kaifV4iaSkxA4FO2oOTY2CKlKf02I8b5JXQU9o2Et9lsQmRGT4fQbsc_hlpDRRgo8juyp-7YNyXb9OsrajTayaA8Yj.png)↓ ↓ 
                        - NOTE: The arrow means from 1 to n.
                        1. We assume the **overall rule!** 
                        2. Just sub in all the values and we'll get out the one we want
                        3. This is on the left hand side of the implication in the fundamental lemma
                        4. We know $v_j$ halts, and we know it's equal by 2. 
                    - Explain this structural induction proof of the fundamental lemma:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vI1md1UhWH7jtCxrUF0NBK014MsK5jpslmc7s_Jp58nND_nA7Yvrs6lC-FqQUs6oLQWJjzU1uhzyKXzSb8-13oMmBCwmZqbQBlFlpl3WT322cX2vOcIftRg0VuKR5MxD.png)↓ ↓ 
                        1. TODO TODO
                    - 
    - Lecture 4 - Datatypes & Polymorphism
        - Representing basic data types
            - So far we've talked about sum and product types, this is enough to represent basic datatypes
            - Boolean
                - How would you encode Booleans with lambda calculus sums & product types?→We use tagged unions (sums), where left is true and right is false - So $\text{If e then e' else e''}$ becomes:
case(e, L_ ⇒ e', R_ ⇒ e'') 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ND0VXDiUwixx9ux4IFCIG2U67SG67V_yMCI__el4OjYAPKMlRkkjDlZdR21mur0_WhU2TfojndFtM0bS0joMupn41WCvEQ03bwTPs1RvZtcsuUsZdEq7EhCDPlehIkSN.png) 
            - Characters
                - Using these Booleans, we can bundle multiple of them into a product to form characters: (true, false, false, false, false, false, true): 'A'
                - This gives us a representation of data, the ability to do conditional branches on data and functional abstraction on operations. **However**, we  __don't have the ability to do loops.__  
        - Adding Looping
            - The simplest way to add looping, is using recursion
                - Explain what these rules are saying:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6YHDFKWN_1vXRD2wQC-XxcRRfXhV58C5nCUf-9sI-2Me6DtlEvHXGPZJ5SJCJlHVA-7junCoYh-2ChWocx3Lq9ahbd4h9nDZ9DEzR5KCm8ZquaHxFbRbQlPX6RQZveub.png)↓ ↓ 
                    1. If you have a function of type X⇒Y ( you need to have it in your hand now, because you may use it in the body of the function), a variable of type X and an expression of type Y - you can bundle that into a function.
                    2. First evaluate the argument.
                    3. Then if the argument is a value, sub that value into x - **then **to allow for recursion we substitute the whole lambda expression in for the variable f! 
So all the recursive function is doing, is subbing v into the expression  __and then subbing itself into e as well!__ 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/G89dsPp44V-MOrP4X6vEQxr55ibC9SiGqpeOXCCct6fYdNdjjCCPm1vbZbn13wKY8OS3fFKd14Z1459Un0X5CUUVQ3Ryr72Z-lHz6w7nwK3fCYSL5iMYYh0CQW0oEw9j.png) 
        - Bounded recursion
            - What if we only had for loops? We do something similar, by adding numbers that will ensure termination
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/8b8JpsGf-nYG2MceI7INhwz0rFxUP1qFdvhiNVFi-N1yTWC9ECILmi83QrTjAXHInoI_r3dIphY3lQnJ7gck-_YsYSHQ7gbVp7pEpIK-d7SLVrNfY2SH017XKLPLOqyz.png) 
            - Write code to simulate the iter rule, what other functional programming idea does this resemble? ↓ 
                - ```python
# Here we'll define the natural numbers as the normal number scheme - as opposed to s(s(s(Z)))

def iter(n, e1, e2):
	if n == 1:
		return e1
	else:
		return e2 (iter(n-1, e1, e2))
``` 
                - This is like folding over a number! Think of it thusly: 
iter(n, e1, e2) just says apply e2  __n times__  to e1
            - Using iter, we can build things like:
                - Sum: iter(5, e1, s(x) ⇒ s(x)) = 5 + e1. We just apply the successor 5 times to x 
                - Product: iter(5, e1, s(x) ⇒ 10 + x) = 10 + 10+ 10+ 10+ 10 = 5*10. E.g. apply + 10 5 times to x
                - power: iter(5, e1, s(x) ⇒ 10*x = 10*10*10*10*10 = $10^5$. E.g. multiple 10 with itself 5 times 
        - Data Structures: Lists
            - What does listfold say?![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/f76GCTUSo-TdTp1IgXycZQrS0P0zXQfGZxU-gLB3Q_QN7njiXc2IOOVhlgyCeJ-m4NTgNTdHzHtOVPFuIJlgcJRpjipDoM1MXuF0x7d-x_jS_UGZ3FQxdWPqW4cifRMs.png)→If you have a list in your hand, an expression to return once you get to the empty list, and an expression which can take r and x (which is the tail of the list) and return Z - then you can fold over your list.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tFm29AYxstSWs_l9azfDQZ-ZsILRKewi6uQsH0v-dPLY0i9V9CAWMkllaRI3D8jiQwldOiI-1CtGqZPIQHAOCXXVDIBK8Ng7KtKHFtcOZQ7Y6_-Lt4aMFcUme1VdxhlO.png) 
            - How would you append two lists using fold?→$$\lambda xs. \ \lambda ys. \text{concat} (xs, [] \rightarrow ys, r::x \rightarrow r:: x )$$
If we're concatenating [1,2,3] with [4,5,6] this will result in:
$$1::2::3::[4,5,6] = [1,2,3,4,5,6]$$ 
            - How would you map a function over a list using fold→$$\lambda f. \ \lambda xs. \ \text{fold}(xs, [] \rightarrow [], x ::r \rightarrow f(x) :: r)$$
For [1,2,3] this results in $$f(1)::f(2)::f(3)::[] = [f(1),f(2), f(3)]$$  
        - A logical perversity
            - The Curry-howard correspondence tells us to think of types as propositions. But what logical propositions do $\N$ or list X correspond to?
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ReKKgOhVVavj6tzw1qmoyqThWmq78YH4rxlW0H_RTX4vQVjA1gNcJZnM5Wa46xeRYXWtNFkzHDoZBbmxzzhyg_c-xEoKcjyp1idOI5ctJMPxhyAt74mqJ9MLR8GmkyzJ.png)
        - A Practical Perversity
            - For our definition of map, we know how to go from a list X to a list Y. However, when writing programs we must re-define map for each pair of types. This is incredibly annoying
        - The polymorphic lambda calculus
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/dde_zb95_h1MFa_AEvWpg0cfMFIrqTWBcwoyPLz5Nyr1zPIdzAeH6VvgS-FzaCxEB50x2VAqdgSTre3_q28v39tSGNnPUnzMlCVdqnwsLXpdlBQAfWa0KrASK70t3zsw.png)How would you use the $\forall \alpha.A$ to define polymorphic mapping?→You create a function that has the type $\forall \alpha. \ \forall \beta. \ (\alpha \rightarrow \beta) \rightarrow  \ \text{list}\  \alpha \rightarrow \text{list}\  \beta$ 
            - Well-formedness of types
                - What are these rules saying?![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/iLz4Tqz4msBwIvKqEFWDHcb68-n14gr3MA2xggI6_m4oVAWKAPo2ejpkfkCRcsw6taPKOC3EffzADgngfcsh43wnlcs_JJLE36Ih2n7GqstlY6DMDZd1kk9i-h-wYeg_.png) ↓ 
                    - Type contexts are a list of available type variables.
                    - Alpha is a well formed type if it's in the typing context.
                    - If A and B are well formed in B then so is A ⇒ B
                    - For all $\alpha$ A is well formed in $\Theta$, if A is well formed in $\Theta$** augmented with **$\bold{\alpha}$ 
                    - Note that because types can have a free variable, we're checking if the type is well scoped!
            - Well-formedness of term contexts
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sdYcRjaYR_HOF-egREBaE6rWg6tUW_DJd5GPoaIc7RdaA5R8Br4R6S7brcfFV8fkfoQvSZRQJ12MOtkRLnFSQxHAz2W4UzLg-lZwpia-Rc6jzhhf19yum8PG3aGYuyMb.png) 
                - Checking that all the types that appear in the term variable contexts are well formed.→TODO make flashcard 
            - Typing for system F
                - Explain these typing rules![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/T17jUN9t5py-G9jrk1cAv-x5PXYzXE2Hc0Egktb5h3uYjD-6v00ugM7z-xzTxMExUOANB1KjQkL_jDL4meJ_N9G00TqBh8sLbb0GMKKi6Xo6T7RgpTTgtUQpPlcWzrMl.png)↓ ↓ 
                    1. If x is in the context, run with it brother
                    2. If A is well formed in $\Theta$ and if e with x subbed in results in a B - you can form yourself a lambda function son. 
                    3. You can apply functions if you're holding the right type of input and the right type of function.
                    4. Introducing the forall type: The big lambda $\alpha.e$ has type $\forall \alpha. \beta$ when e has the type B under the additional assumption that $\alpha$ is a free type variable. Meaning we can add variables to gamma that refer to $\alpha$ 
                    5. If you have a forall, and you know A is a well formed type - then you can do a type application! We sub in A for alpha **in the type! **This is not in the body of the expression itself! 
            - Proving type safety
                - Now because we have implemented substitution of types, we have to prove type weakening, type exchange and type substitution.
                - What does type weakening say?→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4jq3ED2SonNoHulGfNsuOfkJdI2y9UicJhKlINKtc_sxW6XqwiCuSf5O45MsjNC8pc8xU_58lek1DHD_32XHpQqBksj7LNC2Z_uqFv3Yic71090nXc5oxBgmQlPr9u4w.png)
We can add any old type to the definition, doesn't affect anything 
                - What does type exchange say?→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NgIjB7LXPkVcqqGEaVG2HaoOhBYZqeiOszNjXnbt9xwE7qvD-ES-CjSX_mhl_Pg4sNSskS5mcZigeE-pALqjq3q3Kk0Mt9cISZXXDZsYMntrNUO3uaK9snsaqKA5ia7R.png)
We can switch types around in the type context - makes no difference. 
                - What does type substitution say?→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YqElk5G0ulivnLy-BmXCx5BkU-zwLcs8Hm96t2l-NCqwNoDQBV4gOEmcb7vEwQFaLGXj08FLuenMJUNySfl2pXzY1DBvGsQEcR0_P6mN3AC8XL0ECdjWhWwdMHECj1cv.png)
If A is well typed, we can sub it in for alpha in the B type. 
                - Make flashcards for ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/uF1O0FhaZeGMJLRsfGOFE6czyW2YwJxYZu-IDE0EPbgArkK8SpW0daMKBJ0BzA-4MNK7RUjvc_GWG_ZFSYkkzKqFYWz0AW71SgKrNcp4AhrV_hYkemG_HcA2eNJ1x7h9.png)→TODO 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/knxkmNg8nTxZHzMzsuv3GYXMFPJY4X1uxPEsEzPnRF_E4qGFrsqN9o7vKU93dYeQlaLbG2jPD1DOu0nXnc-xHGgZHVGpn6vdoT_aNRGTUU0DhPU2Zcf8wrE-9WT5uTBI.png)→TODO make flashcards for this 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Z2Iw17ZMlLpSk4vla_K6MxzSupiy_eS2KIrZpOeHJ8OhHuRFyKbjnFRNc1dFJu-efUmDZcMrqZHK195GpTYVL4HPv0zRMYytPrudbvHzer1EGrhzMCT8Mq0af4IFBsd_.png)→TODO make flashcard 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ciz9p9mqRvg8Qz-cbQCtclRXElEe-BfmUDrP6HaGc31pb_ZXgzGD6XaphYyenup5Enr-ZD8PL6XRTWIpx4FeR60N90SW8ny2eAlSCWGd8OwR5NFyA66DSVjAzhu7_O6H.png)→TODO MAKE FALSHRACARD 
            - Conclusion
                - Where did the data go in Sytem F? No sums, products etc.
                - 
    - Lecture 5 - System F and Church encodings
        - The polymorphic Lambda Calculus
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KfJp3TvqdczuwbfA3TM2RxT8qWE681EMBzN10LFAkPGb5z8x81jbImdyoy4gEm_8NpkqsmcsPn5KKUx2VpWYL4v3C-FcHuokcyPIuyzcws4hxS_MZeO1IXc2184irdIk.png) 
            - What do these rules mean?
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/49bVUSzxROQBvR0g15tzkyolYBCr0qL4bztGyJIFy7SBg77p_4vRGt0nSO_W3zQZRUKHMZL39FIpvv2Js5IpbgDezv9tth5C1XmaqK28ZSBzw7SyeGBlfb7rvF1LEUva.png) ↓ 
                1. If $\alpha$ is in the typing context, then $\alpha$ has some type 
                2. If A and B are well formed with respect to $\Theta$, then $A \rightarrow B$ is also well formed w.r.t $\Theta$ 
                3. If A has a certain type under the context $\Theta, \alpha$ then for all $\alpha$ A will have that type. Checking if the type variables are all well scoped.
            - What do these rules mean? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zHLp-pf9zsOKtk81JTJiRSifpw1b4y6U6p6Th8fpSOLuxbKVLzr5hrr9FfHXuDym5RWgkTxAYdbsH6u-r7FZB3xcSJzQNHYTwN7tnhx5IompAWFvvts4-74SZcE42P3f.png) ↓ 
                1. We can instantiate the empty context from an empty $\Theta$. 
                2. If $\Gamma$ and A are well formed under $\Theta$ (as a context and type respectively) then the context with A added is also well formed. 
We need this now because types have a well-formedness condition.  
            - Describe these rules![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/i0q5lHrIPLM_32u1Q6681h3yAFcv_V-bUDitb42n5ysEodTy9w-jDMG8cCWTg7-_YauPku_KdLWjVmbM_HNje_cwAmwarKB3pHT3T8sqFm-12PqUnLeSXGHTh2j_kTd7.png) ↓ 
                1. If A well formed under $\Theta$ and e has type B under $\Gamma$ (and $\Gamma$ is well formed under $\Theta$) then we can instantiate a lambda function as normal. 
This is like checking that the progr ammer has put a real type in for A. 
                2. Normal application, while ensuring $\Gamma$ is well formed 
                3. If e has typed B with $\alpha$ included - then when can introduce $\alpha$ with $\land \alpha$ meaning for all alpha. This is a way of binding $\alpha$ to the scope of e.  
                4. If we have an e where for all $\alpha$ it's of type B (for example, for any type of list - counting that list will return an integer) we can substitute that A for $\alpha$ and get the fine grained type of B. 
            - What two value types are there in the polymorphic lambda calculus (one is new)→$$\lambda x:t. e$$
and  $$\bold{\land} \alpha .e$$
These are values because there are times when they evaluate to anything on their own - they need help from outside. I.e. they need to be passed something. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KByNV8OFOhhOq6XiBrHOqwNT5W85Y0MYK23q2KMos3FN91s1DO5ncgHQhcJAW1E7UX0xmSdKJ4Mr1Nmb27byUzG08Vn4_wtPUAKf9Vj7cLEWqPI16fjHwIRJ3Jmv-1jF.png) 
            - What is $\land \alpha .e$?→This is a term. It's an expression which you can substitute in to replace $\alpha$. I.e. $(\land \alpha .e) A \rightarrow [A/\alpha]e$. 
It's the **equivalent for lambda **for types - it's even called lambda. 
            - What is **type **weakening and **context **weaking?→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/THqQHqZLq0x4u0HDU7Jg14U8fa6myB6eXfzqC3iw5BhxMAlou9BBQ0aCDF1U5F_xhXYH0kxFjIfX4QnsbdvPliOEIquXGDQB1XxRP97J9dwk1hhhOQWGIIJGGaavqtRJ.png)
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/r8V7IfQi3OvxnB0VIKVe4yJzyyeoKalkf8m0m7hSYisy-zzPqtDLYLAReVAubOTHzMeFhlFuH5a9zEe4kMX2s8qrPxwGvPlEWKq_2DnP4Rbvxw4XT37QiMwoDsXYFsKF.png) 
            - What is **type **Exchange and **context **Exchange?→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/D9z-9MIZPdqxJ06snhArOzIikdTpVPjQ1Ibn3XkZwwtDSezPxslLQGNJACPLQZxVU_8vTZJAhfqabMndKG2vj1YEdJONhI1jbMrpnmiatCEhW6M938dJkcFpyEvA9ZoI.png)
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/M3MsTL5aPWTT9yGx86wj805h1xEp0en7q7xg6HXZXjmtQvFwgnHOTwxl_djsmJlZa8Y8BL64dd13p2Pb2d0CZrAFLVHSVnVOzKzad2zLEMJ33z4WJgGwWnr7kuef0XcW.png) 
            - What is **type **substitution and **context **substitution?→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/U62u-4iBUAA8HUBcTpa_YNmlHh-12X4xaww-gn6YslZirDB26n2JptBq0gaZIa0KNz-G2GGt_mmGAbUelldhgCqeyeZdYX31p9p0dApMDW19q6ChHqt0LC5vHJR2ChmS.png)
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/eVkAdPzA-PabHH1NPNev8EfyiLJ3T2kGyqJXrDI-SqePeEZ3ytfwZ6L5eEZpt-5ebFbtR5GfHiSUyG8AuxpQulGoQdJrD5x9SnPoB_oDOnyI0xJL3NjEmb8nqcyRR9k5.png)
(note the $\Gamma$ should say ctx - typo) 
            - What is the regularity of typing?→Basically, if the context is well formed - then any type that is well formed under the context will be a well formed type under $\Theta$
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/UXTW1vAEFCUqjADQr7b_7IyU3bxbRC-N38BDFwfGJepbO0k19O9wYMTcgT-rIJC34pYPe7fYxDUFzVlduAi1S8ghRepyPP7E5Ys2xmlYWQQqOGDlteZsequt2pyYD06v.png)
You prove this by induction on the derivation of $\Theta; \Gamma \vdash e:A$ 
            - Prove regularity for the typing rule
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qrBZSjkzGO4WT_f8lfUIZpaGN5H7V2SI86TlLMB0CvUvoObA3Ns18lmkex0-R0sMqFJcLxnB1doDrz3JRYsGnEfAVrXXb_yurFSEy82pk9DIkoaCxXSX8XvnyBx3sCxY.png)↓ ↓ 
                1. Assume $\Theta; \Gamma \vdash e : \forall \alpha .B$ 
                2. Assume $\Theta \vdash A \ \text{type}$ 
                3. By induction on (1), $\Theta \vdash \forall \alpha.B$ 
                4. By inversion on (3): $\Theta , \alpha \vdash B$ 
Using: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/lo_iPjp1a-WIxPRKaREEHqukrgbQ17_uB6AXNourU30iP52axzki70i6bZ5-NWZw3ePJ94Iw2SLJIWKwLzvOxln8wd0f9S972Ku02CkcNdvoiw_x-Ik5JLSlh5jC7ZH5.png)
                5. From type substitution on (2) and (4): $$\Theta \vdash [A/\alpha]B \text{ type}$$ 
            - Prove regularity for  ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/msMJdK0tyUayqEpBGQ0HEkNYV3AAkrG5H4J0AmijCAz-pYvCMQ9C5kzmpKTSX4noxiwaakwq2efyCg4YZszHk-WUTuihznIl1e74lhIT1u6791hUFXWUwA5HjS3fKlym.png)→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/cV3MxlPkKZ8DERl1r4x_JMIxX3seAMl8NnVce_wHmsd5lADLsXPprsg_m5nGZFL74ZSxfQfotejsqFcOt6r71aRw3PAIo6CvB_9-2th5Jcrf9Y_TgQnI6t4tHhq3dSs0.png) 
We need to show that $\Theta, \alpha \vdash \Gamma \text{ ctx}$ before we can use the induction hypothesis!
        - Church encodings: Representing data with functions
            - How are true and false encoded in church encodings and why? ↓ 
                - Church wanted some way of saying if X then e else e1 - to do this he said Booleans were functions that take two types and return the second ones. E.g. $\forall \alpha . \alpha \rightarrow \alpha \rightarrow \alpha$ 
                - True takes two arguments and returns the first one, false takes two arguments and returns the second
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/XlKk_4biAZFIKHmJSNXmLH0IxumyWnoKZCMnd_Ll3UlJjMJwmEpk2IEAtT2dbWSmHF4uPBz5Otte4z_jexbyOR88Q8a65TRBTqIiMWhddmMRaSJ4wpiYOBNhYznbgg4v.png)
                - Then when we have an if:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gX2-NIGE5Y6_03TFA1hmkS_WHBbBcBxvZc13SAX94P3aV3cDxx6V8ALGmCKoGIkLhkfmVmNes4YK4lER-rIz8YRCaOsxvEzlnOBWF6UEWWK-uzQRL1t3Bm5Q9T-FdY4K.png)
If e evaluates to True, then the e' pops out - and if it evaluates to False then e'' pops out as we wanted. The X is subbing a type X in for $\alpha$ - this allows us to do an if then else over any type!
            - How are pairs encoded in church encodings? ↓ 
                - We use the intuition that if we have a pair, I'm allowed to use either value:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tIsKoqo7OvGX0oq5ZXUU42VXIziMiKcTrlhpVUewuHEp63qjE3voo6K9DrxR02113Ukf_GkfEJRgDbW3_ZJfFiUF3XApmFe9UenglzlnZJFRGjdFq3Dau5QTIJncZZ6J.png)
So our pair type takes a function, and applies that function to two expressions that it holds - e and e' are the elements of our pair. 
                - Then fst extracts out the first expression.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/SvrHjCd4tGd8VV9l3r5Q5pCeshrGEkDfS0TH7ZtgkO_LhuyXamqPqLKR9KfOi6hXWa2gP-A8V4gVKeaKiXFOMy31XpblYEeAGVXT0c-WxHJKSYvMuAxRI4XWd36UpvyN.png) 
                - And snd extracts the second.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/LhIf7kB1DTIqIrdZAo9EF7jpu63l7miyvqqQ1flnBZak0GzBLe_HNrgQTz0FkpjVIrVcRL_GdpP1JHeqm8zJDXxzW03bI69Usx_7n-CGYKP4iF6l3PTcug3Qifpirrqb.png) 
            - How are Sums encoded in church encodings? ↓ 
                - We use the intuition that case matching should return either the first or second component depending on if e is an Le or a Re
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/50oS5Iua5H60y_XVXqlp5M36qXvLUWKR8mJ1XvduSVhiOx7HznQKrvhBHbbz-r0seYMPDqZ8UCHH0iNHImfNpxl1UL2WefCKfQBYccrsahMFmGNvXUOXo6y7pdvBnWh7.png)
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/XI9NZEXghGzTLtMlgTEIItlNSHbczJ0famnmVkz5xBQOZkiBJgLzkHH7RJunx6h1IbZPm3wH1xTywA229obZVT4aZiJbmkGhuBpBdT4G-qNoJwioqeVsfRXGjf8IxeYV.png) 
                - So an Le type should take two functions, and as it knows it's an Le it should return the first with e as argument to e1!
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/VHjypwyK7ejOxXjnX9IwW62bz0m_i5FYYLQ0Arvh4LKuYBkikaH7htzIoPQZChxKHQZRvyDdhrH_wBw6gpTQ5OoiAVyyQx2FVTRz3PpU-_EHQP4UHw9QwNpgCRLyrrY1.png) 
                - Similarly for Re - will end up with $[e/x]e_2$
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/uooNfFOUYL63dnGFbPegsUwEq13lYkVywAT3FoUcZdLNXo9xjERur1OnaCLosz7dNMX6vW-b2Yh2xKfDeAqjBXW_aWoPcXx3dtLuypjFpeYrwtTaA6d_5hHVJpRxn7HK.png) 
            - How are natural numbers encoded in the lambda calculus? ↓ 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/fJMxQzqczsxy0IWaPwvRkyxocGyxF1_IJ-_wjCu5lPdEsMkDGVkJPZ4RaSUWnB3gejBlrvGkKUvO2DTGnr5yxevAxaLONZ_BSi3UwWaH11vBnqNQw861X_3zVU1YH_IN.png)
 The zero type just takes it's input, takes another function and spits out it's initial input.
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mKpE6QXaDJjOsATjxlZtJNlLYcNTbQzNMl_Np0WhrEShHNtami4am06pFQSwDeDoJNdKc3K8D93XBOQSgAAOY627LmLP49ZDx3QQ-lGGj-zV9QoJ5ZmJ3rv7zHL6GOLB.png) 
The successor 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZzTu-PhW_oRZIBYWmc-ehXLeu-8E78LIIf6lS8nKPCDDvgCpUPE02E46_jCGvjjza0cRwAMsH4m1Hsp43gBjFlAyewkfC8ixUbsFX7VipSAjr2JbYTDtBkwOHgWiyKJ8.png)
 DONT GET THIS
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/C2C_eRu-ieBeDxNJL2umP6Im4T1zMlhR1EFHaiRo0qTVwsP9Op_fMt12Wb2orDQrdAwTS8DGrPineSu7QkIKrxsQRZs003vZ-xHBJNgqswWCMQ2olSokz2sFRFSUC6qk.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/lB5B-5DqydLOTHnhBjXrbN62ejcpnHIPFk2R7cjulP-8gdPJGSorLcDj8QsZB_hDDT8GTkLvhENvajgwv9TtOPUhzr1QtK9LTa_8EkRALCx73ZvHhXpyfPOnauFSqqbz.png) 
            - How do you encode lists with church encoding? ↓ 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/d79PdggIYp3Z0LPWpOc72YpF4dxmpVtItJwx9UwFMSQTOKPvrir20oLJOrUk2JHrj6CnJ19qLGmvZbZaa-vEct7Yh9itLWETUjjeq_iC6A3hZfCs5aEnpZiD012UyH5v.png) 
                - TODO TODO
        - 
    - Lecture 6 - Existentials, Data Abstraction and Termination for System F 
        - Different implementations of booleans
            - Example ML module signature:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Hh1D4yFWFU6aipr960BWVvkFTkG3SsI_NlwVTRvk8wDrKVjTM8_mjsWtJ4akZLsdGO8FgjcW9xxDgoMCGF9URmOsRtHpXgdkLV0BjExbcmvsEdcG0hN-k3opZoCFD_V2.png)
For this abstract type we need a type to store, a yes function and a no function (which returns said type) and a choose type which takes
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2UR8RQRNEoLRs5HIrz6qd6sGESAHM6FGHKF6cD07W_i4s46qZACWDFVohrkJuVUIApMRDXAK7pGZjmjEQmv_B7Fi1lxS88_UKB3SWRIh5OyvnpHMYE3qA_i8wurEO6t0.png)
When we instantiate this signature, we set t to the unit - then we use choose to decide what to do when we're faced with a Some() or a None. Implemented using pattern matching.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/c_4PxvCXT7ZevOBSDCctvGV4NhnsHrvbAaXPiU-7SXt23TE_kTv13dBR8XV13oX8MHjI_CR-vqIfmWMWn_iDyCwS6kIVeViCSUiUlMcjHggWMG6VkkYDHMZ8oQcTK7kg.png) 
            - With all these implementations, we're just checking for a value and doing something depending on it's value. From a clients point of view there is no difference because **we get the same behaviour! **
            - Whether we do M1.choose M1.no 1 2 or M2.choose M2.no 1 2 - the output will always be 2. 
And you can't do something like M2.choose 1 1 2 because that's a **different type **the integer is not wrapped up the same as the M2.no 
            - We choose a concrete implementation of an abstract type and implement the interface in terms of that abstract type.
        - Abstract Data Types in System F
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/fcmw58aP4yCqUjWSCTFtHMhS0Md05iLU2WX9W-nvrBq02oWPjXzMJyxPrpj52bAskCEHQkWkp5d7SaP7ZzrPuIUb96yOO2mP2Kp0veiuy9HnExfObETswpnjxv4RYMPv.png) Explain these rules and new additions ↓ 
                - $\exists \alpha .A$ is the type of our module, $\alpha$ is the hidden implementation type and A is the body of the module.
                - For rule 1, if we want a module of type B with the hidden implementation type $\alpha$ we need a body of type B when $\alpha$ is replaced with the concrete representation type A - i.e. we implement the operations of the interface depending on the concrete representation.
                - For rule 2, we already have a module so how can we use it?
So if I have a module, I'll get out an alpha and some access to the implementation (x). 
To do this, we have to type check that e is a module, that** e' with that implementation x included comes out with C** and that C is a type.

            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4asiV9S7CBIc4UsJOTy5ZXUu5U2gq8l8gWhx7Tt6UhQVfvaNppTlYeCsqgaN4leRNr0OJ-J01Ib73CZyH4LhFmDZi3tB0p_RHttJmkG9Kznsl7bRezVM3957eevAvQaE.png)
Once everything's reduced down to type, substitute A for $\alpha$ and v for the implementation to be used in e. This is the **same as **M3.choose M3.yes "hello" "world"! We pass the function, pass the value and then it evaluates as normal. 
        - Abstract Type has the universal quantifier
            - Works the same as existential quantification in second-order logic.
            - Thought about initially as the Church encoding for existential types
            - Which part of the rule should you look at to figure out the Church encoding?→**Always look at the eliminator form to figure out how to do the encoding!** 
            - So we examine:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NDeUheEtBLTDwBNILLG-HvI8MBIy403hIyjYLy2M_z0DpUZZq2Ju6BjG2q0y3n6BtQuNmvY0WQedUrtLVx4GJANLut2iSSdYs3YK06yu73AwKKkmWonysqHZkNiCL8Ow.png)
e' has some arbitrary type C which we (Annoyingly) call $\beta$. 
We say, for all $\beta$, give me a continuation that takes a B to a $\beta$ for all alpha we slap into that continuation - and then I'll give you a $\beta$.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qNDqKFNxx-lJIYcCtY8DMy73P-1Cex2OFJBwmt8U8Vx-o41NjVBazfIaDMAw-uz_ZtlsP7wwqFRahMOSoUAacjKUeI87ZOgDrvKGnhqbAxUv4GiA2kGthL6EyXRdndvm.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JzBY_6ulkAhlJLrRU8BPUw0cNFri_mTUF1h4HrBcI11Wt0cwg82xwAu6O7lwdQ2NnIvPnz_FWIIKhpFYurusNn4ZVy3L_0TolCug5L8RKHMs5tdVaH7AM-gI0hkhqJQL.png)
This says, if you give me a type and a function which for any alpha and B gives a $\beta$ (the type you gave me) - then I can apply that function on A and a module. I.e.   so we first apply take A in to k, meaning k has type [A/$\alpha$]B ⇒ $\beta$ - then when we pass e (type $[A/\alpha]$) we get out $\beta$. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/iqg0dneOjH6nrhXAenjVnSdAXZxfPHWic92raLhdUoZekQzV86PXVCU8VZ0A25fKZi7NW6YucLrFCH2B4VUuwHYqBnflFGdflSEHgs9Mkbko7gdGwLqEBzvvA6YJn7et.png)
This is just passing things into pack, i.e we just do:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FZrihNnV4uFk8qDxNrTUjcJvBUUGxUMjhA7vby6UGJVYuM40iB37ZaKosvbe6b3niFsuwua3b_jpPwvUtPH1NYS_A1wRm59Oqd8eC5ArXu6FG1t-mxg1mKoCow5ikB2Q.png) 
Working through you get:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KkkFja_e-eu4QtdgjdfhxxLL7IzZy4vO4hyHIyH3easzFyD4RF29VQkw7iaSbUujMhr5LL1GJw1PuByWCvQUiXNJozzFFJ06D6XVthVxkqDOl-xXoAeiCn0JcrSSlq1x.png)
        - Proving termination of System F
            - Before we had a family of relations, defined by recursion on the structure of the type - the enforced a 'hereditary termination' property.
So, how do we handle free type variables in a similar way?
            - What is a  __semantic type__ ? ↓ 
                - A set of closed terms X, s.t:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/arezPcBT1yn2ZzrzvSNOz6ad2O4uT_cdztaPKg7mE0YYJMAE5LpBACk0xwIXNvZLLo6JzZcika8NlWdrOFDqNSReGBniREKaE5K0DQ7bKYOPQc4Ct013sCSAd1xeWVgA.png)
I.e. every term in X halts and every term in X steps to another term in X. 
            - We build generic properties of a semantic type into the definition of a type and use this to interpret variables. We say these $\alpha$'s are **any **semantic type. 
            - Semantic Type interpretations
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/UiMHLYqy1Rh_DJAJ2YVrQweo7gIFJ0BUg38V7tQiWWu238GfUx76vI_IRy4GQN_K0zzHw7zwwrv5Hu1oAbzZRyRyX_H7NqTA9VHL-fIOVPvcAfipIuzgU-XHwoE2H5rF.png) 
                - Given a type variable context $\Theta$, we define a variable interpretation $\theta$ as a map from $dom(\Theta)$ to semantic types. 
                - Given a variable interpretation $\theta$, we write $(\theta, X/\alpha)$ to mean taking $X$ as extending $\theta$ with the interpretation $X$ for the variable $\alpha$. X is a semantic type!
                - Our interpretation will map every variable in $\Theta$ to **some semantic type.** We don't know which one it is 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/R4LYwmlxJ44hClZ-O1sSivudQRMuAGZljK2KIq2ibKAbYjGbRr0qCtoihQjcjGdZxTphflE6AKdd1ZCZ9aFtHB4kRTfhgtpapvSwzRcqx-YBzGhF8xBQiUfIoT7oOm9Y.png)
We have a function which takes a WellFormedType to a VarInterpretation to a SemanticType! The var interpretation is $\theta$. 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6ypgloNR7ZqvAcLXCnkPPgpMs4LVZjVgpdLGczT4mWDhs7VvRT_fSdsozrWk4F6tCK8-xrR0SNfpSQXECNdz6bNK7U_XV2aPKrWTiikiQioFb2cpUvUJUClX-eI4WjQA.png)
Here we just look up theta in our variable interpretation, and that is its semantic type. 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mHN2nbcET0kOlEIeaI_KAHpmiqxp0aNjfx9mrNoxVd1Oev1OfqxB8okb9Olx3awuSfCft0CxslhgtkKsvgCIpfzAm140lBCwmGy102-j-Gyvu9aigN50t_1CulLLHLiG.png)
e is in the relation for $A\rightarrow B$ when 
   ⇒   e itself halts
   ⇒   For every argument to e' that is in the set of semantic types for A, when you apply e' to e, the result is in the set of semantic types for B.
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Hvv05vfIp0g6V6Uv8xqOIRxWlEugXuS40HHp8PvcA5mGURs9fosbj1GGvMN0bw7gs5cnW0hroNoM-0VEZP_Fl0wrPbFq3dMvlm18FwGhlAmvGAvV0c0axeCgtK-s11mY.png)
 e is in the relation for forall alpha B if
 ⇒ e halts
 ⇒ Forall well typed A, and for any Semantic Type X: when you apply A to e, the result is in the set of semantic types for B when $\alpha$ is mapped to X.
So we're mapping our alpha to **any semantic type! **And we want that to still be a correct semantic type for B - so the only way the term can be in this logical relation if it halts for every single semantic type.

You might wonder why do we need X - can't we just use $[\Theta \vdash A]\theta$ to represent find the semantic type interpretation of A and do $[[\Theta \vdash A]\theta / \alpha]$ instead:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ah1PhOUKKiwv1Ixo91ko_0SLZjW6Mkpmhck39zD-UREEmF0CYr-Hl1NG5hyDxt6o9DU8QOg3fEBf6C7N1zkbcJp7Js9FCqskPnpnhTv5DOke6JlLb4IZhWKkf5xPu_Xn.png)
But that is a circular definition, because **A could be bigger than B - **so this could result in infinite recursion. Instead we iterate over all the semantic types and pick a random A.
            - Properties of the Interpretation
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/HdVUaBIOy_Ol4OTpfUHhtN4XJvVmS9tebOV81yujWNv3FrUW3hJl7oC3hDLUuYGXBEXAZcfqGz5WWO4KeBzWN_c0i5VrzjdKHg0xlfHQ-IiMttR50Qr9xti2z3eT3_XH.png) 
                    - Closure: For all types, it will halt and it will always be in the same set of semantic types.
                    - Weakening: Adding a variable that we don't use, doesn't change the interpretation.
                    - Substitution: The syntactic definition of substitution is the same as the semantic one, we can pout an alpha in as long as we extend theta to ensure alpha is a semantic type.
            - Proving Closure
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yIePAsOKZkmLW5K6MXEV-sPc6b57ELWIYJKnrz_lhFsXVwtZEoG7wSOcEAHNx6VIwbbTIySPPEWTmvhE2kd_WwZRUYxkQxs6vlGsdNaR2ynsnJHJ-hicK5xgypJd3EOC.png) 
            - Proving Substitution
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/24ce_uLCnCGvZAljaoYLYHbugeAZgCtTjpKWaYDqkAEWYwPTf4ZOcjwgxVfuxBhKmlbcAdQ3WGssvMzAOZupc8tWuVMpmRPmb4XfyZev-94dnLJtXAnpxeb6_O55sfpE.png) 
            - The Fundamental Lemma
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/wBav-0Xnp9YwMerNEfN63YBynYqJ8L2DHkFZKtqPW7XO69X2dEdThvr0Lvtj9OATXiwcpiMuwVmMK76zC7eEOP_dea9o3WBOJK3dEp1wtYmzLymulnQE6DniS_LjS91O.png) 
                - If all the e_i's are the semantic type for Ai - then we can sub them all in and come out with the semantic type for B.
    - Lecture 7 - Programming with Effects
        - Wrapping up Polymorphism
            - What is the church encoding for a map function?→$\forall \alpha. \forall \beta. (\alpha 
 \rightarrow \beta) \rightarrow \text{list}\alpha \rightarrow \text{list} \beta$. For any alpha and beta type - give me a function from alpha to beta and a list of alphas and I'll give you a list of betas. 
            - Then a function isEven - $\N \rightarrow bool$ 
            - To define a function taking a list of numbers and apply is Even to it, we need to define all the types - giving ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/md_rZt7ZhIL_L222grLfIJG0xTTnwal8IBKWnTdFzPLZGiHXj8XOPH7t_Nhcmi24MXLVPlpNX9RgHQKVzgEpGyClzk18zhHA93fVaciteRlS72PbiqTfhNuB_5ElzwlC.png) 
            - To go a level deeper with a list of lists:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jGZcYPRQgIvIWBG5QomDlWlMkRGJGuiYqAMRWL0O9csQkwsWour7UA6OoAJ5-y2GOA7wPp9vbdFbEIuCm-Om8n04sdmP4SNI5dLVS_3zRTVyLOnmK5ovG4-umrF-exDU.png)
6 tokens of annotations, and 3 tokens of the actual program. Programming practically with System F isn't viable. 
        - Type Inference
            - For languages like Ocaml we don't have to write every type - type inference is used. This uses a type of constraint propagation to find the type.
Introduce a unification variable and incrementally update the constraints.
            - $\text{map isEven}$: Term that needs type inference 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9nOvAv5fRnj-L0X9ohzWpjvaz50FGwFkXeolqdhd2-hyuBsn2htUXaLPclr7Tkk_ti2xV7iQ3aLWgb5441x0L5Y4fgM5onrhy08AanTya-Xv3XfwASJM7xYAGlUnLt6D.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/427aCcIPF8xi6CS07N2Exo8qTTM_WdVUIveQUtiUq-joC-2w2i2kz6Gtm9qVyJN-EuKJGzROAylieVrAHM31Rt5yLsKp7OGdJCe8WorMVcaxOGY8VH-XtqHBQ4yadWBy.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ws3X2yi2dHGsFKxeaCW9DpeadSCxK3hCb_IbTx8cJQIYU2ezu49W3V2UOHzPkhqSF3XTmthCBR0xDHRZRy1jxOOaEC0gsn05vyPex6Bu9bAOYtPTFNDQBhR34DLTbxxa.png)
We're given values for our constraints! So we can propagate back! 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/PbbiVELTwSTFk4pKonrMedUmJLTeptQXTIVkoZMHqtmvJfPjvXg-ZXJ65Fgd7vAWApe8rkN-vaSDoSDUANFnaJsHfnAHLBsjZzYMaWvV5Zw511FVda5W0gs9bBGOxF0O.png) 
        - Effects
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/nJFe-8ZhIyK9WM9Y60uAa7Zj--n1Y2DVH4AwOqrTlE3mSoHCG2isENJk-8KCKakuE1cdiED88G9PvyeStdWj80yXcNxtCWZZ5jcw6p3NhMMBxpClZ__8t8I4TgefmCfP.png) 
            - Sometimes, we write programs that just take an input and compute an answer.
            - Other times, we write programs to do things - we might want to save a file, update a state, work with I/O, or a robot etc. 
            - This distinction is the difference between **pure **vs **effectful **code! 
            - Two paradigms of Effects
                - State - mutable data structures/ pointers
                - Control - Exceptions, non-determinism (all change the flow of your program)
                - Other effects can be modelled in terms of state and control effects.
            - State:
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zB7fNzpqkP45UTzo4wsdNYXORjvaZGFbVYrlSDgR8Du_ZHxcAaYQyAjTEsEiZt7474nWRu3imzD0sxKqZJ_0YPuqyuPRRS1hjpuDKYY4_-zRSCsrmVs-Ygyu0ZyeiNAu.png) 
                - This means, when we evaluate the same expression twice you don't necessarily get the same answer.
                - We add the following type system:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NOeYMWe0gDV5vM1YYjFExcEvvRlQU_fNbHwOtamTBqca9Gq_JY41bRSm4xf7qz8ROHMJFqHQhOKU9CKheFeqT3kwLlkvnTjYudt7gkZ5R0CuanSmJ86D-fJfIp7oeqHH.png)
 
                    - What does $l$ mean?→The literal location of the pointer, e.g. the address 
                    - What does $\sigma$ mean?→It's a store that tells us what values at each location.
                - Operational Semantics
                    - State gets everywhere:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/GBF5Ksfn4i1yPOsG-nYkJt9V6zh4-zfo_XjwgqXgwG4fp7iQgRTes5pFbbthYnaI2LaLD4pmMPZrc1bNLiyMJGWx65LKvFDXNhLFAu5B-ML9AVivJHS9c_HX0hUHsWMC.png)
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/k9iWiW1XLCsjC3Q4peO6PUxvrSF5uEkuRL_wI0Zi5rlncs18DppMLoJwHXByp7dWaViu3VpYplvaxt-8i3VTvmWEYNo8FOdOStHsz_0H5XhBbTpfOJeDbsRPw3OHPM2O.png) 
                    - When the allocator runs, it gives us a location - and there's no guarantee that the same location will be given over and over. Meaning the program is now non-deterministic.
                - Typing for Terms
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/B_l4tO6I0Jr42C8YlfNK3ogsbHAClRc--XCyqsTjV0TJPAnJjI9WvbcY4f-PKLBLf8DPqt5OoW8KltsqhBjGqkSPUbPJ6-m4zqpptIZLGazZS-Ayp104wpdar54aZTfx.png) 
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9WbMAz6Qfj3TDdrg-tJTARpoo-8FpuPHYzcya-82cJLBW8S8aSByzdihkzeQ3veOJhRjhwvv2hQlPoa4TrdfjHfonciafOstMxzPxxn1fPx9uAuzt4zfXwiLdOotfHyw.png)
We pass the store typing along, and look at it in only the bottom rule. 
Why do we have a bare reference rule? Programmers very rarely have a pointer hard coded in. We do this because of the reduction rules, and new v **creates **bare references even if we didn't have any to begin with. 
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zjvWcNGIn0-j8Jsjdu8SXRPcEqasAf6A031-1FXJW6ZhQrc2UNqoCPE-bLh1Cq25nCLk0FThiMX8qbsKvyac-uhofgTI0zJ4xXUZVGsyy_YwYwRtZEQGWaM5DPRWBnaN.png) 
                    - Explain this rule
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/0Vkytqhm_rLyjO_7VGJe1HKFO4AiNavGqUi8N6rNAL-kaqy24uu1nqplfqs1LBRHfnmediPYiv3m4gP3fShqxvk1mqnPI9SnzYLTHEFZpwpZkbsit3EeQPNssYdkvrr-.png) ↓ 
                        - Remember, $\Sigma$ keeps track of the **types **stored in $\sigma$! Then $\sigma$ has a type that's a subset of $\Sigma$. 
                        - So the top left wants $\sigma'$ to be well typed. 
                        - The top right part says $v$ must have type X under $\Sigma$  
                        - Only then can you slap l : v and l:X into stores and types.
                    - Why do we keep the overall types in this $\Sigma$ object, isn't it redundant? Why can't we just represent the same thing in $\sigma$ : $\Sigma$→Consider a loop in a graph - i.e. create a reference two another reference, and update the second reference to point to the first. Then if we dereference the first to get the second - we won't know the type of the first when we dereference the second!
                    - Configurations are well-typed if the store and the term are both well typed.
                    - Is progress or preservation false when you add references?→Preservation is false, when you add references - creating new references changes the store typing and the type changes 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9epcSJwvdEo5wdpXvrT6xuFL0REUfIFBwqAfRo9uV9f4MbcBRIOTFbct79HxNhey6Vw2BKt-nT3_WGoLMcfJ-kcD2NJAvOHgI8gazfldLry9poSGyxssvQgVzwEvXntq.png)
The heap has **grown!** So the old store typing is no longer suitable
            - Store Monotonicity
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5TDW2wtUnGX4D6pvsbXjFEQqzejFkQaooaInUf-RGo0nOs1vbam3XbUpebUnQF0eotaMC0-rY30k_Du3Q2mwQqMRVWsgqLg1liL_t34KYKP1AelC0QngUWj_kxZwHFUn.png)
I.e. one store has at least as many items as the other - and the smaller one is a subset of the larger one. 
                - What is this lemma saying?:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/OavKHXP0VUabZ_hAMoJgdiCDWr_9G0XyAkugMi9lh-3y68rnXF6JS76zAbK0PB52pTT1wpRVSZ0hEVEdGtvrLOAaWlLzkfZofWIM2qw4UF4EbZoMBCcPiGgv-2tLVJ3_.png)→If one type store is bigger than the other, then it can do all the same things as the other one and find the same typings! 
Additionally, that type store will result in the same context!
                - This means **allocating new references never breaks the typeability of a term!** 
            - Substitution and Structural Properties
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3wDn7LL-78zLawJUrjWsLSlRGJ-5d3pKbCidpmyrd2KC_7IWSE5RSqXzjdIgR-9V2QrFo6UUtEcvbwTGSpxTnKJFcNDeNbBAYYFJoB8JkqxQY7UhGqVjs3bLkR8Nt4LU.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZlYY5qtYoEis4TxmHe7K5NnPGO4kCIHrEX-oc929stM4ZK1-VEAXggAXPHVIJH7BMm9eWtCN-qmoYuDzkHQ1gcdqbcCiJICO3U_4GIFy9tnGqEDiPAaZljKQWoPdqwfz.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/I2y8_zBkyFGAP6w_WlpdvYhnfiwC2BAlOJQXSfViz-n9FJHykyXm_tYgwEbBVNlaaYJ_AhsE-i8CUvUQgk5hfN-x1DS5pPpap0YnlK-mfz8FqFV2YjqWtoUJsekqSsiU.png) 
            - A curious higher-order function
                - If we had an unknown function in the STLC (simply typed lambda calc):. Is this true when we add state?
$$f:((1\rightarrow 1) \rightarrow 1) \rightarrow \N$$
What can this function do? ↓ 
                    - It can only return some constant n, the same one every time. We cannot alter the function we're given so we have to just suck it up and return some number.
I.e. the argument can never influence the value we get out.
                    - This doesn't hold when we add state, we can define a function which goes from unit to unit and increments a counter depending on how many times the function argument is evaluated:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bHUm6MIX1me1CyZQ1aqXQmjpzjWYYF8ij2nk720QrHqx8SJPYsxIO5e7EfNPm6vTlsaf0hM9qUOyTyXnQnvXGsXy_zXZVw7UPVAUXPlU3A-zjndj1Ze_WMNcMtzz1-u3.png)Remember, r:=X returns unit for any X. 
            - Backpatching with Landin's Knot
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9I1Mrsbw3GUzDEubRmMMgRbGR3SWerJrXq7CC4hlVfXU8e2RgpRutfpCwlwuyv2LUX3uqe1r6oORShZED1kmqAD0zr1TtaQsSWiNr12i93rkAfKxPofSvh0_pMHtYw2U.png) 
                - Landin's knot takes a non-recursive function and makes it recursive. A pointer is used to implement a recursive function
            - Another False Theorem
                - Because Landin's knot allows us to implement recursive functions from non-recursive functions - **Termination is no longer a theory! **Functions don't terminate any more. So we can write non-terminating programs.
                - Do we have to choose between state/effects and logical consistency - i.e. is there a Curry-Howard interpretation for effects? Yes, via motherfucking monads.
    - 
    - 
    - Supervision Notes 
        - If we have to prove type safety for VAR: $$\frac{x:X \in \Gamma}{\Gamma \vdash x : X}$$
What problem might we run into and how do we resolve it?→Progress assumes the context is empty - however VAR requires a context with x in it. However, the rule still holds! Type safety says **given **$\cdot \vdash e : t \implies  ...$, our rules still holds as the left part is false so the overall implication is true. (Or you could argue you assume false so you can prove anything you like) 
        - Why is this allowed? $$\frac{v_1 \le v_2}{v_1 \le v_2}$$→Because on the bottom is a **syntactic rule**, in the world of the lambda calculus - while on the top is a mathematical rule in the world of set theory and arithmetic. If we were being proper we would have some symbol around $v_1$ and $v_2$ that say the set theory equivalent to the numbers $v_1$ and $v_2$. 
        - If you want to do structural induction on the shape of a bool type, what must you say?→You're going to go case-wise over true & false, to do that you need to state that "by examining the typing rules, type x can only be true or false".
        - When you're proving things, don't forget to state you're performing structural induction over which rules to prove what.
        - Why does $\pi \rightarrow 0$ mean negation? Give the intuition that **doesn't **rely on propositional logic→This means, if you can prove that the type $\pi$ exists, then that proves a falsehood - clearly this cannot be done. So from this we take that $\pi$ cannot be real, and thus we get that not $\pi$ is true. 
        - Using the correspondence between programs and logic, what can you confirm if a program type checks?→If a program type checks, then the propositional logic formula associate with that formula must be true! 
        - Note that all expressions that halt are in $\text{Halt}_1$ - (1,1) is, 1+4 is, it's all in there okay, okay?!?!  
        - What is this saying ```python
Halt_x = match x with 
| 1 -> ...
| <x,y> -> ...
| (x+y) -> ...
|... 
```→When trying to prove halt_x, it's true if the statement halts and if all its constituent parts are in some halting set. 
        - 
- 📝 Information Theory
    - Lecture 1
        - 
- 
- Term 2
- 🤖 Machine Learning and Bayesian inference 
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
- 🔒 Cryptography 
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
E.g. even if the way our protocol works is leaked, there's nothing you can do [😝](😝.md) 
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
- ⚛️ Quantum Computing 
    - Lecture 1 - Bits and Qubits
        - What computers can or cannot compute is defined by the laws of physics alone.
        - 3 day computation vs 1 minute for a certain problem - note the problem was simulating itself.
        - Double Slit experiment
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zsYW979FOUjLSg3H5VowyWqQ8yZbMSvLNuWOeg89DbHA49v-fSJiw2xHFICLtx-PAvn9Md82CfoPPr6_UBi-8OO6FmygaI6SnIGdEcw9BoiSkgEpN_IuN_g4s-ujhcQb.png) 
            - You get an interference pattern - telling us light acts as a wave not a particle. 
            - When we fire only a SINGLE photon at a time, we still get an interference patter - gives us wave particle duality. So a single photon can exist in superposition, a photon can go through both slits and appear to interfere with itself.
            - However, if you set up measurement apparatus at one slit or the other, light instead acts as a particle. I.e. measurement collapses a superposition.
        - The qubit
            - A classical bit is either equal to:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/aDAj4gj8LJm0HFxdzzyCqXkLi33VOWNLbq1qTNU_VQduEJuXZj4bMpGS281H1RlPgCGrT7xXT28RdIgFhfPLp9ZhEkJy0Xkk-CROfq67L0-_L-6WZ1SJO-2dOpHETdOx.png) 
            - If we are uncertain whether a classical bit B is 0 or 1 we can charactersize it by a probability mass function: $$p(B=0) = p_1; p(B=1)=p_2$$ 
Then we know $p_0 + p_1 = 1$. 
            - A qubit is quite different, it can be in a  __superposition __ of 0 and 1 $$\ket{\psi} = \alpha \ket{0} + \beta \ket{1} = \begin{bmatrix}\alpha \\\beta\end{bmatrix} (\text{Vector notation of a qubit})$$
Where $\alpha, \beta$ are complex numbers s.t. $|\alpha|^2 + |\beta|^2 =1$.    
            - Which of a bra, ket is a row and which is a column?→A ket is the column and a bra is the row - for a ket $\ket a$, $\bra a$ is also the **complex conjugate of **$a$.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/X7n7SkhkEl5ZaIe3CabDHQW6MrAxfcayogt9DSi211O4deWexCkXiceutL1Y38IPApWR3-xrlgR2hrrKojWzk5E4RLutATV0sY8zBmnU_5jj1wkpmKdG7XS7mhrd4ymI.png) 
Turning a bra into a ket or vice versa is called a **conjugate transpose.**
            - Measuring a qubit
                - Any attempt to measure the state results in $\ket{0}$ with probability $|\alpha|^2$ or $\ket{1}$ with probability $|\beta|^2$. This is known as the born rule. After the measurement the system is **in **the measured statae. I.e. $\ket{\psi'}$ will be zero or one.  
                - Further measurement will always yield the same value, this means we can **only **extract one bit of information from the state of a qubit. 
                - The superposition of 0 and 1 states describe ** a physical structure, **and not merely a probability mass function over possible measurement outcomes 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/htAaKu6YEaCGAVbTfIWkS53lMyQnnsrvulHs5CuiWzGqryeuFgtyk5rfKjv9Tbt0VtaEAEOSsqjNK6pPdaLQHLzoZPWp29J3FdIBKEq7VVDEZGi3wvJrowg179qHIYkQ.png)
While all of these have a 50 50 chance of being in the 0 or 1 state if measured, all will result in the system evolving differently when quantum operations are performed. 
            - The Hadamard gate
                - Describe the Hadamard gate ↓ 
                    - The Hadamard gate can take $\ket{+} or \ket{-}$ (which are $\frac{1}{\sqrt{2}} (\ket{0} + \ket{1})$ and $\frac{1}{\sqrt{2}} (\ket{0} - \ket{1})$) and map them to $\ket{0} or \ket{1}$ respectively.  
                    - But it's main usage is the opposite direction where it takes $\ket{0}$ to $\ket{+}$ - this is useful for algorithms where starting states all mapped to zero are taken to all possible states with equal probability. (We see that even though + and - have equal output probs, they yield different results)
        - Entanglement and Bell inequalities
            - Describe the two qubit bell state ↓ 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/acnq1s6o8Biwmvhr4OfLTtLwlBBusqOH1LAluz-jCuZF_rYQHWibvht0o5AWaV4ZS_qoQIE35Y7vu0dH7u0y0mZoIKGkrdPezMKOuD9lnKuu9a1DsQtHCqo_f3-Qbev4.png) 
                - Entangle two qubits, and if one is measured and results in a 0 then the other will collapse to that same state.
    - Lecture 2 - Linear Algebra
        - Linear algebra is→The study of vector spaces and the linear operations on those vector spaces. 
        - Useful properties of complex numbers
            - Conjugate: $z^*=a-ib$ 
            - Modulus: $\sqrt{zz^*}$ 
            - For two complex numbers:
$|z_1 z_2| = |z_1||z_2|$
            - Unit complex numbers lie on the unit circle of the argnad diagram and can be writeen in the form $e^{i\theta}$. Theta is periodic with period $2\pi$ 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/AjtZADBfiDuAB2ACSptid77pZ9fl_rzQS_8PQXHNhtZ4E8wPh8Dk7-vT0tGz2JnWTf96Nz-Mc6u2d4RMJuXcI-6P0QFwWsNP-R7UZy1EceQtDdF1bGVvj8xtUdLtkaMD.png) 
        - Matrics
            - What would the vertically below $a_{12}$ in a matrix be?→$a_{22}$.
X is on the right, Y on the left. Annoying as fuck that it's like that. 
            - When can you do matrix multiplication?→When the width of the first is the same as the height of the second.
Remember, we turn the second on its side & combine.
Remember also - a 2x3 matrix is 3 wide and 2 high...
            - For $A$ being $n\times m$ and $B$ being $m \times l$ we have: 
            - $$c_{ik}=\sum_{j=1}^m A_{ij}B_{jk}$$
This is matrix multiplication, for $i=1, ...,n  \ \ \land \ \ j = 1, ..., l$.  
            - Which of these are true:
Matrix multiplication is associative.
Matrix multiplication is distributive.
Matrix multiplication is commutative→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/59JeIjd43_VE0_WNtQidTu8V8sg1Y8rhJ-QOBnmiL5ymCb7ivnfzg2lkep4wKwY9zB1MoRWfN8bakVFfzd8nuGN2SF8Lxm2sHbvOGD3KwUtCvJ6MAUeYjljPifJ6jkBl.png) 
            - Broadly how do we compute matrix multiplication?→Compute the dot project with row i of the first matrix with column j of the second. This gives the $(i,j)$th element in the resulting matrix:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/aWh6I0lOCgCS7bt2YwdVNhHI3lt233INDGMElHObe0vhb6ySqoKsK5NLX-ZXTOASZfmzMXC0cbLn23gtleulq-dJa70znOIUwTFbaHhJtg0AfjNtsPClmArpP1BBlaRm.png) 
            - How do you compute tensor multiplication?→$$A \otimes B = \begin{bmatrix}a_{11} B \ \ldots \ a_{1m} B \\ 

\vdots \  \ \   \ \  \ddots \ \ \ \   \ \vdots  \\

a_{n1}B \ \ \ldots  \ \ a_{nm} B

\end{bmatrix}$$
I.e.: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qx8rBRhlYSh01nmtAOKBNZowzeUw-0nx0FBeSxI6mjp73obTF9rAhHcQBTi-bAOewUzN92WOm-FjP9bV56dZOiYSYjm07vzj3CmNDhb_PaHW7CgRbwz23QP4oZJOs6bk.png)
            - If A is nxm and B is n'xm'  then $A\otimes B$ is $nn' \times mm'$ 
            - The tensor product is **associative **so $A \otimes (B \otimes C) = (A \otimes B ) \otimes C$ 
            - Additionally:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/H9_NrqEWgAWAtQzRcLSQC2ZRaY-oSso0X5XLSW00wGn-G14KXjckaPWz1kR7JSxGWiyNqiNbPB2PNIC9qcuXq3RtQjkkh_ttdt9gJTvngG_bigho4NA54tz8XrzBmkKB.png)
If A is $n \times m$, B is $n' \times m'$ and $x, y$ and $m, m'$ respectively. 
            - How do you transpose a matrix?→Swap it's rows and columns.  
            - What is the adjoint of a matrix? ($A^{\dagger}$)→$A^\dag = (A^*)^T$  
The conjugate transpose.
            - Note: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/8xM6TvH_kqRu8IGtTtUgcHhFofbk0oHHLi3vICTuFwavzu3RrCf6r3mkUd1znvaxpj2cRbv9-o2MaDZ4TN-jzyQPh-yToUqr2n2AO11TuJtdOj394Sew9DHLr1hGnBRL.png)
        - Dirac notation
            - A ket is a column vector:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/OzvI1m8arvl_tRpMbEBPSTkc14LDl_OYSYK-PC7ayvRAFi5ugzgi-HKypnUU7_AbYsidTDWN19LBTRQWPBa4qccZnop0_NMcODUh5-_S2cXLqaP0MXlyPOsHcFmOUryZ.png)
            - What is the corresponding Ket for a Bra?→It's conjugate transpose:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6_8oZ7_yfm7WApX-mtSjMjOHgO4BLneNvhznGyBUXL5C5cHgc6SkUT6kE_n_EnZqPWax5G6h59mJ2wrYr9D4qSxgfXdE7RBnH2u4hhVIChmXbECOJuAfBiXifWRa5HCN.png) 
            - Note: $$\ket{\psi} \otimes \ket{\phi} = \ket{\psi} \ket{\phi} = \ket{\psi \phi}$$ 
            - Note also that tensor multiplication is associative.
            - A **Hilbert space **is a vector space with {{a defined inner product.}} 
            - Inner Products
                - What is the inner product of two vectors?→$$\braket{u|v} = \braket{u | \times | v} = u^\dag \cdot v$$
I.e. the dot product between a the conjugate transpose of the first vector and the second vector on it's own:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/c7ZrR6N4ZnQQi425nPEWpvqm0HNb6-Z2J7DjmMmwAbiECBHzTuRT6xOQVPBGLRK3897ciixeODG9o8wJMgk1RQF7HjYUcgmLuMhPd8ecbWu8ndFzm7x1mtXWqdo-mcsj.png) 
                - Note $\braket{a|b} = \braket{b|a}^*$ 
                - If $\braket{a|b}$ is zero what do we know?→The two vectors are orthogonal 
                - Note: $\braket{a|a} = \sum |a_i|^2$  - i.e. a positive real number.
            - Outer Products and projectors
                - What is the outer product?→We take the second vector to be conjucate transposed rather than the first - e.g. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/AR0CqQzE-WJ7fwTkNlMh127OcQ5rMQA5xkHc8EFynsdiCa1Iwz27sxiUxs8D1E6lwlSThF1FFdDP_Dl_l_xCkQCzddPWSQS86N1JAAF4halIJH0R6NXH3bpWqUNxwJP_.png)
Note: This is the same as the tensor product but with a conjugate involved... Fuck me this subject.. 
                - What is a projector?→If $\ket{u}$ is a **unit vector** - then $\ket{u} \bra{u}$ is a projector that projects an arbitrary vector onto the subspace $\ket{u}$
I.e. If you imagine looking down from above a vector, we get the 'horizontal' component with $\ket{u}$ as the basis:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/wftcdPlanjCnoWf6DpxPdjYbVF-PfJ3za_CFHQucK4iLMFoXGz1zcLRfAMmejXl2M0iHqkC9vI597023ww7u8Upkzrl8zQ667JMu7odfbF_RoNGTNeSwzSWBJYMGzo0b.png) 
                - Why does this hold and what does this say? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/RRaV4cIVpa21u5DFAGNAPi5HXQccgn_Q4q225gXtKJSXNxVYe41hcTCp5DBwJ2HDP5_X_0aQTLsuwyDHhCHPjaiJBQpv9imwmQpeZ6nM3ex4afAiWODR5EGn1DUKU6L0.png) ↓ 
                    - This holds because $\braket{u|v}$ is just some complex number, i.e. a scalar value so we can move it to the front. 
Also because the inner product is associative.
                    - First we get the inner product, which is a measure of how much two vectors have in common. 
Then we project that amount in common along u.
            - Basis
                - A basis for $\mathbb{C}^n$ is a minimal collection of vectors s.t every vector in  $\mathbb{C}^n$ can be reached via a linear combination of those vectors.
                - Because the collection is minimal, that means that they are all linearly independent.
                - What is an orthonormal basis?→This is where each basis vector is a unit vector **and **all basis vectors are orthogonal. 
                - The computational basis is in general:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/H050YCzvQSR5A9zGcweNHKb_DyZCP1xY4S4X1WIQiX9JKHkaJf2u9euus99d-9z1w6spYqiJE2GzoeKSCSIr6XzsOEbBr_GxbUrkN0GTvUWYnHBYhgTz_CZB24V8hPQ9.png) 
                - Describe the correspondence between the computational basis and two-level quantum systems?→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/rDagdMm4RcaotAU9VENW2vuD2GUu9PjhaZdpBSbfZTHUhjfCuZkMQfYVqQE5eF8yN7lR1ho9U80K-v6dDBcXiwaphhqzyYx7G5sjUIICN6u-o-2czgK7AFmTNBy0aE7W.png) 
                - 
                - Any vector can be expressed as a double sum over the outer-products of standard basis vectors: $∑ ∑ (a_{ij} \ket{i} \ket{j})$ 
                - The i selects the right column and the j selects the right row.
            - Eigenvectors and eigenvalues
                - What is an eigenvector?→A vector for a given matrix, which when applied to that matrix comes out simply scaled by some λ. E.g. $A \ket{v} = λ \ket{v}$ 
I.e. After we apply the linear transform of the matrix, **that vector stays on the same line it was on beforehand.** 
You can view this as the **axis of rotation **for 3D rotations. 
                - What is an eigenvalue?→Eigenvalues give you the **amount **that eigen __vectors __ get extended when the relevant matrix is applied.
The eigenvalues of a matrix are the roots of the characteristic polynomial: $det(A - λ I) = 0$ Note: This is just a rewrite of the eigenvector equation $A \ket{v} = λ \ket{v}$ ⇒ $A \ket{v} = (\lambda I) \ket{v}$ ⇒ $(A  - \lambda I) \ket{v}=0$ ⇒ $\det(A  - \lambda I)=0$.  
                - Give the intuition for the function $\det(A  - \lambda I)=0$→If $\lambda$ is an eigenvalue, when $A - \lambda I$ is applied to an eigen**vector **that vector **remains in place. **
That means that when the determinant is zero (and thus the matrix squishes space onto a line (for 2D)) that vector will be mapped to zero (in order to stay along it's **own **line). 
                - How do you find eigenvectors?→First compute the eigenvalues. Use $\det(A  - \lambda I )=0$ which will give you a polynomial in $\lambda$. Solve this and sub into:
$(A - \lambda I) \vec{v} = 0$.
Solve for the x, y, z, ... components to get the eigenvectors. 
                - Intuitively, what does it mean for a matrix's determinant to be zero?→It means that the matrix squishes space to a lower dimension. For 2D, that would mean all vectors get mapped onto a line/point. For 3D, a plane/line/point.
                - Each square square matrix has at leach one eigenvalue.
                - The determinant of a matrix **IS THE PRODUCT OF ITS EIGENVALUES**.
                - The trace of a square matrix IS** THE SUM OF ITS LEADING DIAGONAL ELEMENTS** and is ALSO the sum of its eigenvalues (sum not product !)
            - Diagonal representation of matrices
                - What is a diagonal matrix?→Simply, it's a matrix with zeroes everywhere but the top-left to bottom-right diagonal. 
It can be considered to be a **basis consisting of only the eigenvalues.** These are easy to use as we can quickly compute multiple multiplications with these matrices - as each row affects one column in the multiplied matrix. 
                - If a square matrix can be expressed in the form:
$$A = \sum_{i=1}^n \lambda_i \ket{v_i} \bra{v_i}$$
where $\lambda_i$ is the $i$th eigenvalue of $A$
and $v_i$ is the ith eigenvector of $A$. 
Then it is said to be diagonalisable.
                - This is called the eigendecomposition or spectral decomposition of $A$. 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gTvQ1kq4We7balM_pHBeXn_VgQVwQK1RqQWJ64HggLNDh2CTPl80vn5nh3W9x3YpwBun6mNi0wzk9nTUAsgm0_-y6icCzXnveP-NB8UF8k7gbCfTG78jyT5bY02xhe-4.png)
Note the empty space means zeroes elsewhere. 
                - When is a matrix normal?→If $A^\dag A = A A^\dag$. This is only the case if it is diagonalisable.
Note also that if $A = A^\dag$ then the matrix is  __Hermitian.__  
                - What is a  __Hermitian__  matrix?→A matrix $A$ where $A = A ^{\dagger}.$  
                - When is a matrix  __unitary__ →If $A^\dag A = A A^\dag = I$ 
All of the eigenvalues of these will have eigenvalue 1.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tFxd3u5495ZPsji_CTvPsMYEw1cdJJmOO5cQH9jRva9gsfep_b39x0QoQ76b8pAcpMZ6_-cuFtybbAnfkwVHOy0t2rhCl6QuuvZQq3snIRPHfIAK1F3HOLRGoNkMVfNc.png) 
        - 
    - Lecture 3 - Quantum mechanics
        - Quantum mechanics is a **framework for the development of physical theories.**  
        - Bits are often abstracted away - whether we run a computer using a bunch of taps or a CMOS circuit you get the same result. Quantum computing is more concerned with the  physical reality.
        - The four postulates of quantum mechanics
            1. **State space:** how to describe a quantum state
            2. **Evolution: **how a quantum state is allowed to change with time.
            3. **Measurement: **the effect on a quantum state of **interaction **with a classical system that yields classical information
            4. **Composition: **How to compose multiple quantum systems
        - State space
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/MdSqfkVrh_moeZdReil5yjW52SeTgRtPx_j5C4jtDCm1STKX9KZkrdwVPFUEp6lY75w6e88YOmtNJh-ZA2xOB5ds07efRvIwCaqWau_1nANe2QfO0dtlaJwOsm2AcbPS.png) 
            - We consider only qubits, 2 element unit vectors, and their composition. We form a larger state space from $\mathbb{C}^2$ 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/H4-eKbzK1ps7WJKdQhduaV5006XvKHWK1XvMyBhC6fls7kHL3n6EY0et5_Kuht77E-vWoltDFhZ9Kb65P7_dlOKYStDSDh5lnJ5URnAI8t7rZH6rtgk9Hu0Zjj3L6cUk.png) 
        - Evolution
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ooj35ot5RJhtuHHLLUkcSxjBj11dgsmkq59pIp26bW-H112pi4lxL_nKUY8QqVwp_MQdBtwIJhBhtWVNvVxAlIaL_PA-SFkz0bJQh5l3wM8r9tIGMlvoRzFNu-CWlbfY.png) 
            - This describes how the system evolves (when it's closed, no classical intervention).
            - $$ih \frac{d \ket{\phi}}{dt} = H \ket{\phi}$$ 
            - We are interested in discrete time intervals - so we simplify to:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/8QCF7FP5XBOZ93WrgqFDEm1dyh5GE6dRELv836gN-xbnBj7KhNF-tRAng1mtYcjWjf48MaIyRuF8inOdJ5-wVMSZ8Esq6v9MSJxe9DNUjTARlHOii8C2KhyG8rTXTxhP.png)
            - What does postulate 2 (regarding evolution) tell us?→Quantum states evolve **by unitary transformations**. $$\ket{\phi_{t_1}} = U\ket{\phi_{t_0}}$$
Where:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YafqEUbsabYVa5cnlUMnuBD_eg9yj_pKCkTamFK_GK4DoCyE_plAkib2vetntU0WKsbNJrbmzdwrLwOQecLaXssr79mScsydZg3WVbA0xdBZDHaS5LPYxEPtigTyMXJK.png)
            - The significance of unitary transformations
                - Unitary operators are the unique linear maps that **preserve the norm**. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tGZCsWU7flckSIp9sFBpHJENPr9j95DJ8agZmCCi8y1mouZ5n7I2kvvIW0bf5xSmriSdX4X5SpfMU6zsAA0mUZ_lX2MVIuKPL1d3DtSUvnwKLYyow91IrlcKeIlzl7OZ.png)
                - This means that unitary operations **map an** **n-qubit state to another n-qubit state. **
Remember: [When is a matrix unitary](♊ Part II Lecture notes/⚛️ Quantum Computing/Lecture 2 - Linear Algebra/Dirac notation/Diagonal representation of matrices/When is a matrix unitary.md)

                --------------------- Portal ---------------------
 -- Avoided infinite recursion --         - The Pauli Matrices
            - These are important one-qubit unitary matrices.
            - The Pauli X matrix is a **not gate **-> 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zhXHHsVhJ5TTGr1jcIydZXoXWipTfqd0v-GrO5SB3CCgebtTnwTnLPNCYmWxZuTbEUiW3pEUEAOBw6YEIYQQB2WgrB0aG6AT-RyzMeU_HvXZw-XLyR2qNnQFLJFh6oLm.png)
            - The Pauli Y matrix:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ji0uQtMs7Or3taYrHm3et6uSJU3HXUfNdK5oCadDYIwY3UtZHdo4kmNaUcF2dVvcIo_vEjYjpyFiXwls409p8P8flK17LrAXarI5SkmZmsO9RuaBX2rHJdE2-ILMZ43E.png)
            - The Pauli Z matrix:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ViulbVdw6-2czf-ftN2XFKO69ZA99bLsfSJJQ3EzmuBHQWsaeIivGIIbBlbPdcJZgEcTTSkV9z06BtKh9IEMMc-Sv2YlzFge36_JL_2ILLeSeNBUZ0cjrYIoCh3aRAwS.png) 
        - The Hadamard matrix
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JGiu0r5eJz57JEp_ZmIUG-eXNNhplYDDQOqh1gP9sHqz6V0-D6WCQEZ_5JsHnUPDqS8SPiR8wt8-1IWowM6D2P6NnMszt28d-kHuFZyz__XzhLersNfTu8djlSsNZM6o.png) 
            - Turns a classical state (0 or 1) into a superposition. These superpositions are different depending on the starting state.
        - Unitaries applied to superpositions of basis states
            - Consider a general one-qubit state,  $$\ket\Psi = a \ket 0 + b \ket 1$$
As the application of unitary matrices is distributed we get:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/OEVSDUuvl_Bhi88rrE7Pkf3vmSNdBDqr-p1Nv6U5C9_uxaGBDeppc6C0ZN31yAOaAwGWAMqPluqoyeHl5g80P3HLs3ncx3mj5YWpny6tflvpcALPULpxrWAMKoFPz70y.png)
We apply to each of the computational basis states in turn. For example:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bzbCuRsRNYPUnNuzjQfY6-0-XiXvqxfi9D-68LPFfoiqoYMPYx6UigcU4GQJPjVxYbG7m0mhQbkrArO_oFR9y-BhGWDaM7sSfr5i9TRNszIGIouhGovgzx7o5On8ZtB4.png)
            - This principle continues to apply to cases of $n>1$.  
        - Measurement
            - We now give the general measurement postulate:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5L4Mq25lmBP_mYc3mwXIhW8KxjBD6jgFPzeC3m82-wm9ceko0IUUxuBi1Tpm70kb2H1mqzxTLXQg1V_Fm_M8Xcers8yaywJISK5vXyQPdJuINPHjKm0JjidH9-RJXdTi.png)
Importantly this is a **non-unitary tranformation.**
            - If the state of the quantum system is $\ket \psi$ before the measurement, the probability of the $m$th outcome is given by:$$\Pr (m) = \bra \psi M^{\dagger}_m M_m \ket \psi$$
The state of the system after the measurement is:
                                   ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_4jRrfGu2AGhhrZzLc7LevR1KuUqug3Jxn1eUW9_DUTVwzGDYNpWvwK9mbe6tzOOQ5ds1pyfruGnjWWDdAgyvKEUqaE5lrE9_2w-jRKPyXkvSpYofPf0SJ-rfW7_yVmu.png) 
I.e. $M_m$ applied to the state, with re-normalisation to ensure it remains a qubit.
            - These probabilities sum to 1, e.g.:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YD9x0xfHdMZNZ2yNeZNmnb084g3c_uy5u5cBjBh-Ysp_TLifIqAECYPeqWj_czYmrfiG5APMeQq8GgPzgd8j9YIsItCff_TEbicY1SSKHKPImplPzi1H0Yke5uC5zvVD.png)
This is only the case iff:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/L8L7Aow0drffjIWEOakkQFqm9pWfoBp53to1kOd0T0UJ33BLA_bcTajwNzltLhynsW4jrZpgqBcy-zcvSb87qeDkMcfPdv2ll7_ks-BMS2CXDwjy_FAj5Ukz7tI9RSjc.png)
Because m only applies to the central part of the braket:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Jr3ZQ-Uw55MnKoTHkJ5f-eKriCRTGUDWW162StV2U5SPAA5mSDpeP_1hZXxl3MpP0WAcC0zvuLessQG9rU84EQ61cCA3SeuX_OWuC7Mrp0b8z04QoEq5_Ue0cbzRfr8q.png) 
            - Measurement in the computational basis
                - We usually implicitly mean single qubit measurements in the computational basis when we say measurements. 
                - What are these?![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/wk-ymJxW7FBGgt2s-21yEhtZrXzMSGk0S8YmZAoBKjTFy_qPpMuhsAxARVFhdleVw3PFp2_LlmxoQYPdCdtn0B8Zikjeja2fuTnXF3MziOcvmPZSRJnUmAgQ8Us19Fd4.png)→These are our measurement operators, the first is for the 0 outcome and the second is for the one outcome.  
Note that $\ket 0 \bra 0$ is just the same as: $\begin{bmatrix} 1\\ 0\end{bmatrix} [1 \  0]$ 
These operators are used to project onto $\ket 0$ and $\ket 1$- they are known as projective measurement.

                - What is the Born rule?→For $$\ket \psi = \alpha \ket 0 + \beta \ket 1$$The probabilities of the measurement OUTCOMES $M_0$ and $M_1$ are:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/rxvUP44M3sfH70PMp1zSXSpTrqADtfveUSaoE2Cm7XfxNnS9ITtnkCq3Dm9HZal9dAORTVklY7rlL7XVpcEU8VvJ_U_Xv4ElAu0F8e2TQFWrRC2gHB2xpNohSmxTteSp.png)

                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9BERKbCIiZCFssnLSThsewc_h1qiu8apv-HcnJXARl4CrPzbXW5F8z6S4336T_MRISP3CSwu3Ig4XwZ1fggYCpE5wWfXfH6PNttJdjlWvODR-9qjKj8JBOcVB7WbZGAk.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ErU5MeBHzhgnQI_C49-FpIBCkPFEMNfXmSCV26ZWo4YTy47Rkq7qEgfaAy4-UkZGacgrQRquse6F3Pom5qEdHrWSMUywDRniN8UedKib7jAIFnbUn2q5CJuNqztaJJ3X.png) 
        - Global and relative phase
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Zc-1ynqUl_msOxDownFy6UXcjwkalllCdtZYGhQo_sNxOOszv2TecfxuFLKp6PyMEZNLyLvBNZF7zFBkEKQoqxxHzvqp7YC8A_uGKGrZwAoP68cf0siFmYkysQPf6YUl.png) 
            - What is the global phase?→If we write a one-qubit state as $$\ket \psi = e^{i\theta} ( \alpha \ket 0 + \beta e^{i \phi} \ket 1 ) \equiv e^{i \theta} \ket {\psi '}$$
$\theta$ is called the **global phase **and has **no observable consequences**. Whenever we measure we get:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/D4Rtbe1ajd1HOAubLK2ojxTcWkyl8Rzp4FbTVpoovmkrJ6zTRILkVWSW5A4R1FANl0B4CApN2n4mu_pB1Sm3f-9s08GVCLt0iSpNT-tMLQhaq_giyEkyfFmUrtFeKm7l.png)
So we neglect global phase. So we can treat $\alpha$ as **always being a positive ** __**real number. **__ If it wasn't, we could just pull it out.
The same cannot be said for the relative phase $\phi$, consider that the difference between $\ket +$ and $\ket -$ depends on this relative phase. 
        - Composition
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/B1PcYKrFGCJgKrNMXdEbM6tlzcemccjtr2YNdvEa6lujG9Iw_lNglc1sKQcPe2dH2-DwFSzquQrEtR2vKcJlbc5PxQNZVRD-qJGabpYG2N8x6-yKQS2-Q5VdFOUyMmQ4.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/V7s_iKu42pQ93XL0FWQfGNjyBh4_vl-vbnj5Wj-XixMvk5C90dsM9lEaxXTk-QEHwsGXr7dnD2VhkJcbUzougLrOA97Z5yPDCx8DUB1jYtF1ByU_jMDd2r3bCMZlvS1_.png) 
    - 
    - . If there's currently any text highlighted, then that will be added to the search bar.  Triggered by the forward. If there's currently any text highlighted, then that will be added to the search bar.  Triggered by the forward
- 🔃 Optimising Compilers 
    - Lecture 1 - 3-Address code and flow-graphs
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-fA56Za1tbM7MZFyb775uaOYAe9bFP8G-8kVCs7vLc2UXru7c4n9kZ2ImP8XuOZgCsx-X-Prcgx-PFDvkjLq6eceWmOgf0xYsWWjjRoo7ja34I8585GeGRFRHOrinOBt.png) 
        - Good programmers write maintainable and **general **code - compilers remove this **unused generality**, and hence make the code smaller faster & cheaper.

        - Optimisation is analysis + transformation - transformation is doing something dangerous, the analysis step determines whether it's safe.
        - Analysis shows your program has some property, the transformation checks if your code has that property and then applies it.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CAPe9nnWaMG1fg9gOcvjWVIKJvk7n4hwdNKGBi-66cyVqoLlwebiOuY02bRWgJmJ_UWOyOe_CG4wJrVod3x16UseeY1psmRlzfNu7p3DgItce3Uj7xfeTKQeX-FO08Jw.png)
We can't simply move k out of the loop here (to not recompute k*2) - but we can't do that here because we have a cross iteration dependency.
        - Stack-oriented code
            - Code heavily using the stack...
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KxKrYbcJfOn2Ug9NaUKYwwJhnJAEz_zLpnnbIVmbvPtXBi52F7L2-kzMlVIxEeb0at-hAvBX4mqjm_CjPavJ8eHjO-N2MO_WmWGyqaEGL2Di5meQ0PKVWEsk7a9ieGkt.png) ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/kXzBui0-Chc1PxdqUxwJ1CHS5WV7GPKNcuzdYf3izM50epAS9y5XC75JlzaTfZk3mGgN25jvqPIV_T3kraar_SUilRwrdheAMUgIquKvvdW7A5JGCQs2xxSm0mpaqmM_.png)
**Not easy to see what's going of from the start.** Dependencies between different instructions is implicit - this makes analysis  _**hard.**_  It also makes adding code very difficult.
        - 3-address code
            - Convert the **stack code **to machine code - e.g. a load becomes a move, an add is an add and a multiply chooses registers not from the top of a stack. Temporary variables are used as temporary locations to store things in - e.g. t34. ArgX is the arguments to the function.** The compiler can create as many temporary variable as it likes.**
Res1 is the result.
            - The links between variables is **explicit**, we can see how t32 flows through the code. Additionally, you can slap things into the code and not affect anything.  
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ktYCiLi5pPih7Bz1WIQQ06vWq5ux-PUTukIIEO62QHWJqh7qeaG_IdeBuzU6h9YUlG59ennVRaDoKSlHQAChT_F5XbTDoTdwsW7P8LDrCubjsoJ3xGXkdL-ly4R42fWj.png) 
            - 
            - 3-Address code commands
                - What does `MOV t32, arg1` do?
                - What does `CMPEQ t32, #0, lab1` do?
                - What does `SUB arg1, t32, #1` do?
                - What does `CALL fact` do?
                - What does `MUL res1, t32, res1` do?
                - What does `MOV t32, arg1` do?
        - Flowgraphs
            - We still don't have our program in a form that's very easy to analyse - we want a graph representation of a program where **each node stores 3-address instructions**. Each edge then represents **potential** control flow - all of the control flow that could possibly happen:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tiSdMuYSO3b2nqyJ0_sw7uNtFTC0yek-cqvlukU1XKOTK977MmI-sfrrdvJk6Nmq2Uz2_dZrSr3CKkoLngolujHLWHm3axLIYN9JfR38gnEMk5xFKSFlqWj70_TovrpF.png)
            - Flow graph for factorial:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sM1jXGbIhzFotsTXQ5EXA_EPZFzgX_n3hixlxYaw0S0TxdQ_QLn4HY4Q1bq6BIJVGyk15Rmix8ngy38AyDU2ChV8nWqFXZWMHcYtuGL9LbtWxb2L0HVRGqspqStPkqVx.png)
Note the graphs flow from entry to exit.
Also note that CALL fact **does not return to the top. **We don't use conditionals.
            - Basic blocks
                - Form a sequence of instructions which form a function. These are grouping of instructions where there is **no **interesting control flow between them - no jumping, we **have **to compute the items in the block.  
                - So **every basic block has one predecessor and one successor **(Perhaps other than the start & end). 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2Xs7HsYqRCUxPBupQsgww_RSuU6KEPwGaWm0FQbQr2cxiAMEUtAPdO8wsqWwzXC6_BasG9rwKFqyIjVX5fLD_1vE0O1LVGugiv7kfA5LecmeLA-wYtof5A95_5SC3MLs.png) 
Do we stop basic blocks at a call instruction? Varies, can be useful to know that control is given up.
                - We then separate out the entry and the exit:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jflCTNZ0gnog6qwc99lJmCk4KAgGPe7LjDisHtkrVFTUs2mV1aj1xRgIHCLP2sNmx6WAvKU5j1v3NdYsyPanHnl7lMUZy5JylYTCXjM7AmCF-2XuyrvGWPVtXyYIb2Gt.png)
                - Why do we use basic blocks?→Reduce time and space requirements for analysis algorithms by calculating and storing data flow information once per block, **instead of once per instruction!
**If we need to we can go in later & examine the basic blocks. 
            - Analysis types
                - Peephole optimsations are→within basic blocks 
                - Global optimisations are→between basic blocks -  
                - Inter-procedural optimisations are→over the whole program. E.g. unreachable function detection.
                - Peephole optimisation example:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Pu2kQb9r2IEkCzmoqqvutQBHzuT1QptYmsMx0QQ41XnSe6G5hBQQxKJsMOR3bzAaTG9MX6rL71OlzydIBMzvLV24LFbs-IM_BpqNcmfV7NSJfAeSJCerXJFzHO9Fx5HL.png)
                - Control flow analysis is→discovering the control flow 
                - Data flow analysis is→finding the data flow structure - (variable use etc.) 
            - Finding basic blocks
                - Find all instructions which are leaders - e.g. the first instruction in a block ,the target of any branch and any instruction immediately following a branch.
                - For each leader, it's basic block consists of all instructions up to the next leader.
    - Lecture 2 - Unreachable code & procedure elimination
        - Intra-procedural analysis
            - Analysing a single procedure on its own, do this for every procedure.
            - What's the difference between dead and unreachable code→Dead code computes **unused **values.
Unreachable code cannot ever possibly be executed.
            - Deadness is a  __data-flow__  property - will a value ever be read?
            - Unreachable is a  __control-flow __ property, is there any path to reach this point? 
            - What does the safety of an analysis mean?→We're **sure **we aren't affecting the program. Many interesting properties are undecidable, so they must be approximated. 
            - Overestimate reachability so we are sure removing it is safe.
I.e. if we can't 100% tell if code is reachable, assume it is.
Assume that loops always terminate and both branches of an if are reachable!
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/BWszlJH7wfmLFjmU_0dSI0zajacMUzZeUJOzZHjbWaR4wtIrrGCVp86cVtXC_jwc6WZX2mWWDmQB--5FFrAA8MQ_ufgIL6khHEOsl58IV6lblNVAaX1INfwDdh4OMOiT.png)
It's not safe to just assume things about JMPS! Could go to the same label or a different one each time. 
So, to stay safe we assume we can go to any of the three!:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/HgBc_1jBLviqLHghuElBoFwX_SoATtDawMu9FPevivJtkDM-cS3P3H8Qg4tE64v3ju-lfD5Twhm_SGSsautSowU99TCXaHUuzMDCXRFO9VAl8sKyqXH3SV875bJxJl0Z.png) 
        - Naive reachability analysis
            - Mark the procedures entry node as reachable, move to successors and mark all of those as reachable until we run out of nodes.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CvEJDshtZ-_8PqpfONV1pnsjOiipqFAmjGvQSKsbM_yrZg0Bt22D_nGz2vKGroWhvSI3fcqTxxLLVEmqi1sNENzwHA5R4VG152uO-Rqf7KribY1rmVgCETwzY1CgiQvs.png)
            - Results in a simplified flow graph.
            - Why do we bother with the unreachability analysis? Surely, programmers would never write code like this→Naively unreachable code may be introduced by the compiler itself!
Something like this caused by copy propagation:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/phVVVVU5joOEGK_HTjean_ugFjo4Sji_bbIoRTUCCa-nYB5gudBW2NxzMyxsFnuIr6lO3mFtdiXnQb1hFBmoW_sZh6LCr8k96ZAtCYY7yTeZleKImJud2-06K1JKKydf.png) 
        - Less Naive analysis
            - We're now analysing the code itself - rather than iterating the flow graph we instead make a **decision **about the path. 
Checking for things like: 

            - if (false && ...)...
if (x != x) ...
if (!true) ...
while (true) {..} ...
            - Unreachable code eliminations not only make the program smaller, they can make it faster if other optimisations are allowed to run.
            - What is code  __straightening?__ →Eliminate jumps between blocks by coalescing them:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JMnqHmgtoLD0gCvARON7Gpm9n5Wt0CGmVjtFbPWo75ipRSHo3xjBH3OzUF19ZUH3mStfNQNMHpF0LZCxifNFSb-Ja1cZDdnnVdXUSMsTVO1OlHBr6VUQOMnKyqlcgZsq.png)
Here we can remove the above blocks and coalesce some blocks:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/R9vAIy9Cz13KeBese_4FRlCa0_t4VTFUbNnWNItsvDi_rKA2pLvKjM_cX3x-eUQfzIRlpbaIABslBaIgqoU8kgFcb2EvbyJcQZwhNuUAnr8E6c9W7VhFtLHaRVkbk-wx.png)

        - Inter-procedural analysis
            - Collects information about an entire program - propagate information from inside procedures to outside. E.g. take information about the callee to the caller.
            - What are call graphs→Stores which functions calls which other functions. Just examine the call instructions.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7T8DW1KPSAQ_4Kz3CoPDkHxeRiX_imqfAL8RS0Id18clJbYrD5mGRtJ5s7v5yII7-wyfWj0ObZoWXPmLQfbHsBiC4CSABeloklZiYLJSJz2Dp3MsdGKf_cttXr9imCzm.png)
Note we have indirect calls - if we're passing functions around we might not know which function is being called.
            - A problem with the indirect calls is we'd need to just connect that function to **every **function... 
            - We can then mark and sweep again, mark every successors of marked nodes until we find functions that are never called:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mOtMxJ7IMvfXRaImqrAfCyttXcfn6VWgLc8f2knG3kAKEPWyxp2Yrv5Ad4wDzPrxzZs_fceIOV5u273W8UyWu9YgAx_iW2eSi1TALMLCM_Y2imFb1UXdThKA29W6JDTd.png)
        - If simplification
            - If we've got an empty if then - we can remove the if...
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CVjbiVpgTB0P2HxSuZB3e_gSl25wg-WsZFhf_ZUFsmKIczsYvHUEyNmqoP3jizp8ws2NddvMag0ho1_Qa-KgyA8YslgoFaSPNkL-zzXDhnyQToCpxVg3FKXv25KRKkx1.png)
Can remove empty elses.
            - Removing them have benefits for simplifying the control flow graph:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YsaON2k--EhRFbJcVkFji68O5W-0tEj7w9vQc0du3MTLKabk4QFV0NZk0ycA2G1n6temLdDEyxnrQans1lURg3HHEMAHbzNLVlTh_yxKIBt5h7_jqM_UjSRN_JNPutgf.png) 
            - Nested if simplification:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/GxGm9ocdgiyL2wz5MPqiSFPYu_cRhnGeI7a_2dYvdClmN7YSdxpZ3pPFzCAznO8T0Cr5n6kgmsIIRDFnK49jWkpezBHkqQYSvlIVsxSFC1D6yKvXRtTK7wS9aoOBVq4G.png) 
            - What is loop unrolling?→Taking a simple loop, converting that to repeating the body code x times - then examining that code to simplify with constants if possible:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/HBrfRndAuE88l7CmjFbXlm1_cbVi5rrGWv8SFeTJpBGp6sAAuOHzyaJLl9rs0NdOaKj8Az8r5soJtF99uh0jXqU_-le1xz6UJhPiXmTzlV4AFb9NiuhMwyU3fqqK6y7L.png)⇒![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sBfCtI1ljtJBCqYqFiF4NDY1UciiGYbuyiN93hLT7PVE2qDSV9fhqfCyxF6IFCzjH6zykUvptlX6fWqQnWCbfZdfqxHayviyqYmO9ZZ8A3R6UwP0h_TaRHrkqUrdhXjU.png)⇒![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ppDxw4KZ_Np4bz50n4BmgPkyCDYMJluV1zZHU0tvA7F4JxjkCSDkBlJNkSSDeIVNi1RA0BCqy7ia75ddr6IsR7ZOnFgpPpbp0uSxZKZzo-fcWGwmImVKVYIHqyyX6wdW.png)

        - 
    - Lecture 3 - Live variable analysis
        - Make notes on the first 2 slides
        - Liveness
            - Liveness is a data-flow property of variables - is the value of the variable needed?
Are there no possible paths through the code where the variable is used.
            - We thus consider liveness from each instruction's perspective - each instruction has an associated set of live variables.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7LhpQ0vfVgo73hPYfYMrqSIgCu253poqVRFytJt-sQB5O16ji_72p1HYOACyfbiKbmTzGQJQnpMG_dQE99o4c3R_aK79lpcez25Meynl2OtmWbL39LyvNW028JNq1ImA.png)
            - Semantic liveness vs syntactic liveness
                - When is a variable semantically live at node n?→If there is some execution sequence starting at n whose behaviour can be affected by changing the value of x. 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/TrEeQ3JVX4ks8LeeV7HS71OTxNsuyjrTFy6tTKIfF2c5dKZMieBpxQO_v86xDgcitTHGLXxC0CJwY48K-QhVUsPWFl3BLatSdMuzj7CSkn_5hDc5W_OkLmoMa2qzfgKh.png) 
                - Semantic liveness is concerned with the __ execution behaviour __ of the program - this is **undecidable **in the general case. 
                - When is a variable syntactically live?→If there is a path to the exit of the flow-graph along which it's value may be used before it is redefined. 
                - The **path to the flow-graph **is different from saying **some execution sequence **- because not all paths through the flow-graph are real, overestimation. 
                - **Semantically**, we would know one of these two values will be true and $t$ is dead:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/MIOEFGxkdMeVM1KX8fDJu8ThOuNq_UROkOfWf-TGCpuzEfxc3SRpQ3GP1ujYh7twImFuoRdmy-TGDWNbwrmqguH6eLNfBhf1Svq1yx_pVOToqVYIHbTjIvg_RQ2khmO1.png) 
However, it is still **syntactically **live:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2XuyBm--YfAy9rIOVCkjfjPHTAkZGPwJvuWvFe3bF38n1-OV_mRiOtizprYYBfXfBdFXRyVwH2xA5ID-pcSg4bwDFcXMBA46Eh-azUoYAMJ_131QPwsS82EJROKikTPA.png)
Even though this path isn't possible.
                - $$\text{sem-live}(n) \subseteq \text{syn-live}(n)$$
We  __safely overestimate liveness.__  
            - Live variable analysis 
                - LVA is a backwards data-flow algorithm - usage information from future instructions is propagated backwards to find which variables are live.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ESw3qfm-G0QNo24emEt-4N5PM2u3uzDk6xcT36Ty10pFU30KIBF340gZrZlBOuVfk201flgciJJ_srTMDMVC-PwhKoGULKiTle29xuan8wk9c00PuChY0dtQVk9CCp0b.png)
                - An instruction makes a variable live when it **references **it - i.e. uses it. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6vs52I90FDZ1Ve8CUNEXZcV-WEqjWik1lPTpkyVOoVHZ1042oUjXBSDhMj7r8hZc6lPZiEsij9Nt4ic6pYRvUrB-uH2lAyUisKGXDJ3rK8vvy7YN8-elYry_vJgb58R7.png)
                - An instruction makes a variable dead when it **assigns **to that variable.
                - Define functions ref and def which gives the set of variables referenced and defined (respectively) by an instruction at node n.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/hOD7B-30TjHtR9b4DxRB2wjRcVLVfwCNOawsu1f4wjq4UDOBVS0iVESW7cEYaEMS4J59iUZLNLC1L50897eNeLEZF4_D706DYw4614GpW44fp8_nvh7Ug5Try9wQH0KI.png)
                - As liveness flows backwards, we modify the reference sets by adding any referenced variables and remove any defined variables. We have to remove those defined **before **adding those referenced. Otherwise x=x+y would only leave y as live. 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/57E6K0T-1jHjh1VsFcpKxhKnFMNp5oeIbqiW--NFiod-eMmCSeDsb1iqfdIwywXeYgEiUMYuvpvNz8tsGOaKpcZNMMpeDLlk8Dw7cXAeTd6V6WAhdDdI3Sw8v55-BMSh.png) 
                - Note that in straight-lint code: **out-live(n) **is just in-live(n+1) - however not all code is a straight line. So we need to combine separate paths when there's a junction.
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3_DKSBlIIjMw5dkUD89fnpjklZgPTkGzm1x30hiU6qj7XuX7viUwZQMNES0OsLHYOh-lD1gQG0s24sbcOb02M1fhBO8V9fmLMIYJQ8AztR5t50j_-gP5VRymkymeK2BN.png) 
                - We take the union of the in-live sets to get the out live sets - we only care [**if a variable can be used **](https://remnote-user-data.s3.amazonaws.com/5n8Wx3mESanhcO9AWIpVy41ZBjKGbsMesHYEBerBbtQ58aK1W3xCBuZ6yp9MeKPgq1o6-fhZ7CKkjD1IUPA7ZWpW0UjEoBzSObfLMqP5uDN7Gla9D3ZKXDCErJ6uEk04.png)not where it can be used.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5n8Wx3mESanhcO9AWIpVy41ZBjKGbsMesHYEBerBbtQ58aK1W3xCBuZ6yp9MeKPgq1o6-fhZ7CKkjD1IUPA7ZWpW0UjEoBzSObfLMqP5uDN7Gla9D3ZKXDCErJ6uEk04.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/1ucGWUorOVwcPNfg_TS9wTbAwPn-vsMU4s9KvnBrLS3SoB2ZyvkOuvGTXbEUCINU4YgZ4fGH_Zof063de7zz_cjoBdFACu480XH1enMLErlaP4vCmPoJGE--w48ug_Wn.png) 
                - So, we have the data flow equations which we can combine:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/i_d-GcLW1LHIp8GHSeLBkTchUCbSAFIXaUdk9CBg5kXPAE2CRznuHF9QLAWYL7cMd-EkIKJH4Uvxjbkss_FFoT5-GmwNfDIYTjk6a6CIi0Z_t235MmnlkuF4tloUmnTl.png) 
                - What are in-live and out-live sets?→The set of live variables right before and right after an instruction executes 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NqcYMFtMCjge1VDFdYafndxA7QkKm2iNGoAb_SULeZtoQ9z6w0tZlPzlUs7XOicTNLT2tIlzAi6ZGASWWkf7eji5X7p4cbQ1SHjHaqU8m11n_6RZ8xZfAD38W9vzjung.png) 
                - An algorithm to compute this is to iterate over the flow-graph and find live(n) for each variable. Adopt an iterative approach. You **keep doing it until nothing changes.** 
                - What's wrong with this example of a liveness algorithm? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NydHgY-fQf5j2a_1QFeEcpXjmchhXY93NRh53CYxxnwFvvxE3JbbLJcnx-G9voCV2CNFIjjDAFOUX7JYfxTp6_fhUy6st3zh9D8CUAtapEKerzOCcujzUUdCrMYHz7Bm.png)→We've calculated this using {y,z} = {z} U {} (as the out-set for def z would have been empty on our first pass). What we need to do is do our first pass, then find that the correct our-set for def z is {x,y} - then we have **both **out sets for ref y and can combine them. I.e. {x,y} U {z} = {x,y,z}
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/fD1mmwN2WGY8kXLH4RWSwfu-_yAvMOnrCkIOTU-yd4cExegnUpPS5-RUbStotjEVMT3FWkjXq4gL3pc3ldsdPyNy6Ns3gDnqlnhRb7fPWfb8Xe7XrdqHBf5zF7VPM_6q.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yqJa_NlHUvt9LHZ6om3GdzmQ-PdUq_XIp9dxHyOfckcpeyRWGQfhVxhBMugoZoH33wTly32hVmSvmPQs-7Vc9WBSc3IrUqYV0uKggNeR5nrQKzjmWHZ1LEyZQ3JR_4aZ.png) 
                - Algorithm is guaranteed to terminate since there are a finite number of variables and the effect of one iteration is monotonic.
                - Furthermore, this algo is guaranteed to find the smallest solution.
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/k45z2rYxh3tsOeJ9PtGmHyh314UK8JMRnZrLtLi_CmJ6NSp2NhHvPEUROQzlwXcbQ_scA7CaOY93dxonnc3Yc6w2BLdvEGyiNh7WYB89l-_qRS1aypr38sQ_sTB2A41u.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/k-gXVVH5afXkibQb7VByb8W7yypBPUCudAK7NordQ-gRerJDRrZnpAgTQPaJ9BepGWkdiX3LbAAAbS46ViiiH8_ZjJitJZtl60Hb4CK19RVprY4V-A47Bc2nY_zHIAYR.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/R5HslkkDSs_r_Ki6fdYcIKxWI5McUkWy1JYgPhtGbBBYWqp5WR24vkNXf8B9rsGSwCI_61aC0bW0WH-yKjbH5kD6rdbXITr5agLgO0clLKnD9F3HczTkvORqrHQNrXjK.png) 
        - 
    - Lecture 4 - Available expression analysis 
        - Programs can contain code where a calculation is needed, but it's been done before ⇒ Redundancy in the code. The concept of  __expression availability __ is useful in this situation. 
        - Expressions
            - Any given program contains a finite number of expressions (computations which produce values) - so we talk about  __ the set of all expressions __ in the program. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/oXUjYeF4ETtWsc0Y5Jug33khfGkpkkvgTLjwWPjlAS5etC9btLDfOIbIhCNV0crlmpN6qBJO100TDF8b4cW0eMWMCLo_UIrtbACirMHDwexc-OCH7WceNuxplQCGCCPG.png) 
            - What is **availability**?―A data-flow property of expressions, has the value of this expression been calculated previously:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vPo-ziw1fDnmYh--wZNxz931gAD8_Aj-tqX-X3yKqtfdEgLdmKPJ7Qm9eEXZ4I_a5IxmntxGY6Kw17z7iCak8l7F5-43ybbJWmHVYo0mzNSGSG9GmFA14FD3lsBa2Hs-.png)
We examine the set of expressions available to from each instructions perspective, we look at the set of available expressions before and after an instruction. Very similar to liveness analysis.
        - Semantic vs syntactic
            - Availability differs from earlier examples in a subtle way - we want to know which expressions are  __definitely __ available (i.e. have already been computed) at an instruction, not which ones  __may __ be available. 
            - We need to consider the difference between  __semantics __ and  __syntactic __ to find the differenceL 
            - When is an expressions **semantically** available→If at node n its value gets computed along (and not subsequently invalidated) **every execution sequence ending at n.** 
            - When is an expression **syntactically **available→If its value gets computed through every path from the entry of the flow-graph to n. This is a computable approximation of the semantic availability. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/i2T_Z_aFznDWFeVJFezKiUFmkIVJeupUM5JyZeu37nYuX04eniTcnj5ktsALMgCyfBVD6XpihMGJZ5pTB8wBsMUNgroumeL5sXd8RSSGFbySYO9jDstnDG8YIADU3hEl.png)
Semantically available but syntactically not. 
Note that the $(x+y)^2$ will not be available **either **- we don't know their the same things 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/phW3d2mb2HuUNgJ1RpdTZxcImhoYrelTMENrI7qO6F8u0iNkrCa-yX2Vh5Ef70Uc2aa5hGyadcYTsF4RA2IvFSuATy9tC2fxVzSN8XtcwtHuhO_ZQ5yJUj4vedoIGVhk.png)
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/L1pf2Lg2PIs7KieFAu-GY85A-FEjZuWQXy3oEzcxxNNrJrOWdFuiyMtp-hJHSrZ8t6vDqyLwtejZyYtTvBU3BY2eCIetvh7VvdT-76i6lwawFbh8TEkVmmyz5jShVcwk.png) 
        - Available expression analysis
            - Forwards data-flow analysis - propagate facts forward.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/C69vC-La2dpVakbTwcn3x38bHhRY968zt2xg-oDh8iU6AQ5QgfGND2Q4hfk9w0zf_rDxqneHUbm3IT2Nq1fXtOSX4zkx0W02Jyhd7MFzu9Qnpe-wN5UC7aAHZ5TUEthj.png) 
            - When is an expression made invalid?→When it is **killed **i.e. when we rewrite or invalidate a value in the expression. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/WrqglLEEMmrc4cLNKithEOEJa7POFUImHWt3H_CkXUXYj90pf-kaAjtXdAZHWDDJXfOJvGcszmcP4fFVziLyCSqGPtINAFz01elI7GD3LFP1vQQYwW9zsAzMq-Y9E45A.png)
            - We device  __gen(n) __ and  __kill(n)__  - which give the set of generated expressions, and killed by an exression at step n. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-W2rAMovsvQo16Pn_bBk_aICgX_AG-_LBPSrodiHFscdCkBLWT5Op8wNX1yZ9nLp_euWZC78LNSC4DNliEF5_I422fM__siZz7pRHL0hZXh2EgIxpK8H7MnnvwXYmp_E.png) 
            - In available expression analysis, what do you do if an instruction both generates and kills expressions?→Generate first, then kill. I.e. **x = x + y** 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/HH2heGxoUTzFK5_VrFEA07SeWm6Qac_e9swju4x0m3vJcplyJDuaAP9SsMhQiHVP46YwkBZ3HRSkHzshN8it_mVBrSgGEHOetfxyjZ68MX8ozZdji6L1oSxkVhwEtbj1.png) 
            - When a node has a single predecessor, then in-avail(n) = out-avail(m). However, when a node has multiple predecessors - you need to unions the available expressions. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/UghWeHbwgBiWnw8KkXoibJs8CUpIkbBjQIu180Mz3s25THg3fvgmDSH-qe23wl44dMN_MhZB7YX6VD5H2S62ZKQGhQ5_16RwJvuAswqL2PGctQPSZJivInsDK-RZ6SpF.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/OyOFsIRaAJx0SffAveLK4J-c6RRdUf5UHu7LsDcp-zoeR_cHsHOpTAytziKKbCRqZi7khf0QI0V2N5zuePgxiL-mVe4fOa9pSrFwTmNmRej0xJLFDncmHijlSNGGci0x.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/y0p_KXwvYI_OsT9GmjAkdWy0Ma1KwW6Fj8itxKmI9aTrXAbWlPbFxOtnZU0kPiY6TJ_copL1sgt3YT1-CgHLrn05e4ArE7dh1xQ7B_a_yWUfdTiQn4nkaujmATZQbFBx.png) 
            - We must make a special case for the **entry point **to the procedure.  
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9K4X41Ue8n9Ysa3zypJr-NdAt2DiT7HOgoIQmkll2-tkQwSWsp6En8lCnm9RgnTykq_BgqlgdgDnVUfg2ynyw9TX9gSKUyx8fKfAaJWYBiPyQSv_MUDd-2pp79hJ3XdL.png)
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/eNg0z5RhdbFWEMr_fqKmVRX7Z9Zq2slc6S-RLm_ufXzzKrNkBMUyExup4zWJ1rZxS3hVX0TtuO4ucmH6g3HsjAy50750Y5XSXaQ9gP9JFOHwO-Zz1ZKdZiXiNx9TrxWI.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/pzdv9ItxfTtBP8cDtA7eKERHZU7r-GNmAkn8GvY5eE8AAnjQ9KdMu8EDaxSG4i9KD6U3VWGYai1kAmt8ggX2xYnqTy8trFdO03NLtyfClbcDe1hh3raSRqqFVaitoVa-.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/D_C6JSIPHltWLGrLOZ-wrK6XWVjTH9yiFqpRWutDPi1awmGbUQdw5i-utdO2Hr1M4gkE51kFeU2cfH5BfTbGbWmpVoV-GWHDhktsg41Z04o7RzVpatJs_v0TKYVILr5h.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ym_ywoBbW4z_c6CGlsw8ScpavIgUxR1HjHjyO2hvcfi5Th_AdbZRE457U4BsNV-WxT8QJ_H6l9rNO_83yGpiRuov9t6Gpy2402FAiIEx5wFuuq4si1k9ij9xDUKHiNtc.png) 
        - Algorithm
            - We use an array to store the available expressions for each node - initially make all expressions available - iterate over the flowgraph until no new items change.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/UukpZiIbVLNn5WeU41DUijWnjhINWoyYsuAaiBezMaPSypqS7o0hi9p6lujZ3fQoagXLfKiDAEeJys4kMkWOUkKEeypf3HQ8RMXxoHbLMLH7YxTM1r-jFTJ8Fu3tkirg.png)
Why do we start from 1?→Something because of the first initial variable. 
            - As with LVA, this algorithm is guaranteed to terminate  since the effect of one iteration is monotonic (it only  removes expressions from availability sets) and an  empty availability set cannot get any smaller. Any solution to the data-flow equations is safe, but  this algorithm is guaranteed to give the largest (and  therefore most precise) solution.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/K3mIT3Fp6ntQyPLb6wTF3Ee5VW87igajdKLzmXJianSg5q6hSi1lOYdpa8CTlBHo2R7-EWlLs9XAjvs1KLrBrtWYYI3xlki5eDE76FuwPEiJ0objfmUN7abjw-ka5Gkc.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/R9TfCo2Y3cScr8TVrF4HaokRJDu9cZC-TFsOn1cHvPLmwjH_BrFLu9T-B9mpw7tv1s_G--INsj_ECQksCC2cnTb1lzlcCwIvvg_K7uvCfNy1EY4B5RaSnWYUORvJEABb.png) 
        - Safety of analysis
            - Syntactic availability safely under-approximates semantic availability. 
            - Address-taken vars are a problem.
                - we must underestimate ambiguous generated (assume no expressions are generated)
                - Overestimate ambiguous killing (assume all expressions containing address-take variables are killed).
            - Reaching definition - finding how far a value reaches down the flow graph.
            - Very busy expressions - calculating if an expressions is **going **to be used later one. (Along every path). 
    - Lecture 5 - Clash Graphs + Liveness
        - Data-flow anomalies, these are where the program is worse, in some sense, than intended.
        - Optimisation vs debugging
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/fymqpfeYC21uosGYeThKhgVLiEfDSKT7GdSBcDj7tHG7B9WvPMPUZXvu5ca2laULW7Z2kNpp5hLRalmCh-UhMp69QjnaVNPy3L-P0Ry8iRid_MI5Ii6yM027g-1W7SSO.png) 
            - The compiler needs to able to report a broken program (compiler warnings). Allows for optimisation **and **bug elimination. 
            - Dead code is a simply example of a data-flow anomaly, and LVA allows us to identify it.
        - Dead Code
            - If an instruction is written into, but is not live when after it's written into - then it's redundant.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/d6Bugzi-qeUoBHH8GPLnLSQ8zVOupNq0Ak7AN9nnqXZsJLB65p2yum-neDT9Wwu5EXt99Mt96C_sLXTZqzEI32vlMdHSSoQSoYT8UQQCJI5E5aNa9HvIbuTQuQwwRPep.png) 
            - Dead code with **no live side effects **is useless and may be removed. If it's dead immediately after being assigned to - we can get rid of it.
            - Once we remove a line of dead code, other code might also turn out to be dead.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tnyO4B7UQWCGDkbw8TOMpAYY0ua4HzrE7FWMJRbxhTm_ZRmOBnJc8W29GEk06Y-9Ey6hgz6WQxvWAA6LsSE1ZoGilARB4CuSfkmeraFacD0FvEAowCd5xLXNdngzWVYm.png) Here b is dead too. Then a & b.
            - This transformation will keep the semantics the same, but the resulting code will be **smaller **and **faster**. 
        - Uninitialised variables
            - In some languages, it is syntactically legitimate for a program to **read **from a variable **before **it has definitely been initialised with a value. 
            - We would like to detect and warn of this situation.
            - How do we use live variable analysis to find uninitialised variables?→In a healthy program, at the start of the program, all variables should be dead (Remember we flow from the bottom to the top in Live variable analysis). I.e. they should have all been assigned a value.
If there are any live variable, they represent potentially undefined behaviour.
Note: This won't catch every case.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YYbyNiiuMgcOnQ8ELekVKBQCJrtXabS4s7mzU7QMV2IYOs1fNpbDsj_pc6C-sdgU9FUVV1ahRzVdZb01htODBDobA3hBQIXxvER04fHqyq8LEyWCFQo12cfI8mT_7nIu.png)
            - What would be the problem when detecting uninitialised variables here?
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/0EK9n9lyVZkAugR4_D8nyYExEbUkXp3XtmlUmxNp28nD1mxY9uLjJ9UUdQutktbQ_di0Q3ZKffDLf47TrgIf5Tqr7vMR-t0kpagRWjSYqX8bF1camP_hBo5ZklWRZNRl.png)→When we have an if, we **union **the two possible paths. So we have (from bottom to top):
{x} U {} = {x}  - Bottom if block
({x}\x) U {x} = {x} - Top if. The {x} comes from the path where we DON'T follow the if.
If p doesn't change in the ... we should **not **be flagging this at all. 
            - The compiler can't do anything automatic here - the programmer needs to fix unitialised variables.
            - How do we adjust our analysis of uninitialised variables for **scopes**?→We would say that at the beginning of any scope, any of the variables **defined **in that scope should be **dead**. 
        - Write-write anomalies
            - What is a write-write anomaly?→When a variable is written to, then written to again without being read in-between. First write is unnecessary.
            - What analysis do we do to detect write-write anomalies?→Step through the program **forwards - **at each expression remove all variables who are **referenced **and add any that are defined.

x=11 {x}
y=13 {x,y}
x = x+y {x} - This is why we check the referenced first, reassigning y **after **it's used makes sense here.
y=11 {y}
y=12 {y!!}

E.g. x = x + y ⇒ ({x} \ x) U {x} = {x}
            - Just finding variables that have been **written **but not yet read from. 
            - This can cause problems like:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/WvpwXhm1wWm55r8kGFzlNJ1e1hcny-04I8Hm3QfGl1kTC3wi9Etm__wKR3mJCEnnnsFUHMPdxE4I585C3kufftIWR-HcUEDSKXMkedDZu0k61Yc5k-2sqUgsThmEVYty.png)
x **will **be written to twice, but that isn't so bad.
        - Clash graphs
            - We need to map from our temporaries to the underlying architecture.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZRLJvG3w5_fnBBDbJXAZK5BiNKbt-EOuA9r5tHQ3hdRtm7O5yIPML5ufk67XfqNO7VadJ5h84ycnPfBwScKavc77d9FSbjiK4fv-t3HHJ8B2RWo4v6hFWxbYcBBuRRCM.png) 
            - Why is LVA useful for generating clash graphs?→Because it tells us which variables are **simultaneously live. **I.e. Which variables are going to be used in the future so we **cannot **keep them in the same register and overwrite one. 
            - How do we form a clash graph?→We run LVA on our three-address code. Then every virtual register is a node on the graph, and if they are ever live at the same time there's an edge between them:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2ESWYXiE51TTeSaePj_rFQRkw1hud6vjGZbdt3HDeeZH_GJm_-iMoUzLFeBejWCvr8xHsmVemftrag1X1SeWYr-MBBgXlKrIp9AVki0X3d8txqBjFNdYuyMpI10t996N.png)
So we couldn't use the same register for a & z, but we could for z and y for example, because they are **never live at the same time**. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/MPYI3iw7pVG3r64oMC7zhl5E37v247RqADlOJgyAngLG3OJMrGB5incFWKPWClRCrdLG4CUyKP53_cukzLjAJuBUzxZfoU94ky4gUuUk-nFH5Ell5PRWLHwYFGJ8vtSE.png) 
        - 
        - 
        - 
        - 
        - 
    - Lecture 6 - Register Allocation
        - Motivation
            - Normal form is convenient for intermediate code **but **it's very wasteful. Additionally, real machines have a finite number of register - at some point we need to transform the intermediate representation to the **real **registers. 
            - This task is called **register allocation.** 
        - Graph colouring
            - Colour in a graph with X colours where no connected nodes have the same colour.
            - For arbitrary graphs - we may need a colour for each node. For 2D maps, you can do it with 4 colours. 
            - This is essentially the  __same problem __ that we wish to solve for clash graphs. 
                - We want to know how many colours we need so no **two simulteneously live variables are stored in the same register.** 
                - And what colour each vertex should be.
        - Allocation by colouring
            - We first pick a colour - and try and spread it as far as possible (we decide x is red).:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tpkbFJoV-7IVog1IWJ3CRfIzCu3rkrI4Udh6bnMlMh1AzNBI8Ovl8_xWXYRPbh_M_D2ZRtm3djpISyDdrzrczl1eRd2kQa7FIBMQilKVAUPBxtiYM1FcveiE6VHhVj7f.png)
            - Do the same for as many colours as necessary:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4M-4ma6KZ5eGPD1KBFBEug7jP1vdS7j855MnEbKEaelUZE3OSeVj0ZU--hpw7X5MhqvAXll6qiA-Cna8YuGwPSS_43rvkTiINjviMh3ibn5sxQG4CjblC9p7OHjXrohK.png) 
            - We then assign colours to registers!
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/XGNT1ClJFJASrrbf4CjvPgKPdHVI8BUIESJzsi8nQ8bSrGhWbSZL_ydHwBpR9GfQE5WMKuy0yDnHw_TV33ohkHRAdFOVfjaZBtCr0pkTGs5_QVUReAQVoE7xb_sb_KJS.png)
        - Algorithm
            - Finding the **minimum **solution is **NP-Hard.** We use a heuristic which yields satisfactory results. 
            - Describe the heuristic algorithm for finding a minimal graph colouring ↓ 
                1. Choose a vertex with the least number of incident edges (clashes).
                2. Remove the vertex and its edges from the graph, and bush the vertex onto a stack
                3. Repeat 1 & 2 until the graph is empty.
                4. Pop items of the stack, and choose a colour that **doesn't clash **with any of it's already coloured neighbours. We will try to take an existing colour before creating a new one.
        - Spilling
            - This algorithm tries to find an approximately minimal colouring, but it assumes new colours are always available when required.
            - How should the algorithm cope when it runs out of colours?
            - What is spilling?→If we have simultaneously live values exceeding the number of architecture register, we have spill them to memory - these have to be loaded into a register before it can be used. 
            - How do we adjust our minimal colouring algorithm?→If we look at an node and it has **more ** __**or equal**__ ** edges than we have colours **(colours = architectural registers) choose a vertex to spill! (Usually **least accessed **variable chosen) E.g. remove it's vertex and edges.
We then look at the vertex again to see if it still has too many edges.
Continue this until the graph is empty, then perform normal algorithm.
            - What's the problem with spilling variables based on the minimum accesses?→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/w7JQ5qnFE7rAr00sCQqHU__H3cZ5VJbZYLq8SaC9sk5NEQ9_E-bIK4F7CjDEvb7ZLyDoDZdiol0S_Dp-fe5sNpRg1Yo7e3MTocjVAdiYfg1Wc2eMn-hXU4mfNJChpMrF.png) 
Remember, we need to load the spilled variables into a real register - so simultaneous liveness matters!
            - Spilled registers obviously need to be loaded from memory  __into a register. __ How do we solve this problem?→Start the process giving the compiler a lower number of colours than we actually have. Then the extra registers can hold the spillover. Generally we only need one or two fewer architectural registers, as most instructions operate on a max of 2 variables at once.
            - What is a preference graph used for?→If we have a `MOV a,b`in our code - we can simply store b in the a arch register and cut out a MOV instruction.
We construct a  __preference graph __ to show the pairs of registers that appear together in MOV instructions - this is then used to guide colouring.
        - Non-orthogonal registers
            - What is the problem with non-orthogonal registers?→On some architectures, certain instructions **require **certain output/input to be in certain registers. So we can't decide for ourselves where things have to go:
 ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/lyj-EDeCZqJu--thdK7hZR8Oac3_DxP4L-dNyNkmusGpEOcDMvxdExVjAyN-N1rZsgOuR-uxzG7zUGeRe0VHvT_Ug-lbYwE1TLz4QfCv1vtQ5Ja7GpoCmwHCMc5SHXQ0.png) 
            - How do we handle non-orthogonal registers?→We pre-allocate a set of virtual registers to be used as swap-in locations for the **all** architectural registers.
We then adjust our intermediate code by putting in mov instructions:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/HuXwZiEUeh4R7sRuFLO2y2xGh1c23y0IK1JDqjQPR8BGWObSauABmWYprbXuTWBDHX9gUrirCLHfUdUJYTI0gUM4X8E17oND7CTXHfd7PcFhbkBBPT7-bXIF0DOWh3ML.png)
Many of these MOV instructions will be eliminated during register allocation. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/DtIccQ7qL8Gs0sNgPpZJT9hqsiwJmeXIkj33H50iQPXNfWXJ8mL4XR4EdZF4We0Jifl0ZoWAznZ4vF06A4kSkUZOIOCaeSYjkw0z_qSJ4iCtNc_4goFaE9jcHUJRp6Ci.png)
            - What do we do about instructions that corrupt the contents of an architectural register? I.e. calling a function could change v0, v1, v3→We can insert an edge on the clash graph between the corrupted register and **all other live values **- so the compiler doesn't store any live values in there which would have been corrupted. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/P_ZT50O7zRReuMts8wqxxJyfpwgK-XQtD4K20hqKG7zexxh6G8F4Lco6jS_A50rAyZmrWgJQ_z8vfNm7nXN3zvQM85zCdZ22bDKFF7VOEJT_Ow9snc94a2k6shlJ2fE1.png) 
        - Procedure calling standards
            - The final technique of synthesising edges on the clash graph can be used for procedure calling standards - e.g. where a function can expect to find it's arguments.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zlPSzlJB7Jp5WYL6gpcPIGECBzDHCsPRtkN5nRvHO1HMC4QXmRyAGWb2uVU_LXtPVK7i4ywB3iHb7gYU-w-VtpnQpRgXX9zukLKE7wjCD5w4wtQdHXy4o8AQambL7k65.png) 
            - **So, **procedure calls may corrupt some of the registers. r0-r3 and possibly r9. 
So we add edges to our clash graph and add colouring preferences to do the right thing.

We also need to add MOV instructions to move the required variables into r0-r3.
            - 
        - 
    - Lecture 7 - Redundancy elimination
        - 
    - 
    - Lecture 9 - Abstract Interpretation
        - Motivation
            - We want to reason about how a program will behave **when it actually executes. **At a particular part of the flowgraph, we don't fully know what's going to happen and which paths we are going to take. To figure this out, we examine this behaviour directly.
            - We find things out by a running smaller simplified version of the program. I.e. execute within the program or  __interpret.__  iplication
        - Abstract interpretation
            - The key idea is to use an  __abstraction: __ I.e. a model of the otherwise unmanageable reality whie: 
                - Discards enough detail that the model is manageable
                - Retains enough detail to provide useful insight into the real world
            - Similar to a map, it discard unnecessary detail while having enough to comfortably accomplish its purpose. Looking at a full 3D model would take too long, maintains too much useless information.
            - Our plan from our abstraction **needs to hold back in reality.** 
        - Multiplying integers
            - If we want to know if $-1515 \times 37$ is positive there are two ways to find out: 
                - Do the calculation.
                - Note that a positive times a negative is always negative. ⇐ this costs less and gives us the same amount of information.
            - We form an abstract world using an  __abstract interpretation __ of multiplication - call it $\otimes$. 
            - The magnitudes of numbers are **insignificant;** we care only about their signs. Discarding the complexity of all those infinite integers, leaving **3 values**. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/kzdxBEhK3ydmiWOPx8zz1Sz9CJuLpO_Dg37lAk5HwSY3WJBDIgQcteTymrPdxqF7Y9FWmpWzisM3PVTA_BUf0qExccF3Mv5J7HHHVEBQGK1L_z0DW3U_Lvor4xbFzIuc.png) 
            - We then define our abstract operators:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FpPAEvh6t6-3rHTt1DbwA2U9tLlSStg_qaunPjS-TvuGwrZ0LEtISpqjwSzEB3HEnLTIXJcecfTQGEyh0RKBi_iVf1HIIKp8AJK4GmZEQvAuLGqY5s7-jWwHkc3bsbg0.png) 
            - In general the process is 
                1. Define the problem
                2. Devise an abstraction that retains the characteristics of the problem
                3. Solve the problem in the abstract world
                4. Interpret the solution back in the concrete world
        - Safety
            - An abstraction discards detail, you need to ensure that the imprecise results are **safe.** 
        - Adding
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yBJ_LXPEchpfif3eUP5DoGgAqXFqwPysOpMhuNr2X5GVwGunnkFPQpBrup3dPTkUNcJIWGwNGl4Pyq2W2AH-tUOm1s9eNZu8whiYLgSkEI3_Wuve2Xd5F3TfT-6-R-8G.png) 
            - When adding integers, their relative magnitudes **are important **in determining the sign of the result - but our abstraction discarded this information. 
            - We add the **I don't fucking know **operator $(?)$ - this could be **any **of the other abstract values. Because we want the abstraction to be **safe **above all, we must put up with this weakness. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/t6pCEV5mhy9kVJLzAcf7fHTUCTmhUuuOMfLKQXwYD2VdvOn8wUwnbEGgdADhfrQNiK-8NBqZy-fSlJm4D_mtwVQNSl8NQuQ04_gJuGMHxgJWb6_1swQDmkzgNUNGirJo.png) We don't know how to handle this !
            - Safety
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/VB1WSl3cWgJwZMVN0WDZKyNd4LA6oi6b5puNS-xb0uYOcCyne_-vt_ZKF9mo2AjEpYDH7S4lBKvG6CVx0xh5QX5TIqeXVXV2y-G2INdBSf0oHJibosn-D971vHdGj7mn.png) 
        - Abstraction overall
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/96xZpthDjwJSTiSvxo4NamJOhNCqeYsYTtsjGL-pudxhnoWdbbGaf8vziUebMkW1XomTNiHr8cFTomSWCsSs-9u-Ug_yrW5o6hbARJ2hCuqN5LV_2Py1EbT6RrRqgMEX.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/uo9z0oZaEKaOU6927P0zmN8NNonjMb-BK-RLKAOW_-QO6DSCNeA8AF6ktl3g-GHsV5FjC_9HFRzYDmEUUNK9PEWzMbFA_V0wygYf0KMnoOqmOzA_US5KOvBMB8aWB7q_.png) 
            - 
        - 
- 🔲 Advanced Computer Architecture 
    - Lecture 1 - History + design choices
        - Best design varies over time and depending on use case - which direction do we take in trade-offs.
        - **Architecture** - set of specifications that describe a computers. Includes the instruction set
            - Architecture specifications: A contract between the hardware and software. Many different compatible processors may be implemented to achieve different goals.
        - **Micro-architecture - **The logical organisation of the inner structure of the computer. 
        - **Hardware or implementation** - The realisation of the physical structure, i.e. logic design & chip packaging.
        - The  __Stack
__ ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/DT0kJDxW54nNUfu948kOdM66RVtAUaEFV7QokCPWZuEvVkXtZWUPJGVW9gMTU60zP166KP-znmVebVFsLLjZ4qow2SJgmFOeGQFw5Bsvclxbr0bNB5Zuz6pVF5sSgNOW.png) 
            - Each level imposes different requirements & constraints.
        - Design Goals
            - **Functional **- We want the thing to work and  __be correct__ . This is hard to fix, verification is the highest single cost in the design process. We then need to **test **chips once they've been manufactured - coverage, cost, testing etc. 
            - **Performance - **what does this mean? No single best answer, depends on the workload/use-case. 
            - **Power **- keep power consumption down. Limits the performance. 
            - **Security **- control access to sensitive data 
            - **Cost **- Design cost (complexity) and die cost (the size/area of the chip - the bigger the more expensive) + packaging. Packaging means you break a chip into **smaller dies **and the combine! 
            - **Reliability **- Do we need to detect or tolerate faults during operation. 
        - Markets and features
            - Each target market requires a different trade-off in terms of power consumption, cost, area, performance, etc.
        - Historical performance gains
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CXdyjj0EMGKXThbSDj9PUm-h-4noF6GEQ_88ZXY3asOSsQfwEcCpJuBRyrp-U5wtdwKBtDvPmEdNNeQIu3qe3jUhE-qGf6NavQcRxmbQ8dzkQRP8rMU87cyDtbovQuFV.png) numbers of fas
Note: 52% improvement year on year for ~20 years. 
            - From 1985-2002 performance improved by ~800 times. Over time technology scaling made transistors faster and lower powert.
            - Time = instructions executed * clocks per instruction * clock period
        - A shorter critical path
            - Why might we want a short critical path?→The critical path is what limites our clock frequency - the shorter the faster 
            - Can be done by inserting additional registers to split into separate pipelines.
            - Length of critical paths decreased **10x** 
        - Instruction Count 
            - Increased datapath width!
            - Larger register files so fewer loads/store instructions
            - More complex instructions? ARM vs RISCV
            - Single instruction, multiple data - data level parallelism can help
        - Clocks per instruction (CPI)
            - Earlier machines transistor limits meant multiple clock cycles required for one instruction.
            - As transistor increase we couold aim to get closer to a CPI of 1 (without our clock frequency being **low!**) A longer pipeline makes getting **cpi & clock frequency down very hard.** 
            - Instruction level parallelism? 
        - Note: Of the 800x improvement, 100x is from frequency and 8x was from other improvements!
        - 
    - Lecture 2 - Core performance + Dennard
        - Better fabrication technologies lead to more markets ⇒ Moving from the room sized computers to smaller microprocessors or higher performance processors or low power processors etc. 
        - Transistor number increase was not the only cause - increasing die size also contributed.
        - Limits to single core performance
            - Limited pipelining - trade-off of frequency vs instructions per branch. Flush loads of instructions when hitting a branch.
            - **Cost of interruptions grow** - higher impact of cache misses and mispredicted branches 
            - Some components v difficult or expensive to pipeline
            - Practical limits for very high freq clocks (we have to distribute the clock + has to arrive at every register at the same time. POWER usage) - registers represent a finite delay?
            - Limits of instruction level parallelism
            - Difficult to discover and exploit instruction level parallelism 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/oZLLhbC5hMcGbZnW5zvDOIgQ-YP1Acve9N4-Lj1azmVDwokBMz7t1IGzejcw13ZBVk6I46bJMsdVhDl5_aaOz5_tmBMXD25K8EK7Fk1BtmwmE8BLeqmmdw6jX2DS_PCy.png) 
            - Dennard and Post-Dennard Scaling
                - Dennard scaling allowed power to remain constant - transistors were made smaller, the number of transistors doubles & the capacitance decrease to 1/s.
This works because we can push the supply voltage down, causing the threshold voltage to fall 
                - Post Dennard scaling, continuing to push threshold voltage means the transistors **leak voltage. **This leakage voltage grows **exponentially **as we push down the threshold voltage... 
                - 
            - On chip wiring
                - Smaller wires do stuff...
                - Wire delays scale poorly compared to logic delays.
                - This limits the amount of state reachable in one clock cycle - bad for large complex processors.
            - As a result of all these problems, gains slowed from 52% to 21% per year for the highest performance processors in ~2004
        - Multi-core processors
            - Increased performance from multi-cores was cheaper than via single core frequency or instruction level parallelism. Lead to shorter pipelines and more power efficient processors.
            - Power consumption may limit performance.
            - Need to write parallel programs.
            - On-chip and off-chip communication will **limit performance gains. **Off-chip bandwidth is limited and may throttle our many cores. 
Cores **need to communicate **to maintain a coherent view of memory.
        - Specialisation
            - Look beyond general purpose and trade flexibility for efficiency.
            - Rather than the ability to run all programs, design for a narrow workload (could even be a single algo).
            - These **accelerators **can be 10-1000x better than a general-purpose solution in terms of power & performance. 
            - What does specialisation allow?
                - Remove infrequently used parts of the processor!
                - Tune instruction set for common operations
                - Exploit forms of parallelism abundant in the application! Specilise for your target area!
                - Instantiate specialised memory and tune widths + size
                - Provide specialised interconnects between components.
                - Optimise data-use patterns
            - Note that for an add instruction, only a very small proportion **is the actual add **:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/kcGtrhz3NxkJoQPWq58DNVu8DkoLfwcdJdwMgpgt5jdLopYLGkxAPhPanprPg6fopFZeMoi5AHBcBlQi_eOjiDCrNyO7O3DFhbTHM2RcAju_aeFkkXfIqvqnmAl2SYwH.png) 
We could specialise for a specific domain we could reduce this power usage.
            - Limits to specialisation
                - Costs when designing a new accelerator
                - Chip may only be competitive in a small target market, reducing profitability
                - Specialisation reduces flexibility
                - Specialisation is also subject to diminishing returns - can't just keep pushing down.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JlU_AJXZMjFJHLFgR1C9ZxU_6MWR7fmyLFwReSz1mvj0Jr7LzZqucepLao7cgf0YCC9-si3hyhoQvXPNXcT5ib-mP0xDc9DjsAwE4eVfgTcg4weCx35o_OgK7uTzg51a.png) 
    - Lecture 3  - ISA + Pipelines
        - Fundamentals of Computer Design
            - Speedup of a part of the system is limited by the amount of the time that system is used - Amdahl's law.
            - Complexity - seek simple elegant solutions. Complexity adds to design and verification costs.
We want to  __understand what we have built __  __**and **__  __predict how it will behave.__  
            - When you add an idea - you don't initially have an appreciation of how it will interact with the rest of the system. What are the costs.
        - Instruction set architecture
            - Acts as the interface between hardware and software. You can decide where to put that line, you could give the processor high level code **or **tailor the instruction set to allow for a high performance implementation. Co-optimize the instruction set and the pipeline. 
            - You could also provide explicit information about how instructions are dependent on each other - makes it easier to make parallel.
            - AArch addressing modes:
Pre-index means that the source register is changed **before **load
Post-index means afterwards:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/wXYDk-SPulhgczXF-oTVQrrW6VgaD1l6cALYlOIMFOL6Ff7HwKkxQr45u_W3wPQ6XGCDAbaZ6CemP0iY81oMcFDJ8F0FE6gTXKm75ZQwFupflplO7seVTzfZkeuGUaGr.png)
        - Advanced Pipelining
            - A simple processor:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gDqzpjHPJc0gq8OU46Cd4SefkU9dCvB1SPjq4enECC5RA8zsJiz-liD-UZnHzB3V6tg-p_oFbrGnaEQHPoIVjMCn47C5GKNKQFrlozRSTO0ElF_3qMLyUrdSWO_N29Yu.png)
Instructions per cycle is one here. 
            - Minimum clock period wil be the worst case delay between two registers shown - this does vary with Process, Voltage, Temperature etc.
            - What does pipelining do to latency and throughput?→Latency will increase (it takes longer to execute each instruction) but throughput also increases.
We don't care about latency, we care about **throughput.** 
            - Why does pipelining improve the clock frequency?→During pipelining we add pipelining registers in the middle of the combinational logic - this reduces the worst case delay between two registers and so we can increase our frequency: Half the worst case, double the throughput.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/rzW2j5TZIwaPK5a01AKe3Hv6VlXxZp1AMxjYXAlMIOeZZtO5J0w7-eZH_9ocyDxgLr1F-acdvzGdkdM37rV3lutVRVwNMTyf5vHafGGwDLmqnZG7Tmq_Ksn6OP_SDD8k.png) 
Note, this does add a pipelining overhead due to the register! Means the gains are not linear.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/UYclCaCWZg7coWo4mbFoLzSN3vO4fLT4WydRon-mRZ6zYJ8xdWOH_5_vzHyirfwKpMbxSYamuYQHM4-QVW9y6pZMRR_CTe7Y-7CYvPZiMmYrmAY54u3PhTd-_m7hbL8M.png)
The control information about each instruction needs to move down the pipeline. E.g. we need to remember what register to write back to.
            - An ideal pipeline
                - Ideally our CPI would equal 1, but in real life our pipeline will stall and the CPI will increase.
            - Stalling to access memory
                - The latency of accessing off-chip memory is typically 10-100 times higher than the clock period. We must use on-chip caches.
                - Why would we want a separate instruction memory?→On every clock cycles we need an instruction and on 30% we'll be accessing data memory. We'd stall every fucking time [😩](😩.md) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/iy_TF4v_Z3CVCRahVyJOgpxFeUuGbdE7CgjWewfZknb6t1wDJhV0Yk0sVZ3P6djV30eXTOQ4IWJtVC3hqBYVWSFBMbRtWZs52_4AJMtvCDTlxY4p4vnCe6SnX575EFyB.png) 
            - Maintaining correctness
                - We need to ensure results from our pipelined processor would be identical to an un-pipelined one.
                - Structural hazards
                    - Arise from resource conflicts. I.e. instructions may bneed to stall to wait for access to a shared resoucrce - i.e. a register file read port. The registers may be full!
                - Data hazard - need to respect inter-instruction data dependencies
                - Control hazard - caused by instructions that change the PC
                - Data dependencies:

                    - True data dependence (read-after-write) can be solved by data forwarding. Two adds - output from ALU to the input of the ALU. Second instruction is data dependent on the first.
                    - Load-use delays are always going to be slow...
                    - What are name dependencies?→When two instructions refer to the same register 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2uYpf_NDpb3iUj-9OZh5UJv7k6kiVFxOuyqcZvRfdi6HIQ2wPy7Uv0wRv9GUpUA_VwzX91H8xii3MqginM53MzmjpGvrjzhsFke7TomqpeY52eAVNTIkHWD2MARB1yrP.png)
We can't reorder lines 3 or 4 - we'd get a writer after read error.
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tJZmQP1VtHRtQTaynnmMfLDgYnU_tXZmhZmg7zLliLMe5j3-dMYC0GVYhySvO7xXexyBan8PXmQRF96pkkN6pNBXgmbAofOtlCaiW8Rt_XtFVvXQMdrdoMjcfpeVvdg1.png)
We usually get around this by **renaming variables**. I.e. the instruction set has 32 available registers but we have 256 to work with.
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/aCwuvR_O7_lr8Nao7WGjxMbSMXjtGyWwNGyHIL5lr_v8ICtPmN7_L7O67vtuKGTYtsZX6g8Ikc9QvpUA96X2AxRy1sS5aqdcWaMg2rw5j48sOrl3bQWuaVFnxnRKa__t.png) 
            - Control Hazards
                - If we don't evaluate the branch in the decode state - we'll have to wait till the execute stage till we know we have a branch. Then we'll have to flush two instructions.
            - Pipeline Control
                - Hazards often require us to stall our pipeline - but this stall logic **could add to the processor's clock period. **One solution to this is to design pipeline sections that **cannot stall!** 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/rvaE7shneYFDzqCLgfLpW8i4ohNx39V_xvglzykkn74LsSimvjae2EfMDrIFAGfB9_JTMjtptkf3j8wCTDCXOeYvSLqBHErk9wLqgaeThjkZro2uHXe44t1_kBlVA5S-.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Rln8Wa7M6kdWSWxc_JPQyPnzUdybSiakIDom5dWS7QdNA1841gwNTsLpwwFsVrVCkqjHHS_3n8j0egDyWsMRDHP62p3FlWrBUZiYti93SNeFJfeQn0FBsd5313Qlq_yB.png) 
    - Lecture 4 - Multiple execution pipelines
        - Multiple execution pipelines
            - It's impractical to require that all instructions execute in a single cycle
            - Instead we form different **length **pipelines. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/T73H_deXyIqJvsBphb0FLxxDVH9nTt5mhCPju5J4u03F0aw8UlsX-ANIAEz8v5o1jtHKLSzj3yrqhPotyizUNz8_ZItF0Evv8Cn--4TtnQOWE_uWqicVmvGUsUi5sQM1.png) 
                - 3 instruction fetch stages!
                - We need to know as soon as we get an instruction that it's a branch
                - One small branch predictor and another larger branch predictor that's available **next **cycle. 
                - Different operations that are pipe-lined - notice that the output are fed into an output pipeline, this ensures results come out **in program order**. Otherwise shorter pipelines would finish first. 
        - Diversified pipelines
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/BXnTD_LvZGID8TYJSEcKLss1fFeRXfZvlHvQ_tkLbaNaMWhcPoQH24lGTARe0MD-kewq5mtVam2jJvA50ib5blFhlhugICdIMVjuH9yPotsH_dTlOpPrDrs0t75vWhqZ.png) 
            - We can sometimes allow pipelines to overtake each other. I.e write back out of order.
                - We need to make sure that contentions for the register write ports are queued. (If two instructions writing to the same destination register happen at the same point)
                - Careful about Write-after-write hazards
                - Out of order completion can cause problems for **exceptions **too 
        - Example ARM10 pipeline (1999) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qqYvNxLGoy5fznuL8Z6LxFZLgT2-xlHHAc6Is7sjwCZB1sdWECWco9yeiRVQPWs_DIbpugayIND8IxuB4yh2obkgUvvgORlZKcF6zN_bBz-mYWoJSbdwis13xI1s3JQH.png)
Stored in the Data cache before put into the register file. 
            - Data Hazards
                - Cannot allow all ALU instructions to bypass memory instructions - must respect dependencies
                - RAW or WAW hazards
        - Pipeline CPI
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/O3xt3KZbi-GDlAkp1O63f8-fHeFzDVUHausFeOqRjASLHk8l7MRtzhDiiAyUVnIw1BTLmtREm590ZmmiebOtcEtb8joEM7JJm6QcC4Z36a-FxguRqOYNoKRGidrhoBAd.png) 
            - What's the tradeoffs for creating a deeper pipeline→A deeper pipeline can have more things going on at once, so the CPI goes down.
However, the longer the pipeline, the higher the cost of exceptions.
Additionally, longer pipelines mean smaller distinct sections - these sections are fast to compute and allow for a higher clock speed. For higher clock speeds, stall times due for memory cost more cycles.
        - An analytical model of performance
            - Examine a critical path of delay T, divide that into S stages f delay $\frac{T}S$. Then add the clocking overhead, the delay of the register:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/RBLqwudzLZusiRhtl_54BS716NypPtMqwaLOmgSGQjnmeQjoFchqD6qkvJQEBWnL6U6DOZk9o4_BVMOnf_TbhIe7aPGo-JK8t95GYqw5ejYLHknk60nCAp1ZIFgYSLj2.png)
            - Using this, we know:
                - Pipeline CPI = ideal pipeline CPI + pipeline stalls **per instruction** 
                - Freq = 1/ (clock period) = 1 / ($\frac TS + C$) 
                - Throughput = Freq / CPI
                - Lets assume stalls occur at frequency b, and their cost is proportional to pipeline depth (say S-1) so:
$$Throughput = \frac{1}{1+(S-1)b} \cdot \frac{1}{\frac TS + C}$$
            - We can plot the number of pipeline stages against the performance:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/MG3MIj_tgYSSBylHPWo0FKEfwhFRCoU8IA4sLo9fBD9z3XHshx3YpeEv7fONTUejNffaAqk_4Vn7dYN0qE0GJB7caYhIe3QEe02qGxebKwne2JH9oCJ37yWGQjBj6gla.png) 
        - Typical pipeline lengths
            - Area optimised cores may have 2-3 stages. 
            - Simple efficient scalar pipelines usually have 5-7 stages
            - Higher performance stages could have 8-16 stages.
            - **Becoming shorter in general, we've moved to more multicore, energy efficient cores.** 
        - Control hazards
            - What would we need to do to reduce control hazards, when we fetch a branch? ↓ 
                - Figure out that the instruction **is **a branch 
                - Compute the target address and branch there.
            - We would like to calculate the next value of the PC in parallel with reading our instruction memory. This is **hard,** as a branch may be decoded/evaluated later in the pipeline. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Pt40cCic1v04u6kGc5-SwLi5gditF0YUbbzuIn64ZEoE5liFff-nmo-WWEopZjFpiUcYW91KVBL6T67hCm3kqA4OvEq9L0TjduSq6lVNQfCJY-59fa_mGGS-vjv7uFG9.png)
The two instructions after become NOPs - wasting two cycles. 
            - Option 1: Assume the branch is  _not_  taken 
                - If we evaluate the branch in the execute stage and 60% are taken (and 20% of instructions are branches) we get:
CPI contribution from branches = 0.2 * 2 * 0.6 
New CPI = 1 + 0.24 = 1.24
            - Option 2: Evaluate the branch  _earlier_  
                - If we bring the test into the decode stage, we can check for a branch (with some simple test) to save 1 cycle.
                - Need to be careful with data hazards - may need to stall when calculating values **used **by the branch. 
            - Option 3: A delayed branch
                - Rearrange the code (with a branch delay slot) so the first instruction after the branch **can be executed:
**![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/nx3FqQH4WMwBjNuVlAgOEWjMGc_q_euFUQdBBEiSCerhaKukWxV3CYgqV76pkpdr6JGgVayhAfQty7ATtup_KXjKr7rYiEvN7UVkffJNHoYaJgRMdQjiwVOUwm9_SYp3.png) 
                - A compiler can usually fill it 60-70% of the time.
                - Could add more, but the idea doesn't scale and quickly becomes a burden.
            - Option 4: Branch prediction
                - For high-performance processors with deep pipelines, why are branches more costly? ↓ 
                    - Branches are decoded later. 
                    - 4 instructions are fetched at once, and 3 are decoded at a time. So we've wasted more time.
                    - Due to these -we may discard > 40 instructions if we flush due to a mispredicted branch.
        - Static branch prediction
            - Exploit that branch instructions are more likely **to go backwards than forwards. **I.e. loops.
Assume it's taken if it goes before the PC. 
            - Accuracy around 65%
        - Example: ARM10 processor
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ByknHhpUnbNJgc4GtuCIeS-2YJENgq21ebQiGpS_Jcu6LgPr7rLOJizJYHZKV2_afaDino9EjfypHBuytlbpkFluZBpmPsajz8X-3AdDggW-mkjN6BccqO6DZVFbmx4p.png) 
            - Could dual issue branches and the first instruction of the branch.
        - 
    - Lecture 5  - Branch prediction & Exceptions
        - A simple one-level dynamic branch predictor
            - Predict a branch was taken only if it was last time. We use a simple table of 1-bit entries to store our predictions. How many incorrect predictions would we get per loop?→2, one going in and one going out. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gf5QGucpdrMYrM-JgHk3xtM3mcBax0q2rDUFCI049aGh55fv6ORJgK-vYR5bQMN2RD7kuGMQbX-vjVWrqqky1oRmj2hxewszu7yHvPg951VNqVOLGQ9h0fBdKCuYG8Wc.png) 
        - One-level branch predictor
            - Describe 2-bit saturating counters for branch predictors→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/v5RIgNL8l2QT8DB_qdnsDR_Znmt3QV3AgqdIJEeAQVT5apsJn2nN5d9ZznVCxjBL_n7fHC7V_tfnzHXdXupGyiH0RkE4YAAgoxpk3mufUuLOikxhn1TSRY920KNtwUqi.png)
Taking the branch increases the counter, not taking it decreases it.
If the counter is at 2 or 3 we branch otherwise we don't.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/IZnq1jeGkHSp3lNZ5_GAVy8HgyK2tEQEnX_bdXAd-1AYdwE3DzTjtf_QUyuIIciascyhCIMG-Uoq_YP0C_yTukF3gMczige0KwNIZPYF_i9JUK1zSNyjQvubnpkDSu9M.png) 
            - This means we only get **one **miss every loop at the end rather than 2. Basically, we only change switch from predicting a positive branch after 3 incorrect guesses. 
            - 2-bit saturating counters are as good as any more bits.
        - Correlating predictors
            - How can we improve on simple bimodal predictors?
            - We take advantage of the branch being correlated with the past outcomes of itself (local history) **and with the past outcomes of other branches **(global history). 
            - Local history
                - Look at what **a particular **branch has done.  10101011011010010110
                - Two-level predictor
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/syPcAZAtF-GsJtE1Ui-VICLaG-YIb2nNorYAqzYWz4DVIfiLSJV4844rN38O8oRvBA8cU0S5QBsOQQtd7u2ETkrd2a7sW8z7es7Byk4inaRSY2ApdwGlVLOEH4osGqMG.png)
What does this two-level predictor do?→First we look in the branch history table, this gives us a record of what this branch has done - e.g. not taken | taken | not taken. 
We use this to index into the pattern history table, this is a collection of 2-bit saturation counters **for each possible history. **I.e. If an if then branch only executes every second time - 010 will lead to a branch, while 101 will not. 
                    - We have two memories - the branch history table and the pattern history table.
            - Exploiting global branch history
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/QgQ_kU0nzmOAnzLXyoC9xSQK5iW5sNOcz6DOeaFeFNTtqwOZv6Y84nks9Vc4da4XIm5_50tE4gXEv87Fi_VluoAVvYqlX9Z_L1992SbSWQ_c7K6ZMPw88T7X4AxFf_Hh.png)
Branches will be correlated! 
                - Explain how global history two-level predictors work→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sJXU0Pm0h-noX4lHyZHpgCIdG2ktB5wh7T9BuUbeNhkKjWoylI-lyv9KtX7dAmStvF6q01i-rJOSZnWGyaSDt5xye_aIVvvbynGEzkqhBnHwn9X4L4yw1NVvi6VoJ9DZ.png)
We examine the global history of all recent branches - then hash that in some way with the branch address and look up in the Pattern History Table.
This just stores a 2-bit saturation counter which we use as normal.
            - Optimisations
                - Tournament Predictors ‒ More advanced schemes employ both local **and **global history predictors. Another predictor then chooses whether the **global **or **local **predictor should be used. 
                - Aliasing problems ‒ Many branches will end up **aliasing **into the same place in the pattern history table. You could put problematic branches in a small tagged cache.
            - Dynamic branch predictors
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/b9dri_FQgZPa-iKiCSSSFTAk-j0N3py23a7NId1ChG4MSBfN-rGa7eChBd97PEjTPLVmKAGKjyntXgtWlnbYSOENdKumGbIlPru7Fz188gPOPCipYUpymCw9oCXPmwDi.png) 
        - Limits to dynamic  branch prediction
            - Give 4 limits to dynamic branch prediction ↓ 
                - Some branches are systematically hard to predict
                - These all need training, so there are going to be some problems
                - Some branches are going to rarely be encountered
                - Predictor accuracy will be limited by the hardware, cycle time, hardware area
                - Aliasing + interference.
        - ARM Cortex A-15
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/m5zUSkfuH8siUywt2WjrgyjRkfs4KQi6J5TQywEJss1stuQWy6Tj7gP9w6aljJLH7ELGQ1RREO4tWo17huXh7wFprL3vFHCx5T3NBVCELWn1jN7aNZ1PYvUXLwl2smw7.png) 
            - The branch predictor consumes ~15% of the core power !
            - Bi-mode predictor
                - To combat the aliasing problem, separate the normally taken branches and normally not taken into two two-level predictors.
The choice predictor decides which one to use.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Xjq36ZNTKpnU7puNt3JdVKOKwnEUHQR4qkYj9h391SJD1NvwYqx7DUCR22o22k4Vldj_EjveBt8rEVHO4y4P1c2skQNV4ygbyqoG45vicYtyHHqRUNQsj5qHaW7c3Rwo.png) 
        - Is branch prediction a solved problem?
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qzTjzqJwC4cNgsQBPlZhTS_BTLLkAo9tYJv-W5ognhNwcBCkW--YPi0T8ABupwCgAlwv6C6rwOpWK4anztz2pGRMwe6RSTLRplbf_we1H9j4SxHNnrfGRTpOS9vZeq50.png) 
What is this graph telling us?→Branch predictors limit how complicated we can build our pipeline, we get diminishing returns. (Note: the X axis is exponential and Y is linear) 
            - What does IPC stand for→Instructions per cycle. 
        - Branching without stalls
            - What do we need to know to **completely avoid **stalling on a branch 
                - Need to know the current instruction is a branch
                - Need to predict if it's taken or not-taken
                - If the branch is predicted as taken, we need to know the branch's target address.
            - What is a Branch Target Buffer?→Cache of recent branches with the target address - tells you if a instruction **is a branch **and where to branch to if it is (also what type of branch):
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/n2QjD2s13QD8tQ6xfWmdwroG7lMgi3lw-p94RitaFRrK6njTqDVURmnUCMU_pRdYomDwD9JxcnonibLWNuttqCLxMjLjBA42bVevVvs97zKA2ybDnSYF61jYkDRfjghj.png) 
            - Explain what's happening here when the PC is incremented
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/c_N2Uot2og3jcqdvwjNN40NUzlBHUwxif1mWGKv220G6vIJsn4dxq3eCbXaXx4MK-hMuNYOAZRsBwaVbUUh77jBPo4eLxtePPFpM-ND1CdmNazA96yeFh2wLHqy8368J.png) ↓ 
                - The next PC is given the next instruction in order - i.e. PC+4. 
                - The branch target buffer passes if the instruction **is a branch **and where its target address is. 
                - The Branch predictor says whether we are to branch or not, this is anded with whether or not the instruction is a branch. If both of those are true, the next PC will be the output of the branch target buffer.
        - Other BTB tricks
            - We could store the **next instruction **in the target address in the branch target buffer - this means we don't need to fetch it, just start decoding immediately. 
            - We could also create a seperate structure to cache these
        - Return address predictors
            - What are indirect branches?→When the target address changes - we could have multiple entries per branch in a BTB.
            - Functions may be called from multiple places in the program, why does this present a problem for branch predictors and what is the solution? ↓ 
                - Near impossible to predict where a function is going to return **to ** 
                - We produce a **return-address-stack **storing locations for called were called from. 
        - Exceptions
            - We need to interrupt a program's execution, pass control over to the **exception handler.** 
            - Synchronous exceptions ‒ caused by a particular instruction. These are precise, can let all previous instructions have executed
            - Describe synchronous vs asynchronous exceptions↓ ↓ 
                - Synchronous ‒ these are caused by a single instruction and can be handled precisely. I.e. we can wait for previous instructions to trickle through the pipeline, then save the processor state and defer to the exception handler.
                - Asynchronous ‒ These are generated externally, i.e. unexpected memory error, interrupt from the hardware/peripherals.
            - Describe the process of handling an exception ↓ 
                1. Save the processor state.
                2. Save the return address PC.
                3. Get the exception handler address from vector register and jump there.
                4. Save the registers state, execute the exception handler then restore the register state.
                5. Return from the exception handler (ERET command)
            - Precise exceptions and pipelining
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/oqwEgbApEQPkUw2o3RjrbJfeLHtK_rLH1si7-kkwCaXslzINGlrNrywnzTrwfrcYnfbIYrGKCap22d5sYEh2CjLq_SEE8TeXr6zrmm0sOgwHlwhATUVaMZQDEv3-gAyF.png) 
                - We can't immediately jump to the exception handler, need to handle in program order.
Wait until writeback and then flush everything before
                - How do we maintain program order when handling precise exceptions?→Ensure other instruction shave finished by **only handling exceptions in the writeback stage.** 
        - Limits of pipelining
            - If we pipeline our execute stage, we will need to find successive independent instructions to keep our instructions from stalling.
            - Need to pipeline our ALU.
            - Registers and clocking overheads are non-zero! Can't have 100 stages, these will dominate.
            - Need to balance logic between pipeline stages, clock period is determined by worst case-delay.
            - Limits on the number of pipelining registers
    - Lecture 6 - Superscalar processors
        - Instruction level parallelism
            - Generally there is a lot of instruction level parallelism.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/d-sGDcty6K41OGNk63og93OqCFGSle1X9ffexcvWpRwDmpxRxoYGsjP2311Ir66aIoI3tpgU_fAKgm6W540cjgEYbxdzvr9QCylkOkKl_XEcflvCjUltysaSq_Z36Lxa.png)
            - The question is, how much can we capitalise from.
        - Super-pipelined and superscalar processors
            - What is a super-pipelined processor?→When the pipeline stages are further divided into M substages - e.g. an ALU execution split into some number of smaller operations
 ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YNiu1gjPCZYVp7ZsCNlwFDTFLSdPBrynJNLgcD4q1dQ3A0RGDGsI5WDbn2_uIUO3VHB1PmETiwUROYC1LmxzqCzqBTzsHwbzI4fXxOA7zFYVUXSrjjakMkyY6thKku1y.png)
Clock can be made M times faster 
            - What is a superscalar processor→Multiple instructions are processed in each pipeline stage - meaning the IPC $\le$ P.
Fetch 4 instructions, decode them etc:
  ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FWeDvcKaVEqKnfCSxQfDQr3IFHn3VjgLTh13EUx7pyhIP1v-t-1NYUq0bPR8pQ88e-Xaz60wjeeZvkfuldofK8QfXiujUAVm7_Rq1yXpjJ2kUVHyrPqy5Ui-CZmOlo_0.png) 
        - 
        - 
        - 
- 🎲 Randomised Algorithms 
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
- 🕷️ Cybercrime
    - Case Study Notes
        - **Critically read the weekly reading assignment.** Only 2 papers a week. 
        - Present a case study:

            - Cybercrime event / series of events.
            - Should be sufficient objective information about the event for you to consider. Make sure the offender **has been prosecuted & sentenced**. This ensures there's enough information.
            - Relate this to the academic literature related to this incident.
            - If it relates to subsequent essays - leave that out.
            - **Can go 10% over.** 
            - Argument ⇒ Evidence to support your argument. Have the argument throughout the essay, don't wait until the end to reveal it.
            - Careful how you **choose sources **journals, social science journals, academic articles and computer science conferences papers. 
            - Make it **accessible **don't assume that the reader knows what a denial of service attack is etc. 
            - Don't be general - e.g. don't write 'Cybercrime has increased exponentially in the last decade', **not relevant!** 
            - Signposting, the first X is this, the second X is this...
Use reader instruction to signal when you shift gear, 'now we turn to consider this...'
            - Intro ⇒ tell me what you're going to tell me
            - Body ⇒ tell me what you're telling me
            - Conclusion ⇒ tell me what you told me
            - Don't use headings, no bullet points, no figures, no appendices.
            - References!
            - Wordcount excludes title & bibliography
            - Department heavily penalises late submissions - NO EXTENSIONS
    - Mirai Notes
        - Paras Jha github: [dreadiscool (dreadiscool) · GitHub](https://github.com/dreadiscool/) 
        - Attacks on ProxyPipe - abuse complaints that kneecapped Mirai.  
            - Goes on to spam ISP abuse complaints - DDOSs Frantech when they didn't respond in reasonable time. Before he did that he threatened them on: [lowendtalk.com/discussion/91889/need about 5 dedicated servers/p2](https://lowendtalk.com/discussion/91889/need-about-5-dedicated-servers/p2) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/aT6HR7p2lTT8_9o4-_qB0Tfe7Ne1KijpM0xMs4rq8WjLRMmdArMzLXCYB_Hk-Qwj96G4JWA4ikUlIM46D13rzdeb6KqixtAW1QsQrercH2Tpy8uxXzD5ZoQszm4-a7fD.png) 
        - **Rents **net-spots - i.e. chunks of the mirai botnet to use for pre-arranged periods of time (starting at $5k a week). 
            - Also paid to DDoS Hypixel
            - Client was upset about an article on krebsonsecurity - so paid to attack it. Supposedly Paras didn't realise.
        - Code in Mirai looks **very similar **to code on github (not 100% sure on this: [Paras Github code](https://github.com/dreadiscool/LastProxy/blob/master/src/network.c?aliasId=spMrMora9IYzb8Cym) - [Mirai code](https://github.com/0x27/linux.mirai/blob/master/mirai/bot/attack_gre.c?aliasId=9l3DsTmFEAu0ftNAm).  
        - Previously his account nickname was OG_Richard_Stallman - with an email ogmemes123123@gmail.com, this was used to create a facebook acount under the name OG_Richard_Stallman which included that the OG_Richard_Stallman studied at Rutgers university... (the uni paras studied at) which had been suffering many DDoS attacks. (He ran an ama about the attacks !! [Reddit AMA](https://www.reddit.com/r/rutgers/comments/3mnxyp/im_exfocus_ama/?aliasId=ZwkGm0SajIvWVOo8H)  and took credit on twitter [twitter.com/ogexfocus](https://twitter.com/ogexfocus)[Twitter](https://twitter.com/ogexfocus?aliasId=UTsUnr9eO0mHVZ2w1).  AND AN INTERVIEW
        - He tried to extort Frantech and a **previous client of ProTraf! **This previous client assumed it was related as they new secret addresses that should have been hidden by Cloudflare. 
        - Entire conversation between ProxyPipe and Anna-Senpai:
[krebsonsecurity.com/wp content/uploads/2017/01/annasenpaichat.txt](https://krebsonsecurity.com/wp-content/uploads/2017/01/annasenpaichat.txt)
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/n_kXndh-YaMdqxeQnh8rFltDka5Ebr4fWMhGM224_C4sf1fwhIHooreJPOKL_JoTLZe0BxwVVudNleH6MK3YY8brfDYBrmfqo83LpsTEffnwdUOMryUhCqoqNhR7eGMU.png) 
Anna senpai interested in the story behind the ProTraf launch!! 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/xqg7S9Np6fmFG_MfINZItC9t_mGpUjKrHyTwsCYgQH315i6UsP5trjQKPZhZ3PAERgkTqFgmsFJoM45LabLKizqXXUCC4bgZkMOZIBG8zWTWqxPp81Hz34naHlVbNnS7.png) 
        - A "null" route specifies a set of Ips to DROP rather than forward - is done in routing, before the packets reach the internals of the network. Also called a black-hold route. Sustain higher throughput than firewalls - so good for DDoS
        - A black hole is a placae in a network where incoming/outgoing traffic is dropped without informing the source. They are invisible when examining the network.
        - Mirai was also used for **click fraud **- i.e. fake users that "click" the ads and cost internet advertisers more than $16 billion a year. Received around **200 bitcoin! **Valued at over 180,000 then. 
        - A paper on the Mirai botnet: 
            - Page 02
                - The Mirai botnet, composed primarily of embedded and IoT devices, took the Internet by storm in late 2016 when it overwhelmed several high-profile targets with massive distributed denial-of-service (DDoS) attacks. In this paper, we provide a seven-month retrospective analysis of Mirai’s growth to a peak of 600k infections and a history of its DDoS victims
                - Starting in September 2016, a spree of massive distributed denial-of-service (DDoS) attacks temporarily crippled Krebs on Security [46], OVH [43], and Dyn [36]. The ini- tial attack on Krebs exceeded 600 Gbps in volume [46]
                - We track the outbreak of Mirai and find the botnet infected nearly 65,000 IoT devices in its first 20 hours before reaching a steady state population of 200,000– 300,000 infections.
            - Page 03
                - While DDoS was Mirai’s flavor of abuse, future strains of IoT malware could leverage access to compromised routers for ad fraud, cameras for extortion, network attached storage for bitcoin mining,
                - Mirai is a worm-like family of malware that infected IoT devices and corralled them into a DDoS botnet.
                - Mirai spread by first entering a rapid scanning phase ( ̈) where it asynchronously and “statelessly” sent TCP SYN probes to pseudorandom IPv4 addresses, excluding those in a hard-coded IP blacklist, on Telnet TCP ports 23 and 2323 (hereafter denoted TCP/23 and TCP/2323). If Mirai identifies a potential victim, it en- tered into a brute-force login phase in which it attempted to establish a Telnet connection using 10 username and password pairs selected randomly from a pre-configured list of 62 credentials. At the first successful login, Mirai sent the victim IP and associated credentials to a hard- coded report server (≠)
                - A separate loader program (Æ) asynchronously in- fected these vulnerable devices by logging in, determining the underlying system environment, and finally, down- loading and executing architecture-specific malware
                - Mirai attempted to conceal its presence by deleting the downloaded binary and ob- fuscating its process name in a pseudorandom alphanu- meric string.
                - In order to fortify itself, the malware additionally killed other processes bound to TCP/22 or TCP/23, as well as processes associated with competing infections,
            - Page 04
                - To distinguish Mirai traffic from background radiation  and other scanning activity, we uniquely fingerprinted Mirai probes based on an artifact of Mirai’s stateless scanning whereby every probe has a TCP sequence number — normally a random 32-bit integer — equal to the destination IP address. The likelihood of this occurring incidentally is 1/232
                - We would expect to see roughly 86 packets demonstrating this pattern in our entire dataset. In stark contrast, we observed 116.2 billion Mirai probes from 55.4 million IP addresses.
                - A number of challenges make accurate device labeling difficult. First, Mirai immediately disables common out- ward facing services (e.g., HTTP) upon infection, which prevents infected devices from being scanned.
            - Page 05
                - To track the evolution of Mirai’s capabilities, we collected binaries installed on a set of Telnet honeypots that masqueraded as vulnerable IoT devices.
                - We logged 80K connection attempts from 54K IP ad- dresses between November 2, 2016 and February 28 , 2017, [118 days total] collecting a total 151 unique binaries. We filtered out executables unrelated to Mirai based on a YARA sig- nature that matched any of the strings from the original source code release, leaving us with 141 Mirai binaries.
            - Page 06
                - We analyzed the binaries for the three most common ar- chitectures — MIPS 32-bit, ARM 32-bit, and x86 32-bit — which account for 74% of our samples. We extracted the set of logins and passwords, IP blacklists, and C2 do- mains from these binaries, identifying 67 C2 domains and 48 distinct username/password dictionaries (containing a total 371 unique passwords).
            - Page 07
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ef_s_W1z4cOGy0E6a2-UR9Kl1zpF9Z_SnH8OyiaYfdrffYuY8CMy5LL_HIAsXlH2krSfiIHAAzacTmqMq4USloMZ19dT1lk2EoAFwqwFiuFTkDN8OhS9sEYq3PVvt2wX.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qlP_m-ICbjThGaKMeq__K9q44eFeiWdZZm6BMbqoNUT39WD_17tb92nvRHWY3g3eNoIio7Bm-Bz1riu7AOrKRGqdggSI22SaTqnBO56mhvF7_dTISKAamlIP0VwcQI1a.png) 
                - We observed multiple phases in Mirai’s life: an initial steady state of 200,000–300,000 infections in September 2016; a peak of 600,000 infections at the end of Novem- ber 2016; and a collapse to roughly 100,000 infections at the end of our observation window in late February 2017
                - The decay that followed may be explained best by Deutsche Telekom patching routers soon after the attack [21]. The non-immediate decay may have been due to the devices requiring a reboot for the patch to take effect.
            - Page 08
                - Mirai largely infected regions the black market considers to be low-quality hosts used for proxies and DDoS [88] and may have limited potential avenues for monetization
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-1WQcinVLe1hj0fU_Vz7M5K3qHy5QxfoplAEJUTKnOjKxuq68IGxlZAEecJPRXOdZA0CjZ629yzXcFe0AwoSRnAGc3DGeIzworuLh_GqmvcJDOQy6oL-oPAhdkX_Uo9U.png) 
            - Page 09
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Wzy4s_qrRhamwuNlJkc9WIG_5w_0zNPqhcRsqBC3y8QTDRH7AsjP_E6LgXN-9QWkGJMoT0j6h-MYUCny_KUQd1_ezMio_NnLGEWhzK0skOnWyxU7Tr914u7Pa3z5Cczk.png) 
                - Our results across all five protocols indicate that security cameras, DVRs, and consumer routers represent the majority of Mirai infections (
            - Page 10
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/h_weEA9cMlyd735fWbW1eZpQ0GjqBreBHC4ApcuUqfkpdZmSqlnXbpU60qWS_n5ZJuqnJRRbkDh1MY8Pqnw0kJ8xn-U1wGuQN_ARObQncXAypHtetNhuDEKtwBCuFERd.png) 
                - We further note that the majority of bots scanned at an estimated rate below 250 bytes per second. We note however this is a strict underestimate, as Mirai may have interrupted scanning to process C2 commands and to conduct brute force login attempts.
                - e used to cluster C2 IPs and domains based on shared network infrastructure.
            - Page 13
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gT-K1dj36UfLH8GLAWkDc_UhTRSTRDlTSd9A6TiS5pKjbpd0YehyRKgj5eN-4gvmnLZC_pBF5rEvf22N3mzkMcRx5P1-WOJ4p0SBkcSrxayj_2kensqgW1Zfw7fkR0D0.png) 
                - hese victims ranged from game servers, telecoms, and anti-DDoS providers, to political websites and relatively obscure Russian site
                - The Mirai source code supports targeting of IPv4 sub- nets, which spreads the botnet’s DDoS firepower across an entire network range.
                - The three most frequently targeted victims were Liberia’s Lonestar Cell (4.1%), Sky Network (2.1%), and 1.1.1.1 (1.6%). We examine Lonestar Cell in depth in Section 6.3. Sky Network is a Brazilian company that operates servers for Minecraft (a popular game), which is hosted by Psychz Networks.
                - Interestingly, the 7th most common attack target was an IP address hosted by Voxility that was associated with one of the Mirai C2 servers, and we note that 47 of 484 Mirai C2 IPs were themselves the target of a Mirai DDoS attack.
            - Page 14
                - Dyn On October 21, 2016, Dyn, a popular DNS provider suffered a series of DDoS attacks that disrupted name resolution for their clients, including high-traffic sites such as Amazon, Github, Netflix, PayPal, Reddit, and Twitter
            - Page 15
                - We note a 71% intersec- tion between the 107K IPs that attacked Dyn and Mirai scanning in our network telescope.
                - Lonestar Cell Attacks on Lonestar Cell, a large tele- com operator in Liberia and the most targeted victim of Mirai (by attack account), have received significant attention due to speculation that Mirai substantially de- teriorated Liberia’s overall Internet connectivity
                - Fur- thermore, the juxtaposition of attacker geography (largely Southeast Asia and South America) and victim geography (majority in the U.S.) places a spotlight on the importance of global solutions, both technical and non-technical, to prevent the rise of similar botnets. Otherwise, adversaries will continue to abuse the most fragile hosts to disrupt the overall Internet ecosystem
        - A paper on the economics of a botnet: 
            - Page 1
                - Botnets and malware over the last couple of years have proven to be a serious threat to cybersecurity.
                - It comes as no surprise that the primary motive for the use of botnets is for economic gain [1].
                - Tier 1:Practitioners who rely on others to develop malicious code, delivery mechanism and execution strategy. Tier 2:Practitioners who have a great depth of experience, with the ability to develop their own tools. Tier 3:Practitioners who focus on the discovery and use of unknown malicious code. Tier 4:Practitioners who are organised, highly technical, proficient and well funded to discover new vulnerabilities and develop exploits.
            - Page 2
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NjFMQS-G6TExmrZJKfgmYyAGzqwxd577fLA1_NrVzzQdW7k4aA6alVTuKLKRu-NX_vbLi_lHgMeLBoI-rqQC2mIdfdtQgc-kU78TEbqllktNyZbypQeMo2ozTLSw2xe2.png) 
                - On this subject, Rodriguez-Gomez et al. [14] argues that there are five motives for a botmaster to setup a botnet. These are money, entertainment, ego, cause and social status.
                - Bottazzi et al. [1] states that spamming and DDoS-attacks can be considered least profitable among the activities mentioned in Table I, since the operation is too noisy,
            - Page 4
                - U.K. based institutions defines four types of costs associated with cybercrime: costs in anticipation of, costs as a consequence of, costs in response to and indirect costs associated with cybercrime
            - Page 5
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2dPSku7jFO8TxzlmgzREJziaRQUrehMyZpH9xWZNi7MRVk0j5MHfwsQbJ7j614AWfJnq_75w_wwJI2YvEP8r8yz6dVpTK4OYDBrgNF37sqKqrlXhbVeDzDDKE7EtyqHW.png) 
        - A paper on the botnet revenue model: 
        - Paras Jha DDoS Court complaint 
        - Paras Jha DDoS plea, 
        - After the source code was released **many botnets were unleashed.** 
        - All the pleas:
            - [Jha click fraud complaint](Jha1.md) (PDF)
[Jha click fraud plea](jhacf plea.md) (PDF)
[Jha DDoS/Mirai complaint](Jha DDoS.md) (PDF)
[Jha DDoS/Mirai plea](Jha DDoS Plea.md) (PDF)
[White DDoS complaint](JWhite DDoS.md) (PDF)
[White DDoS/Mirai Plea](whiteddosplea.md) (PDF)
[Norman click fraud complaint](Norman Clickfraud.md) (PDF)
[Norman click fraud plea](NormanPlea.md) (PDF)
        - 
        - **Essay 2** 
            - Introduction
                - The Mirai botnet attack caused widespread harm to individuals, businesses and governments alike. 
The direct losses, indirect losses and defence costs alike were all massive.
Continues to harm people today, and the potential for further harm lingers (Medusa virus continues to evolve). Made it easier for hackers to get involved.
            - 
            - Direct Losses
                - **Paragraph 1** 
                    - Direct financial losses **to individuals ** - was widespread.
                    - Mention business that got repeatedly DDoSd - mention the effect of the Mirai on your IoT device - mention the students in Rutgers.
                    - "over one million British households have had a machine in a botnet at least once per year" - cost of cybercrime
                    - 
                - Paragraph 2  
                    - PSYCHOLOGICAL EFFECTS ON INDIVIDUALS
                    - We can get quotes for this.
                    - 
                - Paragraph 3
                    - Not only were individuals harmed, the Mirai virus had huge effects on the infrastructure of whole **regions. **Direct financial losses to countries and people through infrastructure destruction. 
                    - Talk about those two big cases
            - 
            - Indirect Losses
                - Paragraph 4 
                    - Indirect losses  - loss of trust in IoT devices (Cost to businesses), increasing security of IoT (more friction), "**Efforts to clean up machines infected with botnet malware" - **Cost of cybercrime quote. This cost was felt by individuals and businesses alike.
                    - "revealed that in 2010, around 6% of the 19 million UK broadband subscribers had a machine in a botnet at some point during the year." - Cost of cybercrime
                    - "costs of cleanup at $500 per infected household, or $30 for every household with a broadband connection." - cost of cybercrime
            - 
            - Defence costs
                - Paragraph 5 
                    - Whole IoT industry had to change - passwords etc.
Cost of software patching, overall cost $1bn in 2012
                    - As for IoT botnets such as Mirai, the appropriate countermeasure is probably a law on patching, such as the new EU directive on sale of goods
                    - require firms that sell goods with digital elements to maintain those elements during the lifetime that consumers can reasonably expect. This will impose substantial costs on some firms,
                    - Government push
                    - Firms have to get ddos protection services from cloudflare
                - Paragraph 6
                    - Botnets in general cause... 

                    - ISPs have to set up abuse handling department - Cost of cybercrime. Typical European ISP will spend over $3m in 2018
                    - From other firms (banks etc) - "Some reports available in 2012 suggested of the order of $20bn" cost of cybercrime.
                    - **ESTIMATE OF $4bn** 
            - 
            - Future costs?
                - 
        - 
        - 
    - Lecture 1
        - Tools & techniques of cybercrime
            - Cyber **dependent** crimes are crimes who are wholly enabled by the internet and would not occur without it. 
            - Cyber **enabled **crimes are traditional offences that have moved online.
            - Three generations of cybercrime
                - Gen 1 mainframes + OS
                - Gen 2 computer networks such as viruses and worms
                - Gen 3 distributed and automated such as botnets
            - Earliest example of cybercrime - illegal interception of telegram communications for injecting terrible news to change stock prices.
            - CCCD Cambridge computer crime database - only arrested/charged.
            - Worm vs Virus vs trojan vs drive-by-download
                - Worm self replicates and activates on its own
                - Viruses are activated by someone
                - Trojans are disguised
                - Drive by download is unauthorised downloads without you knowing
            - Toolkits lower barrier of entry
        - As-A-Service business model
            - Zeus - injects items into say banking sites. Man in the middle, works on websites.
            - You could **buy **Zeus (banking Trojan) for $2000. 
            - Instead sell it as a service to reduce user financial outlay, reduces risk of failure AND outsources logistical and maintenance requirements to the Zeus team.
            - Booter services - denial of service as a service.
        - Airline ticketing fraud
            - Credit card fraud - loyalty point fraud
            - Obtained via unauthorised access to global distribution systems (phishing)
            - Compromised business accounts
            - Linked to other types of crime
                - Human smuggling & trafficking 
                - Theft
                - Smuggling cash and contraband
                - Facilitating money laundering
                - Credit card fraud
        - Anonymity
            - Anonymity networks ⇒ TOR
            - Proxies/VPNs
            - Currencies
            - Physical security
            - Some sites are intended for a **victim **to visit (account recovery, fake websites for phishing, malware dissemination) and some for the **offender **to visit (child porn, drugs etc.) 
            - Currencies
                - Compromised / mule acocunts
                - Alternative currencies - gift cards, loyalty point accounts
                - eCurrencies - web money, RBK money
                - Crypto
    - Lecture 2
        - Lecture 2 Reading Notes
            - [Virtual Criminality: Old wine in new bottles?](https://journals.sagepub.com/doi/pdf/10.1177/a017405?aliasId=YbsThrujaYZqQuQ6i) 
                - "I suggest that ‘virtual criminality’ is basically the same as the terrestrial crime with which we are familiar."
                    - They say it differs only in terms of the medium.
Then describe it's transnational implications.
                - Motivations
                    - "Computer criminals are driven by time-honoured motivations, the most obvious of which are greed, lust, power, revenge, adventure, and the desire to taste ‘forbidden fruit’. "
                        - Waffle - they say funds transfer fraud = greed. Child porn trafficking = lust (??). Are the ones selling it necessarily paedophiles?
                        - Loss or damage = Revenge (???). This is true in some cases but obviously false in others.
                        - They say adventure/forbidden fruit is the idea of hackers being where they aren't supposed to be. 
                    - "Given the degree of technical competence required to commit many computer related crimes, there is one other motivational dimension worth noting here. This, of course, is the intellectual challenge of mastering complex systems"
                - Interpersonal relations in cyberspace
                    - "The illusion of anonymity seems to have elicited more candour over the internet than one would expect in face-to-face communications." 
                        - In some way true in some way not. Certainly people will more candidly insult you - but I'm far more likely to share my mental state, what I study + where in reality than in CS:GO.
                    - Argument that communication over the internet for crime can be done just the same in a disco (i.e. for a predator to lure a victim). Presumably while staying anonymous..?
                    - "The most adept are never noticed, much less identified. By contrast the inept cybercriminal leaves his footprints all over cyberspace." 
                        - Author makes the argument that this is the same for normal criminals and cyber criminals.
Edge cases include crimes so large that they can not go unnoticed. 
Because he says **never noticed **this implies the most adept wouldn't do such large obvious crimes.
                - New challenges for the state
                    - Discusses challenging of policing bad speech on the internet.
                    - Relates burglary (where the criminal will never be caught) to cybercrime where all the police can do is officiate insurance claims. **This is probably true.** 
                - Paradoxes of the digital age
                    - Cryptography boon to criminals and to legitimate business. Conflict of interest then, as business wants low crime.
                    - "Arguably, the internet constitutes a greater threat to privacy than was ever thought possible. The possibility of remaining anonymous in cyberspace, far from being endless, appears significantly constrained." 
                        - He mentions methods of anonymity, but says not everyone uses them.
                - The private threat to privacy
                    - Describes that before the internet, all the public information about you was spread out - and would be near impossible to collate. Data mining now possible.
                    - Apparently someone googled their wifes name and found loads of chat logs to use in his custody battle...
                - The transnational dimension
                    - Crimes across jurisdictions - different laws and different priorities. If I get scammed by an Albanian, good luck to me.
                - Implicating third parties
                    - "If I were to send a co-worker sexually offensive email messages, my employer could be liable for failing to provide a safe working environment. What degree of preventive or reactive response would be required on my employer’s part in order to avoid liability?"
                    - Companies have websites that can be hacked or mimicked. How often should a company's website be update to ensure information on it is correct?
                - Conclusion
                    - "One of the basic tenets of criminology holds that crime can be explained by three factors: motivation, opportunity, and the absence of a capable guardian. This explanation can apply to an individual incident as well as to long-term trends. Derived initially to explain conventional ‘street’ crime, it is equally applicable to crime in cyberspace. As we have seen, motives for computerrelated crime are nothing new. Technologies may change rapidly, but human nature does not. The Ten Commandments are as relevant today as they were in Biblical times." 
                    - But he says there are more opportunities for cybercrime.
                - Makes the argument that there are more private security guards than police in many places - so too with the internet.
            - [Help, I need somebody: Examining the antecedents of social support
seeking among cybercrime](https://reader.elsevier.com/reader/sd/pii/S0747563220300649?token=4EA32B98CBC8C59C2A3D1B00F4704EAC72D8CC32FFE98B158A9EC4002932E32E9A85A1C66134EB99E58CE5BCB753602E&originRegion=eu-west-1&originCreation=20230125175019?aliasId=LXPLg1kuXRhFBbJ86) 
                - 
                - "Moreover, in 2018, 8.5% of the Dutch citizens claimed they were a cybercrime victim (of crimes such as hacking, online fraud, identity theft, ransomware, and interpersonal incidents)" 
                    - 8.5 fucking percent??? Checked median age for Netherlands and it sits about central for Europe.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/SWB3kgl_Kyb_THKQhcfZ11IrgJhw6VtqqRy8QhlvfpiYPZqG2JShWRiFaSiIU7QO9rIntBkebPEPP9ybWVjNQTXgdiYJ_S40kEIRdL5R_-5nyXZcGNy3pmScjZ7cZu8g.png)
                    - 
                - "What these studies have in common is that they apply a situational preventive perspective and aim to reduce the amount of future cybercrime victims. However, it is likely that progress made in the cybersecurity field will always be paralleled by cybercriminals’ increasing professionalism and sophistication" 
                - A considerable number of victims don't share their victimization experience with friends or family.
                    - Not unusual for the victim to be blamed. Which would effect their willingness to share.
                    - Seeking support is effective for dealing with negative psychological and emotional effects **and **can provide useful info to stop it happening in the future. 
                - Consequences of cyber-crime victimization
                    - "Victimization is a potentially traumatizing experience (Richards & Cross, 2018), which can be linked to a myriad of negative effects."
                        - Cybercrime can result in financial consequences.
                            - Direct losses (scammed out of money)
                            - Indirect losses (opportunity cost + cost to society)
                            - Defense costs (costs of antivirus etc.)
                        - Can result in psychological + emotional effects.
                            - "cybercrime victims have reported reduced subjective well-being, feelings of depression, fear, shock, distress, sadness, anger and embarrassment" 
                            - "some online fraud victims have claimed feeling stupid or cheated afterwards, and have reported decreased levels of trust in themselves and in others, which can further develop into physical effects, such as sleeplessness or insomnia, nausea or weight loss"
                - Social support seeking
                    - "It is assumed that victims complete three steps before they decide whether or not to disclose the incident to a third party (van de Weijer, Leukfeldt, & Bernasco, 2018). First, victims need to identify themselves as victims. Next, they assess the seriousness of the crime. Based on these two steps, they can make a final decision about whether to report the incident or not."
                    - Help, I need somebody: Examining the antecedents of social support seeking among cybercrime victims [Article](Article.md)
                --------------------- Portal ---------------------
                    - Page 02
                        - Moreover, receiving social support can help to maintain or enhance victims’ self-esteem, speed up the processing of stress caused by the incident (Frieze et al., 1987), and stabilize emotional functioning (DeValve, 2005) 
                        --------------------- Portal ---------------------
 -- Avoided infinite recursion --                 --------------------- Portal ---------------------
                    - Page 03
                        - Determine how (1) perception of the cybercrime event, (2) primary responses to the event, and (3) a person’s social capital are related to social support seeking. 
                            - This is what the study seeks to do
                - Perception of the event
                    - They measure **perceived severity** __ __ and **perceived control.** 
                    - Perceived severity is important - the more severre it is perceived to be, the more help/compensation they will receive so the **larger the pro is to reporting.** 
                    - **Hypothesis**: H1. There is a positive relationship between perceived severity of cybercrime and social support seeking. 
                    --------------------- Portal ---------------------
                        --------------------- Portal ---------------------
                            - Page 03
                                - internet users take after cybercrime victimization. For example, a study of online fraud victims found that when these victims felt like they had enough skills to deal with the incident on their own, and thus felt like they had control over the situation, they were less likely to seek formal support 
                    - [H2. There is a negative relationship between perceived control and social support seeking. ](Untitled/Page 03/H2. There is a negative relationship between perceived control and social support seeking.md) **Hypothesis: H2. **There is a negative relationship between perceived control and social support seeking. 
                        - The more control - the less likely they are to seek support.
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/E7-ngP6IlAOvvehoUOIBU7MCoa0CxB4-EHJrDtmdClXMiB-FajnEZTLDKyyKoegbT9FRfso8-scF8JjDpJgVLGEcnhaKbkeWybm1x8brVKqK1tJyIJGwI6sY7zFH_Hxt.png) 
                    --------------------- Portal ---------------------
                        - 
                    - [H4. There is a negative relationship between denial and social support seeking. ](Untitled/Page 04/H4. There is a negative relationship between denial and social support seeking.md)** Hypothesis: H3 - **There is a negative relationship between self-blame and social support seeking. 
                - Social capital
                    --------------------- Portal ---------------------
                        - 
                    - The more people around you - the more likely you are to tell them...
                    --------------------- Portal ---------------------
                        - 
                    --------------------- Portal ---------------------
                    - [H7b. A negative relationship exists between fear of cybercrime and perceived control. ](Untitled/Page 04/H7b. A negative relationship exists between fear of cybercrime and perceived control.md) H7b. A negative relationship exists between fear of cybercrime and perceived control. 
                        - More afraid ⇔ Less control
                    - Fear ⇒ Less rational decisions, fight or flight.
                    - [H7c. A positive relationship exists between fear of cybercrime and self- blame. H7d. A positive relationship exists between fear of cybercrime and denial. ](Untitled/Page 05/H7c. A positive relationship exists between fear of cybercrime and self- blame. H7d. A positive relationship exists between fear of cybercrime and denial.md) [H7c. A positive relationship exists between fear of cybercrime and self- blame. H7d. A positive relationship exists between fear of cybercrime and denial. ](Untitled/Page 05/H7c. A positive relationship exists between fear of cybercrime and self- blame. H7d. A positive relationship exists between fear of cybercrime and denial.md) 
                    - 
                    - Found that perceived control + denial (H2 and H4) were found to negative relationship with social support-seeking. 
                    - Significant relationship between **self-blame **and social support seeking - **but the relationship was positive.** So H3 was the wrong way round. I.e.e Those who blame themselves are more likely to seek help. 
                    - H5 Wrong - no significant association found between social capital and social support seeking..
                    - H1 wrong - no significant link betweewn perceived severity and seeking support.
                    - H6 wrong - no significant link between available **trusted **connections and support. 
                    - More fear ⇒ perceived as more severe
                    - More fear ⇒ More self-blame
                    - More fear ⇒ Less control.
                - 
            - 
        - Lecture 2 Notes
            - The routine activity approach
                - Can use in essay 3.
                - Predatory crime = likely offenders + suitable targets - capable guardians.
                - Suitable targets:
                    - VIVA:
                        - Value: Resale value.
                        - Inertia: Ease with which it can be carried (stealing a washing machine hard)
                        - Visibility: is the target in view?
                        - Accessibility: Where the targets are placed.
                - New attack vectors brought by the internet means new victims
                    - Dating apps ⇒ Romance scams
                    - Online shopping ⇒ fraud
                    - Gaming ⇒ DDOS
                    - Finding a job ⇒ Job scams
                - Crime **appeared to be dropiing** in the statistics, but they weren't measuring fraud + computer misuse in the survey. In fact it had increased when those were included. 
                - Note that in British courts, the victim is always R - e.g. Rex or Regina (king or queen). The actual victim becomes a **witness.** 
            - Victims and liability
                - Lots of small print!
                    - When the cost is incurred by the bank or account holder - the customer has things they are required to do. E.g. Having a pin that is difficult to remember but not writing it down.
                    - This shifts the onus onto the customer - if transaction is challenged but authorised by PIN, the banks argue that the user must have violated T&Cs.
            - Businesses
                - Exposure, risk and impact varies (Richards, 2009).
                    - Business size: Larger businesses are more likely to self report victimization.
                    - Business turnover: Large turnover more likely to self-report victimization.
                    - Small business operating in more resouce-constrained operating + technical environments are **less likely to detect** 
                    - Retail most likely to report victimization.
                - **Reputation** 
                    - Organises compete, thus keeping customer data safe is important.
                    - It can also affect **sale price **- when Yahoo announced data breaches, their sales price dropped $350 Million. 
                    - Share price  __usually __ drops. Results can vary.
            - Governments
                - Individuals have little choice about governments holding data - i.e School, taxation, health, council, police records etc. 
Unlike how I can choose my internet provider or google drive etc.
                - Police intelligence data - can do bulk collections of communications data.
                - Governments control **critical** national infrastructure
                    - E.g. Wannacry, randsomware that affected the health sector very badly. Used EternalBlue which was detected and stockpiled by the NSA before it was stolen and leaked by shadow brokers.
            - Blame
                - If offending occurs because of lack of guardianship, who is to blame? 
                - Wannacry blame put on
                    - NHS for not having up to date systems
                    - UK government for not funding NHS enough
                    - Microsoft, for pushing new OSs which didnt support legacy systems
                    - NSA for stockpiling the eternal blue exploit
            - Airline ticketing fraud victim
                - Is it the cardholder who may be reimbursed
                - Is it the card issuer who will normally refund the cardholder
                - Is it the merchant?
            - 
    - Lecture 3
        - Actual reference notes
            - Cost of cybercrime
                - Page 01
                    - The period has seen major platform evolution, with the mobile phone replacing the PC and laptop as the consumer terminal of choice, with Android replacing Windows, and with many services moving to the cloud.
                    - about half of all property crime, by volume and by value, is now online
                    - The infrastructure supporting cybercrime, such as botnets, continues to evolve
                    - traditional offences that are now technically ‘computer crimes’ such as tax and welfare fraud cost the typical citizen in the low hundreds of Eu- ros/dollars a year;
                    - We are particularly bad at prosecuting criminals who operate infrastructure that other wrongdoers exploit.
                - Page 02
                    - However, many of the existing surveys are carried out by organisations (such as security vendors or police agencies) with a particular view of the world and often a specific agenda.
                    - However, many of these activities rely on criminal infrastructure, based on botnets, which impose costs on the owners of subverted machines and also on society more broadly in the form of indirect and defence costs.
                    - Measurement is not straightforward, as cybercrimes frequently cross jurisdictions, and the avail- able statistics are fragmentary.
                - Page 03
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bc-mpJydoY_PS07V9tvjeTAHkW-yUcWwVwAqWPD7DpGeZY65NIQTmDqXmpwOgKAEeHx1w80jZPuZ0EXrN1m08pUpfJy0OZeQzr2tr5bEwMDmjRMsqzuSIgHS1j4yD_zQ.png) 
                    - We split direct costs from indirect costs, accounting for the costs of security (which often cannot be allocated to specific crime types) and for the social and opportunity costs of reduced trust in online transactions
                    - Direct loss is the value of losses, damage, or other suffering felt by the victims as a consequence of a cybercrime. Examples include money withdrawn from victim accounts; time and effort to reset account credentials after compromise (for both banks and consumers); and lost attention and bandwidth caused by spam messages
                - Page 04
                    - Indirect loss is the value of the losses and opportunity costs imposed on society by the fact that a certain type of cybercrime is carried out. Indirect costs generally cannot be attributed to individual perpetrators or victims. Examples include loss of trust in online banking, lead- ing to reduced revenues from transaction fees and higher costs for maintaining branch staff; sales foregone by online retailers when their fraud engines cause them to decline shopping baskets; reduced uptake by citizens of electronic services whether from companies or governments; cancelled operations due to online medical services being unavailable; and efforts to clean up machines infected with botnet malware.
                    - Defence costs measure prevention efforts. They include security products such as spam filters and antivirus; security services provided to individuals, such as awareness raising; security ser- vices provided to industry, such as website ‘take-down’ services; fraud detection and recovery efforts; law enforcement; and opportunity costs such as the inconvenience of missing messages falsely classified as spam.
                    - For example, a botnet that earned about $3m a year by promoting Viagra was costing about a hundred times that much, as it was responsible for about a third of the world’s spam in 2011 – and spam cost the industry about $1bn a year
                - Page 06
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/K8sbhj-3_aE4duPPhTaHVac1qHGeJA_YyzYALKonwqerTotmE9YDbVLzl5lx78i-ou0ChLoet1vYRBFMqp5FmO76UeFsSX6uDdxsMelgVt-RDN1Axsnn4gWdJTwc0_Uj.png) 
                - Page 07
                    - In an APP scam, a bank account holder is tricked into transferring money to the fraudster, who typically poses as a bank employee and uses some combination of social engineering skills and technical mechanisms.
                    - Many banks use SMS for two-factor authentication, but Android apps can listen to any incoming SMS (assuming the user gives consent, which is usually granted without thought). There has been an uptick in frauds based on SMS stealing, but we do not yet have any dependable numbers.
                - Page 09
                    - Ransomware has been around for over a decade, the rise of cryptocurrencies has enabled this particular type of malware to flourish. I
                    - n the first three quarters of 2012, there was an esti- mated £1.9m–3.8m lost to ransomware
                    - we found: $7.1m lost to Ponzi schemes and similar ‘investments’; $52m lost to mining scams; $36.3m raised by fake ICO scams; $6m raised by fraudulent cryptocoins; and $5m raised by other fake cryptocurrency services.
                    - They found over a million crypto- mining samples had been in use over a 12-year period. They extracted the wallet identifiers and mining pool information and grouped the samples into campaigns. This allowed them to count the number of criminal groups involved and estimate their profits, Their conclusion was that at least 4.32% of the Monero crypto-currency had been mined by criminals
                - Page 10
                    - Billions of dollars annually are spent on online advertising, but there’s little authentication to verify that the users are actually viewing the ads that the advertiser is paying for. B
                    - advertising. This fraud is usually in the form of an automated browser viewing ads, especially expensive video ads, whereupon the publisher pockets the revenue (‘impression fraud’
                    - here was $36m lost from ad fraud during 2014–2018 via just two different campaigns from a single advertiser [91]. The amount lost to the entire industry was much higher, though harder to quantify directly.
                - Page 13
                    - The IC3 has published a detailed account of the scam, along with a number of variations [40], and their 2018 Annual Report [39] shows that they received over 14,000 complaints over the year relating to victim losses of $38m, an increase of 161% year on year. The IC3 notes that most of the victims were over 60 years old.
                    - In 2012 we discussed the ‘stranded traveller’ scam whereby an attacker who had compromised an email account posed as the account owner, explained some predicament in a foreign land and asked to be sent money to get home again. The ubiquity of mobile phones which allow rapid debunking of the story has pretty much put paid to this particular scam, so compromised email accounts are of limited use apart from for sending spam.
                    - However, the case of Yahoo gives some indication. In 2014 around 1 billion accounts were compromised by, the FBI alleges, hackers working for the Russian security services [92] and it was then discovered that in an earlier (so far not understood) attack all of Yahoo’s 3 billion accounts were compromised
                - Page 17
                    - Around the time of our 2012 report, government spokespersons were talking up the risk of espionage and ‘IP theft’, particularly by China.
                - Page 19
                    - Cybercriminals continue to use networks of infected computers – so-called botnets – to support their operations. In recent years, the ‘Internet Of Things’ (IoT) has facilitated the spread of new botnets, an example being the Mirai botnet that infects devices such as CCTV cameras and DVRs that have known default passwords
                    - Lowered the acquisition costs of ‘botnet herders’ who can now build large botnets of IoT devices within days.
                    - oday cybercriminals have managed to monetize botnets in multiple ways: they can distribute a range of scams or even ransomware; perform DDoS attacks; mine cryptocurrencies; or be used to cheat advertising networks or social media.
                    - a DDoS-for-hire botnet only earned its herder some $26,000 per month [15
                - Page 20
                    - The costs of botnets thus falls not only on Internet intermediaries and their customers but also on society as a whole. Previous works [7, 18] have shown that almost 85% of the botnet infrastructure is located in consumer ISP networks
                    - However, not all providers suffer the costs of botnets equally. Mimicking the market structure, the concentration of bots across ISPs follows a power-law distribution [7], i.e., two or three ISPs typically account for over half the total infected machines within a country.
                    - In order to fight botnets, medium-sized and large-sized ISPs have set up abuse handling departments. Their costs of these are mainly driven by the salaries and benefits for abuse desk responders plus their technical support staff and managers. On top of staff costs, these depart- ments must bear technology and telecom expenses (computers, software licensing fees, etc.), facilities costs (office space, utilities, insurance, etc.) and training costs too. A recent survey quantified the average cost of a handling a ticket at $15.56 plus $1.60 per minute of handling time [82]. Thus a typical European ISP with about 5 million subscribers that opened 200,000 abuse-related tickets in 2018 will spend over e3m.
                    - Botnet mitigation by firms other than service providers (and banks, whose anti-fraud measures we account for above) is hard to nail down, as are figures for the total information security industry. Some reports available in 2012 suggested of the order of $20bn
                    - Overall an estimate of $4bn seems reasonab
                    - firms also get DDoS defence services from Cloudflare. There’s also the global cost of software patching, which we estimated at $1bn in 2012.
                - Page 21
                    - As for IoT botnets such as Mirai, the appropriate countermeasure is probably a law on patching, such as the new EU directive on sale of goods
                    - which when it comes into force will require firms that sell goods with digital elements to maintain those elements during the lifetime that consumers can reasonably expect. This will impose substantial costs on some firms, but software patching is good practice and needed for product safety and functionality in any case, and we are reluctant to describe compliance with consumer-protection law as a cost of cybercrime
                    - n 2012, we noted two robust and independent estimates that a little over one million British households have had a machine in a botnet at least once per yea
                    - ne from Microsoft, whose Malicious Software Removal Tool cleaned up around 500,000 bots in the UK in the first half of 2010
                    - revealed that in 2010, around 6% of the 19 million UK broadband subscribers had a machine in a botnet at some point during the year.
                    - costs of cleanup at $500 per infected household, or $30 for every household with a broadband connection.
                - Page 23
                    - t became rapidly clear that more than twice as many households were falling victims to scams (that are mostly online) than suffered traditional property crimes such as burglary or car theft.
                    - A big Belgian study [74, 75] surveyed 1000 people on victimisation in both 2015 and 2017, did two online surveys of Belgian businesses with about 300 responding, and did 160 face-to-face interviews. 16.5% of the population reported reducing or stopping certain activities online as a security measur
                - Page 26
                    - In terms of the amounts stolen by criminals, it is still the case that traditional frauds such as tax and welfare fraud cost each of us as citizens a few hundred pounds/euros/dollars a year, while payment card and online banking fraud cost each of us as citizens a few tens of pounds/euros/dollars a year. It is still the case that cyber-frauds such as fake antivirus net their perpetrators relatively small sums, with common scams pulling in tens of cents/pence per year per head of population, while the indirect and defence costs we pay, in terms of securing our systems, are much larger – in the tens of dollars a year.
                    - he core problem is that many cybercriminals operate with near-complete impunity. We con- cluded in 2012 that while we might perhaps spend less in anticipation of computer crime (on antivirus, firewalls etc.), we should certainly spend an awful lot more on catching and punishing the perpetrators. We see no reason to change this policy advice. We will not get a real handle on cybercrime until we put an end to impunity.
                - Page 28
            - The Dark figure of online cybercrime
                - Page 02
                    - A pronounced drop in crime, since the early 1990s, has encompassed every crime category tracked by the FBI’s Uniform Crime Reports, including prop- erty crime. However, over the same period, the rates of online property crime (OPC) have been on the rise according to available evidence
                - Page 04
                    - When fraudulent transactions are reported, it is often impossi- ble to infer exactly how the information was obtained, or even how it was exploited.
                    - Others may have their details exploited to obtain products or services, but will suffer no direct loss themselves—argu- ably a crime more similar to defamation than “theft”, at least as far as the original owner of the data is concerned.
                - Page 05
                    - expansion of human activities past dusk, facilitated by the introduction of electric lighting into newly settled territories in the west, had an impact on crime. Every time human activity crosses new “frontiers”, crime seems to follow.
                    - Botnet herders would manipulate infected computers to gather keystroke information and to direct these com- puters—unbeknownst to their owners—to execute specific programs, host fake websites and online pharmacies, and send out spam emails
                    - In 2011, Symantec reported the price for 10,000 bots (infected computers acting as “robots” on commands) was around $15 - **Note: This is bollocks, Symantec are a fucking Security company** 
                - Page 06
                    - First, existing research shows consistently that a much smaller proportion of victims of property crime report their victimization compared to victims of violent crime
                - Page 07
                    - According to the NCVS estimates, the number of households affected by identity theft has risen from 3.1% in 2004 to 7% in 2010, while the number of individuals affected rose from 5% of the population in 2008 to 7% in 2012
                - Page 08
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ch4EDdSf229yAIDhoz4VnR52bfesFkW3WslKWLqKLUFqrnRD2YL06ruhORrkEKGTAvUc27wOhS0AEGhmBr5aa9FUaGb_QZ6GSPaOzf-Nf_LVnRB4WMl3Jxri1OLOo4wk.png) 
                - Page 09
                    - Identity theft victimization is reported to police at a significantly lower rate—around 20%—compared to the proportion of people who report their victimizations from traditional property crime to police—about 40%,
                - Page 11
                    - Estimates of financial losses from online theft and fraud are compiled by Javelin Strategy & Research (2011), using a methodology closest to the one employed in calculating losses from traditional crime by the FBI in their annual Crime in the US reports (U.S. Federal Bureau of Investigation, 2013). The results paint a picture that clearly shows losses from online crime far surpass those from traditional crime (see Table 3), and that the proportion of people or households financially affected by OPC is substanti
                - Page 12
                    - ven though only less than half of all property crime is reported to the police (according to NCVS estimates), the figures for financial losses cannot be assumed to be representative of losses for all such crimes because one of the main reasons some property crimes are not reported to law enforcement is the insignificance of losses
                - Page 13
                    - One successful security breach of a network may only be a single offense, but its effects on victims may be widespread if millions of data records con- taining personal information are accessed by the hackers. Such a crime may expose millions of people to becoming potential victims of identity theft or account fraud
                - Page 16
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/m4k677AXySgIbHASa-Q9xRDkJLAWnJZZ_kYZFOUKL0efUqw3Uu4_pJJRLxjGIG9jxBj1rbjBvk_XFvuJzQsZS9aL9Pp3k2cncGIe5Y4mIYtkHedyNf04eWOfujVFx1uF.png) 
                - Page 17
                    - (1) malicious attacks that are most similar to vandalism —computer viruses, denial of service, and other attacks designed to bring damage to the systems without the intent to profit financially from such dam- age, and (2) cybercrime that is perpetrated with the explicit intent to profit (designated as cyber-theft in the BJS report [Rantala, 2008]). These two types of OPC (cyber-vandalism and cyber-theft) may have very different origins and types of perpetrators but both cause substantial financial losses to the organi- zations targeted.
                    - The data presented here suggest that the rate at which US residents are now affected by OPC actually outstrips that of traditional property crime, which continues to fall.
                - Page 18
                    - Moreover, the amount of financial harm they suffer is far greater in dollar amounts than that inflicted by traditional property crime
                    - when it comes to counting crime throughout history, namely: what is the unit to be counted?
                    - riminologists have traditionally counted discrete acts as separate “crimes,” but have consis- tently wrestled with the conundrum of how to count criminality which is, in effect, spread out over several acts such as spree or serial/repeat offenses.
                    - When it comes to counting “the victim” and, relatedly, “the victimization”, the same problem occurs. Clearly, victims are a diverse group and victimiza- tions vary in their financial impact, but for counting purposes the real chal- lenge is saying where one victim, and one victimization, begins and ends. Recall that in the case of arson, the FBI has given up on calculating losses because it seems unreasonable to attribute the losses from a fire that burns out of control to a single offense
        - Reference notes
            - Measuring the changing cost of cybercrime
                - Crimes are global with strong externalities - spend **less **in anticipation and more in response. Paper gives a static view of the economics of cybercrime. 
                - Direct losses much lower than indirect losses (imposed by society, e.g. loss of trust, online services being off or the effort required to clean up).
                - Direct losses lower than prevention efforts. **Can be linked to IOT devices needing to be updated.** 
                - 
                - 
                - 
            - other paper other paper other paper other paper other paper other paper 
                - Traditional crime rate decreasing since 1990s
                - Better economic conditions + higher average ages.
                - Authors argue that online property crime (OPC) is increasing, and that would lead to the downward trends in crime overall.
                - OPC likely increasing, **larger surface area. ** 
                - Large online market for personal data - i.e. targeted marketing like Cambridge Analytica.
                - Hard to track OPC
                    - Difficult to quantify what constitutes OPC
                    - Skewing of data due to incentives
                    - Extremely low reporting rates
                    - Existing data not too helpful
                    - What should even be measured
                - Identity theft rate more than doubled from 2004 to 2010 **but **this didn't distinguish between wallet theft or cybersecurity. 
                    - Most identity theft happens offline. But obviously, if your identity is stolen online you might not know. 
                    - Violent crimes reported far more than 
        - Lecture notes - Costs and harms of Cybercrime
            - Is cyber-crime **over-hyped **or **under-reported.** 
            - Action Fraud
                - Centralised reporting for cybercrime + fraud in the UK.
                - Not much action comes from it - with a **49% call abandonment rate** of calls trying to get through.
                - Top 3 by volume
                    - Hacking socials + email 14k
                    - Viruses 5k
                    - Hacking personal devices 5k
                - Top 3 by financial loss
                    - Hacking - Extortion 4.6 M
                    - Virus 800k
                    - Hacking 500k
                - 9000 reports posed a security risk and were blocked! Reporting issue. 
                - After an undercover operation, Action Fraud was found to be very poor. Poor leadership, poor training and most reports are just stored and never investigated.
Action Fraud is set to be replaced in 2025.
            - Cambridge computer crime database
                - The **costs **columns have the most missing data. Alleged financial gain and alleged other costs are often missing (64% and 80%). Note that this is sometimes only attempted, and is sometimes recovered. Loss claims will be exaggerated for insurance by victims, and downplayed by the attacker.
                - Another cost is the financial loss incurred, estimated lost revenue, expenditure to recover from an offence, fix vulnarabilities.
            - IOTA cryptocurrency
                - Attacker sold 10,000,000 euro in crypto (IOTA). He set up a website which was a random password generator, when people put the passwords in he stole their accounts.
                - Note IOTA dropped 94% from the time the attacker stole it, to the time he was sentenced.
            - Some costs are hard to value.
            - Reporting
                - Online property crimes are less likely to be reported to the police than other property crimes.
                - Police often caught misusing the system, are they more often **misusing computer systems? **Probably not. 
                - If you are a victim of online fraud, you report it to the bank **not **to the police. Similar for social media, email provider etc. 
The police is not being roped in! 
            - Financial harm
                - Detica estimated that cybercrime cost the UK £27 BILLION per year (1.8% of GDP) 
                - Anderson et al work:
                    - Over 100 different sources of data, each which their own biases
                    - Provide estimates for a number of different crime types
                    - Misleading to provide a total, due to limitations in the data
                    - A follow up study to the first 2012 paper found that the landscape was largely the same.
                - **Defence costs **are greater than direct losses! 
                - Survey of Australian businesses (Richards, 2009)

                    - Total estimated loss AUD $484-649 Million
                    - Total estimated **security expenditure **was AUD $1.37-1.95 BILLION. 
            - Social + Psychological harm
                - Cross, Richards and Smith. Interviewed victims of online fraud who had lost AUD $10,000+. Harms included
                    - Shame
                    - Distress
                    - Anger
                    - Long-term depressive episodes
                    - Loss of trust of other people
                    - Considering and attempting suicide
                    - Psychosomatic symptoms
                    - Negative impacts on relationships
            - Airline ticketing fraud costs
                - 2015: Annual loss of 1 Billion euros - backed up **by nothing**.  
                - If a **travel agency** is defrauded, they carry the loss - one compromised account incurred losses of $740,000
                - If an **airline **is defrauded, they carry the opportunity cost and the cost of an extra meal, baggage weight if that's added on. 
                - If **loyalty points **are defrauded, the cost of the points and the value of the products that the points can be redeemed for. 
            - 
            - 
        - Include Actual  _**or**_   __Potential __ harms 
    - 
    - Lecture 4
        - Reference notes
            - **Hack for Hire: Exploring the Emerging Market for Account Hijacking** 
                - [Authors](File/Authors.md)→[Ariana Mirian](Ariana Mirian.md), [Joe DeBlasio](Joe DeBlasio.md), [Stefan Savage](Stefan Savage.md), [Geoffrey M. Voelker,Kurt Thomas](Geoffrey M. Voelker,Kurt Thomas.md) 
                - [Keywords](File/Keywords.md)→[email security; hacking; phishing; account compromise](email security; hacking; phishing; account compromise.md)
                - Page 01
                    - Email accounts represent an enticing target for attackers, both for the information they contain and the root of trust they provide to other connected web services. 
                    - study a segment of targeted attackers known as “hack for hire” services to understand the playbook that attackers use to gain access to victim accounts.
                    - It has long been understood that email accounts are the cornerstone upon which much of online identity is built
                    - Whereas attackers operating at scale expect to extract small amounts of value from each of a large number of accounts, targeted attackers expect to extract large amounts of value from a small number of account
                    - Since targeted attackers focus on specific email accounts, they can curate their attacks accordingly to be uniquely effective against those individ- uals. Moreover, since such attackers are unconcerned with scale, they can afford to be far nimbler in adapting to and evading the defenses used by a particular target. Indeed, targeted email attacks— including via spear-phishing and malware—have been implicated in a wide variety of high-profile data breaches against government, industry, NGOs and universities alike
                - Page 02
                    - These victims in turn were “honey pot” Gmail accounts, operated in coordination with Google, and allowed us to record key inter- actions with the victim as well as with other fabricated aspects of their online persona that we created
                    - We confirm that such hack for hire services predominantly rely on social engineering via targeted phishing email messages, though one service attempted to deploy a remote access trojan
                    - As a whole, however, we find that the commercialized account hijacking ecosystem is far from mature. Just five of the services we contacted delivered on their promise to attack our victim personas. The others declined, saying they could not cover Gmail, or were outright scams.
                    - Victim verisimilitude. We created synthetic victims that appeared sufficiently real that the hacking services we hired would treat them no differently from other accounts that they are typically hired to hack into. • Account non-attributability. We took explicit steps to prevent attackers from learning our identities while we engaged with them as buyers, when they interacted with us as victims, and even if they successfully gained access to a victim email account. • Range of attacker options. We did not know a priori what methods the hacking services would use to gain access to victim email accounts. Since there are many possibilities, including brute-force password attacks, phishing attacks on the victim, and malware- based attacks on the victim’s computers, we created a sufficiently rich online presence to give attackers the opportunity to employ a variety of different approaches.
                    - For each victim, we created a unique web site to enhance the fidelity of their online identity. These sites also provided an opportunity for attackers to attempt to compromise the web server as a component of targeting the associated victim (server attacks did not take place
                - Page 03
                    - Associate Identity. In addition to the victim identity, we also cre- ated a unique identity of an associate to the victim such as a spouse or co-worker. The goal with creating an associate was to determine whether the hacking services would impersonate the associate when attacking the victim (and some did, as detailed in Section 3.2)
                    - his script logged any activity that occurs within the account, such as sending or deleting email messages, changing account settings, and so on
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/a1elf8R-czI3SnmjbgTiGxOrMke6wSwjiQ-BRorjWkyH22V1qYAWkthw2I1UgOEUuLHtVM8xPW53sjaE7-p0XRWp-DB9fEnAc38NbFozyUPjNvDKEAeZmmh-9ILe-sJa.png) 
                - Page 04
                    - Service reliability. Of the twenty-seven services engaged, ten re- fused to respond to our inquiries. Another twelve responded to our initial request, but the interactions did not lead to any attempt on the victim account. Of these twelve, nine refused up front to take the contract for various reasons, such as claiming that they no longer hacked Gmail accounts contrary to their contemporary advertisements. The remaining three appear to be pure scams (i.e., they were happy to take payment, but did not perform any service in return). One service provided a web-based interface for entering the target email address, which triggered an obviously fake progress bar followed by a request for payment
                    - Finally, five of the services made clear attempts (some successful, some unsuccessful) to hack into eleven victim accounts. We focus on these services going forwards.
                - Page 05
                    - As a rule, we always paid the services, even when they requested additional money, and even when we strongly suspected that they might not be able to deliver when they asked for payment up front. Our goal was to ultimately discover what each service would actually do when paid.
                    - There are two legal issues at hand in this study: unauthorized access and the terms of service for account creation and use. Obtain- ing unauthorized access to third-party email accounts is unlawful activity in most countries and in the United States is covered under 18 USC 1030, the Computer Fraud and Abuse Act (CFAA). Contract- ing for such services, as we did in this study, could constitute aiding and abetting or conspiracy if the access was, in fact, unauthorized.
                    - We note that the ultimate “success” of these attacks is partially dependent on our experimental protocol: in some cases, we supplied 2FA SMS codes to phishing attacks or installed a provided executable, while in other cases, we avoided such actions to see if the attackers would adapt.
                    - he associate lures tempted the user to click on an “image” for the victim’s associate (using the personal connec- tion as a sense of safety), while the Google, bank, and government lures conveyed a sense of urgency to induce a user to click on the link.
                - Page 06
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mqw5Op40T76TMeMZKwMjRHbOYp-5T24wqkOAL7wn0yE-HEaHPlpeKkc-UsTY0eWonm7EbCh8lvuS9aDtQQPyJ50yoL_hLREwTnLIVB1jFcJ7D_mVk3dxFMDCO7sp2-og.png) 
                    - Only service A.1 was able to construct personal lures without requesting assistance from the buyer, find- ing the details from the victim persona’s website. The extent of personalization was limited, though, consisting either of mimicking the victim persona’s company or their associate’s personal email address. No additional branding was lifted from our web sites.
                    - . All services but one used “combo” domain name squatting [ 14] with the keyword ’google’ in the URL, presumably to trick the victim into thinking that the URL was a real Google subdomain. Services A.2 and B.2 used the same fully qualified domain name for the phishing landing page, suggesting that they share a business relationship (i.e., they may both be value-added resellers for the same phishing page service). Long-lived, reused domains suggest that they are valuable and perhaps relatively costly to acquire
                    - The redirection URLs seemed to be one-time use URLs, since we were not able to visit them after the attack executed and did not see repeat redirection URLs in any of the attacks.
                - Page 07
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/MjmxIjI0iVxfuaVDVjl_4olRYrX4OWdONIi77peMmdMOUI-nRlV_6pW4KFZo5-hfwjBPHF9BCSuqnOwR26VHryGPv0_CIG2pxbyFYNUFk0lDH7lvcC4mUzSbHOVJXyce.png) 
                    - Figure 4 shows an example page flow used by one hacking service. We always entered the Gmail credentials of the victim to see how the hacking attempt would progress. After collecting the password, all but one of the hacking services would redirect to a new screen which asked for the 2FA code that the victim had just received on their phone from Google. Six of the nine hacking attempts captured the password from the phishing page and then immediately tried to use it to login to the victim’s account (as verified with our Gmail access logging). Due to the similar behavior and speed at which these logins occurred, we believe that most of these services used an automated tool, similar to Evilginx [6], for this step.
                    - Service B.2 was similar to service E.1, but when they were blocked by the 2FA challenge they switched to phishing messages that looked exactly like the messages from service A. Upon col- lecting the password and the 2FA code that was sent to the phone number for the victim, the service was able to login.
                    - ervice D was the only service that attempted to hijack our victim account using malware. The attacker in this case sent just one email message to our victim persona—flagged as spam—that contained a link to a rar archive download (Gmail forbids executable attach- ments). The archive contained a sole executable file. We unpacked and ran the executable in an isolated environment, but to no effect. According to VirusTotal [ 32 ], it is a variant of TeamViewer (a com- mercial tool for remote system access) which would have enabled the attacker to hijack any existing web browsing sessions.
                - Page 08
                    - Once accessed, all but one of the services abused a portability feature in Google services (Takeout) to download our victim ac- count’s email content and then provided this parcel to our buyer persona. One advantage of this approach is that it acquires the contracted deliverable in one step, thus removing risks associated with subsequent credentials changes, improvements in defenses, or buyer repudiation.
                    - While in- tended for users, such capabilities also increase the ease with which a single account hijacking incident can expose all of a user’s data to attackers. Since our study, Google has added additional step-up verification on sensitive account actions
                    - Our findings suggest that the hack for hire market is quite niche, with few merchants providing hijacking capabilities beyond a handful of providers
                    - all such login attempts from the three services in aggregate. Over a seven-month period from March 16 to October 15, 2018, Google identified 372 accounts targeted by services A, B, and E. Figure 5 shows a weekly breakdown of activity. On an average week, these services attacked 13 targets, peaking at 35 distinct accounts per week
                    - Thus, we surmise that the targeted account hacking market is likely small when compared to other hacking markets, e.g., for malware distribution [11 ]. While the damage from these commercialized hacking services may be more potent, they are only attractive to attackers with particular needs.
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zXV0R_6Nitxtfo6O8VkYjpaDme4fljoSN2LMG6fW2B25uvPHJTsBDoVTNSuboz1UAfEYM6S_chHW2xM9FxCjygdaiMIJzEIMQ2qvSPKXSvLjikFTq-mtQUwPz2hU28AX.png) 
                - Page 09
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/n5zlSkYIvDLxM1FkcdqVvo8RPsc05hVkYGYDs8wsiUneUPqt7zf0K5YwKN7If6BjIMOERwKboEQ95PixSQO8FwPWn_enInMFmB9gsMd_gnyqa_RwD8gD_ySa9lzgiM5j.png) 
                    - n, all had pinned posts on forums where this option was available. Only service A paid for banner advertisements on all of these forums. Together, this suggests that the services are profitable enough to continue advertising via multiple outlets.
                    - In addition to this qualitative search, we received an email ad- vertisement from one of the services for upcoming changes to the service, which was sent to 44 other buyers as well (exposing their clientele’s email addresses).
                - Page 10
                    - At a high level, we find that the commercial account hijacking ecosystem is far from mature. When such attackers are successful, they can be potentially devastating to individuals. Yet, as an overall market it is not poised to cause widespread harm.
                    - Services have inconsistent and poor customer service. For ex- ample, three of the services charged significantly higher prices than their advertised price, and two services changed their initial prices while they were executing the hack. Moreover, customer service is slow and inconsistent in their communication with the buyer, sometimes taking more than a day to respond.
                    - Attackers showed little initiative. Most attacks made no effort to gather information independently about their victims. Of the nine attempts, only services A.1 and A.2 discovered additional information about the victim on their web sites, such as the name of their associate. The others, including different contracts within service A, would not attempt hacking the account without explicitly requesting additional information from the buyer.
                    - n contrast, studies on markets for CAPTCHA solving [21 ], Twit- ter spam [30 ], and Google phone verified accounts [28 ] show that those services are quick to respond, and stable in their services and pricing.
                    - Two-factor authentication creates friction. Even though phishing can still be successful with 2FA enabled, our results demonstrate that 2FA adds friction to attacks. Various services said that they could not hack into the account without the victim’s phone number, had to adapt to 2FA challenges by sending new phishing messages to bypass them, and one renegotiated their price (from $307 to $690) when they discovered that the account had 2FA protection. Based on these results, we recommend major providers encourage or require their user base to use a 2FA physical token
            - **Plug and Prey? Measuring the Commoditization of Cybercrime  isvia Online Anonymous Markets ** 
                - Page 02
                    - Researchers have observed the increasing commoditiza- tion of cybercrime, that is, the offering of capabilities, services, and resources as commodities by specialized suppliers in the underground economy.
                    - Commoditiza- tion enables outsourcing, thus lowering entry barriers for aspiring criminals, and potentially driving further growth in cybercrime.
                    - We use longitudinal data from eight online anonymous marketplaces over six years, from the original Silk Road to AlphaBay, and track the evolution of commoditiza- tion on these markets.
                    - We conservatively estimate the overall rev- enue for cybercrime commodities on online anonymous markets to be at least US $15M between 2011-2017. While there is growth, commoditization is a spottier phe- nomenon than previously assumed.
                    - The idea is that specialized suppliers in the underground economy cater to criminal entrepreneurs in need of certain capabilities, services, and resources
                    - Commoditization substantially low- ers entry barriers for criminals, which is hypothesized to accelerate the growth of cybercrime
                    - do so, we turn to transaction cost economics (TCE). We argue that the characteristics of commodities are highly congruent with the characteris- tics of online anonymous marketplaces. More precisely, the one-shot, anonymous purchases these markets sup- port require suppliers to offer highly commoditized of- ferings.
                    - While data from online anonymous marketplaces pro-vides a unique opportunity to track the evolution ofUSENIX Association 27th USENIX Security Symposium 1009commoditization, we are not arguing that these market-places provide a complete picture. They do not have amonopoly, of course.
                - Page 03
                    - e analyze longitudinal data on the offerings and transactions from eight online anonymous marketplaces, collected between 2011 and 2017.
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3ykPx24BPivIKJjeuyOsZlUBObZh1ryP44DpD8ONXA6zLu8_3ggirE7D4fjdz3mxpahKB566FktbBMH_LaijIHVk7WpeHj37I1iSOVQq5Cc-GU92LFDXxYNq-Tg3lSjp.png) 
                    - Williamson [47] distinguishes several asset character- istics that determine if and how outsourcing will occur, as shown in Figure 1. A, B, and C are various forms of outsourcing and D is vertical integration
                    - k is a measure of as- set specificity, referring to the degree to which a product or service is specific to e.g., a vendor, location, control over resources, et
                    - “fungible”, meaning that different offer- ings of it are mutually interchangeable (k = 0
                    - The more specific an asset is (k > 0), the more investments are specialized to a particular transaction.
                    - The second factor, s, refers to contractual safeguards.Transactions where investments are exposed to unre-lieved contractual hazards (s = 0) will not be traded pub-1010 27th USENIX Security Symposium USENIX Associationlicly (i.e., anonymous online marketplaces such as SilkRoad or AlphaBay are a poor fit), but on smaller, “invite-only” markets
                - Page 04
                    - When s > 0, con- tracts with transaction-specific safeguards are in place.
                    - The efficiency gains also work in the other di- rection: those who offer goods or services that can be commoditized would use these markets to sell them and benefit from the wide reach and high frequency of trans- actions, without being exposed to risky direct interaction and coordination with buyers.
                    - Similar to the prominent drugs-trade on anonymous online markets, we expect two type of commodities on these markets: business-to-business (B2B), e.g., whole- sale quantities of credit card details, and business-to- consumer (B2C), e.g., a handful of Netflix accounts. We are primarily interested in B2B, as that is the form of commoditization that is the most worrying and specu- lated to cause a massive growth in cybercrime, though we will also report the main findings for B2C. To assess the degree to which B2B services are commoditized, the next section develops a framework to identify the differ- ent value chains where there is demand for commodi- tized cybercrime.
                    - First, we look into the value chain behind spamvertis- ing, which is driven by three resources: a) advertisement distribution b) hosting and click support and c) realiza- tion and cash-ou
                    - Second, extortion schemes, for instance ransomware or fake anti-virus [17] have a value chain that consists of four distinctive resources: a) development of malware b) distribution, by either exploits or (spear)phishing e- mails, c) take-over and “customer service” and d) cash- out [30, 42].
                    - hird, click fraud is supported by four similar, gen- eral resources: a) development of a website, malware or a JavaScript, b) distribution through botnets, c) take- over by either malware or JavaScript and d) cash-out [32, 42].
                    - Fourth, the criminal business model in social engi- neering scams, such as tech support scams [35], or one- click fraud [16] leans on: a) (optional) development of malware or a malicious app, b) distribution by phish- ing e-mail or website, or through social engineering, c) take-over and setting-up “customer service,” and d) cash- out [35, 42].
                    - Fifth, cybercriminal fraud schemes, e.g. those enabled by financial malware, build on four general, main re- sources: a) development and b) distribution of malware or a malicious app, c) take-over, for instance by using web-injects or a RAT,1 and d) cash-out
                    - Sixth, cryptocurrency mining relies on near-similar re- sources as click fraud: a) the development of malware or JavaScript, b) distribution of malware by botnets or the injection of a JavaScript in a compromised websites, c) the take-over, i.e. mining, and d) cash-out
                - Page 05
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/a2aJFbUsR8pFYRQFhQXtZ5QHJZ8gj1f6w7X7cr7SohgvDcYjcZ2MktGvwjk_Yx8S1l_5_VaV55BHVlyIopJ7QTAsItY9RD1aHO5h_38DqVI3qBR3GqiCaufiRfHma1fF.png) 
                    - 1) collecting and parsing data on listings, prices and buyer feed- back from eight prominent online anonymous markets, 2) implementing and applying a classifier to the listings to map them to cybercrime components from our con- ceptual model of value chains (Figure 2) as well as to additional categories of B2C cybercrime, and 3) using Latent Dirichlet Allocation (LDA, [10]) to identify the best-selling clusters of listings
                    - We first leveraged the parsed and analyzed dataset of Soska and Christin [40] to obtain information about item listings and reviews on several prominent online anony- mous marketplaces. For each of the over 230,000 item listings, the data include (but are not limited to) ti- tles, descriptions, advertised prices, item-vendor map- ping, category classification, shipping restrictions and various timestamps. Additionally, each item listing con- tains feedback that has been proven to be a reasonable proxy for sales [15, 40]. Each piece of feedback contains a message, a numerical score, and a timestamp.
                    - AlphaBay is important since, according to the FBI [4], by the time of its closure, it had featured over 100,000 listings for stolen and fraudulent documents, counterfeits, and mal- ware in particular. The US Department of Justice (DoJ) also claims that AlphaBay was the largest single online anonymous marketplace ever taken dow
                - Page 06
                    - Next, we implemented a Linear Support Vector Ma- chine (SVM) classifier. Manual inspection confirmed our suspicion that the markets also contain retail (B2C) cy- bercrime offerings, next to wholesale cybercrime offer- ings. For this reason, we added six product categories to distinguish supply in that part of the market: accounts, custom requests, fake documents, guides and tutorials, pirated goods, and vouchers. A final category, namely, “other”, captures the listings that did not fit anywhere else (e.g., scanned legal documents). The classifier is initially trained and evaluated on a sample of listings (n = 1, 500) from all the markets, where ground truth is created via manual labeling.
                    - First, we identified listings that contain more than one cybercrime component, e.g., offering both a piece of malware and (access to) a botnet. Second, we identified package listings, such as complete cryptocur- rency mining schemes. Third, we observed that some vendors add unrelated keywords to their listings, pre- sumably in a marketing effort similar to search engine optimization. Fourth and last, we observed custom list- ings, i.e., listings that are specifically created to be sold only once to one specific buyer. Custom listings con- tain bespoke products or services ranging from custom quantities to a completely custom-made product such as pre-booked plane tickets.
                    - we excluded three cate- gories of cybercrime components from the classification: JavaScript malware, webinjects, and customer support. For these, we found no listings in our random sample
                    - (i) data cleaning, (ii) tokenizing, (iii) training and evalu- ation of the ground-truth samples which are the concate- nation of the title and description of the item listings
                - Page 07
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Q9_vkgaR_4qpaEIB6cxux_KATsM6cbB8KgqQ0i5ojYljxVU0rWLewxvgOZvBlkydUFzZvZ2EAfeBsKaP9bGmMmY7x4FlPcqoee-cNe8ZI5wMud6st8DPOWJeWrMp4BGU.png) 
                    - o calculate the tf-idf, we used a max-df (maximum document frequency) equal to 0.7 – this dis- cards words appearing in more than 70% of the listings. In the classification phase we then used these values as an input for an L2-Penalized SVM under L2-Loss. We im- plemented this classifier using Python and scikit-learn.
                    - Because of the nature of listings that cover multiple categories, e.g. bundled goods, we anticipate some clas- sification errors. It is however important to distinguish between errors where the item listing is classified as “other” (false negative) from acceptable approximations
                    - Our main goal is therefore to prevent cy- bercrime component listings, like malware, from ending up in “other” and vice versa.
                    - he average precision is 0.78 and the average recall is 0.76, denoting some confusion be- tween cybercrime components categories
                - Page 08
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/v7vy23r0fUCTEiWI1fibs4bgTw86S83gN3vyFrgx2PNIZ-Scd7vG1OxGelEAwNK55iEzMuUWSSSasLFXFpa3EsYymsFUNWR0fwt-O_6_MFMCijG4HBfq2O96bSEQQ9-h.png) 
                    - Cash-out stands out: In terms of the num- ber of listings, active vendors, and in total revenue, this category is by far the larges
                    - We see, again, that the cash-out category contains the most expensive set of offerings with very diverse pricing.
                    - Like an ecstasy tablet, a RAT will hold its value over time in terms of being a functional solution. In contrast, stolen credentials “go bad” after some time. The first buyer who uses these cre- dentials will in all likelihood set off red flags at the credit card company for irregular spending,
                    - Cu- riously, the median lifespan of cash-out listings is above average, which could be due to vendors updating the spe- cific product listed, or persistently selling unusable credit card details, or to a slower-than-expected detection of suspicious transactions by credit card companies.
                - Page 09
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/MeBo-6Z5QFmlPY4fkX0DSjAHGFzLBlbCMD176J56NczV49ojCdttbSL6ZOFbNWAB-7Zp_d2TbukyGuwFb-OHNd2-eK50V5rf_s672TW8FXzgbssVuBtEx-leerDDbKrj.png) 
                    - Figure 4 shows a growth in listings, amount of feed- back and revenue for cybercrime components between 2012 and 2017. The drop at the end of 2013 and the be- ginning of 2014 is partly due to the take-down of Silk Road 1 and Black Market Reloaded
                    - Right after this volatility, the AlphaBay market emerged, and subsequently became the largest
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_FmzP9XbAwG923XXhHVGSyEniickpc1QSTWJ6agTriWwueNdtXv35V7TplowrWLMuNWB21cN1QVD6d746s9lmvzvQZXCzb6TP_qE_SsOk0XudbXx_kjdwOuWfk0KthAZ.png) 
                    - Figure 5 shows that the upward trend in feedback in- stances is not only caused by an increase in listings, but also to the increase of amount of feedback per listing. In 2011, a listing on average received around five pieces of feedback per month. Over time, this ascended to around eight pieces of feedback per listing in 2017
                - Page 10
                    - More specif- ically, one listing offering “US CVVs” received nearly 700 feedbacks in the first quarter of 2014. From the beginning of 2015 onwards we see a steady growth in revenue alongside the growth of AlphaBay market as a whole. In the early days of the ecosystem we see an in- crease in cash-out revenue which was primarily driven by a listing offering “10,000 USD CASH,” which can be seen as typical money laundering – the customer pays in bitcoin and receives cash.
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5ZP3iPNqcDAdR65si_34Yc4Xx8-I3kd_balcZzNL67BKXzFZioGBCfasnvVeg-Ws5I7sDqstdzoCLBzyGFhblODrIPOymyNIRQ59ifMbmzOgnjAvkdep9EkhyOq7RRI_.png) 
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KUvjauDgoilMcsaVeehJLVUwsFxm2lovKNN5N_jzUnw_TGxCBcGILR0RBRIvoZSh3G4RRXfaQHaXwTkkVIrch-sOvu4hCCuWKjx3cyZl1hewaBtT1JI0HhFeYyoNoKjD.png) 
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/iSakBy8wyKMTbKjv9w-TpNxdVXZcNdopNmnxEsQw1wusxtPPk4xq1e_2iqy2-M1JvSZY4pebQn20WX_BZckJ4o4UJmkAdku3l9r19EEtp5W3gE7mEpiYh3uMNATGcfaT.png) 
                    - Similarly, we see a spike in botnet-related sales driven by a mysterious listing ti- tled “source,” receiving 10 – rather negative – feedbacks in the summer of 2014.
                - Page 11
                    - Listings and revenue are not distributed normally across vendors. As in many markets, there are big play- ers and small players. Figure 10 plots the cumulative percentage of listings and revenue of cybercrime compo- nents over vendors. A small portion of vendors are re- sponsible for a large fraction of the listings. To be more precise, around 30% of vendors are responsible for 80% of all listings. More interestingly, just under 10% of ven- dors are responsible for generating 80% of the total rev- enue. That means that around 174 vendors have sold for nearly $7 million worth of cybercrime components. This translates into an average revenue per vendor of around $40,000, but the distribution is wide and skewed. The 174 vendors range from a minimum revenue of $7,355 to a maximum of $1,148,403.
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vLGiugxhZInAn8eHpxmP8pnB7Q6bucUq5IJGxkpk1WcdOqsA-Ol3VGQDBEXmaogmofJ_7XcsBwdOqDEchN4Bj28hVir2J7mBcErm-1UgzFw2qFoAWG6yhjZmE2pVaYW4.png) 
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/87QUb337kWZvdCcABtwKMhkKzAzV43RJflxmAzo9Iq-H_5eJyiJM1AN3KBEz4pjpSZNRNwnKo9dJ8mMw0OY5egn4aE5xMA_oTNce6eFEu9oXjfKgkBTompeNS7gqPgcO.png) 
                - Page 12
                    - The large portion of retail cybercrime is in line with what has been observed on the drugs side of these mar- kets; B2C transactions for consumers of drugs, along with more modest amounts of B2B transactions with larger quantities for lower-level dealers
                    - We identified the three best-selling clusters per category by summing the number of feedbacks of all listings in a specific cluster. We then compute the total revenue gen- erated by the item listings in each cluster
                    - For all cate- gories, the three best-selling clusters contain more than 46% of all feedbacks, and in many cases more than 60% of all feedbacks.
                    - The categories “botnet,” “website,” and “RAT” show lower revenue numbers. Upon manual in- spection, we could identify a very small cluster with only a few feedback that was dominated by a few very expen- sive items.
                - Page 13
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/dXDQrHFsLp-fq4Eq-r10ZGS6-m9WSnETjvtSYuIj0I4EgYJnqkAY3P82osQ7zAnlfoWNFV2bswFxnT0nOwRSQ5DE-ZmjOP50tqfOjFErh5DtcrxKfb7IYv6oTT3CU5uz.png) 
                    - e observe clusters with distinct offer- ings in 4) carding tutorials, 5) PayPal accounts, 6) Visa and Mastercard card details4 , 7) “bitcoin deals,” 8) bank account credentials, 9) Amazon refund guides and 10) Bitcoin exchange
                    - App. Prominent clusters of the App category include of- fers for Android loggers, i.e., malicious keylogger apps, Android bank apps, i.e., malicious banking apps, and Dendroid, a RAT for Android.
                    - Botnet. Prominent clusters of botnet listings feature products and services revolving around Zeus botnets, varying from tutorials, to source-code, to “turn key” setups. We also identified offers on C&C servers and This cluster ressembles 1) and 2) but with a focus on Visa and Mastercard brands. It could a priori also include gift cards. DDoS services
                    - E-mail. The prominent clusters in the e-mail category contain two types of spam lists, namely basic lists of e- mail addresses, as well as complete databases, including personal details to create personalized (spear) phishing mails. In addition we find a cluster of offerings on spam- related services. Exploit. Within the exploit category, the two main themes are 1) Microsoft Office exploits, e.g., malicious macros, and 2) browser exploits. We also recorded a non- trivial set of sales for Mac exploits. Hosting. The prominent “hosting” clusters include host- ing through VPS or CPanel-listings. We also find a prominent cluster on hosting of Tor-based websites. Malware. Within the malware category, ransomware stands out by featuring two prominent clusters. One clus- ter revolves around the Stampado ransomware, the other on Philadelphia ransomware. We also observed a promi- nent cluster on miscellaneous (assistive) software tools such as keyloggers or portscanners. Phone. In the category of phone listings, one prominent cluster comprises listings on bypassing security features on phones. The other two prominent clusters offer re- spectively hacked Vodafone accounts and lists of usable phone numbers. RAT. Two out of three prominent clusters in RAT list- ings contain generic RATs. The third cluster specifically deals with Mac OS RATs. Website. The website category is composed of three distinct, prominent clusters. One cluster contains web- site development listings. The second is predominantly VPN-connections and/or SOCKS proxies. The third cluster consists of compromised RDP-servers/hosts list- ings.
                    - Our analysis suggests that nearly all prolific clusters supply a component that matches B2B demand, but that this supply is incomplete, in that the observed supply ful- fills only a niche demand in each category
                    - For instance, we see ransomware dominating the malware category, whereas domain expertise suggests there are, in general, other types of malware in demand. This demand remains mostly unfulfilled in online anonymous marketplaces.
                    - Yet, the supply is only ori- ented towards setting-up the necessary phone lines. We observed that guides and tutorials are among the promi- nent clusters in the botnet and cash-out categories. We however note that selling a guide is not the same as out- sourcing a cybercrime component.
                - Page 14
                    - In this section we briefly present the prominent clusters in the B2C categories – i.e., retail cybercrime. Account. In listings that sell accounts, we observed two main clusters that revolve around offerings for single ac- counts to pornography websites. Next, we see a cluster of listings selling Netflix and Spotify accounts, in quan- tities between two and ten per listing. Fake. The three prominent clusters are respectively of- fering fake passports, fake IDs and counterfeit money. Guide. The clustering process revealed guides in a) bit- coin (“deals”), b) “making money” or starting a business, and c) “scamming.” Pirated. Miscellaneous pirated software, like the entire Adobe software suite or pirated adult videos, and pirated Microsoft software, e.g. Windows 7, are the prominent clusters in pirated products. Voucher. In the category of voucher-related listings, we see offers for: a) Tesco vouchers, b) lottery tickets and c) “free” pizzas, of which most are indeed discount vouch- ers or gift cards for various pizza chains, but a few are in fact credit card offerings, where “slices” refer to groups of accounts.
                - Page 15
                    - hey investigated the market for exploits - which turned out to be moderate in size - and the cybercrime-as-a-service market, where growing numbers of new services types were discovered.
                - Page 16
                    - In three of them (“javascript,” “customer service,” and “web in- ject”), we found no offerings in the large random sam- ple for the ground truth, not even when we searched the whole data with specific keywords. We assume this means there is very little, if any, commoditization of these value-chain components
                    - n line with what other researchers have observed for the drugs trade on these markets, we see both B2B and B2C transactions in the cybercrime categories. B2B and B2C, a.k.a. retail cybercrime, turns out to be compara- ble in revenue. Between 2011 and 2017 the revenue of B2C cybercrime was around US $7 million, where B2B cybercrime generated US $8 million in revenue.
                    - In terms of generalizability of our findings, we have measured and explained the trends in commoditization of cybercrime on online anonymous markets. Beyond this, our findings only speculatively suggest that the trend to- ward commoditization might not be as comprehensive as has been claimed elsewher
                    - Still, this casts an interesting perspective on the “theory of the commoditization of cybercrime.” There is a huge discrepancy between the reported profitabil- ity of criminal business models like ransomware (over $1 billion in 2016, according to the FBI [20]) or DDoS-services (one youngster making $385,000 with his booter-service according to local British police)
                    - The lack of strong growth suggests that there are still bottlenecks in outsourcing critical parts of criminal value chains. Entry barriers for would-be criminal entrepreneurs remain. The services that are highly commoditized, like booters, seem to draw in mostly B2C activities – i.e., consumers going after other consumers, as was the dominant finding in a victimization study of commoditized DDoS [37]. A recent takedown of a RAT operation also suggested con- sumer consumption, rather than B2B transactions [6].
                    - B2B services that require ongoing coordination among the criminals fall short of full-fledged commodi- tization. In other words, the scarcity of supply suggests less-scalable and potentially vulnerable components in criminal value chains. These might be targeted by inter- ventions
                    - Contrast this approach to the series of police actions aimed at the shutdown of whole markets: from our data, these operations seemed to have had only relatively modest effects on the overall trading of com- moditized cybercrime.
- 
