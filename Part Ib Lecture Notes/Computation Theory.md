-  _**Lecture 1**_   Intro
    - **Hilbert's Entscheidungsproblem**
        - Is there an **algorithm** which when fed **any statement** in the formal language of first-order arithmetic, determines **in a finite number of steps**  _**whether the statement is provable**_  from Peano’s axioms for arithmetic, using the usual rules of first-order logic?  
        - Describe the problem, and is it provable?―can we use an algorithm to **decide whether a statement** (written in formal language) is **provable ** _**in a finite number of steps**_ . It is **not **solvable. 
        - A **decision problem** is―Given a **set S **whose **elements are finite data structures **(simply means some data to read, could be formulas of 1st order arithmetic), and **a property P of S**. The decision problem is **find an algorithm that terminates with 0 or 1 **-  _**only yields 1 when fed s with property p**_ **.** 
    - **What is an algorithm**
        - Common features  ↓ 
            - **Finite **description of the procedure, in terms of elementary operations
            - **Deterministic** 
            - We can recognize when it **does terminate** 
        - Turing ⇒ Turing Machines. Church ⇒ Lambda calc. Allows for regarding algorithms as data, on which algos can act
    - **The Halting Problem**
        - Is the **decision problem **with―Set S of **all pairs (A,D) **- **A **is an **algorithm **and** D **is a **datapoint **that A works on. **Property P holds if A eventually halts**. $A(D)\downarrow$  - means A halts on D.
        - Church and Turing found, no algorithm H such that H(A,D) solves the problem. 
        - Describe the **Informal proof, **by contra ↓ 
            - If there were an algorithm H(A,D) that solved the halting problem.
            - let C be: "input A; compute H(A,A); if H(A,A)=0 then return 1, else loop forever."
            - So we know **within C **- if A(A) runs forever C halts, and A(A) halts C runs forever. But what if we apply C to itself? ⇒ If C(C) runs forever C(C) halts, and C(C) halts C(C) run forever
            - This is a contradiction.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/siFmc-hoYXZI03PTHj1UFNUEdQ78lNvCIy_Lq-2rLG89Dm5egQBa19h0-bBEX6537hlsOchorTSYTvpREK_mMfO9G7wYXdk5et3HPJbSB58zkSZEIXsHM7pK8GpCq6ns.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/run013sEKw6k5TVw9nteiquELNVaqM5bDeYaVbYE1_S7taZeJaLzd4NxVPaGJmBn_fjjJdso-ORkObK8Pm4ChpUFNbzwwjGY0_OkTQhLmcSlTCcc0QHNJd-u2vnMZzDE.png) 
        - The dubious sections of this argument are ↓ 
            - Can we make C out of H?  
            - Is H(A,A) allowed? 
    - **From HP to that German one**
        - Rephrased the question to - If a statement in arithmetic is **provable **then A(D) halts. 
        - They encoded an instance of the halting problem as arithmetic statements $\Phi$, such that if you could decide if $\Phi$ was provable, it decides if the program halts. But as solving the halting problem is impossible, so too is the **Entscheidungsproblem.** 
    - **Hilbert's 10th Problem**
        - A **Diophantine equation** is―an **equation with polynomials** with a **fixed number of unknowns**, with a fixed number of **natural number** coefficients ( __implies whole number coefficients)__ . Where the **only solutions of interest are the integer values**. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qxLC7QDSPKmIEmN0o7zNfIiL7OfeoGT_jHowoaRR1nzL5UOXpWThiBK9ZPofEn-nENcVeaaDMfGMlnCnn1DtFl2nkWVM1rw24jTsI5tOrgNSIiPKJfia7ZfO9s2IojQy.png) 
        - Give an algorithm which, when started with any **Diophantine** equation, determines in a finite number of operations **whether or not there are natural numbers satisfying the equation**.   
        - It is **undecidable - **found by **reduction from the halting problem.** 
        - 
    - 
-  _**Lecture 2**_   Register Machines
    - **Register Machines, informally** 
        - Operate on natural numbers (can be any size), stored in idealized registers using the following elementary Operations: 
            - Add 1 to a register
            - Test if a register holds 0
            - Subtract 1 from a register if non-zero
            - Jumps
            - Conditionals
    - **Register Machines more formally**
        - **Register machines consist of** ↓ 
            - Finitely many registers, R_0, ..., R_n.
            - A program consisting of a finite list of instructions of the form label : body, where labels go from 0 to k.
        - **What are the three types of instructions ** ↓ 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/fxk8AwYFUA0rhP95tR13a2my0eD4RWCqi73G-xqu4UtDOyEnUYxFkwFhhbalvTu7S1d3qCjpXfFHPjnlR-CdYU_KVQPP3Vn94S9Cr7Iol-yycHl4N52bfTzLVZAdXnz1.png) 
    - **Register machine computation**
        - At any time we can store all the data about the register machine by taking: $$c = (l, r_0, ..., r_n)$$
Where c stands for configuration 
        - A computation of a RM is a sequence of configurations. $c_0, c_1, c_2,...$ each configuration can be computed from it's previous configuration (other than  c_0).
    - **Halting**
        - What are the **two **ways of halting a register machine?―HALT command, or jump to a non-existent label. Called an erroneous halt. Can consider infinite HALT commands after finite number of non-HALT commands.
        - The last configuration must be a HALT configuration for a finite computation
    - **Graphical Representation**
        - Easier for representing control flow
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ATSzCaqRa1E99W-Awl8pdLZtB4qVrZ3YH7iQ6nD_aOmS1E2zknssVF09D8hsasqG4E46OpzUL_-VvJB9amrXfRLCPPxPI5q0UQAu9MRZnq5LmzCF63A2kMNBBg71oBSp.png) 
        - Program for summing two numbers:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/p2AtCKLNZDVUBQtBVCl1dzFcagI6NjN8WxjAsbae6T8Lflgad-ue_oyEG8wOahd3qqN8YiBalu9xXhPZ37FBf5LNSOnEWu76bTHX7hbs-unLcZ-0mwrQPieOLeg_Di2B.png) 
    - **Partial functions**
        - Register machine computation is deterministic, relation between initial and final register contents defined by a register machine program is a **partial function:** 
$$( (x,y) \in f) \ \land \ ((x,y') \in f) \implies (y=y')$$ 
    - **Notation**
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/1zv_EQfE_VTdHhjE0s1Tx3oMCaCbfXD4eE185wSJMdwyf19HQQbKmf-kPeIGk5SjWzUr92BYNkv-zD_zApMHrHu1ik_hVUgWlefjYjr53Ghf7xZmkS4I6U2hvg-vE5hv.png) 
        - So the up/down arrows say f(x) is defined.
        - A **total function **from set X to set Y satisfies―$f(x)\downarrow$ for all $x \in X$.
    - **Computable Functions**
        - A function with n arguments is computable by a register machines (with at least n+1 registers, n_1-n_n holds arguments), such that for all argument and output pairs of the function - the machine halts with R_0 = y with the arguments set in R_1 - R_n 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/cuvOKu96585HgTMZDaKltXxfp_Re5kTBmR3Cbne1PxTMhRLYpbzDFMNFO0-lk2qf_afGnYCeum7diREAPOZBA3_bZmSTVgdqOYQglJpMaYHmI9Sl2y267g44sDXwhNeQ.png) 
        - Note, there can be many different M that compute the same partial function f.
        - Note our previous register machine witnesses that, ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/OUusJqbA04doG099vl9ymQrnDKks4l3kpaJ5aNRkwLxg6ZJFjEi19EVi321d5xDAX-eZZ4AE8Z82l-fsgCnMPKA7R_b0SOGrgy86WnzEaWtDmbFKyfCPz7fDLLfXOSX5.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CG-JvWoVYIBLtGajm2nPwpKxErPdhCb3Hg7l3XE3DW0oriC_taKwgAksEkO-hIxXbJ83Gyg2zoGV7Ihg9Osf7pFuqwjMcqMI0daQIfqCTuYQp2lisfE4fmJTvI-9uKlw.png) 
BREAK DOWN INTO SECTIONS AND SHOW IT WORKS 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/m_pOxTAUP6F2kliOu-96STivxWsFgXXHhLs4327ErKEtWK9rtjZiEygt0UihD6DbyTEGZZh0romr0x3ln3Sa37hRdbiP0udzLkNnsdCO5ZjRpLvbTRgDEVhsJcUUzjB8.png) 
    - 
-  _**Lecture 3**_   Coding Programs as Numbers  
    - $Prog, [x_1, x_2, ...] \rightarrow y$. (y in R0) 
    - **Numerical Coding of pairs**
        - Triangle equals means by definition.
        - A bijection (one to one correspondence) between pairs:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/wxblGNzAQoXmEAp1VRPuG8zD2QjQzoqsd9Do2crsF5jy6P1MUXsP7fgMPSVnJelLevodmZauZsuYFMBBaa_l3Iy0e5p7etaHf53VTxOBNdkLIqpFErN8nxMqMkqMwKZU.png) 
        - Every natural number (not including zero in the first case) appears uniquely in this encoding.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/lUV40eWVwJCvak73kaQmwm58az0YmKiIwx66doA-RJ10vPomyVyG-nAAK3VV-wQ4gGsq-Uyn1uyXo-Aldsom7hrC0VRgVnENbHjo2YPbnWfLLX58XNgnB1xKDJOnI5Jq.png) 
        - First version is x 0's, then a 1 and then the binary value of y. Second version is x 1's then a 0 then the binary value of y.
    - **Numerical Coding of a list**
        - We recursively apply this pair encoding, stepping through the list with the empty list set to 0.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Igt53IFPBELGvpNnjMA9xgk2Gm82407Ur22Tp9jTzev0JMDr-LjpupXj4ILEoHqnWTcpElMjUsFrvZx0MJnkkdXv4j7hUmW-PxSouuIqWxTV7XK6auD4PSql6hf-Ybly.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/AWzKSIpKAfvQe29H4D6RVFaK1tjEm84cjuMNfxG_7K3S52QUytj-7pHJbe_ZUvjgA8GspdGnnK7YJrtMU5MEYlYMDE4onjlrpVTGew4YJMgzeKV8YFyYg5NGkZU_i9ZR.png) 
        - You can find the elements in the list within the encoded binary - the number of zeroes in-between 1's form the values.![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gF4nk51h36_RDmyecs-pvBmIAZY5Xqp61M20y1NZ0NxIk9-qBHxWkXvZLkLJpXuEONsGoU8lFEX2-y8B-mEwxpJdb_37j63X9F8poBRjZDAbIKyCw_nsdrxQ7yz_4-mc.png)
E.eg [2, 1, 3] becomes 0b100010100 - 3 0's, 1 0, 2 0's.
    - **Numerical coding of programs**
        - For a program:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/U1BttrJOAPjiiqmrMllzDYSWuXz9xBQhdtEdmHqixxepjyvzqtlL_a8D66lIlqdjabQfzE4PDTVCSyyu7ftudE_H60YKmk-WiJkPYAB1lgrPei5UK-7fZNxiRDXou0jS.png) 
        - It's numerical code is: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/PThJM8ADv9sbWOYMw_R-pieWc6lVNzbJ__WilD-0_B2JZmuyp5jWFY4cQquuSuVFH-G_aejoli-1oNqLryOSGGjyqCkTINr6l0j7c2uhlTw8ayufLhzH7aGkJqPTzCW2.png) 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vt8ogfpFQJ6T0FK4O-VHShYpqbmfvNcwZBpWM1gNumR4UhY9qhmHiGjVozwSBZI8hElL7m4_HAZ7GPN6mCQPBO9-ctsQGu0jwhSeWMIA-Qi9WJBnIOmD5mLtgSiGVdRg.png) 
        - Note, we distinguish between the 1st and 2nd instructions by testing for odd or even.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/1czSVods4EE1kb8fspAYGUkEpCVrVXTGFqi8V3hC5RNp5CG8hWuRuevudjrU5iS-0HYulMXFAGrRpSDjiG9Ve1StKpVOAGsxMKBjnzpWdHntCojXqydae784DW50hK6g.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ypq4lD8J0YnIEGC4AdknfgxCmwXVDoNmI93OknzSl0pvydl-ndwO4b4s9BU8R_1mmuX1p_criJ6pcVM2Jq2tu58SbHrv3bkjiltdWpfcec6KjCDAk_IvrSGnL0QsdPec.png) 
    - **High-level specification**
        - Universal RM $U$, does the following: 
            - Starts with $R_0 = 0$ 
            - $R_1 = e,$ where e is the **code of a program** 
            - $R_2 = a,$ where a is the **code of a list of arguments** 
            - And all other registers are zeroed 
            - We then want the machine to 
                - decode e as an RM program P
                - decode a as a list of register values $a_1, ..., a_n$ 
                - Carry out the computation of P, with $R_0=0, R_1=a_1, ..., R_n = a_n$ 
    - **Overall structure of U's Program**
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6SEXwKGB81mN2HEZW19IO9h7mJ6C34SKBSXv57rMEPEC7TTRziDVsgHZeo55wNx3pvnM-LJrVL62OjqL6k2XNmTLT5rIRAcZHCMSNE30Rdf8DqRruHT_B03nHTIB30Il.png)
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/dMZd0ekDYPufF-mXVg293IHLWpuG3Y22rbiUG7hvc5zBgXciqzkDbKk8cnw_HBORXmQ9vDhvO19AvNmJeah5qwG_KuwJTUImuyOiKUhDtyu9eWcOvLghCx1ot9LIlCid.png) 
        - 2: If a halting instruction, we want to save the output of the simulated machine.
        - 
-  _**Lecture 4**_   Universal Register machine
    - **High-level spec** 
        - Starts with $R_0 = 0, R_1 = e, R_2 = a$ where a is the coded list of arguments.  
        - Then needs to decode the program, decode the arguments and carry out the computation on the decoded arguments. With other registers set to 0
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/K3tc3n2xp2-oDMQ9lBS2ARpLBaCnkKOiTtbqG2aRafKXrhm5fL58aGWv6U47hvt3WF5lALwh6wrek0Pt2xPAg3_VSzEaugaN9Ixwa2k20VFocKUrfOrdHQ6hZvOWSzKe.png) 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2iuOrCYQMNQN-u-HURqJva7bVu7reuk68WIoRuE2PP_FnKCGO3CD_HO7tkLyf9AWCvvsq-oCUITvki3E1bNj--lv4jhX8kmAYAhhbMlBQcLsXcZg6B9_B7XspvJ6HA8s.png) 
    - **First, non-destructive assignment computing S**―**=R** 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/SK-SvNlFgy25MKJkyiTFCqzC5gj0RKLvSOOWint7sKY_n6iHTplVXWXbpA4XiyVT4KjwTPFZ60ad_LSSaM5l2P61a8QIuDUcm4dfQKKz3e0dtgxRag-3EgIk83rdXVj1.png) 
        1. First zero out S 
        2. Then put R into Z & S (R now zero)
        3. Then transfer the contents of Z into R
        - Note - requires Z=0 at the start of the program.
    - **Second, need a method of adding a value to a list (X,L) **―**= (0, X::L)** 
        - Need $2^x (2L + 1)$ 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vjClI-VL7U0maj4KS2xSUGBr_aSOIf-rCDHY3phA0lhItZMfg7I3HyNE0xlcT9dvKf8IkZysQWcK3CmS5vtWYFLp_Z0flM7rNDh4wwec_CUM-8aFu-2qmbgxQwv1ermI.png) 
        1. Z becomes 2*L + 1  in the first 3 transitions
        2. Then Adds Z and L becomes 2*L + 1+ Z 
        3. We then repeat this whole process X times 
    - **Third, need a method of popping an item off a list (0,X**―**L) ::= (X, L)** 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-DZ91vSCkov50xS6muMjEA0s3_ycVD_KFfQuROmKzi4VlWUM1AscJRVEUFk_-C3sGBw0N_6swd10mQV_FcC2rtKfvnfHUfqj7GoAJ9bHJvrcgFGc8TdQmayhJK2bs4gH.png) 
        1. X gets set to zero 
        2. If L is zero then exit
        3. Otherwise, Z = Z+ L and L=0
        4. L=(Z+L)/2 and Z=0 
            - If Z+L even then we compute $(Z,L) ::= (0, \frac{1}{2} (Z+L) )$ and continue. 
            - Otherwise, $(Z,L) ::= (0, \frac{1}{2} (Z+L-1) )$ - then we halt. 
        5. X = X+1 then repeat  
        - We've started with $2^x (2L + 1)$ and found $x$! 
    - **The program for the universal register machine**  
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/fKWdWvWXlf7MRzV4_VUa0zMBKi56VdF7hzbTxpI-z5e7PPS6vEq8F94ZLbqNI4e8BGj8qydq4ZTCFblCC0pbGVJwqu6zXRlaVRXyN4j7r_ilR9IqR8yxtBEQ2OMxNdMh.png) 
        1. First we make sure that the simulated machine has register 0 set to 0 
        2. Copy the program into T, then **continually **pop off elements of the list until we have the **PC'th **one. So at first we get the 0'th item. 
            - If N is 0, then we wanna halt okay!
        3. The we pop N into C (If zero, that's a halt instruction and we need to finish)
        4. Then pop get A (the arguments) into R, we can decide what type of instruction C is by **finding if it's even or odd.** 
            - We need to get the ith register contents in S, as that will tell us what instruction to run
        5. If **C is even** 
            - We know we've got an increment and a jump to Z. First we set the PC to N, that being the instruction we're going to jump to.
            - We've incremented the ith item of the list, so we need to push R back onto A. 
            - That pop S into R (it will be reset anyway)
        6. If **C is odd** 
            - Adding 1 converts thick angle brackets to thick angle brackets, then peels the thin angle brackets to get N In the PC.
            - If R is zero, we want to jump to N
            - If R is non-zero, then we need to loop again
                - 
-  _**Lecture 5**_   The Halting Problem
    - A Register machine **solves the halting problem **if when a program is loaded with arguments, the machine halts with R_0 = 1 if the input program halts or 1 if it loops forever. 
    - **Proof of the theorem**
        - Assume we have such an RM H
        - Let H' be obtained by doing Z = R_1 ⇒push Z to R_2   
Does our diagonalization, sets the input to the program.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/icZsNlwGEfEkQqLBRu1q8NNJBMMfiTKhpP5M2KhQBZbkVFRNClDwBJSZ6dwKq6nuPcQ4_jqKPvIX9GBaX9RVVgMz3JDGcK2HNARXTtv8bXn1gF7tgtQ4BWXqTwCGXDY0.png) 
This just does the - if halt run forever, if run forever halt.
        - Let $c\in \N$ be the index of C's program. 
        - If we stick C into C we have:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/iGWofZILXpfLkMnIaJZNeB60ngWlEj4BUbA8if9mWwVa5Ppo4NNG1pKkYfwCZyll6sIah8RX8p3gL-VlpUkduAt0RnTGmvbEfc7f71QR9Jst34FlPSkfA8TYB70mxbp2.png) 
    - **Computable functions**
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qtXDQx_vG86XX80_EpdlnKN1XaLC_rrhwNLRkhCYvezlZhrO3F4NGgkSci9yF-5452D4rJSjINpNSUz2qrX268EFX7Jf1Di8sVhUTjyhtjUHvmULDt_kMysyYP-10qrs.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/PJDSlq6_zsO1hMQEJh_YmSyNTWZz-PcohWH_N6aKBMOULAPs00r-NEHnRwEilqhDDDV3dTWRo4LliS3oiC3ujjrpbZg9AiFEqEwVc0WSF9Svz_I-PgKi6Jk9YVDcNMkf.png) 
        - Basically apply a register machine to an input. 
        - Thus $e \mapsto \phi_e$, defines an onto function from N to computable partial functions. But this is countable, So $N \mapsto N$ (uncountable by Cantor) contains uncomputable functions 
    - **An uncomputable function**
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/GW93ZmARcIoHylVkuLE0j9kZJsYB6xqdpOGxGI4GwMw3bGmvyFOTLntufpSPQANUAanUh7Lqk-76TCfsREFYgAU75RpSyflkm3Yn9P2tZ8uoXW2f4YtGHW_WvpQpAyD4.png) 
        - 
    - **Undecidable sets of numbers**
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Js2OV9u9HtSzMHQcGQBjgNAUW5bGyhbcPkM8C0Wu-FYL0-JSnBSMbC5-GpfT4gvMMYdHt9E29M7gkwALPZXq-rMzsv_IEpYPZ4rrexeSHE-vUofyUPK0RG7NTsISM3_4.png) 
        - The set S is **decidable**, if there exists a register machine that can always figure out if an x is in S.
        - Basic strategy to prove undecidability:
            - Try to show that decidability of S would imply decidability of the Halting Problem
        - Let the set S0 be the set of register machines that halt when given 0. 
        - 
        - 
-  _**Lecture 6**_   Turing machines
    - Turing Machines 
        - **Informally:**
            - Machine in a finite set of states, with a finite alphabet and a finite number of cells with values in. **Goes infinitely to the right. **Distinct symbol for blank. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/IeWbubffbBSIDQKZVJ_g3W4KCmTU3p_nFXWjKYjlvRU1CGXi7lSZPvLoH8Ccao4bFOJNJS_9YuwHwF30RR4n6DuxYh9xnaZOJLR9Gug_2ur6XjFAFJ5p940EGsbaV5S4.png) 
        - **Formally:** 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/pktd1rD7w9TC4G1z99F-iXcjFAy7rbDQDZ1odh4_cFnTqt7ckziMmUy9XRWWbtjPOJsdVGoVTOVcucb0-51ssyP8jY-RRAsCmwYzlXFj26EhoDnNCtL0_OUvnE89z3lx.png) 
        - **Turing machine configuration** 
            - $(q, w, u)$ ⇔ (current state (could be acc or rej), w = non-empty string of tape symbols under and to the left, u = string of tape symbols to the right (up to some point of all blanks))
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/GNEnc6-kN6WhUIS0cCv0yCj99CH0LcTEXjWPnQFIeydDxF5EYbLpCHJhUH5qmjejmIjv_CRYcm_mASIg64K6UseUmISrsApQ79m_Bf5gzlnAAUFmqp7HySuB6Pvt_OrY.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/J263e2cNBbeSp3D-RuUqBHJdX8IKtvTY80GjgYzFP0C5HaSQEq2HcGw56WNbxw_sfEFIXa2qV_osSSlq77W3vUnzpKw_XkX_pGu7zLHdbX0q0LkWC0NWgQ1hPsif3JRo.png) 
            - Initial configurations = (s, ▷ , u) 
        - **Turing machine computation**
            - A (finite or infinite) sequence of configuration, where the changes in configurations are deterministic. Note, the delta function can only be applied on elements not including acc or rej - so there will be no transition function and the machine will halt.
        - **Register machines can simulate Turing machines** 
            - First we encode symbols numerically 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vpEKLauN7JsrHWEGnLOjQJEkZ1tzQMgOpEfgBAe3R6r6NDbYNf7Mt59_Xxc3PZg8GutEewYyH9_vP2Xy6ULiVu9Y0pMXOlijeW5o6xdgOtpn0q2z2YLOiQoiwABCnD4s.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4Eh3baDkdoHrSZ7KTEg3eENS3JxBOMhUO32AvGdA8PABCZw0HjEK1bWQLhrCgGEuDdu_lJkvf9ccy9JZnVooxtF6b9__t6c3ecKtU1ex09Ixaviud3XmhAENOCwGJVJr.png) 
            - Encode a configuration into a list! Note the list behind you is from end to start - we want to be able to pop off what we're looking at straight away.
            - Next we implement the transition function of the machine 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_zM-rF0Y9txffqJFsLKfkrgGZ5yrYv91rzwvyGZ_7h2NMXxTe0dWtU7jbquaXA-FA5BFkxTjd6V5_ZOafvnG2v8q-NBMxJkNIPZ1SyFurnFiWRYitZWYnjrvQxzBIuRu.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/WJ_UEBqJWz57fRSpQq1DjcWPgQGU_NzarWbajTuIb5AaQtURZ49_R9AgiRx_57ZFmOfwT6XLeJ8wacrCrQNMwR9gwoPOOo-YhotyO8LvsCKTSS3jOxCelf9OTVKCSrxJ.png) 
                - Basically saying, given that there's finitely many such transitions - we can do it. 
            - Finally implement a register machine to repeatedly carry out the instructions
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/wRVf--kZPTRz0fhsW_6vCm43oOaWciw4cojNrL0YqDGmtYuolyZu5zHAh4OelC0VO2uTALjwjq4QjW_Ob9BxFJ-uNhS_nizJEREW5XyA5DJkx5Zcn6HdtrpFtvhVOAxn.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/LoecY4TA6VFG92E0P071sbOcC0C7BvTk-A0XVUgUg5U47SykAbd-KUuTMoUpKTS2UuwZSlK7uSqV981uyxqYRNGQQuLFcKMLwGrLo3O1M8LXcmX3WpWJvuhzsvXL74Fv.png) 
            - If Q<2 we need to accept or reject
            - Otherwise get the instruction we're currently looking at and stick it in A.
            - We can then get Q,A,D - if we move left we need to shift a value to the right of us OTHERWISE we either pop something and push it to the right **or **remain stationary. 
            - 
-  _**Lecture 7**_   TODO
- 
- Supervision 2
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/kFP0VuaP_47A6RwFgm_NaRNz2zTTYQpfmW5005k0aI1IHSIF7cC0Z948wk6YZXRXidmYEHdFLFpTyIXTvD75Trwbg9eLkKdGLS2mhRz2mxKo-NBgw3uC7WXpNof2WBxa.png) 
    - DONT REALLY GET THIS
    - 
    - 
    - **Exercise 4** 
        - Exercise 4. Show that there is a register machine computable partial function f : N ⇒ N such that both {x ∈ N | f(x)↓} and {y ∈ N | (∃x ∈ N) f(x) = y} are register machine undecidable.  
        - 1 - does f halt, given natural numbers as input.
        - 2 - we can find all the defined outputs of f. 
        - Consider the register machine M that takes an input e, and simulates the program e encodes:
        - Proof by Contradiction.
Assume {x ∈ N | f(x)↓} for f = $\varphi_e$ we can decide if M halts given natural numbers as input.
As this is decidable and as our programs are coded over the natural numbers, we can decide if a arbitrary program halts. But this is a contradiction, as the halting problem is undecidable so our assumption must be false.  
        - Proof by Contradiction.
{y ∈ N | (∃x ∈ N) f(x) = y}. Consider, if all the outputs for our simulated function is decidable - we can find all the inputs for which the program halts and thus we know it does not halt for all inputs, solving the halting problem. As this is impossible, this set must be register machine undecidable.
    - **Exercise 5**
        - Assume S2 is register machine decidable - that is assume there exists a register machine M, such that M with input a halts and outputs 1 if a is in S2 and halts and outputs 0 otherwise. 

So to test if an element x is in S1, we simply compute f(x) (which we can do as f(x) is register machine computable) and then execute M on f(x) - if f(x) is in S2 then we know x is in S1, if not then x is not in S1. 
So using M, S1 becomes register machine decidable.  
Therefore if S2 is decidable, S1 is too.
    - 
    - **Exercise 6**
        - Proof by contradiction:
Assume we have a machine M that decides if two codes are equivalent. We can then create a machine that takes the code for a program e and compares it to the program```haskell
 L0: R1+ -> L0
``` which loops forever (using M).
This overall program then decides if a program is equivalent to a program that never halts, (i.e. if it isn't the input program doesn't halt) and we have solved the halting problem.
But, this is a contradiction as the halting problem is undecidable - so we cannot have such a machine M. 
    - 
    - **Exercise 5.1** - Show that decidable sets are closed under union, intersection, and complementation. Do all of these closure properties hold for undecidable languages?   
        - **Union** 
            - If I have a set A & B that are both register machine decidable by machines $M_A$ and $M_B$, we can form a machine that detects the union of the two sets by doing the following: ```haskell
 RUN M_A
 LN : R0- -> LK+1 LN+1
 LN+1: RUN M_B
 LK: R0- -> LK+1 LK+2 
 LK+1: R0+ -> LK+1
 LK+2: HALT
``` I.e. run M_A, then if the output in R0 is nonzero halt (after increasing R0 again) - if R0 is not nonzero then run M_B and check if thats nonzero.
        - **Intersection**
            - If I have a set A & B that are both register machine decidable by machines $M_A$ and $M_B$, we can form a machine that detects the intersection of the two sets by doing the following: ```haskell
 RUN M_A
 LN : R0- ->  LN+1 LK
 LN+1: RUN M_B
 LK: HALT
``` I.e. run M_A, then if the output in R0 is nonzero reduce it to zero and proceed to run M_B - if R0 is not nonzero then halt.
        - **Complementation**
            - If I have a set A that is register machine decidable by a machine  $M_A$, we can form a machine that detects the complementation of A by doing the following: ```haskell
 RUN M_A
 LN: R0- -> LN+2 LN+1
 LN+1: R0+ -> LN+2
 LN+2: HALT
``` I.e. if M_A outputs 0 then switch that to 1, and vice versa.
        - **Do these hold for undecidable languages?** 
            - Clearly this is true for complementation (i.e. that undecidable sets are closed under complementation), as if there were a machine that could decide the complement of an undecidable set - we could just use a register machine to find the complement of that complement and retrieve the original set.
            - Proof by contradiction. Assume undecidable sets are not closed under the union. 
Consider two sets A & B, where A and B are undecidable but the set $A \ \cup\ B$ is decidable by a machine M. Consider if we have another set C that contains no elements of A (and B is a subset of $A \ \cup \ C$ ), and the set $B \ \cup \ C$ is decidable by a machine N. 
However, this makes A,B and C decidable,  as we can simply compute M & N and if only M is 1 then we have A, if both are 1 we have B and if only N is 1 we have C. But as A,B and C are undecidable we must have that undecidable sets are closed under union.
            - Consider two sets A & B, where A and B are undecidable but the set $A \ \cap \ B$ is decidable by a machine M. 
Proof by contradiction. Assume undecidable sets are not closed under the intersect. 
Let A, B and C be three undecidable sets.
We know that $A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$ by the distributive property of unions. 
As the right hand side is decidable (under our assumptions) the left hand must be too - this implies that the union of an undecidable set with a decidable set is decidable. 
This is trivially false, as if we took the union of the set of programs that halt and the set {1}, we could decide the halting problem. Thus the union of an undecidable set with a decidable set is decidable which is a contradiction, so our initial assumption must be false.
    - 
